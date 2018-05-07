---
title: 树控件项标签 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- tree controls [MFC], item labels
- labels, CTreeCtrl items
- CTreeCtrl class [MFC], item labels
- item labels, tree controls
- item labels
ms.assetid: fe834107-1a25-4280-aced-774c11565805
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 598dca9f0d5f394a8e742c1b886588eab3518bf4
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="tree-control-item-labels"></a>树控件项标签
将项添加到树控件时通常指定项的标签的文本 ([CTreeCtrl](../mfc/reference/ctreectrl-class.md))。 `InsertItem`成员函数可以传递[TVITEM](http://msdn.microsoft.com/library/windows/desktop/bb773456)定义项的属性，包括包含标签的文本的字符串的结构。 `InsertItem` 具有多个重载，可以用参数的各种组合调用。  
  
 树控件分配内存来存储每个项;项标签的文本需要占用此内存的重要部分。 如果你的应用程序维护的树控件中字符串的副本，你可以通过指定减少控件的内存要求**LPSTR_TEXTCALLBACK**中的值**pszText** 的成员`TV_ITEM`或`lpszItem`而不是传递到树控件的实际字符串参数。 使用**LPSTR_TEXTCALLBACK**导致树控件项需要重绘时从应用程序检索的项的标签的文本。 若要检索文本，树控件将发送[TVN_GETDISPINFO](http://msdn.microsoft.com/library/windows/desktop/bb773518)通知消息，其中包括的地址[NMTVDISPINFO](http://msdn.microsoft.com/library/windows/desktop/bb773418)结构。 你必须通过设置包含结构的合适成员作出响应。  
  
 树控件使用从创建树控件的进程以及堆分配的内存。 树控件中的项的最大数目取决于堆中可用的内存量。 每个项占用 64 个字节。  
  
## <a name="see-also"></a>请参阅  
 [使用 CTreeCtrl](../mfc/using-ctreectrl.md)   
 [控件](../mfc/controls-mfc.md)

