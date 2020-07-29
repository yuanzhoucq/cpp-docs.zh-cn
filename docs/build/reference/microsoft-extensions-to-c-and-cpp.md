---
title: Microsoft C 和 C++ 扩展
ms.date: 06/14/2018
helpviewer_keywords:
- or_eq operator
- ~ operator, extensions to C/C++
- '& operator, extensions to C/C++'
- '&= operator'
- iso646.h header
- Xor operator, Microsoft extensions to C/C++
- '!= operator'
- '! operator, extension to C++'
- Or operator, Microsoft extensions to C/C++
- ^ operator, extensions to C/C++
- ^= operator, C++ extensions
- xor_eq operator
- and_eq operator
- Microsoft extensions to C/C++
- '|= operator'
- '|| operator'
- And operator, extensions to C/C++
- NOT operator
- '&& operator'
- extensions, C language
- Visual C++, extensions to C/C++
- '| operator, extensions'
- not_eq operator
- Visual C, Microsoft extensions
- extensions
- compl method
ms.assetid: e811a74a-45ba-4c00-b206-2f2321b8689a
ms.openlocfilehash: 77f2ed64a0c816d84e67f66b664141581a9fad51
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87231502"
---
# <a name="microsoft-extensions-to-c-and-c"></a>Microsoft C 和 C++ 扩展

Visual C++ 按如下方式扩展 ANSI C 和 ANSI C++ 标准。

## <a name="keywords"></a>关键字

添加了几个关键字。 在[关键字](../../cpp/keywords-cpp.md)列表中，具有两个前导下划线的关键字是 Visual C++ 扩展。

## <a name="out-of-class-definition-of-static-const-integral-or-enum-members"></a>静态常量整型（或枚举）成员的类定义

在标准（**/za**）下，必须为数据成员生成类外定义，如下所示：

```cpp
class CMyClass  {
   static const int max = 5;
   int m_array[max];
}
// . . .
const int CMyClass::max;   // out of class definition
```

在 **/ze**下，类外定义对于 static、const 整型和 const 枚举数据成员是可选的。 在类中，只有静态和常量类型的整数和枚举可以有初始值；初始化表达式必须是常量表达式。

若要避免在标头文件中提供类外定义且标头文件包含在多个源文件中时出现错误，请使用[selectany](../../cpp/selectany.md)。 例如：

```cpp
__declspec(selectany) const int CMyClass::max = 5;
```

## <a name="casts"></a>转换

C++ 编译器和 C 编译器都支持以下类型的非 ANSI 转换：

- 生成左值的非 ANSI 强制转换。 例如：

   ```C
   char *p;
   (( int * ) p )++;
   ```

   > [!NOTE]
   > 此扩展仅适用于 C 语言。 你可以在 C++ 代码中使用以下 ANSI C 标准窗体，将指针视为指向其他类型的指针来修改。

   可采用如下方式重新编写前面的示例以符合 ANSI C 标准。

   ```C
   p = ( char * )(( int * )p + 1 );
   ```

- 函数指针到数据指针的非 ANSI 强制转换。 例如：

   ```C
   int ( * pfunc ) ();
   int *pdata;
   pdata = ( int * ) pfunc;
   ```

   若要在保持 ANSI 兼容性的同时执行上述转换，您可以在将函数指针转换为数据指针前将前者强制转换为 `uintptr_t`：

   ```C
   pdata = ( int * ) (uintptr_t) pfunc;
   ```

## <a name="variable-length-argument-lists"></a>可变长度参数列表

C++ 编译器和 C 编译器都支持指定可变数量的自变量并后跟提供类型的函数定义的函数声明符：

```cpp
void myfunc( int x, ... );
void myfunc( int x, char * c )
{ }
```

## <a name="single-line-comments"></a>单行注释

