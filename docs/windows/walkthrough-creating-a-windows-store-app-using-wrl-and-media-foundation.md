---
title: "演练：使用 WRL 和 Media Foundation 创建 Windows 应用商店应用程序 | Microsoft Docs"
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
ms.assetid: 0336c550-fbeb-4dc4-aa9b-660f9fc45382
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 演练：使用 WRL 和 Media Foundation 创建 Windows 应用商店应用程序
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

了解如何使用 [!INCLUDE[cppwrl](../windows/includes/cppwrl_md.md)] ([!INCLUDE[cppwrl_short](../windows/includes/cppwrl_short_md.md)]) 来创建 [!INCLUDE[win8_appname_long](../build/includes/win8_appname_long_md.md)] 应用程序使用 [Microsoft 媒体基础](http://msdn.microsoft.com/library/windows/apps/ms694197)。  
  
 此示例将创建一个向捕捉自网络摄像头的图像应用灰度效果的自定义媒体基础转换。 该应用利用 C++ 定义自定义转换，并利用 C# 将该组件用于转换捕捉的图像。  
  
> [!NOTE]
>  除了 C#，你也可以利用 JavaScript、Visual Basic 或 C++ 来使用自定义转换组件。  
  
 大多数情况下，你可以使用 [!INCLUDE[cppwrt](../build/reference/includes/cppwrt_md.md)] ([!INCLUDE[cppwrt_short](../build/reference/includes/cppwrt_short_md.md)]) 来创建 [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)]组件。 (有关详细信息，请参阅 [Visual c + + 语言参考](../Topic/Visual%20C++%20Language%20Reference%20\(C++-CX\).md)。)但是，有时候需要使用 [!INCLUDE[cppwrl_short](../windows/includes/cppwrl_short_md.md)]。 例如，在为 Microsoft 媒体基础创建媒体扩展时，必须创建一个可同时实现 COM 接口和 [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)]接口的组件。 因为 [!INCLUDE[cppwrt_short](../build/reference/includes/cppwrt_short_md.md)] 只能创建 [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)]对象，而要创建媒体扩展，就必须使用 [!INCLUDE[cppwrl_short](../windows/includes/cppwrl_short_md.md)]，因为它可以同时实现 COM 接口和 [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)]接口。  
  
