---
title: 设置单个项的图像
ms.date: 11/04/2016
helpviewer_keywords:
- extended combo boxes [MFC], images
- images [MFC], combo box items
ms.assetid: bde83db8-23a7-4e35-837a-c86447d2c0af
ms.openlocfilehash: 177c06acfe665a43921b19407d9d357d4545e748
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69511273"
---
# <a name="setting-the-images-for-an-individual-item"></a>设置单个项的图像

"扩展" 组合框项使用的不同类型的图像由[COMBOBOXEXITEM](/windows/win32/api/commctrl/ns-commctrl-comboboxexitemw)结构的*iImage*、 *iSelectedImage*和*iOverlay*成员中的值确定。 每个值都是控件的关联图像列表中的图像的索引。 默认情况下, 这些成员设置为 0, 使控件不显示该项的图像。 如果要对特定项使用图像, 则可以在插入组合框项或通过修改现有组合框项时相应地修改该结构。

## <a name="setting-the-image-for-a-new-item"></a>设置新项的图像

如果要插入新项, 请使用正确的值初始化*iImage*、 *iSelectedImage*和*iOverlay*结构成员, 然后使用调用[CComboBoxEx:: InsertItem](../mfc/reference/ccomboboxex-class.md#insertitem)插入该项。

下面的示例在扩展组合框控件 (`cbi``m_comboEx`) 中插入一个新的扩展组合框项 (), 为所有三个图像状态提供索引:

[!code-cpp[NVC_MFCControlLadenDialog#12](../mfc/codesnippet/cpp/setting-the-images-for-an-individual-item_1.cpp)]

## <a name="setting-the-image-for-an-existing-item"></a>设置现有项的图像

如果要修改现有项, 则需要使用**COMBOBOXEXITEM**结构的*mask*成员。

#### <a name="to-modify-an-existing-item-to-use-images"></a>修改现有项目以使用图像

1. 声明**COMBOBOXEXITEM**结构, 然后将*mask*数据成员设置为你想要修改的值。

1. 使用此结构调用[CComboBoxEx:: GetItem](../mfc/reference/ccomboboxex-class.md#getitem)。

1. 使用适当的值修改新返回的结构的*mask*、 *iImage*和*iSelectedImage*成员。

1. 调用[CComboBoxEx:: SetItem](../mfc/reference/ccomboboxex-class.md#setitem), 并传入已修改的结构。

下面的示例通过交换第三个扩展组合框项的选定和未选中的图像来演示此过程:

[!code-cpp[NVC_MFCControlLadenDialog#13](../mfc/codesnippet/cpp/setting-the-images-for-an-individual-item_2.cpp)]

## <a name="see-also"></a>请参阅

[使用 CComboBoxEx](../mfc/using-ccomboboxex.md)<br/>
[控件](../mfc/controls-mfc.md)
