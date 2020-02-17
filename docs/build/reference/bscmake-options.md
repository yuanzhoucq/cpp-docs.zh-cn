---
title: BSCMAKE 选项
description: 引用 Microsoft BSCMAKE 实用程序命令行选项。
ms.date: 02/09/2020
f1_keywords:
- VC.Project.VCBscMakeTool.OutputFile
- VC.Project.VCBscMakeTool.SuppressStartupBanner
- VC.Project.VCBscMakeTool.PreserveSBR
helpviewer_keywords:
- /v BSCMAKE option
- Iu BSCMAKE option
- browse information files (.bsc), content
- /Er BSCMAKE option
- NOLOGO BSCMAKE option
- /s BSCMAKE option
- /Ei BSCMAKE option
- /o BSCMAKE option
- /NOLOGO BSCMAKE option
- /Iu BSCMAKE option
- s BSCMAKE option (/s)
- /Em BSCMAKE option
- Em BSCMAKE option
- Es BSCMAKE option
- files [C++], BSCMAKE
- Er BSCMAKE option
- BSCMAKE, options for controlling files
- controlling BSCMAKE options
- El BSCMAKE option
- /El BSCMAKE option
- /Es BSCMAKE option
- Ei BSCMAKE option
ms.assetid: fa2f1e06-c684-41cf-80dd-6a554835ebd2
ms.openlocfilehash: f0fd0e01d3325267ac175435aab65b5d0a9d47ea
ms.sourcegitcommit: 8414cd91297dea88c480e208c7b5301db9972f19
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/14/2020
ms.locfileid: "77257788"
---
# <a name="bscmake-options"></a>BSCMAKE 选项

> [!WARNING]
> 虽然安装 Visual Studio 时仍会安装 BSCMAKE，但 IDE 将不再使用它。 自 Visual Studio 2008 开始，浏览和符号信息会自动存储在解决方案文件夹中 SQL Server *`.sdf`* 文件中。

本部分介绍可用于控制 BSCMAKE 的选项。 通过排除或包含某些信息，几个选项控制浏览信息文件的内容。 排除选项可以使 BSCMAKE 运行得更快，并可能导致较小的 *`.bsc`* 文件。 选项名区分大小写（ **/help**和 **/nologo**除外）。

Visual Studio 开发环境中仅提供 **/nologo**和 **/o** 。  有关访问项目属性页的信息，请参阅[在 Visual Studio 中设置C++编译器和生成属性](../working-with-project-properties.md)。

**/Ei （** _filename_.。**）** \
从浏览信息文件中排除指定包含文件的内容。 若要指定多个文件，请用空格分隔名称，并将列表括在括号中。 如果只指定一个*文件名*，则不需要括号。 使用 **/Ei**和 **/Es**选项排除 **/Es**未排除的文件。

**/El**\
排除本地符号。 默认值为包括本地符号。 有关本地符号的详细信息，请参阅[创建 .Sbr 文件](creating-an-dot-sbr-file.md)。

**/Em**\
排除宏正文中的符号。 使用 **/Em**仅在浏览信息文件中包含宏的名称。 默认情况下，包括宏的名称和宏扩展的结果。

**/Er （** _符号_.。**）** \
从浏览信息文件中排除指定的符号。 若要指定多个符号名称，请用空格分隔名称，并将列表括在括号中。 如果只指定了一个*符号*，则不需要括号。

**/Es**\
排除使用绝对路径指定的每个包含文件，或在 INCLUDE 环境变量中指定的绝对路径中找到该文件。 （通常情况下，这些文件是系统包含文件，其中包含你在浏览信息文件中可能不需要的大量信息。）此选项不会排除指定的文件，而不是使用路径、相对路径或在包含的相对路径中找到的文件。 可以将 **/Ei**选项与 **/Es**一起使用，排除 **/Es**不能排除的文件。 如果只想排除某些文件，请使用 **/Ei**而不是 **/Es**，并列出要排除的文件。

**/errorreport：** [**none** &#124; **prompt** &#124; **queue** &#124; **send**] \
已弃用此选项。 从 Windows Vista 开始，错误报告由[Windows 错误报告（WER）](/windows/win32/wer/windows-error-reporting)设置控制。

**/Help**\
显示 BSCMAKE 命令行语法摘要。

**/Iu**\
包括未引用的符号。 默认情况下，BSCMAKE 不记录已定义但未引用的任何符号。 如果已打包 *`.sbr`* 文件，则此选项对该输入文件不起作用，因为编译器已删除未引用的符号。

**/n**\
强制非增量生成。 使用 **/n**强制完全生成浏览信息文件（无论 *`.bsc`* 文件是否存在），并防止 *`.sbr`* 文件被截断。 查看[BSCMAKE 如何生成 .Bsc 文件](how-bscmake-builds-a-dot-bsc-file.md)。

**/Nologo**\
禁止显示 BSCMAKE 版权消息。

**/o** *filename*\
指定浏览信息文件的名称。 默认情况下，BSCMAKE 为浏览信息文件提供第一个 *`.sbr`* 文件的基名称和一个 *`.bsc`* 扩展。

**/S （** _filename_.。**）** \
通知 BSCMAKE 在第一次遇到指定的包含文件时对其进行处理，否则将其排除。 使用此选项可以在多个源文件中包含文件（如标头或 *`.h`* 、 *`.c`* 或 *`.cpp`* 源文件的文件，但每次都不需要预处理指令时）来保存处理时间。 如果文件以对要创建的浏览信息文件不重要的方式进行了更改，则使用此选项。 若要指定多个文件，请用空格分隔名称，并用括号将该列表括起来。 如果只指定一个*文件名*，则不需要括号。 如果希望在每次包含文件时都排除该文件，请使用 **/Ei**或 **/Es**选项。

**/v**\
提供详细的输出，包括正在处理的每个 *`.sbr`* 文件的名称以及有关完整 BSCMAKE 运行的信息。

**/?** \
显示 BSCMAKE 命令行语法的简短摘要。

以下命令行通知 BSCMAKE 从三个 *`.sbr`* 文件执行总公司的完整生成。 它还通知 BSCMAKE 排除 "工具箱" 的重复实例：

```cmd
BSCMAKE /n /S toolbox.h /o main.bsc file1.sbr file2.sbr file3.sbr
```

## <a name="see-also"></a>另请参阅

[BSCMAKE 参考](bscmake-reference.md)
