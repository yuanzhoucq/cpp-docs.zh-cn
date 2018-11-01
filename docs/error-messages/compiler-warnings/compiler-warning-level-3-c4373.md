---
title: 编译器警告（等级 3）C4373
ms.date: 11/04/2016
f1_keywords:
- C4373
helpviewer_keywords:
- C4373
ms.assetid: 670c0ba3-b7d6-4aed-b207-1cb84da3bcde
ms.openlocfilehash: 031b32a03d93a51f6fa00041a5b0bdf99e6eacf1
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50456051"
---
# <a name="compiler-warning-level-3-c4373"></a>编译器警告（等级 3）C4373

> '*函数*： 虚函数重写*base_function*上, 一版本的编译器未进行重写时参数只上有差异 const/volatile 限定符

## <a name="remarks"></a>备注

应用程序在派生类中包含一个方法，可重写基类中的虚拟方法，在重写方法中的参数中，只有 [const](../../cpp/const-cpp.md) 或 [volatile](../../cpp/volatile-cpp.md) 限定符与虚拟方法中的参数不同。 这就意味着编译器必须将函数引用绑定到基类或派生类中的方法。

版本在 Visual Studio 2008 之前的编译器将函数绑定到基类中的方法，然后发出一条警告消息。 后续版本的编译器忽略`const`或`volatile`限定符，将函数绑定到该方法在派生类中，然后发出警告**C4373**。 后一种行为符合 C++ 标准。

## <a name="example"></a>示例

下面的代码示例将生成警告 C4373。 若要解决此问题，您可以将其设为基的成员函数中，使用相同的 CV 限定符的重写或如果您不打算创建替代，你可以为派生类中的函数指定其他名称。

```cpp
// c4373.cpp
// compile with: /c /W3
#include <stdio.h>
struct Base
{
    virtual void f(int i) {
        printf("base\n");
    }
};

struct Derived : Base
{
    void f(const int i) {  // C4373
        printf("derived\n");
    }
};

void main()
{
    Derived d;
    Base* p = &d;
    p->f(1);
}
```

```Output
derived
```