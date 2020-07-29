---
title: 范围 (C++)
ms.date: 11/19/2018
helpviewer_keywords:
- classes [C++], scope
- scope [C++]
- function prototypes [C++], scope
- class scope
- prototype scope
- functions [C++], scope
- scope, C++ names
ms.assetid: 81fecbb0-338b-4325-8332-49f33e716352
ms.openlocfilehash: 5cff7a4607201175c7095a87134850583b76d636
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87227083"
---
# <a name="scope-c"></a>范围 (C++)

当你声明一个程序元素（例如类、函数或变量）时，它的名称只能 "查看"，并在程序的某些部分中使用。 名称在其中可见的上下文称为 "*作用域*"。 例如，如果在函数内声明变量 `x` ， `x` 则仅在函数体中可见。 它具有*本地范围*。 你的程序中可能存在同名的其他变量;只要它们在不同的范围内，它们就不会违反一个定义规则，也不会引发错误。

对于自动非静态变量，范围还决定了在程序内存中创建和销毁它们的时间。

有六种范围：

- **全局范围**全局名称是在任何类、函数或命名空间外部声明的名称。 但是，在 c + + 中，即使这些名称都存在于隐式全局命名空间中。 全局名称的作用域从声明点扩展到在其中声明它们的文件的结尾。 对于全局名称，可见性也由用于确定名称在程序的其他文件中是否可见的[链接](program-and-linkage-cpp.md)规则来控制。

- **命名空间范围**在任何类或枚举定义或函数块外的[命名空间](namespaces-cpp.md)中声明的名称，在其声明点到命名空间的末尾可见。 命名空间可以在不同文件的多个块中定义。

- **本地范围**在函数或 lambda 中声明的名称（包括参数名称）具有本地范围。 它们通常称为 "局部变量"。 它们只能从其声明点到函数或 lambda 主体的末尾可见。 本地作用域是一种块范围，本文稍后将对此进行讨论。

- **类范围**类成员的名称具有类作用域，它在整个类定义中进行扩展，而不考虑声明点。 类成员可访问性由 **`public`** 、 **`private`** 和关键字进一步控制 **`protected`** 。 只能使用成员选择运算符（.）访问公共或受保护成员 **。** 或 **->** ）或指向成员的指针运算符（**.** <strong>\*</strong> 或 **->** <strong>\*</strong> ）。

- **语句范围**在、、或语句中声明的名称 **`for`** **`if`** **`while`** **`switch`** 直到语句块的末尾才可见。

- **函数范围**[标签](labeled-statements.md)具有函数范围，这意味着它在整个函数体中可见，即使在其声明点之前也是如此。 函数作用域使得可以在 `goto cleanup` 声明标签之前编写语句 `cleanup` 。

## <a name="hiding-names"></a>隐藏名称

可通过在封闭块中声明名称来隐藏该名称。 在下图中，在内部块中重新声明 `i`，从而隐藏与外部块范围中的 `i` 关联的变量。

![阻止&#45;作用域名称隐藏](../cpp/media/vc38sf1.png "阻止&#45;作用域名称隐藏") <br/>
块范围和名称隐藏

来自图中显示的程序的输出为：

```cpp
i = 0
i = 7
j = 9
i = 0
```

> [!NOTE]
> 自变量 `szWhat` 被视为处于函数的范围内。 因此，它被当做就像已在函数的最外层块中声明一样。

## <a name="hiding-class-names"></a>隐藏类名

通过声明同一范围内的函数、对象或变量或枚举器，可以隐藏类名称。 但是，当使用关键字作为前缀时，仍可以访问类名 **`class`** 。

```cpp
// hiding_class_names.cpp
// compile with: /EHsc
#include <iostream>
using namespace std;

// Declare class Account at global scope.
class Account
{
public:
    Account( double InitialBalance )
        { balance = InitialBalance; }
    double GetBalance()
        { return balance; }
private:
    double balance;
};

double Account = 15.37;            // Hides class name Account

int main()
{
    class Account Checking( Account ); // Qualifies Account as
                                       //  class name

    cout << "Opening account with a balance of: "
         << Checking.GetBalance() << "\n";
}
//Output: Opening account with a balance of: 15.37
```

> [!NOTE]
> 为调用类名称（）的任何位置 `Account` ，都必须使用关键字类将其与全局范围内的变量帐户区分开来。 当类名出现在范围解析运算符 (::) 的左侧时，此规则不适用。 在范围解析运算符的左侧的名称始终被视为类名称。

下面的示例演示如何使用关键字声明指向类型对象的指针 `Account` **`class`** ：

```cpp
class Account *Checking = new class Account( Account );
```

前面的语句中的 `Account` 初始值设定项（括号中）的具有全局范围; 它的类型为 **`double`** 。

> [!NOTE]
> 此示例中所示的标识符名称的重用被视为较差的编程样式。

有关类对象的声明和初始化的信息，请参阅[类、结构和联合](../cpp/classes-and-structs-cpp.md)。 有关使用 **`new`** 和 **`delete`** 免费存储运算符的信息，请参阅[new 和 delete 运算符](new-and-delete-operators.md)。

## <a name="hiding-names-with-global-scope"></a>隐藏具有全局范围的名称

可以通过在块范围内显式声明相同的名称来隐藏具有全局作用域的名称。 但是，可以使用范围解析运算符（）访问全局范围名称 `::` 。

```cpp
#include <iostream>

int i = 7;   // i has global scope, outside all blocks
using namespace std;

int main( int argc, char *argv[] ) {
   int i = 5;   // i has block scope, hides i at global scope
   cout << "Block-scoped i has the value: " << i << "\n";
   cout << "Global-scoped i has the value: " << ::i << "\n";
}
```

```Output
Block-scoped i has the value: 5
Global-scoped i has the value: 7
```

## <a name="see-also"></a>另请参阅

[基本概念](../cpp/basic-concepts-cpp.md)
