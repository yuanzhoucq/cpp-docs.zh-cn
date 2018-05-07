---
title: 编译器错误 C2429 |Microsoft 文档
ms.custom: ''
ms.date: 11/16/2017
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2429
dev_langs:
- C++
helpviewer_keywords:
- C2429
ms.assetid: 57ff6df9-5cf1-49f3-8bd8-4e550dfd65a0
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 032df433b28e83f720fe76952a541b59bda889f5
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c2429"></a>编译器错误 C2429

> *语言功能*要求编译器标志*编译器选项*

语言功能要求特定的编译器选项来支持。

错误**C2429： 语言功能嵌套的命名空间的定义要求编译器标志 / std:c + + 17**如果在尝试定义生成*复合命名空间*，一个包含一个或多个命名空间作用域嵌套命名空间名称，从 Visual Studio 2015 更新 5 开始。 (在 Visual Studio 2017 版本 15.3， **/std:c + + 最新**交换机是必需的。)复合不允许定义在 c + + 在 C + + 17 之前的命名空间。 编译器支持复合命名空间定义时[/std:c + + 17](../../build/reference/std-specify-language-standard-version.md)指定编译器选项：

```cpp
// C2429a.cpp
namespace a::b { int i; } // C2429 starting in Visual C++ 2015 Update 3.
                          // Use /std:c++17 to fix, or do this:
// namespace a { namespace b { int i; }}

int main() {
   a::b::i = 2;
}
```
