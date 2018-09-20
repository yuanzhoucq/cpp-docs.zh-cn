---
title: 使用树控件 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- CTreeCtrl class [MFC], using
- tree controls [MFC], about tree controls
ms.assetid: 4e92941a-e477-4fb1-b1ce-4abeafbef1c1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1fc3efbf48a9005bf117c2dd7ab5f1bd01ed556d
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46403677"
---
# <a name="using-tree-controls"></a>使用树控件

树控件的典型用法 ([CTreeCtrl](../mfc/reference/ctreectrl-class.md)) 遵循以下模式：

- 创建滑块控件。 如果在对话框模板中指定的控件，或如果您使用的`CTreeView`，创建对话框或视图时，会自动创建。 如果你想要创建的目录树控件用作子窗口的某些其他窗口，使用[创建](../mfc/reference/ctreectrl-class.md#create)成员函数。

- 如果你想要使用映像树控件，通过调用设置图像列表[SetImageList](../mfc/reference/ctreectrl-class.md#setimagelist)。 此外可以通过调用更改缩进[SetIndent](../mfc/reference/ctreectrl-class.md#setindent)。 执行此操作的好时机是在[OnInitDialog](../mfc/reference/cdialog-class.md#oninitdialog) （适用于对话框中的控件） 或[OnInitialUpdate](../mfc/reference/cview-class.md#oninitialupdate) （用于视图）。

- 将数据放入该控件，通过调用`CTreeCtrl`的[InsertItem](../mfc/reference/ctreectrl-class.md#insertitem)函数一次为每个数据项。 `InsertItem` 返回一个句柄可用于引用它更高版本，例如当项添加子项。 初始化的数据的好时机是在`OnInitDialog`（适用于对话框中的控件） 或`OnInitialUpdate`（用于视图）。

- 当用户与该控件交互时，将发送各种通知消息。 可以指定一个函数来处理每个你想要通过在控件窗口的消息映射中添加 ON_NOTIFY_REFLECT 宏或 ON_NOTIFY 宏添加到父窗口的消息映射来处理的消息。 请参阅[树控件通知消息](../mfc/tree-control-notification-messages.md)本主题中有关的可能通知列表更高版本。

- 调用各种 Set 成员函数来设置滑块控件的值。 您可以做的更改包括设置缩进和更改文本、 图像或与项相关联的数据。

- 使用各种的 Get 函数来检查该控件的内容。 您可以遍历的函数，允许您检索的句柄父级、 子级和同级的指定项的树控件的内容。 甚至可以对特定节点的子级进行排序。

- 完成该控件后，请确保正确地销毁。 如果树控件在对话框中，或如果它是一个视图，它和`CTreeCtrl`对象将自动被销毁。 否则，您需要确保正确地销毁控件和 `CTreeCtrl` 对象。

## <a name="see-also"></a>请参阅

[使用 CTreeCtrl](../mfc/using-ctreectrl.md)<br/>
[控件](../mfc/controls-mfc.md)

