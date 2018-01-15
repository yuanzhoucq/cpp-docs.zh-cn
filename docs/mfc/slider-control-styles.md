---
title: "滑块控件样式 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- slider controls [MFC], styles
- CSliderCtrl class [MFC], styles
- styles [MFC], CSliderCtrl
- styles [MFC], slider controls
ms.assetid: 64c491fc-5af1-4f97-ae30-854071b3dc02
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 747f5d55821c6911e80087ebbad65b2169e6fc49
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="slider-control-styles"></a>滑块控件样式
滑块控件 ([CSliderCtrl](../mfc/reference/csliderctrl-class.md)) 可以具有垂直或水平方向。 该控件可以在任意一侧带有刻度线，可以两侧都有刻度线，也可以两侧都没有刻度线。 它们还可用于指定一系列连续值。 这些属性是使用滑块控件样式控制的，您可以在创建滑块控件时指定该样式。  
  
 `TBS_HORZ` 和 `TBS_VERT` 样式确定滑块控件的方向。 如果您不指定方向，滑块控件将采用水平方向。  
  
 `TBS_AUTOTICKS` 样式创建一个滑块控件，并且滑块上带有表示其值范围内的每个增量的刻度线。 在调用时，将自动添加这些刻度线[SetRange](../mfc/reference/csliderctrl-class.md#setrange)成员函数。 如果不指定`TBS_AUTOTICKS`，你可以使用成员函数，如[SetTic](../mfc/reference/csliderctrl-class.md#settic)和[SetTicFreq](../mfc/reference/csliderctrl-class.md#setticfreq)，以指定的刻度线的位置。 若要创建不显示刻度线的滑块控件，您可以使用 `TBS_NOTICKS` 样式。  
  
 可以在滑块控件的任意一侧或两侧显示刻度线。 对于水平滑块控件，可以指定 `TBS_BOTTOM` 或 `TBS_TOP` 样式。 对于垂直滑块控件，可以指定 `TBS_RIGHT` 或 `TBS_LEFT` 样式。 （`TBS_BOTTOM` 和 `TBS_RIGHT` 为默认设置。）对于位于采用任何方向的滑块控件的两侧的刻度线，请指定 `TBS_BOTH` 样式。  
  
 仅当您在创建滑块控件时指定了 `TBS_ENABLESELRANGE` 样式时，该控件才能显示选择范围。 当滑块控件具有此样式时，选择范围的起始和结尾位置的刻度线将显示为三角形（而不是垂直的短划线），并且选择范围将突出显示。 例如，选择范围可能在简单的日程安排应用程序中很有用。 用户可选择与一天中的小时对应的刻度线范围来标识已安排的会议时间。  
  
 默认情况下，控件滑块的长度随选择范围的更改而更改。 如果滑块控件具有**TBS_FIXEDLENGTH**样式，将滑块的长度保持不变，即使选择范围发生变化。 滑块控件有**TBS_NOTHUMB**样式不包含滑块。  
  
## <a name="see-also"></a>请参阅  
 [使用 CSliderCtrl](../mfc/using-csliderctrl.md)   
 [控件](../mfc/controls-mfc.md)

