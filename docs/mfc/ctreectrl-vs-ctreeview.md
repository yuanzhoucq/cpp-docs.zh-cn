---
title: "CTreeCtrl vs。CTreeView |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CTreeCtrl
- CTreeView
dev_langs:
- C++
helpviewer_keywords:
- tree view controls
- CTreeCtrl class [MFC], vs. CTreeView class [MFC]
- CTreeView class [MFC], vs. CTreeCtrl class [MFC]
- tree controls [MFC], and tree view
ms.assetid: bba5af25-103f-4b53-84d3-071bc9bd6494
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: bb0c1b7a7bf73ab70bbccca6f2a9ccc2ab385516
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="ctreectrl-vs-ctreeview"></a>CTreeCtrl vs。CTreeView
MFC 提供封装树控件的两个类： [CTreeCtrl](../mfc/reference/ctreectrl-class.md)和[CTreeView](../mfc/reference/ctreeview-class.md)。 每个类是在不同情况下有用。  
  
 使用`CTreeCtrl`时需要纯子窗口控件; 例如，在对话框中。 尤其是要使用`CTreeCtrl`如果在窗口中，如下所示典型的对话框中将其他子控件。  
  
 使用`CTreeView`你想要的作用像文档/视图体系结构中的视图窗口的树控件和树控件。 A`CTreeView`占用整个工作区的框架窗口或拆分器窗口。 它将自动调整时调整其父窗口大小时，并且它可以处理从菜单、 快捷键和工具栏的命令消息。 树控件包含显示树所必需的数据，因为相应的文档对象不具有要复杂 — 你甚至可以使用[CDocument](../mfc/reference/cdocument-class.md)按照与你的文档模板中的文档类型。  
  
## <a name="see-also"></a>请参阅  
 [使用 CTreeCtrl](../mfc/using-ctreectrl.md)   
 [控件](../mfc/controls-mfc.md)

