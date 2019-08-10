---
title: 从图像列表绘制图像
ms.date: 11/04/2016
helpviewer_keywords:
- CImageList class [MFC], drawing images from
- drawing [MFC], images from image lists
- image lists [MFC], drawing images from
- images [MFC], drawing
ms.assetid: 2f6063fb-1c28-45f8-a333-008c064db11c
ms.openlocfilehash: e4e60f0e6e4ee22712e4bbce344fd6437cf3db7e
ms.sourcegitcommit: 46d24d6e70c03e05484923d9efc6ed5150e96a64
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/09/2019
ms.locfileid: "68916413"
---
# <a name="drawing-images-from-an-image-list"></a>从图像列表绘制图像

若要绘制图像, 请使用[CImageList::D raw](../mfc/reference/cimagelist-class.md#draw)成员函数。 您将指定指向设备上下文对象的指针、要绘制的图像的索引、要在其中绘制图像的设备上下文中的位置以及一组表示绘制样式的标志。

指定**ILD_TRANSPARENT**样式时, `Draw`将使用两个步骤来绘制屏蔽图像。 首先，它对图像的位和蒙板的位执行逻辑“与”操作。 然后对第一次操作的结果和目标设备上下文的背景的位执行逻辑“异或”操作。 此过程会在结果图像中创建透明区域；即蒙板中的每个白色位会使结果图像中相应的位变为透明。

在纯色背景上绘制屏蔽图像之前, 应使用[SetBkColor](../mfc/reference/cimagelist-class.md#setbkcolor)成员函数将图像列表的背景色设置为与目标相同的颜色。 通过`Draw`设置颜色, 无需在图像中创建透明区域, 只需将图像复制到目标设备上下文中, 从而显著提高了性能。 若要绘制图像, 请在调用`Draw`时指定 ILD_NORMAL 样式。

您可以随时为屏蔽图像列表 ([CImageList](../mfc/reference/cimagelist-class.md)) 设置背景色, 使其在任何纯色背景上正确绘制。 如果将背景色设置为**CLR_NONE** , 则默认情况下会以透明方式绘制图像。 若要检索图像列表的背景色, 请使用[GetBkColor](../mfc/reference/cimagelist-class.md#getbkcolor)成员函数。

**ILD_BLEND25**和**ILD_BLEND50**样式将图像与系统突出显示颜色仿色。 如果您使用一个添加了蒙板的图像来表示一个用户可以选择的对象，那么这些样式会非常有用。 例如, 当用户选择图像时, 可以使用**ILD_BLEND50**样式来绘制图像。

使用`SRCCOPY`光栅操作将 draw 映像复制到目标设备上下文。 不论设备上下文的背景色是什么，图像中的颜色都相同。 中`Draw`指定的绘制样式也不会影响 draw 图像的外观。

除了 Draw 成员函数外, 另一个函数[DrawIndirect](../mfc/reference/cimagelist-class.md#drawindirect)还扩展了呈现图像的能力。 `DrawIndirect`采用[IMAGELISTDRAWPARAMS](/windows/desktop/api/commctrl/ns-commctrl-imagelistdrawparams)结构作为参数。 此结构可用于自定义当前图像的渲染，包括光栅操作 (ROP) 代码的使用。 有关 ROP 代码的详细信息, 请参阅[光栅操作代码](/windows/desktop/gdi/raster-operation-codes)和[位图作为](/windows/desktop/gdi/bitmaps-as-brushes)Windows SDK 中的画笔。

## <a name="see-also"></a>请参阅

[使用 CImageList](../mfc/using-cimagelist.md)<br/>
[控件](../mfc/controls-mfc.md)
