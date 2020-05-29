---
title: 在日期和时间选取器控件中使用回调字段
ms.date: 11/04/2016
f1_keywords:
- DTN_FORMATQUERY
- DTN_FORMAT
helpviewer_keywords:
- DateTimePicker control [MFC], callback fields
- callback fields in CDateTimeCtrl class [MFC]
- CDateTimeCtrl class [MFC], callback fields
- CDateTimeCtrl class [MFC], handling DTN_FORMAT and DTN_FORMATQ
- DTN_FORMATQUERY notification [MFC]
- DTN_FORMAT notification [MFC]
- DateTimePicker control [MFC]
ms.assetid: 404f4ba9-cba7-4718-9faa-bc6b274a723f
ms.openlocfilehash: 50350e51b6747d8c010db9d0dcaa9dff2e56e1f3
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366559"
---
# <a name="using-callback-fields-in-a-date-and-time-picker-control"></a>在日期和时间选取器控件中使用回调字段

除了定义日期和时间选取器字段的标准格式字符之外，您还可以通过将自定义格式字符串的某些部分指定为回调字段来自定义您的输出。 若要声明回调字段，请在格式字符串主体中的任何位置包含一个或多个“X”字符（ASCII 代码 88）。 例如，以下字符串“Today is: 'yy'/'MM'/'dd' (Day 'X')'”会使日期和时间选取器控件将当前值按照“年、月、日和年积日”格式来显示。

> [!NOTE]
> 回调字段中 X 的数量并不对应于将要显示的字符数。

您可以通过重复“X”字符在自定义字符串中区分多个回调字段。 因此，格式字符串“XXddddMMMdd', 'yyyXXX”包含两个唯一的回调字段“XX”和“XXX”。

> [!NOTE]
> 回调字段被视为有效字段，因此必须准备处理DTN_WMKEYDOWN通知消息。

在日期和时间选取器控件中实现回调字段的过程分为三个部分：

- 初始化自定义格式字符串

- 处理 DTN_FORMATQUERY 通知

- 处理 DTN_FORMAT 通知

## <a name="initializing-the-custom-format-string"></a>初始化自定义格式字符串

通过调用 `CDateTimeCtrl::SetFormat` 初始化自定义字符串。 有关详细信息，请参阅[在日期和时间选取器控件中使用自定义格式字符串](../mfc/using-custom-format-strings-in-a-date-and-time-picker-control.md)。 设置自定义格式字符串的一个常见位置是在所属对话框类的 `OnInitDialog` 函数或所属视图类的 `OnInitialUpdate` 函数中。

## <a name="handling-the-dtn_formatquery-notification"></a>处理 DTN_FORMATQUERY 通知

当控件分析格式字符串并遇到回调字段时，应用程序会发送 DTN_FORMAT 和 DTN_FORMATQUERY 通知消息。 回调字段字符串包含在通知中，以便可以确定正在查询的回调字段。

发送 DTN_FORMATQUERY 通知以检索将显示在当前回调字段中的字符串的最大允许大小（以像素为单位）。

若要正确地计算此值，则必须使用控件的显示字体计算将替换该字段的字符串高度和宽度。 使用调用[GetText范围Point32 Win32](/windows/win32/api/wingdi/nf-wingdi-gettextextentpoint32w)函数，可以轻松实现字符串的实际计算。 确定大小之后，将该值传递回应用程序并退出处理程序函数。

以下示例是一种提供回调字符串的大小的方法：

[!code-cpp[NVC_MFCControlLadenDialog#8](../mfc/codesnippet/cpp/using-callback-fields-in-a-date-and-time-picker-control_1.cpp)]

计算了当前回调字段的大小之后，您必须提供该字段的值。 这在DTN_FORMAT通知的处理程序中完成。

## <a name="handling-the-dtn_format-notification"></a>处理 DTN_FORMAT 通知

应用程序使用 DTN_FORMAT 通知来请求将用来替换的字符串。 以下示例演示了一种可能的方法：

[!code-cpp[NVC_MFCControlLadenDialog#9](../mfc/codesnippet/cpp/using-callback-fields-in-a-date-and-time-picker-control_2.cpp)]

> [!NOTE]
> 通过将通知处理程序的第一个参数强制转换到正确的类型，找到指向**NMDATETIME信息**结构的指针。

## <a name="see-also"></a>另请参阅

[使用 CDateTimeCtrl](../mfc/using-cdatetimectrl.md)<br/>
[控件](../mfc/controls-mfc.md)
