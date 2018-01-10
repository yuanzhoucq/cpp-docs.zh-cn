---
title: "设置单个项的图像 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- extended combo boxes [MFC], images
- images [MFC], combo box items
ms.assetid: bde83db8-23a7-4e35-837a-c86447d2c0af
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 4d9cb74c2290292f44b8c6c9b8797890e759f315
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="setting-the-images-for-an-individual-item"></a>设置单个项的图像
不同类型的扩展的组合框项所使用的图像中的值确定`iImage`， **iSelectedImage**，和**iOverlay**的成员[COMBOBOXEXITEM](http://msdn.microsoft.com/library/windows/desktop/bb775746)结构。 每个值是图像的该控件关联的图像列表中的索引。 默认情况下，这些成员设置为 0，导致要显示的项没有图像的控件。 如果你想要为特定的项使用映像，你可以插入组合框项时或通过修改现有的组合框项相应地，修改结构。  
  
## <a name="setting-the-image-for-a-new-item"></a>为新项设置的图像  
 如果你在插入新项，初始化`iImage`， **iSelectedImage**，和**iOverlay**结构使用合适的值的成员，然后插入的项通过调用[CComboBoxEx::InsertItem](../mfc/reference/ccomboboxex-class.md#insertitem)。  
  
 下面的示例将新的扩展的组合框项 (`cbi`) 到扩展的组合框控件 (`m_comboEx`)，提供有关状态的所有三个图像的索引：  
  
 [!code-cpp[NVC_MFCControlLadenDialog#12](../mfc/codesnippet/cpp/setting-the-images-for-an-individual-item_1.cpp)]  
  
## <a name="setting-the-image-for-an-existing-item"></a>设置现有项的图像  
 如果您正在修改现有项，你需要处理**掩码**的成员**COMBOBOXEXITEM**结构。  
  
#### <a name="to-modify-an-existing-item-to-use-images"></a>若要修改现有项将映像  
  
1.  声明**COMBOBOXEXITEM**结构并设置**掩码**你有兴趣修改为值的数据成员。  
  
2.  使用此结构，请调用[CComboBoxEx::GetItem](../mfc/reference/ccomboboxex-class.md#getitem)。  
  
3.  修改**掩码**， `iImage`，和**iSelectedImage**新返回的结构中，使用适当的值的成员。  
  
4.  调用[CComboBoxEx::SetItem](../mfc/reference/ccomboboxex-class.md#setitem)，并传入修改的结构。  
  
 下面的示例演示了此过程，通过交换的第三个扩展的组合框项的选定和未选定映像：  
  
 [!code-cpp[NVC_MFCControlLadenDialog#13](../mfc/codesnippet/cpp/setting-the-images-for-an-individual-item_2.cpp)]  
  
## <a name="see-also"></a>请参阅  
 [使用 CComboBoxEx](../mfc/using-ccomboboxex.md)   
 [控件](../mfc/controls-mfc.md)

