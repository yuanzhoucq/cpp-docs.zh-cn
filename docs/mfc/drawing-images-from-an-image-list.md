---
title: 从图像列表绘制图像
ms.date: 11/04/2016
helpviewer_keywords:
- CImageList class [MFC], drawing images from
- drawing [MFC], images from image lists
- image lists [MFC], drawing images from
- images [MFC], drawing
ms.assetid: 2f6063fb-1c28-45f8-a333-008c064db11c
ms.openlocfilehash: 2ed309ec4a6e58fbc4a900bc541a80004d6be3d0
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50490553"
---
# <a name="drawing-images-from-an-image-list"></a>从图像列表绘制图像

若要绘制图像，请使用[cimagelist:: Draw](../mfc/reference/cimagelist-class.md#draw)成员函数。 您将指定指向设备上下文对象的指针、要绘制的图像的索引、要在其中绘制图像的设备上下文中的位置以及一组表示绘制样式的标志。

当指定**ILD_TRANSPARENT**样式，`Draw`使用一个两步过程来绘制蒙板的图像。 首先，它对图像的位和蒙板的位执行逻辑“与”操作。 然后对第一次操作的结果和目标设备上下文的背景的位执行逻辑“异或”操作。 此过程会在结果图像中创建透明区域；即蒙板中的每个白色位会使结果图像中相应的位变为透明。

在纯色背景上绘制蒙板的图像之前, 应使用[SetBkColor](../mfc/reference/cimagelist-class.md#setbkcolor)成员函数将图像列表的背景色设置为与目标相同的颜色。 设置颜色无需在映像中创建透明区域并使`Draw`只需将映像复制到目标设备上下文，从而大大提高了性能。 若要绘制图像，请指定**ILD_NORMAL**时调用设置样式`Draw`。

可以设置蒙板的图像列表的背景色 ([CImageList](../mfc/reference/cimagelist-class.md)) 在任何时间，因此它在任何纯色背景上正确绘制。 将背景色设置为**CLR_NONE**会将默认情况下以透明方式绘制图像。 若要检索图像列表的背景色，请使用[GetBkColor](../mfc/reference/cimagelist-class.md#getbkcolor)成员函数。

**ILD_BLEND25**并**ILD_BLEND50**样式抖动具有系统突出显示颜色的图像。 如果您使用一个添加了蒙板的图像来表示一个用户可以选择的对象，那么这些样式会非常有用。 例如，可以使用**ILD_BLEND50**样式用于绘制图像，当用户选择它。

未添加蒙板的图像复制到目标设备上下文使用`SRCCOPY`光栅操作。 不论设备上下文的背景色是什么，图像中的颜色都相同。 在指定的绘图样式`Draw`也不会影响未添加蒙板的图像的外观。

除 Draw 成员函数，另一个函数[DrawIndirect](../mfc/reference/cimagelist-class.md#drawindirect)，扩展了呈现的图像的能力。 `DrawIndirect` 将作为参数， [2&AMP;GT;IMAGELISTDRAWPARAMS&AMP;LT;2](/windows/desktop/api/commctrl/ns-commctrl-_imagelistdrawparams)结构。 此结构可用于自定义当前图像的渲染，包括光栅操作 (ROP) 代码的使用。 有关 ROP 代码的详细信息，请参阅[光栅操作代码](/windows/desktop/gdi/raster-operation-codes)并[用作画笔的位图](/windows/desktop/gdi/bitmaps-as-brushes)Windows SDK 中。

## <a name="see-also"></a>请参阅

[使用 CImageList](../mfc/using-cimagelist.md)<br/>
[控件](../mfc/controls-mfc.md)

