---
title: "从图像列表拖动图像 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- CImageList class [MFC], dragging images from
- dragging images from image lists [MFC]
- image lists [MFC], dragging images from
- images [MFC], dragging from image lists
ms.assetid: af691db8-e4f0-4046-b7b9-9acc68d3713d
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 792f112952493fe1ee86d52a6a235604ebee9db5
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="dragging-images-from-an-image-list"></a>从图像列表拖动图像
[CImageList](../mfc/reference/cimagelist-class.md)包含在屏幕上拖动图像的函数。 拖动函数可以流畅地拖动图像，光标没有任何闪烁。 添加了蒙板的图像和未添加蒙板的图像均可拖动。  
  
 [BeginDrag](../mfc/reference/cimagelist-class.md#begindrag)成员函数开始拖动操作。 参数包括要拖动图像的索引和图像中作用点的位置。 作用点是拖动函数识别为图像的确切屏幕位置的单一像素。 通常，应用程序将设置作用点，以便它与鼠标光标的作用点一致。 [DragMove](../mfc/reference/cimagelist-class.md#dragmove)成员函数将映像移动到新位置。  
  
 [DragEnter](../mfc/reference/cimagelist-class.md#dragenter)成员函数设置一个窗口中拖动图像的初始位置，并将图像绘制的位置。 参数包括一个指向绘制图像窗口的指针和一个指定窗口中初始位置的坐标的点。 坐标相对于窗口的左上角，而不是工作区。 上述情况同样适用于将坐标作为参数使用的所有图像拖动函数。 这意味着您在指定坐标时必须补偿窗口元素的宽度，如边框、标题栏和菜单栏。 如果指定**NULL**窗口句柄时调用`DragEnter`、 拖动函数与桌面窗口中，关联的设备上下文中绘制图像并且坐标相对于屏幕左上角。  
  
 `DragEnter` 在拖动操作期间将锁定给定窗口的所有其他更新。 如果你需要执行任何绘图在拖动操作，如突出显示拖放操作的目标可以通过使用临时隐藏拖动的图像[DragLeave](../mfc/reference/cimagelist-class.md#dragleave)成员函数。 你还可以使用[DragShowNoLock](../mfc/reference/cimagelist-class.md#dragshownolock)成员函数。  
  
 调用[EndDrag](../mfc/reference/cimagelist-class.md#enddrag)完成后拖动图像。  
  
 [SetDragCursorImage](../mfc/reference/cimagelist-class.md#setdragcursorimage)成员函数通过与当前拖动图像组合给定的图像 （通常是鼠标光标图像） 来创建新的拖动图像。 由于拖动函数将在拖动操作期间使用新的映像，你应使用 Windows [ShowCursor](http://msdn.microsoft.com/library/windows/desktop/ms648396)函数调用后隐藏实际鼠标光标`SetDragCursorImage`。 否则，系统在拖动操作期间可能看起来具有两个鼠标光标。  
  
 当应用程序调用 `BeginDrag` 后，系统将创建一个临时的内部图像列表并将指定拖动图像复制到内部列表中。 你可以使用来检索指向临时拖动图像列表的指针[GetDragImage](../mfc/reference/cimagelist-class.md#getdragimage)成员函数。 此函数还将检索当前拖动位置和拖动图像相对于拖动位置的偏移量。  
  
## <a name="see-also"></a>请参阅  
 [使用 CImageList](../mfc/using-cimagelist.md)   
 [控件](../mfc/controls-mfc.md)

