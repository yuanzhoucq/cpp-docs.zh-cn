---
title: "raw_native_types | Microsoft Docs"
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
  - "raw_native_types"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "raw_native_types 特性"
ms.assetid: 9f38daa8-8dc0-46a5-aff9-f1ff9c1e6f48
caps.latest.revision: 5
caps.handback.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# raw_native_types
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**C\+\+ 专用**  
  
 禁止在高级包装器函数中使用 COM 支持类，并强制改用低级数据类型。  
  
## 语法  
  
```  
raw_native_types  
```  
  
## 备注  
 默认情况下，高级错误处理方法使用 COM 支持类 [\_bstr\_t](../cpp/bstr-t-class.md) 和 [\_variant\_t](../cpp/variant-t-class.md) 代替 `BSTR` 和 **VARIANT** 数据类型和原始 COM 接口指针。  这些类封装了为这些数据类型分配和解除分配内存存储的详细信息，并大大简化了类型强制转换和转换操作。  
  
 **结束 C\+\+ 专用**  
  
## 请参阅  
 [\#import 特性](../preprocessor/hash-import-attributes-cpp.md)   
 [\#import 指令](../preprocessor/hash-import-directive-cpp.md)