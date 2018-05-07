---
title: 图像列表中的信息的映像 |Microsoft 文档
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
ms.openlocfilehash: 6b45a685a9de44bdc40f83481cb83ef58a5c4234
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="image-information-in-image-lists"></a>图像列表中的图像信息
[CImageList](../mfc/reference/cimagelist-class.md)包括一些从图像列表中检索信息的函数。 [GetImageInfo](../mfc/reference/cimagelist-class.md#getimageinfo)成员函数填充`IMAGEINFO`使用有关单个图像，包括图像和位图、 颜色平面和每像素位数的数量和的边框句柄的信息的结构图像位图中的映像。 您可使用此信息直接操作图像的位图。  
  
 [GetImageCount](../mfc/reference/cimagelist-class.md#getimagecount)成员函数将检索图像列表中的图像数量。  
  
 你可以创建基于使用的图像和掩码图像列表中的图标[ExtractIcon](../mfc/reference/cimagelist-class.md#extracticon)成员函数。 此函数将返回新图标的句柄。  
  
## <a name="see-also"></a>请参阅  
 [使用 CImageList](../mfc/using-cimagelist.md)   
 [控件](../mfc/controls-mfc.md)

