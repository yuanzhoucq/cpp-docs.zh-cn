---
title: "CDynamicAccessor::GetValue | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "GetValue"
  - "CDynamicAccessor::GetValue<ctype>"
  - "ATL.CDynamicAccessor.GetValue<ctype>"
  - "CDynamicAccessor.GetValue"
  - "CDynamicAccessor::GetValue"
  - "ATL.CDynamicAccessor.GetValue"
  - "ATL::CDynamicAccessor::GetValue"
  - "ATL::CDynamicAccessor::GetValue<ctype>"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "GetValue 方法"
ms.assetid: 553f44af-68bc-4cb6-8774-e0940003fa90
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# CDynamicAccessor::GetValue
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

检索指定列的数据。  
  
## 语法  
  
```  
  
      void* GetValue(   
   DBORDINAL nColumn    
) const throw( );  
void* GetValue(  
   const CHAR* pColumnName   
) const throw( );  
void* GetValue(  
   const WCHAR* pColumnName   
) const throw( );  
template < class ctype >  
bool GetValue(  
   DBORDINAL nColumn,  
   ctype* pData   
) const throw( );  
template < class ctype >  
bool GetValue(  
   const CHAR* pColumnName,  
   ctype* pData   
) const throw( );  
template < class ctype >  
bool GetValue(  
   const WCHAR* pColumnName,  
   ctype* pData   
) const throw( );  
```  
  
#### 参数  
 `ctype`  
 \[in\] 处理除字符串类型的任何数据类型的模板参数\(**CHAR\***，**WCHAR\***\)，需要特殊处理。  `GetValue` 使用基于在这指定的相应数据类型。  
  
 `nColumn`  
 \[in\] 列号。  列数以 1 开始。  若有的话，值 0 是指书签列。  
  
 `pColumnName`  
 \[in\] 列名称。  
  
 `pData`  
 \[out\] 指定列的内容的指针。  
  
## 返回值  
 如果要传递字符串数据，请使用 `GetValue` 的 nontemplated 版本。  此方法的 nontemplated 版本返回 **void\***，指向缓冲区包含部件指定列数据。  如果找不到该列，则返回 **NULL**。  
  
 对于任何其他数据类型，使用 `GetValue` 模板化版本会更简单。  模板化版本在成功上返回 **true** 或在失败上返回 **false**。  
  
## 备注  
 使用 nontemplated 版本返回包含字符串和包含其他数据类型的列的模板化版本。  
  
 在调试模式中，如果 `pData` 大小不等于对它指向列的大小，则你将得到一个断言。  
  
## 要求  
 **标头:** atldbcli.h  
  
## 请参阅  
 [CDynamicAccessor 类](../../data/oledb/cdynamicaccessor-class.md)