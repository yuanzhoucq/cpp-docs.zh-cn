---
title: "异常处理差异 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C++ 异常处理, 与结构化异常处理"
  - "异常, 包装类"
  - "结构化异常处理, 与 C++ 异常处理"
  - "结构化异常处理, 与无结构的"
  - "包装类, C 异常"
ms.assetid: f21d1944-4810-468e-b02a-9f77da4138c9
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# 异常处理差异
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

结构化异常处理和 C\+\+ 异常处理的主要区别在于 C\+\+ 异常处理模式处理的是多个类型，而 C 结构化异常处理模式处理的是一个类型（具体而言就是 `unsigned int`）的异常。  即，C 异常由无符号整数值标识，而 C\+\+ 异常由数据类型标识。  当 C 中引发了异常时，每个可能的处理程序都将执行筛选器来检查 C 异常上下文并确定是接受该异常、将其传递给其他处理程序还是忽略它。  当 C\+\+ 中引发了异常时，该异常可以是任何类型。  
  
 第二个区别在于，C 结构化异常处理模式被称为是“异步的”，因为异常是从属在正常控制流之后发生的。  C\+\+ 异常处理机制是完全“同步的”，这意味着异常仅在被引发时发生。  
  
 如果在 C\+\+ 程序中引发了 C 异常，则可以由结构化异常处理程序与其关联筛选器一起处理，或由 C\+\+ **catch** 处理程序处理，具体取决于哪个更加动态接近异常上下文。  例如，下面的 C\+\+ 程序在 C\+\+ **try** 上下文中引发了 C 异常：  
  
## 示例  
  
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
  
  **In finally.**  
**Caught a C exception.**   
##  <a name="_core_c_exception_wrapper_class"></a> C 异常包装器类  
 在类似上面的简单示例中，C 异常只能由省略号 \(**...**\) **catch** 处理程序捕获。  有关类型或异常性质的信息不传递给该处理程序。  尽管此方法有效，但在某些情况下，您可能需要定义两个异常处理模式之间的转换，以便让每个 C 异常与一个特定类关联。  为此，您可以定义 C 异常“包装器”类，可以使用该类或从中进行派生以将特定类类型特性化为 C 异常。  通过执行此操作，每个异常可以比前一个示例中更独立地由 C\+\+ **catch** 处理程序进行处理。  
  
 您的包装器类可能有一个接口，该接口包含一些成员函数，用来确定异常的值以及访问 C 异常模型提供的扩展异常上下文信息。  您可能还希望定义一个默认构造函数、一个接受 `unsigned int` 参数（用来提供基础 C 异常表示形式）的构造函数和一个按位复制构造函数。  下面是 C 异常包装器类的一个可能的实现：  
  
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
  
 若要使用此类，请安装每次引发 C 异常时由内部异常处理机制调用的自定义 C 异常转换函数。  在转换函数中，您可能引发可由适当匹配的 C\+\+ **catch** 处理程序捕获的任意类型的异常（可能是 `SE_Exception` 类型，或派生自 `SE_Exception` 的类类型）。  转换函数可能直接返回，这表示它没有处理异常。  如果转换功能本身引起了 C 异常，则会调用 [terminate](../c-runtime-library/reference/terminate-crt.md)。  
  
 若要指定自定义转换函数，请使用您的转换函数的名称作为 [\_set\_se\_translator](../c-runtime-library/reference/set-se-translator.md) 的单一参数来调用它。  您编写的转换函数对具有 **try** 块的堆栈上的每个函数调用调用一次。  没有默认转换函数；如果您未通过调用 `_set_se_translator` 来指定一个，C 异常只能由省略号 **catch** 处理程序捕获。  
  
## 示例  
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
  
  **In trans\_func.**  
**In finally**  
**Caught a \_\_try exception with SE\_Exception.**  
**nSE \= 0xc0000094**   
## 请参阅  
 [混合 C（结构化）和 C\+\+ 异常](../cpp/mixing-c-structured-and-cpp-exceptions.md)