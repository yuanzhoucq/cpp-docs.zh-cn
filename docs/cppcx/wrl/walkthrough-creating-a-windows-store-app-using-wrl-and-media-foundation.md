---
title: 演练：使用 WRL 和媒体基础创建 UWP 应用
ms.date: 04/23/2019
ms.topic: reference
ms.assetid: 0336c550-fbeb-4dc4-aa9b-660f9fc45382
ms.openlocfilehash: 5c6fd2613c34fdecdf9128ed6a5d22d563961939
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/21/2020
ms.locfileid: "80079893"
---
# <a name="walkthrough-creating-a-uwp-app-using-wrl-and-media-foundation"></a>演练：使用 WRL 和媒体基础创建 UWP 应用

> [!NOTE]
> 对于新的 UWP 应用和组件，我们建议使用[ C++/WinRT](/windows/uwp/cpp-and-winrt-apis/)，这是一个新的标准 c + + 17 语言投影，适用于 Windows 运行时 api。 C++/WinRT 从版本1803开始，在 Windows 10 SDK 中提供。 C++/WinRT 完全在标头文件中实现，旨在向您提供对新式 Windows API 的第一类访问。

在本教程中，你将了解如何使用 Windows 运行时C++模板库（WRL）创建使用[Microsoft 媒体基础](/windows/win32/medfound/microsoft-media-foundation-sdk)的通用 Windows 平台（UWP）应用。

此示例将创建一个向捕捉自网络摄像头的图像应用灰度效果的自定义媒体基础转换。 该应用利用 C++ 定义自定义转换，并利用 C# 将该组件用于转换捕捉的图像。

> [!NOTE]
> 除了 C#，你也可以利用 JavaScript、Visual Basic 或 C++ 来使用自定义转换组件。

在大多数情况下，可以使用C++/cx 创建 Windows 运行时。 但是，有时您必须使用 WRL。 例如，在为 Microsoft 媒体基础创建媒体扩展时，必须创建同时实现 COM 和 Windows 运行时接口的组件。 因为C++/cx 只能创建 Windows 运行时对象，所以，若要创建媒体扩展，必须使用 WRL，因为它允许同时实现 COM 接口和 Windows 运行时接口。

