---
title: 编译器警告 （等级 C4456
ms.date: 11/04/2016
f1_keywords:
- C4456
helpviewer_keywords:
- C4456
ms.assetid: 5ab39fc1-0e19-461b-842b-4da80560b044
ms.openlocfilehash: 006628721598d838070412c895f64b9a8d3de4e9
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62391499"
---
# <a name="compiler-warning-level-4-c4456"></a>编译器警告 （等级 C4456

> 声明*标识符*隐藏上一个本地声明

声明*标识符*本地作用域中隐藏具有相同名称的上一个本地声明的声明。 此警告，可以了解到引用*标识符*局部范围内解析为本地声明的版本中，不在上一本地，可能会也可能不是你的意图。 若要解决此问题，我们建议你为提供与其他本地名称不冲突的本地变量名称。

## <a name="example"></a>示例

下面的示例生成 C4456，因为循环控制变量`int x`和局部变量`double x`中`member_fn`具有相同的名称。 若要解决此问题，请使用不同的本地变量的名称。

```cpp
// C4456_hide.cpp
// compile with: cl /W4 /c C4456_hide.cpp

struct S {
    void member_fn(unsigned u) {
        double x = 0;
        for (int x = 0; x < 10; ++x) {  // C4456
            u += x; // uses local int x
        }
        x += u; // uses local double x
    }
} s;
```
