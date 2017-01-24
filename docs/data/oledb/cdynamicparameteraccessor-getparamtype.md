---
title: "CDynamicParameterAccessor::GetParamType | Microsoft Docs"
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
  - "CDynamicParameterAccessor.GetParamType"
  - "CDynamicParameterAccessor:GetParamType"
  - "CDynamicParameterAccessor::GetParamType"
  - "ATL.CDynamicParameterAccessor.GetParamType"
  - "GetParamType"
  - "ATL::CDynamicParameterAccessor::GetParamType"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "GetParamType 方法"
ms.assetid: d9c46775-c2a6-4100-8b69-99f13c52958b
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CDynamicParameterAccessor::GetParamType
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

检索指定参数的数据类型。  
  
## 语法  
  
```  
  
      bool GetParamType(  
   DBORDINAL nParam,  
   DBTYPE* pType   
) const throw( );  
```  
  
#### 参数  
 `nParam`  
 \[in\] 参数数目 \(偏离 1\)。  参数 0 用于返回值保留的。  参数编号是基于其用 SQL 或存储过程调用的参数的索引。  用于示例参见 [SetParam](../../data/oledb/cdynamicparameteraccessor-setparam.md)。  
  
 `pType`  
 \[out\] 对包含指定参数的数据类型的变量的指针。  
  
## 返回值  
 在成功的返回 **true** 或 **false** 上失败。  
  
## 要求  
 **标头:** atldbcli.h  
  
## 请参阅  
 [CDynamicParameterAccessor 类](../../data/oledb/cdynamicparameteraccessor-class.md)