---
title: "#ifdef 和 #ifndef 指令 (C/C++) | Microsoft Docs"
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
  - "#ifndef"
  - "#ifdef"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "#ifdef 指令"
  - "#ifndef 指令"
  - "ifdef 指令 (#ifdef)"
  - "ifndef 指令 (#ifndef)"
  - "预处理器, 指令"
ms.assetid: 2b0be69d-9e72-45d8-8e24-e4130fb2455b
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# #ifdef 和 #ifndef 指令 (C/C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

在将 **\#ifdef** 和 **\#ifndef** 指令与 **defined**\(*identifier*\) 一起使用时，它将执行与 `#if` 指令相同的任务。  
  
## 语法  
  
```  
#ifdef identifier  
#ifndef identifier  
  
// equivalent to  
#if defined identifier  
#if !defined identifier  
```  
  
## 备注  
 只要能够使用 `#if`，就可以使用 **\#ifdef** 和 **\#ifndef** 指令。  在定义 *identifier* 时，**\#ifdef** *identifier* 语句与  `#if 1`  等效；当 *identifier* 未定义或没有使用 `#undef` 指令进行定义时，该语句与  `#if 0`  等效。  这些指令只检查使用 `#define` 定义的标识符是否存在，而不检查在 C 或 C\+\+ 源代码中声明的标识符。  
  
 提供这些指令只是为了实现与该语言的早期版本的兼容性。  优先选择将 **defined\(** *identifier* **\)** 常量表达式与 `#if` 指令一起使用。  
  
 **\#ifndef** 指令检查 **\#ifdef** 所检查的条件的相反值。  如果尚未定义标识符（或已使用 `#undef` 移除其定义），则条件为 true（非零）。  否则，条件为 false \(0\)。  
  
 **Microsoft 专用**  
  
 可使用 \/D 选项从命令行中传递 *identifier*。  可使用 \/D 指定最多 30 个宏。  
  
 这对于检查定义是否存在很有用，因为可以从命令行中传递定义。  例如：  
  
```  
// ifdef_ifndef.CPP  
// compile with: /Dtest /c  
#ifndef test  
#define final  
#endif  
```  
  
 **结束 Microsoft 专用**  
  
## 请参阅  
 [预处理器指令](../preprocessor/preprocessor-directives.md)