---
title: ?????????? ???????? ?????? ? ????????? Excel
description: ''
ms.date: 04/13/2018
ms.openlocfilehash: 8e5f09f1c566103f34ad584885769229c17ab1f7
ms.sourcegitcommit: c72c35e8389c47a795afbac1b2bcf98c8e216d82
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/23/2018
---
# <a name="add-data-validation-to-excel-ranges-preview"></a>?????????? ???????? ?????? ? ????????? Excel (??????????????? ??????)

> [!NOTE]
> ???? API ???????? ?????? ???????? ??????????????? ???????, ??? ?? ????????????? ?? ?????? ????????? ????-?????? ?????????? JavaScript ??? Office. URL-?????: https://appsforoffice.microsoft.com/lib/beta/hosted/office.js. ???? ?? ??????????? TypeScript ??? ???????? ???? ?????????? ???? ??????????? ???? TypeScript ??? IntelliSense, ?????????????? https://appsforoffice.microsoft.com/lib/beta/hosted/office.d.ts.

?????????? JavaScript Excel ????????????? API, ??????????? ????? ?????????? ????????? ?????????????? ???????? ?????? ? ???????, ???????, ?????? ? ?????? ????????? ? ?????. ??? ???????????? ? ????????? ? ????????????? ???????? ?????? ???????? ????????? ?????? ? ???, ??? ???????????? ????????? ???????? ?????? ????? ????????? Excel:

