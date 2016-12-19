---
title: "CDynamicAccessor::CDynamicAccessor | Microsoft Docs"
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
  - "CDynamicAccessor::CDynamicAccessor"
  - "ATL::CDynamicAccessor::CDynamicAccessor"
  - "ATL.CDynamicAccessor.CDynamicAccessor"
  - "CDynamicAccessor.CDynamicAccessor"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CDynamicAccessor 类, 构造函数"
ms.assetid: bf40fe81-2c85-473e-9075-51ad9b060b39
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CDynamicAccessor::CDynamicAccessor
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

实例化和初始化 `CDynamicAccessor` 对象。  
  
## 语法  
  
```  
  
      CDynamicAccessor(   
   DBBLOBHANDLINGENUM eBlobHandling = DBBLOBHANDLING_DEFAULT,   
   DBLENGTH nBlobSize = 8000   
);  
```  
  
#### 参数  
 `eBlobHandling`  
 指定二进制大对象 \(BLOB\) \(BLOB\) 数据进行处理。  默认值为 **DBBLOBHANDLING\_DEFAULT**。  为 **DBBLOBHANDLINGENUM** 值的说明参见 [SetBlobHandling](../../data/oledb/cdynamicaccessor-setblobhandling.md)。  
  
 `nBlobSize`  
 最大大小 BLOB 在字节；内处理 BLOB 数据值的列。  默认值为 8,000。  参见 [SetBlobSizeLimit](../../data/oledb/cdynamicaccessor-setblobsizelimit.md)。有关详细信息。  
  
## 备注  
 如果使用构造函数初始化 `CDynamicAccessor` 对象，可以指定如何将它绑定 blob。  Blob 还可包含二进制数据，如图形大相同或编译的代码。  默认行为是将列超过 8,000 字节作为 Blob 尝试将其绑定到 `ISequentialStream` 对象。  但是，可以指定其他值是 BLOB 大小。  
  
 也可以指定限定为 `CDynamicAccessor` 处理 BLOB 数据的列数据：它可以处理 BLOB 数据的默认方式；它可以跳过 \(不 BLOB 数据；绑定\) 也可以将提供程序分配内存的 BLOB 数据。  
  
## 要求  
 **标头:** atldbcli.h  
  
## 请参阅  
 [CDynamicAccessor 类](../../data/oledb/cdynamicaccessor-class.md)