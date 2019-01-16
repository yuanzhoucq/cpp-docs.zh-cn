---
title: Windows 运行时 C++ 模板库 (WRL)
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: b915afce-553b-44a7-b8dc-0ab601758eb0
ms.openlocfilehash: 5c1a4e7df424499f400dbd70d675956deef6bc5d
ms.sourcegitcommit: 360b55e89e5954f494e52b1cf989fbaceda06f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/16/2019
ms.locfileid: "54335744"
---
# <a name="windows-runtime-c-template-library-wrl"></a>Windows 运行时 C++ 模板库 (WRL)

Windows 运行时 C++ 模板库 (WRL) 是一个提供低级别方式来创作和使用 Windows 运行时组件的模板库。

> [!NOTE]
> WRL 现已更名为 C + + / WinRT，的 Windows 运行时 Api 的标准 C + + 17 语言投影。 C + + / WinRT 是 Windows 10 SDK 版本 1803年以后从中可用。 C + + / WinRT 是完全在标头文件中实现，旨在提供对新式 Windows API 的优先访问权限。
>
> 使用 C + + / WinRT，您可以使用和编写 Windows 运行时 Api 使用任何符合标准的 C + + 17 编译器。 C + + WinRT 通常更好地执行，并生成较小的二进制文件比 Windows 运行时的任何其他语言选项。 我们将继续支持 C + + /cli CX 和 WRL，但强烈建议新的应用程序使用 C + + WinRT。 有关详细信息，请参阅[C + + WinRT](https://docs.microsoft.com/windows/uwp/cpp-and-winrt-apis/index)。

## <a name="benefits"></a>优点

Windows 运行时 c + + 模板库，可更轻松地实现和使用组件对象模型 (COM) 组件。 它提供引用计数来管理对象的生存期和测试以确定操作是成功还是失败的 HRESULT 值类管理技术。 若要成功使用 Windows 运行时 c + + 模板库，你必须认真遵循这些规则和技术。

C + + /cli CX 是使用 Windows 运行时组件的高级别，基于语言的方法。 Windows 运行时 c + + 模板库和 C + + /cli CX 通过自动代表用户执行管理任务，简化为 Windows 运行时编写代码。

Windows 运行时 c + + 模板库和 C + + /cli CX 提供不同的优点。 以下是一些原因可能想要使用 Windows 运行时 c + + 模板库，而不是 C + + /cli CX:

- Windows 运行时 c + + 模板库添加少许抽象通过 Windows 运行时应用程序二进制接口 (ABI)，使你能够控制基础代码，以更好地创建或使用 Windows 运行时 Api。

- C + + /cli CX 表示为异常的 COM HRESULT 值。 如果已继承的代码库来使用 COM，或不使用异常，可能会发现 Windows 运行时 c + + 模板库是更简单的方式来使用 Windows 运行时，因为无需使用异常。

   > [!NOTE]
   > Windows 运行时 c + + 模板库使用 HRESULT 值并不会引发异常。 此外，Windows 运行时 c + + 模板库使用智能指针和 RAII 模式，以帮助确保应用程序代码引发异常时正确销毁对象。 有关智能指针和 RAII 的详细信息，请参阅[智能指针](../../cpp/smart-pointers-modern-cpp.md)并[对象自己的资源 (RAII)](../../cpp/objects-own-resources-raii.md)。

- 用途和设计的 Windows 运行时 c + + 模板库被启发的活动模板库 (ATL)，这是一组基于模板的 c + + 类，用于简化 COM 对象的编程。 由于 Windows 运行时 c + + 模板库使用标准 c + + 包装 Windows 运行时，可以更轻松地移植并与在 ATL 中写入到 Windows 运行时的许多现有 COM 组件进行交互。 如果您已经知道 ATL，可能会发现 Windows 运行时 c + + 模板库编程更轻松。

## <a name="getting-started"></a>入门

以下是一些可以帮助您立刻开始工作与 Windows 运行时 c + + 模板库的资源。

[Windows 运行时库 (WRL)](https://channel9.msdn.com/Events/Windows-Camp/Developing-Windows-8-Metro-style-apps-in-Cpp/The-Windows-Runtime-Library-WRL-)<br/>
在此第 9 频道视频中，详细了解 Windows 运行时 c + + 模板库的可帮助你编写通用 Windows 平台 (UWP) 应用以及如何编写和使用 Windows 运行时组件。

[如何：激活和使用 Windows 运行时组件](how-to-activate-and-use-a-windows-runtime-component-using-wrl.md)<br/>
演示如何使用 Windows 运行时 c + + 模板库初始化 Windows 运行时和激活和使用 Windows 运行时组件。

[如何：完成异步操作](how-to-complete-asynchronous-operations-using-wrl.md)<br/>
演示如何使用 Windows 运行时 c + + 模板库启动异步操作并在操作完成时执行工作。

[如何：处理事件](how-to-handle-events-using-wrl.md)<br/>
演示如何使用 Windows 运行时 c + + 模板库来订阅和处理 Windows 运行时对象的事件。

[演练：创建 UWP 应用使用 WRL 和媒体基础](walkthrough-creating-a-windows-store-app-using-wrl-and-media-foundation.md)<br/>
了解如何创建使用的 UWP 应用[Microsoft 媒体基础](/windows/desktop/medfound/microsoft-media-foundation-sdk)。

[如何：创建经典的 COM 组件](how-to-create-a-classic-com-component-using-wrl.md)<br/>
演示如何使用 Windows 运行时 c + + 模板库创建基本的 COM 组件和注册和使用 COM 组件从桌面应用程序的基本方法。

[如何：直接实例化 WRL 组件](how-to-instantiate-wrl-components-directly.md)<br/>
了解如何使用 [Microsoft::WRL::Make](make-function.md) 和 [Microsoft::WRL::Details::MakeAndInitialize](makeandinitialize-function.md) 函数从定义组件的模块实例化组件。

[如何：使用 winmdidl.exe 和 midlrt.exe 通过窗口元数据创建.h 文件](use-winmdidl-and-midlrt-to-create-h-files-from-windows-metadata.md)<br/>
演示如何通过从 .winmd 元数据创建 IDL 文件，使用 WRL 中的自定义 Windows 运行时组件。

[演练：使用任务和 XML HTTP 请求进行连接](../../parallel/concrt/walkthrough-connecting-using-tasks-and-xml-http-requests.md)<br/>
演示如何使用[IXMLHTTPRequest2](/windows/desktop/api/msxml6/nn-msxml6-ixmlhttprequest2)并[IXMLHTTPRequest2Callback](/windows/desktop/api/msxml6/nn-msxml6-ixmlhttprequest2callback)接口与任务以将 HTTP GET 和 POST 请求发送到 UWP 应用中的 web 服务结合使用。

[必应地图行程优化器示例](https://code.msdn.microsoft.com/Bing-Maps-trip-optimizer-c4e037f7)<br/>
使用`HttpRequest`类中定义的[演练：连接使用任务和 XML HTTP 请求](../../parallel/concrt/walkthrough-connecting-using-tasks-and-xml-http-requests.md)完整的 UWP 应用的上下文中。

[使用 c + + 示例创建 Windows 运行时 DLL 组件](https://code.msdn.microsoft.com/windowsapps/Creating-a-Windows-Runtime-6c399797)<br/>
演示如何使用 Windows 运行时 c + + 模板库创建进程内 DLL 组件和使用它从 C + + /cli CX、 JavaScript 和 C#。

[DirectX 大理石迷宫游戏示例](https://code.msdn.microsoft.com/windowsapps/DirectX-Marble-Maze-Game-e4806345)<br/>
演示如何使用 Windows 运行时 c + + 模板库来管理 COM 组件，如 DirectX 和媒体基础的一个完整的三维游戏上下文中的生存期。

[从桌面应用程序示例发送 toast 通知](https://code.msdn.microsoft.com/windowsdesktop/Sending-toast-notifications-71e230a2)<br/>
演示如何使用 Windows 运行时 c + + 模板库以使用从桌面应用的 toast 通知。

## <a name="windows-runtime-c-template-library-compared-to-atl"></a>Windows 运行时 c + + 模板库与 ATL 比较

Windows 运行时 c + + 模板库类似于活动模板库 (ATL)，因为可以使用它来快速创建小型，COM 对象。 Windows 运行时 c + + 模板库和 ATL 还共享概念，例如在模块中，显式注册接口，对象的定义，并使用工厂开始创建对象。 如果你熟悉 atl。 您可能熟悉 Windows 运行时 c + + 模板库

Windows 运行时 c + + 模板库支持的 UWP 应用都需要的 COM 功能。 因此，它又与 ATL 有所不同，因为它无法直接支持下列 COM 功能：

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

Windows 运行时 c + + 模板库提供表示了一些基本概念的类型。 以下几节将介绍这些类型。

### <a name="comptr"></a>ComPtr

[ComPtr](comptr-class.md) 是一种智能指针  类型，表示由模板参数指定的接口。 使用 `ComPtr` 可以声明能够访问从接口派生的对象成员的变量。 `ComPtr` 会自动维护基础接口指针的引用计数，并在引用计数变为零时发布接口。

### <a name="runtimeclass"></a>RuntimeClass

[RuntimeClass](runtimeclass-class.md) 表示继承一组指定接口的实例化类。 一个`RuntimeClass`对象可以提供对一个或多个 Windows 运行时 COM 接口或对组件的弱引用支持的组合。

### <a name="module"></a>模块

[模块](module-class.md) 表示一组相关的对象。 `Module` 对象管理类工厂和注册。类工厂可以创建对象，注册则让其他应用程序能够使用对象。

### <a name="callback"></a>回调

[回调](callback-function-wrl.md) 函数可以创建对象，该对象的成员函数为事件处理程序（回调方法）。 使用 `Callback` 函数可以编写异步操作。

### <a name="eventsource"></a>EventSource

[EventSource](eventsource-class.md) 用于管理委托  事件处理程序。 使用 Windows 运行时 c + + 模板库实现委托，并使用`EventSource`添加、 删除和调用委托。

### <a name="asyncbase"></a>AsyncBase

[AsyncBase](asyncbase-class.md)提供表示 Windows 运行时异步编程模型的虚拟方法。 重写此类中的成员可以创建能够启动、停止或检查异步操作进度的自定义类。

### <a name="ftmbase"></a>FtmBase

[FtmBase](ftmbase-class.md) 表示自由线程封送拆收器对象。 `FtmBase` 可以创建全局接口表 (GIT)，并帮助管理封送处理和代理对象。

### <a name="weakref"></a>WeakRef

[WeakRef](weakref-class.md) 是表示弱引用 的智能指针类型。弱引用可引用能够访问或者不能访问的对象。 一个`WeakRef`可以使用对象，由只有 Windows 运行时，而不是经典 com。

`WeakRef` 对象通常表示由外部线程或应用程序控制其存在性的对象。 例如， `WeakRef` 对象可以引用文件对象。 当文件打开时， `WeakRef` 有效，并且引用的文件可以访问。 当文件关闭时， `WeakRef` 无效，并且文件不可访问。

## <a name="related-topics"></a>相关主题

|||
|-|-|
|[按类别列出的关键 Api](key-wrl-apis-by-category.md)|重点介绍主要的 Windows 运行时 c + + 模板库类型、 函数和宏。|
|[引用](wrl-reference.md)|包含 Windows 运行时 c + + 模板库的参考信息。|
|[快速参考 （Windows 运行时和 Visual c + +）](../../cppcx/quick-reference-c-cx.md)|简要介绍了 C + + /cli CX 功能支持 Windows 运行时。|
|[在 Visual c + + 中使用 Windows 运行时组件](/windows/uwp/winrt-components/walkthrough-creating-a-basic-windows-runtime-component-in-cpp-and-calling-it-from-javascript-or-csharp)|演示如何使用 C + + /cli CX 创建基本 Windows 运行时组件。|
