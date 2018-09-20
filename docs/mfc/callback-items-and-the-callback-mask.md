---
title: 回调项和回调掩码 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- callback items in CListCtrl class [MFC]
- CListCtrl class [MFC], callback item and callback mask
ms.assetid: 67c1f76f-6144-453e-9376-6712f89430ae
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 0711fccb142d9774c37f2cb2d8f576bf7fddd128
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46422839"
---
# <a name="callback-items-and-the-callback-mask"></a>回调项和回调掩码

列表视图控件通常会为它的每一项存储标签文本、项图标的图像列表索引以及表示项状态的一组位标志。 您可以定义单个项作为回调项，当应用程序已经存储某个项的一些信息时，这将很有用。

定义一个项作为回调项指定了相应值来`pszText`并`iImage`的成员**LV_ITEM**结构 (请参阅[clistctrl:: Getitem](../mfc/reference/clistctrl-class.md#getitem))。 如果应用程序需维护项或子项的文本，指定**LPSTR_TEXTCALLBACK**值`pszText`成员。 如果应用程序跟踪的项的图标，指定**I_IMAGECALLBACK**值`iImage`成员。

除了定义回调项之外，您还可以修改控件的回调掩码。 此掩码是一组位标志，用于指定应用程序（而不是控件）存储当前数据的项状态。 回调掩码适用于控件的所有项，而回调项指示符则不同，它适用于特定项。 回调掩码默认为零，这意味着控件将跟踪所有项状态。 若要更改此默认行为，请将掩码初始化为以下值的任意组合：

- **LVIS_CUT**项标记为剪切和粘贴操作。

- **LVIS_DROPHILITED**项被标记为拖放目标。

- **LVIS_FOCUSED**项具有焦点。

- **LVIS_SELECTED**选定项。

- **LVIS_OVERLAYMASK**应用程序存储当前覆盖图像的每个项的图像列表索引。

- **LVIS_STATEIMAGEMASK**应用程序存储的每个项的当前状态图像的图像列表索引。

检索和设置此掩码的进一步信息，请参阅[clistctrl:: Getcallbackmask](../mfc/reference/clistctrl-class.md#getcallbackmask)并[clistctrl:: Setcallbackmask](../mfc/reference/clistctrl-class.md#setcallbackmask)。

## <a name="see-also"></a>请参阅

[使用 CListCtrl](../mfc/using-clistctrl.md)<br/>
[控件](../mfc/controls-mfc.md)

