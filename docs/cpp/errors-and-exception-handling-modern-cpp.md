---
title: "错误和异常处理（现代 C++） | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
ms.assetid: a6c111d0-24f9-4bbb-997d-3db4569761b7
caps.latest.revision: 19
caps.handback.revision: 19
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 错误和异常处理（现代 C++）
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

在现代 c + +，在大多数情况下，报告和处理逻辑错误和运行时错误的首选的方式是使用异常。 当堆栈可能包含检测到错误的函数具有要知道如何处理它的上下文的函数之间的多个函数调用时，也是如此。 异常为检测到错误，无法传递调用堆栈中向上传递信息的代码提供正式的定义完善的方式。  
  
 程序错误数通常分为两类︰ 逻辑错误而引起编程错误，例如，"索引超出范围"错误，而且不受控制的程序员来说，例如，运行时错误"网络服务不可用"错误。 在 C 样式编程中，在 COM 中，错误报告进行管理，通过返回一个值，表示错误代码或特定的功能，状态代码或设置调用方可以根据需要检索每个函数调用以查看是否已报告错误后的全局变量。 例如，COM 编程使用 HRESULT 返回值来传递给调用方的错误，并且 Win32 API 有 GetLastError 函数以检索已报告的调用堆栈的最后一个错误。 在这两种情况下，它由调用方识别的代码，并相应地对它做出响应。 如果调用方不显式处理的错误代码，该程序可能会崩溃而不发出警告，或继续执行用错误的数据并生成错误的结果。  
  
 在现代 c + + 中，异常都被首选以下原因引起的︰  
  
-   异常会强制调用代码以识别出现错误，并处理它。 未经处理的异常停止程序执行。  
  
-   异常跳转到可以处理错误的调用堆栈中的点。 中间函数可以让异常传播。 它们不需要与其他层协调一致。  
  
-   异常堆栈展开机制销毁根据定义完善的规则的作用域中的所有对象后将引发异常。  
  
-   异常实现完全分离之间检测到错误的代码和处理该错误代码。  
  
 以下简化的示例演示引发和捕获异常，c + + 中的必需语法。  
  
```cpp  
  
#include <stdexcept>  
#include <limits>  
#include <iostream>  
  
using namespace std;  
class MyClass  
{  
public:  
   void MyFunc(char c)  
   {  
      if(c < numeric_limits<char>::max())  
         throw invalid_argument("MyFunc argument too large.");  
      //...  
   }  
};  
  
int main()  
{  
   try  
   {  
      MyFunc(256); //cause an exception to throw  
   }  
  
   catch(invalid_argument& e)  
   {  
      cerr << e.what() << endl;  
      return -1;  
   }  
   //...  
   return 0;  
}  
  
```  
  
 在 c + + 异常类似于 C# 和 Java 等语言中。 在 `try` 块，如果引发异常 *引发* 将 *捕获* 通过第一个关联 `catch` 块的类型与匹配的异常。 换而言之，执行将从跳 `throw` 语句 `catch` 语句。 如果找到没有任何可用的 catch 块，则 `std::terminate` 调用并退出程序。 在 c + +，可能会引发任何类型;但是，我们建议您引发派生的类型直接或间接从 `std::exception`。 在前面的示例中，异常类型， [invalid_argument](../standard-library/invalid-argument-class.md), ，标准库中定义 [\< stdexcept>](../standard-library/stdexcept.md) 标头文件。 C + + 未提供，并且不需要， `finally` 块来确保如果引发了异常，释放所有资源。 资源获取即是初始化 (RAII) 习语，使用了智能指针，提供所需的功能的资源清理。 有关详细信息，请参阅 [如何︰ 设计异常安全性](../cpp/how-to-design-for-exception-safety.md)。 有关 c + + 堆栈展开机制的信息，请参阅 [异常和堆栈展开](../cpp/exceptions-and-stack-unwinding-in-cpp.md)。  
  
## <a name="basic-guidelines"></a>基本指南  
 可靠的错误处理是任何编程语言中具有挑战性。 尽管异常提供了多种功能，可支持良好的错误处理，但它们不能为您做的所有工作。 若要实现异常机制的好处，例外情况请记住，设计您的代码。  
  
-   使用断言来检查有应永远不会发生的错误。 使用异常来检查有错误，可能会发生，例如，在公共函数的输入参数验证错误。 有关详细信息，请参阅节 **异常与。断言**。  
  
