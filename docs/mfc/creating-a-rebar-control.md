---
title: 创建 Rebar 控件
ms.date: 11/04/2016
helpviewer_keywords:
- rebar controls [MFC], creating
- CReBarCtrl class [MFC], creating
ms.assetid: 0a012e08-772b-4f6a-af86-7cb651d11d3e
ms.openlocfilehash: 6828fa3b47eaa1e29579b09611d85cd68702c332
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84617127"
---
# <a name="creating-a-rebar-control"></a>创建 Rebar 控件

应在父对象可见之前创建[CReBarCtrl](reference/crebarctrl-class.md)对象。 这将最大限度降低出现绘画问题的可能性。

例如，rebar 控件（在框架窗口对象中使用）通常用作工具栏控件的父窗口。 因此，rebar 控件的父级是框架窗口对象。 由于框架窗口对象是父级，因此父级的 `OnCreate` 成员函数是创建 rebar 控件的极佳位置。

为了使用 `CReBarCtrl` 对象，您通常将执行下列步骤：

### <a name="to-use-a-crebarctrl-object"></a>使用 CReBarCtrl 对象

1. 构造[CReBarCtrl](reference/crebarctrl-class.md)对象。

1. 调用[create](reference/crebarctrl-class.md#create)创建 Windows rebar 公共控件并将其附加到 `CReBarCtrl` 对象，并指定任何所需样式。

1. 使用对[CBitmap：： LoadBitmap](reference/cbitmap-class.md#loadbitmap)的调用加载位图，以用作 rebar 控件对象的背景。

1. 创建并初始化将由 rebar 控件对象包含的任何子窗口对象（工具栏、对话框控件等）。

1. 使用要插入的带区的必要信息初始化**REBARBANDINFO**结构。

1. 调用[InsertBand](reference/crebarctrl-class.md#insertband) ，将现有的子窗口（例如 `m_wndReToolBar` ）插入到新的 rebar 控件中。 有关将带区插入现有 rebar 控件的详细信息，请参阅[Rebar 控件和带区](rebar-controls-and-bands.md)。

## <a name="see-also"></a>另请参阅

[使用 CReBarCtrl](using-crebarctrl.md)<br/>
[控件](controls-mfc.md)
