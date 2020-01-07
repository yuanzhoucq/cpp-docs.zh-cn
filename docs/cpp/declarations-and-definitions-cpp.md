---
title: 声明和定义（C++）
ms.date: 12/12/2019
ms.assetid: 678f1424-e12f-45e0-a957-8169e5fef6cb
ms.openlocfilehash: d52294b635e05f42a4c48620214a90cad609f575
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/20/2019
ms.locfileid: "75301543"
---
# <a name="declarations-and-definitions-c"></a>声明和定义（C++）

C++程序由各种实体（如变量、函数、类型和命名空间）组成。 必须先*声明*其中的每个实体，然后才能使用这些实体。 声明为实体指定唯一的名称，以及其类型和其他特征的相关信息。 在C++声明名称的点中，该名称将对编译器可见。 不能引用在编译单元中的某个后续点声明的函数或类。 在使用变量之前，应尽可能将变量声明为靠近。

下面的示例演示了一些声明：

```cpp
#include <string>

void f(); // forward declaration

int main()
{
    const double pi = 3.14; //OK
    int i = f(2); //OK. f is forward-declared
    std::string str; // OK std::string is declared in <string> header
    C obj; // error! C not yet declared.
    j = 0; // error! No type specified.
    auto k = 0; // OK. type inferred as int by compiler.
}

int f(int i)
{
    return i + 42;
}

namespace N {
   class C{/*...*/};
}
```

第5行声明了 `main` 函数。 在第7行，已声明并*初始化*名为 `pi` 的**常量**变量。 在第8行，使用函数 `f`生成的值来声明和初始化 `i` 整数。 由于第3行上有*前向声明*，因此该名称 `f` 对编译器可见。 

在第9行，声明一个名为 `C` `obj` 类型为的变量。 但是，此声明会引发错误，因为 `C` 在程序的后面不会声明，也不会被转发。 若要修复此错误，你可以在 `main` 之前移动 `C` 的整个*定义*，或者为其添加前向声明。 此行为不同于其他语言（如C#），可以在这些语言中的声明点之前使用它们。 

在第10行，声明一个名为 `std::string` `str` 类型为的变量。 名称 `std::string` 可见，因为它是在 `string`[头文件](header-files-cpp.md)中引入的，该文件将合并到第1行的源文件中。 `std` 是声明 `string` 类的命名空间。

第11行出现错误，因为尚未声明名称 `j`。 声明必须提供与其他语言（如 javaScript）不同的类型。 在第12行中，使用的是 `auto` 关键字，它指示编译器根据其初始化的值推断 `k` 的类型。 在这种情况下，编译器将选择类型 `int`。  

## <a name="declaration-scope"></a>声明范围

声明引入的名称在声明发生的*范围*内有效。 在上面的示例中，在 `main` 函数内声明的变量是*局部变量*。 可以在 main 之外的*全局范围内*声明名为 `i` 的另一个变量，它将是完全独立的实体。 但是，这种名称重复可能会导致程序员混淆和错误，应避免这样做。 在第21行中，类 `C` 在命名空间 `N`的范围内声明。 使用命名空间有助于避免*名称冲突*。 大多数C++标准库名称是在 `std` 命名空间中声明的。 有关范围规则如何与声明进行交互的详细信息，请参阅[作用域](../cpp/scope-visual-cpp.md)。

## <a name="definitions"></a>定义

除了声明以外，还必须定义一些实体，包括函数、类、枚举和常量变量。 *定义*为编译器提供了在稍后在程序中使用该实体时生成计算机代码所需的所有信息。 在上面的示例中，第3行包含函数 `f` 的声明，但在第15行到第18行提供了函数的*定义*。 在第21行，同时声明和定义了类 `C` （尽管在定义类时不会执行任何操作）。 必须在声明常量变量的同一语句中，将其定义为其他的值。 内置类型（如 `int`）的声明会自动定义，因为编译器知道要为其分配多少空间。

下面的示例演示了也定义的声明：

```cpp
// Declare and define int variables i and j.
int i;
int j = 10;

// Declare enumeration suits.
enum suits { Spades = 1, Clubs, Hearts, Diamonds };

// Declare class CheckBox.
class CheckBox : public Control
{
public:
    Boolean IsChecked();
    virtual int     ChangeState() = 0;
};
```

下面是一些不是定义的声明：

```cpp
extern int i;
char *strchr( const char *Str, const char Target );
```

## <a name="typedefs-and-using-statements"></a>Typedef 和 using 语句

在较旧版本C++的中， [typedef](aliases-and-typedefs-cpp.md)关键字用于声明作为另一个名称的*别名*的新名称。 例如，类型 `std::string` 是 `std::basic_string<char>`的另一个名称。 程序员应显而易见，原因是程序员使用了 typedef 名称，而不是实际名称。 在现代C++上， [using](aliases-and-typedefs-cpp.md)关键字优于 typedef，但思路相同：为已声明和定义的实体声明了新名称。

## <a name="static-class-members"></a>静态类成员

因为静态类数据成员是由类的所有对象共享的离散变量，所以必须在类定义外定义和初始化这些变量。 （有关详细信息，请参阅[类](../cpp/classes-and-structs-cpp.md)。）

## <a name="extern-declarations"></a>extern 声明

一个C++程序可能包含多个[编译单元](header-files-cpp.md)。 若要声明在单独的编译单元中定义的实体，请使用[extern](extern-cpp.md)关键字。 声明中的信息足以满足编译器需求，但如果在链接步骤中找不到实体的定义，则链接器将引发错误。

## <a name="in-this-section"></a>本节内容

[存储类](storage-classes-cpp.md)<br/>
[const](const-cpp.md)<br/>
[constexpr](constexpr-cpp.md)<br/>
[extern](extern-cpp.md)<br/>
[初始值设定项](initializers.md)<br/>
[别名和 typedef](aliases-and-typedefs-cpp.md)<br/>
[using 声明](using-declaration.md)<br/>
[volatile](volatile-cpp.md)<br/>
[decltype](decltype-cpp.md)<br/>
[属性C++](attributes.md)<br/>

## <a name="see-also"></a>另请参阅

[基本概念](../cpp/basic-concepts-cpp.md)<br/>
