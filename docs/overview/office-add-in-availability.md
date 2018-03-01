---
title: Доступность ведущих приложений и платформ для надстроек Office
description: 'Поддерживаемые наборы требований для Excel, Word, Outlook, PowerPoint и OneNote.'
ms.date: 12/01/2017
---

# <a name="office-add-in-host-and-platform-availability"></a>Доступность ведущих приложений и платформ для надстроек Office

Работа надстройки Office может зависеть от ведущего приложения Office, набора требований, элемента или версии API. В таблицах ниже представлены сведения о доступной платформе, точках расширения, наборах обязательных элементов API и стандартных наборах обязательных элементов API, которые в настоящее время поддерживаются для всех приложений Office. 

Символ * (звездочка) в ячейке таблицы указывает, что поддержка скоро появится. С наборами требований для Project и Access можно ознакомиться в статье [Стандартные наборы обязательных элементов для Office](https://dev.office.com/reference/add-ins/requirement-sets/office-add-in-requirement-sets).  

> [!NOTE]
> Номер сборки для набора Office 2016, установленного с помощью MSI, — 16.0.4266.1001. Эта версия содержит только набор обязательных элементов ExcelApi 1.1, WordApi 1.1 и стандартные наборы обязательных элементов API.

## <a name="excel"></a>Excel

<table style="width:80%">
  <tr>
    <th style="width:10%">Платформа</th>
    <th style="width:10%">Точки расширения</th> 
    <th style="width:20%">Наборы обязательных элементов API</th> 
    <th style="width:40%"><a href="https://dev.office.com/reference/add-ins/requirement-sets/office-add-in-requirement-sets"><b>Стандартные элементы API</b></a></th> 
  </tr>
  <tr>
    <td>Office Online</td>
    <td> - Область задач<br>
        - Контент<br>
        - <a href="https://dev.office.com/reference/add-ins/requirement-sets/add-in-commands-requirement-sets">Команды надстройки</a>
    </td>
    <td>
        - <a href="https://dev.office.com/reference/add-ins/requirement-sets/excel-api-requirement-sets">ExcelApi 1.1</a><br>
        - <a href="https://dev.office.com/reference/add-ins/requirement-sets/excel-api-requirement-sets">ExcelApi 1.2</a><br>
        - <a href="https://dev.office.com/reference/add-ins/requirement-sets/excel-api-requirement-sets">ExcelApi 1.3</a><br>
        - <a href="https://dev.office.com/reference/add-ins/requirement-sets/excel-api-requirement-sets">ExcelApi 1.4</a><br>
        - <a href="https://dev.office.com/reference/add-ins/requirement-sets/dialog-api-requirement-sets">DialogApi 1.1</a></td>
    <td>
        - BindingEvents<br>
        - DocumentEvents<br>
        - MatrixBindings<br>
        - MatrixCoercion<br>
        - TableBindings<br>
        - TableCoercion<br>
        - TextBindings<br>
        - CompressedFile<br>
        - Параметры<br>
        - TextCoercion</td>
  </tr>
  <tr>
    <td>Office 2013 для Windows</td>
    <td>
        - Область задач<br>
        - Контент</td>
    <td>  - <a href="https://dev.office.com/reference/add-ins/requirement-sets/dialog-api-requirement-sets">DialogApi 1.1</a></td>
    <td>
        - BindingEvents<br>
        - DocumentEvents<br>
        - MatrixBindings<br>
        - MatrixCoercion<br>
        - TableBindings<br>
        - TableCoercion<br>
        - TextBindings<br>
        - Параметры<br>
        - TextCoercion</td>
  </tr>
  <tr>
    <td>Office 2016 для Windows</td>
    <td>- Область задач<br>
        - Контент<br>
        - <a href="https://dev.office.com/reference/add-ins/requirement-sets/add-in-commands-requirement-sets">Команды надстроек</a></td>
    <td>- <a href="https://dev.office.com/reference/add-ins/requirement-sets/excel-api-requirement-sets">ExcelApi 1.1</a><br>
        - <a href="https://dev.office.com/reference/add-ins/requirement-sets/excel-api-requirement-sets">ExcelApi 1.2</a><br>
        - <a href="https://dev.office.com/reference/add-ins/requirement-sets/excel-api-requirement-sets">ExcelApi 1.3</a><br>
        - <a href="https://dev.office.com/reference/add-ins/requirement-sets/excel-api-requirement-sets">ExcelApi 1.4</a><br>
        - <a href="https://dev.office.com/reference/add-ins/requirement-sets/dialog-api-requirement-sets">DialogApi 1.1</a></td>
    <td>- BindingEvents<br>
        - DocumentEvents<br>
        - MatrixBindings<br>
        - MatrixCoercion<br>
        - TableBindings<br>
        - TableCoercion<br>
        - TextBindings<br>
        - Параметры<br>
        - TextCoercion</td> 
  </tr>
  <tr>
    <td>Office для iOS</td>
    <td>- Область задач<br>
        - Контент</td>
    <td>- <a href="https://dev.office.com/reference/add-ins/requirement-sets/excel-api-requirement-sets">ExcelApi 1.1</a><br>
        - <a href="https://dev.office.com/reference/add-ins/requirement-sets/excel-api-requirement-sets">ExcelApi 1.2</a><br>
        - <a href="https://dev.office.com/reference/add-ins/requirement-sets/excel-api-requirement-sets">ExcelApi 1.3</a><br>
        - <a href="https://dev.office.com/reference/add-ins/requirement-sets/dialog-api-requirement-sets">DialogApi 1.1</a></td>
    <td>- BindingEvents<br>
        - DocumentEvents<br>
        - MatrixBindings<br>
        - MatrixCoercion<br>
        - TableBindings<br>
        - TableCoercion<br>
        - TextBindings<br>
        - Параметры<br>
        - TextCoercion</td>
  </tr>
  <tr>
    <td>Office 2016 для Mac</td>
    <td>- Область задач<br>
        - Контент<br>
        - <a href="https://dev.office.com/reference/add-ins/requirement-sets/add-in-commands-requirement-sets">Команды надстроек</a></td>
    <td>- <a href="https://dev.office.com/reference/add-ins/requirement-sets/excel-api-requirement-sets">ExcelApi 1.1</a><br>
        - <a href="https://dev.office.com/reference/add-ins/requirement-sets/excel-api-requirement-sets">ExcelApi 1.2</a><br>
        - <a href="https://dev.office.com/reference/add-ins/requirement-sets/excel-api-requirement-sets">ExcelApi 1.3</a><br>
        - <a href="https://dev.office.com/reference/add-ins/requirement-sets/dialog-api-requirement-sets">DialogApi 1.1</a></td>
    <td>- BindingEvents<br>
        - DocumentEvents<br>
        - MatrixBindings<br>
        - MatrixCoercion<br>
        - TableBindings<br>
        - TableCoercion<br>
        - TextBindings<br>
        - TextCoercion</td>
  </tr>
</table>

<br/>

## <a name="outlook"></a>Outlook

<table style="width:80%">
  <tr>
    <th>Платформа</th>
    <th>Точки расширения</th> 
    <th>Наборы обязательных элементов API</th> 
    <th><a href="https://dev.office.com/reference/add-ins/requirement-sets/office-add-in-requirement-sets"><b>Стандартные элементы API</b></a></th> 
  </tr>
  <tr>
    <td>Office Online</td>
    <td> - Чтение почты<br>
      - Создание сообщения почты<br>
      - <a href="https://dev.office.com/reference/add-ins/requirement-sets/add-in-commands-requirement-sets">Команды надстроек</a></td>
    <td> - Mailbox 1.0<br>
      - Mailbox 1.1<br>
      - Mailbox 1.2<br>
      - Mailbox 1.3<br>
      - Mailbox 1.4<br>
      - Mailbox 1.5</td>
    <td>недоступен</td>
  </tr>
  <tr>
    <td>Office 2013 для Windows</td>
    <td> - Чтение почты<br>
      - Создание сообщения почты<br>
      - <a href="https://dev.office.com/reference/add-ins/requirement-sets/add-in-commands-requirement-sets">Команды надстроек</a></td>
    <td> - Mailbox 1.0<br>
      - Mailbox 1.1<br>
      - Mailbox 1.2<br>
      - Mailbox 1.3<br>
      - Mailbox 1.4</td>
    <td>недоступен</td>
  </tr>
  <tr>
    <td>Office 2016 для Windows</td>
    <td> - Чтение почты<br>
      - Создание сообщения почты<br>
      - <a href="https://dev.office.com/reference/add-ins/requirement-sets/add-in-commands-requirement-sets">Команды надстроек</a><br>
      - Модули</td>
    <td> - Mailbox 1.0<br>
      - Mailbox 1.1<br>
      - Mailbox 1.2<br>
      - Mailbox 1.3<br>
      - Mailbox 1.4<br>
      - Mailbox 1.5</td></td>
    <td>недоступен</td> 
  </tr>
  <tr>
    <td>Office для iOS</td>
    <td> - Чтение почты<br>
      - <a href="https://dev.office.com/reference/add-ins/requirement-sets/add-in-commands-requirement-sets">Команды надстроек</a></td>
    <td> - Mailbox 1.4</td>
    <td>недоступен</td>
  </tr>
  <tr>
    <td>Office 2016 для Mac</td>
    <td> - Чтение почты<br>
      - Создание сообщения почты<br>
      - <a href="https://dev.office.com/reference/add-ins/requirement-sets/add-in-commands-requirement-sets">Команды надстроек</a></td>
    <td> - Mailbox 1.0<br>
      - Mailbox 1.1<br>
      - Mailbox 1.2<br>
      - Mailbox 1.3<br>
      - Mailbox 1.4<br>
      - Mailbox 1.5</td>
    <td>недоступен</td>
  </tr>
  <tr>
    <td>Office для Android</td>
    <td> - Чтение почты<br>
      - <a href="https://dev.office.com/reference/add-ins/requirement-sets/add-in-commands-requirement-sets">Команды надстроек</a></td>
    <td> - Mailbox 1.4</td>
    <td>недоступен</td>
  </tr>
</table>

<br/>

## <a name="word"></a>Word

<table style="width:80%">
  <tr>
    <th>Платформа</th>
    <th>Точки расширения</th> 
    <th>Наборы обязательных элементов API</th> 
    <th><a href="https://dev.office.com/reference/add-ins/requirement-sets/office-add-in-requirement-sets"><b>Стандартные элементы API</b></a></th> 
  </tr> 
  </tr>
  <tr>
    <td>Office Online</td>
    <td> - Область задач<br>
         - <a href="https://dev.office.com/reference/add-ins/requirement-sets/add-in-commands-requirement-sets">Команды надстроек</a></td>
    <td> - <a href="https://dev.office.com/reference/add-ins/requirement-sets/word-api-requirement-sets">WordApi 1.1</a><br>
         - <a href="https://dev.office.com/reference/add-ins/requirement-sets/word-api-requirement-sets">WordApi 1.2</a><br>
         - <a href="https://dev.office.com/reference/add-ins/requirement-sets/word-api-requirement-sets">WordApi 1.3</a><br>
         - <a href="https://dev.office.com/reference/add-ins/requirement-sets/dialog-api-requirement-sets">DialogApi 1.1</a></td>
    <td> - BindingEvents<br>
         - CustomXmlParts<br>
         - MatrixBindings<br>
         - MatrixCoercion<br>
         - TableBindings<br>
         - TableCoercion<br>
         - TextBindings<br>
         - DocumentEvents<br>
         - TextFile<br>
         - ImageCoercion<br>
         - Параметры<br>
         - TextCoercion</td>
  </tr>
  <tr>
    <td>Office 2013 для Windows</td>
    <td> - Область задач</td>
    <td> - <a href="https://dev.office.com/reference/add-ins/requirement-sets/dialog-api-requirement-sets">DialogApi 1.1</a></td>
    <td> - BindingEvents<br>
         - CompressedFile<br>
         - CustomXmlPart<br>
         - DocumentEvents<br>
         - Файл<br>
         - HtmlCoercion<br>
         - ImageCoercion<br>
         - OoxmlCoercion<br>
         - TableBindings<br>
         - TableCoercion<br>
         - TextBindings<br>
         - TextFile<br>
         - Параметры<br>
         - TextCoercion<br>
         - MatrixCoercion<br>
         - Привязки матрицы</td>
  </tr>
  <tr>
    <td>Office 2016 для Windows</td>
    <td> - Область задач<br>
         - <a href="https://dev.office.com/reference/add-ins/requirement-sets/add-in-commands-requirement-sets">Команды надстроек</a></td>
    <td> - <a href="https://dev.office.com/reference/add-ins/requirement-sets/word-api-requirement-sets">WordApi 1.1</a><br>
        - <a href="https://dev.office.com/reference/add-ins/requirement-sets/word-api-requirement-sets">WordApi 1.2</a><br>
        - <a href="https://dev.office.com/reference/add-ins/requirement-sets/word-api-requirement-sets">WordApi 1.3</a><br>
        - <a href="https://dev.office.com/reference/add-ins/requirement-sets/dialog-api-requirement-sets">DialogApi 1.1</a></td>
    <td> - BindingEvents<br>
         - CompressedFile<br>
         - CustomXmlPart<br>
         - DocumentEvents<br>
         - Файл<br>
         - HtmlCoercion<br>
         - ImageCoercion<br>
         - OoxmlCoercion<br>
         - TableBindings<br>
         - TableCoercion<br>
         - TextBindings<br>
         - TextFile<br>
         - Параметры<br>
         - TextCoercion<br>
         - MatrixCoercion<br>
         - Привязки матрицы </td> 
  </tr>
  <tr>
    <td>Office для iOS</td>
    <td> - Область задач</td>
    <td> - <a href="https://dev.office.com/reference/add-ins/requirement-sets/word-api-requirement-sets">WordApi 1.1</a><br>
         - <a href="https://dev.office.com/reference/add-ins/requirement-sets/word-api-requirement-sets">WordApi 1.2</a><br>
         - <a href="https://dev.office.com/reference/add-ins/requirement-sets/word-api-requirement-sets">WordApi 1.3</a><br>
         - <a href="https://dev.office.com/reference/add-ins/requirement-sets/dialog-api-requirement-sets">DialogApi 1.1</a>
</td>
    <td> - BindingEvents<br>
         - CompressedFile<br>
         - CustomXmlPart<br>
         - DocumentEvents<br>
         - Файл<br>
         - HtmlCoercion<br>
         - ImageCoercion<br>
         - OoxmlCoercion<br>
         - TableBindings<br>
         - TableCoercion<br>
         - TextBindings<br>
         - TextFile<br>
         - Параметры<br>
         - TextCoercion<br>
         - MatrixCoercion<br>
         - Привязки матрицы </td> 
  </tr>
  <tr>
    <td>Office 2016 для Mac</td>
    <td> - Область задач<br>
         - <a href="https://dev.office.com/reference/add-ins/requirement-sets/add-in-commands-requirement-sets">Команды надстроек</a></td>
    <td> - <a href="https://dev.office.com/reference/add-ins/requirement-sets/word-api-requirement-sets">WordApi 1.1</a><br>
        - <a href="https://dev.office.com/reference/add-ins/requirement-sets/word-api-requirement-sets">WordApi 1.2</a><br>
        - <a href="https://dev.office.com/reference/add-ins/requirement-sets/word-api-requirement-sets">WordApi 1.3</a><br>
        - <a href="https://dev.office.com/reference/add-ins/requirement-sets/dialog-api-requirement-sets">DialogApi 1.1</a>
</td>
    <td> - BindingEvents<br>
         - CompressedFile<br>
         - CustomXmlPart<br>
         - DocumentEvents<br>
         - Файл<br>
         - HtmlCoercion<br>
         - ImageCoercion<br>
         - OoxmlCoercion<br>
         - TableBindings<br>
         - TableCoercion<br>
         - TextBindings<br>
         - TextFile<br>
         - Параметры<br>
         - TextCoercion<br>
         - MatrixCoercion<br>
         - Привязки матрицы </td> 
  </tr>
</table>

<br/>

## <a name="powerpoint"></a>PowerPoint

<table style="width:80%">
  <tr>
    <th>Платформа</th>
    <th>Точки расширения</th> 
    <th>Наборы обязательных элементов API</th> 
    <th><a href="https://dev.office.com/reference/add-ins/requirement-sets/office-add-in-requirement-sets"><b>Стандартные элементы API</b></a></th> 
  </tr> 
  </tr>
  <tr>
    <td>Office Online</td>
    <td> - Контент<br>
         - Область задач<br>
         - <a href="https://dev.office.com/reference/add-ins/requirement-sets/add-in-commands-requirement-sets">Команды надстроек</a></td>
    <td> - <a href="https://dev.office.com/reference/add-ins/requirement-sets/dialog-api-requirement-sets">DialogApi 1.1</a></td>
    <td> - ActiveView<br>
         - CompressedFile<br>
         - Файл<br>
         - Выделение<br>
         - Параметры<br>
         - TextCoercion<br>
         - ImageCoercion</td>
  </tr>
  <tr>
    <td>Office 2013 для Windows</td>
    <td> - Контент<br>
         - Область задач<br>
    </td>
    <td> - <a href="https://dev.office.com/reference/add-ins/requirement-sets/dialog-api-requirement-sets">DialogApi 1.1</a>
</td>
    <td> - ActiveView<br>
         - CompressedFile<br>
         - DocumentEvents<br>
         - Файл<br>
         - Выделение<br>
         - Параметры<br>
         - TextCoercion</td>
  </tr>
  <tr>
    <td>Office 2016 для Windows</td>
    <td> - Контент<br>
         - Область задач<br>
         - <a href="https://dev.office.com/reference/add-ins/requirement-sets/add-in-commands-requirement-sets">Команды надстроек</a></td>
    <td> - <a href="https://dev.office.com/reference/add-ins/requirement-sets/dialog-api-requirement-sets">DialogApi 1.1</a></td>
    <td> - ActiveView<br>
         - CompressedFile<br>
         - DocumentEvents<br>
         - Файл<br>
         - Выделение<br>
         - Параметры<br>
         - TextCoercion<br>
         - ImageCoercion</td>
  </tr>
  <tr>
    <td>Office для iOS</td>
    <td> - Контент<br>
         - Область задач</td>
    <td> - <a href="https://dev.office.com/reference/add-ins/requirement-sets/dialog-api-requirement-sets">DialogApi 1.1</a></td>
     <td> - ActiveView<br>
         - CompressedFile<br>
         - DocumentEvents<br>
         - Файл<br>
         - Выделение<br>
         - Параметры<br>
         - TextCoercion<br>
         - ImageCoercion</td>
  </tr>
  <tr>
    <td>Office 2016 для Mac</td>
    <td> - Контент<br>
         - Область задач<br>
         - <a href="https://dev.office.com/reference/add-ins/requirement-sets/add-in-commands-requirement-sets">Команды надстроек</a></td>
    <td> - <a href="https://dev.office.com/reference/add-ins/requirement-sets/dialog-api-requirement-sets">DialogApi 1.1</a></td>
    <td> - ActiveView<br>
         - CompressedFile<br>
         - DocumentEvents<br>
         - Файл<br>
         - Выделение<br>
         - Параметры<br>
         - TextCoercion<br>
         - ImageCoercion</td>
  </tr>
</table>

<br/>

## <a name="onenote"></a>OneNote

<table style="width:80%">
  <tr>
    <th>Платформа</th>
    <th>Точки расширения</th> 
    <th>Наборы обязательных элементов API</th> 
    <th><a href="https://dev.office.com/reference/add-ins/requirement-sets/office-add-in-requirement-sets"><b>Стандартные элементы API</b></a></th> 
  </tr> 
  </tr>
  <tr>
    <td>Office Online</td>
    <td> - Контент<br>
         - Область задач<br>
         - <a href="https://dev.office.com/reference/add-ins/requirement-sets/add-in-commands-requirement-sets">Команды надстроек</a></td>
    <td> - <a href="https://dev.office.com/reference/add-ins/requirement-sets/onenote-api-requirement-sets">OneNoteApi 1.1</a><br>
         - <a href="https://dev.office.com/reference/add-ins/requirement-sets/dialog-api-requirement-sets">DialogApi 1.1</a></td>
    <td> - DocumentEvents<br>
         - Параметры<br>
         - TextCoercion<br>
         - HtmlCoercion<br>
         - ImageCoercion</td>
  </tr>
  <tr>
    <td>Office 2013 для Windows</td>
    <td>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;* </td>
    <td>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;* </td>
    <td>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;* </td>
  </tr> 
  <tr>
    <td>Office 2016 для Windows</td>
    <td>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;* </td>
    <td>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;* </td>
    <td>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;* </td> 
  </tr>
  <tr>
    <td>Office для iOS</td>
    <td>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;* </td>
    <td>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;* </td>
    <td>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;* </td>
  </tr>
  <tr>
    <td>Office 2016 для Mac</td>
    <td>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;* </td>
    <td>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;* </td>
    <td>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;* </td>
  </tr>
</table>

<br/>

\* = поддержка скоро появится. 

## <a name="see-also"></a>См. также

- [Обзор платформы надстроек Office](office-add-ins.md)
- [Стандартные наборы обязательных элементов API](https://dev.office.com/reference/add-ins/requirement-sets/office-add-in-requirement-sets)
- [Наборы обязательных элементов для команд надстроек](https://dev.office.com/reference/add-ins/requirement-sets/add-in-commands-requirement-sets)
- [Справка по API JavaScript для Office](https://dev.office.com/reference/add-ins/javascript-api-for-office)
