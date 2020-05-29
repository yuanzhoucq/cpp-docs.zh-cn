---
title: 使用图像列表
ms.date: 11/04/2016
helpviewer_keywords:
- lists [MFC], image
- CImageList class [MFC], using
- image lists [MFC]
ms.assetid: e0aed188-a1e6-400e-9f51-033d61c5541f
ms.openlocfilehash: 0d9566739a15e5d216eb052a7265313850515648
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366576"
---
# <a name="using-an-image-list"></a>使用图像列表

图像列表的典型用法遵循以下模式：

- 构造[CImageList](../mfc/reference/cimagelist-class.md)对象并调用其[Create](../mfc/reference/cimagelist-class.md#create)函数的重载之一以创建图像列表并将其附加到`CImageList`对象。

- 如果在创建图像列表时未添加图像，请通过调用["添加](../mfc/reference/cimagelist-class.md#add)"或["读取](../mfc/reference/cimagelist-class.md#read)成员"功能将图像添加到图像列表中。

- 通过调用该控件的相应成员函数将图像列表与控件关联，或使用图像列表的["绘制](../mfc/reference/cimagelist-class.md#draw)"成员函数自行从图像列表中绘制图像。

- 可能允许用户使用图像列表的内置支持拖动来拖动图像。

> [!NOTE]
> 如果图像列表是**使用新**运算符创建的，则必须在使用该`CImageList`对象时销毁该对象。

## <a name="see-also"></a>另请参阅

[使用 CImageList](../mfc/using-cimagelist.md)<br/>
[控件](../mfc/controls-mfc.md)
