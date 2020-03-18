---
title: LIB 概述
description: 库工具 .lib 的使用和选项概述。
ms.date: 02/09/2020
helpviewer_keywords:
- LIB [C++], modes
ms.assetid: e997d423-f574-434f-8b56-25585d137ee0
ms.openlocfilehash: 4ed725f383d956adf7abcf1c68002dee51703013
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/17/2020
ms.locfileid: "79439011"
---
# <a name="overview-of-lib"></a>LIB 概述

在生成程序时，LIB （.lib）创建可用于[链接](linker-options.md)的标准库、导入库和导出文件。 LIB 在命令提示符下运行。

可以在以下模式中使用 LIB：

- [生成或修改 COFF 库](managing-a-library.md)

- [将成员对象提取到文件中](extracting-a-library-member.md)

- [创建导出文件和导入库](working-with-import-libraries-and-export-files.md)

这些模式互相排斥;一次只能在一种模式下使用 LIB。

## <a name="lib-options"></a>LIB 选项

下表列出了 lib 的选项，并提供了指向详细信息的链接。

|选项|说明|
|-|-|
|**/DEF**|创建导入库和导出文件。<br/><br/>有关详细信息，请参阅[构建导入库和导出文件](building-an-import-library-and-export-file.md)。|
|**/ERRORREPORT**| 已弃用。 有关详细信息，请参阅[运行 LIB](running-lib.md)。|
|**/EXPORT**|   从程序中导出函数。<br/><br/>有关详细信息，请参阅[构建导入库和导出文件](building-an-import-library-and-export-file.md)。|
|**/EXTRACT**|   创建一个对象（.obj）文件，该文件包含现有库的成员的副本。<br/><br/>有关详细信息，请参阅[提取库成员](extracting-a-library-member.md)。|
|**/INCLUDE**|   将符号添加到符号表中。<br/><br/>有关详细信息，请参阅[构建导入库和导出文件](building-an-import-library-and-export-file.md)。|
|**/LIBPATH**|   重写环境库路径。<br/><br/>有关详细信息，请参阅[管理库](managing-a-library.md)。|
|**/LINKREPRO**|   创建重现 lib 崩溃或内部错误所需的项目。<br/><br/>有关详细信息，请参阅[运行 LIB](running-lib.md)。|
|**/LINKREPROTARGET**|   仅当在指定文件中使用 lib 时才生成 **/LINKREPRO**项目。<br/><br/>有关详细信息，请参阅[运行 LIB](running-lib.md)。|
|**/LIST**|   显示有关输出库到标准输出的信息。<br/><br/>有关详细信息，请参阅[管理库](managing-a-library.md)。|
|**/LTCG**|   导致使用链接时间代码生成生成库。<br/><br/>有关详细信息，请参阅[运行 LIB](running-lib.md)。|
|**/MACHINE**|   指定程序的目标平台。<br/><br/>有关详细信息，请参阅[运行 LIB](running-lib.md)。|
|**/NAME**|   生成导入库时，指定正在为其生成导入库的 DLL 的名称。<br/><br/>有关详细信息，请参阅[管理库](managing-a-library.md)。|
|**/NODEFAULTLIB**|   在解析外部引用时，从它搜索的库列表中删除一个或多个默认库。<br/><br/>有关详细信息，请参阅[管理库](managing-a-library.md)。|
|**/NOLOGO**|   禁止显示 LIB 版权消息和版本号，并防止命令文件回显。<br/><br/>有关详细信息，请参阅[运行 LIB](running-lib.md)。|
|**/OUT**|   重写默认输出文件名。<br/><br/>有关详细信息，请参阅[管理库](managing-a-library.md)。|
|**/REMOVE**|   省略输出库中的对象。<br/><br/>有关详细信息，请参阅[管理库](managing-a-library.md)。|
|**/SUBSYSTEM**|   告知操作系统如何运行通过链接到输出库而创建的程序。<br/><br/>有关详细信息，请参阅[管理库](managing-a-library.md)。|
|**/VERBOSE**|   显示有关会话进度的详细信息，包括正在添加的 .obj 文件的名称。<br/><br/>有关详细信息，请参阅[运行 LIB](running-lib.md)。|
|**/WX**|   将警告视为错误。<br/><br/>有关详细信息，请参阅[运行 LIB](running-lib.md)。|

## <a name="see-also"></a>另请参阅

[LIB 引用](lib-reference.md)\
[LIB 输入文件](lib-input-files.md)\
[LIB 输出文件](lib-output-files.md)\
[其他 LIB 输出](other-lib-output.md)\
[库结构](structure-of-a-library.md)
