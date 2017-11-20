---
title: "管理库 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
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
dev_langs: C++
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
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 6ef7f9b1cbeb3aeab28a4c02bce9099aaaf0078d
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="managing-a-library"></a>管理库
默认模式为 LIB 是生成或修改 COFF 对象的库。 LIB 在此模式下运行，如果不指定 /extract، （若要将对象复制到文件中） 或 /DEF （若要生成导入库）。  
  
 若要构建从对象和/或库的库，请使用以下语法：  
  
```  
LIB [options...] files...  
```  
  
 此命令从一个或多个输入创建库*文件*。 *文件*可以是 32 位 OMF 对象文件或现有 COFF 库 COFF 对象文件。 LIB 创建包含指定的文件中的所有对象的一个库。 如果输入的文件是 32 位 OMF 对象文件，LIB 将其转换为 COFF 生成库之前。 LIB 无法接受 LIB 16 位版本创建的库中的 32 位 OMF 对象。 你必须首先使用 16 位 LIB 提取对象;然后你可以作为 32 位 LIB 输入使用提取的对象文件。  
  
 默认情况下，LIB 来命名输出文件使用的第一个对象或库文件和扩展名的基名称。 lib。 输出文件放在当前目录中。 如果已存在具有相同名称的文件，输出文件将替换现有文件。 若要保留现有的库，请使用 /OUT 选项指定输出文件的名称。  
  
 以下选项应用于生成和修改库：  
  
 / LIBPATH:`dir`  
 重写环境库路径。 有关详细信息，请参阅链接的说明[/LIBPATH](../../build/reference/libpath-additional-libpath.md)选项。  
  
 / 列表  
 到标准输出中显示有关输出库的信息。 输出可以定向到一个文件。 /LIST 可用于确定现有库的内容，而无需对其进行修改。  
  
 / 名称： *filename*  
 在生成导入库时，指定正在为其生成导入库的 dll 的名称。  
  
 /NODEFAULTLIB  
 从的解析外部引用时搜索的库的列表中移除一个或多个默认库。 请参阅[/NODEFAULTLIB](../../build/reference/nodefaultlib-ignore-libraries.md)有关详细信息。  
  
 / 输入输出： *filename*  
 重写默认输出文件名。 默认情况下，在命令行和扩展的第一个库或对象文件的基名称与位于当前目录中创建输出库。 lib。  
  
 / 删除：*对象*  
 省略指定*对象*输出库中。 LIB 通过组合所有对象 （无论是在对象文件或库中），然后删除用 /REMOVE 指定的任何对象来创建输出库。  
  
 / 子系统: {控制台 &#124;EFI_APPLICATION &#124;EFI_BOOT_SERVICE_DRIVER &#124;EFI_ROM &#124;EFI_RUNTIME_DRIVER &#124;本机 &#124;POSIX &#124;WINDOWS &#124;WINDOWSCE} [，#[。 # #]]  
 通知操作系统如何运行通过链接到此输出库中创建的程序。 有关详细信息，请参阅链接的说明[/SUBSYSTEM](../../build/reference/subsystem-specify-subsystem.md)选项。  
  
 命令行上指定的 LIB 选项不区分大小写。  
  
 LIB 可用于执行以下库管理任务：  
  
-   若要将对象添加到库中，指定现有的库的文件名称和新的对象的文件名。  
  
-   若要组合库，请指定库文件名称。 您可以添加对象，并将库合并使用单个 LIB 命令。  
  
-   若要使用一个新对象替换库成员，指定包含要替换的成员对象的库和新的对象 （或包含它的库） 的文件名。 在多个输入文件中存在具有相同名称的对象，LIB 会将放入输出库 LIB 命令中指定的最后一个对象。 当替换库成员时，请务必指定之后包含旧对象的库的新对象或库。  
  
-   若要从库中删除成员，请使用 /REMOVE 选项。 LIB 处理后组合所有输入的对象，而不考虑命令行的顺序 /REMOVE 任何规范。  
  
> [!NOTE]
>  无法同时删除成员并将其提取到相同的步骤中的文件。 你必须首先提取成员对象使用 /extract،，然后运行 LIB 再次使用 /REMOVE。 此行为不同于其他 Microsoft 产品中提供 16 位 LIB （对于 OMF 库）。  
  
## <a name="see-also"></a>另请参阅  
 [LIB 引用](../../build/reference/lib-reference.md)