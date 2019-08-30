---
title: 资源
ms.date: 08/28/2019
ms.topic: article
ms.assetid: dade2f6b-c51f-4c33-9023-41956ae4b5f6
f1_keywords:
- VC.Project.VCResourceCompilerTool.PreprocessorDefinitions
- VC.Project.VCResourceCompilerTool.UndefineProcessorDefinitions
- VC.Project.VCResourceCompilerTool.Culture
- VC.Project.VCResourceCompilerTool.AdditionalIncludeDirectories
- VC.Project.VCResourceCompilerTool.IgnoreStandardIncludePath
- VC.Project.VCResourceCompilerTool.ShowProgress
- VC.Project.VCResourceCompilerTool.SuppressStartupBanner
- VC.Project.VCResourceCompilerTool.ResourceOutputFileName
- VC.Project.VCResourceCompilerTool.NullTerminateStrings
- vc.project.AdditionalOptionsPage
ms.openlocfilehash: 916b6615d80000d601c909f771a1ec8f1b947927
ms.sourcegitcommit: e10a5feea193c249ddc5a6faba48e7c6d8784e73
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/30/2019
ms.locfileid: "70177343"
---
# <a name="resources-property-page"></a>资源属性页

对于本机 Windows 桌面程序, build 调用[资源编译器 (rc)](/windows/win32/menurc/resource-compiler)将图像、字符串表和 *.res*文件添加到二进制文件。 此属性页中公开的属性将传递给资源编译器, 而不是C++编译器或链接器。 有关此处列出的属性以及它们如何映射到 RC 命令行选项的详细信息, 请参阅[使用 rc (Rc 命令行)](/windows/win32/menurc/using-rc-the-rc-command-line-)。 有关如何访问 "**资源**" 属性页的信息, 请[参阅C++在 Visual Studio 中设置编译器和生成属性](../working-with-project-properties.md)。 若要以编程方式访问这些属性，请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCResourceCompilerTool>。

在 " C++[托管资源" 属性页](managed-resources-property-page.md)中公开了/CLI 应用程序中 .net 资源的属性。

## <a name="preprocessor-definitions"></a>预处理器定义

为资源编译器指定一个或多个定义。 (/d [宏])

## <a name="undefine-preprocessor-definitions"></a>取消定义预处理器定义

取消定义符号。 /u

## <a name="culture"></a>culture

列出资源中使用的区域性 (如美国英语或意大利语)。 (/l [数字])

## <a name="additional-include-directories"></a>附加包含目录

指定一个或多个要添加到包含路径中的目录;如果多个分隔符, 请使用分号分隔符。 (/I [路径])

## <a name="ignore-standard-include-paths"></a>忽略标准包含路径

阻止资源编译器在 INCLUDE 环境变量中指定的目录中搜索包含文件。 上次

## <a name="show-progress"></a>显示进度

将进度消息发送到输出窗口。 /v

## <a name="suppress-startup-banner"></a>取消显示启动版权标志

禁止显示启动版权标志和信息消息 (/nologo)

## <a name="resource-file-name"></a>资源文件名称

指定资源文件的名称 (/fo [文件])

## <a name="null-terminate-strings"></a>Null 终止字符串 

向字符串表中的所有字符串追加 null。 /n

## <a name="see-also"></a>请参阅

[C++项目属性页引用](property-pages-visual-cpp.md)