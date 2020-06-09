---
title: 向选项卡控件添加选项卡
ms.date: 11/04/2016
helpviewer_keywords:
- tab controls [MFC], adding tabs
- putting tabs on CTabCtrls [MFC]
- CTabCtrl class [MFC], adding tabs
- tabs [MFC], adding to CTabCtrl class [MFC]
ms.assetid: 7f3d9340-e3c7-4c71-9912-be57534ecc78
ms.openlocfilehash: 89132e94396b51bee4a111b963c67d029f3dd9df
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84616536"
---
# <a name="adding-tabs-to-a-tab-control"></a>向选项卡控件添加选项卡

创建选项卡控件（[CTabCtrl](reference/ctabctrl-class.md)）后，添加所需数量的选项卡。

### <a name="to-add-a-tab-item"></a>添加选项卡

1. 准备[TCITEM](/windows/win32/api/commctrl/ns-commctrl-tcitemw)结构。

1. 调用[CTabCtrl：： InsertItem](reference/ctabctrl-class.md#insertitem)，传递结构。

1. 针对其他选项卡项目，重复步骤 1 和 2。

有关详细信息，请参阅在 Windows SDK 中[创建选项卡控件](/windows/win32/Controls/tab-controls)。

## <a name="see-also"></a>另请参阅

[使用 CTabCtrl](using-ctabctrl.md)<br/>
[控件](controls-mfc.md)
