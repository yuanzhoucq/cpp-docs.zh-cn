---
title: BSCMAKE 选项
ms.date: 11/04/2016
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
ms.openlocfilehash: b1d62e8d122cb4f08feef60d6936359b3e246749
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62272866"
---
# <a name="bscmake-options"></a>BSCMAKE 选项

> [!WARNING]
> 虽然安装 Visual Studio 时仍会安装 BSCMAKE，但 IDE 将不再使用它。 从 Visual Studio 2008 起，浏览信息和符号信息自动存储在解决方案文件夹的 SQL Server .sdf 文件中。

本部分介绍可用于控制 BSCMAKE 选项。 多个选项控制通过排除或包括特定的信息的浏览信息文件的内容。 排除选项可以允许 BSCMAKE 运行得更快，并可能会导致较小的.bsc 文件。 选项名称不区分大小写 (除 **/help**并 **/NOLOGO**)。

仅 **/NOLOGO**并 **/o**可从 Visual Studio 开发环境。  请参阅[设置C++Visual Studio 中的编译器和生成属性](../working-with-project-properties.md)有关的信息访问项目的属性页。

**/Ei (** *文件名*...**)**<br/>
从浏览信息文件中排除指定的包含文件的内容。 若要指定多个文件，请用空格分隔这些名称，并将列表括在括号中。 括号不是必需的如果只指定一个*文件名*。 使用 **/Ei**连同 **/Es**选项以排除未排除的文件 **/Es**。

**/El**<br/>
排除本地符号。 默认值是包含本地符号。 有关本地符号的详细信息，请参阅[创建.sbr 文件](creating-an-dot-sbr-file.md)。

**/Em**<br/>
排除宏的正文中的符号。 使用 **/e m**浏览信息文件中包含宏的名称。 默认值是包含宏名称和宏扩展的结果。

**/Er (** *符号*...**)**<br/>
从浏览信息文件中排除指定的符号。 若要指定多个符号名称，请用空格分隔这些名称，并将列表括在括号中。 括号不是必需的如果只指定一个*符号*。

**/Es**<br/>
从浏览信息文件中排除指定的绝对路径或在 INCLUDE 环境变量中指定的绝对路径中找到的每个包含文件。 (通常情况下，这些是系统包含文件，其中包含很多你可能不需要在浏览信息文件中的信息。)此选项不排除没有路径或相对路径或文件中包含的相对路径中找到使用指定的文件。 可以使用 **/Ei**选项和 **/Es**排除的文件 **/Es**不排除。 如果想要排除文件一部分的 **/Es**不包括，使用 **/Ei**而不是 **/Es**和列出你想要排除的文件。

**/errorreport:**[**none** &#124; **prompt** &#124; **queue** &#124; **send**]<br/>
可以将信息发送给 Microsoft，有关 bscmake.exe 中的内部错误。

有关详细信息 **/errorreport**，请参阅[/errorReport （报告内部编译器错误）](errorreport-report-internal-compiler-errors.md)。

**/HELP**<br/>
显示 BSCMAKE 命令行语法的摘要。

**/Iu**<br/>
包括未引用的符号。 默认情况下，BSCMAKE 不会记录任何已定义但未被引用的符号。 如果已打包的.sbr 文件，此选项不起该输入文件因为编译器已移除未引用的符号。

**/n**<br/>
强制非增量生成。 使用 **/n**强制完全生成浏览信息文件.bsc 文件是否存在并防止.sbr 文件被截断。 请参阅[BSCMAKE 如何生成.bsc 文件](how-bscmake-builds-a-dot-bsc-file.md)。

**/NOLOGO**<br/>
禁止显示 BSCMAKE 版权消息。

**/o** *filename*<br/>
指定浏览信息文件的名称。 默认情况下，BSCMAKE 提供浏览信息文件的第一个的.sbr 文件和.bsc 扩展的基名称。

**/S (** *文件名*...**)**<br/>
告知 BSCMAKE 处理指定的包含文件时遇到的第一次，否则排除。 使用此选项可以节省处理时间 （如标头，或.h、.c 或.cpp 源文件） 的文件时在多个源文件包含但预处理指令每次通过保持不变。 您可能想要使用此选项，如果文件在对要创建浏览信息文件不重要的方面进行了更改。 若要指定多个文件，请用空格分隔这些名称，并将列表括在括号中。 括号不是必需的如果只指定一个*文件名*。 如果你想要每次将包括排除的文件，请使用 **/Ei**或 **/Es**选项。

**/v**<br/>
提供详细输出，其中包括正在处理每个.sbr 文件的名称和完整 BSCMAKE 运行有关的信息。

**/?**<br/>
显示 BSCMAKE 命令行语法的简短摘要。

下面的命令行告知 BSCMAKE 执行完全生成 MAIN.bsc 从三个.sbr 文件操作。 它还指示 BSCMAKE 要排除的 TOOLBOX.h 重复实例：

```
BSCMAKE /n /S toolbox.h /o main.bsc file1.sbr file2.sbr file3.sbr
```

## <a name="see-also"></a>请参阅

[BSCMAKE 参考](bscmake-reference.md)
