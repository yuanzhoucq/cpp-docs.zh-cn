---
title: 设置 CStatusBarCtrl 对象的模式
ms.date: 11/04/2016
helpviewer_keywords:
- simple mode and status bar controls
- IsSimple method, using
- SetSimple method [MFC]
- status bar controls [MFC], simple and nonsimple modes
- non-simple mode and status bar controls
- CStatusBarCtrl class [MFC], simple and nonsimple modes
ms.assetid: ca6076e5-1501-4e33-8d35-9308941e46c0
ms.openlocfilehash: e09a7bd274c44df2da48bbc007a95802fadd8cf0
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365419"
---
# <a name="setting-the-mode-of-a-cstatusbarctrl-object"></a>设置 CStatusBarCtrl 对象的模式

对象有两种`CStatusBarCtrl`模式：简单和非简单。 在大多数情况下，您的状态栏控件将包含一个或多个部分，以及文本，以及图标或图标。 这称为非简单模式。 有关此模式的详细信息，请参阅[初始化 CStatusBarCtrl 对象的部分](../mfc/initializing-the-parts-of-a-cstatusbarctrl-object.md)。

但是，在某些情况下，您只需要显示一行文本。 在这种情况下，简单模式足以满足您的需要。 要将`CStatusBarCtrl`对象模式更改为简单，请调用[SetSimple](../mfc/reference/cstatusbarctrl-class.md#setsimple)成员函数。 状态栏控件处于简单模式后，通过调用`SetText`成员函数设置文本，传递 255 作为*nPane*参数的值。

可以使用[IsSimple](../mfc/reference/cstatusbarctrl-class.md#issimple)函数来确定`CStatusBarCtrl`对象处于何种模式。

> [!NOTE]
> 如果状态栏对象从非简单更改为简单，反之亦然，则立即重新绘制窗口，如果适用，将自动还原任何定义的部件。

## <a name="see-also"></a>另请参阅

[使用 CStatusBarCtrl](../mfc/using-cstatusbarctrl.md)<br/>
[控件](../mfc/controls-mfc.md)
