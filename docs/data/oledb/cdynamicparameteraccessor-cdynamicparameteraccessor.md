---
title: "CDynamicParameterAccessor::CDynamicParameterAccessor | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CDynamicParameterAccessor::CDynamicParameterAccessor"
  - "CDynamicParameterAccessor.CDynamicParameterAccessor"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CDynamicParameterAccessor 类, 构造函数"
  - "CDynamicParameterAccessor 方法"
ms.assetid: a1cce5e4-dfb9-43a2-bfb8-0435c653674a
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# CDynamicParameterAccessor::CDynamicParameterAccessor
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

构造函数。  
  
## 语法  
  
```  
  
      typedef CDynamicParameterAccessor _ParamClass;  
CDynamicParameterAccessor(   
   DBBLOBHANDLINGENUM eBlobHandling = DBBLOBHANDLING_DEFAULT,   
   DBLENGTH nBlobSize = 8000 )   
   : CDynamicAccessor( eBlobHandling, nBlobSize )  
```  
  
#### 参数  
 `eBlobHandling`  
 指定如何将处理 BLOB 数据。  默认值为 **DBBLOBHANDLING\_DEFAULT**。  为 **DBBLOBHANDLINGENUM** 值的说明参见 [CDynamicAccessor::SetBlobHandling](../../data/oledb/cdynamicaccessor-setblobhandling.md)。  
  
 `nBlobSize`  
 最大大小 BLOB 在字节；内处理 BLOB 数据值的列。  默认值为 8,000。  参见 [CDynamicAccessor::SetBlobSizeLimit](../../data/oledb/cdynamicaccessor-setblobsizelimit.md)。有关详细信息。  
  
## 备注  
 参见 [CDynamicAccessor::CDynamicAccessor](../../data/oledb/cdynamicaccessor-cdynamicaccessor.md) 构造有关处理 BLOB 函数的更多信息。  
  
## 要求  
 **标头:** atldbcli.h  
  
## 请参阅  
 [CDynamicParameterAccessor 类](../../data/oledb/cdynamicparameteraccessor-class.md)