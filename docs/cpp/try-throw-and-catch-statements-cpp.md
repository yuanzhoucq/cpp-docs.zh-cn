---
title: 请尝试、 throw 和 catch 语句 （C++） |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
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
- throwing exceptions [C++], throw keyword
- try-catch keyword [C++], throw keyword [C++]s
- throwing exceptions [C++], implementing C++ exception handling
- throwing exceptions [C++]
- throw keyword [C++], throw() vs. throw(...)
ms.assetid: 15e6a87b-b8a5-4032-a7ef-946c644ba12a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: dc5480b461a06d84647b7f139b2bd0ccce550dcd
ms.sourcegitcommit: 51f804005b8d921468775a0316de52ad39b77c3e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/02/2018
ms.locfileid: "39462139"
---
# <a name="try-throw-and-catch-statements-c"></a>try、throw 和 catch 语句 (C++)
若要实现 c + + 中的异常处理，您可以使用**尝试**，**引发**，并**捕获**表达式。  
  
 首先，使用**尝试**块包含一个或多个可能引发异常的语句。  
  
 一个**引发**表达式发出信号，异常情况 — 通常是错误 — 中出现**尝试**块。 您可以使用任何类型的对象为操作数**引发**表达式。 该对象一般用于传达有关错误的信息。 在大多数情况下，我们建议你使用[std:: exception](../standard-library/exception-class.md)类或标准库中定义的派生类之一。 如果其中的类不合适，建议你从 `std::exception` 派生自己的异常类。  
  
 若要处理可能引发的异常，实现一个或多个**捕获**块之后立即**尝试**块。 每个**捕获**块指定它能处理的异常的类型。  
  
 此示例演示**尝试**块和其处理程序。 假设 `GetNetworkResource()` 通过网络连接获取数据，并且两个异常类型是从 `std::exception` 派生的用户定义的类。 请注意，通过捕获异常**const**中引用**捕获**语句。 我们建议你通过值引发异常并通过常数引用将其捕获。  
  
## <a name="example"></a>示例  
  
```cpp 
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
 后面的代码**尝试**子句是受保护的代码部分。 **引发**表达式*引发*— 也就是说，将引发 — 异常。 后的代码块**捕获**子句是异常处理程序。 这是处理程序的*捕获*如果引发的异常中的类型**引发**并**捕获**表达式都兼容。 有关用于管理中的类型匹配规则的列表**捕获**块，请参阅[如何 Catch 块计算](../cpp/how-catch-blocks-are-evaluated-cpp.md)。 如果**捕获**语句指定省略号 （...） 而不是类型**捕获**块将处理每种类型的异常。 使用编译[/EHa](../build/reference/eh-exception-handling-model.md)选项，其中可以包括 C 结构化异常和系统生成或应用程序生成的异步异常，例如内存保护、 被零除和浮点冲突. 因为**捕获**块顺序进行处理程序以查找匹配类型，省略号处理程序必须是最后一个处理程序相关联**尝试**块。 请谨慎使用 `catch(...)`；除非 catch 块知道如何处理捕获的特定异常，否则禁止程序继续执行。 `catch(...)` 块一般用于在程序停止执行前记录错误和执行特殊的清理工作。  
  
 一个**引发**具有没有操作数表达式重新引发当前正在处理的异常。 我们建议在重新引发异常时采用该形式，是因为这将保留原始异常的多态类型信息。 此类表达式只应在**捕获**处理程序或在从调用的函数**捕获**处理程序。 重新引发的异常对象是原始异常对象，而不是副本。  
  
```cpp 
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
  
## <a name="see-also"></a>请参阅  
 [C++ 异常处理](../cpp/cpp-exception-handling.md)   
 [关键字](../cpp/keywords-cpp.md)   
 [未处理的 C++ 异常](../cpp/unhandled-cpp-exceptions.md)   
 [__uncaught_exception](../c-runtime-library/reference/uncaught-exception.md)