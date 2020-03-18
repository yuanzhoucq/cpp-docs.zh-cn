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
ms.openlocfilehash: 79b499533196447898ce62ea9dc86c1674fc0302
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/17/2020
ms.locfileid: "79446424"
---
# <a name="setting-the-mode-of-a-cstatusbarctrl-object"></a>设置 CStatusBarCtrl 对象的模式

`CStatusBarCtrl` 对象有两种模式： simple 和不简单。 在大多数情况下，状态栏控件将有一个或多个部件以及文本和图标或图标。 这称为不简单模式。 有关此模式的详细信息，请参阅[初始化 CStatusBarCtrl 对象的各个部分](../mfc/initializing-the-parts-of-a-cstatusbarctrl-object.md)。

但是，在某些情况下，只需显示一行文本。 在这种情况下，简单模式足以满足您的需求。 若要将 `CStatusBarCtrl` 对象的模式更改为 simple，请调用[SetSimple](../mfc/reference/cstatusbarctrl-class.md#setsimple)成员函数。 一旦状态栏控件处于简单模式，就可通过调用 `SetText` 成员函数设置文本，并将255作为*nPane*参数的值传递。

您可以使用[IsSimple](../mfc/reference/cstatusbarctrl-class.md#issimple)函数来确定 `CStatusBarCtrl` 对象所处的模式。

> [!NOTE]
>  如果状态栏对象将从不简单更改为 simple （或相反），则会立即重绘窗口，如果适用，将自动还原任何定义的部件。

## <a name="see-also"></a>另请参阅

[使用 CStatusBarCtrl](../mfc/using-cstatusbarctrl.md)<br/>
[控件](../mfc/controls-mfc.md)
