---
title: "CDynamicAccessor::SetBlobHandling | Microsoft Docs"
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
  - "CDynamicAccessor::SetBlobHandling"
  - "CDynamicAccessor.SetBlobHandling"
  - "ATL::CDynamicAccessor::SetBlobHandling"
  - "SetBlobHandling"
  - "ATL.CDynamicAccessor.SetBlobHandling"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "SetBlobHandling 方法"
ms.assetid: fa8b0bb3-a21b-4d64-aeef-e79bf61d079c
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CDynamicAccessor::SetBlobHandling
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

处理 BLOB 设置当前行的值。  
  
## 语法  
  
```  
  
      bool SetBlobHandling(  
   DBBLOBHANDLINGENUM eBlobHandling   
);  
```  
  
#### 参数  
 `eBlobHandling`  
 指定如何将处理 BLOB 数据。  可以采用下列值：  
  
-   **DBBLOBHANDLING\_DEFAULT**:大于 `nBlobSize` 处理列数据 \(将 `SetBlobSizeLimit`\) 作为 BLOB 数据并通过 `ISequentialStream` 或 `IStream` 对象中检索它。  此选项大于 `nBlobSize` 将尝试将包含数据的每列或一列出。**DBTYPE\_IUNKNOWN** 作为 BLOB 数据。  
  
-   **DBBLOBHANDLING\_NOSTREAMS**:大于 `nBlobSize` 处理列数据 \(将 `SetBlobSizeLimit`\) 作为 BLOB 数据并在提供程序自己的内存分配中，使用者的引用中检索它。  此选项对于多个 BLOB 列的表很有用，并且，提供程序只支持每个访问器添加一个 `ISequentialStream` 对象。  
  
-   **DBBLOBHANDLING\_SKIP**:跳过 \(不绑定\) 限定为包含的列 Blob \(访问器不会绑定也不检索列值，但将检索列的状态和长度\)。  
  
## 备注  
 应在调用 **打开**之前调用 `SetBlobHandling`。  
  
 构造函数方法 [CDynamicAccessor](../../data/oledb/cdynamicaccessor-class.md) 设置处理 BLOB 的值为 **DBBLOBHANDLING\_DEFAULT**。  
  
## 要求  
 **标头:** atldbcli.h  
  
## 请参阅  
 [CDynamicAccessor 类](../../data/oledb/cdynamicaccessor-class.md)