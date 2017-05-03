---
title: "异常 (C++/CX) | Microsoft Docs"
ms.custom: ""
ms.date: "01/22/2017"
ms.prod: "windows-client-threshold"
ms.technology: ""
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 6cbdc1f1-e4d7-4707-a670-86365146432f
caps.latest.revision: 22
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
caps.handback.revision: 22
---
# 异常 (C++/CX)
[!INCLUDE[cppwrt](../cppcx/includes/cppwrt-md.md)] \([!INCLUDE[cppwrt_short](../cppcx/includes/cppwrt-short-md.md)]\) 中的错误处理基于异常。 从根本上讲，[!INCLUDE[wrt](../cppcx/includes/wrt-md.md)]组件将错误报告为 HRESULT 值。 在 [!INCLUDE[cppwrt_short](../cppcx/includes/cppwrt-short-md.md)]中，这些值将转换为包含 HRESULT 值的强类型异常；在 [!INCLUDE[win81](../cppcx/includes/win81-md.md)] 中，这些值将转换为可通过编程方式访问的字符串说明。  异常作为从 `ref class` 派生的  `Platform::Exception`来实现。`Platform` 命名空间为最常见的 HRESULT 值定义独特的异常类，而所有其他值都通过 `Platform::COMException` 类来报告。 所有异常类都有一个 [Exception::HResult Property](../cppcx/exception-hresult-property.md) 字段，可用于检索原始 HRESULT。 在 [!INCLUDE[win81](../cppcx/includes/win81-md.md)] 中，还可以从调试器中检查用户代码的调用堆栈信息，这些信息可帮助确定异常的根源，即使产生异常的代码不是用 C\+\+ 语言编写的，情况也不例外。  
  
## 异常  
 在你的 C\+\+ 程序中，你可以引发和捕获来自 [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)]操作的异常、派生自 `std::exception` 的异常或用户定义的类型。 仅当 [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)]异常将跨越应用程序二进制接口 \(ABI\) 边界时（例如，当捕获你的异常的代码是使用 JavaScript 编写的时），才必须引发该异常。 当非 [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)] C\+\+ 异常到达 ABI 边界时，该异常转换为 `Platform::FailureException` 异常，后者表示 E\_FAIL HRESULT。 有关 ABI 的更多信息，请参见[用 C\+\+ 创建 Windows 运行时组件](../Topic/Creating%20Windows%20Runtime%20Components%20in%20C++.md)。  
  
 通过使用以下两个构造函数之一可声明 [Platform::Exception](../cppcx/platform-exception-class.md)，这两个构造函数采用 HRESULT 参数或者 HRESULT 参数和 [Platform::String](../cppcx/platform-string-class.md)^ 参数，该参数可跨 ABI 传递到能够处理它的任何 Windows 应用商店应用。 也可以使用两个 [Exception::CreateException 方法](../cppcx/exception-createexception-method.md)重载之一声明异常，这两个方法重载采用 HRESULT 参数或者 HRESULT 参数和 `Platform::String^` 参数。  
  
## 标准异常  
 [!INCLUDE[cppwrt_short](../cppcx/includes/cppwrt-short-md.md)] 支持一组表示典型 HRESULT 错误的标准异常。 每个标准异常从 [Platform::COMException](../cppcx/platform-comexception-class.md) 派生，而 Platform::COMException 从 `Platform::Exception` 派生。 当跨 ABI 边界引发异常时，必须引发一个标准异常。  
  
 不能从 `Platform::Exception` 派生您自己的异常类型。 若要引发自定义异常，请使用用户定义的 HRESULT 构造 `COMException` 对象。  
  
 下表列出了标准异常。  
  
|名称|基础 HRESULT|描述|  
|--------|----------------|--------|  
|COMException|*用户定义的 hresult*|从 COM 方法调用返回无法识别的 HRESULT 时引发。|  
|AccessDeniedException|E\_ACCESSDENIED|被拒绝访问资源或功能时引发。|  
|ChangedStateException|E\_CHANGED\_STATE|在父集合更改后调用集合迭代器或集合视图的方法时引发，从而使方法的结果无效。|  
|ClassNotRegisteredException|REGDB\_E\_CLASSNOTREG|当 COM 类尚未注册时引发。|  
|DisconnectedException|RPC\_E\_DISCONNECTED|当对象与其客户端的连接断开时引发。|  
|FailureException|E\_FAIL|操作失败时引发。|  
|InvalidArgumentException|E\_INVALIDARG|当提供给方法的参数之一无效时引发。|  
|InvalidCastException|E\_NOINTERFACE|当类型无法转换为另一种类型时引发。|  
|NotImplementedException|E\_NOTIMPL|当接口方法尚未在类上实现时引发。|  
|NullReferenceException|E\_POINTER|尝试取消引用空对象引用时引发。|  
|ObjectDisposedException|RO\_E\_CLOSED|对已释放对象执行操作时引发。|  
|OperationCanceledException|E\_ABORT|操作中止时引发。|  
|OutOfBoundsException|E\_BOUNDS|某个操作尝试在有效范围外访问数据时引发。|  
|OutOfMemoryException|E\_OUTOFMEMORY|没有足够内存来完成操作时引发。|  
|WrongThreadException|RPC\_E\_WRONG\_THREAD|当一个线程通过专用于代理对象而不属于该线程单元的接口指针调用时引发。|  
  
