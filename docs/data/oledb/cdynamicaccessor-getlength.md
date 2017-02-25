---
title: "CDynamicAccessor::GetLength | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CDynamicAccessor.GetLength"
  - "ATL.CDynamicAccessor.GetLength"
  - "CDynamicAccessor::GetLength"
  - "ATL::CDynamicAccessor::GetLength"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "GetLength 方法"
ms.assetid: 3ae8983b-b267-4cf9-bfc0-3e191f79e646
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# CDynamicAccessor::GetLength
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

检索指定的列的长度。  
  
## 语法  
  
```  
  
      bool GetLength(   
   DBORDINAL nColumn,   
   DBLENGTH* pLength    
) const throw( );  
bool GetLength(   
   const CHAR* pColumnName,   
   DBLENGTH* pLength    
) const throw( );  
bool GetLength(   
   const WCHAR* pColumnName,   
   DBLENGTH* pLength    
) const throw( );  
```  
  
#### 参数  
 `nColumn`  
 \[in\] 列号。  列数以 1 开始。  若有的话，值 0 是指书签列。  
  
 `pColumnName`  
 \[in\] 为包含列名的字符串的指针。  
  
 `pLength`  
 \[out\] 为包含列长度（按字节）的整数的指针。  
  
## 返回值  
 如果指定的列找到，返回 **true**。  否则，该函数返回**false**。  
  
## 备注  
 第一种重写方法将采用列数，并且，第二个和第三个重写分别采用ANSI 或 Unicode 格式的列名。  
  
## 要求  
 **标头:** atldbcli.h  
  
## 请参阅  
 [CDynamicAccessor 类](../../data/oledb/cdynamicaccessor-class.md)   
 [CDynamicAccessor::SetLength](../../data/oledb/cdynamicaccessor-setlength.md)