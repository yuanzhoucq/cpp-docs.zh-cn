---
title: "请尝试、 throw 和 catch 语句 （c + +） |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- catch_cpp
- try_cpp
- throw_cpp
dev_langs:
- C++
helpviewer_keywords:
- catch keyword [C++]
- keywords [C++], exception handling
- C++ exception handling, statement syntax
- try-catch keyword [C++], about try-catch exception handling
- throw keyword [C++]
- try-catch keyword [C++]
- try-catch keyword [C++], exception handling
- throwing exceptions, throw keyword
- try-catch keyword [C++], throw keyword [C++]s
- throwing exceptions, implementing C++ exception handling
- throwing exceptions
- throw keyword [C++], throw() vs. throw(...)
ms.assetid: 15e6a87b-b8a5-4032-a7ef-946c644ba12a
caps.latest.revision: 24
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 6ffef5f51e57cf36d5984bfc43d023abc8bc5c62
ms.openlocfilehash: 89db418a92239460379d1ea41d2d49a8073095c2
ms.contentlocale: zh-cn
ms.lasthandoff: 09/25/2017

---
# <a name="try-throw-and-catch-statements-c"></a>try、throw 和 catch 语句 (C++)
若要在 C++ 中实现异常处理，你可以使用 `try`、`throw` 和 `catch` 表达式。  
  
 首先，使用 `try` 块将可能引发异常的一个或多个语句封闭起来。  
  
 `throw` 表达式发出信号，异常条件（通常是错误）已在 `try` 块中发生。 你可以使用任何类型的对象作为 `throw` 表达式的操作数。 该对象一般用于传达有关错误的信息。 在大多数情况下，我们建议你使用[std:: exception](../standard-library/exception-class.md)类或在标准库中定义的派生类之一。 如果其中的类不合适，建议你从 `std::exception` 派生自己的异常类。  
  
 若要处理可能引发的异常，请在 `catch` 块之后立即实现一个或多个 `try` 块。 每个 `catch` 块指定它能处理的异常类型。  
  
 以下示例将显示 `try` 块及其处理程序。 假设 `GetNetworkResource()` 通过网络连接获取数据，并且两个异常类型是从 `std::exception` 派生的用户定义的类。 请注意，异常由 `const` 语句中的 `catch` 引用捕获。 我们建议你通过值引发异常并通过常数引用将其捕获。  
  
## <a name="example"></a>示例  
  
```  
  
MyData md;  
try {  
   // Code that could throw an exception  
   md = GetNetworkResource();  
}  
catch (const networkIOException& e) {  
   // Code that executes when an exception of type  
   // networkIOException is thrown in the try block  
   // ...  
   // Log error message in the exception object  
   cerr << e.what();  
}  
catch (const myDataFormatException& e) {  
   // Code that handles another exception type  
   // ...  
   cerr << e.what();  
}  
  
// The following syntax shows a throw expression  
MyData GetNetworkResource()  
{  
   // ...  
   if (IOSuccess == false)  
      throw networkIOException("Unable to connect");  
   // ...  
   if (readError)  
      throw myDataFormatException("Format error");   
   // ...  
}  
```  
  
## <a name="remarks"></a>备注  
 `try` 子句后的代码是代码的受保护部分。 `throw`表达式*引发*-即，引发-异常。 `catch` 子句后的代码块是异常处理程序。 这是处理程序，*捕获*如果引发的异常中的类型`throw`和`catch`表达式是兼容。 有关用于管理中的类型匹配规则的列表`catch`块，请参阅[如何 Catch 块计算](../cpp/how-catch-blocks-are-evaluated-cpp.md)。 如果 `catch` 语句指定省略号 (...) 而非类型，`catch` 块将处理每种类型的异常。 使用编译[/EHa](../build/reference/eh-exception-handling-model.md)选项，这些错误可能包括 C 结构化异常和系统生成或应用程序生成的异步异常，例如内存保护，通过零除和浮点型冲突. 由于 `catch` 块按编程顺序处理以查找匹配类型，所以尽量不要使用省略号处理程序来处理关联的 `try` 块。 请谨慎使用 `catch(...)`；除非 catch 块知道如何处理捕获的特定异常，否则禁止程序继续执行。 `catch(...)` 块一般用于在程序停止执行前记录错误和执行特殊的清理工作。  
  
 没有操作数的 `throw` 表达式将重新引发当前正在处理的异常。 我们建议在重新引发异常时采用该形式，是因为这将保留原始异常的多态类型信息。 此类表达式只应在 `catch` 处理程序中或从 `catch` 处理程序调用的函数中使用。 重新引发的异常对象是原始异常对象，而不是副本。  
  
```  
try {  
   throw CSomeOtherException();  
}  
catch(...) {  
   // Catch all exceptions - dangerous!!!  
   // Respond (perhaps only partially) to the exception, then  
   // re-throw to pass the exception to some other handler  
   // ...  
   throw;  
}  
```  
  
## <a name="see-also"></a>另请参阅  
 [C + + 异常处理](../cpp/cpp-exception-handling.md)   
 [关键字](../cpp/keywords-cpp.md)   
 [未处理的 c + + 异常](../cpp/unhandled-cpp-exceptions.md)   
 [__uncaught_exception](../c-runtime-library/reference/uncaught-exception.md)
