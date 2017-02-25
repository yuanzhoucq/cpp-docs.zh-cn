---
title: "IDBCreateCommandImpl::CreateCommand | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDBCreateCommandImpl.CreateCommand"
  - "CreateCommand"
  - "IDBCreateCommandImpl::CreateCommand"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CreateCommand 方法"
ms.assetid: 50ffbf8b-2c07-4bcb-96c5-ffce4519c7f7
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# IDBCreateCommandImpl::CreateCommand
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

创建新的命令并返回请求的接口。  
  
## 语法  
  
```  
  
      STDMETHOD(CreateCommand)(   
   IUnknown * pUnkOuter,   
   REFIID riid,   
   IUnknown ** ppvCommand    
);  
```  
  
#### 参数  
 有关更多信息，请参见 [OLE DB 程序员参考](https://msdn.microsoft.com/en-us/library/ms709772.aspx)（在  中）。  
  
 有些参数对应于 *OLE DB 程序员参考* 不同的名称的引用参数在 **IDBCreateCommand::CreateCommand**中说明：  
  
|OLE DB 模板参数|*OLE DB 程序员引用*参数|  
|-----------------|----------------------|  
|*ppvCommand*|*ppCommand*|  
  
## 要求  
 **页眉：** atldb.h  
  
## 请参阅  
 [IDBCreateCommandImpl 类](../../data/oledb/idbcreatecommandimpl-class.md)