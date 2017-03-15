---
title: "CSession::Commit | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CSession.Commit"
  - "ATL.CSession.Commit"
  - "ATL::CSession::Commit"
  - "CSession::Commit"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Commit 方法"
ms.assetid: 1d5f56b9-000c-4bae-a975-89d3452f499f
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# CSession::Commit
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

提交事务。  
  
## 语法  
  
```  
  
      HRESULT Commit(   
   BOOL bRetaining = FALSE,   
   DWORD grfTC = XACTTC_SYNC,   
   DWORD grfRM = 0    
) const throw( );  
```  
  
#### 参数  
 参见在 *OLE DB Programmer's Reference*中的 [ITransaction::GetTransactionInfo](https://msdn.microsoft.com/en-us/library/ms713008.aspx)。  
  
## 返回值  
 标准版`HRESULT`。  
  
## 备注  
 有关更多信息，请参见 [ITransaction::Commit](https://msdn.microsoft.com/en-us/library/ms713008.aspx)。  
  
## 要求  
 **标头:** atldbcli.h  
  
## 请参阅  
 [CSession 类](../../data/oledb/csession-class.md)