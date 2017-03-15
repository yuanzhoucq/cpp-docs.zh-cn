---
title: "CDynamicParameterAccessor::GetParam | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CDynamicParameterAccessor::GetParam"
  - "ATL.CDynamicParameterAccessor.GetParam"
  - "CDynamicParameterAccessor::GetParam<ctype>"
  - "CDynamicParameterAccessor.GetParam"
  - "GetParam"
  - "ATL::CDynamicParameterAccessor::GetParam<ctype>"
  - "ATL::CDynamicParameterAccessor::GetParam"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "GetParam 方法"
ms.assetid: 893a6bf8-7b55-4f6d-8a10-a43b13be7f56
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# CDynamicParameterAccessor::GetParam
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

从参数缓冲区检索 nonstring 的数据指定的参数。  
  
## 语法  
  
```  
  
      template < class ctype > bool GetParam(   
   DBORDINAL nParam,   
   ctype* pData    
) const throw( );  
template < class ctype > bool GetParam(   
   TCHAR* pParamName,   
   ctype* pData    
) const throw( );  
void* GetParam(   
   DBORDINAL nParam    
) const throw( );  
void* GetParam(   
   TCHAR* pParamName    
) const throw( );  
```  
  
#### 参数  
 `ctype`  
 是数据类型的模板参数。  
  
 `nParam`  
 \[in\] 参数数目 \(偏离 1\)。  为返回值保留参数 0 。  参数编号是基于其用 SQL 或存储过程调用的参数的索引。  有关示例，请参见[SetParam](../../data/oledb/cdynamicparameteraccessor-setparam.md)。  
  
 `pParamName`  
 \[in\] 参数名。  
  
 `pData`  
 \[out\] 对包含数据的内存的指针检索从缓冲区。  
  
## 返回值  
 对于 nontemplated 版本，对包含数据内存的位置检索从缓冲区。  模板化版本在成功上返回 **true** 或在失败上返回 **false**。  
  
 使用 `GetParam` 检索 nonstring 从缓冲区的参数数据。  使用 [GetParamString](../../data/oledb/cdynamicparameteraccessor-getparamstring.md) 从缓冲区检索字符串参数数据。  
  
## 要求  
 **标头:** atldbcli.h  
  
## 请参阅  
 [CDynamicParameterAccessor 类](../../data/oledb/cdynamicparameteraccessor-class.md)