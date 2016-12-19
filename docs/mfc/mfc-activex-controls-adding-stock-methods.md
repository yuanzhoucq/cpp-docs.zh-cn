---
title: "MFC ActiveX 控件：添加常用方法 | Microsoft Docs"
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
  - "DoClick 方法"
  - "MFC ActiveX 控件, 方法"
  - "MFC ActiveX 控件, 常用方法"
ms.assetid: bc4fad78-cabd-4cc0-a798-464b1a682f0b
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# MFC ActiveX 控件：添加常用方法
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

常用方法与自定义方法的不同之处在于它通过 [COleControl](../mfc/reference/colecontrol-class.md)类已经实现。  例如，`COleControl` 包含对控件的方法刷新的预定义的成员函数。  此计划映射项的常用方法是 **DISP\_STOCKFUNC\_REFRESH**。  
  
 `COleControl` 支持两种常用方法：DoClick 并刷新。  由控件调用将立即更新刷新的用户控件的外观；DoClick 调用触发控件的单击事件。  
  
|方法|计划映射项|注释|  
|--------|-----------|--------|  
|`DoClick`|**DISP\_STOCKPROP\_DOCLICK \(\)**|单击引发事件。|  
|**刷新**|**DISP\_STOCKPROP\_REFRESH \(\)**|立即更新控件的外观。|  
  
##  <a name="_core_adding_a_stock_method_using_classwizard"></a> 添加使用"添加方法向导的常用方法  
 添加常用方法可以使用 [添加方法向导](../ide/add-method-wizard.md)很简单。  下面的过程演示方法添加一个刷新到使用 MFC ActiveX 控件向导创建的控件。  
  
#### 使用 Add 方法向导，将库存刷新方法  
  
1.  加载控件的项目。  
  
2.  在"类视图，展开控件的库节点。  
  
3.  右击控件 \(库节点的第二个节点接口节点\) 打开快捷菜单。  
  
4.  从快捷菜单中单击 **添加**，然后单击 **添加方法**。  
  
     这将打开"添加方法向导"  
  
5.  在 **方法名称** 框中，单击 **刷新**。  
  
6.  单击**“完成”**。  
  
##  <a name="_core_classwizard_changes_for_stock_methods"></a> 添加方法向导"提供常用方法更改  
 因为股票刷新方法由控件的基类支持，因此 **添加方法向导** 既不更改控件的类声明。  该方法的输入控件添加到计划的映射及其 .idl 文件。  下列代码行添加到控件中映射计划，位于它实现 \(.cpp\) 文件：  
  
 [!code-cpp[NVC_MFC_AxUI#16](../mfc/codesnippet/CPP/mfc-activex-controls-adding-stock-methods_1.cpp)]  
  
 这使方法刷新活动控件的用户。  
  
 下列代码行添加到控件的 .idl 文件：  
  
 [!code-cpp[NVC_MFC_AxUI#17](../mfc/codesnippet/CPP/mfc-activex-controls-adding-stock-methods_2.idl)]  
  
 此行分配方法刷新特定 ID 号。  
  
## 请参阅  
 [MFC ActiveX 控件](../mfc/mfc-activex-controls.md)