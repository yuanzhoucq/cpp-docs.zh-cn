---
title: "用于记录滚动的命令处理程序（MFC 数据访问） | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "记录滚动 [C++]"
  - "记录视图 [C++], 滚动"
  - "滚动记录"
ms.assetid: f8b13477-2a37-459e-a30c-806fb78165ac
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# 用于记录滚动的命令处理程序（MFC 数据访问）
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

类 [CRecordView](../mfc/reference/crecordview-class.md) 和 [CDaoRecordView](../mfc/reference/cdaorecordview-class.md) 提供了处理以下标准命令的默认命令：  
  
-   **ID\_RECORD\_MOVE\_FIRST**  
  
-   **ID\_RECORD\_MOVE\_LAST**  
  
-   **ID\_RECORD\_MOVE\_NEXT**  
  
-   **ID\_RECORD\_MOVE\_PREV**  
  
 类 `CRecordView` 和 `CDaoRecordView` 的 `OnMove` 成员函数提供了用于处理逐条移动的所有四个命令的默认命令。  发布这些命令后，RFX（或 DFX）将加载新记录到记录集字段，DDX 将移动值到记录窗体控件。  有关 RFX 的信息，请参阅[记录字段交换 \(RFX\)](../data/odbc/record-field-exchange-rfx.md)。  
  
> [!NOTE]
>  确保将这些标准的命令 ID 用于任何与标准记录导航命令关联的用户界面对象。  
  
## 请参阅  
 [支持在记录视图中导航](../data/supporting-navigation-in-a-record-view-mfc-data-access.md)