---
title: MFC ActiveX 控件：添加常用方法
ms.date: 09/12/2018
helpviewer_keywords:
- MFC ActiveX controls [MFC], stock methods
- MFC ActiveX controls [MFC], methods
- DoClick method [MFC]
ms.assetid: bc4fad78-cabd-4cc0-a798-464b1a682f0b
ms.openlocfilehash: ec59ccc0cbd48fc3114eb2dc0833dd3dd65691de
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364673"
---
# <a name="mfc-activex-controls-adding-stock-methods"></a>MFC ActiveX 控件：添加常用方法

stock 方法不同于自定义方法，因为它已经由类[COleControl](../mfc/reference/colecontrol-class.md)实现。 例如，`COleControl`包含支持控件的刷新方法的预定义成员函数。 此库存方法的调度映射条目DISP_STOCKFUNC_REFRESH。

>[!IMPORTANT]
> ActiveX 是一种不应用于新开发的传统技术。 有关取代 ActiveX 的现代技术的详细信息，请参阅[ActiveX 控件](activex-controls.md)。

`COleControl`支持两种库存方法：DoClick 和刷新。 控件的用户调用刷新以立即更新控件的外观;调用 DoClick 以触发控件的单击事件。

|方法|调度映射条目|注释|
|------------|------------------------|-------------|
|`DoClick`|**DISP_STOCKPROP_DOCLICK）**|触发单击事件。|
|`Refresh`|**DISP_STOCKPROP_REFRESH）**|立即更新控件的外观。|

## <a name="adding-a-stock-method-using-the-add-method-wizard"></a><a name="_core_adding_a_stock_method_using_classwizard"></a>使用添加方法向导添加库存方法

使用[添加方法向导](../ide/add-method-wizard.md)添加库存方法非常简单。 以下过程演示了将刷新方法添加到使用 MFC ActiveX 控制向导创建的控件。

#### <a name="to-add-the-stock-refresh-method-using-the-add-method-wizard"></a>使用添加方法向导添加库存刷新方法

1. 加载控件的项目。

1. 在“类视图”中，展开控件的库节点。

1. 右键单击控件的接口节点（库节点的第二个节点）以打开快捷菜单。

1. 在快捷菜单中，单击"**添加**"，然后单击"**添加方法**"。

   这将打开"添加方法向导"。

1. 在 **"方法名称"** 框中，单击 **"刷新**"。

1. 单击“完成”  。

## <a name="add-method-wizard-changes-for-stock-methods"></a><a name="_core_classwizard_changes_for_stock_methods"></a>添加库存方法的方法向导更改

由于控件的基类支持股票刷新方法，**因此 Add 方法向导**不会以任何方式更改控件的类声明。 它将该方法的条目添加到控件的调度映射及其 。IDL 文件。 以下行将添加到控件的调度映射中，位于其实现 （中。CPP） 文件：

[!code-cpp[NVC_MFC_AxUI#16](../mfc/codesnippet/cpp/mfc-activex-controls-adding-stock-methods_1.cpp)]

这使刷新方法可供控件的用户使用。

以下行将添加到控件的 。IDL 文件：

[!code-cpp[NVC_MFC_AxUI#17](../mfc/codesnippet/cpp/mfc-activex-controls-adding-stock-methods_2.idl)]

此行为刷新方法指定特定的 ID 号。

## <a name="see-also"></a>另请参阅

[MFC 活动X控制](../mfc/mfc-activex-controls.md)
