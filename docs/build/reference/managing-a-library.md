---
title: 管理库
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCLibrarianTool.OVERWRITEAllDefaultLibraries
- VC.Project.VCLibrarianTool.AdditionalDependencies
- VC.Project.VCLibrarianTool.RemoveObjects
- VC.Project.VCLibrarianTool.LibraryPaths
- VC.Project.VCLibrarianTool.OutputFile
- VC.Project.VCLibrarianTool.OVERWRITEDefaultLibraryNames
- VC.Project.VCLibrarianTool.AdditionalLibraryDirectories
- VC.Project.VCLibrarianTool.ListContentsFile
- VC.Project.VCLibrarianTool.ListContents
- VC.Project.VCLibrarianTool.SubSystemVersion
- VC.Project.VCLibrarianTool.OVERWRITEDefaultLibraryName
- VC.Project.VCLibrarianTool.SubSystem
helpviewer_keywords:
- /LIBPATH library manager option
- OUT library manager option
- CONVERT library manager option
- LIBPATH library manager option
- /LIST library manager option
- object files, building and modifying
- -LINK50COMPAT library manager option
- REMOVE library manager option
- SUBSYSTEM library manager option
- /LINK50COMPAT library manager option
- /OUT library manager option
- LIB [C++], managing COFF libraries
- -CONVERT library manager option
- LINK50COMPAT library manager option
- -OUT library manager option
- -REMOVE library manager option
- -LIST library manager option
- /SUBSYSTEM library manager option
- -SUBSYSTEM library manager option
- /REMOVE library manager option
- -LIBPATH library manager option
- object files
- LIST library manager option
- /CONVERT library manager option
ms.assetid: f56a8b85-fbdc-4c09-8d8e-00f0ffe1da53
ms.openlocfilehash: de55059834a0887d487b7be38377af9984512b75
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81336405"
---
# <a name="managing-a-library"></a>管理库

LIB 的默认模式是生成或修改 COFF 对象库。 如果不指定 /EXTRACT（将对象复制到文件）或 /DEF（生成导入库），LIB 将在此模式下运行。

要从对象和/或库生成库，请使用以下语法：

```
LIB [options...] files...
```

此命令从一个或多个输入*文件*创建库。 *这些文件*可以是 COFF 对象文件、32 位 OMF 对象文件或现有的 COFF 库。 LIB 创建一个库，其中包含指定文件中的所有对象。 如果输入文件是 32 位 OMF 对象文件，LIB 在构建库之前将其转换为 COFF。 LIB 不能接受由 16 位版本的 LIB 创建的库中的 32 位 OMF 对象。 您必须首先使用 16 位 LIB 提取对象;因此，您必须首先使用 16 位 LIB 来提取对象。然后，您可以使用提取的对象文件作为 32 位 LIB 的输入。

默认情况下，LIB 使用第一个对象或库文件的基本名称以及扩展名 .lib 命名输出文件。 输出文件放在当前目录中。 如果文件已存在同名文件，则输出文件将替换现有文件。 要保留现有库，请使用 /OUT 选项为输出文件指定名称。

以下选项适用于构建和修改库：

**/LIBPATH：** *dir*<br/>
重写环境库路径。 有关详细信息，请参阅[LINK/LIBPATH](libpath-additional-libpath.md)选项的说明。

**/LIST**<br/>
显示有关输出库到标准输出的信息。 输出可以重定向到文件。 您可以使用 /LIST 来确定现有库的内容，而无需对其进行修改。

**/NAME：***文件名*<br/>
生成导入库时，指定正在为其生成导入库的 DLL 的名称。

**/NODEFAULTLIB**<br/>
从解析外部引用时搜索的库列表中删除一个或多个默认库。 有关详细信息，请参阅[/NODEFAULTLIB。](nodefaultlib-ignore-libraries.md)

**/OUT：***文件名*<br/>
覆盖默认输出文件名。 默认情况下，输出库在当前目录中创建，命令行上的第一个库或对象文件的基本名称以及扩展点 .lib。

**/REMOVE：***对象*<br/>
从输出库中省略指定的*对象*。 LIB 通过合并所有对象（无论是在对象文件还是库中），然后删除使用 /REMOVE 指定的任何对象来创建输出库。

**/SUBSYSTEM：**[ **WINDOWS** **&#124;EFI_APPLICATION&#124;&#124;EFI_BOOT_SERVICE_DRIVER** **CONSOLE** **&#124;EFI_ROMEFI_ROM** **EFI_ROM** **POSIX** **&#124;EFI_RUNTIME_DRIVER&#124;****本机**&#124; &#124; **WINDOWS&#124;** WINDOWS_______________&#124; &#124;&#124;&#124;&#124;<br/>
告诉操作系统如何运行通过链接到输出库创建的程序。 有关详细信息，请参阅[LINK/SUBSYSTEM](subsystem-specify-subsystem.md)选项的说明。

在命令行上指定的 LIB 选项不区分大小写。

您可以使用 LIB 执行以下库管理任务：

- 要将对象添加到库，请指定现有库的文件名和新对象的文件名。

- 要合并库，请指定库文件名。 您可以添加对象并将库与单个 LIB 命令合并。

- 要将库成员替换为新对象，请指定包含要替换的成员对象的库以及新对象（或包含该对象的库）的文件名。 当多个输入文件中存在具有相同名称的对象时，LIB 会将 LIB 命令中指定的最后一个对象放入输出库中。 替换库成员时，请确保在包含旧对象的库之后指定新对象或库。

- 要从库中删除成员，请使用 /REMOVE 选项。 LIB 在组合所有输入对象后处理 /REMOVE 的任何规范，而不考虑命令行顺序。

> [!NOTE]
> 不能同时删除成员并将其提取到同一步骤中的文件。 您必须首先使用 /EXTRACT 提取成员对象，然后使用 /REMOVE 再次运行 LIB。 此行为不同于其他 Microsoft 产品中提供的 16 位 LIB（用于 OMF 库）。

## <a name="see-also"></a>另请参阅

[LIB 参考](lib-reference.md)
