---
title: "CDynamicParameterAccessor::GetParamName | Microsoft Docs"
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
  - "CDynamicParameterAccessor::GetParamName"
  - "ATL.CDynamicParameterAccessor.GetParamName"
  - "GetParamName"
  - "CDynamicParameterAccessor.GetParamName"
  - "ATL::CDynamicParameterAccessor::GetParamName"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "GetParamName 方法"
ms.assetid: 707c08ed-d3d0-4ce8-b23e-20b07202a3e2
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CDynamicParameterAccessor::GetParamName
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

检索指定参数的名称。  
  
## 语法  
  
```  
  
      LPOLESTR GetParamName(   
   DBORDINAL nParam    
) const throw( );  
```  
  
#### 参数  
 `nParam`  
 \[in\] 参数数目 \(偏离 1\)。  为返回值保留参数 0 。  参数编号是基于其用 SQL 或存储过程调用的参数的索引。  有关示例，请参见[SetParam](../../data/oledb/cdynamicparameteraccessor-setparam.md)。  
  
## 返回值  
 获取指定工具的参数。  
  
## 要求  
 **标头:** atldbcli.h  
  
## 请参阅  
 [CDynamicParameterAccessor 类](../../data/oledb/cdynamicparameteraccessor-class.md)