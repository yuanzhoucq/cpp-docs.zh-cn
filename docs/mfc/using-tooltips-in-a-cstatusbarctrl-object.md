---
title: 在 CStatusBarCtrl 对象中使用工具提示
ms.date: 11/04/2016
helpviewer_keywords:
- tool tips [MFC], using in status bars
- status bars [MFC], tool tips
- CStatusBarCtrl class [MFC], tool tips
ms.assetid: a77597a7-43ef-4b8f-87bc-a8ea1dc63dc3
ms.openlocfilehash: 29d326c708743424686d616bbaf172ccd72481ce
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374697"
---
# <a name="using-tooltips-in-a-cstatusbarctrl-object"></a>在 CStatusBarCtrl 对象中使用工具提示

要启用状态栏控件的工具提示，`CStatusBarCtrl`请使用SBT_TOOLTIPS样式创建对象。

> [!NOTE]
> 如果要使用 `CStatusBar` 对象实现状态栏，请使用 `CStatusBar::CreateEx` 函数。 它允许您为嵌入`CStatusBarCtrl`对象指定其他样式。

成功创建`CStatusBarCtrl`对象后，请使用[CStatusBarCtrl：：SetTipText](../mfc/reference/cstatusbarctrl-class.md#settiptext)和[CStatusBarCtrl：：获取提示文本](../mfc/reference/cstatusbarctrl-class.md#gettiptext)来设置和检索特定窗格的提示文本。

设置工具提示后，仅当部件具有图标且没有文本，或所有文本无法在部件内显示时才显示工具提示。 简单模式中不支持工具提示。

## <a name="see-also"></a>另请参阅

[使用 CStatusBarCtrl](../mfc/using-cstatusbarctrl.md)<br/>
[控件](../mfc/controls-mfc.md)
