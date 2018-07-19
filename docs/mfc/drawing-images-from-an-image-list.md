---
title: 从图像列表绘制图像 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- CImageList class [MFC], drawing images from
- drawing [MFC], images from image lists
- image lists [MFC], drawing images from
- images [MFC], drawing
ms.assetid: 2f6063fb-1c28-45f8-a333-008c064db11c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 0ebc05a83eb22d494a75ed474e315112522af3fc
ms.sourcegitcommit: 060f381fe0807107ec26c18b46d3fcb859d8d2e7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/25/2018
ms.locfileid: "36932063"
---
# <a name="drawing-images-from-an-image-list"></a>从图像列表绘制图像
若要绘制图像，请使用[cimagelist:: Draw](../mfc/reference/cimagelist-class.md#draw)成员函数。 您将指定指向设备上下文对象的指针、要绘制的图像的索引、要在其中绘制图像的设备上下文中的位置以及一组表示绘制样式的标志。  
  
 当指定**ILD_TRANSPARENT**样式，`Draw`使用一个两步过程来绘制蒙板的图像。 首先，它对图像的位和蒙板的位执行逻辑“与”操作。 然后对第一次操作的结果和目标设备上下文的背景的位执行逻辑“异或”操作。 此过程会在结果图像中创建透明区域；即蒙板中的每个白色位会使结果图像中相应的位变为透明。  
  
 在纯色背景上绘制蒙板的图像之前, 应使用[SetBkColor](../mfc/reference/cimagelist-class.md#setbkcolor)成员函数将图像列表的背景色设置为与目标相同的颜色。 设置颜色消除图像中创建透明区域的需要并启用`Draw`只需将映像复制到目标设备上下文，从而导致显著的性能提升。 若要绘制图像，指定**ILD_NORMAL**样式在调用时`Draw`。  
  
 你可以设置蒙板的图像列表的背景色 ([CImageList](../mfc/reference/cimagelist-class.md)) 在任何时间，以便它在任何纯色背景上正确绘制。 将背景色设置为**CLR_NONE**会将默认情况下透明地绘制图像。 若要检索图像列表的背景色，请使用[GetBkColor](../mfc/reference/cimagelist-class.md#getbkcolor)成员函数。  
  
 **ILD_BLEND25**和**ILD_BLEND50**样式抖动具有系统突出显示颜色的图像。 如果您使用一个添加了蒙板的图像来表示一个用户可以选择的对象，那么这些样式会非常有用。 例如，你可以使用**ILD_BLEND50**样式绘制图像，当用户选择它。  
  
 未添加蒙板的图像复制到目标设备上下文使用`SRCCOPY`光栅操作。 不论设备上下文的背景色是什么，图像中的颜色都相同。 在指定的绘图样式`Draw`还具有对未添加蒙板的图像的外观没有影响。  
  
 除 Draw 成员函数，另一个函数， [DrawIndirect](../mfc/reference/cimagelist-class.md#drawindirect)，扩展的能力，以呈现图像。 `DrawIndirect` 采用，作为参数， [IMAGELISTDRAWPARAMS](http://msdn.microsoft.com/library/windows/desktop/bb761395)结构。 此结构可用于自定义当前图像的渲染，包括光栅操作 (ROP) 代码的使用。 ROP 代码的详细信息，请参阅[光栅操作代码](http://msdn.microsoft.com/library/windows/desktop/dd162892)和[位图为画笔](http://msdn.microsoft.com/library/windows/desktop/dd183378)Windows SDK 中。  
  
## <a name="see-also"></a>请参阅  
 [使用 CImageList](../mfc/using-cimagelist.md)   
 [控件](../mfc/controls-mfc.md)

