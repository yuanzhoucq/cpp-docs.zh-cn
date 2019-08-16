---
title: 回调项和回调掩码
ms.date: 11/04/2016
helpviewer_keywords:
- callback items in CListCtrl class [MFC]
- CListCtrl class [MFC], callback item and callback mask
ms.assetid: 67c1f76f-6144-453e-9376-6712f89430ae
ms.openlocfilehash: 5c326d8498ea297936254a8650f666103ea3c772
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69509133"
---
# <a name="callback-items-and-the-callback-mask"></a>回调项和回调掩码

列表视图控件通常会为它的每一项存储标签文本、项图标的图像列表索引以及表示项状态的一组位标志。 您可以定义单个项作为回调项，当应用程序已经存储某个项的一些信息时，这将很有用。

通过为`pszText` `LVITEM`结构的和`iImage`成员指定适当的值, 将项定义为回调项 (请参见[CListCtrl:: GetItem](../mfc/reference/clistctrl-class.md#getitem))。 如果应用程序维护项或子项的文本, 则为`pszText`成员指定**LPSTR_TEXTCALLBACK**值。 如果应用程序跟踪项的图标, 请指定该`iImage`成员的**I_IMAGECALLBACK**值。

除了定义回调项之外，您还可以修改控件的回调掩码。 此掩码是一组位标志，用于指定应用程序（而不是控件）存储当前数据的项状态。 回调掩码适用于控件的所有项，而回调项指示符则不同，它适用于特定项。 回调掩码默认为零，这意味着控件将跟踪所有项状态。 若要更改此默认行为，请将掩码初始化为以下值的任意组合：

- **LVIS_CUT**该项已标记为进行剪切和粘贴操作。

- **LVIS_DROPHILITED**该项突出显示为拖放目标。

- **LVIS_FOCUSED**该项具有焦点。

- **LVIS_SELECTED**选定该项。

- **LVIS_OVERLAYMASK**应用程序存储每个项的当前覆盖图像的图像列表索引。

- **LVIS_STATEIMAGEMASK**应用程序存储每个项的当前状态图像的图像列表索引。

有关检索和设置此掩码的详细信息, 请参阅[CListCtrl:: GetCallbackMask](../mfc/reference/clistctrl-class.md#getcallbackmask)和[CListCtrl:: SetCallbackMask](../mfc/reference/clistctrl-class.md#setcallbackmask)。

## <a name="see-also"></a>请参阅

[使用 CListCtrl](../mfc/using-clistctrl.md)<br/>
[控件](../mfc/controls-mfc.md)
