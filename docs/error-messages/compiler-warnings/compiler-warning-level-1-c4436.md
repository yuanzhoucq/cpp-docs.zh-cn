---
title: 编译器警告（等级 1）C4436
ms.date: 11/04/2016
f1_keywords:
- C4436
helpviewer_keywords:
- C4436
ms.assetid: 2b54a1fc-c9c6-4cc9-90be-faa44fc715d5
ms.openlocfilehash: 6a15220cb02a48fb11936b69e5830412f1221108
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87230670"
---
# <a name="compiler-warning-level-1-c4436"></a>编译器警告（等级 1）C4436

构造函数或析构函数中从虚拟基“class1”到“class2”的 dynamic_cast 对于部分构造的对象可能会失败。使用 /vd2 编译或使用生效的 #pragma vtordisp(2) 定义“class2”

编译器遇到 **`dynamic_cast`** 具有以下特征的操作。

- 转换是从基类指针到派生类的指针。

- 派生类虚拟继承基类。

- 派生类没有虚拟基的 `vtordisp` 字段。

- 在派生类或进一步继承派生类的一些类的构造函数或析构函数中发现转换。

**`dynamic_cast`** 如果在部分构造的对象上操作，则该警告指示可能未正确执行。  如果派生的构造函数/析构函数在某些进一步派生对象的子对象上操作时，可能会发生该情况。  如果警告中指定的派生类不再进一步派生，可以忽略警告。

## <a name="example"></a>示例

下面的示例生成 C4436 并演示缺少 `vtordisp` 字段所引发的代码生成问题。

```cpp
// C4436.cpp
// To see the warning and runtime assert, compile with: /W1
// To eliminate the warning and assert, compile with: /W1 /vd2
//       or compile with: /W1 /DFIX
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
        A* a = static_cast<A*>(this);
        B* b = dynamic_cast<B*>(a);     // C4436
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

## <a name="see-also"></a>另请参阅

[dynamic_cast 运算符](../../cpp/dynamic-cast-operator.md)<br/>
[vtordisp](../../preprocessor/vtordisp.md)<br/>
[编译器警告（等级4） C4437](../../error-messages/compiler-warnings/compiler-warning-level-4-c4437.md)
