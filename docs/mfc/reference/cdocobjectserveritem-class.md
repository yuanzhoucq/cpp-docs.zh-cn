---
title: "CDocObjectServerItem Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CDocObjectServerItem"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ActiveX documents [C++], document server"
  - "CDocObjectServerItem class"
  - "docobject server"
  - "document object server"
  - "servers [C++], ActiveX documents"
  - "servers [C++], doc objects"
ms.assetid: 530f7156-50c8-4806-9328-602c9133f622
caps.latest.revision: 22
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 23
---
# CDocObjectServerItem Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

实现OLE特定服务器谓词DocObject服务器的。  
  
## 语法  
  
```  
class CDocObjectServerItem : public COleServerItem  
```  
  
## 成员  
  
### 受保护的构造函数  
  
|名称|说明|  
|--------|--------|  
|[CDocObjectServerItem::CDocObjectServerItem](../Topic/CDocObjectServerItem::CDocObjectServerItem.md)|构造 `CDocObjectServerItem` 对象。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CDocObjectServerItem::GetDocument](../Topic/CDocObjectServerItem::GetDocument.md)|检索指向包含项目的文档。|  
  
### 受保护的方法  
  
|名称|说明|  
|--------|--------|  
|[CDocObjectServerItem::OnHide](../Topic/CDocObjectServerItem::OnHide.md)|如果该结构尝试隐藏DocObject项目，将引发异常。|  
|[CDocObjectServerItem::OnShow](../Topic/CDocObjectServerItem::OnShow.md)|调用由结构进行DocObject项目就地激活。  如果该项不是DocObject，调用 [COleServerItem::OnShow](../Topic/COleServerItem::OnShow.md)。|  
  
## 备注  
 `CDocObjectServerItem` 定义可重写的成员函数: [OnHide](../Topic/CDocObjectServerItem::OnHide.md)、 [OnOpen](http://msdn.microsoft.com/zh-cn/7a9b1363-6ad8-4732-9959-4e35c07644fd)和 [OnShow](../Topic/CDocObjectServerItem::OnShow.md)。  
  
 若要使用 `CDocObjectServerItem`，请确保在您的 `COleServerDoc`的 [OnGetEmbeddedItem](../Topic/COleServerDoc::OnGetEmbeddedItem.md) 重写派生类返回一个新的 `CDocObjectServerItem` 对象。  如果需要更改在项目的任何功能，您可以创建自己的 `CDocObjectServerItem`新实例的派生类。  
  
 有关DocObjects的详细信息，请参见 [CDocObjectServer](../../mfc/reference/cdocobjectserver-class.md) 和 [COleCmdUI](../../mfc/reference/colecmdui-class.md) " *MFC参考*。  另请参见 [Internet第一步:活动文档](../../mfc/active-documents-on-the-internet.md) 和 [活动文档](../../mfc/active-documents-on-the-internet.md)。  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CDocItem](../../mfc/reference/cdocitem-class.md)  
  
 [COleServerItem](../../mfc/reference/coleserveritem-class.md)  
  
 `CDocObjectServerItem`  
  
## 要求  
 **Header:** afxdocob.h  
  
## 请参阅  
 [COleServerItem Class](../../mfc/reference/coleserveritem-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CDocObjectServer Class](../../mfc/reference/cdocobjectserver-class.md)   
 [COleDocObjectItem Class](../../mfc/reference/coledocobjectitem-class.md)