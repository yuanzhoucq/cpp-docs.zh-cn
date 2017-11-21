---
title: "图像列表中的信息的映像 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- CImageList class [MFC], image information in
- image lists [MFC], image information in
ms.assetid: 73c41543-fa91-405d-b15b-0feffa6a72c1
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 80e897ec79314abb2e77864e53d470e72f275a94
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="image-information-in-image-lists"></a>图像列表中的图像信息
[CImageList](../mfc/reference/cimagelist-class.md)包括一些从图像列表中检索信息的函数。 [GetImageInfo](../mfc/reference/cimagelist-class.md#getimageinfo)成员函数填充`IMAGEINFO`使用有关单个图像，包括图像和位图、 颜色平面和每像素位数的数量和的边框句柄的信息的结构图像位图中的映像。 您可使用此信息直接操作图像的位图。  
  
 [GetImageCount](../mfc/reference/cimagelist-class.md#getimagecount)成员函数将检索图像列表中的图像数量。  
  
 你可以创建基于使用的图像和掩码图像列表中的图标[ExtractIcon](../mfc/reference/cimagelist-class.md#extracticon)成员函数。 此函数将返回新图标的句柄。  
  
## <a name="see-also"></a>另请参阅  
 [使用 CImageList](../mfc/using-cimagelist.md)   
 [控件](../mfc/controls-mfc.md)

