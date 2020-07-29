---
title: 默认自变量
ms.date: 11/04/2016
helpviewer_keywords:
- arguments [C++], function
- function declarators
- functions [C++], default arguments
- declaring functions [C++], declarators
- default arguments
- arguments [C++], default
- defaults [C++], arguments
ms.assetid: d32cf516-05cb-4d4d-b169-92f5649fdfa2
ms.openlocfilehash: ef0c81501fe37bd27a23daf2dd1c58b3e6a4f6c0
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87221726"
---
# <a name="default-arguments"></a>默认自变量

在许多情况下，函数具有不常使用的自变量，因为使用默认值便已足够。 为了解决此问题，默认自变量工具允许为函数仅指定在给定调用中有意义的自变量。 为了说明此概念，请考虑[函数重载](../cpp/function-overloading.md)中提供的示例。

```cpp
// Prototype three print functions.
int print( char *s );                  // Print a string.
int print( double dvalue );            // Print a double.
int print( double dvalue, int prec );  // Print a double with a
//  given precision.
```

在许多应用程序中，可为 `prec` 提供合理的默认值，从而消除对两个函数的需求：

```cpp
// Prototype two print functions.
int print( char *s );                    // Print a string.
int print( double dvalue, int prec=2 );  // Print a double with a
//  given precision.
```

函数的实现 `print` 略有变化，以反映出对于类型仅存在一个此类函数的事实 **`double`** ：

```cpp
// default_arguments.cpp
// compile with: /EHsc /c

// Print a double in specified precision.
//  Positive numbers for precision indicate how many digits
//  precision after the decimal point to show. Negative
//  numbers for precision indicate where to round the number
//  to the left of the decimal point.

#include <iostream>
#include <math.h>
using namespace std;

int print( double dvalue, int prec ) {
   // Use table-lookup for rounding/truncation.
   static const double rgPow10[] = {
      10E-7, 10E-6, 10E-5, 10E-4, 10E-3, 10E-2, 10E-1, 10E0,
         10E1,  10E2,  10E3,  10E4, 10E5,  10E6
   };
   const int iPowZero = 6;
   // If precision out of range, just print the number.
   if( prec >= -6 && prec <= 7 )
      // Scale, truncate, then rescale.
      dvalue = floor( dvalue / rgPow10[iPowZero - prec] ) *
      rgPow10[iPowZero - prec];
   cout << dvalue << endl;
   return cout.good();
}
```

若要调用新的 `print` 函数，请使用如下代码：

```cpp
print( d );    // Precision of 2 supplied by default argument.
print( d, 0 ); // Override default argument to achieve other
//  results.
```

使用默认参数时，请注意以下几点：

- 默认参数仅在其中省略了尾随参数的函数调用中使用 - 它们必须是最后的参数。 因此，以下代码是非法的：

    ```cpp
    int print( double dvalue = 0.0, int prec );
    ```

- 默认参数不能在以后的声明中重新定义，即使重新定义的参数与原始参数相同也是如此。 因此，以下代码将生成错误：

    ```cpp
    // Prototype for print function.
    int print( double dvalue, int prec = 2 );

    ...

    // Definition for print function.
    int print( double dvalue, int prec = 2 )
    {
    ...
    }
    ```

   此代码的问题在于定义中的函数声明重新定义了 `prec` 的默认自变量。

- 以后的声明可添加额外的默认自变量。

- 可为指向函数的指针提供默认自变量。 例如：

    ```cpp
    int (*pShowIntVal)( int i = 0 );
    ```
