---
title: "使用滑块控件 | Microsoft Docs"
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
  - "CSliderCtrl 类, using"
  - "滑块控件"
  - "滑块控件, using"
ms.assetid: 2b1a8ac8-2b17-41e1-aa24-83c1fd737049
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 使用滑块控件
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Slider 控件的典型用法遵循以下模式：  
  
-   创建控件。  如果控件在对话框模板指定的，则该控件在对话框创建时自动创建。\(您应具有对话框类的一个 [CSliderCtrl](../mfc/reference/csliderctrl-class.md) 成员对应于相应的slider控件。\) 或者，可以使用 [创建](../Topic/CSliderCtrl::Create.md) 成员函数来创建控件作为所有窗口的一个子窗口。  
  
-   调用的各种集合成员函数设置控件的值。  更改可包括设置slider空间的 Min 和 Max 位置，绘制刻度线，设置选择范围，和重新定位slider。  若要在对话框的控件，执行这的好时机是在对话框的 [OnInitDialog](../Topic/CDialog::OnInitDialog.md)函数中。  
  
-   当用户与控件交互，将发送的不同通知消息。  您可以通过调用 [GetPos](../Topic/CSliderCtrl::GetPos.md) 成员函数从slider控件的抽取值。  
  
-   当您用完成控件使用时，请确保正确销毁它。  如果slider控件在对话框中，它和 `CSliderCtrl` 对象将被自动销毁。  否则，您需要确保正确销毁控件和 `CSliderCtrl` 对象。  
  
## 请参阅  
 [使用 CSliderCtrl](../mfc/using-csliderctrl.md)   
 [控件](../mfc/controls-mfc.md)