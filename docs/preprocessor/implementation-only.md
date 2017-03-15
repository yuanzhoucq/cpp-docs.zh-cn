---
title: "implementation_only | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "implementation_only"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "implementation_only 特性"
ms.assetid: d8cabc86-4425-45a0-9587-d57536980088
caps.latest.revision: 4
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 4
---
# implementation_only
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**C\+\+ 专用**  
  
 取消生成 .tlh 头文件（主要头文件）。  
  
## 语法  
  
```  
implementation_only  
```  
  
## 备注  
 此文件包含用于公开类型库内容的所有声明。  具有包装器成员函数的实现的 .tli 头文件将会生成并包含在编译中。  
  
 指定此特性后，.tli 标头的内容将位于通常在 .tlh 标头中使用的同一命名空间中。  此外，成员函数未声明为内联。  
  
 `implementation_only` 特性专门与 [no\_implementation](../preprocessor/no-implementation.md) 特性结合使用以作为将实现保持在预编译的头 \(PCH\) 文件外部的方式。  将在用于创建 PCH 的源区域中放置具有 `no_implementation` 特性的 `#import` 语句。  生成的 PCH 由很多源文件使用。  之后将在 PCH 区域外使用具有 `implementation_only` 特性的 `#import` 语句。  您需要在源文件之一中仅使用此语句一次。  这将生成所有必需的包装器成员函数，而不会额外重新编译每个源文件。  
  
> [!NOTE]
>  一个 `#import` 语句中的 `implementation_only` 特性必须与同一类型库的具有 `no_implementation` 特性的另一个 `#import` 语句结合使用。  否则，将生成编译器错误。  这是因为编译 `implementation_only` 特性生成的实现需要具有 `no_implementation` 特性的 `#import` 语句生成的包装器类定义。  
  
 **结束 C\+\+ 专用**  
  
## 请参阅  
 [\#import 特性](../preprocessor/hash-import-attributes-cpp.md)   
 [\#import 指令](../preprocessor/hash-import-directive-cpp.md)