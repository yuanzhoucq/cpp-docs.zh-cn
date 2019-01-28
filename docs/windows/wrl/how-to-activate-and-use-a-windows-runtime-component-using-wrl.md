---
title: 如何：激活和使用 Windows 运行时组件使用 WRL
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 54828f02-6af3-45d1-b965-d0104442f8d5
ms.openlocfilehash: ccc64769ca319e8aba141ce95a00eb876cc051f3
ms.sourcegitcommit: c85c8a1226d8fbbaa29f4691ed719f8e6cc6575c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/24/2019
ms.locfileid: "54893959"
---
# <a name="how-to-activate-and-use-a-windows-runtime-component-using-wrl"></a>如何：激活和使用 Windows 运行时组件使用 WRL

本文档演示如何使用 Windows 运行时 c + + 模板库 (WRL) 初始化 Windows 运行时以及如何进行激活和使用 Windows 运行时组件。

若要使用的组件，必须获取由该组件实现的类型的接口指针。 并且由于 Windows 运行时的基础技术是组件对象模型 (COM)，必须遵循 COM 规则以维护类型的实例。 例如，你必须维持*引用计数*，它确定何时从内存中删除类型。

为了简化使用 Windows 运行时，Windows 运行时 c + + 模板库，提供了智能指针模板[ComPtr\<T >](comptr-class.md)，来自动执行引用计数。 当您声明变量时，指定`ComPtr<`*接口名称*`>` *标识符*。 若要访问接口成员，将应用箭头成员访问运算符 (`->`) 的标识符。

> [!IMPORTANT]
> 当调用接口函数时，始终测试 HRESULT 返回值。

## <a name="activating-and-using-a-windows-runtime-component"></a>激活和使用 Windows 运行时组件

以下步骤使用`Windows::Foundation::IUriRuntimeClass`接口来演示如何创建 Windows 运行时组件的激活工厂、 创建该组件的实例并检索属性值。 它们还演示如何初始化 Windows 运行时。 以下是完整的示例。

> [!IMPORTANT]
> 虽然通常使用 Windows 运行时 c + + 模板库中的通用 Windows 平台 (UWP) 应用，但此示例使用一个控制台应用程序是为了进行说明。 函数如`wprintf_s`UWP 应用中不可用。 有关类型和可以在 UWP 应用中使用的函数的详细信息，请参阅[通用 Windows 平台应用中不支持的 CRT 函数](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md)并[Win32 和 COM 适用于 UWP 应用](/uwp/win32-and-com/win32-and-com-for-uwp-apps)。

#### <a name="to-activate-and-use-a-windows-runtime-component"></a>若要激活和使用 Windows 运行时组件

1. 包括 (`#include`) 所需的任何 Windows 运行时、 Windows 运行时 c + + 模板库或 c + + 标准库标头。

   [!code-cpp[wrl-consume-component#2](../codesnippet/CPP/how-to-activate-and-use-a-windows-runtime-component-using-wrl_1.cpp)]

   我们建议你在 .cpp 文件中使用 `using namespace` 指令使代码更具可读性。

2. 初始化应用程序在其中执行的线程。 每个应用必须初始化其线程和线程模型。 此示例使用[Microsoft::WRL::Wrappers::RoInitializeWrapper](roinitializewrapper-class.md)类来初始化 Windows 运行时和指定[RO_INIT_MULTITHREADED](/windows/desktop/api/roapi/ne-roapi-ro_init_type)作为线程模型。 `RoInitializeWrapper`类调用`Windows::Foundation::Initialize`在构建过程中和`Windows::Foundation::Uninitialize`时销毁。

   [!code-cpp[wrl-consume-component#3](../codesnippet/CPP/how-to-activate-and-use-a-windows-runtime-component-using-wrl_2.cpp)]

   在第二个语句中， [RoInitializeWrapper::HRESULT](roinitializewrapper-class.md#hresult)运算符将返回`HRESULT`调用`Windows::Foundation::Initialize`。

3. 创建*激活工厂*为`ABI::Windows::Foundation::IUriRuntimeClassFactory`接口。

   [!code-cpp[wrl-consume-component#4](../codesnippet/CPP/how-to-activate-and-use-a-windows-runtime-component-using-wrl_3.cpp)]

   Windows 运行时使用完全限定的名称来标识类型。 `RuntimeClass_Windows_Foundation_Uri`参数是由 Windows 运行时提供，包含所需的运行时类名称的字符串。

4. 初始化[Microsoft::WRL::Wrappers::HString](hstring-class.md)表示的 URI 的变量`"http://www.microsoft.com"`。

   [!code-cpp[wrl-consume-component#6](../codesnippet/CPP/how-to-activate-and-use-a-windows-runtime-component-using-wrl_4.cpp)]

   在 Windows 运行时，不为 Windows 运行时将使用一个字符串来分配内存。 相反，Windows 运行时，它维护和使用进行操作，，然后返回一个句柄到缓冲区它创建的缓冲区中创建您的字符串的副本。

5. 使用`IUriRuntimeClassFactory::CreateUri`工厂方法来创建`ABI::Windows::Foundation::IUriRuntimeClass`对象。

   [!code-cpp[wrl-consume-component#7](../codesnippet/CPP/how-to-activate-and-use-a-windows-runtime-component-using-wrl_5.cpp)]

6. 调用`IUriRuntimeClass::get_Domain`方法来检索的值`Domain`属性。

   [!code-cpp[wrl-consume-component#8](../codesnippet/CPP/how-to-activate-and-use-a-windows-runtime-component-using-wrl_6.cpp)]

7. 打印到控制台的域名，并返回。 所有 `ComPtr` 和 RAII 对象都离开范围并自动释放。

   [!code-cpp[wrl-consume-component#9](../codesnippet/CPP/how-to-activate-and-use-a-windows-runtime-component-using-wrl_7.cpp)]

   [WindowsGetStringRawBuffer](/windows/desktop/api/winstring/nf-winstring-windowsgetstringrawbuffer)函数检索基础 Unicode 形式的 URI 字符串。

下面是完整的示例：

[!code-cpp[wrl-consume-component#1](../codesnippet/CPP/how-to-activate-and-use-a-windows-runtime-component-using-wrl_8.cpp)]

## <a name="compiling-the-code"></a>编译代码

若要编译代码，将其复制然后将其粘贴到 Visual Studio 项目中，或将其粘贴在文件中名为`wrl-consume-component.cpp`然后在 Visual Studio 命令提示符窗口中运行以下命令。

`cl.exe wrl-consume-component.cpp runtimeobject.lib`

## <a name="see-also"></a>请参阅

[Windows 运行时 C++ 模板库 (WRL)](windows-runtime-cpp-template-library-wrl.md)