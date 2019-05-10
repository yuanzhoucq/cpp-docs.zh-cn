---
title: 设置 CStatusBarCtrl 对象的模式
ms.date: 11/04/2016
f1_keywords:
- CStatusBarCtrl
helpviewer_keywords:
- simple mode and status bar controls
- IsSimple method, using
- SetSimple method [MFC]
- status bar controls [MFC], simple and nonsimple modes
- non-simple mode and status bar controls
- CStatusBarCtrl class [MFC], simple and nonsimple modes
ms.assetid: ca6076e5-1501-4e33-8d35-9308941e46c0
ms.openlocfilehash: a6d1a0edb356f9737aa287809dd8bca4146c1854
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62307713"
---
# <a name="setting-the-mode-of-a-cstatusbarctrl-object"></a>设置 CStatusBarCtrl 对象的模式

有两种模式`CStatusBarCtrl`对象： 简单和非简单。 在大多数情况下，在状态栏控件将具有一个或多个部分，以及文本和可能是一个图标或图标。 这被称为非简单模式。 此模式的详细信息，请参阅[初始化 CStatusBarCtrl 对象的组成部分](../mfc/initializing-the-parts-of-a-cstatusbarctrl-object.md)。

但是，有情况下，只需要显示单行文本。 在这种情况下，简单模式足以满足你的需求。 若要更改的模式`CStatusBarCtrl`对象为 simple 时，调用[SetSimple](../mfc/reference/cstatusbarctrl-class.md#setsimple)成员函数。 在简单模式下状态栏控件后，通过调用设置的文本`SetText`成员函数，传递的值为 255 *nPane*参数。

可以使用[IsSimple](../mfc/reference/cstatusbarctrl-class.md#issimple)函数来确定哪种模式`CStatusBarCtrl`对象处于。

> [!NOTE]
>  如果，反之亦然，立即重绘窗口或状态栏对象从不简单更改为简单的、 和，如果适用，将自动还原任何已定义的部件。

## <a name="see-also"></a>请参阅

[使用 CStatusBarCtrl](../mfc/using-cstatusbarctrl.md)<br/>
[控件](../mfc/controls-mfc.md)
