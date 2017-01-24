---
title: "树控件项位置 | Microsoft Docs"
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
  - "CTreeCtrl 类, 项位置"
  - "树控件中的项位置"
  - "位置, CTreeCtrl 项"
  - "树控件, 项位置"
ms.assetid: cd264344-2cf9-4d90-9ea8-c6900b6f60e7
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 树控件项位置
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

项的初始位置设置，在将项添加为树控件 \([CTreeCtrl](../mfc/reference/ctreectrl-class.md)\) 时使用 `InsertItem` 函数。成员，  成员函数调用指定父项的处理以及句柄后，新的项会插入。  第二处理必须标识任何子项给定父或一个值：`TVI_FIRST`、`TVI_LAST`或 `TVI_SORT`。  
  
 在 `TVI_FIRST` 或 `TVI_LAST` 中指定树，控件首先将新项或结尾。子项给定父项的列表。  如果指定 `TVI_SORT`，则树控件按字母顺序插入新项到子项列表基于项标签的文本。  
  
 可以将子项父项列表到字母顺序通过调用成员函数。[SortChildren](../Topic/CTreeCtrl::SortChildren.md) 此函数由指定的实所有级别删除给定的父项的子项是否还按字母顺序排序。  
  
 [SortChildrenCB](../Topic/CTreeCtrl::SortChildrenCB.md) 成员函数可以排序基于您定义的标准的子项。  当您调用此函数时，需要指定树控件可以调用的应用程序中定义回调的函数，当两个子项相对顺序需要决定。  指定，则在调用 `SortChildrenCB`时的回调函数接收比较项的两个 32 位应用程序定义的值和第三个 32 位值。  
  
## 请参阅  
 [使用 CTreeCtrl](../mfc/using-ctreectrl.md)   
 [控件](../mfc/controls-mfc.md)