> [!NOTE]
> 尽管此代码示例很长，但它演示了创建有用的媒体基础转换所需的最低要求。 你可以将它作为自己的自定义转换的起点。 此示例与[media extensions 示例](https://code.msdn.microsoft.com/windowsapps/Media-extensions-sample-7b466096)进行了调整，该示例使用媒体扩展将效果应用于视频和解码视频，并创建生成媒体流的方案处理程序。

## <a name="prerequisites"></a>必备条件

- 在 Visual Studio 2017 和更高版本中，UWP 支持是一个可选组件。 若要安装它，请从 Windows "开始" 菜单打开 Visual Studio 安装程序，并找到你的 Visual Studio 版本。 选择 "**修改**"，然后确保选中 "**通用 Windows 平台开发**" 磁贴。 在 "**可选组件**" 下，检查 **C++ visual studio 2017 的 uwp 工具（v141）** 或 **C++ visual studio 2019 的 uwp 工具（v142）** 。 然后检查要使用的 Windows SDK 的版本。

- [Windows 运行时](/uwp/api/)的经验。

- 熟悉 COM。

- 网络摄像机。

## <a name="key-points"></a>关键点

- 要创建自定义媒体基础组件，请使用 Microsoft 接口定义语言 (MIDL) 定义文件定义一个接口，实现该接口，然后使其可从其他组件激活。

- `namespace` 和 `runtimeclass` 属性以及 `NTDDI_WIN8`[版本](/windows/win32/Midl/version)特性值是使用 WRL 的媒体基础组件的 MIDL 定义的重要部分。

- [Microsoft：： WRL：： RuntimeClass](runtimeclass-class.md)是自定义媒体基础组件的基类。 [Microsoft：： WRL：： RuntimeClassType：： WinRtClassicComMix](runtimeclasstype-enumeration.md)枚举值以模板参数形式提供，用于将类标记为同时用作 Windows 运行时类和典型的 COM 运行时类。

- [InspectableClass](inspectableclass-macro.md)宏实现基本 COM 功能，如引用计数和 `QueryInterface` 方法，并设置运行时类名称和信任级别。

- 使用 Microsoft：： WRL：：[Module 类](module-class.md)实现 DLL 入口点函数，例如[DllGetActivationFactory](/windows/win32/winrt/functions)、 [DllCanUnloadNow](/windows/win32/api/combaseapi/nf-combaseapi-dllcanunloadnow)和[DllGetClassObject](/windows/win32/api/combaseapi/nf-combaseapi-dllgetclassobject)。

- 将组件 DLL 链接到 runtimeobject.lib。 还在链接器行上指定[/WINMD](../../cppcx/compiler-and-linker-options-c-cx.md)以生成 Windows 元数据。

- 使用项目引用可使 WRL 组件可用于 UWP 应用。

### <a name="to-use-the-wrl-to-create-the-media-foundation-grayscale-transform-component"></a>使用 WRL 创建媒体基础灰度转换组件

1. 在 Visual Studio 中，创建一个**空白解决方案**项目。 为该项目命名，例如， *MediaCapture*。

1. 将**DLL （通用 Windows）** 项目添加到解决方案。 为该项目命名，例如， *GrayscaleTransform*。

1. 将**Midl 文件（.idl）** 文件添加到项目。 为文件命名，例如， *GrayscaleTransform*。

1. 将以下代码添加到 GrayscaleTransform：

   [!code-cpp[wrl-media-capture#1](../codesnippet/CPP/walkthrough-creating-a-windows-store-app-using-wrl-and-media-foundation_1.idl)]

1. 使用以下代码替换 `pch.h`的内容：

   [!code-cpp[wrl-media-capture#2](../codesnippet/CPP/walkthrough-creating-a-windows-store-app-using-wrl-and-media-foundation_2.h)]

1. 向项目中添加一个新的头文件，将其命名为 `BufferLock.h`，然后将内容替换为以下代码：

   [!code-cpp[wrl-media-capture#3](../codesnippet/CPP/walkthrough-creating-a-windows-store-app-using-wrl-and-media-foundation_3.h)]

1. 在此示例中不使用 `GrayscaleTransform.h`。 如有需要，可以将其从项目中删除。

1. 使用以下代码替换 `GrayscaleTransform.cpp`的内容：

   [!code-cpp[wrl-media-capture#4](../codesnippet/CPP/walkthrough-creating-a-windows-store-app-using-wrl-and-media-foundation_4.cpp)]

1. 向项目中添加一个新的模块定义文件，将其命名为 `GrayscaleTransform.def`，然后添加以下代码：

   ```
   EXPORTS
       DllCanUnloadNow                     PRIVATE
       DllGetActivationFactory             PRIVATE
       DllGetClassObject                   PRIVATE
   ```

1. 使用以下代码替换 `dllmain.cpp`的内容：

   [!code-cpp[wrl-media-capture#6](../codesnippet/CPP/walkthrough-creating-a-windows-store-app-using-wrl-and-media-foundation_6.cpp)]

1. 在项目的 "**属性页**" 对话框中，设置以下**链接器**属性。

   1. 在 "**输入**" 下，为**模块定义文件**指定 `GrayScaleTransform.def`。

   1. 此外，在 "**输入**" 下，将 `runtimeobject.lib`、`mfuuid.lib`和 `mfplat.lib` 添加到 "**其他依赖项**" 属性。

   1. 在**Windows 元数据**下，将 "**生成 Windows 元数据**" 设置为 **"是（/WINMD）"** 。

### <a name="to-use-the-wrl-the-custom-media-foundation-component-from-a-c-app"></a>在C#应用中使用 WRL 自定义媒体基础组件

1. 将新 **C#的空白应用（通用 Windows）** 项目添加到 `MediaCapture` 解决方案中。 为该项目命名，例如， *MediaCapture*。

1. 在**MediaCapture**项目中，添加对 `GrayscaleTransform` 项目的引用。 若要了解如何操作，请参阅[如何：使用引用管理器添加或删除引用](/visualstudio/ide/how-to-add-or-remove-references-by-using-the-reference-manager)。

1. 在 `Package.appxmanifest`的 "**功能**" 选项卡上，选择 "**麦克风**和**网络摄像机**"。 从网络摄像头中捕捉照片时需要这两项功能。

1. 在 `MainPage.xaml`中，将以下代码添加到根[网格](/uwp/api/Windows.UI.Xaml.Controls.Grid)元素：

   [!code-xml[wrl-media-capture#7](../codesnippet/Xaml/walkthrough-creating-a-windows-store-app-using-wrl-and-media-foundation_7.xaml)]

1. 使用以下代码替换 `MainPage.xaml.cs`的内容：

   [!code-cs[wrl-media-capture#8](../codesnippet/CSharp/walkthrough-creating-a-windows-store-app-using-wrl-and-media-foundation_8.cs)]

下图显示了 `MediaCapture app`。

![捕获照片的 MediaCapture 应用](../media/wrl_media_capture.png "WRL_Media_Capture")

## <a name="next-steps"></a>后续步骤

该示例演示如何从默认网络摄像头逐张捕捉照片。 [媒体扩展示例](https://code.msdn.microsoft.com/windowsapps/Media-extensions-sample-7b466096)执行的功能更多。 它演示如何枚举网络摄像头设备和使用本地方案处理程序，并演示对单张照片和视频流都产生影响的其他媒体效果。

## <a name="see-also"></a>另请参阅

[Windows 运行时 C++ 模板库 (WRL)](windows-runtime-cpp-template-library-wrl.md)<br/>
[Microsoft 媒体基础](/windows/win32/medfound/microsoft-media-foundation-sdk)<br/>
[媒体扩展示例](https://code.msdn.microsoft.com/windowsapps/Media-extensions-sample-7b466096)
