---
title: "CDynamicAccessor::GetColumnType | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ATL.CDynamicAccessor.GetColumnType"
  - "CDynamicAccessor::GetColumnType"
  - "GetColumnType"
  - "CDynamicAccessor.GetColumnType"
  - "ATL::CDynamicAccessor::GetColumnType"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "GetColumnType 方法"
ms.assetid: ac96a2e9-6049-4eb5-9718-9f5f5446b74e
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# CDynamicAccessor::GetColumnType
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

检索指定列的数据类型。  
  
## 语法  
  
```  
  
      bool GetColumnType(   
   DBORDINAL nColumn,   
   DBTYPE* pType    
) const throw( );  
```  
  
#### 参数  
 `nColumn`  
 \[in\] 列号。  列数以 1 开始。  若有的话，值 0 是指书签列。  
  
 `pType`  
 \[out\] 一个指向列中的值类型的指针。  
  
## 返回值  
 如果成功，则返回**true**；如果失败，则返回**false**。  
  
## 要求  
 **标头:** atldbcli.h  
  
## 请参阅  
 [CDynamicAccessor 类](../../data/oledb/cdynamicaccessor-class.md)   
 [DBTYPE](https://msdn.microsoft.com/en-us/library/ms711251.aspx)