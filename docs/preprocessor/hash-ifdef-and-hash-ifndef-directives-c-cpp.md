---
title: '#ifdef 和 #ifndef 指令 （C/c + +）'
ms.date: 11/04/2016
f1_keywords:
- '#ifndef'
- '#ifdef'
helpviewer_keywords:
- '#ifdef directive'
- preprocessor, directives
- ifdef directive (#ifdef)
- ifndef directive (#ifndef)
- '#ifndef directive'
ms.assetid: 2b0be69d-9e72-45d8-8e24-e4130fb2455b
ms.openlocfilehash: 418b19e844d56fa2f33cf91a1b072e9add771eb2
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50643789"
---
# <a name="ifdef-and-ifndef-directives-cc"></a>#ifdef 和 #ifndef 指令 (C/C++)
**#Ifdef**并 **#ifndef**指令执行相同的任务`#if`指令与一起使用时**定义**(*标识符* ).

## <a name="syntax"></a>语法

```
#ifdef identifier
#ifndef identifier

// equivalent to
#if defined identifier
#if !defined identifier
```

## <a name="remarks"></a>备注

可以使用 **#ifdef**并 **#ifndef**指令`#if`可用。 **#Ifdef** *标识符*语句等效于`#if 1`时*标识符*已经定义，并且等效于`#if 0`时*标识符*未定义或定义与`#undef`指令。 这些指令只检查使用 `#define` 定义的标识符是否存在，而不检查在 C 或 C++ 源代码中声明的标识符。

提供这些指令只是为了实现与该语言的早期版本的兼容性。 **定义 (** *标识符* **)** 与一起使用的常量表达式`#if`指令是首选。

**#Ifndef**指令检查的相反值检查的条件 **#ifdef**。 如果尚未定义标识符（或已使用 `#undef` 移除其定义），则条件为 true（非零）。 否则，条件为 false (0)。

**Microsoft 专用**

*标识符*可以从命令行使用传递`/D`选项。 可以使用指定最多 30 个宏`/D`。

这对于检查定义是否存在很有用，因为可以从命令行中传递定义。 例如：

```cpp
// ifdef_ifndef.CPP
// compile with: /Dtest /c
#ifndef test
#define final
#endif
```

**结束 Microsoft 专用**

## <a name="see-also"></a>请参阅

[预处理器指令](../preprocessor/preprocessor-directives.md)