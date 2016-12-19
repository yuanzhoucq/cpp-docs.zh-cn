---
title: "在扩展组合框控件中使用图像列表 | Microsoft Docs"
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
  - "图像列表 [C++], 组合框"
  - "图像 [C++], 组合框项"
ms.assetid: dfff25fe-af70-47a2-8032-3901d1e6842d
caps.latest.revision: 11
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 在扩展组合框控件中使用图像列表
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

扩展组合框控件的主要功能是关联从图像列表的图像与组合框控件中的单个项。  每项可显示三个图像：一个其选定状态的，一个 nonselected 状态和覆盖图像的第三列。  
  
 以下过程将图像列表与扩展组合框控件：  
  
### 若要将图像列表中使用扩展组合框控件  
  
1.  构造新的图像列表 \(或者使用现有的图像列表对象\)。[CImageList](../mfc/reference/cimagelist-class.md) 构造函数和存储提供的指针。  
  
2.  通过调用 [CImageList::Create](../Topic/CImageList::Create.md)初始化新图像列表对象。  以下代码是此调用的一个示例。  
  
     [!code-cpp[NVC_MFCControlLadenDialog#10](../mfc/codesnippet/CPP/using-image-lists-in-an-extended-combo-box-control_1.cpp)]  
  
3.  添加每种可能状态的图像的选项：选择或 nonselected 和覆盖。  以下代码添加三预定义的图像。  
  
     [!code-cpp[NVC_MFCControlLadenDialog#11](../mfc/codesnippet/CPP/using-image-lists-in-an-extended-combo-box-control_2.cpp)]  
  
4.  将图像列表与个名为的控件。[CComboBoxEx::SetImageList](../Topic/CComboBoxEx::SetImageList.md)。  
  
 在图像列表与控件关联，您可以分别为每项指定三个可能状态要使用的图像。  有关更多信息，请参见 [设置个别项的图像](../mfc/setting-the-images-for-an-individual-item.md)。  
  
## 请参阅  
 [使用 CComboBoxEx](../mfc/using-ccomboboxex.md)   
 [控件](../mfc/controls-mfc.md)