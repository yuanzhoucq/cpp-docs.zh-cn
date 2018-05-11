---
title: '#ifdef 和 #ifndef 指令 （C/c + +） |Microsoft 文档'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- '#ifndef'
- '#ifdef'
dev_langs:
- C++
helpviewer_keywords:
- '#ifdef directive'
- preprocessor, directives
- ifdef directive (#ifdef)
- ifndef directive (#ifndef)
- '#ifndef directive'
ms.assetid: 2b0be69d-9e72-45d8-8e24-e4130fb2455b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9a5ecfc9cc63fc4028e1f93d8f30e8d5cb9f9357
ms.sourcegitcommit: 96cdc2da0d8c3783cc2ce03bd280a5430e1ac01d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/10/2018
---
# <a name="ifdef-and-ifndef-directives-cc"></a>#ifdef 和 #ifndef 指令 (C/C++)
**#Ifdef**和 **#ifndef**指令执行相同的任务`#if`指令在使用它的**定义**(*标识符* ).  
  
## <a name="syntax"></a>语法  
  
```  
#ifdef identifier  
#ifndef identifier  
  
// equivalent to  
#if defined identifier  
#if !defined identifier  
```  
  
## <a name="remarks"></a>备注  
 你可以使用 **#ifdef**和 **#ifndef**指令任意位置`#if`可用。 **#Ifdef** *标识符*语句是等效于`#if 1`时*标识符*已经定义，并且等效于`#if 0`时*标识符*未定义或已定义与`#undef`指令。 这些指令只检查使用 `#define` 定义的标识符是否存在，而不检查在 C 或 C++ 源代码中声明的标识符。  
  
 提供这些指令只是为了实现与该语言的早期版本的兼容性。 **定义 (** *标识符* **)** 与一起使用的常量表达式`#if`指令是首选。  
  
 **#Ifndef**指令检查检查的条件的相反 **#ifdef**。 如果尚未定义标识符（或已使用 `#undef` 移除其定义），则条件为 true（非零）。 否则，条件为 false (0)。  
  
 **Microsoft 专用**  
  
 *标识符*可以从命令行使用 /D 选项中传递。 可使用 /D 指定最多 30 个宏。  
  
 这对于检查定义是否存在很有用，因为可以从命令行中传递定义。 例如：  
  
```  
// ifdef_ifndef.CPP  
// compile with: /Dtest /c  
#ifndef test  
#define final  
#endif  
```  
  
 **结束 Microsoft 专用**  
  
## <a name="see-also"></a>请参阅  
 [预处理器指令](../preprocessor/preprocessor-directives.md)