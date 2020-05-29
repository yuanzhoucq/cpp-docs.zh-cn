---
title: 演练：使用 WRL 和媒体基础创建 UWP 应用
ms.date: 04/23/2019
ms.topic: reference
ms.assetid: 0336c550-fbeb-4dc4-aa9b-660f9fc45382
ms.openlocfilehash: 272092982c5e9cc57f52043e08c8bd384c43ea96
ms.sourcegitcommit: 89d9e1cb08fa872483d1cde98bc2a7c870e505e9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/22/2020
ms.locfileid: "82031506"
---
# <a name="walkthrough-creating-a-uwp-app-using-wrl-and-media-foundation"></a>演练：使用 WRL 和媒体基础创建 UWP 应用

> [!NOTE]
> 对于新的 UWP 应用和组件，我们建议您使用[C++/WinRT，](/windows/uwp/cpp-and-winrt-apis/)这是 Windows 运行时 API 的新标准C++17语言投影。 从版本 1803 起，C++/WinRT 在 Windows 10 SDK 中可用。 C++/WinRT 完全在标头文件中实现，旨在为您提供对现代 Windows API 的一流访问权限。

在本教程中，您将学习如何使用 Windows 运行时C++模板库 （WRL） 创建使用[Microsoft 媒体基础](/windows/win32/medfound/microsoft-media-foundation-sdk)的通用 Windows 平台 （UWP） 应用。

此示例将创建一个向捕捉自网络摄像头的图像应用灰度效果的自定义媒体基础转换。 该应用利用 C++ 定义自定义转换，并利用 C# 将该组件用于转换捕捉的图像。

> [!NOTE]
> 除了 C#，你也可以利用 JavaScript、Visual Basic 或 C++ 来使用自定义转换组件。

在大多数情况下，可以使用C++/CX 创建 Windows 运行时。 但是，有时您必须使用 WRL。 例如，在为 Microsoft 媒体基础创建媒体扩展时，必须创建实现 COM 和 Windows 运行时接口的组件。 由于C++/CX 只能创建 Windows 运行时对象，因此必须使用 WRL，因为它支持实现 COM 和 Windows 运行时接口。

