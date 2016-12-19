---
title: "CDynamicParameterAccessor::GetParamIO | Microsoft Docs"
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
  - "GetParamIO"
  - "CDynamicParameterAccessor::GetParamIO"
  - "ATL.CDynamicParameterAccessor.GetParamIO"
  - "CDynamicParameterAccessor.GetParamIO"
  - "ATL::CDynamicParameterAccessor::GetParamIO"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "GetParamIO 方法"
ms.assetid: 9c485e39-c67e-4df7-a707-c773019c4d1e
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CDynamicParameterAccessor::GetParamIO
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

确定指定的参数是否输入或输出参数。  
  
## 语法  
  
```  
  
      bool GetParamIO(   
   DBORDINAL nParam,   
   DBPARAMIO * pParamIO    
) const throw( );  
```  
  
#### 参数  
 `nParam`  
 \[in\] 参数数目 \(偏离 1\)。  为返回值保留参数 0 。  参数编号是基于其用 SQL 或存储过程调用的参数的索引。  有关示例，请参见[SetParam](../../data/oledb/cdynamicparameteraccessor-setparam.md)。  
  
 *pParamIO*  
 将包含 **DBPARAMIO** 类型 \(输入或输出\) 指定的参数变量的指针。  其定义如下：  
  
 `typedef DWORD DBPARAMIO;`  
  
 `enum DBPARAMIOENUM`  
  
 `{   DBPARAMIO_NOTPARAM   = 0,`  
  
 `DBPARAMIO_INPUT      = 0x1,`  
  
 `DBPARAMIO_OUTPUT     = 0x2`  
  
 `};`  
  
## 返回值  
 如果成功，则返回**true**；如果失败，则返回**false**。  
  
## 要求  
 **标头:** atldbcli.h  
  
## 请参阅  
 [CDynamicParameterAccessor 类](../../data/oledb/cdynamicparameteraccessor-class.md)