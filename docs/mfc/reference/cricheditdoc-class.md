---
title: "CRichEditDoc Class | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CRichEditDoc"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CRichEditDoc class"
  - "document/view architecture, Rich Edit 控件"
  - "文档, rich edit"
  - "OLE containers, rich edit"
  - "Rich Edit 控件, OLE container"
ms.assetid: c936ec18-d516-49d4-b7fb-c9aa0229eddc
caps.latest.revision: 24
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CRichEditDoc Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

[CRichEditView](../../mfc/reference/cricheditview-class.md) 和 [CRichEditCntrItem](../../mfc/reference/cricheditcntritem-class.md)，提供功能丰富在MFC的上下文中编辑文档中的控件视图结构。  
  
## 语法  
  
```  
  
class CRichEditDoc : public COleServerDoc  
  
```  
  
## 成员  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CRichEditDoc::CreateClientItem](../Topic/CRichEditDoc::CreateClientItem.md)|调用执行文档的清理。|  
|[CRichEditDoc::GetStreamFormat](../Topic/CRichEditDoc::GetStreamFormat.md)|指示流输入和输出是否应包括格式设置信息。|  
|[CRichEditDoc::GetView](../Topic/CRichEditDoc::GetView.md)|检索asssociated [CRichEditView](../../mfc/reference/cricheditview-class.md) 对象。|  
  
### 公共数据成员  
  
|名称|说明|  
|--------|--------|  
|[CRichEditDoc::m\_bRTF](../Topic/CRichEditDoc::m_bRTF.md)|指示流I\/O是否应包括格式设置。|  
  
## 备注  
 “rich edit控件”是用户可以输入和编辑文本的窗口。  该文本分配字符和段落格式设置，并且可以包含嵌入OLE对象。  rich edit控件为格式化文本的编程接口。  但是，应用程序必须实现必要所有用户界面的组件具有格式设置操作提供给用户。  
  
 `CRichEditView` 维护文本和格式设置典型文本。  `CRichEditDoc` 维护的客户端项列表在视图。  `CRichEditCntrItem` 提供容器端对OLE客户端项目。  
  
 此Windows公共控件\(并 [CRichEditCtrl](../../mfc/reference/cricheditctrl-class.md) 和相关选件类\)若要在运行Windows 95 \/98和Windows NT 3.51版下的程序可用和更高版本。  
  
 对的示例丰富在MFC应用程序的文档，请参见 [WORDPAD](../../top/visual-cpp-samples.md) 示例应用程序。  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CDocument](../../mfc/reference/cdocument-class.md)  
  
 [COleDocument](../../mfc/reference/coledocument-class.md)  
  
 [COleLinkingDoc](../../mfc/reference/colelinkingdoc-class.md)  
  
 [COleServerDoc](../../mfc/reference/coleserverdoc-class.md)  
  
 `CRichEditDoc`  
  
## 要求  
 **Header:** afxrich.h  
  
## 请参阅  
 [MFC示例WORDPAD](../../top/visual-cpp-samples.md)   
 [COleServerDoc Class](../../mfc/reference/coleserverdoc-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CRichEditView Class](../../mfc/reference/cricheditview-class.md)   
 [CRichEditCntrItem Class](../../mfc/reference/cricheditcntritem-class.md)   
 [COleDocument Class](../../mfc/reference/coledocument-class.md)   
 [CRichEditCtrl Class](../../mfc/reference/cricheditctrl-class.md)