---
title: "CDynamicParameterAccessor::GetParamStatus | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CDynamicParameterAccessor::GetParamStatus"
  - "CDynamicParameterAccessor.GetParamStatus"
  - "ATL.CDynamicParameterAccessor.GetParamStatus"
  - "ATL::CDynamicParameterAccessor::GetParamStatus"
  - "GetParamStatus"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "GetParamStatus 方法"
ms.assetid: 9300225a-616c-4a7d-82d0-8c2ecd4d8185
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# CDynamicParameterAccessor::GetParamStatus
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

检索存储在缓冲区中的指定参数的长度。  
  
## 语法  
  
```  
  
      bool GetParamStatus(  
   DBORDINAL nParam,  
   DBSTATUS* pStatus  
);  
DBSTATUS* GetParamStatus(   
   DBORDINAL nParam    
) const throw( );  
```  
  
#### 参数  
 `nParam`  
 \[in\] 参数数目 \(偏离 1\)。  为返回值保留参数 0 。  参数编号是基于其用 SQL 或存储过程调用的参数的索引。  有关示例，请参见[SetParam](../../data/oledb/cdynamicparameteraccessor-setparam.md)。  
  
 `pStatus`  
 \[out\] 对包含指定参数的 `DBSTATUS` 状态变量的指针。  有关 `DBSTATUS` 值的信息，请参见在 *OLE DB 程序员参考*中的[状态](https://msdn.microsoft.com/en-us/library/ms722617.aspx) 或在 oledb.h 中搜索 `DBSTATUS`。  
  
## 备注  
 第一种替代方法将返回上成功上失败的 **true** 或 **false**。  对包含指定的参数的内存的第二个重写点。  
  
## 要求  
 **标头:** atldbcli.h  
  
## 请参阅  
 [CDynamicParameterAccessor 类](../../data/oledb/cdynamicparameteraccessor-class.md)