---
title: "回调项和回调掩码 | Microsoft Docs"
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
  - "CListCtrl 类中的回调项"
  - "CListCtrl 类, 回调项和回调掩码"
ms.assetid: 67c1f76f-6144-453e-9376-6712f89430ae
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# 回调项和回调掩码
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

对于其项中的每一个，列表视图控件通常存储文本标签，项的图标的图像列表的索引，以及项状态的一组位标志。  您可以定义单个项作为回调项，如果应用程序已经存储某些项的信息，这将很有用。  
  
 您通过为 **LV\_ITEM** 的 `pszText` 和 `iImage` 成员 \(参见 [CListCtrl::GetItem](../Topic/CListCtrl::GetItem.md)\)指定相应的取值定义一个项作为回调项。  如果应用程序的维护项或子项的文本，为`pszText` 成员指定 **LPSTR\_TEXTCALLBACK**的取值。  如果应用程序记录项的图标，为`iImage` 成员指定 **I\_IMAGECALLBACK**的取值。  
  
 除了定义回调项之外，您可以修改控件的回调掩码。  此掩码为指定项的一组位标志，由应用程序，而不是控件存储当前数据。  回调掩码应用于所有控件的项，不同于回调项标识，适用于特定项。  回调掩码默认为零，这意味着控件跟踪所有项状态。  若要更改此默认行为，请以下值的任意组合初始化掩码：  
  
-   `LVIS_CUT` 项被标记为剪切操作。  
  
-   `LVIS_DROPHILITED` 项被标记为为拖放目标。  
  
-   `LVIS_FOCUSED`该项被聚焦。  
  
-   `LVIS_SELECTED`该项已选定。  
  
-   **LVIS\_OVERLAYMASK** 应用程序为每个项存储了当前覆盖图像的图像列表索引。  
  
-   **LVIS\_OVERLAYMASK** 应用程序为每个项存储了当前状态图像的图像列表索引。  
  
 Programmer's 关于检索和设置此掩码的详细信息，请参见 [CListCtrl::GetCallbackMask](../Topic/CListCtrl::GetCallbackMask.md) 和 [CListCtrl::SetCallbackMask](../Topic/CListCtrl::SetCallbackMask.md)。  
  
## 请参阅  
 [使用 CListCtrl](../mfc/using-clistctrl.md)   
 [控件](../mfc/controls-mfc.md)