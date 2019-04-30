---
title: 对标题控件使用图像列表
ms.date: 11/04/2016
helpviewer_keywords:
- header controls [MFC], image lists
- CHeaderCtrl class [MFC], image lists
- image lists [MFC], header controls
ms.assetid: d5e9b310-6278-406c-909c-eefa09549a47
ms.openlocfilehash: 3d9a4a0c655fa46c15d8c4d9b2b4e90cd34c2937
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62411534"
---
# <a name="using-image-lists-with-header-controls"></a>对标题控件使用图像列表

标头项具有显示标头项内的图像的能力。 存储在关联的图像列表中，此图像是 16 x 16 像素，并且具有相同的特性列表视图控件中使用的图标图像。 为了成功实现此行为，必须首先创建和初始化的图像列表中，将列表与标头控件相关联，然后修改都会显示图像的标头项的属性。

以下过程说明了使用指向标头控件的详细信息 (`m_pHdrCtrl`) 和图像列表的指针 (`m_pHdrImages`)。

### <a name="to-display-an-image-in-a-header-item"></a>若要显示的图像中的标头项

1. 构造一个新的图像列表 （或使用现有的图像列表对象） 使用[CImageList](../mfc/reference/cimagelist-class.md)构造函数中，存储结果的指针。

1. 初始化新的图像列表对象通过调用[CImageList::Create](../mfc/reference/cimagelist-class.md#create)。 下面的代码是此调用的一个示例。

   [!code-cpp[NVC_MFCControlLadenDialog#15](../mfc/codesnippet/cpp/using-image-lists-with-header-controls_1.cpp)]

1. 添加为每个标头项的映像。 以下代码添加两个预定义的映像。

   [!code-cpp[NVC_MFCControlLadenDialog#16](../mfc/codesnippet/cpp/using-image-lists-with-header-controls_2.cpp)]

1. 将图像列表与标头控件通过调用相关联[CHeaderCtrl::SetImageList](../mfc/reference/cheaderctrl-class.md#setimagelist)。

1. 修改要显示来自关联的图像列表的图像的标头项。 以下示例将从分配的第一个图像`m_phdrImages`，与第一个标头项， `m_pHdrCtrl`。

   [!code-cpp[NVC_MFCControlLadenDialog#17](../mfc/codesnippet/cpp/using-image-lists-with-header-controls_3.cpp)]

有关使用的参数值的详细信息，请查阅相关[CHeaderCtrl](../mfc/reference/cheaderctrl-class.md)。

> [!NOTE]
>  很可能有多个控件使用相同的图像列表。 例如，在标准列表视图控件中，可能有的图像列表 （16 x 16 像素的图像） 由列表视图控件的小图标视图和列表视图控件的标头项。

## <a name="see-also"></a>请参阅

[使用 CHeaderCtrl](../mfc/using-cheaderctrl.md)
