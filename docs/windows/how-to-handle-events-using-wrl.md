---
title: "如何：使用 WRL 处理事件 | Microsoft Docs"
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
ms.assetid: 1c77543f-7b0c-4a94-93bf-e3225885ed76
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 如何：使用 WRL 处理事件
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

文档演示如何使用 [!INCLUDE[cppwrl](../windows/includes/cppwrl_md.md)]（[!INCLUDE[cppwrl_short](../windows/includes/cppwrl_short_md.md)]） 订阅和处理[!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)] 对象的事件。  
  
 有关创建一个组件实例并检索属性值的一种更简单的示例，请参见 [如何：激活和使用 Windows 运行时组件](../windows/how-to-activate-and-use-a-windows-runtime-component-using-wrl.md)。  
  
## 订阅和处理事件  
 以下步骤开始 `ABI::Windows::System::Threading::IDeviceWatcher` 对象，并监视。使用事件处理程序将继续运行。  如果设备添加，移除或更改时，`IDeviceWatcher` 接口允许您异步或设备枚举，在后台，并接收通知。  [回拨](../windows/callback-function-windows-runtime-cpp-template-library.md) 函数是该示例的一个重要组成部分，因为它使得指定处理后台操作结果的事件处理程序。  下面是完整的示例。  
  
> [!WARNING]
>  尽管可以在 [!INCLUDE[win8_appname_long](../build/includes/win8_appname_long_md.md)] 应用通常使用 [!INCLUDE[cppwrl_short](../windows/includes/cppwrl_short_md.md)]，此示例使用图的控制台应用。  函数 \(如 `wprintf_s` \) 从 [!INCLUDE[win8_appname_long](../build/includes/win8_appname_long_md.md)] 应用不可用。  有关在 [!INCLUDE[win8_appname_long](../build/includes/win8_appname_long_md.md)] 应用中使用和函数的类型的更多信息，请参见 [CRT 函数不支持与 \/ZW](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx) 和 [Win32 和 COM 中存储应用的](http://msdn.microsoft.com/library/windows/apps/br205757.aspx)。  
  
1.  包括 \(`#include`\) 任何必需的 [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)]、[!INCLUDE[cppwrl_short](../windows/includes/cppwrl_short_md.md)] 或标准 C\+\+ 库标头。  
  
     [!CODE [wrl-consume-event#2](../CodeSnippet/VS_Snippets_Misc/wrl-consume-event#2)]  
  
     Windows.Devices.Enumeration.h 声明需要枚举的设备类型。  
  
     我们建议您在 .cpp 文件中使用 `using namespace` 指令使代码更具可读性。  
  
2.  声明应用局部变量。  此示例枚举保持的设备和注册标记数的计数。使从事件之后取消订阅。  
  
     [!CODE [wrl-consume-event#7](../CodeSnippet/VS_Snippets_Misc/wrl-consume-event#7)]  
  
3.  初始化 [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)]。  
  
     [!CODE [wrl-consume-event#3](../CodeSnippet/VS_Snippets_Misc/wrl-consume-event#3)]  
  
4.  创建同步枚举过程对主应用程序的对象。[事件](../windows/event-class-windows-runtime-cpp-template-library.md)  
  
     [!CODE [wrl-consume-event#4](../CodeSnippet/VS_Snippets_Misc/wrl-consume-event#4)]  
  
    > [!NOTE]
    >  在控制台应用一部分，此事件只用于演示。  此示例使用事件以确保可操作完成，在应用之前退出。  在大多数应用，通常不可在等待操作完成。  
  
5.  创建接口的一个活动 `IDeviceWatcher` 工厂。  
  
     [!CODE [wrl-consume-event#5](../CodeSnippet/VS_Snippets_Misc/wrl-consume-event#5)]  
  
     [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)] 使用完全限定的名称标识一类型。  `RuntimeClass_Windows_Devices_Enumeration_DeviceInformation` 参数是包含 [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)] 提供并需的运行时类名称的字符串。  
  
6.  创建 `IDeviceWatcher` 对象。  
  
     [!CODE [wrl-consume-event#6](../CodeSnippet/VS_Snippets_Misc/wrl-consume-event#6)]  
  
7.  使用 `Callback` 函数订阅 `Added`、`EnumerationCompleted`和 `Stopped` 事件。  
  
     [!CODE [wrl-consume-event#8](../CodeSnippet/VS_Snippets_Misc/wrl-consume-event#8)]  
  
     `Added` 事件处理程序递增计数枚举的设备。  在十设备找到后停止，它枚举过程。  
  
     `Stopped` 事件处理程序移除事件处理程序并将事件完成。  
  
     `EnumerationCompleted` 事件处理程序会停止枚举过程。  如果小于，许多设备，我们有处理此事件。  
  
    > [!TIP]
    >  此示例使用 lambda 表达式定义回调。  也可以使用中与函数对象 \(functor\)，函数指针或 [std::function](../standard-library/function-class.md) 对象。  有关 lambda 表达式的更多信息，请参见 [lambda 表达式](../cpp/lambda-expressions-in-cpp.md)。  
  
8.  开始枚举过程。  
  
     [!CODE [wrl-consume-event#9](../CodeSnippet/VS_Snippets_Misc/wrl-consume-event#9)]  
  
9. 等待完成枚举过程然后打印消息。  所有 `ComPtr` 和 RAII 对象都离开范围并自动释放。  
  
     [!CODE [wrl-consume-event#10](../CodeSnippet/VS_Snippets_Misc/wrl-consume-event#10)]  
  
 这是完整示例:  
  
 [!CODE [wrl-consume-event#1](../CodeSnippet/VS_Snippets_Misc/wrl-consume-event#1)]  
  
## 编译代码  
 若要编译代码，请复制代码并将其粘贴到  项目中或一个名为 parallel\-matrix\-multiply.cpp 的文件中，然后在命令提示符窗口中运行以下命令。  
  
 **cl.exe wrl\-consume\-events.cpp runtimeobject.lib**  
  
## 请参阅  
 [Windows 运行时 C\+\+ 模板库 \(WRL\)](../windows/windows-runtime-cpp-template-library-wrl.md)