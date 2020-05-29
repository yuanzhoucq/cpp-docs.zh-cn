---
title: 使用 CStatusBarCtrl 创建 CStatusBarCtrl 对象
ms.date: 11/04/2016
helpviewer_keywords:
- status bar controls [MFC], creating
- CStatusBarCtrl class [MFC], creating
ms.assetid: 365c2b65-12de-49e6-9a2e-416c6ee10d60
ms.openlocfilehash: 12d5664b9fc59c4569ec2ee7db4ae883911f7bcd
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/17/2020
ms.locfileid: "79442382"
---
# <a name="using-cstatusbarctrl-to-create-a-cstatusbarctrl-object"></a>使用 CStatusBarCtrl 创建 CStatusBarCtrl 对象

下面是[CStatusBarCtrl](../mfc/reference/cstatusbarctrl-class.md)的典型用法示例：

### <a name="to-use-a-status-bar-control-with-parts"></a>若要将状态栏控件与部件一起使用

1. 构造 `CStatusBarCtrl` 对象。

1. 如果要设置状态栏控件的绘图区域的最小高度，请调用[SetMinHeight](../mfc/reference/cstatusbarctrl-class.md#setminheight) 。

1. 调用[SetBkColor](../mfc/reference/cstatusbarctrl-class.md#setbkcolor)以设置状态栏控件的背景色。

1. 调用[SetParts](../mfc/reference/cstatusbarctrl-class.md#setparts)以设置状态栏控件中的部件数以及每个部件的右边缘的坐标。

1. 调用[SetText](../mfc/reference/cstatusbarctrl-class.md#settext)以设置状态栏控件给定部分中的文本。 此消息会使控件中已更改的部分无效，导致控件下一次接收到 WM_PAINT 消息时显示新文本。

在某些情况下，状态栏只需要显示一行文本。 在这种情况下，请调用[SetSimple](../mfc/reference/cstatusbarctrl-class.md#setsimple)。 这会将状态栏控件置于 "简单" 模式，这种模式显示单行文本。

## <a name="see-also"></a>另请参阅

[使用 CStatusBarCtrl](../mfc/using-cstatusbarctrl.md)<br/>
[控件](../mfc/controls-mfc.md)
