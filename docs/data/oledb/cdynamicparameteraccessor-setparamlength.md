---
title: "CDynamicParameterAccessor::SetParamLength | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ATL::CDynamicParameterAccessor::SetParamLength"
  - "CDynamicParameterAccessor.SetParamLength"
  - "ATL.CDynamicParameterAccessor.SetParamLength"
  - "CDynamicParameterAccessor::SetParamLength"
  - "SetParamLength"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "SetParamLength 方法"
ms.assetid: d8e0bbfe-e1ae-4a8f-9567-584fbb0c8385
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# CDynamicParameterAccessor::SetParamLength
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

在缓冲存储区指定的参数的长度。  
  
## 语法  
  
```  
  
      bool SetParamLength(  
   DBORDINAL nParam,  
   DBLENGTH length  
);  
```  
  
#### 参数  
 `nParam`  
 \[in\] 参数数目 \(偏离 1\)。  参数 0 用于返回值保留的。  参数编号是基于其用 SQL 或存储过程调用的参数的索引。  用于示例参见 [SetParam](../../data/oledb/cdynamicparameteraccessor-setparam.md)。  
  
 *length*  
 \[in\] 长度中指定参数的字节。  
  
## 备注  
 在成功的返回 **true** 或 **false** 上失败。  
  
## 要求  
 **标头:** atldbcli.h  
  
## 请参阅  
 [CDynamicParameterAccessor 类](../../data/oledb/cdynamicparameteraccessor-class.md)