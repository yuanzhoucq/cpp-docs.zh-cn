---
title: 如何： 完成异步操作，使用 WRL |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
ms.assetid: 02173eae-731b-49bc-b412-f1f69388b99d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: fff0a6e98dd6fdd28b1fbc2e9146d5b68975e0f0
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/08/2018
---
# <a name="how-to-complete-asynchronous-operations-using-wrl"></a>如何：使用 WRL 完成异步操作
本文档演示如何使用 Windows 运行时 c + + 模板库 (WRL) 来启动异步操作并在操作完成时执行工作。  
  
 本文档显示两个示例。 第一个示例将启动异步计时器，并等待计时器过期。 在此示例中，在创建计时器对象时指定的异步操作。 第二个示例运行的后台辅助线程。 此示例演示如何使用返回的 Windows 运行时方法`IAsyncInfo`接口。 [回调](../windows/callback-function-windows-runtime-cpp-template-library.md)函数是这两个示例的重要组成部分，因为它使他们能够指定事件处理程序来处理异步操作的结果。  
  
 有关更多基础示例，创建组件的实例，并检索属性值的说明，请参阅[How to： 激活和使用 Windows 运行时组件](../windows/how-to-activate-and-use-a-windows-runtime-component-using-wrl.md)。  
  
> [!TIP]
>  这些示例使用 lambda 表达式来定义回调。 你还可以使用函数对象 （函子），函数指针或[std:: function](../standard-library/function-class.md)对象。 有关 c + + lambda 表达式的详细信息，请参阅[Lambda 表达式](../cpp/lambda-expressions-in-cpp.md)。  
  
## <a name="example-working-with-a-timer"></a>示例： 使用计时器  
 以下步骤启动异步计时器，并等待计时器过期。 以下是完整的示例。  
  
> [!WARNING]
>  虽然通常使用 Windows 运行时 c + + 模板库中的通用 Windows 平台 (UWP) 应用，但此示例是为了进行说明使用控制台应用程序。 函数如`wprintf_s`UWP 应用中不可用。 有关类型和可以在 UWP 应用中使用的函数的详细信息，请参阅[通用 Windows 平台应用中不支持的 CRT 函数](../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md)和[Win32 和 COM 适用于 UWP 应用](/uwp/win32-and-com/win32-and-com-for-uwp-apps)。  
  
