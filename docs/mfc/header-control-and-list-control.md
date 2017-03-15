---
title: "标题控件和列表控件 | Microsoft Docs"
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
  - "CHeaderCtrl 类, 使用 CListCtrl"
  - "CListCtrl 类, 标题控件"
  - "CListCtrl 类, 使用 CHeaderCtrl"
  - "控件 [MFC], 标题"
  - "标题控件"
  - "标题控件, 列表控件用于"
ms.assetid: b20194b1-1a6b-4e2f-b890-1b3cca6650bc
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# 标题控件和列表控件
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

在许多情况下，您将使用 [CListCtrl](../mfc/reference/clistctrl-class.md) 中或 [CListView](../mfc/reference/clistview-class.md) 嵌入对象的标题控件。  但是，有单独标题控件需要的对象，如操作中，数据排列在列或行的情况，如 [CView](../mfc/reference/cview-class.md)派生的对象。  在这些情况下，您需要对外观更大程度的控制而默认嵌入的标题控件的行为。  
  
 在常见要控制标题提供标准，默认行为，您可能需要使用或 [CListCtrl](../mfc/reference/clistctrl-class.md) [CListView](../mfc/reference/clistview-class.md)。  使用 `CListCtrl`，当需要默认标题控件的功能，嵌入在列表视图公共控件。  使用 [CListView](../mfc/reference/clistview-class.md)，当所需默认标题控件的功能，嵌入对象视图。  
  
> [!NOTE]
>  这些控件只包含的内置标题控件，使用 `LVS_REPORT` 样式，则列表创建视图控件。  
  
 在大多数情况下，将的标题控件的外观可以通过更改中的列表视图控件的样式。  此外，关于可以对标题控件的信息可以通过父列表视图控件的成员函数中。  但是，用于完全控制和访问权限，对嵌入的标题控件的特性和样式，建议对标题控件的对象指针获取。  
  
 嵌入对象的标题控件可以从 **CListCtrl** 或 `CListView` 的调用。访问各个类的 `GetHeaderCtrl` 成员函数。  以下代码对此进行了说明：  
  
 [!code-cpp[NVC_MFCControlLadenDialog#14](../mfc/codesnippet/CPP/header-control-and-list-control_1.cpp)]  
  
## 您想进一步了解什么？  
  
-   [对标题控件使用图像列表](../mfc/using-image-lists-with-header-controls.md)  
  
## 请参阅  
 [使用 CHeaderCtrl](../mfc/using-cheaderctrl.md)   
 [控件](../mfc/controls-mfc.md)