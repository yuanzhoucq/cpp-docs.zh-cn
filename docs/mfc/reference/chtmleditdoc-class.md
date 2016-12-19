---
title: "CHtmlEditDoc Class | Microsoft Docs"
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
  - "CHtmlEditDoc"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CHtmlEditDoc class"
ms.assetid: b2cca61f-e5d6-4099-b0d1-46bf85f0bd64
caps.latest.revision: 24
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CHtmlEditDoc Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

[CHtmlEditView](../../mfc/reference/chtmleditview-class.md)，提供编辑平台浏览器的功能在MFC文档视图结构的上下文中。  
  
## 语法  
  
```  
class AFX_NOVTABLE CHtmlEditDoc : public CDocument  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CHtmlEditDoc::CHtmlEditDoc](../Topic/CHtmlEditDoc::CHtmlEditDoc.md)|构造 `CHtmlEditDoc` 对象。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CHtmlEditDoc::GetView](../Topic/CHtmlEditDoc::GetView.md)|检索附加 `CHtmlEditView` 对象到该文档。|  
|[CHtmlEditDoc::IsModified](../Topic/CHtmlEditDoc::IsModified.md)|返回关联的视图的浏览器控件是否包含用户修改的文档。|  
|[CHtmlEditDoc::OpenURL](../Topic/CHtmlEditDoc::OpenURL.md)|打开URL。|  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CDocument](../../mfc/reference/cdocument-class.md)  
  
 `CHtmlEditDoc`  
  
## 要求  
 **Header:** afxhtml.h  
  
## 请参阅  
 [HTMLEdit示例](../../top/visual-cpp-samples.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)