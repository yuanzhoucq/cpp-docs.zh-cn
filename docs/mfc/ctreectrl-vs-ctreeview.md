---
title: CTreeCtrl vs。CTreeView |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d71048b6f03f7f1b4400c0a88c178d1b97acdf2f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33342028"
---
# <a name="ctreectrl-vs-ctreeview"></a>CTreeCtrl vs。CTreeView
MFC 提供封装树控件的两个类： [CTreeCtrl](../mfc/reference/ctreectrl-class.md)和[CTreeView](../mfc/reference/ctreeview-class.md)。 每个类是在不同情况下有用。  
  
 使用`CTreeCtrl`时需要纯子窗口控件; 例如，在对话框中。 尤其是要使用`CTreeCtrl`如果在窗口中，如下所示典型的对话框中将其他子控件。  
  
 使用`CTreeView`你想要的作用像文档/视图体系结构中的视图窗口的树控件和树控件。 A`CTreeView`占用整个工作区的框架窗口或拆分器窗口。 它将自动调整时调整其父窗口大小时，并且它可以处理从菜单、 快捷键和工具栏的命令消息。 树控件包含显示树所必需的数据，因为相应的文档对象不具有要复杂 — 你甚至可以使用[CDocument](../mfc/reference/cdocument-class.md)按照与你的文档模板中的文档类型。  
  
## <a name="see-also"></a>请参阅  
 [使用 CTreeCtrl](../mfc/using-ctreectrl.md)   
 [控件](../mfc/controls-mfc.md)

