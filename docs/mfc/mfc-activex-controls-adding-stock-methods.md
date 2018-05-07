---
title: MFC ActiveX 控件： 添加常用方法 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
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
ms.openlocfilehash: f02712f3df56bf2fc04fba736f28931250f7bcb8
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="mfc-activex-controls-adding-stock-methods"></a>MFC ActiveX 控件：添加常用方法
常用的方法与不同的自定义方法的已由类[COleControl](../mfc/reference/colecontrol-class.md)。 例如，`COleControl`包含支持刷新方法为您的控件的预定义的成员函数。 此常用方法的调度映射条目**DISP_STOCKFUNC_REFRESH**。  
  
 `COleControl` 支持两种常用的方法： DoClick 和刷新。 刷新调用由控件的用户，以立即更新控件的外观;DoClick 调用激发控件的单击事件。  
  
|方法|调度映射条目|注释|  
|------------|------------------------|-------------|  
|`DoClick`|**DISP_STOCKPROP_DOCLICK （)**|触发单击事件。|  
|**刷新**|**DISP_STOCKPROP_REFRESH （)**|立即更新控件的外观。|  
  
##  <a name="_core_adding_a_stock_method_using_classwizard"></a> 添加常用方法使用添加方法向导  
 添加常用方法是简单使用[添加方法向导](../ide/add-method-wizard.md)。 下面的过程演示将刷新方法添加到使用 MFC ActiveX 控件向导创建的控件。  
  
#### <a name="to-add-the-stock-refresh-method-using-the-add-method-wizard"></a>若要添加使用添加方法向导股票刷新方法  
  
1.  加载控件的项目。  
  
2.  在“类视图”中，展开控件的库节点。  
  
3.  右键单击控件的接口节点（库节点的第二个节点）以打开快捷菜单。  
  
4.  从快捷菜单中，单击**添加**，然后单击**添加方法**。  
  
     这将打开添加方法向导。  
  
5.  在**方法名称**框中，单击**刷新**。  
  
6.  单击 **“完成”**。  
  
##  <a name="_core_classwizard_changes_for_stock_methods"></a> 添加方法向导正在更改的常用方法  
 因为股票刷新方法支持由该控件的基类，**添加方法向导**不会更改控件的类声明以任何方式。 它将添加到控件的调度映射和方法的条目其。IDL 文件。 以下行添加到控件的调度映射，位于其实现 (。CPP) 文件：  
  
 [!code-cpp[NVC_MFC_AxUI#16](../mfc/codesnippet/cpp/mfc-activex-controls-adding-stock-methods_1.cpp)]  
  
 这使得刷新方法控制的用户。  
  
 以下行添加到控件的。IDL 文件：  
  
 [!code-cpp[NVC_MFC_AxUI#17](../mfc/codesnippet/cpp/mfc-activex-controls-adding-stock-methods_2.idl)]  
  
 此行将刷新方法分配一个特定的 ID 号。  
  
## <a name="see-also"></a>请参阅  
 [MFC ActiveX 控件](../mfc/mfc-activex-controls.md)

