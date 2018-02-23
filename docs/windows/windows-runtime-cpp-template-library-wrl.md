---
title: "Windows 运行时 c + + 模板库 (WRL) |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs:
- C++
ms.assetid: b915afce-553b-44a7-b8dc-0ab601758eb0
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 98b97098f397772026d0926c72ad83dadd5e59cb
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/14/2018
---
# <a name="windows-runtime-c-template-library-wrl"></a>Windows 运行时 C++ 模板库 (WRL)
Windows 运行时 C++ 模板库 (WRL) 是一个提供低级别方式来创作和使用 Windows 运行时组件的模板库。  
  
## <a name="benefits"></a>优点  
 Windows 运行时 c + + 模板库，可更轻松地实现和使用组件对象模型 (COM) 组件。 它提供引用计数这类管理技术来管理对象的生存期，并可通过测试 `HRESULT` 值来确定操作是否成功。 若要成功使用 Windows 运行时 c + + 模板库，你必须认真遵循这些规则和技术。  
  
 C + + /cli CX 是使用 Windows 运行时组件高级的、 基于语言的方法。 Windows 运行时 c + + 模板库和 C + + /cli CX 通过替你自动执行管理任务来简化的代码编写的 Windows 运行时。  
  
 Windows 运行时 c + + 模板库和 C + + /cli CX 具有不同的优点。 下面是一些原因，你可能想要使用 Windows 运行时 c + + 模板库而不是 C + + /cli CX:  
  
-   Windows 运行时 c + + 模板库添加少抽象通过 Windows 运行时应用程序二进制接口 (ABI)，使你能够控制基础代码，以便更好地创建或使用 Windows 运行时 Api。  
  
-   C + + /cli CX 表示 COM`HRESULT`作为异常的值。 如果您已继承了使用 COM 或不使用异常的基本代码，你可能会发现 Windows 运行时 c + + 模板库是以更自然的方式，因为你不必使用异常的情况下用于 Windows 运行时。  
  
    > [!NOTE]
    >  Windows 运行时 c + + 模板库使用`HRESULT`值并不会引发异常。 此外，Windows 运行时 c + + 模板库使用智能指针和 RAII 模式，以帮助确保应用程序代码引发异常时正确销毁对象。 有关智能指针和 RAII 的详细信息，请参阅[智能指针](../cpp/smart-pointers-modern-cpp.md)和[对象自己资源 (RAII)](../cpp/objects-own-resources-raii.md)。  
  
-   用途和设计的 Windows 运行时 c + + 模板库是由活动模板库 (ATL) 创作，这是一组基于模板的 c + + 类，用于简化 COM 对象的编程。 因为 Windows 运行时 c + + 模板库使用标准 c + + 包装 Windows 运行时，你可以更轻松地交互和端口许多写入 ATL 到 Windows 运行时的现有 COM 组件。 如果你已经知道 ATL，你可能会发现 Windows 运行时 c + + 模板库编程将更加轻松。  
  
