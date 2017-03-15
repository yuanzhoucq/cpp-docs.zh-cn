---
title: "滑块控件样式 | Microsoft Docs"
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
  - "CSliderCtrl 类, 样式"
  - "滑块控件, 样式"
  - "样式, CSliderCtrl"
  - "样式, 滑块控件"
ms.assetid: 64c491fc-5af1-4f97-ae30-854071b3dc02
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# 滑块控件样式
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

滑块控件 \([CSliderCtrl](../mfc/reference/csliderctrl-class.md)\) 可以具有垂直或水平方向。  它们不能在任何一方具有刻度线，或双方。  它们还可用于指定范围连续值。  这些属性是通过使用 Slider 控件样式控制的，指定何时创建的滑块控件。  
  
 `TBS_HORZ` 和 `TBS_VERT` 样式确定滑块控件的方向。  如果您不指定方向，滑块控件水平放置。  
  
 `TBS_AUTOTICKS` 样式创建一个递增的刻度线在其范围值的滑块控件。  当调用 [SetRange](../Topic/CSliderCtrl::SetRange.md) 成员函数时，这些刻度行自动添加。  如果未指定 `TBS_AUTOTICKS`，可以使用成员函数，如 [SetTic](../Topic/CSliderCtrl::SetTic.md)和 [SetTicFreq](../Topic/CSliderCtrl::SetTicFreq.md)，指定刻度线的位置。  若要创建不显示刻度线中的滑块控件，则可以使用 `TBS_NOTICKS` 样式。  
  
 可以在滑块控件的任意或两侧显示刻度线。  对于水平滑块控件，可以指定 `TBS_BOTTOM` 或 `TBS_TOP` 样式。  对于垂直滑块控件，可以指定 `TBS_RIGHT` 或 `TBS_LEFT` 样式。（`TBS_BOTTOM` 和 `TBS_RIGHT` 和为默认设置。）对于所有方向的滑块两侧控件刻度线，指定 `TBS_BOTH` 样式。  
  
 滑块控件可以显示选择范围，只有创建它时才能指定 `TBS_ENABLESELRANGE` 样式。  当滑块控件具有此样式时，在启动的刻度线和选择范围的结束位置显示为三角形 \(而不是垂直的短划线\)，然后选择范围突出显示。  例如，在计划的应用程序中选择范围可能很有用。  用户选择刻度线范围与一天中的小时一致，为标识已计划的会议时间。  
  
 默认情况下，控件滑块的长度与选择范围变化成比例。  如果滑块控件具有 **TBS\_FIXEDLENGTH** 样式，滑块的长度保持相同，即使选择范围更改。  **TBS\_NOTHUMB** 具有样式的滑块控件不包括滑块。  
  
## 请参阅  
 [使用 CSliderCtrl](../mfc/using-csliderctrl.md)   
 [控件](../mfc/controls-mfc.md)