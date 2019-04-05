---
title: 编译器警告（等级 4）C4437
ms.date: 11/04/2016
ms.assetid: dc07e350-20eb-474c-a7ad-f841ae7ec339
ms.openlocfilehash: 9ff52ae6d10f7d4ba429bbf3457a2a6b969998d4
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/05/2019
ms.locfileid: "59037813"
---
# <a name="compiler-warning-level-4-c4437"></a>编译器警告（等级 4）C4437

从虚拟基 class1 到 class2 的 dynamic_cast 可能失败，在某些上下文中编译使用/vd2 或有效定义 class2 与 #pragma vtordisp （2）

默认情况下，此警告处于关闭状态。 请参阅 [默认情况下处于关闭状态的编译器警告](../../preprocessor/compiler-warnings-that-are-off-by-default.md) 了解详细信息。

编译器遇到具有以下特征的 `dynamic_cast` 操作。

- 转换是从基类指针到派生类的指针。

- 派生类虚拟继承基类。

- 派生类没有虚拟基的 `vtordisp` 字段。

- 构造函数或派生类的析构函数中找不到该强制转换或某些类进一步继承派生类 （否则为编译器警告将颁发 C4436）。

警告指示`dynamic_cast`可能无法正确执行在部分构造的对象上操作时。  从构造函数或析构函数的类的继承警告中指定的派生的类调用将封闭函数时，将出现这种情况。  如果警告中指定的派生的类不再进一步派生，或将封闭函数不调用对象构造或析构期间，可以忽略此警告。

## <a name="example"></a>示例

以下示例生成 C4437 并演示缺少的代码生成问题`vtordisp`字段。

```cpp
// C4437.cpp
// To see the warning and runtime assert, compile with: /W4
// To eliminate the warning and assert, compile with: /W4 /vd2
//       or compile with: /W4 /DFIX
#pragma warning(default : 4437)
#include <cassert>

struct A
{
public:
    virtual ~A() {}
};

#if defined(FIX)
#pragma vtordisp(push, 2)
#endif
struct B : virtual A
{
    B()
    {
        func();
    }

    void func()
    {
        A* a = static_cast<A*>(this);
        B* b = dynamic_cast<B*>(a);     // C4437
        assert(this == b);              // assert unless compiled with /vd2
    }
};
#if defined(FIX)
#pragma vtordisp(pop)
#endif

struct C : B
{
    int i;
};

int main()
{
    C c;
}
```

## <a name="see-also"></a>请参阅

[dynamic_cast 运算符](../../cpp/dynamic-cast-operator.md)<br/>
[vtordisp](../../preprocessor/vtordisp.md)<br/>
[编译器警告（等级 1）C4436](../../error-messages/compiler-warnings/compiler-warning-level-1-c4436.md)