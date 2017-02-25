---
title: "CMFCToolBarFontComboBox Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CMFCToolBarFontComboBox"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCToolBarFontComboBox class"
ms.assetid: 25f8e08c-aadd-4cb5-9581-a99d49d444b1
caps.latest.revision: 29
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 31
---
# CMFCToolBarFontComboBox Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

一个包含组合框控件使用户选择字体从系统字体列表的工具栏按钮。  
  
## 语法  
  
```  
class CMFCToolBarFontComboBox : public CMFCToolBarComboBoxButton  
```  
  
## 成员  
  
### 受保护的构造函数  
  
|名称|说明|  
|--------|--------|  
|[CMFCToolBarFontComboBox::CMFCToolBarFontComboBox](../Topic/CMFCToolBarFontComboBox::CMFCToolBarFontComboBox.md)|构造 `CMFCToolBarFontComboBox` 对象。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CMFCToolBarFontComboBox::GetFontDesc](../Topic/CMFCToolBarFontComboBox::GetFontDesc.md)|返回指针传递给指定索引处。`CMFCFontInfo` 对象在组合框。|  
|[CMFCToolBarFontComboBox::SetFont](../Topic/CMFCToolBarFontComboBox::SetFont.md)|根据字体的名称选择字体组合框内的字体或字体的标题和字符集。|  
  
### 数据成员  
 [CMFCToolBarFontComboBox::m\_nFontHeight](../Topic/CMFCToolBarFontComboBox::m_nFontHeight.md)  
 字符的高度\(以字体组合框中。  
  
## 备注  
 若要将字体组合框按钮添加到工具栏，请执行以下步骤:  
  
1.  保留虚拟资源ID在父工具栏资源的按钮。  
  
2.  构造 `CMFCToolBarFontComboBox` 对象。  
  
3.  使用 [CMFCToolBar::ReplaceButton](../Topic/CMFCToolBar::ReplaceButton.md)，在处理 `AFX_WM_RESETTOOLBAR` 消息的消息处理程序，请在新的组合框按钮替换原始按钮。  
  
4.  同步通过使用 [CMFCToolBarFontComboBox::SetFont](../Topic/CMFCToolBarFontComboBox::SetFont.md) 方法，在具有字体的组合框中选择文档的字体。  
  
 与组合框中选择的字体若要同步文档的字体，请使用 [CMFCToolBarFontComboBox::GetFontDesc](../Topic/CMFCToolBarFontComboBox::GetFontDesc.md) 方法检索选定的字体属性，然后使用这些属性创建 [CFont Class](../../mfc/reference/cfont-class.md) 对象。  
  
 字体组合框按钮调用Win32函数 [EnumFontFamiliesEx](http://msdn.microsoft.com/library/windows/desktop/dd162620) 确定屏幕和打印机字体提供对系统。  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md)  
  
 [CMFCToolBarComboBoxButton](../../mfc/reference/cmfctoolbarcomboboxbutton-class.md)  
  
 [CMFCToolBarFontComboBox](../../mfc/reference/cmfctoolbarfontcombobox-class.md)  
  
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