---
title: 向选项卡控件添加选项卡 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- tab controls [MFC], adding tabs
- putting tabs on CTabCtrls [MFC]
- CTabCtrl class [MFC], adding tabs
- tabs [MFC], adding to CTabCtrl class [MFC]
ms.assetid: 7f3d9340-e3c7-4c71-9912-be57534ecc78
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d5f9a9ab897a91fe886a1ba3ad46fe8fab94d94c
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46416586"
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

