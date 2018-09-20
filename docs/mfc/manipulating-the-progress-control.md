---
title: 操作进度控件 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- CProgressCtrl class [MFC], working with
- progress controls [MFC], manipulating
- CProgressCtrl class [MFC], manipulating
- controlling progress controls [MFC]
- CProgressCtrl class [MFC], using
ms.assetid: 9af561d1-980b-4003-a6da-ff79be15bf23
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9fe784dfd63ec5c27a3695df3e6bc42ae0de2f7f
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46416768"
---
# <a name="manipulating-the-progress-control"></a>操作进度控件

有三种方式更改进度控件的当前位置 ([CProgressCtrl](../mfc/reference/cprogressctrl-class.md))。

- 可以按预设增量更改位置。

- 可以按任意数量更改位置。

- 位置可以更改为特定值。

### <a name="to-change-the-position-by-a-preset-amount"></a>按预设量更改位置

1. 使用[SetStep](../mfc/reference/cprogressctrl-class.md#setstep)成员函数设置增量。 默认情况下，此值为 10。 此值通常设置为控件的某个初始设置。 步长值可以为负。

1. 使用[StepIt](../mfc/reference/cprogressctrl-class.md#stepit)成员函数递增此位置。 这将导致控件重绘自身。

    > [!NOTE]
    >  `StepIt` 将导致环绕此位置。 例如，给定范围为 1-100，为 20，且位置为 90，`StepIt`将位置设置为 10。

### <a name="to-change-the-position-by-an-arbitrary-amount"></a>按任意数量更改位置

1. 使用[OffsetPos](../mfc/reference/cprogressctrl-class.md#offsetpos)成员函数更改位置。 `OffsetPos` 将接受负值。

    > [!NOTE]
    >  与 `OffsetPos` 不同，`StepIt` 将不会环绕位置。 调整新位置以保持在范围内。

### <a name="to-change-the-position-to-a-specific-value"></a>将位置更改为特定值

1. 使用[SetPos](../mfc/reference/cprogressctrl-class.md#setpos)成员函数以将位置设置为特定值。 如有必要，可调整新位置以使其保持在范围内。

通常，进度控件仅用于输出。 若要获取当前位置而无需指定新值，请使用[GetPos](../mfc/reference/cprogressctrl-class.md#getpos)。

## <a name="see-also"></a>请参阅

[使用 CProgressCtrl](../mfc/using-cprogressctrl.md)<br/>
[控件](../mfc/controls-mfc.md)

