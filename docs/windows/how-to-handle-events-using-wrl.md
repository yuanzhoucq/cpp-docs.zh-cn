---
title: 如何： 使用 WRL 处理事件 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
ms.assetid: 1c77543f-7b0c-4a94-93bf-e3225885ed76
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 287fe57868f1550e2f778bd9122d0d350011084e
ms.sourcegitcommit: d5d6bb9945c3550b8e8864b22b3a565de3691fde
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/06/2018
ms.locfileid: "39570628"
---
# <a name="how-to-handle-events-using-wrl"></a>如何：使用 WRL 处理事件
本文档演示如何使用 Windows 运行时 c + + 模板库 (WRL) 订阅和处理 Windows 运行时对象的事件。  
  
 有关创建该组件的实例，并检索属性值的更多基础示例，请参阅[如何： 激活和使用 Windows 运行时组件](../windows/how-to-activate-and-use-a-windows-runtime-component-using-wrl.md)。  
  
## <a name="subscribing-to-and-handling-events"></a>订阅和处理事件  
 以下步骤开始`ABI::Windows::System::Threading::IDeviceWatcher`对象，并使用事件处理程序来监视进度。 `IDeviceWatcher`接口，可枚举的设备，以异步方式，或在后台，并添加、 移除或更改设备时收到通知。 [回调](../windows/callback-function-windows-runtime-cpp-template-library.md)函数是此示例中的一个重要部分，因为它可以使该代码以指定的事件处理程序处理的后台操作的结果。 以下是完整的示例。  
  
> [!WARNING]
>  虽然通常使用 Windows 运行时 c + + 模板库中的通用 Windows 平台应用，但此示例使用一个控制台应用程序是为了进行说明。 函数如`wprintf_s`通用 Windows 平台应用中不可用。 有关类型和可以在通用 Windows 平台应用中使用的函数的详细信息，请参阅[通用 Windows 平台应用中不支持的 CRT 函数](../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md)并[Win32 和 COM 适用于 UWP 应用](/uwp/win32-and-com/win32-and-com-for-uwp-apps)。  
  
1.  包括 (`#include`) 所需的任何 Windows 运行时、 Windows 运行时 c + + 模板库或 c + + 标准库标头。  
  
     [!code-cpp[wrl-consume-event#2](../windows/codesnippet/CPP/how-to-handle-events-using-wrl_1.cpp)]  
  
     Windows.Devices.Enumeration.h 声明枚举设备所需的类型。  
  
     我们建议您在 .cpp 文件中使用 `using namespace` 指令使代码更具可读性。  
  
2.  声明应用程序的本地变量。 此示例中包含的枚举的设备和注册令牌，使其可以稍后取消订阅事件数的计数。  
  
     [!code-cpp[wrl-consume-event#7](../windows/codesnippet/CPP/how-to-handle-events-using-wrl_2.cpp)]  
  
3.  初始化 Windows 运行时。  
  
     [!code-cpp[wrl-consume-event#3](../windows/codesnippet/CPP/how-to-handle-events-using-wrl_3.cpp)]  
  
4.  创建[事件](../windows/event-class-windows-runtime-cpp-template-library.md)对象同步到主应用程序在枚举进程完成。  
  
     [!code-cpp[wrl-consume-event#4](../windows/codesnippet/CPP/how-to-handle-events-using-wrl_4.cpp)]  
  
    > [!NOTE]
    >  此事件是有关仅作为控制台应用程序的一部分的演示。 此示例使用事件来确保此应用退出前完成的异步操作。 在大多数应用中，您通常不等待异步操作完成。  
  
5.  创建的激活工厂`IDeviceWatcher`接口。  
  
     [!code-cpp[wrl-consume-event#5](../windows/codesnippet/CPP/how-to-handle-events-using-wrl_5.cpp)]  
  
     Windows 运行时使用完全限定的名称来标识类型。 `RuntimeClass_Windows_Devices_Enumeration_DeviceInformation`参数是由 Windows 运行时提供，包含所需的运行时类名称的字符串。  
  
6.  创建`IDeviceWatcher`对象。  
  
     [!code-cpp[wrl-consume-event#6](../windows/codesnippet/CPP/how-to-handle-events-using-wrl_6.cpp)]  
  
7.  使用`Callback`函数来订阅`Added`， `EnumerationCompleted`，和`Stopped`事件。  
  
     [!code-cpp[wrl-consume-event#8](../windows/codesnippet/CPP/how-to-handle-events-using-wrl_7.cpp)]  
  
     `Added`事件处理程序枚举的设备的计数递增。 之后发现有十个设备，它将停止枚举过程。  
  
     `Stopped`事件处理程序中移除事件处理程序，并设置完成事件。  
  
     `EnumerationCompleted`事件处理程序将停止枚举过程。 有数不足十个设备的情况下，我们处理此事件。  
  
    > [!TIP]
    >  此示例使用 lambda 表达式来定义回调。 此外可以使用函数对象 （函子） 函数指针或[std:: function](../standard-library/function-class.md)对象。 有关 lambda 表达式的详细信息，请参阅 [Lambda 表达式](../cpp/lambda-expressions-in-cpp.md)。  
  
8.  开始枚举过程。  
  
     [!code-cpp[wrl-consume-event#9](../windows/codesnippet/CPP/how-to-handle-events-using-wrl_8.cpp)]  
  
9. 等待枚举进程完成，然后打印一条消息。 所有 `ComPtr` 和 RAII 对象都离开范围并自动释放。  
  
     [!code-cpp[wrl-consume-event#10](../windows/codesnippet/CPP/how-to-handle-events-using-wrl_9.cpp)]  
  
 下面是完整的示例：  
  
 [!code-cpp[wrl-consume-event#1](../windows/codesnippet/CPP/how-to-handle-events-using-wrl_10.cpp)]  
  
## <a name="compiling-the-code"></a>编译代码  
 若要编译代码，将其复制然后将其粘贴到 Visual Studio 项目中，或将其粘贴在文件中名为`wrl-consume-events.cpp`然后在 Visual Studio 命令提示符窗口中运行以下命令。  
  
 `cl.exe wrl-consume-events.cpp runtimeobject.lib`  
  
## <a name="see-also"></a>请参阅  
 [Windows 运行时 C++ 模板库 (WRL)](../windows/windows-runtime-cpp-template-library-wrl.md)