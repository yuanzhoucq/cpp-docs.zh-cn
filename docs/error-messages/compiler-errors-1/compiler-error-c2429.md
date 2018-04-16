---
title: "编译器错误 C2429 |Microsoft 文档"
ms.custom: 
ms.date: 11/16/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2429
dev_langs:
- C++
helpviewer_keywords:
- C2429
ms.assetid: 57ff6df9-5cf1-49f3-8bd8-4e550dfd65a0
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 6882804d1ddf2e4f83947e310cde4c8c114120d1
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
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
