---
title: "进度控件的样式 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CProgressCtrl 类, 样式"
  - "PBS_SMOOTH 样式"
  - "PBS_VERTICAL 样式"
  - "进度控件 [C++], 样式"
ms.assetid: 39eb8081-bc20-4552-91b9-e7cdd1b7d8ae
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# 进度控件的样式
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

在最初创建进度 \([CProgressCtrl::Create](../Topic/CProgressCtrl::Create.md)\)，请使用 `dwStyle` 参数用于进度指定所需窗口样式。  下表详述相应的窗口样式。  控件将忽略所有窗口样式不列出的以外示。  应始终创建控件作为子窗口通常，父对话框。  
  
|窗口样式|效果|  
|----------|--------|  
|`WS_BORDER`|在窗口周围创建边框。|  
|**WS\_CHILD**|创建子窗口 \(应对 `CProgressCtrl`始终使用\)。|  
|**WS\_CLIPCHILDREN**|在父窗口中绘图时，会排除子窗口占用的区域。  在创建父窗口时使用。|  
|**WS\_CLIPSIBLINGS**|剪辑相对的子窗口。|  
|**已禁用**|用于创建初始禁用的窗口。|  
|**WS\_VISIBLE**|创建初始可见的窗口。|  
|**WS\_TABSTOP**|指定控件可以接收焦点，则用户按 Tab 键移动到它。|  
  
 此外，还可以指定仅适用于进度控件`PBS_VERTICAL` 和 `PBS_SMOOTH`的两种方式。  
  
 使用垂直 `PBS_VERTICAL` 放在控件中，而不是水平。  使用 `PBS_SMOOTH` 完全填充控件，而不是显示控件小的增量填充说明的正方形。  
  
 如果没有 `PBS_SMOOTH` 样式：  
  
 ![标准进度栏样式](../mfc/media/vc4ruw1.png "vc4RUW1")  
  
 `PBS_SMOOTH` 和 `PBS_VERTICAL` 样式：  
  
 ![进度栏样式 &#45; 平滑和垂直](../mfc/media/vc4ruw2.png "vc4RUW2")  
  
 有关更多信息，请参见" *MFC 参考"中的*[窗口样式](../mfc/reference/frame-window-styles-mfc.md)。  
  
## 请参阅  
 [使用 CProgressCtrl](../mfc/using-cprogressctrl.md)