> [!NOTE]
> 尽管此代码示例很长，但它演示了创建有用的媒体基础转换所需的最低要求。 你可以将它作为自己的自定义转换的起点。 此示例根据[Media 扩展示例](https://code.msdn.microsoft.com/windowsapps/Media-extensions-sample-7b466096)改编，该示例使用媒体扩展将效果应用于视频、解码视频以及创建生成媒体流的方案处理程序。

## <a name="prerequisites"></a>先决条件

- 在 Visual Studio 2017 及更高版本中，UWP 支持是可选组件。 要安装它，请从 Windows "开始"菜单打开可视化工作室安装程序，然后查找您的视觉工作室版本。 选择 **"修改**"，然后确保选中**通用 Windows 平台开发**磁贴。 在 **"可选组件**"下，检查 Visual Studio 2017 的**UWP C++工具 （v141），** 检查 Visual Studio 2019**的 C++工具（v142）。** 然后检查要使用的 Windows SDK 版本。

- 体验[Windows 运行时](/uwp/api/)。

- 熟悉 COM。

- 网络摄像机。

## <a name="key-points"></a>关键点

- 要创建自定义媒体基础组件，请使用 Microsoft 接口定义语言 (MIDL) 定义文件定义一个接口，实现该接口，然后使其可从其他组件激活。

- 和`namespace``runtimeclass`属性以及`NTDDI_WIN8`[版本](/windows/win32/Midl/version)属性值是使用 WRL 的媒体基础组件的 MIDL 定义的重要组成部分。

- [Microsoft：WRL：运行时类](runtimeclass-class.md)是自定义媒体基础组件的基础类。 [Microsoft：：WRL：：运行时类类型：：WinRtClassicComMix](runtimeclasstype-enumeration.md)枚举值（作为模板参数提供）将类标记为 Windows 运行时类和经典 COM 运行时类。

- ["可检查类"](inspectableclass-macro.md)宏实现基本的 COM 功能，如引用`QueryInterface`计数和方法，并设置运行时类名称和信任级别。

- 使用 Microsoft：：WRL：：[模块类](module-class.md)实现 DLL 入口点函数，如[DllGet 激活工厂](/windows/win32/winrt/functions)[、DllCanUnloadNow](/windows/win32/api/combaseapi/nf-combaseapi-dllcanunloadnow)和[DllGetClassObject。](/windows/win32/api/combaseapi/nf-combaseapi-dllgetclassobject)

- 将组件 DLL 链接到 runtimeobject.lib。 还在链接器行上指定[/WINMD](../../cppcx/compiler-and-linker-options-c-cx.md)以生成 Windows 元数据。

- 使用项目引用使 WWP 应用可以访问 WRL 组件。

### <a name="to-use-the-wrl-to-create-the-media-foundation-grayscale-transform-component"></a>使用 WRL 创建媒体基础灰度变换组件

1. 在可视化工作室中，创建**一个空白解决方案**项目。 命名项目，例如，*媒体捕获*。

1. 向解决方案添加**DLL（通用 Windows）** 项目。 命名项目，例如，*灰度变换*。

1. 将**Midl 文件 （.idl）** 文件添加到项目中。 命名文件，例如，*灰度转换.idl*。

1. 将此代码添加到灰度转换.idl：

   [!code-cpp[wrl-media-capture#1](../codesnippet/CPP/walkthrough-creating-a-windows-store-app-using-wrl-and-media-foundation_1.idl)]

1. 使用以下代码替换 的内容`pch.h`：

   [!code-cpp[wrl-media-capture#2](../codesnippet/CPP/walkthrough-creating-a-windows-store-app-using-wrl-and-media-foundation_2.h)]

1. 向项目添加新的标头文件，命名它`BufferLock.h`，然后将内容替换为此代码：

   [!code-cpp[wrl-media-capture#3](../codesnippet/CPP/walkthrough-creating-a-windows-store-app-using-wrl-and-media-foundation_3.h)]

1. `GrayscaleTransform.h`此示例中不使用。 如有需要，可以将其从项目中删除。

1. 使用以下代码替换 的内容`GrayscaleTransform.cpp`：

   [!code-cpp[wrl-media-capture#4](../codesnippet/CPP/walkthrough-creating-a-windows-store-app-using-wrl-and-media-foundation_4.cpp)]

1. 向项目添加新的模块定义文件，命名它`GrayscaleTransform.def`，然后添加此代码：

   ```
   EXPORTS
       DllCanUnloadNow                     PRIVATE
       DllGetActivationFactory             PRIVATE
       DllGetClassObject                   PRIVATE
   ```

1. 使用以下代码替换 的内容`dllmain.cpp`：

   [!code-cpp[wrl-media-capture#6](../codesnippet/CPP/walkthrough-creating-a-windows-store-app-using-wrl-and-media-foundation_6.cpp)]

1. 在项目**的属性页**对话框中，设置以下**链接器**属性。

   1. 在 **"输入**"下，对于**模块定义文件**，指定`GrayScaleTransform.def`。

   1. 还在 **"输入**"`runtimeobject.lib`下`mfuuid.lib`，添加`mfplat.lib`和 添加到 **"附加依赖项"** 属性。

   1. 在**Windows 元数据**下，将 **"生成 Windows 元数据"** 设置为 **"是"（/WINMD）。**

### <a name="to-use-the-wrl-the-custom-media-foundation-component-from-a-c-app"></a>使用来自 C# 应用中的自定义媒体基础组件

1. 向`MediaCapture`解决方案添加新的**C# 空白应用（通用 Windows）** 项目。 命名项目，例如，*媒体捕获*。

1. 在**MediaCapture**项目中，添加对项目的`GrayscaleTransform`引用。 要了解如何[使用：使用参考管理器添加或删除引用](/visualstudio/ide/how-to-add-or-remove-references-by-using-the-reference-manager)。

1. 在`Package.appxmanifest`"**功能"** 选项卡上，选择 **"麦克风**"和 **"网络摄像头**"。 从网络摄像头中捕捉照片时需要这两项功能。

1. 在`MainPage.xaml`中，将此代码添加到根[网格](/uwp/api/windows.ui.xaml.controls.grid)元素：

   [!code-xml[wrl-media-capture#7](../codesnippet/Xaml/walkthrough-creating-a-windows-store-app-using-wrl-and-media-foundation_7.xaml)]

1. 使用以下代码替换 的内容`MainPage.xaml.cs`：

   [!code-cs[wrl-media-capture#8](../codesnippet/CSharp/walkthrough-creating-a-windows-store-app-using-wrl-and-media-foundation_8.cs)]

下图显示了 。 `MediaCapture app`

![捕获照片的 MediaCapture 应用程序](../media/wrl_media_capture.png "WRL_Media_Capture")

## <a name="next-steps"></a>后续步骤

该示例演示如何从默认网络摄像头逐张捕捉照片。 [媒体扩展示例](https://code.msdn.microsoft.com/windowsapps/Media-extensions-sample-7b466096)执行更多工作。 它演示如何枚举网络摄像头设备和使用本地方案处理程序，并演示对单张照片和视频流都产生影响的其他媒体效果。

## <a name="see-also"></a>请参阅

[Windows 运行时 C++ 模板库 (WRL)](windows-runtime-cpp-template-library-wrl.md)<br/>
[微软媒体基金会](/windows/win32/medfound/microsoft-media-foundation-sdk)<br/>
[媒体扩展示例](https://code.msdn.microsoft.com/windowsapps/Media-extensions-sample-7b466096)
