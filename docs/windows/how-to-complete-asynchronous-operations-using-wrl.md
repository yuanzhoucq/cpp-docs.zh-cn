---
title: "如何：使用 WRL 完成异步操作 | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
dev_langs: 
  - "C++"
ms.assetid: 02173eae-731b-49bc-b412-f1f69388b99d
caps.latest.revision: 13
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 如何：使用 WRL 完成异步操作
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

文档演示如何使用 [!INCLUDE[cppwrl](../windows/includes/cppwrl_md.md)] \([!INCLUDE[cppwrl_short](../windows/includes/cppwrl_short_md.md)]\) 启动异步操作并在操作完成时执行工作。  
  
 此文档显示两个示例。  第一个示例开始异步的计时器并等待计时器过期。  在此示例中，在创建对象时，只需指定异步操作。  第二个示例运行在后台工作的线程。  此示例演示如何使用 [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)] 方法返回 `IAsyncInfo` 接口。  [Callback](../windows/callback-function-windows-runtime-cpp-template-library.md) 函数是两个示例的一个重要部分，因为它使他们指定事件处理程序处理异步操作结果。  
  
 有关创建一个组件实例并检索属性值的一种更简单的示例，请参见 [如何：激活和使用 Windows 运行时组件](../windows/how-to-activate-and-use-a-windows-runtime-component-using-wrl.md)。  
  
> [!TIP]
>  这些示例使用 lambda 表达式定义回调。  也可以使用中与函数对象 \(functor\)，函数指针或 [std::function](../standard-library/function-class.md) 对象。  有关 C\+\+ lambda 表达式的更多信息，请参见 [lambda 表达式](../cpp/lambda-expressions-in-cpp.md)。  
  
## 示例：使用计时器的使用  
 以下步骤开始异步的计时器并等待计时器过期。  下面是完整的示例。  
  