- [?????????? ???????? ?????? ? ???????](https://support.office.com/en-us/article/Apply-data-validation-to-cells-29FECBCC-D1B9-42C1-9D76-EFF3CE5F7249)
- [????????? ? ???????? ??????](https://microsoft.sharepoint.com/:p:/r/teams/oext/_layouts/15/Doc.aspx?sourcedoc=%7B51143964-d52c-429d-bfac-c7495473d536%7D&action=edit)
- [???????? ? ??????? ???????? ?????? ? Excel](https://support.microsoft.com/en-us/help/211485/description-and-examples-of-data-validation-in-excel)

## <a name="programmatic-control-of-data-validation"></a>??????????? ??????? ?????????? ????????? ??????

???????? `Range.dataValidation`, ??????? ????????? ?????? [DataValidation](https://dev.office.com/reference/add-ins/excel/datavalidation), ???????? ?????? ????? ??? ???????????? ?????????? ????????? ?????? ? Excel. ?????????? ???? ??????? ??????? `DataValidation`:

- `rule` ? ??????????, ????? ?????? ??? ????????? ???????? ????????????. ??. [DataValidationRule](https://dev.office.com/reference/add-ins/excel/datavalidationrule).
- `errorAlert` ? ?????????, ?????????? ?? ??????, ???? ???????????? ?????? ???????? ??????, ? ?????????? ?????, ???????? ? ????? ??????????, ????????, **Informational** (??????????????), **Warning** (??????????????), ? ????? **Stop** (?????????). ??. [DataValidationErrorAlert](https://dev.office.com/reference/add-ins/excel/datavalidationerroralert).
- `prompt` ? ?????????, ?????????? ?? ?????????, ????? ???????????? ??????? ?????? ???? ?? ????????, ? ?????????? ????? ?????????. ??. [DataValidationPrompt](https://dev.office.com/reference/add-ins/excel/datavalidationprompt).
- `ignoreBlanks` ? ?????????, ??????????? ?? ??????? ???????? ?????? ? ?????? ??????? ? ?????????. ???????? ?? ?????????: `true`.
- `type` ? ????????????? ???? ???????? "?????? ??? ??????", ????????, WholeNumber, Date, TextLength ? ?. ?. ??? ???????? ??????????????? ?????? ??? ????????? `rule`.

> [!NOTE]
> ??????????? ?????????? ???????? ?????? ????? ???? ??? ??, ??? ? ??????????? ???????. ????????, ???????? ????????, ??? ???????? ?????? ??????????? ?????? ? ??? ??????, ???? ???????????? ??????????????? ?????? ???????? ? ?????? ??? ???????? ? ????????? ?????? ?? ??????? ????? ? ????? ? ?????????? ??????? **????????**. ???? ???????????? ???????? ?????? ? ????????? ??????? ??????? ? ???????? ? ????????? ??????, ???????? ?? ???????????.

### <a name="creating-validation-rules"></a>???????? ?????? ????????

????? ???????? ???????? ?????? ? ????????, ? ??? ????? ???????? ???????? `rule` ??????? `DataValidation` ? `Range.dataValidation`. ??? ???? ???????????? ?????? [DataValidationRule](https://dev.office.com/reference/add-ins/excel/datavalidationrule), ??????? ????? ???? ?????????????? ???????. *? ????? ??????? `DataValidationRule` ????? ?????????????? ?? ????? ?????? ?? ???? ???????.* ?????????? ???????? ?????????? ??? ????????.

#### <a name="basic-and-datetime-validation-rule-types"></a>???? ?????? ???????? Basic ? DateTime

?????? ??? ???????? `DataValidationRule` (?. ?. ???? ?????? ????????) ? ???????? ?????? ???????? ????????? ?????? [BasicDataValidation](https://dev.office.com/reference/add-ins/excel/basicdatavalidation).

- `wholeNumber` ? ??????? ????? ????? ? ?????????? ? ?????? ?????????, ???????????? ? ??????? `BasicDataValidation`.
- `decimal` ? ??????? ?????????? ????? ? ?????????? ? ?????? ???????? ????????, ???????????? ? ??????? `BasicDataValidation`.
- `textLength` ? ????????? ???????? ???????? ??????? `BasicDataValidation` ? *?????* ???????? ??????.

??? ?????? ???????? ??????? ????????. ???????? ???????? ?? ??????????? ????? ????:

-  `operator` ? ??? ???????? ???????? "GreaterThan". ?????? ???, ????? ?? ??????????? ???????? ????????, ????????, ??????? ???????????? ???????? ?????? ? ??????, ? ??? ????? ???????, ? ????????, ????????? ? `formula1` ? ?????? ???????. ????? ???????, ??? ??????? ?????????????, ??? ????????????? ?????? ????? ?????, ??????? ?????? 0. 
-  `formula1` ? ?????? ???????? ?????. ???? ?? ????? ????????? ???? ?? ?? ??????, ????? ?????? ???? ????????, ??? ???? ????? ???????????? ??????? Excel (??? ??????). ????????, "= A3" ? "= SUM (A4, B5)" ????? ????? ???? ?????????? `formula1`.

```js
Excel.run(function (context) {
    var sheet = context.workbook.worksheets.getActiveWorksheet();
    var range = sheet.getRange("B2:C5");
   
    range.dataValidation.rule = {
            wholeNumber: {
                formula1: 0,
                operator: "GreaterThan"
            }
        };

    return context.sync();
})
```

???????? ?????? ???????? ?????????? ??. ? ?????? [BasicDataValidation](https://dev.office.com/reference/add-ins/excel/basicdatavalidation). 

???? ????? ??? ????????? ?????????: "Between" ? "NotBetween". ????? ?? ????????????, ?????????? ??????? ?????????????? ???????? `formula2`. ???????? `formula1` ? `formula2` ? ?????????????? ????????. ????????, ??????? ???????????? ?????? ? ??????, ???????? ??????? (???????????) ?????????. ???? ???????? ?????? ????????????? ????????? "Between":

```js
Excel.run(function (context) {
    var sheet = context.workbook.worksheets.getActiveWorksheet();
    var range = sheet.getRange("B2:C5");
   
    range.dataValidation.rule = {
            decimal: {
                formula1: 0,
                formula2: 100,
                operator: "Between"
            }
        };

    return context.sync();
})
```

????????? ??? ???????? ??????? ? ???????? ?????? ???????? ????????? ?????? [DateTimeDataValidation](https://dev.office.com/reference/add-ins/excel/basicdatavalidation).

- `date`
- `time`

?????? `DateTimeDataValidation` ?????????????? ?????????? `BasicDataValidation`: ?? ???????? ???????? `formula1`, `formula2` ? `operator` ? ???????????? ????? ?? ???????. ??????? ??????? ? ???, ??? ????? ? ????????? ??????? ???????????? ??????, ?? ????? ?????? ?????? [? ????? ? ???????? ?? ISO 8606](https://www.iso.org/iso-8601-date-and-time-format.html) (??? ??????? Excel). ???? ???????? ??????, ? ??????? ?????????? ?????????? ???????? ??? ??? ?????? ?????? ?????? 2018 ????. 

```js
Excel.run(function (context) {
    var sheet = context.workbook.worksheets.getActiveWorksheet();
    var range = sheet.getRange("B2:C5");
   
    range.dataValidation.rule = {
            date: {
                formula1: "2018-04-01",
                formula2: "2018-04-08",
                operator: "Between"
            }
        };

    return context.sync();
})
```

#### <a name="list-validation-rule-type"></a>??? ??????? ???????? List

??????????? ???????? `list` ??? ??????? `DataValidationRule` ??? ???????? ????, ??? ??????????? ??????????? ???????? ???????? ?? ????????????? ??????. ???? ???????? ??????. ???????? ???????? ?? ??????????? ????? ????:

- ??????????????, ??? ?????????? ???? ? ?????? "Names", ? ???????? ? ????????? "A1: A3" ???????? ???????.
- ???????? `source`?????? ?????? ?????????? ????????. ??? ???????? ???????? ? ???????. ????? ????? ????????? ?????? ? ?????????????-????????, ????????, "???, ????, ???". 
- ???????? `inCellDropDown` ??????????, ????? ?? ?????????? ??????? ?????????? ?????????? ? ??????, ????? ???????????? ?? ???????. ???? ??????????? ???????? `true`, ???????? ?????????? ?????? ???????? ?? `source`.

```js
Excel.run(function (context) {
    var sheet = context.workbook.worksheets.getActiveWorksheet();
    var range = sheet.getRange("B2:C5");   
    var nameSourceRange = context.workbook.worksheets.getItem("Names").getRange("A1:A3");

    range.dataValidation.rule = {
        list: {
            inCellDropDown: true,
            source: nameSourceRange
        }
    };

    return context.sync();
})
```

#### <a name="custom-validation-rule-type"></a>??? ??????? ???????? Custom

??????????? ???????? `custom` ??? ??????? `DataValidationRule`, ????? ??????? ????????????? ??????? ????????. ???? ???????? ??????. ???????? ???????? ?? ??????????? ????? ????:

- ??????????????, ??? ?? ????? ??????????? ??????? ? ????? ?????????, A ? B: **Athlete Name** (??? ??????????) ? **Comments** .
- ??? ?????????? ??????????? ? ??????? **???????????** ??? ?????????? ????????????? ??????, ??????? ???????? ??? ??????????.
- `SEARCH(A2,B2)` ?????????? ????????? ??????? ?????? ? A2 ? ?????? ? B2. ???? A2 ?? ?????????? ? B2, ????? ?? ????????????. `ISNUMBER()` ?????????? ?????????? ????????. ????, ???????? `formula` ???????, ??? ?????? ? ???????**Comment** ?????????????, ???? ? ??? ?? ???????? ?????? ?? ??????? **??? ??????**.

```js
Excel.run(function (context) {
    var sheet = context.workbook.worksheets.getActiveWorksheet();
    var range = sheet.getRange("B2:C5");   
    var commentsRange = sheet.tables.getItem("AthletesTable").columns.getItem("Comments").getDataBodyRange();

    commentsRange.dataValidation.rule = {
            custom: {
                formula: "=NOT(ISNUMBER(SEARCH(A2,B2)))"
            }
        };

    return context.sync();
})
```

### <a name="create-validation-error-alerts"></a>???????? ?????????????? ?? ??????? ????????

?? ?????? ??????? ????????????? ?????????????? ?? ??????, ??????? ??????????, ????? ???????????? ???????? ?????? ???????????? ?????? ? ??????. ???? ???????? ??????? ??????. ???????? ???????? ?? ??????????? ????? ????:

- ???????? `style` ??????????, ????? ????????? ??????? ????????????: alert (??????????), warning (??????????????) ??? "stop" (????-??????????). ?????? `Stop` ????????????? ????????????? ?????????? ????????????? ???????????? ??????. ??????????? ???? `Warning` ? `Information` ???????? ???????????, ??????? ????????? ???????????? ??? ????? ?????? ???????????? ??????.
- ???????? `showAlert` ?? ????????? ????? ???????? `true`. ??? ????????, ??? ? ??????? ?????????? Excel ???????? ????? ?????????? (???? `Stop`), ???? ?? ?? ??????? ????????????? ??????????, ??????? ???? ????????????? `showAlert` ???????? `false`, ???? ????????????? ????????????? ?????????, ????????? ? ?????. ???? ??? ????????????? ????????????? ????????? ? ?????????.


```js
Excel.run(function (context) {
    var sheet = context.workbook.worksheets.getActiveWorksheet();
    var range = sheet.getRange("B2:C5");
   
    range.dataValidation.errorAlert = {
            message: "Sorry, only positive whole numbers are allowed",
            showAlert: true, // default is 'true'
            style: "Stop", // other possible values: Warning, Information
            title: "Negative or Decimal Number Entered"
        };
    
    // Set range.dataValidation.rule and optionally .prompt here.

    return context.sync();
})
```

?????????????? ???????? ??. ? ?????? [DataValidationErrorAlert](https://dev.office.com/reference/add-ins/excel/datavalidationerroralert).

### <a name="create-validation-prompts"></a>???????? ???????? ????????

?? ?????? ??????? ?????????, ??????? ??????????, ????? ???????????? ??????? ?????? ???? ?? ??????, ? ??????? ??????????? ???????? ??????, ??? ???????? ??. ???? ???????? ??????.

```js
Excel.run(function (context) {
    var sheet = context.workbook.worksheets.getActiveWorksheet();
    var range = sheet.getRange("B2:C5");
   
    range.dataValidation.prompt = {
            message: "Please enter a positive whole number.",
            showPrompt: true, // default is 'false'
            title: "Positive Whole Numbers Only."
        };
    
    // Set range.dataValidation.rule and optionally .errorAlert here.

    return context.sync();
})
```

?????????????? ???????? ??. ? ?????? [DataValidationPrompt](https://dev.office.com/reference/add-ins/excel/datavalidationprompt).

### <a name="remove-data-validation-from-a-range"></a>???????? ???????? ?????? ?? ?????????

????? ??????? ???????? ?????? ?? ?????????, ???????? ????? [Range.dataValidation.clear ()](https://dev.office.com/reference/add-ins/excel/datavalidation#clear).

```js
myrange.dataValidation.clear()
```

?? ???????????, ????? ????????, ??????? ?? ????????, ????????? ???????? ? ??????????, ??? ???????? ?? ???????? ???????? ??????. ???? ??? ?? ?????????, ????????? ?????? ?? ???? ??????????, ??????? ?????????. 

> [!NOTE]
> ??????? ???????? ?????? ?? ????????? ????? ???????????????? ?? ????? ???????? ??????, ??????? ???????????? ??????? ??????? ? ????????.

## <a name="see-also"></a>??. ?????

- [???????? ??????? API JavaScript ??? Excel](excel-add-ins-core-concepts.md)
- [?????? DataValidation (API JavaScript ??? Excel)](https://dev.office.com/reference/add-ins/excel/datavalidation)
- [?????? ???????? (API JavaScript ??? Excel)](https://dev.office.com/reference/add-ins/excel/range)



 