---
title: 向标题控件添加项
ms.date: 11/04/2016
helpviewer_keywords:
- controls [MFC], header
- CHeaderCtrl class [MFC], adding items
- header controls [MFC], adding items to
ms.assetid: 2e9a28b1-7302-4a93-8037-c5a4183e589a
ms.openlocfilehash: c751458a3a2e7e049364ef22a161a3dc9f81df13
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50483559"
---
# <a name="adding-items-to-the-header-control"></a>向标题控件添加项

之后创建标题控件 ([CHeaderCtrl](../mfc/reference/cheaderctrl-class.md)) 在其父窗口中，添加任意多个"标头项"所需： 通常每列一个。

### <a name="to-add-a-header-item"></a>添加标题项

1. 准备[HD_ITEM](/windows/desktop/api/commctrl/ns-commctrl-_hd_itema)结构。

1. 调用[cheaderctrl:: Insertitem](../mfc/reference/cheaderctrl-class.md#insertitem)，并传入此结构。

1. 对于其他项，重复步骤 1 和 2。

有关详细信息，请参阅[将项添加到标头控件](/windows/desktop/Controls/header-controls)Windows SDK 中。

## <a name="see-also"></a>请参阅

[使用 CHeaderCtrl](../mfc/using-cheaderctrl.md)<br/>
[控件](../mfc/controls-mfc.md)

