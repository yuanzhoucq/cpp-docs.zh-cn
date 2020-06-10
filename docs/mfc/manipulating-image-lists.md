---
title: 操作图像列表
ms.date: 11/04/2016
helpviewer_keywords:
- image lists [MFC], manipulating
- lists [MFC], image
- CImageList class [MFC], manipulating
ms.assetid: 043418f8-077e-4dce-b8bb-2b7b0d7b5156
ms.openlocfilehash: cb7376241febd6bd1545cd183147e14a15313820
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84622463"
---
# <a name="manipulating-image-lists"></a>操作图像列表

[Replace](reference/cimagelist-class.md#replace)成员函数使用新图像替换图像列表（[CImageList](reference/cimagelist-class.md)）中的图像。 如果需要动态增加图像列表对象中的图像数，此函数也很有用。 [SetImageCount](reference/cimagelist-class.md#setimagecount)函数动态更改存储在图像列表中的图像数量。 如果增加图像列表的大小，请调用 `Replace` 将映像添加到新的图像槽。 如果减小图像列表的大小，则释放超出新大小的图像。

[Remove](reference/cimagelist-class.md#remove)成员函数从图像列表中移除图像。 [Copy](reference/cimagelist-class.md#copy)成员函数可以复制或交换图像列表中的图像。 利用此函数，您可以指示是否应将源图像复制到目标索引，或指示是否应交换源和目标图像。

若要通过合并两个图像列表来创建新的图像列表，请使用[create](reference/cimagelist-class.md#create)成员函数的适当重载。 此重载 `Create` 合并现有图像列表的第一个图像，并将生成的图像存储在新的图像列表对象中。 通过在第一个图像上透明地绘制第二个图像来创建新图像。 新图像的蒙板是对两个现有图像的蒙板的位执行逻辑“或”运算的结果。

此运算将重复执行，直到所有图像合并在一起并添加到新图像列表对象。

可以通过调用[write](reference/cimagelist-class.md#write)成员函数将图像信息写入存档，并通过调用[read](reference/cimagelist-class.md#read)成员函数将其读回存档。

" [GetSafeHandle](reference/cimagelist-class.md#getsafehandle)"、"[附加](reference/cimagelist-class.md#attach)" 和 "[分离](reference/cimagelist-class.md#detach)" 成员函数使你可以操作附加到对象的图像列表的句柄 `CImageList` ，而[DeleteImageList](reference/cimagelist-class.md#deleteimagelist)成员函数将删除图像列表，而不会销毁 `CImageList` 对象。

## <a name="see-also"></a>另请参阅

[使用 CImageList](using-cimagelist.md)<br/>
[控件](controls-mfc.md)
