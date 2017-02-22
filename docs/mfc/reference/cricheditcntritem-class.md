---
title: "CRichEditCntrItem Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CRichEditCntrItem"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CRichEditCntrItem class"
  - "OLE items, in rich edit views"
  - "Rich Edit 控件, OLE items"
  - "Rich Edit 控件, using"
ms.assetid: 6c0b4efe-0fb8-4621-b5e1-fdcb8ec48c3b
caps.latest.revision: 24
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 26
---
# CRichEditCntrItem Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

[CRichEditView](../../mfc/reference/cricheditview-class.md) 和 [CRichEditDoc](../../mfc/reference/cricheditdoc-class.md)，提供功能丰富在MFC的上下文中编辑文档中的控件视图结构。  
  
## 语法  
  
```  
class CRichEditCntrItem : public COleClientItem  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CRichEditCntrItem::CRichEditCntrItem](../Topic/CRichEditCntrItem::CRichEditCntrItem.md)|构造 `CRichEditCntrItem` 对象。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CRichEditCntrItem::SyncToRichEditObject](../Topic/CRichEditCntrItem::SyncToRichEditObject.md)|激活该项目为其他类型。|  
  
## 备注  
 “rich edit控件”是用户可以输入和编辑文本的窗口。  该文本分配字符和段落格式设置，并且可以包含嵌入OLE对象。  rich edit控件为格式化文本的编程接口。  但是，应用程序必须实现必要所有用户界面的组件具有格式设置操作提供给用户。  
  
 `CRichEditView` 维护文本和格式设置典型文本。  `CRichEditDoc` 维护OLE在视图的客户端项列表。  `CRichEditCntrItem` 提供容器端对OLE客户端项目。  
  
 此Windows公共控件\(并 [CRichEditCtrl](../../mfc/reference/cricheditctrl-class.md) 和相关选件类\)若要在运行Windows 95 \/98和Windows NT 3.51版下的程序可用和更高版本。  
  
 对于使用基于丰富编辑在MFC应用程序的容器项目，请参见 [WORDPAD](../../top/visual-cpp-samples.md) 示例应用程序。  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CDocItem](../../mfc/reference/cdocitem-class.md)  
  
 [COleClientItem](../../mfc/reference/coleclientitem-class.md)  
  
 `CRichEditCntrItem`  
  
## 要求  
 **Header:** afxrich.h  
  
## 请参阅  
 [MFC示例WORDPAD](../../top/visual-cpp-samples.md)   
 [COleClientItem Class](../../mfc/reference/coleclientitem-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CRichEditDoc Class](../../mfc/reference/cricheditdoc-class.md)   
 [CRichEditView Class](../../mfc/reference/cricheditview-class.md)