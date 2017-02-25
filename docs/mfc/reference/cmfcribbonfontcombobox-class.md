---
title: "CMFCRibbonFontComboBox Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CMFCRibbonFontComboBox"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCRibbonFontComboBox class"
ms.assetid: 33b4db50-df4f-45fa-8f05-2e6e73c31435
caps.latest.revision: 24
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 26
---
# CMFCRibbonFontComboBox Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

实现包含字体列表的组合框。  将组合框置于功能区面板上。  
  
## 语法  
  
```  
class CMFCRibbonFontComboBox : public CMFCRibbonComboBox  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|描述|  
|--------|--------|  
|`CMFCRibbonFontComboBox::~CMFCRibbonFontComboBox`|析构函数。|  
  
### 受保护的构造函数  
  
|名称|说明|  
|--------|--------|  
|[CMFCRibbonFontComboBox::CMFCRibbonFontComboBox](../Topic/CMFCRibbonFontComboBox::CMFCRibbonFontComboBox.md)|构造并初始化一个 `CMFCRibbonFontComboBox` 对象。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CMFCRibbonFontComboBox::BuildFonts](../Topic/CMFCRibbonFontComboBox::BuildFonts.md)|使用具有指定字体类型、字符集以及间距和系列的字体填充功能区字体组合框。|  
|`CMFCRibbonFontComboBox::CreateObject`|由框架用于创建此类类型的动态实例。|  
|[CMFCRibbonFontComboBox::GetCharSet](../Topic/CMFCRibbonFontComboBox::GetCharSet.md)|返回指定字符集。|  
|[CMFCRibbonFontComboBox::GetFontDesc](../Topic/CMFCRibbonFontComboBox::GetFontDesc.md)||  
|[CMFCRibbonFontComboBox::GetFontType](../Topic/CMFCRibbonFontComboBox::GetFontType.md)|返回要在组合框中显示的字体类型。  有效选项是是 DEVICE\_FONTTYPE、RASTER\_FONTTYPE 和 TRUETYPE\_FONTTYPE 或是它们的任何按位组合。|  
|[CMFCRibbonFontComboBox::GetPitchAndFamily](../Topic/CMFCRibbonFontComboBox::GetPitchAndFamily.md)|返回组合框中显示的字体的间距和系列。|  
|`CMFCRibbonFontComboBox::GetThisClass`|由框架用于获取指向与此类类型关联的 [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) 对象的指针。|  
|[CMFCRibbonFontComboBox::RebuildFonts](../Topic/CMFCRibbonFontComboBox::RebuildFonts.md)|使用具有以前指定的字体类型、字符集以及间距和系列的字体填充功能区字体组合框。|  
|[CMFCRibbonFontComboBox::SetFont](../Topic/CMFCRibbonFontComboBox::SetFont.md)|选择组合框中的指定字体。|  
  
## 备注  
 创建 `CMFCRibbonFontComboBox` 对象之后，通过调用 [CMFCRibbonPanel::Add](../Topic/CMFCRibbonPanel::Add.md) 将它添加到功能区面板。  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)  
  
 [CMFCRibbonButton](../../mfc/reference/cmfcribbonbutton-class.md)  
  
 [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md)  
  
 [CMFCRibbonComboBox](../../mfc/reference/cmfcribboncombobox-class.md)  
  
 [CMFCRibbonFontComboBox](../../mfc/reference/cmfcribbonfontcombobox-class.md)  
  
## 要求  
 **标头：**afxRibbonComboBox.h  
  
## 请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [类](../../mfc/reference/mfc-classes.md)   
 [CMFCRibbonComboBox Class](../../mfc/reference/cmfcribboncombobox-class.md)