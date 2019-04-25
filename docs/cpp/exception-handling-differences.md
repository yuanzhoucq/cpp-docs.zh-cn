---
title: 处理中的结构化的异常C++
ms.date: 08/14/2018
helpviewer_keywords:
- structured exception handling [C++], vs. C++ exception handling
- structured exception handling [C++], vs. unstructured
- exceptions [C++], wrapper class
- C++ exception handling [C++], vs. structured exception handling
- wrapper classes [C++], C exception
ms.assetid: f21d1944-4810-468e-b02a-9f77da4138c9
ms.openlocfilehash: 2c4f1a8c3729e2b4d49a0152425e57717f7e9997
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62154396"
---
# <a name="handle-structured-exceptions-in-c"></a>处理中的结构化的异常C++

C 之间的主要区别结构化异常处理 (SEH) 和C++，异常处理是指C++类型中处理的异常处理模型，而 C 结构化的异常处理模型的处理是一种类型; 的异常具体而言，**无符号的 int**。即，C 异常由无符号整数值标识，而 C++ 异常由数据类型标识。 当在 C 中引发结构化的异常时，每个可能的处理程序执行的筛选器检查 C 异常上下文并确定是否接受该异常、 将其传递给其他处理，或将其忽略。 当 C++ 中引发了异常时，该异常可以是任何类型。

第二个区别是，C 结构化的异常处理模型被称为*异步*，因为次要的正常控制流发生的异常。 C++异常处理机制是完全*同步*，这意味着，会发生异常，仅在被引发。

当你使用[/EHs 或 /EHsc](../build/reference/eh-exception-handling-model.md)编译器选项，则不C++异常处理程序处理结构化的异常。 仅可由处理这些异常 **__catch**结构化异常处理程序或 **__finally**结构化终止处理程序。 有关信息，请参阅[结构化异常处理 (C /C++)](structured-exception-handling-c-cpp.md)。

下[/EHa](../build/reference/eh-exception-handling-model.md)编译器选项时，如果在引发 C 异常，则C++程序，它可以处理结构化的异常处理程序与其关联筛选器或通过C++**捕获**处理程序，无论是动态接近异常上下文。 例如，下面的 C++ 程序引发了 C 异常在 C++**重**上下文：

## <a name="example---catch-a-c-exception-in-a-c-catch-block"></a>示例-在 Catch C 异常C++catch 块

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

可以在类似上面的简单示例中，捕获的 C 异常只能由省略号 (**...**)**捕获**处理程序。 有关类型或异常性质的信息不传递给该处理程序。 尽管此方法有效，在某些情况下您可能想要定义两个异常处理模式之间进行转换，使每个 C 异常不与特定的类相关联。 为此，您可以定义 C 异常“包装器”类，可以使用该类或从中进行派生以将特定类类型特性化为 C 异常。 通过此操作，每个 C 异常可以单独处理由特定C++**捕获**处理程序，而不是所有这些单个处理程序中。

您的包装器类可能有一个接口，该接口包含一些成员函数，用来确定异常的值以及访问 C 异常模型提供的扩展异常上下文信息。 您可能还需要定义默认构造函数和构造函数接受**无符号的 int**参数 （用于提供基础 C 异常表示形式），和一个按位复制构造函数。 下面是可能的 C 异常包装器类实现：

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

若要使用此类，请安装由内部异常处理机制每次引发 C 异常时调用的自定义 C 异常转换函数。 在你的转换函数，你可以引发任何类型化的异常 (可能是`SE_Exception`类型或类类型派生自`SE_Exception`)，可由适当匹配 C++ 捕获**捕获**处理程序。 转换函数可能直接返回，这表示它没有处理异常。 如果转换功能本身引起了 C 异常，[终止](../c-runtime-library/reference/terminate-crt.md)调用。

若要指定自定义转换函数，请调用[_set_se_translator](../c-runtime-library/reference/set-se-translator.md)函数和转换函数作为其单个参数的名称。 您编写的转换函数的堆栈上的具有每个函数调用一次**尝试**块。 没有默认转换函数;如果未指定某个通过调用 **_set_se_translator**，仅可由省略号捕获到 C 异常**捕获**处理程序。

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

## <a name="see-also"></a>请参阅

[混合 C （结构化） 和C++异常](../cpp/mixing-c-structured-and-cpp-exceptions.md)
