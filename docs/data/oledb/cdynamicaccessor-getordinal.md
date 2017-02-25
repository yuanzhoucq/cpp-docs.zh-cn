---
title: "CDynamicAccessor::GetOrdinal | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CDynamicAccessor.GetOrdinal"
  - "ATL::CDynamicAccessor::GetOrdinal"
  - "CDynamicAccessor::GetOrdinal"
  - "ATL.CDynamicAccessor.GetOrdinal"
  - "GetOrdinal"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "GetOrdinal 方法"
ms.assetid: 2095b71c-a7a4-4034-89a1-77a78cb9633f
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# CDynamicAccessor::GetOrdinal
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

检索给定列名的列数。  
  
## 语法  
  
```  
  
      bool GetOrdinal(  
   const CHAR* pColumnName,  
   DBORDINAL* pOrdinal   
) const throw( );  
bool GetOrdinal(  
   const WCHAR* pColumnName,  
   DBORDINAL* pOrdinal   
) const throw( );  
```  
  
#### 参数  
 `pColumnName`  
 \[in\] 为包含列名的字符串的指针。  
  
 *pOrdinal*  
 \[out\] 指向列数的指针。  
  
## 返回值  
 如果找到具有指定名称的列，则返回 **true**。  否则，该函数返回**false**。  
  
## 要求  
 **标头:** atldbcli.h  
  
## 请参阅  
 [CDynamicAccessor 类](../../data/oledb/cdynamicaccessor-class.md)