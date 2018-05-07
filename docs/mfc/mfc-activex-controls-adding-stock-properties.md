---
title: MFC ActiveX 控件： 添加常用属性 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- BackColor property [MFC]
- properties [MFC], adding stock
- ForeColor property [MFC]
- MFC ActiveX controls [MFC], properties
- foreground colors, ActiveX controls
- foreground colors [MFC]
ms.assetid: 8b98c8c5-5b69-4366-87bf-0e61e6668ecb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c51a2efba3c89b4e216fec96459b14c3d0c637d8
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="mfc-activex-controls-adding-stock-properties"></a>MFC ActiveX 控件：添加常用属性
常用属性不同于自定义属性，因为它们已实现由类`COleControl`。 `COleControl` 包含控件中支持通用属性的预定义的成员函数。 一些常见属性包括控件的标题和前景色和背景颜色。 有关其他常用属性的信息，请参阅[Stock 属性支持添加属性向导](#_core_stock_properties_supported_by_classwizard)本文后续部分中。 常用属性的调度映射条目始终为前缀的**DISP_STOCKPROP**。  
  
 本文介绍如何使用添加属性向导的 ActiveX 控件添加常用属性 （在这种情况下，标题），并说明的生成的代码修改。 包括以下主题：  
  
-   [使用添加属性向导来添加常用属性](#_core_using_classwizard_to_add_a_stock_property)  
  
-   [添加属性向导正在更改的常用属性页](#_core_classwizard_changes_for_stock_properties)  
  
-   [添加属性向导支持的常用属性](#_core_stock_properties_supported_by_classwizard)  
  
-   [常用属性和通知](#_core_stock_properties_and_notification)  
  
-   [颜色属性](#_core_color_properties)  
  
    > [!NOTE]
    >  Visual Basic 自定义控件通常具有例如顶部、 左侧、 宽度、 高度、 对齐、 标记、 名称、 TabIndex、 TabStop，和父属性。 ActiveX 控件容器，但是，负责实现这些控件属性，因此 ActiveX 控件应支持这些属性。  
  
##  <a name="_core_using_classwizard_to_add_a_stock_property"></a> 使用添加属性向导，以便添加常用属性  
 添加常用属性需要更少的代码比添加自定义属性，因为会自动处理属性的支持`COleControl`。 下面的步骤演示如何将 stock Caption 属性添加到 ActiveX 控件框架，并且还可以用于添加其他常用的属性。 标题的所选的常用属性名称替换。  
  
#### <a name="to-add-the-stock-caption-property-using-the-add-property-wizard"></a>若要添加常用标题属性使用添加属性向导  
  
1.  加载控件的项目。  
  
2.  在“类视图”中，展开控件的库节点。  
  
3.  右键单击控件的接口节点（库节点的第二个节点）以打开快捷菜单。  
  
4.  从快捷菜单中，单击**添加**，然后单击**添加属性**。  
  
     这将打开[添加属性向导](../ide/names-add-property-wizard.md)。  
  
5.  在**属性名称**框中，单击**标题**。  
  
6.  单击 **“完成”**。  
  
##  <a name="_core_classwizard_changes_for_stock_properties"></a> 添加属性向导正在更改的常用属性页  
 因为`COleControl`支持常用属性，添加属性向导不会更改任何方式中的类声明; 它将属性添加到调度映射。 添加属性向导将以下行添加到该控件，它位于中实现的调度映射 (。CPP) 文件：  
  
 [!code-cpp[NVC_MFC_AxUI#22](../mfc/codesnippet/cpp/mfc-activex-controls-adding-stock-properties_1.cpp)]  
  
 以下行添加到控件的接口描述 (。IDL) 文件：  
  
 [!code-cpp[NVC_MFC_AxUI#23](../mfc/codesnippet/cpp/mfc-activex-controls-adding-stock-properties_2.idl)]  
  
 此行将 Caption 属性分配一个特定的 id。 请注意该属性是可绑定，并将权限从数据库之前请求修改的值。  
  
 这使得 Caption 属性控件的用户。 若要使用的常用属性的值，访问成员变量或成员函数`COleControl`基类。 有关这些成员变量和成员函数的详细信息，请参阅下一部分中，库存属性支持添加属性向导。  
  
##  <a name="_core_stock_properties_supported_by_classwizard"></a> 常用属性支持添加属性向导  
 `COleControl`类提供了九个常用的属性。 你可以添加想要通过使用添加属性向导的属性。  
  
|属性|调度映射条目|如何访问值|  
|--------------|------------------------|-------------------------|  
|**外观**|**DISP_STOCKPROP_APPEARANCE （)**|值的可访问性**m_sAppearance**。|  
|`BackColor`|**DISP_STOCKPROP_BACKCOLOR （)**|通过调用可访问的值`GetBackColor`。|  
|`BorderStyle`|**DISP_STOCKPROP_BORDERSTYLE （)**|值的可访问性**m_sBorderStyle**。|  
|**标题**|**DISP_STOCKPROP_CAPTION （)**|通过调用可访问的值`InternalGetText`。|  
|**启用**|**DISP_STOCKPROP_ENABLED （)**|值的可访问性**m_bEnabled**。|  
|**字体**|**DISP_STOCKPROP_FONT （)**|请参阅文章[MFC ActiveX 控件： 使用字体](../mfc/mfc-activex-controls-using-fonts.md)的用法。|  
|`ForeColor`|**DISP_STOCKPROP_FORECOLOR （)**|通过调用可访问的值`GetForeColor`。|  
|**hWnd**|**DISP_STOCKPROP_HWND （)**|值的可访问性`m_hWnd`。|  
|**文本**|**DISP_STOCKPROP_TEXT （)**|通过调用可访问的值`InternalGetText`。 此属性是相同**标题**，属性名称除外。|  
|**ReadyState**|**DISP_STOCKPROP_READYSTATE()**|M_lReadyState 的可访问性的值或 `GetReadyState`|  
  
##  <a name="_core_stock_properties_and_notification"></a> 常用属性和通知  
 大多数常用属性具有通知函数可以重写。 例如，每当`BackColor`属性更改，`OnBackColorChanged`调用函数 （控件类的成员函数）。 默认实现 (在`COleControl`) 调用`InvalidateControl`。 如果你想要在这种情况下执行其他操作，重写此函数。  
  
##  <a name="_core_color_properties"></a> 颜色属性  
 你可以使用常用`ForeColor`和`BackColor`属性或您自己的自定义颜色属性，在绘制控件。 若要使用的颜色属性，调用[COleControl::TranslateColor](../mfc/reference/colecontrol-class.md#translatecolor)成员函数。 此函数的参数是颜色属性和的可选调色板的句柄的值。 返回值是**COLORREF**值，可以传递给 GDI 函数，如`SetTextColor`和`CreateSolidBrush`。  
  
 常用的颜色值`ForeColor`和`BackColor`属性可以访问通过调用`GetForeColor`或`GetBackColor`函数，分别。  
  
 下面的示例演示如何在绘制控件时使用这些两个颜色属性。 初始化一个临时**COLORREF**变量和一个`CBrush`对象通过调用`TranslateColor`： 一个使用`ForeColor`属性和其他使用`BackColor`属性。 一个临时`CBrush`对象然后用于绘制控件的矩形，并使用设置的文本颜色`ForeColor`属性。  
  
 [!code-cpp[NVC_MFC_AxUI#24](../mfc/codesnippet/cpp/mfc-activex-controls-adding-stock-properties_3.cpp)]  
  
## <a name="see-also"></a>请参阅  
 [MFC ActiveX 控件](../mfc/mfc-activex-controls.md)   
 [MFC ActiveX 控件： 属性](../mfc/mfc-activex-controls-properties.md)   
 [MFC ActiveX 控件： 方法](../mfc/mfc-activex-controls-methods.md)   
 [COleControl 类](../mfc/reference/colecontrol-class.md)
