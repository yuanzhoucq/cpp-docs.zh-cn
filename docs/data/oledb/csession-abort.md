---
title: "CSession::Abort | Microsoft Docs"
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
  - "CSession.Abort"
  - "CSession::Abort"
  - "ATL.CSession.Abort"
  - "ATL::CSession::Abort"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Abort 方法"
ms.assetid: 02413b20-c486-451f-b4d7-73a6e8065df8
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CSession::Abort
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

终止事务。  
  
## 语法  
  
```  
  
      HRESULT Abort(   
   BOID* pboidReason = NULL,   
   BOOL bRetaining = FALSE,   
   BOOL bAsync = FALSE    
) const throw( );  
```  
  
#### 参数  
 参见[ITransaction::Abort](https://msdn.microsoft.com/en-us/library/ms709833.aspx)在 *OLE DB Programmer's Reference*中。  
  
## 返回值  
 标准版`HRESULT`。  
  
## 要求  
 **标头:** atldbcli.h  
  
## 请参阅  
 [CSession 类](../../data/oledb/csession-class.md)