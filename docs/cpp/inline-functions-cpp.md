---
title: 内联函数 (C++)
ms.date: 10/09/2018
f1_keywords:
- __forceinline_cpp
- __inline_cpp
- inline_cpp
- __inline
- _inline
- __forceinline
- _forceinline
helpviewer_keywords:
- inline functions [C++], class members
ms.assetid: 355f120c-2847-4608-ac04-8dda18ffe10c
ms.openlocfilehash: 703c04873a733d068da025b595909ecc681ff147
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374091"
---
# <a name="inline-functions-c"></a>内联函数 (C++)

类声明的主体中定义的函数是内联函数。

## <a name="example"></a>示例

在下面的类声明中，`Account` 构造函数是内联函数。 成员函数`GetBalance` `Deposit`、 未`Withdraw`指定为**内联**，但可以作为内联函数实现。

```cpp
// Inline_Member_Functions.cpp
class Account
{
public:
    Account(double initial_balance) { balance = initial_balance; }
    double GetBalance();
    double Deposit( double Amount );
    double Withdraw( double Amount );
private:
    double balance;
};

inline double Account::GetBalance()
{
    return balance;
}

inline double Account::Deposit( double Amount )
{
    return ( balance += Amount );
}

inline double Account::Withdraw( double Amount )
{
    return ( balance -= Amount );
}
int main()
{
}
```

> [!NOTE]
> 在类声明中，函数声明时没有**内联**关键字。 内**联**关键字可以在类声明中指定;因此，可以在类声明中指定内联关键字。结果相同。

给定的内联成员函数在每个编译单元中必须以相同的方式进行声明。 此约束会导致内联函数像实例化函数一样运行。 此外，必须有精确的内联函数的定义。

类成员函数默认为外部链接，除非该函数的定义包含**内联**指定器。 前面的示例表明，这些函数不需要使用**内联**指定器显式声明;在函数定义中使用**内联**会导致它是内联函数。 但是，在调用该函数后将函数重新声明为**内联**是非法的。

## <a name="inline-__inline-and-__forceinline"></a>内联、__inline和\__forceinline

**内联**和 **__inline**指定器指示编译器将函数正文的副本插入到调用函数的每个位置。

仅当编译器的成本/收益分析显示有好处时，才会进行插入（称为内联展开或内联）。 内联展开以代码大小较大的潜在成本减少函数调用的系统开销。

**__forceinline**关键字覆盖成本/收益分析，而是依赖于程序员的判断。 使用 **__forceinline**时要谨慎。 滥用 **__forceinline**可能导致代码越大，性能只会略有提升，在某些情况下甚至性能损失（例如，由于较大可执行文件的分页增加）。

使用内联函数可以使程序更快，因为它们消除了与函数调用关联的开销。 内联展开的函数可以进行无法对普通函数使用的代码优化。

编译器将内联扩展选项和关键字视为建议。 不保证会对函数进行内联。 即使使用 **__forceinline**关键字，也不能强制编译器内联特定函数。 使用 **/clr**编译时，如果对函数应用了安全属性，编译器将不会内联函数。

