---
title: 在扩展组合框控件中使用图像列表
ms.date: 11/04/2016
helpviewer_keywords:
- image lists [MFC], combo boxes
- extended combo boxes [MFC], images
- images [MFC], combo box items
ms.assetid: dfff25fe-af70-47a2-8032-3901d1e6842d
ms.openlocfilehash: 6e4d983d53e49fc8d9c80c206f1a23078eb82f61
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62411547"
---
# <a name="using-image-lists-in-an-extended-combo-box-control"></a>在扩展组合框控件中使用图像列表

扩展的组合框控件的主要功能是能够将映像从图像列表与组合框控件中的各个项相关联。 每个项是可以显示三个不同的映像： 一个用于其所选的状态，另一个用于其未选定的状态和第三个覆盖图像。

以下过程将图像列表与扩展的组合框控件相关联：

### <a name="to-associate-an-image-list-with-an-extended-combo-box-control"></a>若要将图像列表与扩展的组合框控件相关联

1. 构造一个新的图像列表 （或使用现有的图像列表对象），使用[CImageList](../mfc/reference/cimagelist-class.md)构造函数和存储结果的指针。

1. 初始化新的图像列表对象通过调用[CImageList::Create](../mfc/reference/cimagelist-class.md#create)。 下面的代码是此调用的一个示例。

   [!code-cpp[NVC_MFCControlLadenDialog#10](../mfc/codesnippet/cpp/using-image-lists-in-an-extended-combo-box-control_1.cpp)]

1. 添加每个可能状态的可选图像： 所选或原样，和一个覆盖区。 以下代码添加三个预定义的映像。

   [!code-cpp[NVC_MFCControlLadenDialog#11](../mfc/codesnippet/cpp/using-image-lists-in-an-extended-combo-box-control_2.cpp)]

1. 将图像列表与通过调用控件相关联[CComboBoxEx::SetImageList](../mfc/reference/ccomboboxex-class.md#setimagelist)。

图像列表与控件关联后，可以单独指定每个项将用于三种可能状态的图像。 有关详细信息，请参阅[设置单个项的图像](../mfc/setting-the-images-for-an-individual-item.md)。

## <a name="see-also"></a>请参阅

[使用 CComboBoxEx](../mfc/using-ccomboboxex.md)<br/>
[控件](../mfc/controls-mfc.md)
