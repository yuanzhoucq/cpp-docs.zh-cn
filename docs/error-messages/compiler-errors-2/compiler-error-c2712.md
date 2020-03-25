---
title: 编译器错误 C2712
ms.date: 11/04/2016
f1_keywords:
- C2712
helpviewer_keywords:
- C2712
ms.assetid: f7d4ffcc-7ed2-459b-8067-a728ce647071
ms.openlocfilehash: a25c59fa5c9ba0102666f6c8922a61b063e7627a
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80202301"
---
# <a name="compiler-error-c2712"></a>编译器错误 C2712

> 无法在要求对象展开的函数中使用 __try

## <a name="remarks"></a>备注

如果你使用[/ehsc](../../build/reference/eh-exception-handling-model.md)，并且具有结构化异常处理的函数也具有需要展开（析构）的对象，则会发生错误 C2712。

可能的解决方法：

- 将要求 SEH 的代码移动到另一个函数中

- 重写使用 SEH 的函数以避免使用具有析构函数的局部变量和参数。 在构造函数或析构函数中不要使用 SEH

- 不使用 /EHsc 进行编译

如果调用使用[__event](../../cpp/event.md)关键字声明的方法，也会发生错误 C2712。 由于可以在多线程环境中使用该事件，因此编译器将生成代码来阻止对基础事件对象的操作，然后将生成的代码封装在 SEH [try finally 语句](../../cpp/try-finally-statement.md)中。 因此，如果调用事件方法并按值传递其类型具有析构函数的自变量，则将发生错误 C2712。 这种情况的一种解决方法是将参数作为常数引用进行传递。

如果使用 **/clr： pure**进行编译，并在 `__try` 块中声明指向函数的指针的静态数组，则也会发生 C2712。 静态成员要求编译器使用 **/clr： pure**下的动态初始化，这会C++引发异常处理。 但是，不允许在 `__try` 块中进行 C++ 异常处理。

**/Clr： pure**和 **/clr： safe**编译器选项在 visual studio 2015 中已弃用，在 visual studio 2017 中不受支持。

## <a name="example"></a>示例

下面的示例生成 C2712，并演示如何修复此错误。

```cpp
// C2712.cpp
// compile with: /clr:pure /c
struct S1 {
   static int smf();
   void fnc();
};

void S1::fnc() {
   __try {
      static int (*array_1[])() = {smf,};   // C2712

      // OK
      static int (*array_2[2])();
      array_2[0] = smf;
    }
    __except(0) {}
}
```
