---
title: 创建 Rebar 控件
ms.date: 11/04/2016
helpviewer_keywords:
- rebar controls [MFC], creating
- CReBarCtrl class [MFC], creating
ms.assetid: 0a012e08-772b-4f6a-af86-7cb651d11d3e
ms.openlocfilehash: 0fb651aef599b64b787d96a668e2e1496c1dff8e
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/04/2019
ms.locfileid: "57274442"
---
# <a name="creating-a-rebar-control"></a>创建 Rebar 控件

[CReBarCtrl](../mfc/reference/crebarctrl-class.md)父对象可见之前，应该创建对象。 这将最大限度降低出现绘画问题的可能性。

例如，rebar 控件（在框架窗口对象中使用）通常用作工具栏控件的父窗口。 因此，rebar 控件的父级是框架窗口对象。 由于框架窗口对象是父级，因此父级的 `OnCreate` 成员函数是创建 rebar 控件的极佳位置。

为了使用 `CReBarCtrl` 对象，您通常将执行下列步骤：

### <a name="to-use-a-crebarctrl-object"></a>使用 CReBarCtrl 对象

1. 构造[CReBarCtrl](../mfc/reference/crebarctrl-class.md)对象。

1. 调用[创建](../mfc/reference/crebarctrl-class.md#create)若要创建 Windows rebar 公共控件并将其附加到`CReBarCtrl`对象，指定任何所需样式。

1. 加载位图，通过调用[cbitmap:: Loadbitmap](../mfc/reference/cbitmap-class.md#loadbitmap)、 要用作背景的 rebar 控件对象。

1. 创建并初始化将由 rebar 控件对象包含的任何子窗口对象（工具栏、对话框控件等）。

1. 初始化**REBARBANDINFO**使用带区将插入所需信息的结构。

1. 调用[InsertBand](../mfc/reference/crebarctrl-class.md#insertband)要插入现有子窗口 (如`m_wndReToolBar`) 到新的 rebar 控件。 带区插入现有 rebar 控件的详细信息，请参阅[Rebar 控件和带区](../mfc/rebar-controls-and-bands.md)。

## <a name="see-also"></a>请参阅

[使用 CReBarCtrl](../mfc/using-crebarctrl.md)<br/>
[控件](../mfc/controls-mfc.md)
