---
title: "CDynamicAccessor::GetColumnFlags | Microsoft Docs"
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
  - "CDynamicAccessor.GetColumnFlags"
  - "ATL::CDynamicAccessor::GetColumnFlags"
  - "ATL.CDynamicAccessor.GetColumnFlags"
  - "CDynamicAccessor::GetColumnFlags"
  - "GetColumnFlags"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "GetColumnFlags 方法"
ms.assetid: b2ba2f3a-2c61-4a49-abfb-75823908ccf4
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CDynamicAccessor::GetColumnFlags
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

检索列特性。  
  
## 语法  
  
```  
  
      bool GetColumnFlags(   
   DBORDINAL nColumn,   
   DBCOLUMNFLAGS* pFlags    
) const throw( );  
```  
  
#### 参数  
 `nColumn`  
 \[in\] 列数。  与 1. 的列数开头。  值 0 是指，书签列，如果中的任何一个。  
  
 `pFlags`  
 \[out\] 指向描述列特性的位屏蔽的指针。  请参见“DBCOLUMNFLAGS 枚举类型在”*OLE DB 程序员参考》\) 中的*[IColumnsInfo::GetColumnInfo](https://msdn.microsoft.com/en-us/library/ms722704.aspx)。  
  
## 返回值  
 如果列特性成功找回，返回 **true**。  否则，返回 **false**。  
  
## 备注  
 列数从一个偏移量。  列零是一个特例；如果有的话为书签。  
  
## 要求  
 **标头:** atldbcli.h  
  
## 请参阅  
 [CDynamicAccessor 类](../../data/oledb/cdynamicaccessor-class.md)