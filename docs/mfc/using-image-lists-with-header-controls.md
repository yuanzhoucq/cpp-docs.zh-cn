---
title: 对标题控件使用图像列表
ms.date: 11/04/2016
helpviewer_keywords:
- header controls [MFC], image lists
- CHeaderCtrl class [MFC], image lists
- image lists [MFC], header controls
ms.assetid: d5e9b310-6278-406c-909c-eefa09549a47
ms.openlocfilehash: 8002c16d1cdf5e0683b642001409b6da9c260660
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366470"
---
# <a name="using-image-lists-with-header-controls"></a>对标题控件使用图像列表

标头项能够在标头项中显示图像。 此图像存储在关联的图像列表中，为 16 x 16 像素，其特征与列表视图控件中使用的图标图像相同。 为了成功实现此行为，必须首先创建和初始化图像列表，将列表与标头控件关联，然后修改将显示图像的头项的属性。

以下过程说明了详细信息，使用指向标头控件 （`m_pHdrCtrl`） 的指针和指向图像列表的指针 （`m_pHdrImages`） 。

### <a name="to-display-an-image-in-a-header-item"></a>在标题项中显示图像

1. 使用[CImageList](../mfc/reference/cimagelist-class.md)构造函数构造新的图像列表（或使用现有图像列表对象），存储产生的指针。

1. 通过调用[CImageList：：：创建](../mfc/reference/cimagelist-class.md#create)来初始化新的图像列表对象。 以下代码是此调用的一个示例。

   [!code-cpp[NVC_MFCControlLadenDialog#15](../mfc/codesnippet/cpp/using-image-lists-with-header-controls_1.cpp)]

1. 为每个标题项添加图像。 以下代码添加了两个预定义的映像。

   [!code-cpp[NVC_MFCControlLadenDialog#16](../mfc/codesnippet/cpp/using-image-lists-with-header-controls_2.cpp)]

1. 将映像列表与标头控件与对[CHeaderCtrl 的调用相关联：：SetImageList](../mfc/reference/cheaderctrl-class.md#setimagelist)。

1. 修改标题项以显示关联图像列表中的图像。 下面的示例将第一个图像（从`m_phdrImages`）分配给第一个标头项`m_pHdrCtrl`。

   [!code-cpp[NVC_MFCControlLadenDialog#17](../mfc/codesnippet/cpp/using-image-lists-with-header-controls_3.cpp)]

有关所用参数值的详细信息，请参阅相关的[CHeaderCtrl](../mfc/reference/cheaderctrl-class.md)。

> [!NOTE]
> 可以使用相同的图像列表有多个控件。 例如，在标准列表视图控件中，列表视图控件的小图标视图和列表视图控件的头项都可以使用图像列表（包含 16 x 16 像素图像）。

## <a name="see-also"></a>另请参阅

[使用 CHeaderCtrl](../mfc/using-cheaderctrl.md)
