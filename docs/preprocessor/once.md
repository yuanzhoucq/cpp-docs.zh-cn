---
title: once 杂注
ms.date: 08/29/2019
f1_keywords:
- vc-pragma.once
- once_CPP
helpviewer_keywords:
- once pragma
- pragmas, once
ms.assetid: c7517556-6403-4b16-8898-f2aa0a6f685f
ms.openlocfilehash: 643ad83b672f7b632925383972751a966256eb41
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/03/2019
ms.locfileid: "70220536"
---
# <a name="once-pragma"></a>once 杂注

指定在编译源代码文件时编译器仅包含头文件一次。

## <a name="syntax"></a>语法

> **#pragma 一次**

## <a name="remarks"></a>备注

使用`#pragma once`可以减少生成时间, 因为编译器不会在翻译单元中的第一个`#include`文件之后打开并再次读取该文件。 这称为 "*多个包含优化*"。 它的作用类似于*include guard*方法, 该方法使用预处理器宏定义来防止多次包含文件内容。 它还有助于防止违反*单个定义规则*, 要求所有模板、类型、函数和对象在代码中都不能有多个定义。

例如:

```cpp
// header.h
#pragma once
// Code placed here is included only once per translation unit
```

建议对新代码使用 `#pragma once` 指令，因为它不会用预处理器符号污染全局命名空间。 它需要更少的键入, 减少了混乱程度, 并且不会导致*符号冲突*, 因此, 当不同的标头文件使用与临界值相同的预处理器符号时, 会导致错误。 它不是C++标准的一部分, 而是由多个常用编译器来实现移植。

在同一文件中同时使用 include 防护方法并`#pragma once`没有优势。 编译器可识别 include guard 方法, 并以与`#pragma once`指令相同的方式实现多重包含优化, 前提是在标准形式的方法之前或之后没有任何非注释代码或预处理器指令:

```cpp
// header.h
// Demonstration of the #include guard idiom.
// Note that the defined symbol can be arbitrary.
#ifndef HEADER_H_     // equivalently, #if !defined HEADER_H_
#define HEADER_H_
// Code placed here is included only once per translation unit
#endif // HEADER_H_
```

如果必须将代码移植到未实现`#pragma once`指令的编译器、保持与现有代码的一致性或无法进行多重包含优化, 则建议包含 guard。 如果文件系统别名或别名包含路径包含路径, 则可能会在复杂的项目中出现此问题。

请注意不要使用`#pragma once`或在设计为多次包含的标头文件中包含防护用法, 使用预处理器符号控制其效果。 有关此设计的示例, 请参阅\<assert > 头文件。 还要小心管理包含路径, 以避免创建到包含文件的多个路径, 这会使其中包含保护和`#pragma once`的多包含优化。

## <a name="see-also"></a>请参阅

[Pragma 指令和 __pragma 关键字](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
