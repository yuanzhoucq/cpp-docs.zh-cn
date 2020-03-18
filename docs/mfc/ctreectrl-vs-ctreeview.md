---
title: CTreeCtrl 与 CTreeView
ms.date: 11/04/2016
helpviewer_keywords:
- tree view controls
- CTreeCtrl class [MFC], vs. CTreeView class [MFC]
- CTreeView class [MFC], vs. CTreeCtrl class [MFC]
- tree controls [MFC], and tree view
ms.assetid: bba5af25-103f-4b53-84d3-071bc9bd6494
ms.openlocfilehash: 7c78dfa9920c913fdbedb009c5a6f275a3e3e273
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/17/2020
ms.locfileid: "79445229"
---
# <a name="ctreectrl-vs-ctreeview"></a>CTreeCtrl 与 CTreeView

MFC 提供了两个用于封装树控件的类： [CTreeCtrl](../mfc/reference/ctreectrl-class.md)和[CTreeView](../mfc/reference/ctreeview-class.md)。 每个类在不同情况下都很有用。

需要普通的子窗口控件时，请使用 `CTreeCtrl`;例如，在对话框中。 如果窗口中存在其他子控件（如典型对话框），则特别需要使用 `CTreeCtrl`。

当你希望树控件在文档/视图体系结构中与视图窗口一起工作时，请使用 `CTreeView`，并使用树控件。 `CTreeView` 将占用框架窗口或拆分器窗口的整个工作区。 它将在其父窗口调整大小时自动调整大小，并可处理菜单、快捷键和工具栏上的命令消息。 由于树控件包含显示树所需的数据，因此对应的文档对象不必太复杂，甚至可以使用[CDocument](../mfc/reference/cdocument-class.md)作为文档模板中的文档类型。

## <a name="see-also"></a>另请参阅

[使用 CTreeCtrl](../mfc/using-ctreectrl.md)<br/>
[控件](../mfc/controls-mfc.md)
