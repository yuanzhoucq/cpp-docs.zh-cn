---
title: "调节按钮样式 | Microsoft Docs"
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
  - "CSpinButtonCtrl 类, 样式"
  - "数值调节钮控件, 样式"
  - "样式, CSpinButtonCtrl"
  - "样式, 数值调节钮控件"
ms.assetid: fb4a7f6f-9182-47be-bccf-0728fdc5332f
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 调节按钮样式
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

许多旋转按钮 \([CSpinButtonCtrl](../mfc/reference/cspinbuttonctrl-class.md)\) 设置由样式控制。  使用 **属性** 窗口在对话框编辑器，您可以设置以下样式。  
  
-   水平或垂直的**方向**。  控件的方向箭头按钮。  与 `UDS_HORZ` 样式。  
  
-   **对齐**一独立，左侧或右侧。  旋转按钮控件的位置。  左右位置"合作者旁边的旋转按钮。  合作者窗口的宽度会降低将旋转按钮。  与 `UDS_ALIGNLEFT` 和 `UDS_ALIGNRIGHT` 样式。  
  
-   **Auto Buddy** 自动选中上一个窗口，窗口中的区分合作者到旋转按钮。  在对话框模板，这是前在 Tab 键顺序中的数值调节钮按钮的控件。  与 `UDS_AUTOBUDDY` 样式。  
  
-   在当前位置，更改**Set Buddy Integer** 使旋转控件增大和递减合作者窗口的标题。  与 `UDS_SETBUDDYINT` 样式。  
  
-   **No Thousands** 不插入千位分隔符在"合作者窗口的标题的值。  与 `UDS_NOTHOUSANDS` 样式。  
  
    > [!NOTE]
    >  设置了此样式，则要使用对话框数据交换 \(DDX\) 合作者从控件获取整数值。  `DDX_Text` 不接受嵌入一次分隔符。  
  
-   在值超出控件的范围外，递增或递减**换行**生成位置到“包装”。  与 `UDS_WRAP` 样式。  
  
-   在向上键和向下键按下时，**Arrow Keys** 将会旋转按钮递增或递减位置。  与 `UDS_ARROWKEYS` 样式。  
  
## 请参阅  
 [使用 CSpinButtonCtrl](../mfc/using-cspinbuttonctrl.md)   
 [控件](../mfc/controls-mfc.md)