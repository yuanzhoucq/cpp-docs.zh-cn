---
title: "CDocObjectServer Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CDocObjectServer"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ActiveX documents [C++], document server"
  - "CDocObjectServer class"
  - "docobject server"
  - "document object server"
  - "servers [C++], ActiveX documents"
  - "servers [C++], doc objects"
ms.assetid: 18cd0dff-0616-4472-b8d9-66c081bc383a
caps.latest.revision: 23
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 24
---
# CDocObjectServer Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

实现需要其他的OLE接口进行普通 `COleDocument` 服务器转换为完整的DocObject服务器: `IOleDocument`、 `IOleDocumentView`、 `IOleCommandTarget`和 `IPrint`。  
  
## 语法  
  
```  
class CDocObjectServer : public CCmdTarget  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CDocObjectServer::CDocObjectServer](../Topic/CDocObjectServer::CDocObjectServer.md)|构造 `CDocObjectServer` 对象。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CDocObjectServer::ActivateDocObject](../Topic/CDocObjectServer::ActivateDocObject.md)|活动文档服务器对象，但是，不显示它。|  
  
### 受保护的方法  
  
|名称|说明|  
|--------|--------|  
|[CDocObjectServer::OnActivateView](../Topic/CDocObjectServer::OnActivateView.md)|显示DocObject视图。|  
|[CDocObjectServer::OnApplyViewState](../Topic/CDocObjectServer::OnApplyViewState.md)|还原DocObject视图状态。|  
|[CDocObjectServer::OnSaveViewState](../Topic/CDocObjectServer::OnSaveViewState.md)|保存DocObject视图状态。|  
  
## 备注  
 `CDocObjectServer` 从 `CCmdTarget` 和工作更加派生与 `COleServerDoc` 公开接口。  
  
 DocObject服务器文档可以包含 [CDocObjectServerItem](../../mfc/reference/cdocobjectserveritem-class.md) 对象，该对象表示服务器接口为DocObject项目。  
  
 若要自定义您的DocObject服务器，从 `CDocObjectServer` 派生您的选件类并重写其视图设置功能、 [OnActivateView](../Topic/CDocObjectServer::OnActivateView.md)、 [OnApplyViewState](../Topic/CDocObjectServer::OnApplyViewState.md)和 [OnSaveViewState](../Topic/CDocObjectServer::OnSaveViewState.md)。  您将需要提供自己的选件类的新实例以响应机制调用。  
  
 有关DocObjects的详细信息，请参见 [CDocObjectServerItem](../../mfc/reference/cdocobjectserveritem-class.md) 和 [COleCmdUI](../../mfc/reference/colecmdui-class.md) " *MFC参考*。  另请参见 [Internet第一步:活动文档](../../mfc/active-documents-on-the-internet.md) 和 [活动文档](../../mfc/active-documents-on-the-internet.md)。  
  
 请参见下面的知识库文章:  
  
-   Q247382:PRB:控件的工具提示在ActiveX文档服务器由ActiveX隐藏文档容器  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 `CDocObjectServer`  
  
## 要求  
 **Header:** afxdocob.h  
  
## 请参阅  
 [CCmdTarget Class](../../mfc/reference/ccmdtarget-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CDocObjectServerItem Class](../../mfc/reference/cdocobjectserveritem-class.md)