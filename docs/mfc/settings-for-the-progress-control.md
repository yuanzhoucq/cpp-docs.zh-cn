---
title: 进度控件的设置
ms.date: 11/04/2016
helpviewer_keywords:
- CProgressCtrl class [MFC], settings
- progress controls [MFC], settings
ms.assetid: f4616e91-74fa-4000-ba0d-d3ddc0ee075b
ms.openlocfilehash: 1960b15c2f76d7cbfc9f249a77481b795e6a27ea
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/04/2019
ms.locfileid: "57290744"
---
# <a name="settings-for-the-progress-control"></a>进度控件的设置

进度控件的基本设置 ([CProgressCtrl](../mfc/reference/cprogressctrl-class.md)) 的范围和当前的位置。 范围表示该操作的整个持续时间。 当前的位置表示你的应用程序已完成该操作方面的进度。 对区域或位置的任何更改会导致进度控件重绘自身。

默认情况下，设置范围为 0-100 和初始位置设置为 0。 若要检索进度控件的当前区域设置，请使用[GetRange](../mfc/reference/cprogressctrl-class.md#getrange)成员函数。 若要更改的范围，请使用[SetRange](../mfc/reference/cprogressctrl-class.md#setrange)成员函数。

若要设置位置，请使用[SetPos](../mfc/reference/cprogressctrl-class.md#setpos)。 若要检索当前的位置，而不指定新值，请使用[GetPos](../mfc/reference/cprogressctrl-class.md#getpos)。 例如，你可能想要只需查询的当前操作状态。

若要单步执行当前进度控件的位置，请使用[StepIt](../mfc/reference/cprogressctrl-class.md#stepit)。 若要设置每个步骤的量，请使用[SetStep](../mfc/reference/cprogressctrl-class.md#setstep)

## <a name="see-also"></a>请参阅

[使用 CProgressCtrl](../mfc/using-cprogressctrl.md)<br/>
[控件](../mfc/controls-mfc.md)
