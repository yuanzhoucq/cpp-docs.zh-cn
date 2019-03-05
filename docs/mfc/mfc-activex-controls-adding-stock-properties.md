---
title: MFC ActiveX 控件：添加常用属性
ms.date: 11/04/2016
helpviewer_keywords:
- BackColor property [MFC]
- properties [MFC], adding stock
- ForeColor property [MFC]
- MFC ActiveX controls [MFC], properties
- foreground colors, ActiveX controls
- foreground colors [MFC]
ms.assetid: 8b98c8c5-5b69-4366-87bf-0e61e6668ecb
ms.openlocfilehash: 940f61c9ce6ccb57843333582455e61c1f7ac73b
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/04/2019
ms.locfileid: "57289684"
---
# <a name="mfc-activex-controls-adding-stock-properties"></a>MFC ActiveX 控件：添加常用属性

常用属性不同于自定义属性，类已经实现`COleControl`。 `COleControl` 包含支持控件的常见属性的预定义的成员函数。 一些常见属性包括控件的标题和前景色和背景颜色。 有关其他常用属性的信息，请参阅[股票属性支持添加属性向导](#_core_stock_properties_supported_by_classwizard)这篇文章中更高版本。 属性始终加 DISP_STOCKPROP 股票调度映射条目。

本文介绍如何使用添加属性向导的 ActiveX 控件添加常用属性 （在此情况下，标题），并说明生成的代码修改。 包括以下主题：

- [使用添加属性向导来添加常用属性](#_core_using_classwizard_to_add_a_stock_property)

- [添加属性向导正在更改的常用属性页](#_core_classwizard_changes_for_stock_properties)

- [添加属性向导支持的常用属性](#_core_stock_properties_supported_by_classwizard)

- [常用属性和通知](#_core_stock_properties_and_notification)

- [颜色属性](#_core_color_properties)

    > [!NOTE]
    >  Visual Basic 自定义控件通常具有如 Top、 左侧、 宽度、 高度、 对齐、 标记、 名称、 TabIndex、 TabStop 和父属性。 ActiveX 控件容器，但是，需负责实现这些控件属性，因此 ActiveX 控件应支持这些属性。

##  <a name="_core_using_classwizard_to_add_a_stock_property"></a> 使用添加属性向导以添加常用属性

添加常用属性需要更少的代码比添加自定义属性，因为对来自动处理该属性的支持`COleControl`。 以下过程演示如何将库存 Caption 属性添加到 ActiveX 控件框架，并还可用于添加其他常用的属性。 替换标题的所选的常用属性名称。

#### <a name="to-add-the-stock-caption-property-using-the-add-property-wizard"></a>若要添加常用的标题属性使用添加属性向导

1. 加载控件的项目。

1. 在“类视图”中，展开控件的库节点。

1. 右键单击控件的接口节点（库节点的第二个节点）以打开快捷菜单。

1. 从快捷菜单中，单击**外**，然后单击**添加属性**。

   这将打开[添加属性向导](../ide/names-add-property-wizard.md)。

1. 在中**属性名称**框中，单击**标题**。

1. 单击 **“完成”**。

##  <a name="_core_classwizard_changes_for_stock_properties"></a> 添加属性向导正在更改的常用属性页

因为`COleControl`支持常用属性，添加属性向导不会更改以任何方式在类声明; 它将属性添加到调度映射。 添加属性向导将以下行添加到该控件，位于在实现中的调度映射 (。CPP) 文件：

[!code-cpp[NVC_MFC_AxUI#22](../mfc/codesnippet/cpp/mfc-activex-controls-adding-stock-properties_1.cpp)]

以下行添加到控件的接口说明 (。IDL) 文件：

[!code-cpp[NVC_MFC_AxUI#23](../mfc/codesnippet/cpp/mfc-activex-controls-adding-stock-properties_2.idl)]

此行将 Caption 属性分配一个特定的 id。 请注意，该属性是可绑定，将权限从数据库之前请求修改值。

这使标题属性可供用户控件。 若要使用的常用属性的值，访问成员变量或成员函数的`COleControl`基类。 有关这些成员变量和成员函数的详细信息，请参阅下一部分中，库存的添加属性向导支持的属性。

##  <a name="_core_stock_properties_supported_by_classwizard"></a> 常用属性支持添加属性向导

`COleControl`类提供了九个常用的属性。 可以添加想要通过使用添加属性向导的属性。

|属性|调度映射条目|如何访问值|
|--------------|------------------------|-------------------------|
|`Appearance`|DISP_STOCKPROP_APPEARANCE( )|值的可访问性`m_sAppearance`。|
|`BackColor`|DISP_STOCKPROP_BACKCOLOR( )|值通过调用可访问`GetBackColor`。|
|`BorderStyle`|DISP_STOCKPROP_BORDERSTYLE( )|值的可访问性`m_sBorderStyle`。|
|`Caption`|DISP_STOCKPROP_CAPTION( )|值通过调用可访问`InternalGetText`。|
|`Enabled`|DISP_STOCKPROP_ENABLED( )|值的可访问性`m_bEnabled`。|
|`Font`|DISP_STOCKPROP_FONT( )|请参阅文章[MFC ActiveX 控件：使用字体](../mfc/mfc-activex-controls-using-fonts.md)的使用情况。|
|`ForeColor`|DISP_STOCKPROP_FORECOLOR( )|值通过调用可访问`GetForeColor`。|
|`hWnd`|DISP_STOCKPROP_HWND （)|值的可访问性`m_hWnd`。|
|`Text`|DISP_STOCKPROP_TEXT( )|值通过调用可访问`InternalGetText`。 此属性等同于`Caption`，属性名称除外。|
|`ReadyState`|DISP_STOCKPROP_READYSTATE()|值的可访问性`m_lReadyState`或 `GetReadyState`|

##  <a name="_core_stock_properties_and_notification"></a> 常用属性和通知

大多数常用属性具有可重写的通知函数。 例如，每当`BackColor`更改属性时，`OnBackColorChanged`调用函数 （控件类的一个成员函数）。 默认实现 (在`COleControl`) 调用`InvalidateControl`。 如果你想要对这种情况下采取其他操作，重写此函数。

##  <a name="_core_color_properties"></a> 颜色属性

可以使用股票`ForeColor`和`BackColor`属性或您自己的自定义颜色属性，绘制控件时。 若要使用的颜色属性，请调用[COleControl::TranslateColor](../mfc/reference/colecontrol-class.md#translatecolor)成员函数。 此函数的参数是颜色属性的可选调色板的句柄的值。 返回值是**COLORREF**值，可传递给 GDI 函数，如`SetTextColor`和`CreateSolidBrush`。

股票的颜色值`ForeColor`并`BackColor`属性访问通过调用`GetForeColor`或`GetBackColor`函数，分别。

下面的示例演示如何在绘制控件时使用这些两个颜色属性。 初始化一个临时**COLORREF**变量和一个`CBrush`对象通过调用`TranslateColor`： 一个使用`ForeColor`属性和其他使用`BackColor`属性。 临时`CBrush`对象用来绘制控件的矩形，并使用设置的文本颜色`ForeColor`属性。

[!code-cpp[NVC_MFC_AxUI#24](../mfc/codesnippet/cpp/mfc-activex-controls-adding-stock-properties_3.cpp)]

## <a name="see-also"></a>请参阅

[MFC ActiveX 控件](../mfc/mfc-activex-controls.md)<br/>
[MFC ActiveX 控件：属性](../mfc/mfc-activex-controls-properties.md)<br/>
[MFC ActiveX 控件：方法](../mfc/mfc-activex-controls-methods.md)<br/>
[COleControl 类](../mfc/reference/colecontrol-class.md)
