---
title: "CSession::StartTransaction | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CSession::StartTransaction"
  - "StartTransaction"
  - "ATL.CSession.StartTransaction"
  - "CSession.StartTransaction"
  - "ATL::CSession::StartTransaction"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "StartTransaction 方法"
ms.assetid: cd7bd2be-fad1-4e2b-932b-79d308efb8fb
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# CSession::StartTransaction
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

开始此会话的新事务。  
  
## 语法  
  
```  
  
      HRESULT StartTransaction(  
   ISOLEVEL isoLevel = ISOLATIONLEVEL_READCOMMITTED,  
   ULONG isoFlags = 0,  
   ITransactionOptions* pOtherOptions = NULL,  
   ULONG* pulTransactionLevel = NULL   
) const throw( );  
```  
  
#### 参数  
 参阅《*OLE DB 程序员参考》\) 中的*[ITransactionLocal::StartTransaction](https://msdn.microsoft.com/en-us/library/ms709786.aspx)。  
  
## 返回值  
 标准 `HRESULT`。  
  
## 备注  
 有关详细信息，请参阅《*OLE DB 程序员参考》\) 中的*[ITransactionLocal::StartTransaction](https://msdn.microsoft.com/en-us/library/ms709786.aspx)。  
  
## 要求  
 **标头:** atldbcli.h  
  
## 请参阅  
 [CSession 类](../../data/oledb/csession-class.md)