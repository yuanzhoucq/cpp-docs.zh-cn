---
title: '范围解析运算符：::'
ms.date: 11/04/2016
f1_keywords:
- '::'
helpviewer_keywords:
- scope, scope resolution operator
- operators [C++], scope resolution
- scope resolution operator
- ':: operator'
ms.assetid: fd5de9d3-c716-4e12-bae9-03a16fd79a50
ms.openlocfilehash: 07c2884ed0ba114c22a0c71bbaf7268d6f6931a4
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80178881"
---
# <a name="scope-resolution-operator-"></a>范围解析运算符：::

范围解析运算符 **：：** 用于标识和消除在不同范围内使用的标识符。 有关作用域的详细信息，请参阅[作用域](../cpp/scope-visual-cpp.md)。

## <a name="syntax"></a>语法

```
:: identifier
class-name :: identifier
namespace :: identifier
enum class :: identifier
enum struct :: identifier
```

## <a name="remarks"></a>备注

`identifier` 可以是变量、函数或枚举值。

## <a name="with-classes-and-namespaces"></a>具有命名空间和类

以下示例显示范围解析运算符如何与命名空间和类一起使用：

```cpp
namespace NamespaceA{
    int x;
    class ClassA {
    public:
        int x;
    };
}

int main() {

    // A namespace name used to disambiguate
    NamespaceA::x = 1;

    // A class name used to disambiguate
    NamespaceA::ClassA a1;
    a1.x = 2;
}
```

没有范围限定符的范围解析运算符表示全局命名空间。

```cpp
namespace NamespaceA{
    int x;
}

int x;

int main() {
    int x;

    // the x in main()
    x = 0;
    // The x in the global namespace
    ::x = 1;

    // The x in the A namespace
    NamespaceA::x = 2;
}
```

你可以使用范围解析运算符来标识命名空间的成员，还可标识通过 using 指定成员的命名空间的命名空间。 在下面的示例中，你可以使用 `NamespaceC``ClassB``ClassB` 限定 `NamespaceB``NamespaceB``NamespaceC`（尽管 {7}{8}{9} 已在 {10}{11}{12} 中声明），因为已通过 using 指令在 {13}{14}{15} 中指定 {16}{17}{18}。

```cpp
namespace NamespaceB {
    class ClassB {
    public:
        int x;
    };
}

namespace NamespaceC{
    using namespace B;
}
int main() {
    NamespaceB::ClassB c_b;
    NamespaceC::ClassB c_c;

    c_b.x = 3;
    c_c.x = 4;
}
```

可使用范围解析运算符链。 在以下示例中，`NamespaceD::NamespaceD1` 将标识嵌套的命名空间 `NamespaceD1`，并且 `NamespaceE::ClassE::ClassE1` 将标识嵌套的类 `ClassE1`。

```cpp
namespace NamespaceD{
    namespace NamespaceD1{
        int x;
    }
}

namespace NamespaceE{
    class ClassE{
    public:
        class ClassE1{
        public:
            int x;
        };
    };
}

int main() {
    NamespaceD:: NamespaceD1::x = 6;
    NamespaceE::ClassE::ClassE1 e1;
    e1.x = 7  ;
}
```

## <a name="with-static-members"></a>具有静态成员

必须使用范围解析运算符来调用类的静态成员。

```cpp
class ClassG {
public:
    static int get_x() { return x;}
    static int x;
};

int ClassG::x = 6;

int main() {

    int gx1 = ClassG::x;
    int gx2 = ClassG::get_x();
}
```

## <a name="with-scoped-enumerations"></a>具有区分范围的枚举

作用域内的解析运算符也与范围枚举[枚举声明](../cpp/enumerations-cpp.md)的值一起使用，如以下示例中所示：

```cpp
enum class EnumA{
    First,
    Second,
    Third
};

int main() {
    EnumA enum_value = EnumA::First;
}
```

## <a name="see-also"></a>另请参阅

[C++ 内置运算符、优先级和关联性](../cpp/cpp-built-in-operators-precedence-and-associativity.md)<br/>
[命名空间](../cpp/namespaces-cpp.md)