## <a name="getting-started"></a>入门  
 下面是一些可帮助你获取使用 Windows 运行时 c + + 模板库立即的资源。  
  
 [Windows 运行时库 (WRL)](http://channel9.msdn.com/Events/Windows-Camp/Developing-Windows-8-Metro-style-apps-in-Cpp/The-Windows-Runtime-Library-WRL-)  
 在此第 9 频道视频中，详细了解 Windows 运行时 c + + 模板库的可帮助你编写通用 Windows 平台 (UWP) 应用以及如何生成和使用 Windows 运行时组件。  
  
 [如何： 激活和使用 Windows 运行时组件](../windows/how-to-activate-and-use-a-windows-runtime-component-using-wrl.md)  
 演示如何使用 Windows 运行时 c + + 模板库初始化 Windows 运行时以及激活和使用 Windows 运行时组件。  
  
 [如何： 完成异步操作](../windows/how-to-complete-asynchronous-operations-using-wrl.md)  
 演示如何使用 Windows 运行时 c + + 模板库启动异步操作，并在操作完成时执行工作。  
  
 [如何： 处理事件](../windows/how-to-handle-events-using-wrl.md)  
 演示如何使用 Windows 运行时 c + + 模板库订阅和处理 Windows 运行时对象的事件。  
  
 [演练： 创建基本 Windows 运行时组件](../windows/walkthrough-creating-a-basic-windows-runtime-component-using-wrl.md)  
 演示如何使用 Windows 运行时 c + + 模板库创建两个数相加的基本 Windows 运行时组件。 此外演示如何引发事件，以及通过使用 JavaScript 的 UWP 应用使用组件。  
  
 [演练：使用 WRL 和媒体基础创建 UWP 应用](../windows/walkthrough-creating-a-windows-store-app-using-wrl-and-media-foundation.md)  
 了解如何创建的 UWP 应用程序使用[Microsoft 媒体基础](http://msdn.microsoft.com/library/windows/apps/ms694197)。  
  
 [如何： 创建传统型 COM 组件](../windows/how-to-create-a-classic-com-component-using-wrl.md)  
 演示如何使用 Windows 运行时 c + + 模板库创建基本的 COM 组件和一种注册和使用从桌面应用程序的 COM 组件的基本方法。  
  
 [如何：直接实例化 WRL 组件](../windows/how-to-instantiate-wrl-components-directly.md)  
 了解如何使用[Microsoft::WRL::Make](../windows/make-function.md)和[Microsoft::WRL::Details::MakeAndInitialize](../windows/makeandinitialize-function.md)函数来实例化定义它的模块中的组件。  
  
 [如何：使用 winmdidl.exe 和 midlrt.exe 通过窗口元数据创建 .h 文件](../windows/use-winmdidl-and-midlrt-to-create-h-files-from-windows-metadata.md)  
 演示如何通过从 .winmd 元数据创建 IDL 文件，使用 WRL 中的自定义 Windows 运行时组件。  
  
 [演练：使用任务和 XML HTTP 请求进行连接](../parallel/concrt/walkthrough-connecting-using-tasks-and-xml-http-requests.md)  
 演示如何使用[IXMLHTTPRequest2](http://msdn.microsoft.com/en-us/bbc11c4a-aecf-4d6d-8275-3e852e309908)和[IXMLHTTPRequest2Callback](http://msdn.microsoft.com/en-us/aa4b3f4c-6e28-458b-be25-6cce8865fc71)接口与任务以将 HTTP GET 和 POST 请求发送到 web 服务中的 UWP 应用。  
  
 [必应地图行程优化器示例](http://code.msdn.microsoft.com/Bing-Maps-trip-optimizer-c4e037f7)  
 使用`HttpRequest`中定义的类[演练： 连接使用任务和 XML HTTP 请求](../parallel/concrt/walkthrough-connecting-using-tasks-and-xml-http-requests.md)完整的 UWP 应用的上下文中。  
  
 [创建具有 c + + 示例的 Windows 运行时 DLL 组件](http://code.msdn.microsoft.com/windowsapps/Creating-a-Windows-Runtime-6c399797)  
 演示如何使用 Windows 运行时 c + + 模板库创建进程内 DLL 组件，以及使用它从 C + + /cli CX、 JavaScript 和 C#。  
  
 [DirectX 大理石迷宫游戏示例](http://code.msdn.microsoft.com/windowsapps/DirectX-Marble-Maze-Game-e4806345)  
 演示如何使用 Windows 运行时 c + + 模板库来管理 COM 组件，如 DirectX 和媒体基础的完整的三维游戏上下文中的生存期。  
  
 [从桌面应用程序示例发送 toast 通知](http://code.msdn.microsoft.com/windowsdesktop/Sending-toast-notifications-71e230a2)  
 演示如何使用 Windows 运行时 c + + 模板库用于从桌面应用的 toast 通知。  
  
## <a name="windows-runtime-c-template-library-compared-to-atl"></a>Windows 运行时 c + + 模板库与 ATL 比较  
 Windows 运行时 c + + 模板库类似于活动模板库 (ATL)，因为你可以使用它来快速创建小型，COM 对象。 Windows 运行时 c + + 模板库以及 ATL 共享概念，例如在模块中，显式注册接口，对象定义和使用工厂开始创建对象。 如果你熟悉 atl。 你可能熟悉 Windows 运行时 c + + 模板库  
  
 Windows 运行时 c + + 模板库支持适用于 UWP 应用需要的 COM 功能。 因此，它又与 ATL 有所不同，因为它无法直接支持下列 COM 功能：  
  
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
 Windows 运行时 c + + 模板库提供类型来表示几个基本概念。 以下几节将介绍这些类型。  
  
### <a name="comptr"></a>ComPtr  
 [ComPtr](../windows/comptr-class.md)是*智能指针*表示由模板参数指定的接口的类型。 使用 `ComPtr` 可以声明能够访问从接口派生的对象成员的变量。 `ComPtr` 会自动维护基础接口指针的引用计数，并在引用计数变为零时发布接口。  
  
### <a name="runtimeclass"></a>RuntimeClass  
 [RuntimeClass](../windows/runtimeclass-class.md)表示继承一组指定接口的实例化的类。 A`RuntimeClass`对象可以提供了对一个或多个 Windows 运行时 COM 接口或对组件的弱引用支持的组合。  
  
### <a name="module"></a>模块  
 [模块](../windows/module-class.md)表示相关对象的集合。 `Module` 对象管理类工厂和注册。类工厂可以创建对象，注册则让其他应用程序能够使用对象。  
  
### <a name="callback"></a>回调  
 [回调](../windows/callback-function-windows-runtime-cpp-template-library.md)函数创建对象，该对象的成员函数为事件处理程序 （回调方法）。 使用 `Callback` 函数可以编写异步操作。  
  
### <a name="eventsource"></a>EventSource  
 [EventSource](../windows/eventsource-class.md)用于管理*委托*事件处理程序。 使用 Windows 运行时 c + + 模板库实现委托，并使用`EventSource`添加、 移除和调用委托。  
  
### <a name="asyncbase"></a>AsyncBase  
 [AsyncBase](../windows/asyncbase-class.md)提供表示 Windows 运行时异步编程模型的虚方法。 重写此类中的成员可以创建能够启动、停止或检查异步操作进度的自定义类。  
  
### <a name="ftmbase"></a>FtmBase  
 [FtmBase](../windows/ftmbase-class.md)表示自由线程封送处理程序对象。 `FtmBase` 可以创建全局接口表 (GIT)，并帮助管理封送处理和代理对象。  
  
### <a name="weakref"></a>WeakRef  
 [WeakRef](../windows/weakref-class.md)是智能指针类型，表示*弱引用*，引用可能会或可能无法访问的对象。 A`WeakRef`对象可使用由只有 Windows 运行时，而不是传统 com 使用。  
  
 `WeakRef` 对象通常表示由外部线程或应用程序控制其存在性的对象。 例如， `WeakRef` 对象可以引用文件对象。 当文件打开时， `WeakRef` 有效，并且引用的文件可以访问。 当文件关闭时， `WeakRef` 无效，并且文件不可访问。  
  
## <a name="related-topics"></a>相关主题  
  
|||  
|-|-|  
|[类库项目模板](../windows/wrl-class-library-project-template.md)|介绍如何访问 WRL 类库项目模板。 此模板有助于简化使用 Visual Studio 创建 Windows 运行时组件的任务。|  
|[按类别列出的关键 Api](../windows/key-wrl-apis-by-category.md)|突出显示主的 Windows 运行时 c + + 模板库类型、 函数和宏。|  
|[参考](../windows/wrl-reference.md)|包含 Windows 运行时 c + + 模板库的参考信息。|  
|[快速参考 （Windows 运行时和 Visual c + +）](http://go.microsoft.com/fwlink/p/?linkid=229180)|简要介绍 C + + /cli CX 支持 Windows 运行时的功能。|  
|[在 Visual c + + 中使用 Windows 运行时组件](http://go.microsoft.com/fwlink/p/?linkid=229155)|演示如何使用 C + + /cli CX 创建基本 Windows 运行时组件。|