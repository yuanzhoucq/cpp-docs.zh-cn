---
title: "CDynamicAccessor::SetBlobSizeLimit | Microsoft Docs"
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
  - "CDynamicAccessor::SetBlobSizeLimit"
  - "SetBlobSizeLimit"
  - "CDynamicAccessor.SetBlobSizeLimit"
  - "ATL.CDynamicAccessor.SetBlobSizeLimit"
  - "ATL::CDynamicAccessor::SetBlobSizeLimit"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "SetBlobSizeLimit 方法"
ms.assetid: fb8cb85d-f841-408e-a344-37895b10993f
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CDynamicAccessor::SetBlobSizeLimit
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

以字节 BLOB 设置最大大小。  
  
## 语法  
  
```  
  
      void SetBlobSizeLimit(  
   DBLENGTH nBlobSize   
);  
```  
  
#### 参数  
 `nBlobSize`  
 指定 BLOB 大小限制。  
  
## 备注  
 以字节设置最大大小 BLOB;数据列大于此值处理 BLOB。  某些提供程序使列中的大的范围 \(如 2 GB\)。  而不是尝试分配的内存范围，则此列通常会尝试将这些接口绑定列作为 blob。  在这样无需分配任何内存，但是，仍然可以读取所有数据，而不会害怕截断的遭到报复。  但是，您可能需要强制 `CDynamicAccessor` 绑定。这些本机数据类型的列大的情形。  为此，请在调用 **打开**之前调用 `SetBlobSizeLimit`。  
  
 构造函数方法 [CDynamicAccessor](../../data/oledb/cdynamicaccessor-class.md) 设置最大大小 BLOB 为默认值 8,000 字节。  
  
## 要求  
 **标头:** atldbcli.h  
  
## 请参阅  
 [CDynamicAccessor 类](../../data/oledb/cdynamicaccessor-class.md)