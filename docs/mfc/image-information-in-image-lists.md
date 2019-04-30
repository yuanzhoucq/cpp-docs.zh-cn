---
title: 图像列表中的图像信息
ms.date: 11/04/2016
helpviewer_keywords:
- CImageList class [MFC], image information in
- image lists [MFC], image information in
ms.assetid: 73c41543-fa91-405d-b15b-0feffa6a72c1
ms.openlocfilehash: 7b83b7e5f7de6f8ccca95d732f71a5d73a97e943
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62363513"
---
# <a name="image-information-in-image-lists"></a>图像列表中的图像信息

[CImageList](../mfc/reference/cimagelist-class.md)包括一些函数，用于从图像列表中检索信息。 [GetImageInfo](../mfc/reference/cimagelist-class.md#getimageinfo)成员函数填充`IMAGEINFO`结构有关的单一映像，包括图像和位图、 颜色平面和每像素位的数量和边界的矩形的句柄的信息图像位图中的图像。 您可使用此信息直接操作图像的位图。

[GetImageCount](../mfc/reference/cimagelist-class.md#getimagecount)成员函数将检索图像列表中的映像数量。

可以创建基于使用的图像和掩码图像列表中的图标[ExtractIcon](../mfc/reference/cimagelist-class.md#extracticon)成员函数。 此函数将返回新图标的句柄。

## <a name="see-also"></a>请参阅

[使用 CImageList](../mfc/using-cimagelist.md)<br/>
[控件](../mfc/controls-mfc.md)
