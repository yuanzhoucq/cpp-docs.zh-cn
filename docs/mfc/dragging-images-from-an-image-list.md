---
title: "从图像列表拖动图像 | Microsoft Docs"
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
  - "CImageList 类, 拖动图像自"
  - "从图像列表拖动图像"
  - "图像列表 [C++], 拖动图像自"
  - "图像 [C++], 从图像列表拖动"
ms.assetid: af691db8-e4f0-4046-b7b9-9acc68d3713d
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# 从图像列表拖动图像
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

包含[CImageList](../mfc/reference/cimagelist-class.md) 将函数的图像在屏幕上。  函数将图像拖动的成功，在 Color 和，而任何转换光标。  被遮掩的和撕下伪面具的图像可以拖动。  
  
 [BeginDrag](../Topic/CImageList::BeginDrag.md) 成员函数开始拖动操作。  包括参数拖动图像的索引和作用点的位置在映像中。  作用点是要拖动到的函数识别为图像的确切屏幕位置的一个像素。  通常，应用程序设置的作用点时，使用鼠标光标的作用点进行匹配。  [DragMove](../Topic/CImageList::DragMove.md) 成员函数移到图像新位置。  
  
 [DragEnter](../Topic/CImageList::DragEnter.md) 成员函数设置拖动图像的初始位置。窗口中并绘制图像位置。  包括参数的指针到窗口中绘制图像和最初指定的位置坐标窗口内的。  坐标相对于控件的工作区的左上角来表示。  上述情况同样适用于所有图像拖动函数为协调作为参数。  这意味着必须抵消窗口元素的宽度，例如边框、标题栏和菜单栏，指定坐标。  如果指定 **NULL** 窗口句柄，而调用 `DragEnter`，则拖动的函数在设备上下文绘制图像与桌面窗口，并且，坐标系是相对于屏幕的左上角。  
  
 `DragEnter` 锁定其他更新到特定窗口在拖动操作过程。  如果需要在一个拖动操作时执行任何绘图，如突出显示拖放操作的目标，可以使用 [DragLeave](../Topic/CImageList::DragLeave.md) 成员函数，您可以暂时隐藏拖动的图像。  还可以使用 [DragShowNoLock](../Topic/CImageList::DragShowNolock.md) 成员函数。  
  
 当执行拖动图像时，则请调用 [EndDrag](../Topic/CImageList::EndDrag.md)。  
  
 [SetDragCursorImage](../Topic/CImageList::SetDragCursorImage.md) 成员函数通过将特定图像生成新图像拖动 \(通常鼠标光标图像\)。当拖动图像。  由于将在拖动操作的函数时使用新的图像，您应使用 Windows [ShowCursor](http://msdn.microsoft.com/library/windows/desktop/ms648396) 函数在调用 `SetDragCursorImage`后隐藏实际鼠标光标。  否则，系统可能看起来具有拖动操作的持续时间的两鼠标光标。  
  
 当应用程序调用 `BeginDrag`时，系统会创建一个临时的，在图像列表和复制指定的拖动图像对生成列表。  使用 [GetDragImage](../Topic/CImageList::GetDragImage.md) 成员函数，则可以检索指向临时拖动图像列表。  函数来检索当前位置拖动和拖动图像相对于的偏移量位置拖动。  
  
## 请参阅  
 [使用 CImageList](../mfc/using-cimagelist.md)   
 [控件](../mfc/controls-mfc.md)