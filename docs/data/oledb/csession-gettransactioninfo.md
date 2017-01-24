---
title: "CSession::GetTransactionInfo | Microsoft Docs"
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
  - "GetTransactionInfo"
  - "CSession.GetTransactionInfo"
  - "ATL.CSession.GetTransactionInfo"
  - "CSession::GetTransactionInfo"
  - "ATL::CSession::GetTransactionInfo"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "GetTransactionInfo 方法"
ms.assetid: 9fa62808-3162-4b5a-8610-e1abb8cf9a71
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CSession::GetTransactionInfo
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

返回有关事务的信息。  
  
## 语法  
  
```  
  
      HRESULT GetTransactionInfo(   
   XACTTRANSINFO* pInfo    
) const throw( );  
```  
  
#### 参数  
 参见在 *OLE DB Programmer's Reference*中的 [ITransaction::GetTransactionInfo](https://msdn.microsoft.com/en-us/library/ms714975.aspx)。  
  
## 返回值  
 标准版`HRESULT`。  
  
## 备注  
 有关详细信息，请参阅《*OLE DB 程序员参考》\) 中的*[ITransaction::GetTransactionInfo](https://msdn.microsoft.com/en-us/library/ms714975.aspx)。  
  
## 要求  
 **标头:** atldbcli.h  
  
## 请参阅  
 [CSession 类](../../data/oledb/csession-class.md)