---
title: MFC ActiveX 控件： 添加常用方法 |Microsoft Docs
ms.custom: ''
ms.date: 09/12/2018
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- MFC ActiveX controls [MFC], stock methods
- MFC ActiveX controls [MFC], methods
- DoClick method [MFC]
ms.assetid: bc4fad78-cabd-4cc0-a798-464b1a682f0b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b42907273423d69ed93df5700b33556047338fe2
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46391421"
---
# <a name="mfc-activex-controls-adding-stock-methods"></a>MFC ActiveX 控件：添加常用方法

常用的方法不同于自定义方法，它已经由类实现[COleControl](../mfc/reference/colecontrol-class.md)。 例如，`COleControl`包含支持为您的控件的 Refresh 方法的预定义的成员函数。 此常用的方法的调度映射项是 DISP_STOCKFUNC_REFRESH。

>[!IMPORTANT]
> ActiveX 是一项传统技术，不应使用新的开发。 本文将取代 ActiveX 的现代技术的详细信息，请参阅[ActiveX 控件](activex-controls.md)。

`COleControl` 支持两种常用方法： DoClick 和刷新。 控件的用户，以立即更新控件的外观; 调用刷新DoClick 调用以引发该控件的 Click 事件。

|方法|调度映射条目|注释|
|------------|------------------------|-------------|
|`DoClick`|**DISP_STOCKPROP_DOCLICK （)**|触发 Click 事件。|
|`Refresh`|**DISP_STOCKPROP_REFRESH （)**|将立即更新控件的外观。|

##  <a name="_core_adding_a_stock_method_using_classwizard"></a> 添加常用方法使用添加方法向导

添加常用方法是简单使用[添加方法向导](../ide/add-method-wizard.md)。 以下过程演示如何将刷新方法添加到使用 MFC ActiveX 控件向导创建的控件。

#### <a name="to-add-the-stock-refresh-method-using-the-add-method-wizard"></a>若要添加股票刷新方法使用添加方法向导

1. 加载控件的项目。

1. 在“类视图”中，展开控件的库节点。

1. 右键单击控件的接口节点（库节点的第二个节点）以打开快捷菜单。

1. 从快捷菜单中，单击**外**，然后单击**添加方法**。

     这将打开添加方法向导。

1. 在中**方法名称**框中，单击**刷新**。

1. 单击 **“完成”**。

##  <a name="_core_classwizard_changes_for_stock_methods"></a> 添加方法向导正在更改的常用方法

常用的 Refresh 方法支持的控件的基类，因为**添加方法向导**不会更改控件的类声明，以任何方式。 它将添加到控件的调度映射和方法的条目及其。IDL 文件。 将以下行添加到控件的调度映射，位于它的实现 (。CPP) 文件：

[!code-cpp[NVC_MFC_AxUI#16](../mfc/codesnippet/cpp/mfc-activex-controls-adding-stock-methods_1.cpp)]

这使刷新方法可供该控件的用户。

以下行添加到控件的。IDL 文件：

[!code-cpp[NVC_MFC_AxUI#17](../mfc/codesnippet/cpp/mfc-activex-controls-adding-stock-methods_2.idl)]

此行将刷新方法分配特定的 ID 号。

## <a name="see-also"></a>请参阅

[MFC ActiveX 控件](../mfc/mfc-activex-controls.md)

