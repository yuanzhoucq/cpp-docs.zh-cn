---
title: CTreeCtrl 与CTreeView
ms.date: 11/04/2016
f1_keywords:
- CTreeCtrl
- CTreeView
helpviewer_keywords:
- tree view controls
- CTreeCtrl class [MFC], vs. CTreeView class [MFC]
- CTreeView class [MFC], vs. CTreeCtrl class [MFC]
- tree controls [MFC], and tree view
ms.assetid: bba5af25-103f-4b53-84d3-071bc9bd6494
ms.openlocfilehash: 29349e169e5ad8475001235d9b355da52156d683
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62241907"
---
# <a name="ctreectrl-vs-ctreeview"></a>CTreeCtrl 与CTreeView

MFC 提供了封装树控件的两个类：[CTreeCtrl](../mfc/reference/ctreectrl-class.md)并[CTreeView](../mfc/reference/ctreeview-class.md)。 每个类是在不同情况下很有用。

使用`CTreeCtrl`时需要普通子窗口控件; 例如，在对话框中。 尤其是想要使用`CTreeCtrl`如果在窗口中，如下所示典型的对话框中将其他子控件。

使用`CTreeView`当你想要充当文档/视图体系结构中的视图窗口的树控件和树控件。 一个`CTreeView`将占用整个工作区的拆分器窗口或框架窗口。 它将自动调整时其父窗口的大小调整，并且它可以处理来自菜单、 加速键和工具栏的命令消息。 树控件包含显示树所需的数据，因为相应的文档对象不具有复杂 — 您甚至可以使用[CDocument](../mfc/reference/cdocument-class.md)作为文档模板中的文档类型。

## <a name="see-also"></a>请参阅

[使用 CTreeCtrl](../mfc/using-ctreectrl.md)<br/>
[控件](../mfc/controls-mfc.md)
