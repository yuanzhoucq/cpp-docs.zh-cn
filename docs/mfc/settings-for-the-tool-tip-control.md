---
title: 设置工具提示控件 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- tool tips [MFC], activating
- CToolTipCtrl class [MFC], settings
ms.assetid: ff8c5c46-2047-403a-bd98-ffec3d21ee3a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6d0adfd1c7a7ae1e1f36fa8dd53610d19ad8e7b2
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46379549"
---
# <a name="settings-for-the-tool-tip-control"></a>工具提示控件的设置

可以将工具提示控件 ([CToolTipCtrl](../mfc/reference/ctooltipctrl-class.md)) 设置为活动或非活动。 如果将其设置为活动状态，当光标位于工具上时，将显示工具提示控件。 如果将其设置为非活动状态，即使光标位于工具上时，也不会显示工具提示控件。 调用 [Activate](../mfc/reference/ctooltipctrl-class.md#activate) 以激活或停用工具提示控件。

您可以设置活动的工具提示显示的工具提示在光标位于工具上时将工具提示控件所有者窗口处于活动状态还是处于非活动状态，使用 TTS_ALWAYSTIP 样式。 如果不使用此样式，工具提示控件将在工具的所有者窗口处于活动状态时显示，当其处于非活动状态时则不显示。

大多数应用程序均有工具栏，工具栏中的工具与菜单命令对应。 对于此类工具，工具提示控件可以方便地显示与相应菜单项相同的文本。 系统自动去除与号 (&) 加速器字符的所有字符串传递给工具提示控件，除非控件具有 TTS_NOPREFIX 样式。

## <a name="see-also"></a>请参阅

[使用 CToolTipCtrl](../mfc/using-ctooltipctrl.md)<br/>
[控件](../mfc/controls-mfc.md)

