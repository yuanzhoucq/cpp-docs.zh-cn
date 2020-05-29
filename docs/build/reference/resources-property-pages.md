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
ms.openlocfilehash: c4a3048bfa07e9635662534b510fa57caa091f00
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81336078"
---
# <a name="resources-property-page"></a>资源属性页

对于本机 Windows 桌面程序，生成调用[资源编译器 （rc.exe）](/windows/win32/menurc/resource-compiler)将图像、字符串表和 *.res*文件添加到二进制文件。 此属性页中公开的属性将传递给资源编译器，而不是C++编译器或链接器。 有关此处列出的属性及其映射到 RC 命令行选项的详细信息，请参阅[使用 RC（RC 命令行）。](/windows/win32/menurc/using-rc-the-rc-command-line-) 有关如何访问**参考资料**属性页的信息，请参阅[在 Visual Studio 中设置C++编译器和生成属性](../working-with-project-properties.md)。 若要以编程方式访问这些属性，请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCResourceCompilerTool>。

C++/CLI 应用程序中的 .NET 资源的属性在["托管资源属性页](managed-resources-property-page.md)"中公开。

## <a name="preprocessor-definitions"></a>预处理器定义

为资源编译器指定一个或多个定义。 （/d[宏]）

## <a name="undefine-preprocessor-definitions"></a>取消定义预处理器定义

取消定义符号。 （/u）

## <a name="culture"></a>culture

列出资源中使用的区域性（如美国英语或意大利语）。 （/l [数字]）

## <a name="additional-include-directories"></a>附加包含目录

指定要添加到包含路径的一个或多个目录;如果有多个，请使用分号分隔符。 （/I[路径]）

## <a name="ignore-standard-include-paths"></a>忽略标准包含路径

防止资源编译器在 INCLUDE 环境变量中指定的目录中搜索包含文件。 （/X）

## <a name="show-progress"></a>显示进度

将进度消息发送到输出窗口。 （/v）

## <a name="suppress-startup-banner"></a>取消显示启动版权标志

禁止显示启动横幅和信息消息 （/nologo）

## <a name="resource-file-name"></a>资源文件名

指定资源文件（/fo_file_）的名称

## <a name="null-terminate-strings"></a>空终止字符串

将 null 追加到字符串表中的所有字符串。 （/n）

## <a name="see-also"></a>另请参阅

[C++项目属性页引用](property-pages-visual-cpp.md)
