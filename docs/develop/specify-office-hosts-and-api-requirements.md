---
title: Указание ведущих приложение Office и требований к API
description: ''
ms.date: 12/04/2017
ms.openlocfilehash: bd517dee1faf8d3f3009a0b9ce7127f5760e730d
ms.sourcegitcommit: c72c35e8389c47a795afbac1b2bcf98c8e216d82
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/23/2018
ms.locfileid: "19437712"
---
# <a name="specify-office-hosts-and-api-requirements"></a>Указание ведущих приложение Office и требований к API

Работа надстройки Office может зависеть от ведущего приложения Office, набора требований, элемента или версии API. Например, надстройка может:

- работать в одном (Word или Excel) или нескольких приложениях Office;
    
- использовать API JavaScript, доступные только в некоторых версиях Office. Например, можно создать надстройку Excel 2016 на базе новых API JavaScript для Excel; 
    
- работать только в версиях Office, которые поддерживают элементы API, используемые вашей надстройкой.
    
Эта статья поможет вам разобраться, какие параметры следует выбрать для правильной работы надстройки и максимального охвата аудитории.

> [!NOTE]
> Общие сведения о том, на каких платформах поддерживаются надстройки Office, см. в [этой статье](../overview/office-add-in-availability.md). 

В таблице ниже перечислены основные понятия, рассматриваемые в этой статье.

