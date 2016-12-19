---
title: "使用 CSpinButtonCtrl | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CSpinButtonCtrl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CSpinButtonCtrl 类, using"
  - "数值调节钮控件"
  - "up-down 控件"
  - "up-down 控件, 数值调节钮控件"
ms.assetid: a91db36b-e11e-42ef-8e89-51915cc486d2
caps.latest.revision: 14
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 使用 CSpinButtonCtrl
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

*旋转按钮控件* \(也称为 *up\-down* 控件\) 提供用户可单击调整值的一对箭头。  此值称为 *当前位置*。  位置旋转按钮在的范围内进行。  当用户单击此箭头，朝着最大数量；位置此外，用户在单击向下键时，位置被移向最小数量。  
  
 旋转按钮控件 MFC 中由 [CSpinButtonCtrl](../mfc/reference/cspinbuttonctrl-class.md) 类。  
  
> [!NOTE]
>  默认情况下，数值调节钮按钮的范围有最大大小为零 \(0\) 和最小设置为 100。  由于最大值小于最小值，单击箭头将位置降低，再单击向下使其增大。  使用 [CSpinButtonCtrl::SetRange](../Topic/CSpinButtonCtrl::SetRange.md) 调整这些值。  
  
 通常，当前位置显示在该控件。  伴随控件称为" *合作者窗口*。  有关旋转按钮控件的阐释，请参阅《[!INCLUDE[winSDK](../atl/includes/winsdk_md.md)]的 [Up\-Down 关于控件](http://msdn.microsoft.com/library/windows/desktop/bb759889)。  
  
 若要旋转，请创建控件和一个编辑控件合作者窗口，在 Visual Studio 中，首先编辑控件拖动到对话框或窗口，然后拖动调节钮控件。  选择数值调节钮控件并设置其 **自动合作者** 和 **设置合作者整数** 属性设置为 **True**。  并将 **对齐** 属性；**右端对齐** 最典型的。  这些设置中，因为它直接位于在 Tab 键顺序的编辑控件，编辑控件设置为合作者窗口。  编辑控件显示整数和数值调节钮控件处于编辑嵌入控件的右侧。  或者，可以使用 [CSpinButtonCtrl::SetRange](../Topic/CSpinButtonCtrl::SetRange.md) 方法，可以设置数值调节钮控件的有效范围内。  不需要在旋转合作者控件和窗口之间进行事件处理程序进行通信，因为它们直接交换数据。  如果因其他目的，例如，通过 Windows 序列页或对话框来使用数值调节钮控件，然后将 `UDN_DELTAPOS` 消息的处理程序并执行自定义操作的位置。  
  
## 您想进一步了解什么？  
  
-   [调节按钮样式](../mfc/spin-button-styles.md)  
  
-   [调节钮成员函数](../mfc/spin-button-member-functions.md)  
  
## 请参阅  
 [控件](../mfc/controls-mfc.md)