1.  包括 (`#include`) 任何必需的 Windows 运行时、 Windows 运行时 c + + 模板库或 c + + 标准库头文件。  
  
     [!code-cpp[wrl-consume-async#2](../windows/codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_1.cpp)]  
  
     Windows.System.Threading.h 声明都需要使用异步计时器的类型。  
  
     我们建议您在 .cpp 文件中使用 `using namespace` 指令使代码更具可读性。  
  
2.  初始化 Windows 运行时。  
  
     [!code-cpp[wrl-consume-async#3](../windows/codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_2.cpp)]  
  
3.  创建有关的激活工厂`ABI::Windows::System::Threading::IThreadPoolTimer`接口。  
  
     [!code-cpp[wrl-consume-async#4](../windows/codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_3.cpp)]  
  
     Windows 运行时使用完全限定名称来标识类型。 `RuntimeClass_Windows_System_Threading_ThreadPoolTimer`参数是由 Windows 运行时提供且包含所需的运行时类名称的字符串。  
  
4.  创建[事件](../windows/event-class-windows-runtime-cpp-template-library.md)同步主应用程序的计时器回调的对象。  
  
     [!code-cpp[wrl-consume-async#5](../windows/codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_4.cpp)]  
  
    > [!NOTE]
    >  此事件是有关仅作为控制台应用程序的一部分的演示。 此示例使用事件来确保在应用程序退出前完成的异步操作。 在大多数应用中，你通常不等待异步操作完成。  
  
5.  创建`IThreadPoolTimer`在两个秒后过期的对象。 使用`Callback`函数来创建事件处理程序 (`ABI::Windows::System::Threading::ITimerElapsedHandler`对象)。  
  
     [!code-cpp[wrl-consume-async#6](../windows/codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_5.cpp)]  
  
6.  将消息打印到控制台，并等待完成的计时器回调。 所有 `ComPtr` 和 RAII 对象都离开范围并自动释放。  
  
     [!code-cpp[wrl-consume-async#7](../windows/codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_6.cpp)]  
  
 下面是完整的示例：  
  
 [!code-cpp[wrl-consume-async#1](../windows/codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_7.cpp)]  
  
### <a name="compiling-the-code"></a>编译代码  
 若要编译代码，将其复制，然后将其粘贴到 Visual Studio 项目中，或将其粘贴在文件中名为`wrl-consume-async.cpp`然后在 Visual Studio 命令提示符窗口中运行以下命令。  
  
 **cl.exe wrl 使用 async.cpp runtimeobject.lib**  
  
## <a name="example-working-with-a-background-thread"></a>示例： 使用后台线程  
 以下步骤启动的工作线程，并定义由该线程执行的操作。 以下是完整的示例。  
  
> [!TIP]
>  此示例演示如何使用`ABI::Windows::Foundation::IAsyncAction`接口。 你可以将此模式应用于实现任何接口`IAsyncInfo`: `IAsyncAction`， `IAsyncActionWithProgress`， `IAsyncOperation`，和`IAsyncOperationWithProgress`。  
  
1.  包括 (`#include`) 任何必需的 Windows 运行时、 Windows 运行时 c + + 模板库或 c + + 标准库头文件。  
  
     [!code-cpp[wrl-consume-asyncOp#2](../windows/codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_8.cpp)]  
  
     Windows.System.Threading.h 声明都需要使用一个工作线程的类型。  
  
     我们建议你使用`using namespace`指令使代码更具可读性.cpp 文件中。  
  
2.  初始化 Windows 运行时。  
  
     [!code-cpp[wrl-consume-asyncOp#3](../windows/codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_9.cpp)]  
  
3.  创建有关的激活工厂`ABI::Windows::System::Threading::IThreadPoolStatics`接口。  
  
     [!code-cpp[wrl-consume-asyncOp#4](../windows/codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_10.cpp)]  
  
4.  创建[事件](../windows/event-class-windows-runtime-cpp-template-library.md)同步到主应用程序工作线程完成的对象。  
  
     [!code-cpp[wrl-consume-asyncOp#5](../windows/codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_11.cpp)]  
  
    > [!NOTE]
    >  此事件是有关仅作为控制台应用程序的一部分的演示。 此示例使用事件来确保在应用程序退出前完成的异步操作。 在大多数应用中，你通常不等待异步操作完成。  
  
5.  调用`IThreadPoolStatics::RunAsync`方法来创建工作线程。 使用`Callback`函数来定义操作。  
  
     [!code-cpp[wrl-consume-asyncOp#6](../windows/codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_12.cpp)]  
  
     `IsPrime`在下面的完整示例中定义函数。  
  
6.  将消息打印到控制台，并等待要完成的线程。 所有 `ComPtr` 和 RAII 对象都离开范围并自动释放。  
  
     [!code-cpp[wrl-consume-asyncOp#7](../windows/codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_13.cpp)]  
  
 下面是完整的示例：  
  
 [!code-cpp[wrl-consume-asyncOp#1](../windows/codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_14.cpp)]  
  
### <a name="compiling-the-code"></a>编译代码  
 若要编译代码，将其复制，然后将其粘贴到 Visual Studio 项目中，或将其粘贴在文件中名为`wrl-consume-asyncOp.cpp`然后在 Visual Studio 命令提示符窗口中运行以下命令。  
  
 **cl.exe wrl 使用 asyncOp.cpp runtimeobject.lib**  
  
## <a name="see-also"></a>请参阅  
 [Windows 运行时 C++ 模板库 (WRL)](../windows/windows-runtime-cpp-template-library-wrl.md)
