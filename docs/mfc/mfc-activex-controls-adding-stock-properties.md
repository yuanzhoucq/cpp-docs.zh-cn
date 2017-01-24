---
title: "MFC ActiveX 控件：添加常用属性 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "BackColor 属性"
  - "ForeColor 属性"
  - "前景色"
  - "前景色, ActiveX 控件"
  - "MFC ActiveX 控件, 属性"
  - "属性 [MFC], 添加常用"
ms.assetid: 8b98c8c5-5b69-4366-87bf-0e61e6668ecb
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# MFC ActiveX 控件：添加常用属性
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

常用属性与自定义属性不同它们由类已经实现 `COleControl`。  `COleControl` 包含预定义的成员函数共同支持的控件属性。  某些包含通用控件的标题和前景色和背景色。  有关其他常用属性的信息后，请参见 [添加属性向导支持的常用属性](#_core_stock_properties_supported_by_classwizard) 本文。  常用属性的计划映射条目按 **DISP\_STOCKPROP**始终前缀。  
  
 本文介绍如何添加常用属性 \(在此例，标题\) 为 ActiveX 控件使用"添加属性向导并说明发生的代码更改。  主题包括：  
  
-   [使用添加属性向导的自定义属性](#_core_using_classwizard_to_add_a_stock_property)  
  
-   [添加属性向导"提供常用属性更改](#_core_classwizard_changes_for_stock_properties)  
  
-   [添加属性向导支持的常用属性](#_core_stock_properties_supported_by_classwizard)  
  
-   [常用属性和通知](#_core_stock_properties_and_notification)  
  
-   [颜色属性](#_core_color_properties)  
  
    > [!NOTE]
    >  Visual Basic 自定义控件通常具有属性 \(顶部，左侧，宽度、高度、对齐、、、、TabStop TabIndex 标记名称和父级。  ActiveX 控件容器，但是，将负责实现这些控件的属性。和 ActiveX 控件不应支持这些属性。  
  
##  <a name="_core_using_classwizard_to_add_a_stock_property"></a> 使用添加属性向导的自定义属性  
 因为属性的 `COleControl`支持，会自动处理添加常用属性比添加自定义属性需要更少的代码。  下面的过程演示添加股票的 caption 属性到 ActiveX 控件框架，也可用于添加其他常用属性。  标题并重写选定的常用属性名。  
  
#### 使用"添加属性向导，将库存 caption 属性  
  
1.  加载控件项目。  
  
2.  在类视图中，展开控件的库节点。  
  
3.  右击控件的接口节点 \(库节点的第二个节点\) ，打开快捷菜单。  
  
4.  从快捷菜单中，单击**“添加”**，然后单击**“添加属性”**。  
  
     这会打开 [添加属性向导](../ide/names-add-property-wizard.md)。  
  
5.  在 **属性名** 框中，单击 **标题**。  
  
6.  单击**“完成”**。  
  
##  <a name="_core_classwizard_changes_for_stock_properties"></a> 添加属性向导"提供常用属性更改  
 由于支持 `COleControl` 常用属性，添加属性向导既不将类声明更改；它将属性添加到计划映射。  添加属性向导以下行添加到的控件映射计划，实现 \(.cpp\) 文件中：  
  
 [!code-cpp[NVC_MFC_AxUI#22](../mfc/codesnippet/CPP/mfc-activex-controls-adding-stock-properties_1.cpp)]  
  
 下列代码行添加到控件的 .IDL 文件：  
  
 [!code-cpp[NVC_MFC_AxUI#23](../mfc/codesnippet/CPP/mfc-activex-controls-adding-stock-properties_2.idl)]  
  
 此行将标题属性特定 ID.  请注意属性绑定，再修改值之前从数据库请求权限。  
  
 这使标题属性可用控件的用户。  若要使用常用属性的值，请访问基类的 `COleControl` 成员变量或成员函数。  有关这些变量成员和成员函数的更多信息，请参见下部分，"添加属性向导"支持的常用属性。  
  
##  <a name="_core_stock_properties_supported_by_classwizard"></a> 添加属性向导支持的常用属性  
 `COleControl` 类提供了常用属性。  可以使用添加"添加属性向导"您需的属性。  
  
|Property|计划映射项|如何访问此值|  
|--------------|-----------|------------|  
|**外观**|**DISP\_STOCKPROP\_APPEARANCE \(\)**|访问的值为 **m\_sAppearance**。|  
|`BackColor`|**DISP\_STOCKPROP\_BACKCOLOR \(\)**|值访问通过调用 `GetBackColor`。|  
|`BorderStyle`|**DISP\_STOCKPROP\_BORDERSTYLE \(\)**|访问的值为 **m\_sBorderStyle**。|  
|**Caption**|**DISP\_STOCKPROP\_CAPTION \(\)**|值访问通过调用 `InternalGetText`。|  
|**Enabled**|**DISP\_STOCKPROP\_ENABLED \(\)**|访问的值为 **m\_bEnabled**。|  
|**字体**|**DISP\_STOCKPROP\_FONT \(\)**|用于条件参见文章 [MFC ActiveX 控件：使用字体](../mfc/mfc-activex-controls-using-fonts.md)。|  
|`ForeColor`|**DISP\_STOCKPROP\_FORECOLOR \(\)**|值访问通过调用 `GetForeColor`。|  
|**hWnd**|**DISP\_STOCKPROP\_HWND\( \)**|访问值为 `m_hWnd`。|  
|**Text**|**DISP\_STOCKPROP\_TEXT\( \)**|值访问通过调用 `InternalGetText`。  此属性与 **标题**，除属性名。|  
|**ReadyState**|**DISP\_STOCKPROP\_READYSTATE\(\)**|访问的值作为 m\_lReadyState 或 `GetReadyState`|  
  
##  <a name="_core_stock_properties_and_notification"></a> 常用属性和通知  
 最常用属性可以重写通知的函数。  例如，每当 `BackColor`，属性已更改，则 `OnBackColorChanged` 函数 \(控件类的成员函数\) 调用。  默认实现\(在 `COleControl` 中\)调用`InvalidateControl`。  重写此函数是要执行其他操作来响应此情况。  
  
##  <a name="_core_color_properties"></a> 颜色属性  
 在绘制控件时，可以使用常用 `ForeColor` 和 `BackColor` 属性或自己的自定义颜色属性。  若要使用颜色属性，请调用成员函数。[COleControl::TranslateColor](../Topic/COleControl::TranslateColor.md) 此函数参数为 Color 属性值和一选项调色板句柄。  返回值是可传递给函数，如 `SetTextColor` GDI 和 `CreateSolidBrush`的 **COLORREF** 值。  
  
 将 `ForeColor` 和 `BackColor` 属性的颜色值通过调用 `GetForeColor` 或 `GetBackColor` 函数，您可以分别访问  
  
 在绘制控件时，下面的示例演示如何使用两种颜色属性。  该临时变量 **COLORREF** 和 `CBrush` 对象用调用 `TranslateColor`:一个使用 `ForeColor` 和其他 `BackColor` 属性使用。  临时 `CBrush` 对象用于绘制的矩形，然后控件使用 `ForeColor` 属性，并且，设置文本颜色。  
  
 [!code-cpp[NVC_MFC_AxUI#24](../mfc/codesnippet/CPP/mfc-activex-controls-adding-stock-properties_3.cpp)]  
  
## 请参阅  
 [MFC ActiveX 控件](../mfc/mfc-activex-controls.md)   
 [MFC ActiveX 控件：属性](../mfc/mfc-activex-controls-properties.md)   
 [MFC ActiveX 控件：方法](../mfc/mfc-activex-controls-methods.md)   
 [COleControl Class](../mfc/reference/colecontrol-class.md)