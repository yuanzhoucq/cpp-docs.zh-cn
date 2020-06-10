---
title: 初始化 CStatusBarCtrl 对象的组成部分
ms.date: 11/04/2016
helpviewer_keywords:
- CStatusBarCtrl class [MFC], simple mode
- status bars [MFC], declaring parts of
- simple status bars [MFC]
- status bars [MFC], icons
- status bars [MFC], simple mode
- icons, using in status bars
- CStatusBarCtrl class [MFC], declaring parts of
ms.assetid: 60e8f285-d2d8-424a-a6ea-2fc548370303
ms.openlocfilehash: bd099a67d9f11cc3657a91b4141d3f18c6fa719d
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84621655"
---
# <a name="initializing-the-parts-of-a-cstatusbarctrl-object"></a>初始化 CStatusBarCtrl 对象的组成部分

默认情况下，状态栏使用独立的窗格显示状态信息。 这些窗格（也称为部件）可包含文本字符串、图标或两者。

使用[SetParts](reference/cstatusbarctrl-class.md#setparts)定义状态栏将具有的部分和长度。 创建状态栏的各个部分后，调用[SetText](reference/cstatusbarctrl-class.md#settext)和[SetIcon](reference/cstatusbarctrl-class.md#seticon)以设置状态栏的特定部分的文本或图标。 成功设置部件后，控件会自动重绘。

以下示例初始化具有四个窗格的现有 `CStatusBarCtrl` 对象 (`m_StatusBarCtrl`)，然后在第二个部件中设置一个图标 (IDI_ICON1) 和一些文本。

[!code-cpp[NVC_MFCControlLadenDialog#31](codesnippet/cpp/initializing-the-parts-of-a-cstatusbarctrl-object_1.cpp)]

有关将对象模式设置为 "简单" 的详细信息 `CStatusBarCtrl` ，请参阅[设置 CStatusBarCtrl 对象的模式](setting-the-mode-of-a-cstatusbarctrl-object.md)。

## <a name="see-also"></a>另请参阅

[使用 CStatusBarCtrl](using-cstatusbarctrl.md)<br/>
[控件](controls-mfc.md)
