---
title: static_cast 运算符
ms.date: 11/04/2016
f1_keywords:
- static_cast_cpp
helpviewer_keywords:
- static_cast keyword [C++]
ms.assetid: 1f7c0c1c-b288-476c-89d6-0e2ceda5c293
ms.openlocfilehash: 8551d41417647ee4f759e2547e2c1909c59d78cd
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87213198"
---
# <a name="static_cast-operator"></a>static_cast 运算符

仅基于表达式中存在的类型将*表达式*转换为*类型 id*的类型。

## <a name="syntax"></a>语法

```
static_cast <type-id> ( expression )
```

## <a name="remarks"></a>备注

在标准 C++ 中，不进行运行时类型检查来帮助确保转换的安全。 在 C++/CX 中，将执行编译时和运行时检查。 有关更多信息，请参见 [强制转换](casting.md)中定义的接口的私有 C++ 特定实现。

**`static_cast`** 运算符可用于将指向基类的指针转换为指向派生类的指针等操作。 此类转换并非始终安全。

一般情况下， **`static_cast`** 当你想要将数值数据类型（如枚举）转换为整数或整数，并确定转换中涉及的数据类型时，请使用。 **`static_cast`** 转换不像转换那样安全 **`dynamic_cast`** ，因为在执行时不 **`static_cast`** 会进行任何运行时类型检查 **`dynamic_cast`** 。 对于 **`dynamic_cast`** 不明确的指针，将会失败，而返回的内容将会失败 **`static_cast`** ; 这可能是危险的。 虽然 **`dynamic_cast`** 转换更安全，但 **`dynamic_cast`** 仅适用于指针或引用，并且运行时类型检查是一项开销。 有关详细信息，请参阅[Dynamic_cast 运算符](../cpp/dynamic-cast-operator.md)。

在下面的示例中，因为 `D* pd2 = static_cast<D*>(pb);` 可能有不在 `D` 内的字段和方法，所以行 `B` 不安全。 但是，因为 `B* pb2 = static_cast<B*>(pd);` 始终包含所有 `D`，所以行 `B` 是安全的转换。

```cpp
// static_cast_Operator.cpp
// compile with: /LD
class B {};

class D : public B {};

void f(B* pb, D* pd) {
   D* pd2 = static_cast<D*>(pb);   // Not safe, D can have fields
                                   // and methods that are not in B.

   B* pb2 = static_cast<B*>(pd);   // Safe conversion, D always
                                   // contains all of B.
}
```

与[dynamic_cast](../cpp/dynamic-cast-operator.md)相比，不会对的转换进行运行时检查 **`static_cast`** `pb` 。 由 `pb` 指向的对象可能不是 `D` 类型的对象，在这种情况下使用 `*pd2` 会是灾难性的。 例如，调用 `D` 类（而非 `B` 类）的成员函数可能会导致访问冲突。

**`dynamic_cast`** 和 **`static_cast`** 运算符在类层次结构中移动指针。 但是， **`static_cast`** 仅依赖于 cast 语句中提供的信息，因此可能是不安全的。 例如：

```cpp
// static_cast_Operator_2.cpp
// compile with: /LD /GR
class B {
public:
   virtual void Test(){}
};
class D : public B {};

void f(B* pb) {
   D* pd1 = dynamic_cast<D*>(pb);
   D* pd2 = static_cast<D*>(pb);
}
```

如果 `pb` 确实指向 `D` 类型的对象，则 `pd1` 和 `pd2` 将获取相同的值。 如果 `pb == 0`，它们也将获取相同的值。

如果 `pb` 指向类型为 `B` 而不是完整类的对象 `D` ，则 **`dynamic_cast`** 将知道是否足以返回零。 但是， **`static_cast`** 依赖于程序员的断言，该断言指向 `pb` 类型的对象 `D` ，只是返回指向该对象的指针 `D` 。

因此， **`static_cast`** 可以反转隐式转换，在这种情况下，结果是不确定的。 它留给程序员来验证转换的结果 **`static_cast`** 是否安全。

该行为也适用于类以外的类型。 例如， **`static_cast`** 可用于从 int 转换为 **`char`** 。 但是，生成的 **`char`** 位数可能不足以容纳整个 **`int`** 值。 同样，它还留给程序员来验证转换的结果 **`static_cast`** 是否安全。

**`static_cast`** 运算符还可用于执行任何隐式转换，包括标准转换和用户定义的转换。 例如：

```cpp
// static_cast_Operator_3.cpp
// compile with: /LD /GR
typedef unsigned char BYTE;

void f() {
   char ch;
   int i = 65;
   float f = 2.5;
   double dbl;

   ch = static_cast<char>(i);   // int to char
   dbl = static_cast<double>(f);   // float to double
   i = static_cast<BYTE>(ch);
}
```

**`static_cast`** 运算符可以将整数值显式转换为枚举类型。 如果整型值不在枚举值的范围内，生成的枚举值是不确定的。

**`static_cast`** 运算符将 null 指针值转换为目标类型的 null 指针值。

任何表达式都可以通过运算符显式转换为 void 类型 **`static_cast`** 。 目标 void 类型可以选择性地包括 **`const`** 、 **`volatile`** 或 **`__unaligned`** 特性。

**`static_cast`** 运算符不能转换为 **`const`** 、 **`volatile`** 或 **`__unaligned`** 特性。 有关删除这些属性的信息，请参阅[Const_cast 运算符](../cpp/const-cast-operator.md)。

**C + +/CLI：** 由于在重新定位垃圾回收器之上执行未检查强制转换的危险，在 **`static_cast`** 您确定其可以正常工作时，使用应在性能关键代码中。 如果必须 **`static_cast`** 在发布模式下使用，请将其替换为调试版本中的[safe_cast](../extensions/safe-cast-cpp-component-extensions.md) ，以确保成功。

## <a name="see-also"></a>另请参阅

[转换运算符](../cpp/casting-operators.md)<br/>
[关键字](../cpp/keywords-cpp.md)
