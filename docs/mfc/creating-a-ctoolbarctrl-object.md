---
title: 创建 CToolBarCtrl 对象
ms.date: 11/04/2016
helpviewer_keywords:
- toolbar controls [MFC], creating
- CToolBarCtrl class [MFC], creating toolbars
ms.assetid: a4f6bf0c-0195-4dbf-a09e-aee503e19dc3
ms.openlocfilehash: 2627f9aaceeab7760e15b23435233e124c5ea6f0
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84619001"
---
# <a name="creating-a-ctoolbarctrl-object"></a>创建 CToolBarCtrl 对象

[CToolBarCtrl](reference/ctoolbarctrl-class.md)对象包含多个内部数据结构（一个按钮图像位图列表、一个按钮标签字符串列表和一个 `TBBUTTON` 结构列表），这些结构将图像和/或字符串与按钮的位置、样式、状态和命令 ID 相关联。 这些数据结构的每个元素均由从零开始的索引引用。 `CToolBarCtrl`必须先设置这些数据结构，然后才能使用对象。 有关数据结构的列表，请参阅 Windows SDK 中的[工具栏控件](controls-mfc.md)。 字符串列表只能用于按钮标签;不能从工具栏检索字符串。

为了使用 `CToolBarCtrl` 对象，您通常将执行下列步骤：

### <a name="to-use-a-ctoolbarctrl-object"></a>使用 CToolBarCtrl 对象

1. 构造[CToolBarCtrl](reference/ctoolbarctrl-class.md)对象。

1. 调用[create](reference/ctoolbarctrl-class.md#create)创建 Windows 工具栏公共控件并将其附加到 `CToolBarCtrl` 对象。 如果希望按钮使用位图图像，请通过调用[AddBitmap](reference/ctoolbarctrl-class.md#addbitmap)将按钮位图添加到工具栏中。 如果需要按钮的字符串标签，请通过调用[AddString](reference/ctoolbarctrl-class.md#addstring)和/或[AddStrings](reference/ctoolbarctrl-class.md#addstrings)将字符串添加到工具栏中。 调用 `AddString` 和/或后 `AddStrings` ，应调用[AutoSize](reference/ctoolbarctrl-class.md#autosize)以便使字符串或字符串显示。

1. 通过调用[AddButtons](reference/ctoolbarctrl-class.md#addbuttons)向工具栏添加按钮结构。

1. 如果需要工具提示，请在工具栏的所有者窗口中处理**TTN_NEEDTEXT**消息，如[处理工具提示通知](handling-tool-tip-notifications.md)中所述。

1. 如果希望用户能够自定义工具栏，请在所有者窗口中处理自定义通知消息，如[处理自定义通知](handling-customization-notifications.md)中所述。

## <a name="see-also"></a>另请参阅

[使用 CToolBarCtrl](using-ctoolbarctrl.md)<br/>
[控件](controls-mfc.md)
