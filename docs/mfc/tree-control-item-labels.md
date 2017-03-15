---
title: "树控件项标签 | Microsoft Docs"
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
  - "CTreeCtrl 类, 项标签"
  - "项标签"
  - "项标签, 树控件"
  - "标签, CTreeCtrl 项"
  - "树控件, 项标签"
ms.assetid: fe834107-1a25-4280-aced-774c11565805
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# 树控件项标签
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

通常指定项标签的文本，在将项添加为树控件 \(\)。[CTreeCtrl](../mfc/reference/ctreectrl-class.md) `InsertItem` 成员函数来传递定义项的一个属性 [TVITEM](http://msdn.microsoft.com/library/windows/desktop/bb773456) 结构，包括包含的标签文本的字符串。  `InsertItem` 可以调用使用参数的各种组合的一些重载。  
  
 树控件的每个项分配存储内存；项的标签文本将占用此内存的重要的一部分。  如果应用程序维护字符串的副本在树控件中，您可以通过指定 **LPSTR\_TEXTCALLBACK** 值。`TV_ITEM` 的 **pszText** 成员或 `lpszItem` 参数的控件降低内存要求而不是传递实际字符串为树控件。  使用 **LPSTR\_TEXTCALLBACK** 会导致树从控制应用程序检索项标签的文本项，当需要重新绘制。  若要检索文本，该树控件发送通知消息，包括 [TVN\_GETDISPINFO](http://msdn.microsoft.com/library/windows/desktop/bb773518)[NMTVDISPINFO](http://msdn.microsoft.com/library/windows/desktop/bb773418) 结构的地址。  必须通过设置包括结构的相应成员的响应。  
  
 树控件使用从创建树控件的过程堆分配的内存。  项的最大页数。基于树控件的内存量。堆中可用。  每个项都采用 64 字节。  
  
## 请参阅  
 [使用 CTreeCtrl](../mfc/using-ctreectrl.md)   
 [控件](../mfc/controls-mfc.md)