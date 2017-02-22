---
title: "CDocItem Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CDocItem"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CDocItem class"
  - "client document items"
  - "container document items"
  - "document items"
  - "items, 文档"
  - "OLE 文档, items"
  - "server documents"
  - "server documents, document items"
ms.assetid: 84fb8610-a4c8-4211-adc0-e70e8d002c11
caps.latest.revision: 22
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 23
---
# CDocItem Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

基类为文档项目，是文件中的数据的元素。  
  
## 语法  
  
```  
class CDocItem : public CCmdTarget  
```  
  
## 成员  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CDocItem::GetDocument](../Topic/CDocItem::GetDocument.md)|返回包含项目的文档。|  
|[CDocItem::IsBlank](../Topic/CDocItem::IsBlank.md)|确定该项是否包含任何信息。|  
  
## 备注  
 `CDocItem` 对象用于表示中的OLE项客户端和服务器文档。  
  
 有关更多信息，请参见文章 [容器:实现容器](../../mfc/containers-implementing-a-container.md)。  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 `CDocItem`  
  
## 要求  
 **Header:** afxole.h  
  
## 请参阅  
 [CCmdTarget Class](../../mfc/reference/ccmdtarget-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [COleDocument Class](../../mfc/reference/coledocument-class.md)   
 [COleServerItem Class](../../mfc/reference/coleserveritem-class.md)   
 [COleClientItem Class](../../mfc/reference/coleclientitem-class.md)