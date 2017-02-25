---
title: "从图像列表绘制图像 | Microsoft Docs"
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
  - "CImageList 类, 绘制图像自"
  - "绘图, 来自图像列表的图像"
  - "图像列表 [C++], 绘制图像自"
  - "图像 [C++], 绘图"
ms.assetid: 2f6063fb-1c28-45f8-a333-008c064db11c
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# 从图像列表绘制图像
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

若要绘制图像，请使用 [CImageList::Draw](../Topic/CImageList::Draw.md) 成员函数。  您将指定指针到设备上下文对象，所要绘制图像的索引，图像在设备上下文中的位置，和一组指定绘图风格的标志。  
  
 当指定 `ILD_TRANSPARENT` 样式时， **绘制**使用两部过程来绘制过滤的图像。  首先，它对图像的位和遮蔽的位和进行了一个逻辑与操作。  然后在第一次操作的结果和目标设备上下文的背景位上进行逻辑异或操作。  此过程会在结果图像中创建一个透明区域；即是在掩码中的白位会使相应的结果图像中的位变为透明。  
  
 在纯色背景下绘制被遮掩的图像之前，应使用 [SetBkColor](../Topic/CImageList::SetBkColor.md) 成员函数将图像列表的背景色设置到和目标色一致。  设置颜色就无需创建图像中的透明区域并使用 **绘制** 将图像复制到目标设备上下文，从而在性能上有显著提升。  当您调用 **绘制**来绘制图像时，请指定 `ILD_NORMAL` 样式。  
  
 可以随时设置 Masked 图像列表 \([CImageList](../mfc/reference/cimagelist-class.md)\) 的背景色，以便在任何纯背景下能正确地绘制图像。  将背景颜色设置为 `CLR_NONE`可以默认地绘制透明的图像。  若要检索图像列表的背景色，请使用 [GetBkColor](../Topic/CImageList::GetBkColor.md) 成员函数。  
  
 `ILD_BLEND25` 和 `ILD_BLEND50` 样式励振用系统高亮颜色显示。  这些样式非常有用，如果你使用一个蒙板的图像来表示一个可以被选择的对象。  例如，当用户选中时，你可以使用 `ILD_BLEND50` 样式来绘制图像。  
  
 使用 图像光栅操作**SRCCOPY**,nonmasked图像可以被复制到目标设备上下文。  不论设备上下文中的背景颜色是什么，图像中的颜色都相同。  在**绘制** 中指定的绘图样式对 nonmasked 图像的外观效果没有影响。  
  
 除了成员函数Draw，另外一个函数[DrawIndirect](../Topic/CImageList::DrawIndirect.md)继承了呈现图像的能力。  `DrawIndirect` 采用，作为参数，[IMAGELISTDRAWPARAMS](http://msdn.microsoft.com/library/windows/desktop/bb761395) 结构。  此结构可用于定义自当前图像的呈现，包括使用的光栅 \(ROP\) 操作代码。   更多有关ROP代码的信息，请参阅[!INCLUDE[winSDK](../atl/includes/winsdk_md.md)]中的[光栅操作代码](http://msdn.microsoft.com/library/windows/desktop/dd162892) [用作画笔的位图](http://msdn.microsoft.com/library/windows/desktop/dd183378) 。  
  
## 请参阅  
 [使用 CImageList](../mfc/using-cimagelist.md)   
 [控件](../mfc/controls-mfc.md)