C 编译器支持单行注释，它是使用两个正斜杠 (//) 字符引入的：

```C
// This is a single-line comment.
```

## <a name="scope"></a>作用域

C 编译器支持以下范围相关功能。

- 将 extern 项的重新定义为静态：

   ```C
   extern int clip();
   static int clip()
   {}
   ```

- 在同一范围内使用良性 typedef 重新定义：

   ```C
   typedef int INT;
   typedef int INT;
   ```

- 函数声明符具有文件范围：

   ```C
   void func1()
   {
       extern int func2( double );
   }
   int main( void )
   {
       func2( 4 );    //  /Ze passes 4 as type double
   }                  //  /Za passes 4 as type int
   ```

- 用非常量表达式初始化的块范围变量的使用：

   ```C
   int clip( int );
   int bar( int );
   int main( void )
   {
       int array[2] = { clip( 2 ), bar( 4 ) };
   }
   int clip( int x )
   {
       return x;
   }
   int bar( int x )
   {
       return x;
   }
   ```

## <a name="data-declarations-and-definitions"></a>数据声明和定义

C 编译器支持以下数据声明和定义功能。

- 初始值设定项中的混合字符和字符串常量：

   ```C
   char arr[5] = {'a', 'b', "cde"};
   ```

- 包含除或之外的基类型的位域 **`unsigned int`** **`signed int`** 。

- 没有类型的声明符：

   ```C
   x;
   int main( void )
   {
       x = 1;
   }
   ```

- 成员列表数组数组作为结构和联合中的最后一个字段：

   ```C
   struct zero
   {
       char *c;
       int zarray[];
   };
   ```

- 未命名（匿名）结构：

   ```C
   struct
   {
       int i;
       char *s;
   };
   ```

- 未命名（匿名）联合：

   ```C
   union
   {
       int i;
       float fl;
   };
   ```

- 未命名成员：

   ```C
   struct s
   {
      unsigned int flag : 1;
      unsigned int : 31;
   }
   ```

## <a name="intrinsic-floating-point-functions"></a>内部浮点函数

`atan` `atan2` `cos` `exp` `log` `log10` `sin` `sqrt` `tan` 当指定 **/Oi**时，x86 c + + 编译器和 C 编译器都支持、、、、、、、和函数的内联生成。 对于 C 编译器，使用这些内部函数时将违反 ANSI，因为它们没有设置 `errno` 变量。

## <a name="passing-a-non-const-pointer-parameter-to-a-function-that-expects-a-reference-to-a-const-pointer-parameter"></a>向需要引用常量指针参数的函数传递一个非常量指针参数

这是 c + + 的扩展。 此代码将用 **/ze**编译：

```cpp
typedef   int   T;

const T  acT = 9;      // A constant of type 'T'
const T* pcT = &acT;   // A pointer to a constant of type 'T'

void func2 ( const T*& rpcT )   // A reference to a pointer to a constant of type 'T'
{
   rpcT = pcT;
}

T*   pT;               // A pointer to a 'T'

void func ()
{
   func2 ( pT );      // Should be an error, but isn't detected
   *pT   = 7;         // Invalidly overwrites the constant 'acT'
}
```

## <a name="iso646h-not-enabled"></a>ISO646.H 未启用

在 **/ze**下，如果要使用以下运算符的文本格式，则必须包含 iso646：

- &&（与）

- &= （and_eq）

- & （bitand）

- &#124; （bitor）

- ~ （compl）

- ! 不仅

- ！ = （not_eq）

- &#124;&#124;（或）

- &#124;= （or_eq）

- ^ （xor）

- ^ = （xor_eq）

## <a name="address-of-string-literal-has-type-const-char--not-const-char--"></a>字符串的地址具有类型 const char []，而不是常量 char （*） []

下面的示例将 `char const (*)[4]` 在 **/za**下输出，但 `char const [4]` 在 **/ze**下输出。

```cpp
#include <stdio.h>
#include <typeinfo>

int main()
{
    printf_s("%s\n", typeid(&"abc").name());
}
```

## <a name="see-also"></a>另请参阅

- [/Za、/Ze （禁用语言扩展）](za-ze-disable-language-extensions.md)
- [MSVC 编译器选项](compiler-options.md)
- [MSVC 编译器命令行语法](compiler-command-line-syntax.md)
