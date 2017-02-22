---
title: "COleTemplateServer Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "COleTemplateServer"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Automation servers [C++], 实现"
  - "COleTemplateServer class"
  - "link containers [C++]"
  - "OLE link containers"
  - "OLE 服务器应用程序, COleTemplateServer class"
  - "OLE 服务器应用程序, managing server documents"
  - "服务器, OLE"
  - "visual editing, 服务器"
ms.assetid: 47a2887d-8162-4993-a842-a784177c7f5c
caps.latest.revision: 23
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 25
---
# COleTemplateServer Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

用于编辑服务器、自动化服务器和链接容器\(支持连接到嵌入\)的应用程序的OLE可视化。  
  
## 语法  
  
```  
class COleTemplateServer : public COleObjectFactory  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[COleTemplateServer::COleTemplateServer](../Topic/COleTemplateServer::COleTemplateServer.md)|构造 `COleTemplateServer` 对象。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[COleTemplateServer::ConnectTemplate](../Topic/COleTemplateServer::ConnectTemplate.md)|连接文档模板为基础 `COleObjectFactory` 对象。|  
|[COleTemplateServer::Unregister](../Topic/COleTemplateServer::Unregister.md)|关联的取消文档模板。|  
|[COleTemplateServer::UpdateRegistry](../Topic/COleTemplateServer::UpdateRegistry.md)|注册OLE系统注册表的文件类型。|  
  
## 备注  
 此选件类从选件类 [COleObjectFactory](../../mfc/reference/coleobjectfactory-class.md)派生;通常，可以直接使用 `COleTemplateServer` 而不是派生您的选件类。  `COleTemplateServer` 使用一 [CDocTemplate](../../mfc/reference/cdoctemplate-class.md) 对象控制服务器文档。  请使用 `COleTemplateServer`，当实现完整的服务器，也就是说，可以运行作为独立应用程序的服务器上。  完整服务器通常是多个文档界面\(MDI\)应用程序，不过，单文档界面\(SDI\)应用程序的支持。  一 `COleTemplateServer` 对象为服务器的每种类型需要的文档应用程序支持;也就是说，如果您的服务器应用程序支持工作表和图表，您必须具有两 `COleTemplateServer` 对象。  
  
 `COleTemplateServer` 重写 `COleObjectFactory`定义的 `OnCreateInstance` 成员函数。  此成员函数由框架调用创建适当类型的c. C\+\+对象。  
  
 有关服务器的更多信息，请参见文章 [服务器:实现服务器](../../mfc/servers-implementing-a-server.md)。  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [COleObjectFactory](../../mfc/reference/coleobjectfactory-class.md)  
  
 `COleTemplateServer`  
  
## 要求  
 **Header:** afxdisp.h  
  
## 请参阅  
 [MFC示例HIERSVR](../../top/visual-cpp-samples.md)   
 [COleObjectFactory Class](../../mfc/reference/coleobjectfactory-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [COleServerDoc Class](../../mfc/reference/coleserverdoc-class.md)   
 [COleServerItem Class](../../mfc/reference/coleserveritem-class.md)