> [!WARNING]
>  尽管可以在 [!INCLUDE[win8_appname_long](../build/includes/win8_appname_long_md.md)] 应用通常使用 [!INCLUDE[cppwrl_short](../windows/includes/cppwrl_short_md.md)]，此示例使用图的控制台应用。  函数 \(如 `wprintf_s` \) 从 [!INCLUDE[win8_appname_long](../build/includes/win8_appname_long_md.md)] 应用不可用。  有关在 [!INCLUDE[win8_appname_long](../build/includes/win8_appname_long_md.md)] 应用中使用和函数的类型的更多信息，请参见 [CRT 函数不支持 \/ZW](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx) 和 [Win32 和 COM 中存储应用的](http://msdn.microsoft.com/library/windows/apps/br205757.aspx)。  
  
1.  包括 \(`#include`\) 任何必需的 [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)]、[!INCLUDE[cppwrl_short](../windows/includes/cppwrl_short_md.md)] 或标准 C\+\+ 库标头。  
  
     [!code-cpp[wrl-consume-async#2](../windows/codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_1.cpp)]  
  
     Windows.System.Threading.h 声明异步计时器需要的类型。  
  
     我们建议您在 .cpp 文件中使用 `using namespace` 指令使代码更具可读性。  
  
2.  初始化 [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)]。  
  
     [!code-cpp[wrl-consume-async#3](../windows/codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_2.cpp)]  
  
3.  创建接口的一个活动 `ABI::Windows::System::Threading::IThreadPoolTimer` 工厂。  
  
     [!code-cpp[wrl-consume-async#4](../windows/codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_3.cpp)]  
  
     [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)] 使用完全限定的名称标识一类型。  `RuntimeClass_Windows_System_Threading_ThreadPoolTimer` 参数是包含 [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)] 提供并需的运行时类名称的字符串。  
  
4.  创建[事件](../windows/event-class-windows-runtime-cpp-template-library.md)对象，同步主应用程序的 Timer 回调。  
  
     [!code-cpp[wrl-consume-async#5](../windows/codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_4.cpp)]  
  
    > [!NOTE]
    >  在控制台应用一部分，此事件只用于演示。  此示例使用事件以确保可操作完成，在应用之前退出。  在大多数应用，通常不可在等待操作完成。  
  
5.  创建在两秒后过期的 `IThreadPoolTimer` 对象。  使用 `Callback` 函数创建事件处理程序 \( `ABI::Windows::System::Threading::ITimerElapsedHandler` 对象\)。  
  
     [!code-cpp[wrl-consume-async#6](../windows/codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_5.cpp)]  
  
6.  将消息打印到控制台并等待计时器回调完成。  所有 `ComPtr` 和 RAII 对象都离开范围并自动释放。  
  
     [!code-cpp[wrl-consume-async#7](../windows/codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_6.cpp)]  
  
 这是完整示例:  
  
 [!code-cpp[wrl-consume-async#1](../windows/codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_7.cpp)]  
  
### 编译代码  
 若要编译代码，请复制代码并将其粘贴到 `wrl-consume-async.cpp` 项目中或一个名为 parallel\-matrix\-multiply.cpp 的文件中，然后在命令提示符窗口中运行以下命令。  
  
 **cl.exe wrl\-consume\-async.cpp runtimeobject.lib**  
  
## 示例：用后台线程处理  
 以下步骤启动辅助线程和定义该线程执行的操作。  下面是完整的示例。  
  
> [!TIP]
>  此示例演示如何使用 `ABI::Windows::Foundation::IAsyncAction` 接口工作。  可以将此模式应用与所有的接口实现 `IAsyncInfo`: `IAsyncAction`、`IAsyncActionWithProgress`、`IAsyncOperation`和 `IAsyncOperationWithProgress`。  
  
1.  包括 \(`#include`\) 任何必需的 [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)]、[!INCLUDE[cppwrl_short](../windows/includes/cppwrl_short_md.md)] 或标准 C\+\+ 库标头。  
  
     [!code-cpp[wrl-consume-asyncOp#2](../windows/codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_8.cpp)]  
  
     Windows.System.Threading.h 声明需要辅助线程使用的类型。  
  
     我们建议您在 .cpp 文件中使用 `using namespace` 指令使代码更具可读性。  
  
2.  初始化 [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)]。  
  
     [!code-cpp[wrl-consume-asyncOp#3](../windows/codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_9.cpp)]  
  
3.  创建接口的一个活动 `ABI::Windows::System::Threading::IThreadPoolStatics` 工厂。  
  
     [!code-cpp[wrl-consume-asyncOp#4](../windows/codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_10.cpp)]  
  
4.  创建[事件](../windows/event-class-windows-runtime-cpp-template-library.md)对象同步对主应用程序的工作线程。  
  
     [!code-cpp[wrl-consume-asyncOp#5](../windows/codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_11.cpp)]  
  
    > [!NOTE]
    >  在控制台应用一部分，此事件只用于演示。  此示例使用事件以确保可操作完成，在应用之前退出。  在大多数应用，通常不可在等待操作完成。  
  
5.  调用 `IThreadPoolStatics::RunAsync` 方法创建辅助线程。  使用 `Callback` 函数定义操作。  
  
     [!code-cpp[wrl-consume-asyncOp#6](../windows/codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_12.cpp)]  
  
     `IsPrime` 函数在如下的完整示例中定义。  
  
6.  将消息打印到控制台并等待线程完成。  所有 `ComPtr` 和 RAII 对象都离开范围并自动释放。  
  
     [!code-cpp[wrl-consume-asyncOp#7](../windows/codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_13.cpp)]  
  
 这是完整示例:  
  
 [!code-cpp[wrl-consume-asyncOp#1](../windows/codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_14.cpp)]  
  
### 编译代码  
 若要编译代码，请复制代码并将其粘贴到 `wrl-consume-asyncOp.cpp` 项目中或一个名为 parallel\-matrix\-multiply.cpp 的文件中，然后在命令提示符窗口中运行以下命令。  
  
 **cl.exe wrl\-consume\-asyncOp.cpp runtimeobject.lib**  
  
## 请参阅  
 [Windows 运行时 C\+\+ 模板库 \(WRL\)](../windows/windows-runtime-cpp-template-library-wrl.md)