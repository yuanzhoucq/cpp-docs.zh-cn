---
title: Windows 运行时 C++ 模板库 (WRL)
ms.date: 11/04/2016
ms.topic: overview
ms.assetid: b915afce-553b-44a7-b8dc-0ab601758eb0
ms.openlocfilehash: 7a7b37a32ebaa0bb6ad71c8f710300256589388d
ms.sourcegitcommit: 3ee06ec53153cf21910fc8cfef78a4f25f9633f3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/26/2019
ms.locfileid: "74541200"
---
# <a name="windows-runtime-c-template-library-wrl"></a>Windows 运行时 C++ 模板库 (WRL)

Windows 运行时 C++ 模板库 (WRL) 是一个提供低级别方式来创作和使用 Windows 运行时组件的模板库。

> [!NOTE]
> WRL 现已由C++/WinRT （Windows 运行时 api 的标准 c + + 17 语言投影）取代。 C++/WinRT 从版本1803开始，在 Windows 10 SDK 中提供。 C++/WinRT 完全在标头文件中实现，旨在向您提供对新式 Windows API 的第一类访问。
>
> 使用C++/WinRT，可以使用任何符合标准的 c + + 17 编译器来使用和创作 Windows 运行时 api。 C++与 Windows 运行时的任何其他语言选项相比，/WinRT 通常性能更好，生成的二进制文件更小。 我们将继续支持 C++/CX 和 WRL，但强烈建议新应用程序使用 C++/WinRT。 有关详细信息，请参阅 [C++/WinRT](https://docs.microsoft.com/windows/uwp/cpp-and-winrt-apis/index)。

## <a name="benefits"></a>优点

Windows 运行时C++模板库使您能够更轻松地实现和使用组件对象模型（COM）组件。 它提供了一些管理技术（如引用计数）来管理对象的生存期和测试 HRESULT 值，以确定操作是成功还是失败。 若要成功使用 Windows 运行时C++模板库，必须认真遵循这些规则和技术。

C++/Cx 是一种使用 Windows 运行时组件的基于语言的高级方法。 Windows 运行时C++模板库和C++/cx 都通过代表您自动执行自动维护任务来简化 Windows 运行时的代码编写。

Windows 运行时C++模板库和C++/cx 提供了不同的优点。 下面是你可能想要使用 Windows 运行时C++模板库而不是/cx 的C++一些原因：

- Windows 运行时C++模板库在 Windows 运行时应用程序二进制接口（ABI）上添加了少量抽象，使你能够控制基础代码，以便更好地创建或使用 Windows 运行时 api。

- C++/CX 将 COM HRESULT 值表示为异常。 如果继承了使用 COM 或不使用异常的基本代码，你可能会发现 Windows 运行时C++模板库是使用 Windows 运行时的更自然的方式，因为你不必使用异常。

   > [!NOTE]
   > Windows 运行时C++模板库使用 HRESULT 值，不会引发异常。 此外，Windows 运行时C++模板库使用智能指针和 RAII 模式，以帮助确保在应用程序代码引发异常时正确销毁对象。 有关智能指针和 RAII 的详细信息，请参阅[智能指针](../../cpp/smart-pointers-modern-cpp.md)和[对象资源（RAII）](../../cpp/objects-own-resources-raii.md)。

- Windows 运行时C++模板库的用途和设计是由活动模板库（ATL）的，它是一组基于C++模板的类，可简化 COM 对象的编程。 由于 Windows 运行时C++模板库使用标准C++来包装 Windows 运行时，因此你可以更轻松地将用 ATL 编写的多个现有 COM 组件与 Windows 运行时进行端口和交互。 如果你已经知道 ATL，你可能会发现 Windows 运行时C++模板库编程更容易。

## <a name="getting-started"></a>入门

下面是一些可帮助你立即开始使用 Windows 运行时C++模板库的资源。

[Windows 运行时库（WRL）](https://channel9.msdn.com/Events/Windows-Camp/Developing-Windows-8-Metro-style-apps-in-Cpp/The-Windows-Runtime-Library-WRL-)<br/>
在此第9频道视频中，详细了解 Windows 运行时C++模板库如何帮助你编写通用 WINDOWS 平台（UWP）应用，以及如何创作和使用 Windows 运行时组件。

[如何：激活和使用 Windows 运行时组件](how-to-activate-and-use-a-windows-runtime-component-using-wrl.md)<br/>
演示如何使用 Windows 运行时C++模板库来初始化 Windows 运行时并激活和使用 Windows 运行时组件。

[如何：完成异步操作](how-to-complete-asynchronous-operations-using-wrl.md)<br/>
演示如何使用 Windows 运行时C++模板库来启动异步操作，并在操作完成时执行工作。

[如何：处理事件](how-to-handle-events-using-wrl.md)<br/>
演示如何使用 Windows 运行时C++模板库来订阅和处理 Windows 运行时对象的事件。

[演练：使用 WRL 和媒体基础创建 UWP 应用](walkthrough-creating-a-windows-store-app-using-wrl-and-media-foundation.md)<br/>
了解如何创建使用[Microsoft 媒体基础](/windows/win32/medfound/microsoft-media-foundation-sdk)的 UWP 应用。

[如何：创建经典 COM 组件](how-to-create-a-classic-com-component-using-wrl.md)<br/>
演示如何使用 Windows 运行时C++模板库来创建基本的 com 组件，以及从桌面应用程序注册和使用 COM 组件的基本方法。

[如何：直接实例化 WRL 组件](how-to-instantiate-wrl-components-directly.md)<br/>
了解如何使用 [Microsoft::WRL::Make](make-function.md) 和 [Microsoft::WRL::Details::MakeAndInitialize](makeandinitialize-function.md) 函数从定义组件的模块实例化组件。

[如何：使用 winmdidl.exe 和 midlrt.exe 通过窗口元数据创建 .h 文件](use-winmdidl-and-midlrt-to-create-h-files-from-windows-metadata.md)<br/>
演示如何通过从 .winmd 元数据创建 IDL 文件，使用 WRL 中的自定义 Windows 运行时组件。

[演练：使用任务和 XML HTTP 请求进行连接](../../parallel/concrt/walkthrough-connecting-using-tasks-and-xml-http-requests.md)<br/>
演示如何将[IXMLHTTPRequest2](/windows/win32/api/msxml6/nn-msxml6-ixmlhttprequest2)和[IXMLHTTPRequest2Callback](/windows/win32/api/msxml6/nn-msxml6-ixmlhttprequest2callback)接口与任务一起使用，以将 HTTP GET 和 POST 请求发送到 UWP 应用中的 web 服务。

[必应地图行程优化器示例](https://code.msdn.microsoft.com/Bing-Maps-trip-optimizer-c4e037f7)<br/>
使用在演练中定义的 `HttpRequest` 类：在完整 UWP 应用的上下文中[使用任务和 XML HTTP 请求进行连接](../../parallel/concrt/walkthrough-connecting-using-tasks-and-xml-http-requests.md)。

[使用C++示例创建 Windows 运行时 DLL 组件](https://code.msdn.microsoft.com/windowsapps/Creating-a-Windows-Runtime-6c399797)<br/>
演示如何使用 Windows 运行时C++模板库创建进程内 DLL 组件，并从C++/cx、JavaScript 和C#使用该组件。

[DirectX 大理石迷宫游戏示例](https://docs.microsoft.com/samples/microsoft/windows-appsample-marble-maze/directx-marble-maze-game-sample/)<br/>
演示如何使用 Windows 运行时C++模板库在完整的三维游戏上下文中管理 COM 组件（例如 DirectX 和媒体基础）的生存期。

[从桌面应用发送 toast 通知示例](https://code.msdn.microsoft.com/windowsdesktop/Sending-toast-notifications-71e230a2)<br/>
演示如何使用 Windows 运行时C++模板库从桌面应用程序中使用 toast 通知。

## <a name="windows-runtime-c-template-library-compared-to-atl"></a>与C++ ATL 比较 Windows 运行时模板库

Windows 运行时C++模板库类似于活动模板库（ATL），因为你可以使用它来创建小型、快速的 COM 对象。 Windows 运行时C++模板库和 ATL 还在模块中共享对象的定义、显式注册接口，以及使用工厂打开对象创建等概念。 如果你熟悉 ATL，你C++可能会喜欢 Windows 运行时模板库。

Windows 运行时C++模板库支持 UWP 应用所需的 COM 功能。 因此，它又与 ATL 有所不同，因为它无法直接支持下列 COM 功能：

- 聚合

- 常用实现

- 双重接口 (`IDispatch`)

- 标准枚举器接口

- 连接点

- 分离式接口

- OLE 嵌入

- ActiveX 控件

- COM+

## <a name="concepts"></a>概念

Windows 运行时C++模板库提供了表示几个基本概念的类型。 以下几节将介绍这些类型。

### <a name="comptr"></a>ComPtr

[ComPtr](comptr-class.md) 是一种智能指针 类型，表示由模板参数指定的接口。 使用 `ComPtr` 可以声明能够访问从接口派生的对象成员的变量。 `ComPtr` 会自动维护基础接口指针的引用计数，并在引用计数变为零时释放接口。

### <a name="runtimeclass"></a>RuntimeClass

[RuntimeClass](runtimeclass-class.md) 表示继承一组指定接口的实例化类。 `RuntimeClass` 对象可以提供对一个或多个 Windows 运行时 COM 接口的支持或对组件的弱引用。

### <a name="module"></a>模块

[模块](module-class.md) 表示一组相关的对象。 `Module` 对象管理类工厂和注册。类工厂可以创建对象，注册则让其他应用程序能够使用对象。

### <a name="callback"></a>回拨

[回调](callback-function-wrl.md) 函数可以创建对象，该对象的成员函数为事件处理程序（回调方法）。 使用 `Callback` 函数可以编写异步操作。

### <a name="eventsource"></a>EventSource

[EventSource](eventsource-class.md) 用于管理委托 事件处理程序。 使用 Windows 运行时C++模板库来实现委托，并使用 `EventSource` 添加、移除和调用委托。

### <a name="asyncbase"></a>AsyncBase

[AsyncBase](asyncbase-class.md)提供表示异步编程模型 Windows 运行时的虚拟方法。 重写此类中的成员可以创建能够启动、停止或检查异步操作进度的自定义类。

### <a name="ftmbase"></a>FtmBase

[FtmBase](ftmbase-class.md) 表示自由线程封送拆收器对象。 `FtmBase` 创建一个全局接口表（GIT），并帮助管理封送处理和代理对象。

### <a name="weakref"></a>WeakRef

[WeakRef](weakref-class.md) 是表示弱引用的智能指针类型。弱引用可引用能够访问或者不能访问的对象。 `WeakRef` 对象只能由 Windows 运行时（而不是经典 COM）使用。

`WeakRef` 对象通常表示由外部线程或应用程序控制其存在性的对象。 例如， `WeakRef` 对象可以引用文件对象。 当文件打开时， `WeakRef` 有效，并且引用的文件可以访问。 当文件关闭时， `WeakRef` 无效，并且文件不可访问。

## <a name="related-topics"></a>相关主题

|||
|-|-|
|[按类别列出的密钥 Api](key-wrl-apis-by-category.md)|突出显示主 Windows 运行时C++模板库类型、函数和宏。|
|[引用](wrl-reference.md)|包含 Windows 运行时C++模板库的参考信息。|
|[快速参考C++/cx）](../../cppcx/quick-reference-c-cx.md)|简要介绍支持C++Windows 运行时的/cx 功能。|
|[在视觉对象中使用 Windows 运行时组件C++](/windows/uwp/winrt-components/walkthrough-creating-a-basic-windows-runtime-component-in-cpp-and-calling-it-from-javascript-or-csharp)|演示如何使用C++/cx 创建基本 Windows 运行时组件。|
