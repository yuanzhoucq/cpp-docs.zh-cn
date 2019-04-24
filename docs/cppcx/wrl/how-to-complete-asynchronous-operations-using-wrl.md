---
title: 如何：使用 WRL 完成异步操作
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 02173eae-731b-49bc-b412-f1f69388b99d
ms.openlocfilehash: 09c341e5e3d4f6007d5d5f66b7c06e1f0af5a65c
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/18/2019
ms.locfileid: "59040220"
---
# <a name="how-to-complete-asynchronous-operations-using-wrl"></a>如何：使用 WRL 完成异步操作

本文档演示如何使用 Windows 运行时C++模板库 (WRL) 启动异步操作并在操作完成时执行工作。

本文档演示两个示例。 第一个示例将启动异步计时器，并等待计时器过期。 在此示例中，在创建计时器对象时指定的异步操作。 第二个示例运行后台辅助线程。 此示例演示如何使用返回的 Windows 运行时方法`IAsyncInfo`接口。 [回调](callback-function-wrl.md)函数是这两个示例的重要组成部分，因为它可以让管理员指定事件处理程序以处理异步操作的结果。

创建组件的实例，并检索属性值的更多基础示例，请参阅[如何：激活和使用 Windows 运行时组件](how-to-activate-and-use-a-windows-runtime-component-using-wrl.md)。

> [!TIP]
> 这些示例使用 lambda 表达式来定义回调。 此外可以使用函数对象 （函子） 函数指针或[std:: function](../../standard-library/function-class.md)对象。 有关详细信息C++lambda 表达式，请参阅[Lambda 表达式](../../cpp/lambda-expressions-in-cpp.md)。

## <a name="example-working-with-a-timer"></a>示例:使用计时器

以下步骤启动异步计时器，并等待计时器过期。 以下是完整的示例。

> [!WARNING]
> 虽然通常使用 Windows 运行时C++模板库在通用 Windows 平台 (UWP) 应用中，此示例使用一个控制台应用程序是为了进行说明。 函数如`wprintf_s`UWP 应用中不可用。 有关类型和可以在 UWP 应用中使用的函数的详细信息，请参阅[通用 Windows 平台应用中不支持的 CRT 函数](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md)并[Win32 和 COM 适用于 UWP 应用](/uwp/win32-and-com/win32-and-com-for-uwp-apps)。

1. 包括 (`#include`) 所需 Windows 运行时，Windows 运行时的任何C++模板库，或C++标准库标头。

   [!code-cpp[wrl-consume-async#2](../codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_1.cpp)]

   `Windows.System.Threading.h` 声明使用异步计时器所需的类型。

   我们建议您在 .cpp 文件中使用 `using namespace` 指令使代码更具可读性。

2. 初始化 Windows 运行时。

   [!code-cpp[wrl-consume-async#3](../codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_2.cpp)]

3. 创建的激活工厂`ABI::Windows::System::Threading::IThreadPoolTimer`接口。

   [!code-cpp[wrl-consume-async#4](../codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_3.cpp)]

   Windows 运行时使用完全限定的名称来标识类型。 `RuntimeClass_Windows_System_Threading_ThreadPoolTimer`参数是由 Windows 运行时提供，包含所需的运行时类名称的字符串。

4. 创建[事件](event-class-wrl.md)同步主应用程序的计时器回调的对象。

   [!code-cpp[wrl-consume-async#5](../codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_4.cpp)]

   > [!NOTE]
   > 此事件是有关仅作为控制台应用程序的一部分的演示。 此示例使用事件来确保此应用退出前完成的异步操作。 在大多数应用中，您通常不等待异步操作完成。

5. 创建`IThreadPoolTimer`对象，它将在两秒后过期。 使用`Callback`函数来创建事件处理程序 (`ABI::Windows::System::Threading::ITimerElapsedHandler`对象)。

   [!code-cpp[wrl-consume-async#6](../codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_5.cpp)]

6. 将消息打印到控制台并等待要完成的计时器回调。 所有 `ComPtr` 和 RAII 对象都离开范围并自动释放。

   [!code-cpp[wrl-consume-async#7](../codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_6.cpp)]

下面是完整的示例：

[!code-cpp[wrl-consume-async#1](../codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_7.cpp)]

### <a name="compiling-the-code"></a>编译代码

若要编译代码，将其复制然后将其粘贴到 Visual Studio 项目中，或将其粘贴在文件中名为`wrl-consume-async.cpp`然后在 Visual Studio 命令提示符窗口中运行以下命令。

`cl.exe wrl-consume-async.cpp runtimeobject.lib`

## <a name="example-working-with-a-background-thread"></a>示例:使用后台线程

以下步骤启动工作线程，并定义由该线程执行的操作。 以下是完整的示例。

> [!TIP]
> 此示例演示如何使用`ABI::Windows::Foundation::IAsyncAction`接口。 可以将此模式应用于实现任何接口`IAsyncInfo`: `IAsyncAction`， `IAsyncActionWithProgress`， `IAsyncOperation`，和`IAsyncOperationWithProgress`。

1. 包括 (`#include`) 所需 Windows 运行时，Windows 运行时的任何C++模板库，或C++标准库标头。

   [!code-cpp[wrl-consume-asyncOp#2](../codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_8.cpp)]

   Windows.System.Threading.h 声明使用工作线程所需的类型。

   我们建议你使用`using namespace`指令使代码更具可读性.cpp 文件中。

2. 初始化 Windows 运行时。

   [!code-cpp[wrl-consume-asyncOp#3](../codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_9.cpp)]

3. 创建的激活工厂`ABI::Windows::System::Threading::IThreadPoolStatics`接口。

   [!code-cpp[wrl-consume-asyncOp#4](../codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_10.cpp)]

4. 创建[事件](event-class-wrl.md)同步完成的工作线程到主应用程序的对象。

   [!code-cpp[wrl-consume-asyncOp#5](../codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_11.cpp)]

   > [!NOTE]
   > 此事件是有关仅作为控制台应用程序的一部分的演示。 此示例使用事件来确保此应用退出前完成的异步操作。 在大多数应用中，您通常不等待异步操作完成。

5. 调用`IThreadPoolStatics::RunAsync`方法来创建工作线程。 使用`Callback`函数来定义操作。

   [!code-cpp[wrl-consume-asyncOp#6](../codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_12.cpp)]

   `IsPrime`函数定义中后面的完整示例。

6. 将消息打印到控制台并等待线程完成。 所有 `ComPtr` 和 RAII 对象都离开范围并自动释放。

   [!code-cpp[wrl-consume-asyncOp#7](../codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_13.cpp)]

下面是完整的示例：

[!code-cpp[wrl-consume-asyncOp#1](../codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_14.cpp)]

### <a name="compiling-the-code"></a>编译代码

若要编译代码，将其复制然后将其粘贴到 Visual Studio 项目中，或将其粘贴在文件中名为`wrl-consume-asyncOp.cpp`，然后运行以下命令中**Visual Studio 命令提示符**窗口。

`cl.exe wrl-consume-asyncOp.cpp runtimeobject.lib`

## <a name="see-also"></a>请参阅

[Windows 运行时 C++ 模板库 (WRL)](windows-runtime-cpp-template-library-wrl.md)