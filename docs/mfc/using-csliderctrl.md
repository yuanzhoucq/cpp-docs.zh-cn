---
title: "使用 CSliderCtrl | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CSliderCtrl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CSliderCtrl 类, using"
  - "滑块控件, using"
ms.assetid: 242c7bcd-126e-4b9b-8f76-8082ad06fe73
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 使用 CSliderCtrl
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

[CSliderCtrl](../mfc/reference/csliderctrl-class.md) 类表示滑块控件，也称为刻度条。  滑块控件是一个窗口包含滑块和选项刻度线。  当用户移动滑块时，使用鼠标或箭头键，滑块控件发送通知消息指示更改。  
  
 当您希望让用户选择一种离散值或一组连续的值在一个范围中时滑动控件很有用。  例如，您可能使用滑块控件允许用户通过移动滑块设置键盘重复速率到给定刻度线。  
  
 当你创建它时滑块控件的滑块移动指定的增量。  例如，如果指定滑块控件应当具有范围五，滑块只能占用六个位置：在滑块控件的左侧有一个位置且范围中的每个增量有一个位置。  通常，这些位置中的每个部分由一个刻度线的确定。  
  
## 您想进一步了解什么？  
  
-   [使用滑块控件](../mfc/using-slider-controls.md)  
  
-   [滑块控件样式](../mfc/slider-control-styles.md)  
  
-   [滑块控件成员函数](../mfc/slider-control-member-functions.md)  
  
-   [滑块通知消息](../mfc/slider-notification-messages.md)  
  
## 请参阅  
 [控件](../mfc/controls-mfc.md)