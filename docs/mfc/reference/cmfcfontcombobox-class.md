---
title: "CMFCFontComboBox Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CMFCFontComboBox"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCFontComboBox class"
  - "CMFCFontComboBox::CompareItem method"
  - "CMFCFontComboBox::DrawItem method"
  - "CMFCFontComboBox::MeasureItem method"
  - "CMFCFontComboBox::PreTranslateMessage method"
ms.assetid: 9a53fb0c-7b45-486d-8187-2a4c723d9fbb
caps.latest.revision: 29
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 31
---
# CMFCFontComboBox Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

`CMFCFontComboBox` 选件类创建包含字体列表中某个组合框控件。  
  
## 语法  
  
```  
class CMFCFontComboBox : public CComboBox  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CMFCFontComboBox::CMFCFontComboBox](../Topic/CMFCFontComboBox::CMFCFontComboBox.md)|构造 `CMFCFontComboBox` 对象。|  
|`CMFCFontComboBox::~CMFCFontComboBox`|析构函数。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|`CMFCFontComboBox::CompareItem`|调用由框架确定新项目的相对位置在已排序的当前字体组合框控件的列表框。  （重写 [CComboBox::CompareItem](../Topic/CComboBox::CompareItem.md)。）|  
|`CMFCFontComboBox::DrawItem`|调用由框架绘制在当前字体组合框控件的指定项目。  （重写 [CComboBox::DrawItem](../Topic/CComboBox::DrawItem.md)。）|  
|[CMFCFontComboBox::GetSelFont](../Topic/CMFCFontComboBox::GetSelFont.md)|检索有关当前选定的字体的信息。|  
|`CMFCFontComboBox::MeasureItem`|调用由框架通知Windows列表框的尺寸在当前字体组合框控件的。  （重写 [CComboBox::MeasureItem](../Topic/CComboBox::MeasureItem.md)。）|  
|`CMFCFontComboBox::PreTranslateMessage`|在将调度到 [TranslateMessage](http://msdn.microsoft.com/library/windows/desktop/ms644955) 和 [DispatchMessage](http://msdn.microsoft.com/library/windows/desktop/ms644934) Windows功能之前，将windows消息。  （重写 [CWnd::PreTranslateMessage](../Topic/CWnd::PreTranslateMessage.md)。）|  
|[CMFCFontComboBox::SelectFont](../Topic/CMFCFontComboBox::SelectFont.md)|选择与从字体组合框中指定条件的字体。|  
|[CMFCFontComboBox::Setup](../Topic/CMFCFontComboBox::Setup.md)|初始化项列表FONT组合框中。|  
  
### 数据成员  
  
|名称|说明|  
|--------|--------|  
|[CMFCFontComboBox::m\_bDrawUsingFont](../Topic/CMFCFontComboBox::m_bDrawUsingFont.md)|指示要使用的字体绘制该项目在当前字体组合框标记的结构。|  
  
## 备注  
 若要使用 `CMFCFontComboBox` 对象在对话框中，添加一个 `CMFCFontComboBox` 变量添加到对话框选件类。  然后在对话框选件类的 `OnInitDialog` 方法，请调用 [CMFCFontComboBox::Setup](../Topic/CMFCFontComboBox::Setup.md) 方法初始化项列表在组合框控件的。  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CComboBox](../../mfc/reference/ccombobox-class.md)  
  
 [CMFCFontComboBox](../../mfc/reference/cmfcfontcombobox-class.md)  
  
## 要求  
 **标头:** afxfontcombobox.h  
  
## 请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [类](../../mfc/reference/mfc-classes.md)   
 [CMFCToolBarFontComboBox Class](../../mfc/reference/cmfctoolbarfontcombobox-class.md)   
 [CMFCFontInfo Class](../../mfc/reference/cmfcfontinfo-class.md)