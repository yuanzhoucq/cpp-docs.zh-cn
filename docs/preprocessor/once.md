---
title: once
ms.date: 11/04/2016
f1_keywords:
- vc-pragma.once
- once_CPP
helpviewer_keywords:
- once pragma
- pragmas, once
ms.assetid: c7517556-6403-4b16-8898-f2aa0a6f685f
ms.openlocfilehash: 6061fe77960aa64e2dcb39db05897ef0e7fb5f2e
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/18/2019
ms.locfileid: "59039869"
---
# <a name="once"></a>once
指定该文件在编译源代码文件时仅由编译器包含（打开）一次。

## <a name="syntax"></a>语法

```
#pragma once
```

## <a name="remarks"></a>备注

利用`#pragma once`可减少生成次数，因为编译器不将打开并读取该文件后第一个`#include`的翻译单元中的文件。 这被称为*多次包括优化*。 它具有类似的效果`#include guard`惯用语法，后者使用预处理器宏定义来避免多次包含文件的内容。 这也有助于防止违反*定义的一个规则*— 要求，所有模板、 类型、 函数和对象不能超过一个定义都具有你的代码。

例如：

```
// header.h
#pragma once
// Code placed here is included only once per translation unit
```

建议对新代码使用 `#pragma once` 指令，因为它不会用预处理器符号污染全局命名空间。 它需要的键入较少，因此不太会让人分心，并且不会导致符号冲突（不同的头文件使用相同的预处理器符号作为防护值时导致的错误）。 它不属于 C++ 标准，而是由几个常见的编译器移植实现。

在同一文件中同时使用 #include 防护惯用语法和 `#pragma once` 没有任何优势。 编译器会识别 #include 防护惯用语法，并在标准形式的惯用语法前后未出现任何非注释代码或预处理器指令时实现多次包括优化，实现方法与`#pragma once` 指令相同：

```
// header.h
// Demonstration of the #include guard idiom.
// Note that the defined symbol can be arbitrary.
#ifndef HEADER_H_     // equivalently, #if !defined HEADER_H_
#define HEADER_H_
// Code placed here is included only once per translation unit
#endif // HEADER_H_
```

我们建议`#include guard`惯用语法时代码必须是可移植到未实现的编译器`#pragma once`指令，以保持与现有代码的一致性时，或者当多次包括优化是不可能。 在复杂的项目中，当文件系统别名化或使用别名的包括路径使编译器无法按规范路径识别相同的包括文件时可能出现这种情况。

请注意，不要使用`#pragma once`或`#include guard`惯用语法设计为包含多个时间，使用预处理器符号来控制其效果的标头文件中。 这种设计的示例，请参阅\<assert.h > 标头文件。 此外，还要注意管理包括路径，以避免创建多个路径包含的文件，可以抵消多次包括优化`#include guard`s 和`#pragma once`。

## <a name="see-also"></a>请参阅

[Pragma 指令和 __Pragma 关键字](../preprocessor/pragma-directives-and-the-pragma-keyword.md)