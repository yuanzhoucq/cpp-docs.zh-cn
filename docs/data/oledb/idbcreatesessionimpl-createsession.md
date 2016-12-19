---
title: "IDBCreateSessionImpl::CreateSession | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDBCreateSessionImpl::CreateSession"
  - "IDBCreateSessionImpl.CreateSession"
  - "CreateSession"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CreateSession 方法"
ms.assetid: 035e5ddb-56e6-43b1-874d-89c0e40b103b
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# IDBCreateSessionImpl::CreateSession
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

创建从数据源对象的新会话并返回在新生成的会话的请求的接口。  
  
## 语法  
  
```  
  
      STDMETHOD(CreateSession)(   
   IUnknown * pUnkOuter,   
   REFIID riid,   
   IUnknown ** ppDBSession    
);  
```  
  
#### 参数  
 有关更多信息，请参见 *OLE DB Programmer's Reference*中的[IDBCreateSession::CreateSession](https://msdn.microsoft.com/en-us/library/ms714942.aspx)。  
  
## 要求  
 **头文件：** atldb.h  
  
## 请参阅  
 [IDBCreateSessionImpl 类](../../data/oledb/idbcreatesessionimpl-class.md)