> [!NOTE]
>  尽管此代码示例很长，但它演示了创建有用的媒体基础转换所需的最低要求。 你可以将它作为自己的自定义转换的起点。 此示例是改编自 [媒体扩展示例](http://code.msdn.microsoft.com/windowsapps/Media-extensions-sample-7b466096), 、 后者使用媒体扩展将应用到视频效果、 视频解码，并创建生成媒体流的方案处理程序。  
  
## <a name="prerequisites"></a>先决条件  
  
-   它提供坚实基础 [Windows 运行时](http://msdn.microsoft.com/library/windows/apps/br211377.aspx)。  
  
-   熟悉 COM。  
  
-   网络摄像头。  
  
## <a name="key-points"></a>关键点  
  
-   要创建自定义媒体基础组件，请使用 Microsoft 接口定义语言 (MIDL) 定义文件定义一个接口，实现该接口，然后使其可从其他组件激活。  
  
-    `namespace` 和 `runtimeclass` 属性，与 `NTDDI_WIN8`[版本](http://msdn.microsoft.com/zh-cn/66ac5cf3-2230-44fd-aaf6-8013e4a4ae81) 属性值都是重要的部分使用的媒体基础组件的 MIDL 定义 [!INCLUDE[cppwrl_short](../windows/includes/cppwrl_short_md.md)]。  
  
-   [Microsoft::WRL::RuntimeClass](../windows/runtimeclass-class.md) 是自定义媒体基础组件的基类。  [Microsoft::WRL::RuntimeClassType::WinRtClassicComMix](../windows/runtimeclasstype-enumeration.md) 作为模板参数提供的枚举值将用作这两个类标记 [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)] 类和为经典的 COM 运行时类。  
  
-    [InspectableClass](../windows/inspectableclass-macro.md) 宏实现基本的 COM 功能，比如引用计数和 `QueryInterface` 方法，并设置运行时类名称和信任级别。  
  
-   使用 microsoft:: wrl::[模块类](https://www.microsoftonedoc.com/#/organizations/e6f6a65cf14f462597b64ac058dbe1d0/projects/3fedad16-eaf1-41a6-8f96-0c1949c68f32/containers/a3daf831-1c5f-4bbe-964d-503870caf874/tocpaths/b4acf5de-2f4c-4c8b-b5ff-9140d023ecbe/locales/en-US) 来实现 DLL 入口点函数，如 [为 dllgetactivation ­ Factory](http://msdn.microsoft.com/library/br205771.aspx), ，[DllCanUnloadNow](http://msdn.microsoft.com/library/windows/desktop/ms690368\(v=vs.85\).aspx), ，和 [DllGetClassObject](http://msdn.microsoft.com/library/windows/desktop/ms680760\(v=vs.85\).aspx)。  
  
-   将组件 DLL 链接到 runtimeobject.lib。 此外指定 [/WINMD](../Topic/Compiler%20and%20Linker%20options%20\(C++-CX\).md) 链接器行才能生成 Windows 元数据。  
  
-   使用项目引用，使 [!INCLUDE[cppwrl_short](../windows/includes/cppwrl_short_md.md)] 组件可供 [!INCLUDE[win8_appname_long](../build/includes/win8_appname_long_md.md)]应用访问。  
  
### <a name="to-use-the-includecppwrlshorttokencppwrlshortmdmd-to-create-the-media-foundation-grayscale-transform-component"></a>使用 [!INCLUDE[cppwrl_short](../windows/includes/cppwrl_short_md.md)] 创建媒体基础灰度转换组件  
  
1.  在 Visual Studio 中，创建 **空白解决方案** 项目。 该项目命名，例如， `MediaCapture`。  
  
2.  添加 **DLL （Windows 应用商店应用）** 到解决方案的项目。 该项目命名，例如， `GrayscaleTransform`。  
  
3.  添加 **Midl 文件 (.idl)** 到项目文件。 例如，命名该文件， `GrayscaleTransform.idl`。  
  
4.  将此代码添加到 GrayscaleTransform.idl。  
  
     [!code-cpp[wrl-media-capture#1](../windows/codesnippet/CPP/walkthrough-creating-a-windows-store-app-using-wrl-and-media-foundation_1.idl)]  
  
5.  用下面的代码替换 pch.h 的内容。  
  
     [!code-cpp[wrl-media-capture#2](../windows/codesnippet/CPP/walkthrough-creating-a-windows-store-app-using-wrl-and-media-foundation_2.h)]  
  
6.  向项目添加新的头文件、 命名 `BufferLock.h`, ，然后添加以下代码︰  
  
     [!code-cpp[wrl-media-capture#3](../windows/codesnippet/CPP/walkthrough-creating-a-windows-store-app-using-wrl-and-media-foundation_3.h)]  
  
7.  此示例中未使用 GrayscaleTransform.h。 如有需要，可以将其从项目中删除。  
  
8.  用下面的代码替换 GrayscaleTransform.cpp 的内容。  
  
     [!code-cpp[wrl-media-capture#4](../windows/codesnippet/CPP/walkthrough-creating-a-windows-store-app-using-wrl-and-media-foundation_4.cpp)]  
  
9. 向项目添加新的模块定义文件，将其 `GrayscaleTransform.def`, ，然后添加以下代码︰  
  
     [!CODE [wrl-media-capture#5](../CodeSnippet/VS_Snippets_Misc/wrl-media-capture#5)]  
  
10. 用下面的代码替换 dllmain.cpp 的内容。  
  
     [!code-cpp[wrl-media-capture#6](../windows/codesnippet/CPP/walkthrough-creating-a-windows-store-app-using-wrl-and-media-foundation_6.cpp)]  
  
11. 在项目的 **属性页** 对话框框中，设置以下 **链接器** 属性。  
  
    1.  在下 **输入**, ，为 **模块定义文件**, ，指定 `GrayScaleTransform.def`。  
  
    2.  此外，在 **输入**, ，添加 `runtimeobject.lib`, ，`mfuuid.lib`, ，和 `mfplatf.lib` 到 **附加依赖项** 属性。  
  
    3.  在下 **Windows 元数据**, ，请设置 **生成 Windows 元数据** 到 **是 (/ WINMD)**。  
  
### <a name="to-use-the-includecppwrlshorttokencppwrlshortmdmd-the-custom-media-foundation-component-from-a-c-app"></a>使用 [!INCLUDE[cppwrl_short](../windows/includes/cppwrl_short_md.md)] 从 C# 应用创建自定义媒体基础组件  
  
1.  添加一个新 **C# 空白应用 (XAML)** 项目合并为 `MediaCapture` 解决方案。 该项目命名，例如， `MediaCapture`。  
  
2.  在 **MediaCapture** 项目中，添加对引用 `GrayscaleTransform` 项目。 若要了解如何操作，请参阅 [如何︰ 添加或移除引用，使用引用管理器](../Topic/How%20to:%20Add%20or%20Remove%20References%20By%20Using%20the%20Reference%20Manager.md)。  
  
3.  在 Package.appxmanifest 中上 **功能** 选项卡上，选择 **麦克风** 和 **网络摄像头**。 从网络摄像头中捕捉照片时需要这两项功能。  
  
4.  在 MainPage.xaml 中，将此代码添加到根 [网格](http://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.grid.aspx) 元素︰  
  
     [!code-xml[wrl-media-capture#7](../windows/codesnippet/Xaml/walkthrough-creating-a-windows-store-app-using-wrl-and-media-foundation_7.xaml)]  
  
5.  用下面的代码替换 MainPage.xaml.cs 的内容。  
  
     [!code-cs[wrl-media-capture#8](../windows/codesnippet/CSharp/walkthrough-creating-a-windows-store-app-using-wrl-and-media-foundation_8.cs)]  
  
 下图展示了 MediaCapture 应用。  
  
 ![捕获照片的 MediaCapture 应用程序](../windows/media/wrl_media_capture.png "WRL_Media_Capture")  
  
## <a name="next-steps"></a>后续步骤  
 该示例演示如何从默认网络摄像头逐张捕捉照片。  [媒体扩展示例](http://code.msdn.microsoft.com/windowsapps/Media-extensions-sample-7b466096) 小或最大。 它演示如何枚举网络摄像头设备和使用本地方案处理程序，并演示对单张照片和视频流都产生影响的其他媒体效果。  
  
## <a name="see-also"></a>另请参阅  
 [Windows 运行时 c + + 模板库 (WRL)](../windows/windows-runtime-cpp-template-library-wrl.md)   
 [Microsoft Media Foundation](http://msdn.microsoft.com/library/windows/apps/ms694197)   
 [媒体扩展示例](http://code.msdn.microsoft.com/windowsapps/Media-extensions-sample-7b466096)