---
title: 向选项卡控件添加选项卡
ms.date: 11/04/2016
helpviewer_keywords:
- tab controls [MFC], adding tabs
- putting tabs on CTabCtrls [MFC]
- CTabCtrl class [MFC], adding tabs
- tabs [MFC], adding to CTabCtrl class [MFC]
ms.assetid: 7f3d9340-e3c7-4c71-9912-be57534ecc78
ms.openlocfilehash: be622035355a68d1527a515bfdcb633a3af274d8
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50618265"
---
# <a name="adding-tabs-to-a-tab-control"></a>向选项卡控件添加选项卡

创建选项卡控件之后 ([CTabCtrl](../mfc/reference/ctabctrl-class.md))，添加所需的任意多个选项卡。

### <a name="to-add-a-tab-item"></a>添加选项卡

1. 准备[TCITEM](/windows/desktop/api/commctrl/ns-commctrl-tagtcitema)结构。

1. 调用[ctabctrl:: Insertitem](../mfc/reference/ctabctrl-class.md#insertitem)，并传入此结构。

1. 针对其他选项卡项目，重复步骤 1 和 2。

有关详细信息，请参阅[创建选项卡控件](/windows/desktop/Controls/tab-controls)Windows SDK 中。

## <a name="see-also"></a>请参阅

[使用 CTabCtrl](../mfc/using-ctabctrl.md)<br/>
[控件](../mfc/controls-mfc.md)

