---
title: 操作进度控件
ms.date: 11/04/2016
helpviewer_keywords:
- CProgressCtrl class [MFC], working with
- progress controls [MFC], manipulating
- CProgressCtrl class [MFC], manipulating
- controlling progress controls [MFC]
- CProgressCtrl class [MFC], using
ms.assetid: 9af561d1-980b-4003-a6da-ff79be15bf23
ms.openlocfilehash: 3e3521a82854a85062f9b06bc33eb268d4b9c7a6
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84622434"
---
# <a name="manipulating-the-progress-control"></a>操作进度控件

有三种方法可以更改进度控件（[CProgressCtrl](reference/cprogressctrl-class.md)）的当前位置。

- 可以按预设增量更改位置。

- 可以按任意数量更改位置。

- 位置可以更改为特定值。

### <a name="to-change-the-position-by-a-preset-amount"></a>按预设量更改位置

1. 使用[SetStep](reference/cprogressctrl-class.md#setstep)成员函数设置增量量。 默认情况下，此值为10。 此值通常设置为控件的某个初始设置。 步长值可以为负。

1. 使用[StepIt](reference/cprogressctrl-class.md#stepit)成员函数递增位置。 这将导致控件重绘自身。

    > [!NOTE]
    >  `StepIt` 将导致环绕此位置。 例如，如果某个范围为 1-100，则步骤为20，位置为90，则 `StepIt` 将其位置设置为10。

### <a name="to-change-the-position-by-an-arbitrary-amount"></a>按任意数量更改位置

1. 使用[OffsetPos](reference/cprogressctrl-class.md#offsetpos)成员函数更改位置。 `OffsetPos` 将接受负值。

    > [!NOTE]
    >  与 `OffsetPos` 不同，`StepIt` 将不会环绕位置。 调整新位置以保持在范围内。

### <a name="to-change-the-position-to-a-specific-value"></a>将位置更改为特定值

1. 使用[SetPos](reference/cprogressctrl-class.md#setpos)成员函数将位置设置为特定值。 如有必要，可调整新位置以使其保持在范围内。

通常，进度控件仅用于输出。 若要获取当前位置而不指定新值，请使用[GetPos](reference/cprogressctrl-class.md#getpos)。

## <a name="see-also"></a>另请参阅

[使用 CProgressCtrl](using-cprogressctrl.md)<br/>
[控件](controls-mfc.md)
