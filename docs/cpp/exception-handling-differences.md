---
title: 异常处理差异 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-language
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- structured exception handling [C++], vs. C++ exception handling
- structured exception handling [C++], vs. unstructured
- exceptions [C++], wrapper class
- C++ exception handling [C++], vs. structured exception handling
- wrapper classes [C++], C exception
ms.assetid: f21d1944-4810-468e-b02a-9f77da4138c9
caps.latest.revision: 11
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 63fff00222aa083bcb392e0d71411bfcf5c0f418
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="exception-handling-differences"></a>异常处理差异
结构化异常处理和 C++ 异常处理的主要区别在于 C++ 异常处理模式处理的是多个类型，而 C 结构化异常处理模式处理的是一个类型（具体而言就是 `unsigned int`）的异常。 即，C 异常由无符号整数值标识，而 C++ 异常由数据类型标识。 当 C 中引发了异常时，每个可能的处理程序都将执行筛选器来检查 C 异常上下文并确定是接受该异常、将其传递给其他处理程序还是忽略它。 当 C++ 中引发了异常时，该异常可以是任何类型。  
  
 第二个区别在于，C 结构化异常处理模式被称为是“异步的”，因为异常是从属在正常控制流之后发生的。 C++ 异常处理机制是完全“同步的”，这意味着异常仅在被引发时发生。  
  
 如果在 C++ 程序中引发了 C 异常，则可以一起处理通过具有与其关联筛选器的结构化的异常处理程序或 C++**捕获**处理程序中，于哪个更加动态接近异常上下文。 例如，下面的 C++ 程序引发了 C 异常在 C++**重**上下文：  
  
## <a name="example"></a>示例  
  
```  
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
  
##  <a name="_core_c_exception_wrapper_class"></a>C 异常包装器类  
 可在类似上面的简单示例中，捕获 C 异常只能由省略号 (**...**)**捕获**处理程序。 有关类型或异常性质的信息不传递给该处理程序。 尽管此方法有效，但在某些情况下，你可能需要定义两个异常处理模式之间的转换，以便让每个 C 异常与一个特定类关联。 为此，您可以定义 C 异常“包装器”类，可以使用该类或从中进行派生以将特定类类型特性化为 C 异常。 通过这样做，可以由 C++ 处理每个 C 异常**捕获**处理程序单独比在前面的示例。  
  
 您的包装器类可能有一个接口，该接口包含一些成员函数，用来确定异常的值以及访问 C 异常模型提供的扩展异常上下文信息。 您可能还希望定义一个默认构造函数、一个接受 `unsigned int` 参数（用来提供基础 C 异常表示形式）的构造函数和一个按位复制构造函数。 下面是 C 异常包装器类的一个可能的实现：  
  
```  
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
  
 若要使用此类，请安装每次引发 C 异常时由内部异常处理机制调用的自定义 C 异常转换函数。 在你的转换函数，你可以引发任何类型化的异常 (可能是`SE_Exception`类型或类类型派生自`SE_Exception`)，可由适当匹配 C++ 捕获**捕获**处理程序。 转换函数可能直接返回，这表示它没有处理异常。 如果转换功能本身引起了 C 异常，[终止](../c-runtime-library/reference/terminate-crt.md)调用。  
  
 若要指定自定义转换函数，调用[_set_se_translator](../c-runtime-library/reference/set-se-translator.md)函数替换为你作为其单个参数的转换函数的名称。 你编写的转换函数具有的堆栈上每个函数调用一次**重**块。 没有默认转换函数;如果不指定一个，方法是调用`_set_se_translator`，C 异常仅可由省略号捕获**捕获**处理程序。  
  
## <a name="example"></a>示例  
 例如，以下代码安装了自定义转换函数，然后引发了由 `SE_Exception` 类包装的 C 异常：  
  
```  
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
 [混合使用 C（结构化）和 C++ 异常](../cpp/mixing-c-structured-and-cpp-exceptions.md)