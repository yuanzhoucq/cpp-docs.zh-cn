---
title: 编译器警告 （等级 C4457 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4457
dev_langs:
- C++
helpviewer_keywords:
- C4457
ms.assetid: 02fd149a-917d-4f67-97a6-eb714572271f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 62232a814bed47f8b6a5041d20e6f37776abffe8
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46093527"
---
# <a name="compiler-warning-level-4-c4457"></a>编译器警告 （等级 C4457

> 声明*标识符*隐藏了函数参数

声明*标识符*本地作用域中隐藏了名称同为函数参数的声明。 此警告，可以了解到引用*标识符*局部范围内解析为本地声明的版本中，不使用参数可能会也可能不是你的意图。 若要解决此问题，我们建议为指定的参数名不冲突的本地变量名称。

## <a name="example"></a>示例

下面的示例生成 C4457，因为参数`x`和局部变量`x`中`member_fn`具有相同的名称。 若要解决此问题，请使用不同的参数和局部变量的名称。

```cpp
// C4457_hide.cpp
// compile with: cl /W4 /c C4457_hide.cpp

struct S {
    void member_fn(unsigned x) {
        double a = 0;
        for (int x = 0; x < 10; ++x) {  // C4457
            a += x; // uses local x
        }
        a += x; // uses parameter x
    }
} s;
```
