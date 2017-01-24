---
title: "设置单个项的图像 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "扩展组合框, 图像"
  - "图像 [C++], 组合框项"
ms.assetid: bde83db8-23a7-4e35-837a-c86447d2c0af
caps.latest.revision: 11
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 设置单个项的图像
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

扩展组合框项的图像类型的不同的依赖于 `iImage`、**iSelectedImage**和 [COMBOBOXEXITEM](http://msdn.microsoft.com/library/windows/desktop/bb775746) 结构的 **iOverlay** 成员中的值。  每个值都是图像的索引。控件关联的图像列表中。  默认情况下，这些成员未设置为 0，将使控件显示项的图像。  如果您想要为特定项使用图像，可以相应地修改结构，或者，当在一组合框项或通过更改现有的组合框项。  
  
## 设置新项的图像  
 如果插入新项，请初始化 `iImage`、**iSelectedImage**和 **iOverlay** 成员与结构相应的值然后插入该项。对 [CComboBoxEx::InsertItem](../Topic/CComboBoxEx::InsertItem.md)。  
  
 下面的示例插入新的扩展组合框项 \(`cbi`\) 中扩展组合框控件 \(`m_comboEx`\)，为所有三状态图像的索引：  
  
 [!code-cpp[NVC_MFCControlLadenDialog#12](../mfc/codesnippet/CPP/setting-the-images-for-an-individual-item_1.cpp)]  
  
## 将现有项的图像  
 如果要修改现有项，则需要使用 **COMBOBOXEXITEM** 结构的 **mask** 成员中。  
  
#### 修改现有项使用图像  
  
1.  **COMBOBOXEXITEM** 结构声明并将 **mask** 数据成员添加到您对感兴趣修改的值。  
  
2.  使用此结构，请调用 [CComboBoxEx::GetItem](../Topic/CComboBoxEx::GetItem.md)。  
  
3.  使用相应的值，修改 **mask**、`iImage`和最近返回结构的 **iSelectedImage** 成员中，  
  
4.  调用 [CComboBoxEx::SetItem](../Topic/CComboBoxEx::SetItem.md)，将修改结构。  
  
 下面的示例通过交换第三个扩展组合框项的选择和取消选中的图像演示此过程：  
  
 [!code-cpp[NVC_MFCControlLadenDialog#13](../mfc/codesnippet/CPP/setting-the-images-for-an-individual-item_2.cpp)]  
  
## 请参阅  
 [使用 CComboBoxEx](../mfc/using-ccomboboxex.md)   
 [控件](../mfc/controls-mfc.md)