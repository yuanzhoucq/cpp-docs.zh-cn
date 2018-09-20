---
title: 创建 CToolBarCtrl 对象 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- CToolBarCtrl
dev_langs:
- C++
helpviewer_keywords:
- toolbar controls [MFC], creating
- CToolBarCtrl class [MFC], creating toolbars
ms.assetid: a4f6bf0c-0195-4dbf-a09e-aee503e19dc3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c98f99ef7ff26fed7d7df89881d2148af6bc993a
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46421643"
---
# <a name="creating-a-ctoolbarctrl-object"></a>创建 CToolBarCtrl 对象

[CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md)对象包含多个内部数据结构 — 按钮图像的位图的列表、 一系列按钮标签字符串和一系列`TBBUTTON`结构 — 的关联映像和/或带有位置、 样式、 状态、 字符串和按钮的命令 ID。 每个元素的这些数据结构称为按从零开始的索引。 可以使用之前`CToolBarCtrl`对象，你必须设置了这些数据结构。 数据结构的列表，请参阅[工具栏上的控件](controls-mfc.md)Windows SDK 中。 字符串的列表可以仅用于按钮标签;从工具栏中，无法检索字符串。

为了使用 `CToolBarCtrl` 对象，您通常将执行下列步骤：

### <a name="to-use-a-ctoolbarctrl-object"></a>使用 CToolBarCtrl 对象

1. 构造[CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md)对象。

1. 调用[创建](../mfc/reference/ctoolbarctrl-class.md#create)若要创建 Windows 工具栏公共控件并将其附加到`CToolBarCtrl`对象。 如果你想位图图像的按钮，按钮位图向工具栏添加通过调用[AddBitmap](../mfc/reference/ctoolbarctrl-class.md#addbitmap)。 如果您希望字符串标签的按钮，将字符串添加到工具栏通过调用[AddString](../mfc/reference/ctoolbarctrl-class.md#addstring)和/或[AddStrings](../mfc/reference/ctoolbarctrl-class.md#addstrings)。 在调用`AddString`和/或`AddStrings`，应调用[AutoSize](../mfc/reference/ctoolbarctrl-class.md#autosize)以获取字符串或字符串才会显示。

1. 通过调用向工具栏添加按钮结构[AddButtons](../mfc/reference/ctoolbarctrl-class.md#addbuttons)。

1. 如果所需的工具提示，处理**TTN_NEEDTEXT**中所述，在工具栏的所有者窗口消息[处理工具提示通知](../mfc/handling-tool-tip-notifications.md)。

1. 如果您想让用户能够自定义工具栏，处理所有者窗口中的自定义通知消息中所述[处理自定义通知](../mfc/handling-customization-notifications.md)。

## <a name="see-also"></a>请参阅

[使用 CToolBarCtrl](../mfc/using-ctoolbarctrl.md)<br/>
[控件](../mfc/controls-mfc.md)

