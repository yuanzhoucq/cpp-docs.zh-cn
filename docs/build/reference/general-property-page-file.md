---
title: “常规”属性页（文件）
ms.date: 08/30/2019
f1_keywords:
- VC.Project.VCFileConfiguration.ExcludedFromBuild
- VC.Project.VCFileConfiguration.Tool
ms.assetid: 26e3711e-9e7d-4e8d-bc4c-2474538efdad
ms.openlocfilehash: 41366e2eae479c3d00f79cc47da9100b22129d50
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/03/2019
ms.locfileid: "70218180"
---
# <a name="general-property-page-file"></a>“常规”属性页（文件）

本主题适用于 Windows 项目。 对于非 Windows 项目, 请参阅[Linux C++属性页引用](../../linux/prop-pages-linux.md)。

右键单击**解决方案资源管理器**的文件节点时, 将打开 "**配置属性**" 节点下的 "**常规**属性" 页。 它包含以下属性:

- **从生成中排除**

   指定文件是否应位于当前配置的生成中。

   若要以编程方式访问此属性，请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCFileConfiguration.ExcludedFromBuild%2A>。

- **内容**(仅适用于 UWP 应用。)指定文件是否包含要包含在应用包中的内容。

- **项类型**

   **项类型**指定在生成过程中用于处理文件的工具。 [扩展名为 Visual Studio 已知的文件](/visualstudio/extensibility/visual-cpp-project-extensibility?view=vs-2019#project-items)在此属性中具有默认值。 如果有自定义文件类型或希望替代已知文件类型的默认工具, 可以在此处指定自定义工具。 请参阅[指定自定义生成工具](../specifying-custom-build-tools.md)，获取详细信息。 您还可以使用此属性页来指定文件不是生成过程的一部分。

   下图显示了 *.cpp*文件的属性页。 这种类型的文件的默认**项类型**是**CC++ /编译器**(*cl*), 属性页公开了各种仅适用于此文件的编译器设置。

   ![项目项的 "常规属性" 页](media/file-general-item-type.png "项类型选择")

    下表列出了默认项类型:

    |文件扩展名|项目类型|默认工具|
    |-|-|-|
    |.appx|XAML 应用程序定义|[应用包装器](/windows/win32/appxpkg/make-appx-package--makeappx-exe-)|
    |. hlsl、cso|HLSL 编译器|[fxc.exe](/windows/win32/direct3dtools/fxc)|
    |.h|C/C++标头|[C/C++ 预处理器](../../preprocessor/c-cpp-preprocessor-reference.md)|
    |n/a|不参与生成|n/a|
    |.xml、xslt、.xsl|Xml|[XML 编辑器](/visualstudio/xml-tools/xml-editor)|
    |. .resw、. resjson|PRI 资源 (UWP 应用)|[Makepri.exe](/windows/uwp/app-resources/compile-resources-manually-with-makepri)|
    ||媒体 (UWP)|[应用包装器](/windows/win32/appxpkg/make-appx-package--makeappx-exe-)|
    |.xsd|XML 数据生成器工具|[XML 架构定义工具 (xsd.exe)](/dotnet/standard/serialization/xml-schema-definition-tool-xsd-exe)(需要 .NET 工作负荷。 不包含在 MSVC 中。)|
    ||清单工具|[mt.exe](/windows/win32/sbscs/mt-exe)|
    |.rc|资源|[Windows 资源编译器 (rc)](/windows/win32/menurc/resource-compiler)|
    |。 appxmanifest.xml|应用程序包清单|[应用包装器](/windows/win32/appxpkg/make-appx-package--makeappx-exe-)|
    |.obj|Object|[C/C++链接器 (link .exe)](cl-invokes-the-linker.md)|
    |。 .ttf|字体|n/a|
    |.txt|文本|n/a|
    |n/a|自定义生成工具|用户定义|
    |n/a|复制文件|n/a|
    |。 app.packagelayout|应用包布局|[应用包装器](/windows/win32/appxpkg/make-appx-package--makeappx-exe-)|
    |.resx|编译器托管资源|[Resgen.exe（资源文件生成器）](/dotnet/framework/tools/resgen-exe-resource-file-generator)|
    |。 natvis|C++调试器可视化文件|[Natvis 框架](/visualstudio/debugger/create-custom-views-of-native-objects)|
    |.jpg、.bmp、.ico 等。|图像|基于应用程序类型的资源编译器。|
    |.cpp|C/C++编译器|cl|

   若要以编程方式访问此属性，请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCFileConfiguration.Tool%2A>。

有关如何访问 "**配置属性**" 节点下的 "**常规**属性" 页的信息, 请参阅[在C++ Visual Studio 中设置编译器和生成属性](../working-with-project-properties.md)。

## <a name="see-also"></a>请参阅

[C++项目属性页引用](property-pages-visual-cpp.md)