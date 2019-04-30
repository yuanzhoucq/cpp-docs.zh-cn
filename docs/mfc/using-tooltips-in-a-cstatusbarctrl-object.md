---
title: 在 CStatusBarCtrl 对象中使用工具提示
ms.date: 11/04/2016
f1_keywords:
- CStatusBarCtrl
helpviewer_keywords:
- tool tips [MFC], using in status bars
- status bars [MFC], tool tips
- CStatusBarCtrl class [MFC], tool tips
ms.assetid: a77597a7-43ef-4b8f-87bc-a8ea1dc63dc3
ms.openlocfilehash: 3f9a1fec7eb951fa76c542e09df751b4c58ddb16
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62411430"
---
# <a name="using-tooltips-in-a-cstatusbarctrl-object"></a>在 CStatusBarCtrl 对象中使用工具提示

若要启用状态栏控件的工具提示，请创建`CStatusBarCtrl`SBT_TOOLTIPS 样式的对象。

> [!NOTE]
>  如果要使用 `CStatusBar` 对象实现状态栏，请使用 `CStatusBar::CreateEx` 函数。 它允许您指定的嵌入其他样式`CStatusBarCtrl`对象。

一次`CStatusBarCtrl`已成功创建对象，请使用[cstatusbarctrl:: Settiptext](../mfc/reference/cstatusbarctrl-class.md#settiptext)并[cstatusbarctrl:: Gettiptext](../mfc/reference/cstatusbarctrl-class.md#gettiptext)来设置和检索特定窗格的提示文本。

设置工具提示后，仅当部件具有图标且没有文本，或所有文本无法在部件内显示时才显示工具提示。 简单模式中不支持工具提示。

## <a name="see-also"></a>请参阅

[使用 CStatusBarCtrl](../mfc/using-cstatusbarctrl.md)<br/>
[控件](../mfc/controls-mfc.md)