-   使用异常的代码可处理该错误可能由一个或多个干预的函数调用分隔的代码中检测到错误时。 考虑是否将处理该错误的代码是紧密耦合到检测到它的代码时改为使用性能关键循环中的错误代码。 有关何时不使用异常的详细信息，请参阅 [(NOTINBUILD) 何时不使用异常](http://msdn.microsoft.com/zh-cn/e810df8b-2217-4e81-bae5-02f0a69f1346)。  
  
-   对于每个函数可能会引发或传播异常，提供一个三个异常保证︰ 增强保证、 基本保证或 nothrow (noexcept) 保证。 有关详细信息，请参阅 [如何︰ 设计异常安全性](../cpp/how-to-design-for-exception-safety.md)。  
  
-   通过值引发异常，通过引用捕获它们。 不会捕获您不能处理。 有关详细信息，请参阅 [引发和捕获异常 （c + +） (NOTINBUILD) 准则](http://msdn.microsoft.com/zh-cn/0a9b0a3a-64c5-43f5-a080-fca69b89e839)。  
  
-   不要使用 C + + 11 中弃用的异常规范。 有关详细信息，请参阅节 **异常规范和 noexcept**。  
  
-   适用时，请使用标准库异常类型。 派生自定义异常类型从 [exception 类](../standard-library/exception-class1.md) 层次结构。 有关详细信息，请参阅 [(NOTINBUILD) 如何︰ 使用标准库异常对象](http://msdn.microsoft.com/zh-cn/ad1fb785-ed4e-4d94-8e84-964353aed7b6)。  
  
-   不允许异常从析构函数转义或内存释放函数。  
  
## <a name="exceptions-and-performance"></a>异常和性能  
 异常机制具有很少的性能开销，如果不引发任何异常。 如果引发异常，成本的堆栈遍历和展开是大概相当于函数调用的开销。 附加数据结构所需跟踪后的调用堆栈 `try` 输入块时，和其他说明所需展开堆栈，如果引发了异常。 但是，在大多数情况下，在性能和内存占用量的开销并不重要。 在性能上配置例外的副作用是可能具有重要价值仅在非常受内存限制的系统上或在性能关键循环错误可能会定期进行，并且处理它的代码紧密耦合到其报告的代码。 在任何情况下，不可能知道的异常的实际成本而无需分析和测量。 即使在极少情况下时的成本是很重要，您可以衡量它提高的正确性、 更轻松的可维护性和提供设计良好的异常策略的其他优点。  
  
## <a name="exceptions-vs-assertions"></a>与断言异常  
 异常和断言两种不同机制来检测在程序运行时错误。 使用断言来在不应可从您的代码是否正确，则返回 true 的开发过程中测试条件。 没有任何意义，在该错误指示在代码中必须保持不变，因为使用异常处理此类错误并不表示该程序是否在运行时从恢复的条件。 断言处停止执行该语句，以便您可以检查调试器; 中的程序状态异常将继续从第一个适当的 catch 处理程序的执行。 使用异常来检查可能会在运行时中，即使您的代码正确，例如，"文件找不到"或"内存不足。"的错误条件 您可能想要从这些条件，恢复，即使恢复只输出到日志消息并退出该程序。 始终检查通过使用异常的公共函数的参数。 即使您的函数是错误的您可能没有完全控制用户可能会传递给它的参数。  
  
## <a name="c-exceptions-versus-windows-seh-exceptions"></a>与 Windows SEH 异常的 c + + 异常  
 C 和 c + + 程序可以使用的结构化的异常处理 (SEH) 机制，Windows 操作系统中。 中的概念类似 c + + 异常类似，只不过 SEH 使用 `__try`, ，`__except`, ，和 `__finally` 构造而不是 `try` 和 `catch`。 在 Visual c + +，c + + 异常用于 SEH 实现。 但是，当您编写 c + + 代码，使用 c + + 异常语法。  
  
 有关 SEH 详细信息，请参阅 [结构化异常处理 （C/c + +）](../cpp/structured-exception-handling-c-cpp.md)。  
  
## <a name="exception-specifications-and-noexcept"></a>异常规范和 noexcept  
 异常规范是 c + + 中引入提升以任何方式来指定函数可能引发的异常。 但是，异常规范事实证明，在实践中，有问题，并且 C + + 11 草稿标准中已弃用。 我们建议您不要使用除异常规范 `throw()`, ，指示该异常，允许进行转义的异常。 如果必须使用类型的异常规范 `throw(`*类型*`)`, ，请注意， [!INCLUDE[vcprvc](../build/includes/vcprvc_md.md)] 偏离以某些方式的标准。 有关详细信息，请参阅 [异常规范 （引发）](../cpp/exception-specifications-throw-cpp.md)。  `noexcept` 说明符在 C + + 11 中引入的首选替代为 `throw()`。  
  
## <a name="see-also"></a>另请参阅  
 [如何︰ 异常和非异常代码之间的接口](../cpp/how-to-interface-between-exceptional-and-non-exceptional-code.md)   
 [欢迎回到 c + +](../cpp/welcome-back-to-cpp-modern-cpp.md)   
 [C + + 语言参考](../cpp/cpp-language-reference.md)   
 [C + + 标准库](../standard-library/cpp-standard-library-reference.md)