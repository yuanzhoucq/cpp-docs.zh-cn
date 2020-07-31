---
title: 处理 C++ 中的结构性异常
description: 如何使用 c + + 异常处理模型处理结构化异常。
ms.date: 09/19/2019
helpviewer_keywords:
- structured exception handling [C++], vs. C++ exception handling
- structured exception handling [C++], vs. unstructured
- exceptions [C++], wrapper class
- C++ exception handling [C++], vs. structured exception handling
- wrapper classes [C++], C exception
ms.assetid: f21d1944-4810-468e-b02a-9f77da4138c9
ms.openlocfilehash: 0f92bbe64db028ec6a7fd6ae2cc217c707d3e2c5
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87221583"
---
# <a name="handle-structured-exceptions-in-c"></a>处理 C++ 中的结构性异常

C 结构化异常处理（SEH）和 c + + 异常处理之间的主要区别在于 c + + 异常处理模型处理类型，而 C 结构化异常处理模型处理一种类型的异常;具体而言， **`unsigned int`** 。 即，C 异常由无符号整数值标识，而 C++ 异常由数据类型标识。 如果 C 中引发了结构化异常，则每个可能的处理程序将执行一个筛选器，该筛选器检查 C 异常上下文并确定是否接受异常、将其传递给其他处理程序或忽略它。 当 C++ 中引发了异常时，该异常可以是任何类型。

第二个差异是 C 结构化异常处理模型称为 "*异步*"，因为异常发生在正常的控制流中。 C + + 异常处理机制完全*同步*，这意味着异常仅在引发时才会发生。

使用[/ehs 或/ehsc](../build/reference/eh-exception-handling-model.md)编译器选项时，任何 c + + 异常处理程序都不会处理结构化异常。 这些异常仅由 **`__except`** 结构化异常处理程序或 **`__finally`** 结构化终止处理程序处理。 有关信息，请参阅[结构化异常处理（c/c + +）](structured-exception-handling-c-cpp.md)。

在[/eha](../build/reference/eh-exception-handling-model.md)编译器选项下，如果 c + + 程序中引发了 c 异常，则它可以由结构化异常处理程序（与其关联的筛选器或 c + + **`catch`** 处理程序）处理，以动态接近异常上下文。 例如，此示例 c + + 程序在 c + + 上下文中引发了 C 异常 **`try`** ：

## <a name="example---catch-a-c-exception-in-a-c-catch-block"></a>示例-在 c + + catch 块中捕获 C 异常

```cpp
// exceptions_Exception_Handling_Differences.cpp
// compile with: /EHa
#include <iostream>

using namespace std;
void SEHFunc( void );

int main() {
   try {
      SEHFunc();
   }
   catch( ... ) {
      cout << "Caught a C exception."<< endl;
   }
}

void SEHFunc() {
   __try {
      int x, y = 0;
      x = 5 / y;
   }
   __finally {
      cout << "In finally." << endl;
   }
}
```

```Output
In finally.
Caught a C exception.
```

## <a name="c-exception-wrapper-classes"></a>C 异常包装器类

在类似上述的简单示例中，C 异常只能由省略号（**...**） **`catch`** 捕获函数. 有关类型或异常性质的信息不传递给该处理程序。 尽管此方法有效，但在某些情况下，您可能需要在两个异常处理模型之间定义转换，以便每个 C 异常与一个特定类关联。 若要转换一个，可以定义一个 C 异常 "包装" 类，该类可用于将特定类类型属性为 C 异常。 这样，每个 C 异常都可以由特定 c + + **`catch`** 处理程序单独处理，而不是在单个处理程序中单独处理。

您的包装器类可能有一个接口，该接口包含一些成员函数，用来确定异常的值以及访问 C 异常模型提供的扩展异常上下文信息。 你可能还需要定义默认构造函数和接受自变量的构造函数 **`unsigned int`** （以提供基础 C 异常表示形式）和按位复制构造函数。 下面是 C 异常包装器类的可能实现：

```cpp
// exceptions_Exception_Handling_Differences2.cpp
// compile with: /c
class SE_Exception {
private:
   SE_Exception() {}
   SE_Exception( SE_Exception& ) {}
   unsigned int nSE;
public:
   SE_Exception( unsigned int n ) : nSE( n ) {}
   ~SE_Exception() {}
   unsigned int getSeNumber() {
      return nSE;
   }
};
```

若要使用此类，请安装自定义 C 异常转换函数，该函数在每次引发 C 异常时由内部异常处理机制调用。 在您的转换函数内，您可以引发任何类型化的异常（可能是 `SE_Exception` 类型，也可能是派生自的类类型 `SE_Exception` ），该异常可通过相应的匹配 c + + **`catch`** 处理程序捕获。 转换函数可以返回，这表示它不处理异常。 如果转换函数本身引发 C 异常，则调用[终止](../c-runtime-library/reference/terminate-crt.md)。

若要指定自定义转换函数，请使用您的转换函数的名称作为其单个参数来调用[_set_se_translator](../c-runtime-library/reference/set-se-translator.md)函数。 对于具有块的堆栈上的每个函数调用，将调用您编写的转换函数一次 **`try`** 。 没有默认的转换函数;如果未通过调用 **_set_se_translator**指定一个，则 C 异常只能由省略号 **`catch`** 处理程序捕获。

## <a name="example---use-a-custom-translation-function"></a>示例-使用自定义转换函数

例如，以下代码安装了自定义转换函数，然后引发了由 `SE_Exception` 类包装的 C 异常：

```cpp
// exceptions_Exception_Handling_Differences3.cpp
// compile with: /EHa
#include <stdio.h>
#include <eh.h>
#include <windows.h>

class SE_Exception {
private:
   SE_Exception() {}
   unsigned int nSE;
public:
   SE_Exception( SE_Exception& e) : nSE(e.nSE) {}
   SE_Exception(unsigned int n) : nSE(n) {}
   ~SE_Exception() {}
   unsigned int getSeNumber() { return nSE; }
};

void SEFunc() {
    __try {
        int x, y = 0;
        x = 5 / y;
    }
    __finally {
        printf_s( "In finally\n" );
    }
}

void trans_func( unsigned int u, _EXCEPTION_POINTERS* pExp ) {
    printf_s( "In trans_func.\n" );
    throw SE_Exception( u );
}

int main() {
    _set_se_translator( trans_func );
    try {
        SEFunc();
    }
    catch( SE_Exception e ) {
        printf_s( "Caught a __try exception with SE_Exception.\n" );
        printf_s( "nSE = 0x%x\n", e.getSeNumber() );
    }
}
```

```Output
In trans_func.
In finally
Caught a __try exception with SE_Exception.
nSE = 0xc0000094
```

## <a name="see-also"></a>另请参阅

[混合使用 C（结构化）和 C++ 异常](../cpp/mixing-c-structured-and-cpp-exceptions.md)
