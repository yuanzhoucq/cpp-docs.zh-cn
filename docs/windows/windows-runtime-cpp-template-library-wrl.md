---
title: "Windows 运行时 C++ 模板库 (WRL) | Microsoft Docs"
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
ms.assetid: b915afce-553b-44a7-b8dc-0ab601758eb0
caps.latest.revision: 32
caps.handback.revision: 32
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Windows 运行时 C++ 模板库 (WRL)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

[!INCLUDE[cppwrl](../windows/includes/cppwrl_md.md)] ([!INCLUDE[cppwrl_short](../windows/includes/cppwrl_short_md.md)]) 是一个模板库，提供了一种生成和使用 [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)] 组件的简单方法。  
  
## <a name="benefits"></a>优点  
 利用 [!INCLUDE[cppwrl_short](../windows/includes/cppwrl_short_md.md)] ，你可以更轻松地实现和使用组件对象模型 (COM) 组件。 它提供引用计数这类管理技术来管理对象的生存期，并可通过测试 `HRESULT` 值来确定操作是否成功。 若要成功使用 [!INCLUDE[cppwrl_short](../windows/includes/cppwrl_short_md.md)]，你必须认真遵循这些规则和技术。  
  
 [!INCLUDE[cppwrt](../build/reference/includes/cppwrt_md.md)] ([!INCLUDE[cppwrt_short](../build/reference/includes/cppwrt_short_md.md)]) 是一种高级的、基于语言的 [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)] 组件使用方式。 [!INCLUDE[cppwrl_short](../windows/includes/cppwrl_short_md.md)] 和 [!INCLUDE[cppwrt_short](../build/reference/includes/cppwrt_short_md.md)] 均可替你自动执行管理任务，从而简化 [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)] 的代码编写。  
  
 [!INCLUDE[cppwrl_short](../windows/includes/cppwrl_short_md.md)] 和 [!INCLUDE[cppwrt_short](../build/reference/includes/cppwrt_short_md.md)] 具有不同的优点。 基于以下原因，你可能需要使用 [!INCLUDE[cppwrl_short](../windows/includes/cppwrl_short_md.md)] 而不是 [!INCLUDE[cppwrt_short](../build/reference/includes/cppwrt_short_md.md)]：  
  
-   [!INCLUDE[cppwrl_short](../windows/includes/cppwrl_short_md.md)] 不需要在 [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)]应用程序二进制接口 (ABI) 上添加抽象，从而让你能够控制基础代码，以便更好地创建或使用 [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)] API。  
  
-   [!INCLUDE[cppwrt_short](../build/reference/includes/cppwrt_short_md.md)] 将 COM `HRESULT` 值表示为异常。 如果继承了使用 COM 或不使用异常的基本代码，你可能会发现 [!INCLUDE[cppwrl_short](../windows/includes/cppwrl_short_md.md)] 可以更自然地与 [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)]搭配使用，因为你不必使用异常。  
  
    > [!NOTE]
    >  [!INCLUDE[cppwrl_short](../windows/includes/cppwrl_short_md.md)] 使用 `HRESULT` 值，且不会引发异常。 此外， [!INCLUDE[cppwrl_short](../windows/includes/cppwrl_short_md.md)] 还会使用智能指针和 RAII 模式，以帮助确保在应用程序代码引发异常时正确销毁对象。 有关智能指针和 RAII 的更多信息，请参阅 [智能指针](../cpp/smart-pointers-modern-cpp.md) 和 [对象自己的资源 (RAII)](../cpp/objects-own-resources-raii.md)。  
  
-   [!INCLUDE[cppwrl_short](../windows/includes/cppwrl_short_md.md)] 的用途和设计是由活动模板库 (ATL) 创作而来。活动模板库是一组基于模板的 C++ 类，可以简化编程 COM 对象。 由于 [!INCLUDE[cppwrl_short](../windows/includes/cppwrl_short_md.md)] 使用标准 C++ 包装 [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)]，因此可以更轻松地让许多写入 ATL 的现有 COM 组件与 [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)]进行交互和端口通信。 如果你已经知道 ATL，你可能会发现 [!INCLUDE[cppwrl_short](../windows/includes/cppwrl_short_md.md)] 编程变得更加容易。  
  
