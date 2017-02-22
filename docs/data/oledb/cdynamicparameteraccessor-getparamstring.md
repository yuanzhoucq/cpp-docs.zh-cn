---
title: "CDynamicParameterAccessor::GetParamString | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CDynamicParameterAccessor.GetParamString"
  - "GetParamString"
  - "CDynamicParameterAccessor::GetParamString"
  - "ATL.CDynamicParameterAccessor.GetParamString"
  - "ATL::CDynamicParameterAccessor::GetParamString"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "GetParamString 方法"
ms.assetid: 078c2b1c-7072-47c1-a203-f47e75363f91
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# CDynamicParameterAccessor::GetParamString
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

检索存储在缓冲区中的指定参数的字符串数据。  
  
## 语法  
  
```  
  
      bool GetParamString(  
   DBORDINAL nParam,  
   CSimpleStringA& strOutput  
) throw( );  
bool GetParamString(  
   DBORDINAL nParam,  
   CSimpleStringW& strOutput  
) throw( );  
bool GetParamString(  
   DBORDINAL nParam,  
   CHAR* pBuffer,  
   size_t* pMaxLen  
) throw( );  
bool GetParamString(  
   DBORDINAL nParam,  
   WCHAR* pBuffer,  
   size_t* pMaxLen  
) throw( );  
```  
  
#### 参数  
 `nParam`  
 \[in\] 参数数目 \(偏离 1\)。  为返回值保留参数 0 。  参数编号是基于其用 SQL 或存储过程调用的参数的索引。  有关示例，请参见[SetParam](../../data/oledb/cdynamicparameteraccessor-setparam.md)。  
  
 `strOutput`  
 \[out\] 指定参数的 ANSI \(**CSimpleStringA**\) 或**CSimpleStringW**\(Unicode 字符串\) 数据。  例如应传递参数，类型 `CString`:  
  
 [!code-cpp[NVC_OLEDB_Consumer#9](../../data/oledb/codesnippet/CPP/cdynamicparameteraccessor-getparamstring_1.cpp)]  
  
 `pBuffer`  
 \[out\] 为 ANSI \(**CHAR**\) 的指针或 Unicode \(**WCHAR**\) 指定参数的字符串数据。  
  
 `pMaxLen`  
 \[out\] 与缓冲区大小的指针指向 `pBuffer` \(在字符，包括终止 null。\)  
  
## 备注  
 如果成功，则返回**true**；如果失败，则返回**false**。  
  
 如果 `pBuffer` 为 NULL，此方法将在内存所需的缓冲区大小由 `pMaxLen` 指向并返回 **true**，而不复制数据。  
  
 如果缓冲区 `pBuffer` 不足以容纳整个字符串，该方法将失败。  
  
 使用 `GetParamString` 检索string 从缓冲区的参数数据。  使用[GetParam](../../data/oledb/cdynamicparameteraccessor-getparam.md)检索 nonstring 从缓冲区的参数数据。  
  
## 要求  
 **标头:** atldbcli.h  
  
## 请参阅  
 [CDynamicParameterAccessor 类](../../data/oledb/cdynamicparameteraccessor-class.md)