---
title: 如何：使用 WRL 激活和使用 Windows 运行时组件
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 54828f02-6af3-45d1-b965-d0104442f8d5
ms.openlocfilehash: 9e15886e9045f15adb929678ba45023ce80fb084
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69498396"
---
# <a name="how-to-activate-and-use-a-windows-runtime-component-using-wrl"></a>如何：使用 WRL 激活和使用 Windows 运行时组件

本文档演示如何使用 Windows 运行时C++模板库 (WRL) 初始化 Windows 运行时以及如何激活和使用 Windows 运行时组件。

若要使用组件, 您必须获取一个接口指针, 该指针指向由组件实现的类型。 由于 Windows 运行时的基础技术是组件对象模型 (COM), 因此必须遵循 COM 规则来维护类型的实例。 例如, 您必须维护确定何时从内存中删除该类型的*引用计数*。

为了简化 Windows 运行时的使用, Windows 运行时C++模板库提供了可自动执行引用计数的智能指针模板[ComPtr\<T >](comptr-class.md)。 当你声明变量时, 请`ComPtr<`指定*接口名称*`>` *标识符*。 若要访问接口成员, 请将箭头成员访问运算符 (`->`) 应用于标识符。

> [!IMPORTANT]
> 调用接口函数时, 请始终测试 HRESULT 返回值。

## <a name="activating-and-using-a-windows-runtime-component"></a>激活和使用 Windows 运行时组件

以下步骤使用`Windows::Foundation::IUriRuntimeClass`接口演示如何为 Windows 运行时组件创建激活工厂, 如何创建该组件的实例, 以及如何检索属性值。 它们还演示了如何初始化 Windows 运行时。 下面是完整的示例。

> [!IMPORTANT]
> 尽管通常在通用 Windows 平台 (UWP C++ ) 应用中使用 Windows 运行时模板库, 但本示例使用控制台应用程序进行说明。 某些函数 ( `wprintf_s`如) 在 UWP 应用中不可用。 有关可在 UWP 应用中使用的类型和函数的详细信息, 请参阅[通用 Windows 平台应用中不支持的 CRT 函数](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md)以及[Uwp 应用的 Win32 和 COM](/uwp/win32-and-com/win32-and-com-for-uwp-apps)。

#### <a name="to-activate-and-use-a-windows-runtime-component"></a>激活和使用 Windows 运行时组件

1. 包含 (`#include`) 任何所需 Windows 运行时、 C++ Windows 运行时模板库或C++标准库标头。

   [!code-cpp[wrl-consume-component#2](../codesnippet/CPP/how-to-activate-and-use-a-windows-runtime-component-using-wrl_1.cpp)]

   我们建议您在 .cpp 文件中使用 `using namespace` 指令使代码更具可读性。

2. 初始化应用程序在其中执行的线程。 每个应用都必须初始化其线程模型和线程模型。 此示例使用[Microsoft:: WRL:: 包装:: RoInitializeWrapper](roinitializewrapper-class.md)类来初始化 Windows 运行时, 并将[RO_INIT_MULTITHREADED](/windows/win32/api/roapi/ne-roapi-ro_init_type)指定为线程模型。 类在构造时调用, `Windows::Foundation::Uninitialize`在销毁时调用`Windows::Foundation::Initialize`。 `RoInitializeWrapper`

   [!code-cpp[wrl-consume-component#3](../codesnippet/CPP/how-to-activate-and-use-a-windows-runtime-component-using-wrl_2.cpp)]

   在第二个语句中, [RoInitializeWrapper:: HRESULT](roinitializewrapper-class.md#hresult)运算符`HRESULT` `Windows::Foundation::Initialize`从对的调用返回。

3. 为`ABI::Windows::Foundation::IUriRuntimeClassFactory`接口创建*激活工厂*。

   [!code-cpp[wrl-consume-component#4](../codesnippet/CPP/how-to-activate-and-use-a-windows-runtime-component-using-wrl_3.cpp)]

   Windows 运行时使用完全限定的名称标识类型。 `RuntimeClass_Windows_Foundation_Uri`参数是由 Windows 运行时提供的字符串, 它包含所需的运行时类名称。

4. 初始化表示 URI `"http://www.microsoft.com"`的[Microsoft:: WRL:: 包装:: HString](hstring-class.md)变量。

   [!code-cpp[wrl-consume-component#6](../codesnippet/CPP/how-to-activate-and-use-a-windows-runtime-component-using-wrl_4.cpp)]

   在 Windows 运行时中, 不会为 Windows 运行时将使用的字符串分配内存。 相反, Windows 运行时会在其维护并用于操作的缓冲区中创建字符串的副本, 然后将句柄返回到它创建的缓冲区。

5. 使用工厂方法创建`ABI::Windows::Foundation::IUriRuntimeClass`对象。 `IUriRuntimeClassFactory::CreateUri`

   [!code-cpp[wrl-consume-component#7](../codesnippet/CPP/how-to-activate-and-use-a-windows-runtime-component-using-wrl_5.cpp)]

6. 调用方法以检索`Domain`属性的值。 `IUriRuntimeClass::get_Domain`

   [!code-cpp[wrl-consume-component#8](../codesnippet/CPP/how-to-activate-and-use-a-windows-runtime-component-using-wrl_6.cpp)]

7. 将域名打印到控制台并返回。 所有 `ComPtr` 和 RAII 对象都离开范围并自动释放。

   [!code-cpp[wrl-consume-component#9](../codesnippet/CPP/how-to-activate-and-use-a-windows-runtime-component-using-wrl_7.cpp)]

   [WindowsGetStringRawBuffer](/windows/win32/api/winstring/nf-winstring-windowsgetstringrawbuffer)函数检索 URI 字符串的基础 Unicode 形式。

下面是完整示例:

[!code-cpp[wrl-consume-component#1](../codesnippet/CPP/how-to-activate-and-use-a-windows-runtime-component-using-wrl_8.cpp)]

## <a name="compiling-the-code"></a>编译代码

若要编译代码, 请复制代码, 然后将其粘贴到 Visual studio 项目中, 或粘贴到一个名`wrl-consume-component.cpp`为的文件中, 然后在 Visual Studio 命令提示符窗口中运行以下命令。

`cl.exe wrl-consume-component.cpp runtimeobject.lib`

## <a name="see-also"></a>请参阅

[Windows 运行时 C++ 模板库 (WRL)](windows-runtime-cpp-template-library-wrl.md)