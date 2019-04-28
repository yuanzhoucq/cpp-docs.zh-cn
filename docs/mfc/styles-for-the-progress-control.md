---
title: 进度控件的样式
ms.date: 11/19/2018
helpviewer_keywords:
- PBS_SMOOTH style
- progress controls [MFC], styles
- PBS_VERTICAL style
- CProgressCtrl class [MFC], styles
ms.assetid: 39eb8081-bc20-4552-91b9-e7cdd1b7d8ae
ms.openlocfilehash: 3adbd32456b1375bd2dc8574220e083ca3d83ee9
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62306791"
---
# <a name="styles-for-the-progress-control"></a>进度控件的样式

在最初创建进度控件 ([cprogressctrl:: Create](../mfc/reference/cprogressctrl-class.md#create))，使用*dwStyle*参数来指定您的进度控件的所需的窗口样式。 以下列表详述了适用的窗口样式。 进度控件将忽略此处列出的窗口样式以外的所有窗口样式。 应始终将进度控件作为子窗口（通常是父对话框的子窗口）创建。

|窗口样式|效果|
|------------------|------------|
|WS_BORDER|在窗口周围创建边框。|
|WS_CHILD|创建子窗口（应始终用于 `CProgressCtrl`）。|
|WS_CLIPCHILDREN|在父窗口中绘制时，将排除子窗口占用的区域。 创建父窗口时使用。|
|WS_CLIPSIBLINGS|相对于彼此裁剪子窗口。|
|WS_DISABLED|创建初始禁用的窗口。|
|WS_VISIBLE|创建初始可见的窗口。|
|WS_TABSTOP|指定当用户按 Tab 键来移动焦点时，进度控件可以接收焦点。|

此外，可以指定两个样式应用于进度控件仅 PBS_VERTICAL 和 PBS_SMOOTH。

使用 PBS_VERTICAL 竖向，而不是水平进度控件。 使用 PBS_SMOOTH 完全，而不是显示以增量方式填充控件的小界定的方块填充进度控件。

而无需 PBS_SMOOTH 样式：

![标准进度栏样式](../mfc/media/vc4ruw1.gif "标准进度栏样式")

PBS_SMOOTH 和 PBS_VERTICAL 样式：

![进度栏样式，平滑和垂直](../mfc/media/vc4ruw2.gif "进度栏样式，平滑和垂直")

有关详细信息，请参阅[的窗口样式](../mfc/reference/styles-used-by-mfc.md#frame-window-styles-mfc)中*MFC 参考*。

## <a name="see-also"></a>请参阅

[使用 CProgressCtrl](../mfc/using-cprogressctrl.md)
