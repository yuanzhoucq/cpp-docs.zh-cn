---
title: 编译器警告 （等级 C4458 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4458
dev_langs:
- C++
helpviewer_keywords:
- C4458
ms.assetid: 7bdaa1b1-0caf-4d68-98c4-6bdd441c23fb
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 873aa94db899ae6620e2bbb1f24277c6e7c841c4
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46094541"
---
# <a name="compiler-warning-level-4-c4458"></a>编译器警告 （等级 C4458

> 声明*标识符*隐藏了类成员

声明*标识符*在本地作用域中隐藏了相同名称的声明*标识符*在类范围内。 此警告，可以了解到引用*标识符*在此范围内解析为本地声明的版本中，不是类成员版本，可能会也可能不是你的意图。 若要解决此问题，我们建议为指定类成员名称不冲突的本地变量名称。

## <a name="example"></a>示例

下面的示例生成 C4458，因为参数`x`和局部变量`y`中`member_fn`类中具有相同的数据成员名称。 若要解决此问题，请使用不同的参数和局部变量的名称。

```cpp
// C4458_hide.cpp
// compile with: cl /W4 /c C4458_hide.cpp

struct S {
    int x;
    float y;
    void member_fn(long x) {   // C4458
        double y;  // C4458
        y = x;
        // To fix this issue, change the parameter name x
        // and local name y to something that does not
        // conflict with the data member names.
    }
} s;
```