## HResult 和 Message 属性  
 所有异常都有一个 [HResult](../cppcx/comexception-hresult-property.md) 属性和一个 [Message](../cppcx/comexception-message-property.md) 属性。[Exception::HResult](../cppcx/exception-hresult-property.md) 属性获取异常的基础数字 HRESULT 值。[Exception::Message](../cppcx/exception-message-property.md) 属性获取系统提供的描述异常的字符串。 在 [!INCLUDE[win8](../cppcx/includes/win8-md.md)] 中，消息仅显示在调试器中，并且是只读的。 这意味着，重新引发异常时将无法对其进行更改。 在 [!INCLUDE[win81](../cppcx/includes/win81-md.md)] 中，可通过编程方式访问消息字符串，并在重新引发异常时提供新的消息。 调试器中还提供了更详细的调用堆栈信息，包括异步方法调用的调用堆栈。  
  
## 示例  
 此示例演示如何为同步操作引发 [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)]异常：  
  
 [!code-cpp[cx_exceptions#01](../snippets/cpp/VS_Snippets_Misc/cx_exceptions/cpp/class1.cpp#01)]  
  
 下一个示例演示如何捕获该异常。  
  
 [!code-cpp[cx_exceptions#02](../snippets/cpp/VS_Snippets_Misc/cx_exceptions/cpp/class1.cpp#02)]  
  
 若要捕捉异步操作期间引发的异常，请使用任务类并添加一个错误处理继续符。 错误处理延续将其他线程上引发的异常封送回调用线程，以便你可以在代码中一个地方处理所有潜在异常。 有关更多信息，请参见[使用 C\+\+ 异步编程](http://msdn.microsoft.com/library/windows/apps/Hh780559.aspx)。  
  
## UnhandledErrorDetected 事件  
 在 [!INCLUDE[win81](../cppcx/includes/win81-md.md)] 中，可订阅 [Windows::ApplicationModel::Core::CoreApplication::UnhandledErrorDetected](http://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.core.coreapplication.unhandlederrordetected.aspx) 静态事件，通过该事件可访问即将关闭进程的未处理的错误。 无论错误源于何处，它都作为与事件参数一起传入的 [Windows::ApplicationModel::Core::UnhandledError](http://msdnstage.redmond.corp.microsoft.com/library/windows/apps/windows.applicationmodel.core.unhandlederror.aspx) 对象到达此处理程序。 对该对象调用 `Propagate` 时，它根据错误代码创建并引发相应类型的 `Platform::*Exception`。 在 catch 块内，可根据需要保存用户状态，然后通过调用 `throw` 让进程终止，或者执行其他操作让程序返回已知的状态。 下面的示例演示了基本模式：  
  
```  
  
// In app.xaml.h:  
void OnUnhandledException(Platform::Object^ sender, Windows::ApplicationModel::Core::UnhandledErrorDetectedEventArgs^ e);  
  
// In app.xaml.cpp  
  
// Subscribe to the event, for example in the app class constructor:  
Windows::ApplicationModel::Core::CoreApplication::UnhandledErrorDetected += ref new EventHandler<UnhandledErrorDetectedEventArgs^>(this, &App::OnUnhandledException);  
  
// Event handler implementation:  
void App::OnUnhandledException(Platform::Object^ sender, Windows::ApplicationModel::Core::UnhandledErrorDetectedEventArgs^ e)  
{  
    auto err = e->UnhandledError;  
  
    if (!err->Handled) //Propagate has not been called on it yet.  
{  
     try  
    {  
        err->Propagate();  
    }  
    // Catch any specific exception types if you know how to handle them  
    catch (AccessDeniedException^ ex)  
    {  
        // TODO: Log error and either take action to recover  
        // or else re-throw exception to continue fail-fast  
    }  
  
}  
  
```  
  
## 备注  
 [!INCLUDE[cppwrt_short](../cppcx/includes/cppwrt-short-md.md)] 不使用 `finally` 子句。  
  
## 请参阅  
 [Visual C\+\+ 语言参考](../cppcx/visual-c-language-reference-c-cx.md)   
 [命名空间参考](../cppcx/namespaces-reference-c-cx.md)