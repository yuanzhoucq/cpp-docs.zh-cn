---
title: 编译器警告（等级 1）C4537
ms.date: 08/27/2018
f1_keywords:
- C4537
helpviewer_keywords:
- C4537
ms.assetid: 9454493c-d419-475e-8f35-9c00233c9329
ms.openlocfilehash: 2f97be4e1aaa5143df685cb95935d350e6f02534
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50441309"
---
# <a name="compiler-warning-level-1-c4537"></a>编译器警告（等级 1）C4537

> '*对象*':'*运算符*应用于非 UDT 类型

## <a name="remarks"></a>备注

已传递的引用，需要的对象 （用户定义类型） 的位置。 引用不是一个对象，但内联汇编程序代码不能使这种差异。 编译器生成的代码，如同*对象*是实例一样。

## <a name="example"></a>示例

下面的示例生成 C4537 并演示如何修复此错误：

```cpp
// C4537.cpp
// compile with: /W1 /c
// processor: x86
struct S {
    int member;
};

void f1(S &s) {
    __asm mov eax, s.member;   // C4537
    // try the following code instead
    // or, make the declaration "void f1(S s)"
    /*
    mov eax, s
    mov eax, [eax]s.member
    */
}
```