---
title: 复制构造函数和复制赋值运算符 (C++)
ms.date: 11/04/2016
helpviewer_keywords:
- = operator [C++], copying objects
- assignment statements [C++], copying objects
- assignment operators [C++], for copying objects
- objects [C++], copying
- initializing objects, by copying objects
- copying objects
- assigning values to copy objects
ms.assetid: a94fe1f9-0289-4fb9-8633-77c654002c0d
ms.openlocfilehash: beabe4c6219975d33c7af98a94498188c9abfa55
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80189520"
---
# <a name="copy-constructors-and-copy-assignment-operators-c"></a>复制构造函数和复制赋值运算符 (C++)

> [!NOTE]
> 从 c + + 11 开始，语言支持两种类型的分配：*复制分配*和*移动分配*。 在本文中，“赋值”意味着复制赋值，除非有其他显式声明。 有关移动赋值的信息，请参阅[移动构造函数和移动赋值C++运算符（）](move-constructors-and-move-assignment-operators-cpp.md)。
>
> 赋值操作和初始化操作都会导致对象被复制。

- **赋值**：将一个对象的值分配给另一个对象时，会将第一个对象复制到第二个对象。 因此，

    ```cpp
    Point a, b;
    ...
    a = b;
    ```

   导致 `b` 的值被复制到 `a` 中。

- **初始化**：在以下情况下进行初始化：声明新对象、按值将参数传递给函数时，或按值从函数返回值。

您可以为类类型的对象定义“复制”的语义。 例如，假设有以下代码：

```cpp
TextFile a, b;
a.Open( "FILE1.DAT" );
b.Open( "FILE2.DAT" );
b = a;
```

前面的代码可能表示“将 FILE1.DAT 的内容复制到 FILE2.DAT”，也可能表示“忽略 FILE2.DAT 并使 `b` 成为 FILE1.DAT 的另一个句柄”。 您必须将适当的复制语义附加到每个类，如下所示。

- 通过将赋值运算符**运算符**（和对类类型的引用）与对类类型的引用一起使用来作为返回类型和**常数**引用传递的参数（例如 `ClassName& operator=(const ClassName& x);`。

- 通过通过复制构造函数。

如果不声明复制构造函数，编译器将为你生成 member-wise 复制构造函数。  如果不声明复制赋值运算符，编译器将为你生成 member-wise 复制赋值运算符。 声明复制构造函数不会取消编译器生成的复制赋值运算符，反之亦然。 如果实现上述其中一项，建议你还实现另一项以使代码的含义变得明确。

复制构造函数采用类型为<em>class-name</em>的参数<strong>&</strong>，其中，*类名称*是为其定义构造函数的类的名称。 例如：

```cpp
// spec1_copying_class_objects.cpp
class Window
{
public:
    Window( const Window& ); // Declare copy constructor.
    // ...
};

int main()
{
}
```

> [!NOTE]
> 尽可能使复制构造函数的参数**const** <em>类名</em><strong>&</strong>的类型。 这可防止复制构造函数意外更改从中复制它的对象。 它还允许从**const**对象进行复制。

## <a name="compiler-generated-copy-constructors"></a>编译器生成的构造函数

编译器生成的复制构造函数（如用户定义的复制构造函数）具有一个类型为 "引用*类名*" 的单个自变量。 当所有基类和成员类都具有声明为采用**const** <em>类名</em><strong>&</strong>类型的单个自变量的复制构造函数时，就会出现异常。 在这种情况下，编译器生成的复制构造函数的自变量也是**const**。

当复制构造函数的参数类型不是**const**时，通过复制**const**对象进行初始化将生成错误。 反之亦然：如果参数是**const**，则可以通过复制不是**const**的对象进行初始化。

编译器生成的赋值运算符遵循与 const 相同的模式 **。** 它们采用类型为<em>类名称</em>的单个参数<strong>&</strong> ，除非所有基类和成员类中的赋值运算符采用**const** <em>class-name</em> <strong>&</strong>的参数。 在这种情况下，类的生成的赋值运算符采用**const**参数。

> [!NOTE]
> 当虚拟基类由复制构造函数（编译器生成或用户定义的）初始化时，将只初始化这些基类一次：在构造它们时。

含义类似于复制构造函数的含义。 当参数类型不是**const**时，从**const**对象赋值将产生错误。 反之亦然：如果将**常**数值赋给的值不是**常量**，则赋值成功。

有关重载赋值运算符的详细信息，请参阅[赋值](../cpp/assignment.md)。