## <a name="getting-started"></a>入门  
 以下是一些可帮助你立即开始使用 [!INCLUDE[cppwrl_short](../windows/includes/cppwrl_short_md.md)] 的资源。  
  
 [Windows 运行时库 (WRL)](http://channel9.msdn.com/Events/Windows-Camp/Developing-Windows-8-Metro-style-apps-in-Cpp/The-Windows-Runtime-Library-WRL-)  
 在这个第 9 频道视频中，你可以详细了解 [!INCLUDE[cppwrl_short](../windows/includes/cppwrl_short_md.md)] 如何帮助你编写 [!INCLUDE[win8_appname_long](../build/includes/win8_appname_long_md.md)] 应用，以及如何生成和使用 [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)] 组件。  
  
 [如何︰ 激活和使用 Windows 运行时组件](../windows/how-to-activate-and-use-a-windows-runtime-component-using-wrl.md)  
 演示如何使用 [!INCLUDE[cppwrl_short](../windows/includes/cppwrl_short_md.md)] 初始化 [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)] 以及激活和使用 [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)] 组件。  
  
 [如何︰ 完成异步操作](../windows/how-to-complete-asynchronous-operations-using-wrl.md)  
 演示如何使用 [!INCLUDE[cppwrl_short](../windows/includes/cppwrl_short_md.md)] 启动异步操作并在操作完成时执行工作。  
  
 [如何︰ 处理事件](../windows/how-to-handle-events-using-wrl.md)  
 演示如何使用 [!INCLUDE[cppwrl_short](../windows/includes/cppwrl_short_md.md)] 订阅和处理 [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)] 对象的事件。  
  
 [演练︰ 创建基本 Windows 运行时组件](../windows/walkthrough-creating-a-basic-windows-runtime-component-using-wrl.md)  
 演示如何使用 [!INCLUDE[cppwrl_short](../windows/includes/cppwrl_short_md.md)] 创建将两个数字相加的基本 [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)] 组件。 此外，还会演示如何引发事件，以及如何使用来自使用 JavaScript 的 [!INCLUDE[win8_appname_long](../build/includes/win8_appname_long_md.md)] 应用的组件。  
  
 [演练︰ 创建使用 WRL 和 Media Foundation 的 Windows 应用商店应用程序](../windows/walkthrough-creating-a-windows-store-app-using-wrl-and-media-foundation.md)  
 了解如何创建使用 [!INCLUDE[win8_appname_long](../build/includes/win8_appname_long_md.md)] Microsoft 媒体基础 [的](http://msdn.microsoft.com/library/windows/apps/ms694197)应用。  
  
 [如何︰ 创建传统型 COM 组件](../windows/how-to-create-a-classic-com-component-using-wrl.md)  
 演示如何使用 [!INCLUDE[cppwrl_short](../windows/includes/cppwrl_short_md.md)] 创建基本的 COM 组件，以及从桌面应用程序注册和使用 COM 组件的基本方法。  
  
 [如何︰ 直接实例化 WRL 组件](../windows/how-to-instantiate-wrl-components-directly.md)  
 了解如何使用 [Microsoft::WRL::Make](../windows/make-function.md) 和 [Microsoft::WRL::Details::MakeAndInitialize](../windows/makeandinitialize-function.md) 函数从定义组件的模块实例化组件。  
  
 [如何︰ 使用 winmdidl.exe 和 midlrt.exe 通过窗口元数据创建.h 文件](../windows/use-winmdidl-and-midlrt-to-create-h-files-from-windows-metadata.md)  
 演示如何通过从 .winmd 元数据创建 IDL 文件，使用 WRL 中的自定义 Windows 运行时组件。  
  
 [演练︰ 使用任务和 XML HTTP 请求连接](../parallel/concrt/walkthrough-connecting-using-tasks-and-xml-http-requests.md)  
 演示如何将 [IXMLHTTPRequest2](http://msdn.microsoft.com/zh-cn/bbc11c4a-aecf-4d6d-8275-3e852e309908) 和 [IXMLHTTPRequest2Callback](http://msdn.microsoft.com/zh-cn/aa4b3f4c-6e28-458b-be25-6cce8865fc71) 接口与任务结合使用，以将 HTTP GET 和 POST 请求发送至 [!INCLUDE[win8_appname_long](../build/includes/win8_appname_long_md.md)] 应用中的 Web 服务。  
  
 [必应地图行程优化器示例](http://code.msdn.microsoft.com/Bing-Maps-trip-optimizer-c4e037f7)  
 使用 `HttpRequest` 中定义的类 [演练︰ 连接使用任务和 XML HTTP 请求](../parallel/concrt/walkthrough-connecting-using-tasks-and-xml-http-requests.md) 一套完整的上下文中 [!INCLUDE[win8_appname_long](../build/includes/win8_appname_long_md.md)] 应用程序。  
  
 [使用 c + + 示例中创建 Windows 运行时 DLL 组件](http://code.msdn.microsoft.com/windowsapps/Creating-a-Windows-Runtime-6c399797)  
 演示如何使用 [!INCLUDE[cppwrl_short](../windows/includes/cppwrl_short_md.md)] 创建进程内 DLL 组件，以及如何在 C++/CX、JavaScript 和 C# 中使用它。  
  
 [DirectX 大理石迷宫游戏示例](http://code.msdn.microsoft.com/windowsapps/DirectX-Marble-Maze-Game-e4806345)  
 演示如何使用 [!INCLUDE[cppwrl_short](../windows/includes/cppwrl_short_md.md)] 管理 COM 组件（比如，完整的三维游戏上下文中的 DirectX 和媒体基础）的生存期。  
  
 [从桌面应用程序示例发送 toast 通知](http://code.msdn.microsoft.com/windowsdesktop/Sending-toast-notifications-71e230a2)  
 演示如何在桌面应用程序中将 [!INCLUDE[cppwrl_short](../windows/includes/cppwrl_short_md.md)] 与 toast 通知一起使用。  
  
## <a name="includecppwrlshorttokencppwrlshortmdmd-compared-to-atl"></a>[!INCLUDE[cppwrl_short](../windows/includes/cppwrl_short_md.md)] 与 ATL 比较  
 [!INCLUDE[cppwrl_short](../windows/includes/cppwrl_short_md.md)] 与活动模板库 (ATL) 相似，因为你也可使用它来快速创建小型 COM 对象。 [!INCLUDE[cppwrl_short](../windows/includes/cppwrl_short_md.md)] 和 ATL 之间还存在一些相同的概念，例如在模块中定义对象、显式注册接口，以及使用工厂开始创建对象。 如果你熟悉 ATL，可能就会适应 [!INCLUDE[cppwrl_short](../windows/includes/cppwrl_short_md.md)]。  
  
 [!INCLUDE[cppwrl_short](../windows/includes/cppwrl_short_md.md)] 支持 [!INCLUDE[win8_appname_long](../build/includes/win8_appname_long_md.md)]应用所需的 COM 功能。 因此，它又与 ATL 有所不同，因为它无法直接支持下列 COM 功能：  
  
-   聚合  
  
-   常用实现  
  
-   双重接口 (`IDispatch`)  
  
-   标准枚举器接口  
  
-   连接点  
  
-   分离式接口  
  
-   OLE 嵌入  
  
-   ActiveX 控件  
  
-   COM+  
  
## <a name="concepts"></a>概念  
 [!INCLUDE[cppwrl_short](../windows/includes/cppwrl_short_md.md)] 提供了几个类型来表示几种基本的概念。 以下几节将介绍这些类型。  
  
### <a name="comptr"></a>ComPtr  
 [ComPtr](../windows/comptr-class.md) 是一种智能指针  类型，表示由模板参数指定的接口。 使用 `ComPtr` 可以声明能够访问从接口派生的对象成员的变量。 `ComPtr` 会自动维护基础接口指针的引用计数，并在引用计数变为零时发布接口。  
  
### <a name="runtimeclass"></a>RuntimeClass  
 [RuntimeClass](../windows/runtimeclass-class.md) 表示继承一组指定接口的实例化类。 `RuntimeClass` 对象既可支持一个或多个 [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)] COM 接口，也可提供对组件的弱引用。  
  
### <a name="module"></a>模块  
 [模块](../windows/module-class.md) 表示一组相关的对象。 `Module` 对象管理类工厂和注册。类工厂可以创建对象，注册则让其他应用程序能够使用对象。  
  
### <a name="callback"></a>回调  
 [回调](../windows/callback-function-windows-runtime-cpp-template-library.md) 函数可以创建对象，该对象的成员函数为事件处理程序（回调方法）。 使用 `Callback` 函数可以编写异步操作。  
  
### <a name="eventsource"></a>EventSource  
 [EventSource](../windows/eventsource-class.md) 用于管理委托  事件处理程序。 使用 [!INCLUDE[cppwrl_short](../windows/includes/cppwrl_short_md.md)] 可以实现委托，使用 `EventSource` 可以添加、移除和调用委托。  
  
### <a name="asyncbase"></a>AsyncBase  
 [AsyncBase](../windows/asyncbase-class.md) 提供表示 [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)] 异步编程模型的虚方法。 重写此类中的成员可以创建能够启动、停止或检查异步操作进度的自定义类。  
  
### <a name="ftmbase"></a>FtmBase  
 [FtmBase](../windows/ftmbase-class.md) 表示自由线程封送拆收器对象。 `FtmBase` 可以创建全局接口表 (GIT)，并帮助管理封送处理和代理对象。  
  
### <a name="weakref"></a>WeakRef  
 [WeakRef](../windows/weakref-class.md) 是表示弱引用 的智能指针类型。弱引用可引用能够访问或者不能访问的对象。 `WeakRef` 对象仅可由 [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)]使用，而不能由传统 COM 使用。  
  
 `WeakRef` 对象通常表示由外部线程或应用程序控制其存在性的对象。 例如， `WeakRef` 对象可以引用文件对象。 当文件打开时， `WeakRef` 有效，并且引用的文件可以访问。 当文件关闭时， `WeakRef` 无效，并且文件不可访问。  
  
## <a name="related-topics"></a>相关主题  
  
|||  
|-|-|  
|[类库项目模板](../windows/wrl-class-library-project-template.md)|介绍如何访问 WRL 类库项目模板。 此模板有助于简化使用 Visual Studio 创建 [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)] 组件的任务。|  
|[按类别列出的关键 Api](../windows/key-wrl-apis-by-category.md)|重点介绍主要的 [!INCLUDE[cppwrl_short](../windows/includes/cppwrl_short_md.md)] 类型、函数和宏。|  
|[参考](../windows/wrl-reference.md)|包含有关 [!INCLUDE[cppwrl_short](../windows/includes/cppwrl_short_md.md)]的参考信息。|  
|[快速参考 （Windows 运行时和 Visual c + +）](http://go.microsoft.com/fwlink/?LinkId=229180)|简要介绍支持 [!INCLUDE[cppwrt_short](../build/reference/includes/cppwrt_short_md.md)] 的 [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)]功能。|  
|[在 Visual c + + 中使用 Windows 运行时组件](http://go.microsoft.com/fwlink/?LinkId=229155)|演示如何使用 [!INCLUDE[cppwrt_short](../build/reference/includes/cppwrt_short_md.md)] 创建基本 [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)] 组件。|