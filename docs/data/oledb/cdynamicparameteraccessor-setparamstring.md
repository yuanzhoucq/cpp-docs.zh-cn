---
title: "CDynamicParameterAccessor::SetParamString | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ATL.CDynamicParameterAccessor.SetParamString"
  - "ATL::CDynamicParameterAccessor::SetParamString"
  - "SetParamString"
  - "CDynamicParameterAccessor::SetParamString"
  - "CDynamicParameterAccessor.SetParamString"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "SetParamString 方法"
ms.assetid: 77a38d23-7e33-4e5a-bda6-c12c4c3fe2e4
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# CDynamicParameterAccessor::SetParamString
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

检索存储在缓冲区中的指定参数的字符串数据。  
  
## 语法  
  
```  
  
      bool SetParamString(   
   DBORDINAL nParam,   
   const CHAR* pString,   
   DBSTATUS status = DBSTATUS_S_OK    
) throw( );  
bool SetParamString(   
   DBORDINAL nParam,   
   const WCHAR* pString,   
   DBSTATUS status = DBSTATUS_S_OK    
) throw( );  
```  
  
#### 参数  
 `nParam`  
 \[in\] 参数数目 \(偏离 1\)。  为返回值保留参数 0 。  参数编号是基于其用 SQL 或存储过程调用的参数的索引。  有关示例，请参见[SetParam](../../data/oledb/cdynamicparameteraccessor-setparam.md)。  
  
 `pString`  
 \[in\] 为 ANSI \(**CHAR**\) 的指针或 Unicode \(**WCHAR**\) 指定参数的字符串数据。  参见 oledb.h 中的 `DBSTATUS`。  
  
 *status*  
 \[in\] 指定参数的 `DBSTATUS` 状态。  有关 `DBSTATUS` 值的信息，请参见在 *OLE DB 程序员参考*中的[状态](https://msdn.microsoft.com/en-us/library/ms722617.aspx) 或在 oledb.h 中搜索 `DBSTATUS`。  
  
## 备注  
 如果成功，则返回**true**；如果失败，则返回**false**。  
  
 `SetParamString` 将失败，如果尝试将设置为大于 `pString`指定的最大大小值的字符串。  
  
 使用 `SetParamString` 将字符串在缓冲区的参数数据。  使用 [SetParam](../../data/oledb/cdynamicparameteraccessor-setparam.md) 将缓冲区的 nonstring 的参数数据。  
  
## 要求  
 **标头:** atldbcli.h  
  
## 请参阅  
 [CDynamicParameterAccessor 类](../../data/oledb/cdynamicparameteraccessor-class.md)