|**Концепция**|**Описание**|
|:-----|:-----|
|Приложение Office, ведущее приложение Office или ведущее приложение|Приложение Office, используемое для запуска надстройки, например Word, Word Online, Excel и т. д.|
|Платформа|Платформа ведущего приложения Office, например Office Online или Office для iPad.|
|Набор обязательных элементов|Именованная группа связанных элементов API. С помощью наборов требований надстройка определяет, поддерживает ли ведущее приложение Office элементы API, которые она использует. Проще проверять поддержку набора требований, а не отдельных элементов API. Поддержка набора требований зависит от ведущего приложения Office и его версии. <br >Наборы требований указываются в файле манифеста. Задавая наборы требований в манифесте, вы указываете, какой минимальный уровень поддержки API должно обеспечить ведущее приложение Office, чтобы можно было запустить надстройку. Надстройка не будет работать в ведущих приложениях Office, которые не поддерживают наборы требований, указанные в манифесте, и не будет отображаться в разделе <span class="ui">Мои надстройки</span>. Это ограничивает доступность надстройки.В коде с помощью проверок в среде выполнения. Полный список наборов требований см. в статье[Наборы требований для надстроек Office](https://dev.office.com/reference/add-ins/requirement-sets/office-add-in-requirement-sets).|
|Проверка в среде выполнения|Проверка в среде выполнения, которая позволяет определить, поддерживает ли ведущее приложение Office наборы требований или методы, которые использует надстройка. Чтобы запустить такую проверку, используйте оператор **if** с методом **isSetSupported**, наборами требований или именами методов, которые не входят в набор требований. Проверки в среде выполнения позволяют максимально расширить аудиторию надстройки. В отличие от наборов требований, такие проверки не позволяют задать минимальный уровень поддержки API, который требуется для запуска надстройки. Вместо этого с помощью оператора **if** вы определяете, поддерживается ли элемент API, и если это так, добавляете в надстройку дополнительные функции. Если вы используете проверки в среде выполнения, ваша надстройка всегда будет отображаться в разделе **Мои надстройки**.|

## <a name="before-you-begin"></a>Перед началом работы

Надстройка должна использовать последнюю версию схемы манифеста надстройки. Если вы используете проверки в среде выполнения, используйте последнюю версию библиотеки API JavaScript для Office (office.js).

### <a name="specify-the-latest-add-in-manifest-schema"></a>Выбор последней версии схема манифестов надстроек

Ваша надстройка должна использовать схему манифеста 1.1. Настройте элемент **OfficeApp** в манифесте надстройки указанным ниже образом.

```XML
<OfficeApp xmlns="http://schemas.microsoft.com/office/appforoffice/1.1" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:type="TaskPaneApp">
```

### <a name="specify-the-latest-javascript-api-for-office-library"></a>Выбор последней версии библиотеки API JavaScript для Office

Если вы используете проверки в среде выполнения, то вам необходимо ссылаться на последнюю версию библиотеки API JavaScript для Office из сети доставки содержимого. Для этого добавьте указанный ниже тег `script` в HTML-код. Чтобы всегда ссылаться на последнюю версию файла Office.js, используйте `/1/` в URL-адресе сети доставки содержимого.

```HTML
<script src="https://appsforoffice.microsoft.com/lib/1/hosted/Office.js" type="text/javascript"></script>
```

## <a name="options-to-specify-office-hosts-or-api-requirements"></a>Параметры для задания ведущих приложений Office или требований к API

При указании ведущих приложений Office и требований к API необходимо учитывать несколько факторов. На следующей схеме показано, как выбрать правильный метод для надстройки.

![Выбор самого подходящего варианта указания ведущих приложений Office или элементов API для надстройки](../images/options-for-office-hosts.png)

- Если ваша надстройка работает в одном приложении Office, укажите элемент **Hosts** в манифесте. Дополнительные сведения см. в разделе [Задание элемента Hosts](#set-the-hosts-element).
    
- Чтобы задать минимальный набор требований или элементы API, которые должно поддерживать ведущее приложение Office для запуска надстройки, задайте элемент **Requirements** в манифесте. Дополнительные сведения см. в разделе [Задание элемента Requirements в манифесте](#set-the-requirements-element-in-the-manifest).
    
- Чтобы предоставить дополнительные функции, если определенные наборы требований или элементы API доступны в ведущем приложении Office, выполните проверку в среде выполнения для кода JavaScript надстройки. Например, если надстройка выполняется в Excel 2016, используйте элементы нового API JavaScript для Excel, чтобы предоставить дополнительные функции. Дополнительные сведения см. в разделе [Использование проверок в среде выполнения для кода JavaScript](#use-runtime-checks-in-your-javascript-code).
    
## <a name="set-the-hosts-element"></a>Задание элемента Hosts

Чтобы надстройка работала в одном ведущем приложении Office, используйте элементы **Hosts** и **Host** в манифесте. Если элемент **Hosts** не указан, надстройка будет работать во всех ведущих приложениях.

Например, указанное ниже объявление **Hosts** и **Host** указывает, что надстройка будет работать с любым выпуском Excel, включая Excel для Windows, Excel Online и Excel для iPad.

```xml
<Hosts>
  <Host Name="Workbook" />
</Hosts>
```

Элемент **Hosts** может содержать один или несколько элементов **Host**. Элемент **Host** указывает ведущее приложение Office, в котором может работать ваша надстройка. Обязательному атрибуту **Name** можно присвоить одно из указанных ниже значений.

| Имя          | Ведущие приложения Office                      |
|:--------------|:----------------------------------------------|
| База данных      | Веб-приложения Access                               |
| Документ      | Word для Windows, Mac, iPad и Word Online        |
| Почтовый ящик       | Outlook для Windows, Mac, Outlook в Интернете и Outlook.com | 
| Презентация  | PowerPoint для Windows, Mac, iPad и PowerPoint Online  |
| Проект       | Проект                                       |
| книга      | Excel для Windows, Mac, iPad и Excel Online           |

> [!NOTE]
> Атрибут `Name` указывает приложение Office, в котором может запускаться ваша надстройка. Приложения Office поддерживаются на разных платформах и работают на настольных ПК, в веб-браузерах, на планшетах и мобильных устройствах. Нельзя указать платформу, на которой можно запускать надстройку. Например, если вы укажете `Mailbox`, то для запуска надстройки можно будет использовать и Outlook, и Outlook Web App. 


## <a name="set-the-requirements-element-in-the-manifest"></a>Указание элемента Requirements в манифесте

С помощью элемента **Requirements** можно задать минимальные наборы требований или элементы API, которые должно поддерживать ведущее приложение Office для запуска надстройки. В элементе **Requirements** можно указать как наборы требований, так и отдельные методы, используемые в надстройке. В версии 1.1 схемы манифестов надстроек элемент **Requirements** необязателен для всех надстроек, кроме надстроек Outlook.

> [!WARNING]
> Используйте элемент **Requirements**, только чтобы указать ключевые элементы API, которые должна использовать надстройка. Если платформа или ведущее приложение Office не поддерживают элементы API, указанные в элементе **Requirements**, надстройка не будет работать в этом ведущем приложении или на этой платформе, а также не будет отображаться в разделе **My Add-ins**. Рекомендуем сделать надстройку доступной на всех платформах ведущего приложения Office, например Excel для Windows, Excel Online и Excel для iPad. Чтобы надстройка была доступной во _всех_ приложениях Office и на всех платформах, используйте проверки в среде выполнения, а не элемент **Requirements**.

В примере кода ниже показана надстройка, которая загружается во всех ведущих приложениях Office, поддерживающих указанные ниже элементы.

-  Набор требований **TableBindings** 1.1 или более поздней версии.
    
-  Набор требований **OOXML** 1.1 или более поздней версии.
    
-  Метод **Document.getSelectedDataAsync**.

```XML
<Requirements>
   <Sets DefaultMinVersion="1.1">
      <Set Name="TableBindings" MinVersion="1.1"/>
      <Set Name="OOXML" MinVersion="1.1"/>
   </Sets>
   <Methods>
      <Method Name="Document.getSelectedDataAsync"/>
   </Methods>
</Requirements>
```

- Элемент **Requirements** содержит дочерние элементы **Sets** и **Methods**.
    
- Элемент **Sets** может содержать один или несколько элементов **Set**. Параметр **DefaultMinVersion** задает значение **MinVersion** по умолчанию для всех дочерних элементов **Set**.
    
- Элемент **Set** указывает наборы требований, которые ведущее приложение Office должно поддерживать для запуска надстройки. Атрибут **Name** указывает имя набора требований. Атрибут **MinVersion** указывает минимальную версию набора требований. **MinVersion** переопределяет значение **DefaultMinVersion**. Дополнительные сведения о наборах требований и их версиях, к которым принадлежат элементы API, см. в статье [Наборы требований для надстроек Office](https://dev.office.com/reference/add-ins/office-add-in-requirement-sets).
    
- Элемент **Methods** может содержать один или несколько элементов **Method**. Элемент **Methods** не следует использовать с надстройками Outlook.
    
- Элемент **Method** задает отдельный метод, который должно поддерживать ведущее приложение Office, в котором работает надстройка. Атрибут **Name** обязателен и указывает имя метода с его родительским объектом.
    

## <a name="use-runtime-checks-in-your-javascript-code"></a>Использование проверок в среде выполнения для кода JavaScript


Если ведущее приложение Office поддерживает определенные наборы требований, вы можете добавить в надстройку дополнительные функции. Например, если надстройка работает в Word 2016, вы можете использовать в ней новые API JavaScript для Word. Для этого используйте метод **isSetSupported** с именем набора требований. В среде выполнения метод **isSetSupported** определяет, поддерживается ли набор требований ведущим приложением Office, в котором запущена надстройка. Если он поддерживается, то метод **isSetSupported** возвращает значение **true** и запускает дополнительный код, который использует элементы API из этого набора. Если приложение Office не поддерживает набор требований, метод **isSetSupported** возвращает значение **false**, и дополнительный код не запускается. В коде ниже показан синтаксис, который необходимо использовать с методом **isSetSupported**.


```js
if (Office.context.requirements.isSetSupported(RequirementSetName , VersionNumber))
{
   // Code that uses API members from RequirementSetName.
}

```


-  _RequirementSetName_ (обязательный параметр) — это имя набора требований. Дополнительные сведения о доступных наборах требований см. в статье [Наборы требований для надстроек Office](https://dev.office.com/reference/add-ins/office-add-in-requirement-sets).
    
-  _VersionNumber_ (необязательный параметр) — это версия набора требований.
    
В Excel 2016 или Word 2016 для наборов требований **ExcelAPI** или **WordAPI** используйте метод **isSetSupported**. Метод **isSetSupported**, а также наборы требований **ExcelAPI** и **WordAPI** доступны в последней версии файла Office.js в CDN. Если вы не используете файл Office.js из CDN, надстройка может создавать исключения, так как метод **isSetSupported** не будет определен. Дополнительные сведения см. в статье [Выбор последней версии библиотеки API JavaScript для Office](#specify-the-latest-javascript-api-for-office-library). 


> [!NOTE]
> Метод **isSetSupported** не работает в Outlook и Outlook Web App. Чтобы использовать проверку в среде выполнения в Outlook или Outlook Web App, используйте способ, описанный в разделе [Проверки в среде выполнения с использованием методов, не входящих в набор требований](#runtime-checks-using-methods-not-in-a-requirement-set).

В приведенном ниже примере кода показано, как функциональность надстройки может отличаться в ведущих приложениях Office, поддерживающих разные наборы требований или элементы API.




```js
if (Office.context.requirements.isSetSupported('WordApi', 1.1))
{
    // Run code that provides additional functionality using the JavaScript API for Word when the add-in runs in Word 2016.
}
else if (Office.context.requirements.isSetSupported('CustomXmlParts'))
{
      // Run code that uses API members from the CustomXmlParts requirement set.
}
else 
{
    // Run additional code when the Office host is not Word 2016, and when the Office host does not support the CustomXmlParts requirement set.
}

```


## <a name="runtime-checks-using-methods-not-in-a-requirement-set"></a>Проверки в среде выполнения с использованием методов, не входящих в набор требований


Некоторые элементы API не входят в наборы требований. Это относится только к тем элементам API, которые входят в пространства имен [JavaScript для Office](https://dev.office.com/reference/add-ins/javascript-api-for-office) (все элементы в Office.), и не относится к элементам API, принадлежащим к пространствам имен API JavaScript для Word (все элементы в Word.) или [API JavaScript для надстроек Excel](https://dev.office.com/reference/add-ins/excel/excel-add-ins-reference-overview) (все элементы в Excel.). Если надстройка зависит от метода, не входящего в набор требований, вы можете использовать проверку в среде выполнения, чтобы определить, поддерживается ли метод ведущим приложением Office, как показано в примере кода ниже. Список всех методов, не входящих в набор требований, см. в статье [Наборы требований для надстроек Office](https://dev.office.com/reference/add-ins/office-add-in-requirement-sets).


> [!NOTE]
> Рекомендуем ограничить использование этого типа проверки в среде выполнения в коде надстройки.

В примере кода ниже показано, как проверить, поддерживает ли ведущее приложение метод **document.setSelectedDataAsync**.




```js
if (Office.context.document.setSelectedDataAsync)
{
    // Run code that uses document.setSelectedDataAsync.
}
```


## <a name="see-also"></a>См. также

- [XML-манифест надстройки Office](add-in-manifests.md)
- [Наборы обязательных элементов для надстроек Office](https://dev.office.com/reference/add-ins/requirement-sets/office-add-in-requirement-sets)
- [Word-Add-in-Get-Set-EditOpen-XML](https://github.com/OfficeDev/Word-Add-in-Get-Set-EditOpen-XML)