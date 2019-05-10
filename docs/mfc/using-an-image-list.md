---
title: 使用图像列表
ms.date: 11/04/2016
helpviewer_keywords:
- lists [MFC], image
- CImageList class [MFC], using
- image lists [MFC]
ms.assetid: e0aed188-a1e6-400e-9f51-033d61c5541f
ms.openlocfilehash: cb95de134939e1b06e2a8b827424c986f8c48ef3
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62180461"
---
# <a name="using-an-image-list"></a>使用图像列表

图像列表的典型用法遵循以下模式：

- 构造[CImageList](../mfc/reference/cimagelist-class.md)对象并调用的重载之一，其[创建](../mfc/reference/cimagelist-class.md#create)函数来创建图像列表，并将其附加到`CImageList`对象。

- 如果没有添加图像创建图像列表时，将添加图像到图像列表通过调用[外](../mfc/reference/cimagelist-class.md#add)或[读取](../mfc/reference/cimagelist-class.md#read)成员函数。

- 通过调用该控件的相应成员函数与控件关联的图像列表或您自己使用的图像列表从图像列表绘制图像[绘制](../mfc/reference/cimagelist-class.md#draw)成员函数。

- 可能是允许用户拖动图像，通过拖动图像列表的内置支持。

> [!NOTE]
>  如果使用的图像列表创建了**新**运算符，您必须销毁`CImageList`对象都完成。

## <a name="see-also"></a>请参阅

[使用 CImageList](../mfc/using-cimagelist.md)<br/>
[控件](../mfc/controls-mfc.md)
