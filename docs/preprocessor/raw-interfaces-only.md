---
title: "raw_interfaces_only | Microsoft Docs"
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
  - "raw_interfaces_only"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "raw_interfaces_only 特性"
ms.assetid: 87056c6d-3f34-4248-af58-f5775a35bfb7
caps.latest.revision: 5
caps.handback.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# raw_interfaces_only
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**C\+\+ 专用**  
  
 取消错误处理的包装器函数的生成以及使用那些包装器函数的 [属性](../cpp/property-cpp.md) 声明。  
  
## 语法  
  
```  
raw_interfaces_only  
```  
  
## 备注  
 `raw_interfaces_only` 特性还会导致移除在命名非属性函数时使用的默认前缀。  通常，该前缀是 **raw\_**。  如果指定了此特性，函数名将直接来自类型库。  
  
 利用此特性，您可以只公开类型库的低级别内容。  
  
 **结束 C\+\+ 专用**  
  
## 请参阅  
 [\#import 特性](../preprocessor/hash-import-attributes-cpp.md)   
 [\#import 指令](../preprocessor/hash-import-directive-cpp.md)