---
title: 使用 CToolTipCtrl 创建和操作 CToolTipCtrl 对象
ms.date: 11/04/2016
f1_keywords:
- CToolTipCtrl
helpviewer_keywords:
- tool tips [MFC], creating
- CToolTipCtrl class [MFC], using
ms.assetid: 0a34583f-f66d-46a1-a239-31b80ea395ad
ms.openlocfilehash: b0f008c70eeb43455408e5b0ad302df6b923608e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62411638"
---
# <a name="using-ctooltipctrl-to-create-and-manipulate-a-ctooltipctrl-object"></a>使用 CToolTipCtrl 创建和操作 CToolTipCtrl 对象

下面是举例[CToolTipCtrl](../mfc/reference/ctooltipctrl-class.md)使用情况：

### <a name="to-create-and-manipulate-a-ctooltipctrl"></a>创建和操作 CToolTipCtrl

1. 构造 `CToolTipCtrl` 对象。

1. 调用[创建](../mfc/reference/ctooltipctrl-class.md#create)创建 Windows 工具提示公共控件并将其附加到`CToolTipCtrl`对象。

1. 调用[AddTool](../mfc/reference/ctooltipctrl-class.md#addtool)与工具提示控件，注册工具，以便在光标位于工具上时显示工具提示中存储的信息。

1. 调用[SetToolInfo](../mfc/reference/ctooltipctrl-class.md#settoolinfo)设置工具提示维护有关工具的信息。

1. 调用[SetToolRect](../mfc/reference/ctooltipctrl-class.md#settoolrect)设置一种工具的新边框。

1. 调用[HitTest](../mfc/reference/ctooltipctrl-class.md#hittest)若要测试的点来确定它是否位于给定工具的边框内，如果是这样，检索有关该工具的信息。

1. 调用[GetToolCount](../mfc/reference/ctooltipctrl-class.md#gettoolcount)若要检索的工具计数注册与工具提示控件。

## <a name="see-also"></a>请参阅

[使用 CToolTipCtrl](../mfc/using-ctooltipctrl.md)<br/>
[控件](../mfc/controls-mfc.md)
