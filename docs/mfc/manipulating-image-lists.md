---
title: 操作图像列表 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- image lists [MFC], manipulating
- lists [MFC], image
- CImageList class [MFC], manipulating
ms.assetid: 043418f8-077e-4dce-b8bb-2b7b0d7b5156
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 559cb87dbed412e706cc85b3db1120083b694991
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="manipulating-image-lists"></a>操作图像列表
[替换](../mfc/reference/cimagelist-class.md#replace)成员函数将图像列表中的映像 ([CImageList](../mfc/reference/cimagelist-class.md)) 为新图像。 如果需要动态增加图像列表对象中的图像数，此函数也很有用。 [SetImageCount](../mfc/reference/cimagelist-class.md#setimagecount)函数动态地更改存储的图像列表中的图像数量。 如果增加图像列表的大小，调用**替换**将映像添加到新的映像槽。 如果减小图像列表的大小，则释放超出新大小的图像。  
  
 [删除](../mfc/reference/cimagelist-class.md#remove)成员函数从图像列表中删除映像。 [复制](../mfc/reference/cimagelist-class.md#copy)成员函数可以复制或交换图像列表中的图像。 利用此函数，您可以指示是否应将源图像复制到目标索引，或指示是否应交换源和目标图像。  
  
 若要通过合并两个图像列表创建一个新的映像列表，使用的相应重载[创建](../mfc/reference/cimagelist-class.md#create)成员函数。 此重载**创建**合并现有图像的第一个图像列表，并将生成的图像存储在新的图像列表对象。 通过在第一个图像上透明地绘制第二个图像来创建新图像。 新图像的蒙板是对两个现有图像的蒙板的位执行逻辑“或”运算的结果。  
  
 此运算将重复执行，直到所有图像合并在一起并添加到新图像列表对象。  
  
 你可以将图像信息写入存档通过调用[编写](../mfc/reference/cimagelist-class.md#write)成员函数，并在读取回通过调用[读取](../mfc/reference/cimagelist-class.md#read)成员函数。  
  
 [GetSafeHandle](../mfc/reference/cimagelist-class.md#getsafehandle)，[附加](../mfc/reference/cimagelist-class.md#attach)，和[分离](../mfc/reference/cimagelist-class.md#detach)成员函数支持您将操作附加到的图像列表的句柄`CImageList`对象，而[DeleteImageList](../mfc/reference/cimagelist-class.md#deleteimagelist)成员函数而不销毁下删除图像列表`CImageList`对象。  
  
## <a name="see-also"></a>请参阅  
 [使用 CImageList](../mfc/using-cimagelist.md)   
 [控件](../mfc/controls-mfc.md)

