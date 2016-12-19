---
title: "滑块控件成员函数 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CSliderCtrl 类, 方法"
  - "滑块控件, 成员函数"
ms.assetid: dbde49ee-7306-4d14-a6ce-d09aa198178f
caps.latest.revision: 11
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 滑块控件成员函数
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

应用程序可以调用滑块控件的成员函数检索有关滑块控件 \([CSliderCtrl](../mfc/reference/csliderctrl-class.md)\) 的信息和更改其特性。  
  
 若要检索滑块 \(即用户选择\) 的值的位置，请使用 [GetPos](../Topic/CSliderCtrl::GetPos.md) 成员函数。  若要设置滑块的位置，请使用 [SetPos](../Topic/CSliderCtrl::SetPos.md) 成员函数。  随时都可以使用 `VerifyPos` 成员确保函数，滑块在最小值和最大值之间。  
  
 Slider 控件的范围是滑块控件能够表示的组连续的值。  则首次创建时，大多数应用程序使用 [SetRange](../Topic/CSliderCtrl::SetRange.md) 成员函数设置滑块控件的范围。  使用 [SetRangeMax](../Topic/CSliderCtrl::SetRangeMax.md)[SetRangeMin](../Topic/CSliderCtrl::SetRangeMin.md) 和成员函数，应用程序可以在滑块控件之后动态修改范围创建。  允许范围动态特性更改的应用程序检索最终范围设置，当用户完成与滑块控件时。  若要检索这些设置，请使用 [GetRange](../Topic/CSliderCtrl::GetRange.md)[GetRangeMax](../Topic/CSliderCtrl::GetRangeMax.md)[GetRangeMin](../Topic/CSliderCtrl::GetRangeMin.md)、和成员函数。  
  
 应用程序可以使用 `TBS_AUTOTICKS` 样式将自动显示的滑块控件的刻度线。  如果应用程序确实需要控制位置或刻度线的频率，但是，可以使用很多的成员函数。  
  
 若要设置一个刻度线的位置，则应用程序可以使用 [SetTic](../Topic/CSliderCtrl::SetTic.md) 成员函数。  [SetTicFreq](../Topic/CSliderCtrl::SetTicFreq.md) 成员函数允许应用程序设置定期显示滑块控件范围的刻度线。  例如，应用程序只能使用该成员函数在某一范围内显示刻度 10 行 1 到 100。  
  
 若要检索在范围的索引对应于刻度一行对应，请使用 [GetTic](../Topic/CSliderCtrl::GetTic.md) 成员函数。  [GetTicArray](../Topic/CSliderCtrl::GetTicArray.md) 成员函数检索这些数组索引。  若要检索一个刻度线的位置，在坐标，请使用 [GetTicPos](../Topic/CSliderCtrl::GetTicPos.md) 成员函数。  使用 [GetNumTics](../Topic/CSliderCtrl::GetNumTics.md) 成员函数，应用程序便可以检索的刻度线数量。  
  
 [ClearTics](../Topic/CSliderCtrl::ClearTics.md) 成员函数中移除所有滑块控件的刻度线。  
  
 如果应用程序收到 **TB\_LINEDOWN** 或 **TB\_LINEUP** 通知消息时，滑块控制行范围边缘多远确定滑块移动。  同样，页大小确定对 **TB\_PAGEDOWN** 和 **TB\_PAGEUP** 消息通知的响应。  使用 [GetLineSize](../Topic/CSliderCtrl::GetLineSize.md)[SetLineSize](../Topic/CSliderCtrl::SetLineSize.md)[GetPageSize](../Topic/CSliderCtrl::GetPageSize.md)[SetPageSize](../Topic/CSliderCtrl::SetPageSize.md)、、和成员函数，应用程序便可以检索和设置行和页大小的值。  
  
 应用程序可使用成员函数检索滑块控件的尺寸。  [GetThumbRect](../Topic/CSliderCtrl::GetThumbRect.md) 成员函数检索滑块的边框。  [GetChannelRect](../Topic/CSliderCtrl::GetChannelRect.md) 成员函数检索控制通道滑块的边框。通道 \(是滑块移动，并突出显示包含的区域，则范围选择。\)  
  
 如果滑块控件都有 `TBS_ENABLESELRANGE` 样式，用户还可以选择值域从该的连续值。  允许选择范围动态调整许多的成员函数。  [SetSelection](../Topic/CSliderCtrl::SetSelection.md) 成员函数设置选择的开始位置和结束位置。  当用户完成选择设置范围时，可以使用 [GetSelection](../Topic/CSliderCtrl::GetSelection.md) 成员函数，应用程序便可以检索设置。  若要清除用户的选择，请使用 [ClearSel](../Topic/CSliderCtrl::ClearSel.md) 成员函数。  
  
## 请参阅  
 [使用 CSliderCtrl](../mfc/using-csliderctrl.md)   
 [控件](../mfc/controls-mfc.md)