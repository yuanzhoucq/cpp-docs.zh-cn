---
title: 编译器警告（等级 1）C4537
ms.date: 08/27/2018
f1_keywords:
- C4537
helpviewer_keywords:
- C4537
ms.assetid: 9454493c-d419-475e-8f35-9c00233c9329
ms.openlocfilehash: 81058f153228d3d8fbf4097c140962d0cb9677e5
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80186356"
---
# <a name="compiler-warning-level-1-c4537"></a>编译器警告（等级 1）C4537

> "*object*"： "*operator*" 应用于非 UDT 类型

## <a name="remarks"></a>备注

在需要对象（用户定义类型）的位置传递了引用。 引用不是对象，但内联汇编程序代码无法进行区分。 尽管*对象*是实例，但编译器会生成代码。

## <a name="example"></a>示例

下面的示例生成 C4537，并演示如何修复此问题：

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
