---
title: const (C++)
ms.date: 11/04/2016
f1_keywords:
- const_cpp
helpviewer_keywords:
- const keyword [C++]
ms.assetid: b21c0271-1ad0-40a0-b21c-5e812bba0318
ms.openlocfilehash: db79e228f1fabc4b2da0a7778126a1b576a67768
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87229033"
---
# <a name="const-c"></a>const (C++)

在修改数据声明时， **`const`** 关键字指定对象或变量不可修改。

## <a name="syntax"></a>语法

```
const declaration ;
member-function const ;
```

## <a name="const-values"></a>常量值

**`const`** 关键字指定变量的值是常量，并通知编译器阻止程序员修改该变量的值。

```cpp
// constant_values1.cpp
int main() {
   const int i = 5;
   i = 10;   // C3892
   i++;   // C2105
}
```

在 c + + 中，可以使用 **`const`** 关键字而不是[#define](../preprocessor/hash-define-directive-c-cpp.md)预处理器指令来定义常量值。 使用定义的值 **`const`** 受类型检查的约束，可用于代替常量表达式。 在 c + + 中，可以使用变量指定数组的大小，如下所示 **`const`** ：

```cpp
// constant_values2.cpp
// compile with: /c
const int maxarray = 255;
char store_char[maxarray];  // allowed in C++; not allowed in C
```

在 C 中，常量值默认为外部链接，因此它们只能出现在源文件中。 在 C++ 中，常量值默认为内部链接，这使它们可以出现在标头文件中。

**`const`** 关键字还可以用在指针声明中。

```cpp
// constant_values3.cpp
int main() {
   char *mybuf = 0, *yourbuf;
   char *const aptr = mybuf;
   *aptr = 'a';   // OK
   aptr = yourbuf;   // C3892
}
```

指向声明为的变量的指针只能 **`const`** 分配给同时声明为的指针 **`const`** 。

```cpp
// constant_values4.cpp
#include <stdio.h>
int main() {
   const char *mybuf = "test";
   char *yourbuf = "test2";
   printf_s("%s\n", mybuf);

   const char *bptr = mybuf;   // Pointer to constant data
   printf_s("%s\n", bptr);

   // *bptr = 'a';   // Error
}
```

可以将指向常量数据的指针用作函数参数，以防止函数修改通过指针传递的参数。

对于声明为的对象 **`const`** ，只能调用常量成员函数。 这将确保从不修改常量对象。

```cpp
birthday.getMonth();    // Okay
birthday.setMonth( 4 ); // Error
```

可以为非常量对象调用常量或非常量成员函数。 你还可以使用关键字重载成员函数 **`const`** ; 这允许为常量和非常量对象调用函数的不同版本。

不能用关键字声明构造函数或析构函数 **`const`** 。

## <a name="const-member-functions"></a>常量成员函数

使用关键字声明成员函数 **`const`** 时，指定该函数是一个 "只读" 函数，该函数不会修改为其调用该函数的对象。 常量成员函数不能修改任何非静态数据成员或调用不是常量的任何成员函数。若要声明常量成员函数，请在 **`const`** 参数列表的右括号后放置关键字。 **`const`** 声明和定义中都需要关键字。

```cpp
// constant_member_function.cpp
class Date
{
public:
   Date( int mn, int dy, int yr );
   int getMonth() const;     // A read-only function
   void setMonth( int mn );   // A write function; can't be const
private:
   int month;
};

int Date::getMonth() const
{
   return month;        // Doesn't modify anything
}
void Date::setMonth( int mn )
{
   month = mn;          // Modifies data member
}
int main()
{
   Date MyDate( 7, 4, 1998 );
   const Date BirthDate( 1, 18, 1953 );
   MyDate.setMonth( 4 );    // Okay
   BirthDate.getMonth();    // Okay
   BirthDate.setMonth( 4 ); // C2662 Error
}
```

## <a name="c-and-c-const-differences"></a>C 和 c + + const 差异

当你 **`const`** 在 C 源代码文件中将变量声明为时，你可以执行以下操作：

```cpp
const int i = 2;
```

您随后可以在另一个模块中使用此变量，如下所示：

```cpp
extern const int i;
```

但若要在 c + + 中获取相同的行为，则必须将 **`const`** 变量声明为：

```cpp
extern const int i = 2;
```

如果希望在 c **`extern`** + + 源代码文件中声明变量以便在 c 源代码文件中使用，请使用：

```cpp
extern "C" const int x=10;
```

以防止 C++ 编译器进行名称重整。

## <a name="remarks"></a>备注

在成员函数的参数列表后， **`const`** 关键字指定函数不会修改为其调用该函数的对象。

有关的详细信息 **`const`** ，请参阅以下主题：

- [const 和 volatile 指针](../cpp/const-and-volatile-pointers.md)

- [类型限定符（C# 语言参考）](../c-language/type-qualifiers.md)

- [volatile](../cpp/volatile-cpp.md)

- [#define](../preprocessor/hash-define-directive-c-cpp.md)

## <a name="see-also"></a>另请参阅

[关键字](../cpp/keywords-cpp.md)
