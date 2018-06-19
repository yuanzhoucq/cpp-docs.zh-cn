---
title: 进度控件的样式 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- PBS_SMOOTH style
- progress controls [MFC], styles
- PBS_VERTICAL style
- CProgressCtrl class [MFC], styles
ms.assetid: 39eb8081-bc20-4552-91b9-e7cdd1b7d8ae
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4c1044c82c2864d71047e4fe3c7461d03a17d9d3
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33380105"
---
# <a name="styles-for-the-progress-control"></a>进度控件的样式
当你最初创建进度控件 ([cprogressctrl:: Create](../mfc/reference/cprogressctrl-class.md#create))，使用`dwStyle`参数来指定进度控件的所需的窗口样式。 以下列表详述了适用的窗口样式。 进度控件将忽略此处列出的窗口样式以外的所有窗口样式。 应始终将进度控件作为子窗口（通常是父对话框的子窗口）创建。  
  
|窗口样式|效果|  
|------------------|------------|  
|`WS_BORDER`|在窗口周围创建边框。|  
|**WS_CHILD**|创建子窗口（应始终用于 `CProgressCtrl`）。|  
|**WS_CLIPCHILDREN**|在父窗口中绘制时，将排除子窗口占用的区域。 创建父窗口时，请使用此选项。|  
|**WS_CLIPSIBLINGS**|相对于彼此裁剪子窗口。|  
|**WS_DISABLED**|创建初始禁用的窗口。|  
|**WS_VISIBLE**|创建初始可见的窗口。|  
|**WS_TABSTOP**|指定当用户按 Tab 键来移动焦点时，进度控件可以接收焦点。|  
  
 此外，还可以指定仅适用于进度控件的两种样式：`PBS_VERTICAL` 和 `PBS_SMOOTH`。  
  
 使用 `PBS_VERTICAL` 将进度控件设为垂直方向而不是水平方向。 使用 `PBS_SMOOTH` 完全填充进度控件，而不是显示以增量方式填充进度控件的画有边线的小方块。  
  
 不使用 `PBS_SMOOTH` 样式：  
  
 ![标准进度栏样式](../mfc/media/vc4ruw1.gif "vc4ruw1")  
  
 使用 `PBS_SMOOTH` 和 `PBS_VERTICAL` 样式：  
  
 ![进度栏样式，平滑和垂直](../mfc/media/vc4ruw2.gif "vc4ruw2")  
  
 有关详细信息，请参阅[窗口样式](../mfc/reference/styles-used-by-mfc.md#frame-window-styles-mfc)中*MFC 参考*。  
  
## <a name="see-also"></a>请参阅  
 [使用 CProgressCtrl](../mfc/using-cprogressctrl.md)

