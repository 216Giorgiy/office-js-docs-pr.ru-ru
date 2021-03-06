---
title: Обзор создания кода с помощью API JavaScript для OneNote
description: ''
ms.date: 01/23/2018
ms.openlocfilehash: aded1210abc11a80c6200a207d3896df8ef4218b
ms.sourcegitcommit: c72c35e8389c47a795afbac1b2bcf98c8e216d82
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/23/2018
ms.locfileid: "19439014"
---
# <a name="onenote-javascript-api-programming-overview"></a>Обзор создания кода с помощью API JavaScript для OneNote

В OneNote представлен API JavaScript для надстроек OneNote Online. Вы можете создавать надстройки области задач, контентные надстройки и команды надстроек, которые взаимодействуют с объектами OneNote и подключаются к веб-службам или другим веб-ресурсам.

> [!NOTE]
> Если вы планируете [опубликовать](../publish/publish.md) надстройку в AppSource и сделать ее доступной в интерфейсе Office, убедитесь, что она соответствует [политикам проверки AppSource](https://docs.microsoft.com/en-us/office/dev/store/validation-policies). Например, чтобы пройти проверку, надстройка должна работать на всех платформах, поддерживающих определенные вами методы. Дополнительные сведения см. в [разделе 4.12](https://docs.microsoft.com/en-us/office/dev/store/validation-policies#4-apps-and-add-ins-behave-predictably) и на [странице со сведениями о доступности и ведущих приложениях для надстроек Office](../overview/office-add-in-availability.md).

## <a name="components-of-an-office-add-in"></a>Компоненты надстройки Office

Надстройки состоят из двух указанных ниже основных компонентов.

- **Веб-приложение**, состоящее из веб-страницы и необходимых JavaScript-, CSS- или других файлов. Эти файлы можно разместить на веб-сервере или в службе веб-хостинга, например в Microsoft Azure. В OneNote Online веб-приложение отображается в элементе управления браузера или в iFrame.
    
- **Манифест в формате XML**, в котором указан URL-адрес веб-страницы надстройки и все требования, необходимые для получения доступа, параметры и возможности для надстройки. Этот файл хранится на клиентском компьютере. Для надстроек OneNote используется такой же формат [манифеста](../develop/add-in-manifests.md), что и для других надстроек Office.

**Надстройка Office = манифест + веб-страница**

![Надстройка Office состоит из манифеста и веб-страницы](../images/onenote-add-in.png)

## <a name="using-the-javascript-api"></a>Использование API JavaScript

Для доступа к API JavaScript надстройки используют контекст среды выполнения ведущего приложения. API состоит из двух указанных ниже уровней. 

- **Многофункциональный API** для связанных с OneNote операций, доступ к которому осуществляется с помощью объекта **Application**.
- **Стандартный API**, используемый приложениями Office, доступ к которому осуществляется с помощью объекта **Document**.

### <a name="accessing-the-rich-api-through-the-application-object"></a>Доступ к многофункциональному API с помощью объекта *Application*

Для доступа к объектам OneNote, например к объектам **Notebook**, **Section** и **Page**, используйте объект **Application**. С помощью многофункциональных API вы можете запустить пакетные операции на прокси-объектах. Основной процесс выглядит примерно так, как указано ниже. 

1. Получение экземпляра приложения из контекста.

2. Создание прокси-объекта, представляющего объект OneNote, с которым вам необходимо работать. Для синхронного взаимодействия с прокси-объектами можно считывать и записывать их свойства и вызывать имеющиеся в них методы. 

3. Вызовите метод **load** прокси-объекта, чтобы указать для него значения свойств, указанные в параметре. Этот вызов будет добавлен в очередь команд.

   > [!NOTE]
   > Вызовы, которые методы совершают к API (например, `context.application.getActiveSection().pages;`), также добавляются в очередь.

4. Чтобы запустить все поставленные в очередь команды в том порядке, в котором они находятся в очереди, вызовите метод **context.sync**. Этот метод синхронизирует состояния выполняющихся сценариев и реальных объектов, а также получает свойства загруженных объектов OneNote, которые необходимо использовать в сценарии. Вы можете использовать возвращенный объект обещания для связывания дополнительных действий в цепочку.

Примеры: 

```js
function getPagesInSection() {
    OneNote.run(function (context) {
        
        // Get the pages in the current section.
        var pages = context.application.getActiveSection().pages;
        
        // Queue a command to load the id and title for each page.            
        pages.load('id,title');
        
        // Run the queued commands, and return a promise to indicate task completion.
        return context.sync()
            .then(function () {
                
                // Read the id and title of each page. 
                $.each(pages.items, function(index, page) {
                    var pageId = page.id;
                    var pageTitle = page.title;
                    console.log(pageTitle + ': ' + pageId); 
                });
            })
            .catch(function (error) {
                app.showNotification("Error: " + error);
                console.log("Error: " + error);
                if (error instanceof OfficeExtension.Error) {
                    console.log("Debug info: " + JSON.stringify(error.debugInfo));
                }
            });
    });
}
```

Сведения о поддерживаемых объектах и операциях OneNote см. в [справочнике по API](https://dev.office.com/reference/add-ins/onenote/onenote-add-ins-javascript-reference).

### <a name="accessing-the-common-api-through-the-document-object"></a>Получение доступа к стандартному API с помощью объекта *Document*

Для доступа к стандартному API, например к методам **getSelectedDataAsync** и [setSelectedDataAsync](https://dev.office.com/reference/add-ins/shared/document.getselecteddataasync), используйте объект [Document](https://dev.office.com/reference/add-ins/shared/document.setselecteddataasync). 

Например:  

```js
function getSelectionFromPage() {
    Office.context.document.getSelectedDataAsync(
        Office.CoercionType.Text,
        { valueFormat: "unformatted" },
        function (asyncResult) {
            var error = asyncResult.error;
            if (asyncResult.status === Office.AsyncResultStatus.Failed) {
                console.log(error.message);
            }
            else $('#input').val(asyncResult.value);
        });
}
```
Надстройки OneNote поддерживают только указанные ниже стандартные API.

| API | Примечания |
|:------|:------|
| [Office.context.document.getSelectedDataAsync](https://dev.office.com/reference/add-ins/shared/document.getselecteddataasync) | Только **Office.CoercionType.Text** и **Office.CoercionType.Matrix** |
| [Office.context.document.setSelectedDataAsync](https://dev.office.com/reference/add-ins/shared/document.setselecteddataasync) | Только **Office.CoercionType.Text**, **Office.CoercionType.Image** и **Office.CoercionType.Html** | 
| [var mySetting = Office.context.document.settings.get(имя);](https://dev.office.com/reference/add-ins/shared/settings.get) | Параметры поддерживаются только контентными надстройками | 
| [Office.context.document.settings.set(имя, значение);](https://dev.office.com/reference/add-ins/shared/settings.set) | Параметры поддерживаются только контентными надстройками | 
| [Office.EventType.DocumentSelectionChanged](https://dev.office.com/reference/add-ins/shared/document.selectionchanged.event) ||

В общем случае стандартный API следует использовать только тогда, когда необходимые возможности не поддерживаются в многофункциональном API. Дополнительные сведения об использовании стандартного API см. в [документации](../overview/office-add-ins.md) и [справочнике](https://dev.office.com/reference/add-ins/javascript-api-for-office) по надстройкам Office.


<a name="om-diagram"></a>
## <a name="onenote-object-model-diagram"></a>Схема объектной модели OneNote 
На схеме ниже показаны возможности, которые на данный момент доступны в API JavaScript для OneNote .

  ![Схема объектной модели OneNote](../images/onenote-om.png)


## <a name="see-also"></a>См. также

- [Создание первой надстройки OneNote](onenote-add-ins-getting-started.md)
- [Справочник по API JavaScript для OneNote](https://dev.office.com/reference/add-ins/onenote/onenote-add-ins-javascript-reference)
- [Пример надстройки Rubric Grader](https://github.com/OfficeDev/OneNote-Add-in-Rubric-Grader)
- [Обзор платформы надстроек Office](../overview/office-add-ins.md)
