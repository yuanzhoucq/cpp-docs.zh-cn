---
title: 映像图像列表中的信息 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- CImageList class [MFC], image information in
- image lists [MFC], image information in
ms.assetid: 73c41543-fa91-405d-b15b-0feffa6a72c1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c98bc629cde74cf7a6fc8a416de862f50a1dd5ae
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46422262"
---
# <a name="image-information-in-image-lists"></a>图像列表中的图像信息

[CImageList](../mfc/reference/cimagelist-class.md)包括一些函数，用于从图像列表中检索信息。 [GetImageInfo](../mfc/reference/cimagelist-class.md#getimageinfo)成员函数填充`IMAGEINFO`结构有关的单一映像，包括图像和位图、 颜色平面和每像素位的数量和边界的矩形的句柄的信息图像位图中的图像。 您可使用此信息直接操作图像的位图。

[GetImageCount](../mfc/reference/cimagelist-class.md#getimagecount)成员函数将检索图像列表中的映像数量。

可以创建基于使用的图像和掩码图像列表中的图标[ExtractIcon](../mfc/reference/cimagelist-class.md#extracticon)成员函数。 此函数将返回新图标的句柄。

## <a name="see-also"></a>请参阅

[使用 CImageList](../mfc/using-cimagelist.md)<br/>
[控件](../mfc/controls-mfc.md)

