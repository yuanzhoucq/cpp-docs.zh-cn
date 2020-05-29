---
title: const (C++)
ms.date: 11/04/2016
f1_keywords:
- const_cpp
helpviewer_keywords:
- const keyword [C++]
ms.assetid: b21c0271-1ad0-40a0-b21c-5e812bba0318
ms.openlocfilehash: cc1f117cc5f26edf9cd85461281b925c97fa5225
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80180299"
---
# <a name="const-c"></a>const (C++)

在修改数据声明时， **const**关键字指定对象或变量不可修改。

## <a name="syntax"></a>语法

```
const declaration ;
member-function const ;
```

## <a name="const-values"></a>常量值

**Const**关键字指定变量的值是常量，并通知编译器阻止程序员修改它。

```cpp
// constant_values1.cpp
int main() {
   const int i = 5;
   i = 10;   // C3892
   i++;   // C2105
}
```

在C++中，可以使用**const**关键字而不是[#define](../preprocessor/hash-define-directive-c-cpp.md)预处理器指令来定义常量值。 使用**const**定义的值受类型检查的限制，可用于代替常量表达式。 在C++中，可以使用**const**变量指定数组的大小，如下所示：

```cpp
// constant_values2.cpp
// compile with: /c
const int maxarray = 255;
char store_char[maxarray];  // allowed in C++; not allowed in C
```

在 C 中，常量值默认为外部链接，因此它们只能出现在源文件中。 在 C++ 中，常量值默认为内部链接，这使它们可以出现在标头文件中。

**Const**关键字还可以用在指针声明中。

```cpp
// constant_values3.cpp
int main() {
   char *mybuf = 0, *yourbuf;
   char *const aptr = mybuf;
   *aptr = 'a';   // OK
   aptr = yourbuf;   // C3892
}
```

指向声明为**const**的变量的指针只能分配给也被声明为**常量**的指针。

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

对于声明为**const**的对象，只能调用常量成员函数。 这将确保从不修改常量对象。

```cpp
birthday.getMonth();    // Okay
birthday.setMonth( 4 ); // Error
```

可以为非常量对象调用常量或非常量成员函数。 还可以使用**const**关键字重载成员函数;这允许为常量和非常量对象调用函数的不同版本。

不能用**const**关键字声明构造函数或析构函数。

## <a name="const-member-functions"></a>常量成员函数

使用**const**关键字声明成员函数时，该函数是一个 "只读" 函数，不会修改为其调用该函数的对象。 常量成员函数不能修改任何非静态数据成员或调用不是常量的任何成员函数。若要声明常量成员函数，请在参数列表的右括号后放置**const**关键字。 在声明和定义中都需要**const**关键字。

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

## <a name="c-and-c-const-differences"></a>C 和C++ const 差异

当在 C 源代码文件中将变量声明为**const**时，可以执行以下操作：

```cpp
const int i = 2;
```

您随后可以在另一个模块中使用此变量，如下所示：

```cpp
extern const int i;
```

但是，若要在中C++获取相同的行为，必须将**常数**变量声明为：

```cpp
extern const int i = 2;
```

如果要在C++源代码文件中声明**外部**变量以便在 C 源代码文件中使用，请使用：

```cpp
extern "C" const int x=10;
```

以防止 C++ 编译器进行名称重整。

## <a name="remarks"></a>备注

当遵循成员函数的参数列表时， **const**关键字指定函数不会修改为其调用该函数的对象。

有关**常量**的详细信息，请参阅以下主题：

- [固定和可变指针](../cpp/const-and-volatile-pointers.md)

- [类型限定符（C 语言参考）](../c-language/type-qualifiers.md)

- [volatile](../cpp/volatile-cpp.md)

- [#define](../preprocessor/hash-define-directive-c-cpp.md)

## <a name="see-also"></a>另请参阅

[关键字](../cpp/keywords-cpp.md)
