---
title: "raw_method_prefix | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "raw_method_prefix"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "raw_method_prefix 特性"
ms.assetid: 71490313-af78-4bb2-b28a-eee67950d30b
caps.latest.revision: 4
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 4
---
# raw_method_prefix
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**C\+\+ 专用**  
  
 指定不同的前缀以避免名称冲突。  
  
## 语法  
  
```  
raw_method_prefix("Prefix")  
```  
  
#### 参数  
 `Prefix`  
 要使用的前缀。  
  
## 备注  
 低级属性和方法由使用默认前缀 **raw\_** 命名的成员函数公开，以避免与高级错误处理成员函数发生名称冲突。  
  
> [!NOTE]
>  [raw\_interfaces\_only](#_predir_raw_interfaces_only) 特性是否存在不会改变 `raw_method_prefix` 特性的效果。  指定前缀时，`raw_method_prefix` 始终优先于 `raw_interfaces_only`。  如果同一 `#import` 语句中同时使用了这两个特性，则使用 `raw_method_prefix` 特性指定的前缀。  
  
 **结束 C\+\+ 专用**  
  
## 请参阅  
 [\#import 特性](../preprocessor/hash-import-attributes-cpp.md)   
 [\#import 指令](../preprocessor/hash-import-directive-cpp.md)