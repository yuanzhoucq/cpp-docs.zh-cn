---
title: "no_namespace | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "no_namespace"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "no_namespace 特性"
ms.assetid: 5d81b741-a558-451b-b493-1f3b18967337
caps.latest.revision: 4
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 4
---
# no_namespace
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**C\+\+ 专用**  
  
 指定命名空间的名称不由编译器生成。  
  
## 语法  
  
```  
no_namespace  
```  
  
## 备注  
 `#import` 标头文件中的类型库内容通常在命名空间中定义。  命名空间名称在原始 IDL 文件的 **library** 语句中指定。  如果指定了 `no_namespace` 特性，则编译器不生成此命名空间。  
  
 如果要使用不同的命名空间名称，请使用 [rename\_namespace](../preprocessor/rename-namespace.md) 特性。  
  
 **结束 C\+\+ 专用**  
  
## 请参阅  
 [\#import 特性](../preprocessor/hash-import-attributes-cpp.md)   
 [\#import 指令](../preprocessor/hash-import-directive-cpp.md)