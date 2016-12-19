---
title: "在日期和时间选取器控件中使用回调字段 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "DTN_FORMATQUERY"
  - "DTN_FORMAT"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CDateTimeCtrl 类中的回调字段"
  - "CDateTimeCtrl 类, 回调字段"
  - "CDateTimeCtrl 类, 处理 DTN_FORMAT 和 DTN_FORMATQ"
  - "DateTimePicker 控件 [MFC]"
  - "DateTimePicker 控件 [MFC], 回调字段"
  - "DTN_FORMAT 通知"
  - "DTN_FORMATQUERY 通知"
ms.assetid: 404f4ba9-cba7-4718-9faa-bc6b274a723f
caps.latest.revision: 11
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 在日期和时间选取器控件中使用回调字段
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

除了定义日期和时间选择器字段的标准格式字符之外，您还可以通过指定自定义格式字符串的一些部分自定义输出作为回调字段。  声明字段，回调包含一个或多个“X”字符 \(ASCII 代码 88\) 中的任何地方。格式字符串主体中。  例如，以下字符串““有：“yy”\/“MM”\/“dd”\(日“X”\)”“\)，显示当前日期和时间值的选取器控件作为使用后跟的年份，日期和最后年的日期。  
  
> [!NOTE]
>  X's 数在回调字段不对应于要显示的字符数。  
  
 可以区分自定义字符串的多种回调字段之间通过重复“X”字符。  因此，XXddddMMMdd 格式字符串“，“yyyXXX”包含两个字段，回调“XX”和“”等。  
  
> [!NOTE]
>  回调字段视为有效的字段，因此，必须准备处理应用程序的 **DTN\_WMKEYDOWN** 通知消息。  
  
 实现和日期时间选择器控件的回调字段由三部分组成：  
  
-   初始化自定义格式字符串  
  
-   处理 **DTN\_FORMATQUERY** 通知  
  
-   处理 **DTN\_FORMAT** 通知  
  
## 初始化自定义格式字符串  
 初始化用名为的自定义字符串设置为 `CDateTimeCtrl::SetFormat`。  有关更多信息，请参见 [在使用日期和时间选择器控件的自定义格式字符串](../mfc/using-custom-format-strings-in-a-date-and-time-picker-control.md)。  将自定义格式字符串的一种常用排列中的视图类包含的对话框类或 `OnInitialUpdate` 函数的 `OnInitDialog` 函数。  
  
## 处理 DTN\_FORMATQUERY 通知  
 当分析控件格式字符串，回调遇到字段时应用程序发送 **DTN\_FORMAT** 和 **DTN\_FORMATQUERY** 则通知消息。  回调字段字符串包含通知，以便可以确定字段回调查询。  
  
 **DTN\_FORMATQUERY** 通知发送回调检索在当前字段将显示字符串的像素的最大允许大小。  
  
 To properly calculate this value, you must calculate the height and width of the string, to be substituted for the field, using the control's display font.  字符串的实际计算方便地实现与 [GetTextExtentPoint32](http://msdn.microsoft.com/library/windows/desktop/dd144938) Win32 函数的调用。  范围是一个标识，将值传递回应用程序并退出处理程序函数。  
  
 下面的示例是所提供回调字符串的大小的方法：  
  
 [!code-cpp[NVC_MFCControlLadenDialog#8](../mfc/codesnippet/CPP/using-callback-fields-in-a-date-and-time-picker-control_1.cpp)]  
  
 一次当前回调字段的大小计算，您必须提供字段的值。  它会在 **DTN\_FORMAT** 通知的处理程序执行。  
  
## 处理 DTN\_FORMAT 通知  
 应用程序使用 **DTN\_FORMAT** 通知请求被替换的字符串。  下面的示例对y一种可能方法进行了演示。  
  
 [!code-cpp[NVC_MFCControlLadenDialog#9](../mfc/codesnippet/CPP/using-callback-fields-in-a-date-and-time-picker-control_2.cpp)]  
  
> [!NOTE]
>  在 **NMDATETIMEFORMAT** 结构的指针转换通过通知处理程序的第一个参数。查找相应的类型。  
  
## 请参阅  
 [使用 CDateTimeCtrl](../mfc/using-cdatetimectrl.md)   
 [控件](../mfc/controls-mfc.md)