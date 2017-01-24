---
title: "记录视图的数据交换（MFC 数据访问） | Microsoft Docs"
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
  - "对话框数据交换 (DDX), 记录视图"
  - "DAO 记录字段交换 (DFX)"
  - "DAO 记录字段交换 (DFX), 数据交换机制"
  - "DAO 记录字段交换 (DFX), 记录视图"
  - "记录视图, 数据交换"
  - "记录字段交换 (RFX)"
  - "记录字段交换 (RFX), 数据交换机制"
  - "记录字段交换 (RFX), 记录视图"
ms.assetid: abc52ca7-6997-47a7-98f3-f347f52b1f72
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 记录视图的数据交换（MFC 数据访问）
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

当使用[添加类](../mfc/reference/adding-an-mfc-odbc-consumer.md)将记录视图的对话框模板资源中控件映射到记录集的字段时，此框架将以两个方向管理数据交换 — 从记录集到控件以及从控件到记录集。  使用 DDX 机制意味着你不必编写代码来回传输数据。  
  
 记录视图的 DDX 与以下项配合使用：  
  
-   `CRecordset` \(ODBC\) 类的记录集的 [RFX](../data/odbc/record-field-exchange-rfx.md)  
  
-   `CDaoRecordset` \(DAO\) 类的记录集的 DFX。  
  
 尽管其实现方法不同，但接口层 RFX 和 DFX 与数据交换机制非常相似。  DAO 版本 DFX 是仿照早期的 ODBC 版本 RFX 而来。  如果知道如何使用 RFX，你就知道如何使用 DFX。  
  
 RFX 和 DFX 在数据源的当前记录和记录集对象的字段数据成员之间移动数据。  DDX 可将数据从字段数据成员移动到窗体的控件中。  此组合在初始时和用户逐条移动记录时填充窗体控件。  它还可以将更新的数据移回记录集，然后再移到数据源。  
  
 以下数据显示了记录视图的 DDX 和 RFX（或 DFX）之间的关系。  
  
 ![对话框数据交换和记录字段交换](../data/media/vc37xt1.gif "vc37XT1")  
对话框数据交换和记录字段交换  
  
 有关 DDX 的更多信息，请参阅[对话框数据交换和验证](../mfc/dialog-data-exchange-and-validation.md)。  有关 RFX 的更多信息，请参阅[记录字段交换 \(RFX\)](../data/odbc/record-field-exchange-rfx.md)。  
  
## 请参阅  
 [记录视图（MFC 数据访问）](../data/record-views-mfc-data-access.md)   
 [ODBC 驱动程序列表](../data/odbc/odbc-driver-list.md)