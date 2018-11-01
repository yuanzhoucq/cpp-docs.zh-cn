---
title: 包含变量自变量列表的函数 （C++）
ms.date: 11/04/2016
helpviewer_keywords:
- arguments [C++], variable number of
- variable argument lists
- declarators, functions
- argument lists [C++], variable number of
- declaring functions [C++], variables
- function calls, variable number of arguments
ms.assetid: 27c2f83a-21dd-44c6-913c-2834cb944703
ms.openlocfilehash: 1f366af6f4058ffb8356017d59a7c176a978b860
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50637292"
---
# <a name="functions-with-variable-argument-lists--c"></a>包含变量自变量列表的函数 （C++）

如果函数声明中最后一个成员是省略号 (...)，则函数声明可采用数量可变的自变量。 在这些情况下，C++ 只为显式声明的参数提供类型检查。 即使自变量的数量和类型是可变的，在需要使函数泛化时也可使用变量自变量列表。 函数系列是使用变量参数列表的函数的示例。`printf`*参数声明列表*

## <a name="functions-with-variable-arguments"></a>包含变量自变量的函数

若要访问声明后的自变量，请使用包含在标准包含文件中的宏\<stdarg.h > 如下所述。

**Microsoft 专用**

Microsoft C++ 允许将省略号指定为自变量（如果省略号是最后一个自变量且在逗号的后面）。 因此，声明 `int Func( int i, ... );` 是合法的，但 `int Func( int i ... );` 不是合法的。

**结束 Microsoft 专用**

采用数量可变的自变量的函数声明至少需要一个占位符自变量（即使不使用它）。 如果未提供此占位符自变量，则无法访问其余自变量。

当类型的自变量**char**传递作为变量自变量，它们会转换为类型**int**。同样，当类型的自变量**float**传递作为变量自变量，它们会转换为类型**double**。 其他类型的参数受常见整型和浮点型提升的限制。 请参阅[标准转换](standard-conversions.md)有关详细信息。

使用自变量列表中的省略号 (...) 来声明需要变量列表的函数。 使用的类型和中所述的宏\<stdarg.h > 包括访问自变量传递的变量列表的文件。 有关这些宏的详细信息，请参阅[va_arg、 va_copy、 va_end、 va_start](../c-runtime-library/reference/va-arg-va-copy-va-end-va-start.md)。 （处于 C 运行时库文档中）。

下面的示例演示如何宏类型一起使用 (中声明\<stdarg.h >):

```cpp
// variable_argument_lists.cpp
#include <stdio.h>
#include <stdarg.h>

//  Declaration, but not definition, of ShowVar.
void ShowVar( char *szTypes, ... );
int main() {
   ShowVar( "fcsi", 32.4f, 'a', "Test string", 4 );
}

//  ShowVar takes a format string of the form
//   "ifcs", where each character specifies the
//   type of the argument in that position.
//
//  i = int
//  f = float
//  c = char
//  s = string (char *)
//
//  Following the format specification is a variable
//  list of arguments. Each argument corresponds to
//  a format character in the format string to which
// the szTypes parameter points
void ShowVar( char *szTypes, ... ) {
   va_list vl;
   int i;

   //  szTypes is the last argument specified; you must access
   //  all others using the variable-argument macros.
   va_start( vl, szTypes );

   // Step through the list.
   for( i = 0; szTypes[i] != '\0'; ++i ) {
      union Printable_t {
         int     i;
         float   f;
         char    c;
         char   *s;
      } Printable;

      switch( szTypes[i] ) {   // Type to expect.
         case 'i':
            Printable.i = va_arg( vl, int );
            printf_s( "%i\n", Printable.i );
         break;

         case 'f':
             Printable.f = va_arg( vl, double );
             printf_s( "%f\n", Printable.f );
         break;

         case 'c':
             Printable.c = va_arg( vl, char );
             printf_s( "%c\n", Printable.c );
         break;

         case 's':
             Printable.s = va_arg( vl, char * );
             printf_s( "%s\n", Printable.s );
         break;

         default:
         break;
      }
   }
   va_end( vl );
}
//Output:
// 32.400002
// a
// Test string
```

上一个示例演示以下重要概念：

1. 在访问任何变量自变量前，必须建立一个列表标记作为类型 `va_list` 的变量。 在前面的示例中，该标记称为 `vl`。

1. 使用 `va_arg` 宏访问各个自变量。 必须告知 `va_arg` 宏要检索的自变量的类型，以便它可以从堆栈中传输正确的字节数。 如果为 `va_arg` 指定的大小的类型与通过调用程序提供的类型不同，则结果是不可预知的。

1. 应将使用 `va_arg` 宏获取的结果显式强制转换为所需类型。

必须调用宏以终止可变参数处理。`va_end`