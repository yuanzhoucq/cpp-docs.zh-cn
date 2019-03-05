---
title: 设置单个项的图像
ms.date: 11/04/2016
helpviewer_keywords:
- extended combo boxes [MFC], images
- images [MFC], combo box items
ms.assetid: bde83db8-23a7-4e35-837a-c86447d2c0af
ms.openlocfilehash: 39aa4761dbc753c42f1aedbb18f1832eab471e50
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/04/2019
ms.locfileid: "57294702"
---
# <a name="setting-the-images-for-an-individual-item"></a>设置单个项的图像

不同类型的扩展的组合框项所使用的映像由中的值*iImage*， *iSelectedImage*，并*iOverlay* 的成员[COMBOBOXEXITEM](/windows/desktop/api/commctrl/ns-commctrl-tagcomboboxexitema)结构。 每个值是图像的在该控件关联的图像列表中的索引。 默认情况下，这些成员设置为 0，从而导致要显示的项没有图像的控件。 如果你想要用于特定项的图像，您可以插入组合框项时或通过修改现有的组合框项相应地，修改结构。

## <a name="setting-the-image-for-a-new-item"></a>设置新项的图像

如果要插入新项，初始化*iImage*， *iSelectedImage*，并*iOverlay*结构具有适当的值的成员，然后将通过调用项[CComboBoxEx::InsertItem](../mfc/reference/ccomboboxex-class.md#insertitem)。

下面的示例插入一个新的扩展的组合框项 (`cbi`) 到扩展的组合框控件 (`m_comboEx`)，提供有关状态的所有三个图像的索引：

[!code-cpp[NVC_MFCControlLadenDialog#12](../mfc/codesnippet/cpp/setting-the-images-for-an-individual-item_1.cpp)]

## <a name="setting-the-image-for-an-existing-item"></a>设置现有项的图像

如果要修改现有的项，则需要使用*掩码*的成员**COMBOBOXEXITEM**结构。

#### <a name="to-modify-an-existing-item-to-use-images"></a>若要修改现有项目以使用映像

1. 声明**COMBOBOXEXITEM**结构，并设置*掩码*感兴趣修改的数据成员的值。

1. 使用此结构，请调用[CComboBoxEx::GetItem](../mfc/reference/ccomboboxex-class.md#getitem)。

1. 修改*掩码*， *iImage*，并*iSelectedImage*成员的新返回的结构，使用适当的值。

1. 调用[CComboBoxEx::SetItem](../mfc/reference/ccomboboxex-class.md#setitem)、 传入已修改的结构。

下面的示例演示了此过程通过交换的第三个扩展的组合框项的选定和未选定的映像：

[!code-cpp[NVC_MFCControlLadenDialog#13](../mfc/codesnippet/cpp/setting-the-images-for-an-individual-item_2.cpp)]

## <a name="see-also"></a>请参阅

[使用 CComboBoxEx](../mfc/using-ccomboboxex.md)<br/>
[控件](../mfc/controls-mfc.md)
