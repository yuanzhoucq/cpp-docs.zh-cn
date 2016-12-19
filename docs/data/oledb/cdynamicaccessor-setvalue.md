---
title: "CDynamicAccessor::SetValue | Microsoft Docs"
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
  - "ATL.CDynamicAccessor.SetValue"
  - "ATL::CDynamicAccessor::SetValue"
  - "ATL::CDynamicAccessor::SetValue<ctype>"
  - "CDynamicAccessor.SetValue"
  - "ATL.CDynamicAccessor.SetValue<ctype>"
  - "CDynamicAccessor::SetValue"
  - "CDynamicAccessor::SetValue<ctype>"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "SetValue 方法"
ms.assetid: ecc18850-96e5-4845-abe5-ab34ad467238
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CDynamicAccessor::SetValue
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

数据存储为指定列。  
  
## 语法  
  
```  
  
      template < class ctype >    
bool SetValue(   
   DBORDINAL nColumn,   
   const ctype& data    
) throw( );  
template < class ctype >    
bool SetValue(   
   const CHAR * pColumnName,   
   const ctype& data    
) throw( );  
template <class ctype>   
bool SetValue(  
   const WCHAR *pColumnName,  
   const ctype& data   
) throw( );  
```  
  
#### 参数  
 `ctype`  
 \[in\] 处理除字符串的任何数据类型的模板参数类型 \(**CHAR\***，**WCHAR\***\)，需要特殊处理。  `GetValue` 用于根据的相应数据类型。此处指定。  
  
 `pColumnName`  
 \[in\] 为包含列名的字符串的指针。  
  
 `data`  
 \[in\] 对包含数据的内存的指针。  
  
 `nColumn`  
 \[in\] 列数。  与 1. 的列数开头。  值 0 是指，书签列，如果中的任何一个。  
  
## 返回值  
 如果要设置字符串数据，请使用 `GetValue`nontemplated 版本。  此方法 nontemplated 版本返回 **void\***，指向缓冲区包含部件指定列数据。  如果列没有找到，将返回 **NULL**。  
  
 对于任何其他数据类型，使用 `GetValue`会更简单模板化版本。  模板化版本返回在成功上失败的 **true** 或 **false**。  
  
## 要求  
 **标头:** atldbcli.h  
  
## 请参阅  
 [CDynamicAccessor 类](../../data/oledb/cdynamicaccessor-class.md)