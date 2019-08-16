---
title: 图像列表中的图像覆盖
ms.date: 11/04/2016
helpviewer_keywords:
- overlays [MFC]
- image lists [MFC], image overlays in
- CImageList class [MFC], image overlays in
ms.assetid: aaf4e1c4-cd12-42c8-9af4-1bb458889b4e
ms.openlocfilehash: ec795193a28a68d8aee61e9932481a89c4b3e8e0
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69508386"
---
# <a name="image-overlays-in-image-lists"></a>图像列表中的图像覆盖

每个图像列表 ([CImageList](../mfc/reference/cimagelist-class.md)) 都包含一个要用作覆盖蒙板的图像的列表。 “覆盖掩码”是在其他图像上透明绘制的图像。 任何图像都可用作覆盖掩码。 每个图像列表您最多可以指定 4 个覆盖掩码。

使用[SetOverlayImage](../mfc/reference/cimagelist-class.md#setoverlayimage)成员函数、图像的索引和覆盖掩码的索引, 将图像的索引添加到覆盖掩码列表。 请注意，覆盖掩码的索引是从 1 而不是 0 开始的。

使用对`Draw`的单个调用, 可以在图像上绘制覆盖屏蔽。 参数包括要绘制图像的索引和覆盖掩码的索引。 必须使用[INDEXTOOVERLAYMASK](/windows/win32/api/commctrl/nf-commctrl-indextooverlaymask)宏来指定覆盖掩码的索引。 在调用[DrawIndirect](../mfc/reference/cimagelist-class.md#drawindirect)成员函数时, 还可以指定覆盖图像。

## <a name="see-also"></a>请参阅

[使用 CImageList](../mfc/using-cimagelist.md)<br/>
[控件](../mfc/controls-mfc.md)
