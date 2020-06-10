---
title: MFC ActiveX 控件：添加常用方法
ms.date: 09/12/2018
helpviewer_keywords:
- MFC ActiveX controls [MFC], stock methods
- MFC ActiveX controls [MFC], methods
- DoClick method [MFC]
ms.assetid: bc4fad78-cabd-4cc0-a798-464b1a682f0b
ms.openlocfilehash: 42d8dfecd32b4aecd0daa4034497ec9abff6d11a
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84619937"
---
# <a name="mfc-activex-controls-adding-stock-methods"></a>MFC ActiveX 控件：添加常用方法

Stock 方法不同于自定义方法，因为它已由类[COleControl](reference/colecontrol-class.md)实现。 例如， `COleControl` 包含一个预定义的成员函数，该函数支持控件的刷新方法。 此常用方法的调度映射项 DISP_STOCKFUNC_REFRESH。

>[!IMPORTANT]
> ActiveX 是一种不能用于新开发的旧技术。 有关取代 ActiveX 的新式技术的详细信息，请参阅[Activex 控件](activex-controls.md)。

`COleControl`支持两种常用方法： DoClick 和 Refresh。 刷新由控件的用户调用以立即更新控件的外观;调用 DoClick 来触发控件的 Click 事件。

|方法|调度映射项|评论|
|------------|------------------------|-------------|
|`DoClick`|**DISP_STOCKPROP_DOCLICK （）**|触发 Click 事件。|
|`Refresh`|**DISP_STOCKPROP_REFRESH （）**|立即更新控件的外观。|

## <a name="adding-a-stock-method-using-the-add-method-wizard"></a><a name="_core_adding_a_stock_method_using_classwizard"></a>使用添加方法向导添加常用方法

使用[添加方法向导](../ide/add-method-wizard.md)添加 stock 方法非常简单。 下面的过程演示如何将 Refresh 方法添加到使用 MFC ActiveX 控件向导创建的控件。

#### <a name="to-add-the-stock-refresh-method-using-the-add-method-wizard"></a>使用 "添加方法向导" 添加股票刷新方法

1. 加载控件的项目。

1. 在“类视图”中，展开控件的库节点。

1. 右键单击控件的接口节点（库节点的第二个节点）以打开快捷菜单。

1. 在快捷菜单中，单击 "**添加**"，然后单击 "**添加方法**"。

   这将打开 "添加方法向导"。

1. 在 "**方法名称**" 框中，单击 "**刷新**"。

1. 单击“完成”。

## <a name="add-method-wizard-changes-for-stock-methods"></a><a name="_core_classwizard_changes_for_stock_methods"></a>常用方法的添加方法向导更改

由于该控件的基类支持 stock Refresh 方法，因此**添加方法向导**不会以任何方式更改控件的类声明。 它将方法的条目添加到控件的调度映射和。IDL 文件。 将以下行添加到控件的调度映射中（位于其实现（）中。CPP）文件：

[!code-cpp[NVC_MFC_AxUI#16](codesnippet/cpp/mfc-activex-controls-adding-stock-methods_1.cpp)]

这使 Refresh 方法可用于控件的用户。

以下行将添加到控件的。IDL 文件：

[!code-cpp[NVC_MFC_AxUI#17](codesnippet/cpp/mfc-activex-controls-adding-stock-methods_2.idl)]

此行将 Refresh 方法分配给特定的 ID 号。

## <a name="see-also"></a>另请参阅

[MFC ActiveX 控件](mfc-activex-controls.md)