**内联**关键字仅在C++中可用。 **__inline**和 **__forceinline**关键字在 C 和 C++ 中都有。 为了与早期版本兼容 **，_inline**和 **_forceinline**是 **__inline**的同义词，除非指定编译器选项[\(/Za 禁用语言扩展），](../build/reference/za-ze-disable-language-extensions.md)否则 **__forceinline。**

**内联**关键字告诉编译器，内联扩展是首选。 但是，编译器可以创建函数的单独实例（实例化），并创建标准调用链接而不是内联插入代码。 可能会出现这种行为的两种情况是：

- 递归函数。

- 在翻译单元中的其他位置通过指针引用的函数。

这些原因可能会干扰编译器酌情内联，*可能还有其他原因*;不应依赖**内联**指定器来导致函数内联。

与普通函数一样，对内联函数计算自变量没有明确顺序。 事实上，这可能与使用普通函数调用协议传递时计算自变量的顺序不同。

[/Ob](../build/reference/ob-inline-function-expansion.md)编译器优化选项有助于确定内联函数扩展是否实际发生。

[/LTCG](../build/reference/ltcg-link-time-code-generation.md)执行跨模块内联，无论是否在源代码中请求。

### <a name="example-1"></a>示例 1

```cpp
// inline_keyword1.cpp
// compile with: /c
inline int max( int a , int b ) {
   if( a > b )
      return a;
   return b;
}
```

可以使用**内联**关键字或将函数定义放在类定义中，内联声明类的成员函数。

### <a name="example-2"></a>示例 2

```cpp
// inline_keyword2.cpp
// compile with: /EHsc /c
#include <iostream>
using namespace std;

class MyClass {
public:
   void print() { cout << i << ' '; }   // Implicitly inline
private:
   int i;
};
```

**微软特定**

**__inline**关键字等效于**内联**。

即使 **__forceinline，** 编译器也不能在所有情况下内联代码。 如果出现以下情况，编译器无法对函数进行内联：

- 使用 /Ob0（调试生成的默认选项）编译函数或其调用方。

- 函数和调用方使用不同类型的异常处理（一个中使用 C++ 异常处理，另一个中使用结构化异常处理）。

- 函数具有变量自变量列表。

- 除非使用 /Og、/Ox、/O1 或 /O2 进行编译，否则函数使用内联程序集。

- 函数是递归的，不附带 **#pragmainline_recursion（上）**。 递归函数使用杂注内联为 16 个调用的默认深度。 要减小内衬深度，请使用[inline_depth](../preprocessor/inline-depth.md)杂注。

- 函数是虚函数，进行虚拟调用。 对虚函数的直接调用可以进行内联。

- 程序采用函数地址，调用通过指向函数的指针进行。 对采用其地址的函数的直接调用可以进行内联。

- 该函数还标有[裸](../cpp/naked-cpp.md)[__declspec](../cpp/declspec.md)修饰符。

如果编译器无法内联用 **__forceinline**声明的函数，它将生成级别 1 警告，除非：

- 函数使用 /Od 或 /Ob0 编译。 在这些情况下，预计不会进行内联。

- 函数在外部、包含在的库或其他翻译单元中定义，或是虚拟呼叫目标或间接呼叫目标。 编译器无法标识在当前翻译单元中找不到的非内联代码。

递归函数可以内联替换为[inline_depth](../preprocessor/inline-depth.md)杂注指定的深度，最多只能进行 16 个调用。 该深度之后，递归函数调用被视为对函数实例的调用。  内联启发式对递归函数检查到的深度不能超过 16。 [inline_recursion](../preprocessor/inline-recursion.md)杂注控制当前正在扩展的函数的内联扩展。 有关详细信息[，请参阅内联函数扩展](../build/reference/ob-inline-function-expansion.md)（/Ob） 编译器选项。

**结束微软特定**

有关使用**内联**指定器的详细信息，请参阅：

- [内联类成员函数](../cpp/inline-functions-cpp.md)

- [使用 dllexport 和 dllimport 定义内联 C++ 函数](../cpp/defining-inline-cpp-functions-with-dllexport-and-dllimport.md)

## <a name="when-to-use-inline-functions"></a>何时使用内联函数

内联函数最适用于小函数使用，例如访问私有数据成员。 这些一行或两行代码的“访问器”函数的主要用途是返回有关对象的状态信息；短函数对函数调用的开销很敏感。 较长的函数在调用/返回序列方面花费的时间可成比例地减少，而从内联的获益也会减少。

类`Point`的定义如下：

```cpp
// when_to_use_inline_functions.cpp
class Point
{
public:
    // Define "accessor" functions as
    //  reference types.
    unsigned& x();
    unsigned& y();
private:
    unsigned _x;
    unsigned _y;
};

inline unsigned& Point::x()
{
    return _x;
}
inline unsigned& Point::y()
{
    return _y;
}
int main()
{
}
```

假设坐标操作是此类类的客户端中相对常见的操作，指定两个访问器函数（`x`在前面`y`的示例中），因为**内联**通常节省开销：

- 函数调用（包括参数传递和在堆栈上放置对象地址）

- 保留调用者的堆栈帧

- 设置新的堆栈帧

- 返回值通信

- 旧堆栈帧还原

- 返回

## <a name="inline-functions-vs-macros"></a>内联函数与宏

虽然内联函数类似于宏（因为在编译时进行调用会展开函数代码），但内联函数是通过编译器分析的，而宏是通过预处理器展开的。 因此，存在很多重大差异：

- 内联函数遵循对正常函数强制执行的所有类型安全协议。

- 内联函数使用与任何其他函数相同的语法进行指定，只不过它们在函数声明中包含**内联**关键字。

- 计算一次作为内联函数的参数传递的表达式。 在某些情况下，作为宏的自变量传递的表达式可计算多次。

下面的示例演示了将小写字母转换为大写字母的宏：

```cpp
// inline_functions_macro.c
#include <stdio.h>
#include <conio.h>

#define toupper(a) ((a) >= 'a' && ((a) <= 'z') ? ((a)-('a'-'A')):(a))

int main() {
   char ch;
   printf_s("Enter a character: ");
   ch = toupper( getc(stdin) );
   printf_s( "%c", ch );
}
//  Sample Input:  xyz
// Sample Output:  Z
```

表达式`toupper(getc(stdin))`的意图是应从控制台设备读取字符 （），`stdin`如有必要，应转换为大写。

由于宏的实现，执行一次 `getc` 以确定字符是否大于或等于“a”，再将其执行一次以确定字符是否小于或等于“z”。 如果它在该范围内，则再次执行 `getc` 以将其转换为大写形式。 这意味着，程序将等待两个或三个字符，而在理想情况下，它只应等待一个字符。

内联函数纠正了前面所述的问题：

```cpp
// inline_functions_inline.cpp
#include <stdio.h>
#include <conio.h>

inline char toupper( char a ) {
   return ((a >= 'a' && a <= 'z') ? a-('a'-'A') : a );
}

int main() {
   printf_s("Enter a character: ");
   char ch = toupper( getc(stdin) );
   printf_s( "%c", ch );
}
```

```Output
Sample Input: a
Sample Output: A
```

## <a name="see-also"></a>另请参阅

[noinline](../cpp/noinline.md)<br/>
[auto_inline](../preprocessor/auto-inline.md)
