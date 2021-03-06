---
title: Работа с содержимым страницы в OneNote
description: ''
ms.date: 12/04/2017
ms.openlocfilehash: d05f251a798a7670983187bfa4c80140b30f6147
ms.sourcegitcommit: c72c35e8389c47a795afbac1b2bcf98c8e216d82
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/23/2018
ms.locfileid: "19438860"
---
# <a name="work-with-onenote-page-content"></a>Работа с содержимым страницы в OneNote 

В API JavaScript для надстроек OneNote содержимое страницы представлено указанной ниже объектной моделью.

  ![Схема объектной модели страницы OneNote](../images/one-note-om-page.png)

- Объект Page содержит коллекцию объектов PageContent.
- Объект PageContent содержит контент типов Outline, Image или Other.
- Объект Outline содержит коллекцию объектов Paragraph.
- Объект Paragraph содержит контент типов RichText, Image, Table или Other.

Чтобы создать пустую страницу OneNote, воспользуйтесь одним из указанных ниже методов.

- [Section.addPage](https://dev.office.com/reference/add-ins/onenote/section#addpagetitle-string)
- [Page.insertPageAsSibling](https://dev.office.com/reference/add-ins/onenote/page#insertpageassiblinglocation-string-title-string)

Затем используйте методы в указанных ниже объектах для работы с содержимым страницы, например Page.addOutline и Outline.appendHtml. 

- [Страница](https://dev.office.com/reference/add-ins/onenote/page)
- [Структура](https://dev.office.com/reference/add-ins/onenote/outline)
- [Абзац](https://dev.office.com/reference/add-ins/onenote/paragraph)

Для представления содержимого и структуры страницы OneNote используется HTML. Для создания или обновления содержимого страницы поддерживается только подмножество HTML, как описано ниже.

## <a name="supported-html"></a>Поддерживаемые элементы HTML

Для создания и обновления содержимого страницы в API JavaScript для надстроек OneNote используются указанные ниже элементы HTML.

- `<html>`, `<body>`, `<div>`, `<span>`, `<br/>` 
- `<p>`
- `<img>`
- `<a>`
- `<ul>`, `<ol>`, `<li>` 
- `<table>`, `<tr>`, `<td>`
- `<h1>` ... `<h6>`
- `<b>`, `<em>`, `<strong>`, `<i>`, `<u>`, `<del>`, `<sup>`, `<sub>`, `<cite>`

## <a name="accessing-page-contents"></a>Доступ к содержимому страницы

Через `Page#load` доступ можно получить только к *содержимому активной страницы*. Чтобы изменить активную страницу, вызовите команду `navigateToPage($page)`.

Метаданные, например "Название", можно запросить для любой страницы.

## <a name="see-also"></a>См. также

- [Обзор создания кода с помощью API JavaScript для OneNote](onenote-add-ins-programming-overview.md)
- [Справочник по API JavaScript для OneNote](https://dev.office.com/reference/add-ins/onenote/onenote-add-ins-javascript-reference)
- [Пример надстройки Rubric Grader](https://github.com/OfficeDev/OneNote-Add-in-Rubric-Grader)
- [Обзор платформы надстроек Office](../overview/office-add-ins.md)
