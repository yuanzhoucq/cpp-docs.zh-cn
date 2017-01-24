---
title: "列表控件和列表视图 | Microsoft Docs"
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
  - "CListCtrl 类, 和 CListView"
  - "CListView 类, 和 CListCtrl"
  - "列表控件, 列表视图"
  - "列表视图"
  - "视图, 列表和列表控件"
ms.assetid: 7aee1c48-b158-4399-be0b-be366993665e
caps.latest.revision: 11
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 列表控件和列表视图
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

为方便起见，MFC 封装列表控件的两种方式。  可使用列表控件：  
  
-   直接通过嵌入，对话框类中的一个对象。[CListCtrl](../mfc/reference/clistctrl-class.md)  
  
-   间接，使用类，[CListView](../mfc/reference/clistview-class.md)。  
  
 在 [CEditView](../mfc/reference/ceditview-class.md) 一编辑控件，`CListView` 可以轻松集成带有 MFC 文档\/视图结构的列表，控件封装了控件：控件以 MFC 视图的整个外围应用。\(视图 *是* 控件，被转换为 `CListView`。\)  
  
 `CListView` 对象从 [CCtrlView](../mfc/reference/cctrlview-class.md) 及其基类继承并添加成员函数检索基础列表控件。  使用视图成员与视图中用作视图。  使用 [GetListCtrl](../Topic/CListView::GetListCtrl.md) 成员函数为列表控件的成员函数的访问。  使用这些成员：  
  
-   添加删除，或者操作“Item”列表中。  
  
-   集合或者获取列表控件特性。  
  
 若要获取对基础 `CListView`的 `CListCtrl` 引用，请调用从列表视图类的 `GetListCtrl` :  
  
 [!CODE [NVC_MFCListView#4](../CodeSnippet/VS_Snippets_Cpp/NVC_MFCListView#4)]  
  
 本主题介绍两种使用列表控件。  
  
## 请参阅  
 [使用 CListCtrl](../mfc/using-clistctrl.md)   
 [控件](../mfc/controls-mfc.md)