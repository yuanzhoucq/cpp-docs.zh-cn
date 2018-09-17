---
title: 管理库 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
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
dev_langs:
- C++
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: dd6fff812d200e16b82994f9f9bbe598aface547
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/17/2018
ms.locfileid: "45713149"
---
# <a name="managing-a-library"></a>管理库

LIB 的默认模式是可以生成或修改的 COFF 对象库。 LIB 以此模式运行时不指定 /EXTRACT （若要将对象复制到一个文件） 或 /DEF （若要生成的导入库）。

若要生成对象和/或库从一个库，请使用以下语法：

```
LIB [options...] files...
```

此命令将创建一个库从一个或多个输入*文件*。 *文件*可以是 COFF 对象文件、 32 位 OMF 对象文件或现有的 COFF 库。 LIB 创建包含指定的文件中的所有对象的一个库。 如果输入的文件是一个 32 位 OMF 对象文件，LIB 将其转换到 COFF 之前生成库。 LIB 无法接受创建 LIB 的 16 位版本的库中的 32 位 OMF 对象。 必须先使用 16 位 LIB 提取对象;然后，作为 32 位 LIB 的输入，可以使用提取的对象文件。

默认情况下，LIB 来命名输出文件使用的第一个对象或库文件和扩展的基名称。 lib。 输出文件将在当前目录。 如果已存在具有相同名称的文件，该输出文件会替换现有文件。 若要保留现有的库，请使用 /OUT 选项指定输出文件的名称。

以下选项适用于生成和修改库：

**/LIBPATH:** *dir*<br/>
重写环境库路径。 有关详细信息，请参阅链接的说明[/LIBPATH](../../build/reference/libpath-additional-libpath.md)选项。

**/ 列表**<br/>
到标准输出将显示有关输出库的信息。 输出可以定向到一个文件。 可以使用 /LIST 来确定现有库的内容，而无需修改它。

**/ 名称：** *文件名*<br/>
当生成导入库，指定正在为其生成导入库的 DLL 的名称。

**/NODEFAULTLIB**<br/>
从其解析外部引用时搜索的库列表中删除一个或多个默认库。 请参阅[/NODEFAULTLIB](../../build/reference/nodefaultlib-ignore-libraries.md)有关详细信息。

**/ 输入输出：** *文件名*<br/>
重写默认输出文件名。 默认情况下，使用命令行和扩展上的第一个库或对象文件的基名称在当前目录中创建输出库。 lib。

**/ 删除：** *对象*<br/>
省略指定*对象*输出库中。 LIB 通过组合所有对象 （无论是在对象文件或库中），然后删除使用 /REMOVE 指定的任何对象来创建输出库。

**/SUBSYSTEM:**{**控制台** &AMP;#124; **EFI_APPLICATION** &AMP;#124; **EFI_BOOT_SERVICE_DRIVER** &AMP;#124; **EFI_ROM**&AMP;#124; **EFI_RUNTIME_DRIVER** &AMP;#124; **本机** &AMP;#124; **POSIX** &AMP;#124; **WINDOWS** &AMP;#124; **WINDOWSCE**} [，#[。 # #]]<br/>
告知操作系统如何运行通过链接到输出库创建的程序。 有关详细信息，请参阅链接的说明[/SUBSYSTEM](../../build/reference/subsystem-specify-subsystem.md)选项。

在命令行上指定的 LIB 选项不区分大小写。

LIB 可用于执行以下库管理任务：

- 若要将对象添加到库中，指定现有的库文件的名称和新对象的文件名。

- 若要组合库，请指定库文件名称。 您可以添加对象和库结合单个 LIB 命令。

- 若要替换为新对象的库成员，指定包含要替换的成员对象的库和新对象 （或包含它的库） 的文件名。 如果在多个输入文件中存在具有相同名称的对象，LIB 将放入输出库的 LIB 命令中指定的最后一个对象。 替换时库成员，请务必指定新的对象或库之后包含旧对象的库。

- 若要从库中删除成员，请使用 /REMOVE 选项。 LIB 处理后组合所有输入的对象，而不考虑命令行的顺序 /REMOVE 任何规范。

> [!NOTE]
>  您不能同时删除的成员并将其解压缩到同一个步骤中的文件。 必须先提取成员对象使用 /EXTRACT，然后运行 LIB 再次使用 /REMOVE。 此行为不同于其他 Microsoft 产品中提供 16 位 LIB （适用于 OMF 库）。

## <a name="see-also"></a>请参阅

[LIB 引用](../../build/reference/lib-reference.md)