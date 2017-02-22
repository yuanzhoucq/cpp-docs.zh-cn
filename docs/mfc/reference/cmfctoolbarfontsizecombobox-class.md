---
title: "CMFCToolBarFontSizeComboBox Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CMFCToolBarFontSizeComboBox"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCToolBarFontSizeComboBox class"
ms.assetid: 72e0c44c-6a0e-4194-a71f-ab64e3afb9b5
caps.latest.revision: 26
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 28
---
# CMFCToolBarFontSizeComboBox Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

一个包含组合框控件使用户选择字体大小的工具栏按钮。  
  
## 语法  
  
```  
class CMFCToolBarFontSizeComboBox : public CMFCToolBarComboBoxButton  
```  
  
## 成员  
  
### 受保护的构造函数  
  
|名称|说明|  
|--------|--------|  
|[CMFCToolBarFontSizeComboBox::CMFCToolBarFontSizeComboBox](../Topic/CMFCToolBarFontSizeComboBox::CMFCToolBarFontSizeComboBox.md)|构造 `CMFCToolBarFontSizeComboBox` 对象。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CMFCToolBarFontSizeComboBox::GetTwipSize](../Topic/CMFCToolBarFontSizeComboBox::GetTwipSize.md)|返回在twips的选定的字体大小。|  
|[CMFCToolBarFontSizeComboBox::RebuildFontSizes](../Topic/CMFCToolBarFontSizeComboBox::RebuildFontSizes.md)|填充组合框列表与指定的字体的所有支持的字体大小。|  
|[CMFCToolBarFontSizeComboBox::SetTwipSize](../Topic/CMFCToolBarFontSizeComboBox::SetTwipSize.md)|将twips的字体大小。|  
  
## 备注  
 可以使用 [CMFCToolBarFontComboBox Class](../../mfc/reference/cmfctoolbarfontcombobox-class.md) 对象一起使用 `CMFCToolBarFontSizeComboBox` 对象允许用户选择字体、字体大小。  
  
 就象添加一个字体组合框按钮，可以向字号组合框按钮添加到工具栏。  有关更多信息，请参见 [CMFCToolBarFontComboBox Class](../../mfc/reference/cmfctoolbarfontcombobox-class.md)。  
  
 当用户选择 `CMFCToolBarFontComboBox` 对象时新的字体，使用 [CMFCToolBarFontSizeComboBox::RebuildFontSizes](../Topic/CMFCToolBarFontSizeComboBox::RebuildFontSizes.md) 方案中，可以在该字体支持的大小加载字号组合框。  
  
## 示例  
 下面的示例在 `CMFCToolBarFontSizeComboBox` 选件类演示如何使用各种方案配置 `CMFCToolBarFontSizeComboBox` 对象。  示例在twips演示如何从文本框检索字号，在twips，加载具有特定字体的任何有效范围的字号组合框，并指定字号。  此代码段是 [Word填充示例](../../top/visual-cpp-samples.md)的一部分。  
  
 [!code-cpp[NVC_MFC_WordPad#8](../../mfc/reference/codesnippet/CPP/cmfctoolbarfontsizecombobox-class_1.cpp)]  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md)  
  
 [CMFCToolBarComboBoxButton](../../mfc/reference/cmfctoolbarcomboboxbutton-class.md)  
  
 [CMFCToolBarFontSizeComboBox](../../mfc/reference/cmfctoolbarfontsizecombobox-class.md)  
  
## 要求  
 **标头:** afxtoolbarfontcombobox.h  
  
## 请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [类](../../mfc/reference/mfc-classes.md)   
 [CMFCToolBar Class](../../mfc/reference/cmfctoolbar-class.md)   
 [CMFCToolBarButton Class](../../mfc/reference/cmfctoolbarbutton-class.md)   
 [CMFCToolBarComboBoxButton Class](../../mfc/reference/cmfctoolbarcomboboxbutton-class.md)   
 [CMFCFontInfo Class](../../mfc/reference/cmfcfontinfo-class.md)   
 [CMFCToolBar::ReplaceButton](../Topic/CMFCToolBar::ReplaceButton.md)   
 [演练：将控件置于工具栏上](../../mfc/walkthrough-putting-controls-on-toolbars.md)