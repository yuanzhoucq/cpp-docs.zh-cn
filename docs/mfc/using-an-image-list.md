---
title: "使用图像列表 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- lists [MFC], image
- CImageList class [MFC], using
- image lists [MFC]
ms.assetid: e0aed188-a1e6-400e-9f51-033d61c5541f
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 4321649bf4e8fe0e34fef8fe37b8c96598bef2c2
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="using-an-image-list"></a>使用图像列表
图像列表的典型用法遵循以下模式：  
  
-   构造[CImageList](../mfc/reference/cimagelist-class.md)对象并调用的重载之一其[创建](../mfc/reference/cimagelist-class.md#create)函数创建图像列表，并将其附加到`CImageList`对象。  
  
-   如果您没有添加图像创建图像列表时，添加图像的图像列表通过调用[添加](../mfc/reference/cimagelist-class.md#add)或[读取](../mfc/reference/cimagelist-class.md#read)成员函数。  
  
-   与控件关联的图像列表，通过调用适当的成员函数的功能，或使用图像列表自行从图像列表绘制图像[绘制](../mfc/reference/cimagelist-class.md#draw)成员函数。  
  
-   可能允许用户拖动图像，拖动使用图像列表的内置支持。  
  
> [!NOTE]
>  如果使用的图像列表创建了**新**运算符，必须销毁`CImageList`对象都完成。  
  
## <a name="see-also"></a>请参阅  
 [使用 CImageList](../mfc/using-cimagelist.md)   
 [控件](../mfc/controls-mfc.md)

