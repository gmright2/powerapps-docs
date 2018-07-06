---
title: Trim and TrimEnds functions | Microsoft Docs
description: Reference information, including syntax and an example, for the Trim and TrimEnds functions in PowerApps
documentationcenter: na
author: gregli-msft
manager: kfile
editor: ''
tags: ''

ms.service: powerapps
ms.devlang: na
ms.topic: reference
ms.component: canvas
ms.date: 09/09/2016
ms.author: gregli

---
# Trim and TrimEnds functions in PowerApps
Removes extra spaces from a string of text.

## Description
The **Trim** function removes all spaces from a string of text except for single spaces between words.  

The **TrimEnds** function removes all spaces from the start and end of a string of text but leaves spaces between words intact.

If you specify a single string of text, the return value for either function is the string with any extra spaces removed. If you specify a single-column [table](../working-with-tables.md) that contains strings, the return value is a single-column table of trimmed strings. If you have a multi-column table, you can shape it into a single-column table, as [working with tables](../working-with-tables.md) describes.

By trimming spaces between words, **Trim** is consistent with the function of the same name in Microsoft Excel. However, **TrimEnds** is consistent with programming tools that trim spaces only from the start and end of each string.

## Syntax
**Trim**( *String* )<br>**TrimEnds**( *String* )

* *String* - Required. The string of text to remove spaces from.

**Trim**( *SingleColumnTable* )<br>**TrimEnds**( *SingleColumnTable* )

* *SingleColumnTable* - Required. A single-column table of strings to remove spaces from.

## Example

| Formula | Description | Result |
| --- | --- | --- |
| **Trim(&nbsp;"&nbsp;&nbsp;&nbsp;Hello&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;World&nbsp;&nbsp;&nbsp;"&nbsp;)** |Removes all spaces from the start and end of a string and extra spaces from within the string. |"Hello World" |
| **TrimEnds(&nbsp;"&nbsp;&nbsp;&nbsp;Hello&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;World&nbsp;&nbsp;&nbsp;"&nbsp;)** |Removes all spaces from the start and end of a string. |"Hello&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;World" |

The following examples use a single-column collection, named **Spaces**, that contains these strings:

![](media/function-trim/input-strings.png)

To create this collection, set the **OnSelect** property of a **[Button](../controls/control-button.md)** control to this formula, open Preview mode, and then click or tap the button:
<br>**ClearCollect( Spaces, [ "&nbsp;&nbsp;&nbsp;Jane&nbsp;&nbsp;&nbsp;Doe&nbsp;&nbsp;&nbsp;", "&nbsp;&nbsp;&nbsp;&nbsp;Jack&nbsp;&nbsp;&nbsp;and&nbsp;&nbsp;&nbsp;Jill", "Already&nbsp;trimmed", "&nbsp;&nbsp;&nbsp;Venus,&nbsp;&nbsp;&nbsp;Earth,&nbsp;&nbsp;&nbsp;Mars&nbsp;&nbsp;", "Oil&nbsp;and&nbsp;Water&nbsp;&nbsp;&nbsp;" ] )**

| Formula | Description | Result |
| --- | --- | --- |
| **Trim(&nbsp;Spaces&nbsp;)** |Trims all spaces from the start and end of each string and extra spaces from within each string in the **Spaces** collection. |<style> img { max-width: none } </style> ![](media/function-trim/output-trim.png) |
| **TrimEnds(&nbsp;Spaces&nbsp;)** |Trims all spaces from the start and end of each string in the **Spaces** collection. |<style> img { max-width: none } </style> ![](media/function-trim/output-trimends.png) |

> [!NOTE]
> Extra spaces don't appear if you display a collection by clicking or tapping **Collections** on the **File** menu. To verify string length, use the **[Len](function-len.md)** function.
