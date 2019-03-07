---
title: 图像列表类型
ms.date: 11/04/2016
helpviewer_keywords:
- lists [MFC], image
- image lists [MFC], types of
- CImageList class [MFC], types
ms.assetid: bee5e7c3-78f5-4037-a136-9c50d67cdee5
ms.openlocfilehash: 939aad78b7cf8cca9c940bae11892d23dbb659cb
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/04/2019
ms.locfileid: "57304751"
---
# <a name="types-of-image-lists"></a>图像列表类型

有两种类型的图像列表 ([CImageList](../mfc/reference/cimagelist-class.md)): 未添加蒙板和掩码。 包含一个或多个图像的颜色位图的包含"未添加蒙板的图像列表"。 "蒙板的图像列表"包含两个大小相等的位图。 第一个是包含的图像的颜色位图和第二个是包含一系列屏蔽屏蔽的单色位图 — 一个用于第一个位图中的每个图像。

重载之一`Create`成员函数采用一个标志，指示是否屏蔽的图像列表。 （其他重载创建蒙板的图像列表。）

未添加蒙板的图像绘制时，只需复制到目标设备上下文;也就是说，它通过设备上下文的现有背景色绘制。 绘制蒙板的图像，图像的位被结合的位掩码，其中的目标设备上下文的背景色显示通过，则通常生成位图中的透明区域。 绘制蒙板的图像时，可以指定多个的绘制样式。 例如，可以指定抖色图像以指示所选的对象。

## <a name="see-also"></a>请参阅

[使用 CImageList](../mfc/using-cimagelist.md)<br/>
[控件](../mfc/controls-mfc.md)
