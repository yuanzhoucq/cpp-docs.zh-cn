---
title: LIB 概述 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- Lib
dev_langs:
- C++
helpviewer_keywords:
- LIB [C++], modes
ms.assetid: e997d423-f574-434f-8b56-25585d137ee0
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 223f5284ed25b5a13fddef879e63ec2e480f3314
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/17/2018
ms.locfileid: "45703762"
---
# <a name="overview-of-lib"></a>LIB 概述

LIB 创建标准库、 导入库和导出的文件可用于[链接](../../build/reference/linker-options.md)时生成程序。 在命令提示符下运行 LIB。

在以下模式，可使用 LIB:

- [生成或修改 COFF 库](../../build/reference/managing-a-library.md)

- [提取到文件的成员对象](../../build/reference/extracting-a-library-member.md)

- [创建一个导出文件和导入库](../../build/reference/working-with-import-libraries-and-export-files.md)

这些模式是互斥的;一次只有一种模式中都可以使用 LIB。

## <a name="lib-options"></a>Lib 选项

下表列出了 lib.exe，其中包含指向详细信息的选项。

|选项|描述|
|-|-|
|**/ DEF**|创建导入库和导出文件。<br/><br/>有关详细信息请参阅[生成导入库和导出文件](../../build/reference/building-an-import-library-and-export-file.md)。|
|**/ERRORREPORT**|   内部错误的 lib.exe 向 Microsoft 发送信息。<br/><br/>有关详细信息请参阅[运行 LIB](../../build/reference/running-lib.md)。|
|**/EXPORT**|   从你的程序中导出函数。<br/><br/>有关详细信息请参阅[生成导入库和导出文件](../../build/reference/building-an-import-library-and-export-file.md)。|
|**/ 提取**|   创建一个包含一份现有库的成员的对象 (.obj) 文件。<br/><br/>有关详细信息请参阅[提取库成员](../../build/reference/extracting-a-library-member.md)。|
|**/INCLUDE**|   将符号添加到符号表。<br/><br/>有关详细信息请参阅[生成导入库和导出文件](../../build/reference/building-an-import-library-and-export-file.md)。|
|**/LIBPATH**|   重写环境库路径。<br/><br/>有关详细信息请参阅[管理库](../../build/reference/managing-a-library.md)。|
|**/ 列表**|   到标准输出将显示有关输出库的信息。<br/><br/>有关详细信息请参阅[管理库](../../build/reference/managing-a-library.md)。|
|**/LTCG**|   导致要生成使用链接时间代码生成库。<br/><br/>有关详细信息请参阅[运行 LIB](../../build/reference/running-lib.md)。|
|**/ 计算机**|   指定程序的目标平台。<br/><br/>有关详细信息请参阅[运行 LIB](../../build/reference/running-lib.md)。|
|**/ 名称**|   当生成导入库，指定正在为其生成导入库的 DLL 的名称。<br/><br/>有关详细信息请参阅[管理库](../../build/reference/managing-a-library.md)。|
|**/NODEFAULTLIB**|   从其解析外部引用时搜索的库列表中删除一个或多个默认库。<br/><br/>有关详细信息请参阅[管理库](../../build/reference/managing-a-library.md)。|
|**/NOLOGO**|   取消显示 LIB 版权消息和版本，并防止回显命令文件。<br/><br/>有关详细信息请参阅[运行 LIB](../../build/reference/running-lib.md)。|
|**/ 输入输出**|   重写默认输出文件名。<br/><br/>有关详细信息请参阅[管理库](../../build/reference/managing-a-library.md)。|
|**/ 删除**|   忽略输出库中的对象。<br/><br/>有关详细信息请参阅[管理库](../../build/reference/managing-a-library.md)。|
|**/SUBSYSTEM**|   告知操作系统如何运行通过链接到输出库创建的程序。<br/><br/>有关详细信息请参阅[管理库](../../build/reference/managing-a-library.md)。|
|**/VERBOSE**|   显示有关进度的会话，包括要添加的.obj 文件的名称的详细信息。<br/><br/>有关详细信息请参阅[运行 LIB](../../build/reference/running-lib.md)。|
|**/WX**|   将警告视为错误。<br/><br/>有关详细信息请参阅[运行 LIB](../../build/reference/running-lib.md)。|

## <a name="see-also"></a>请参阅

[LIB 引用](../../build/reference/lib-reference.md)<br/>
[LIB 输入文件](../../build/reference/lib-input-files.md)<br/>
[LIB 输出文件](../../build/reference/lib-output-files.md)<br/>
[其他 LIB 输出](../../build/reference/other-lib-output.md)<br/>
[库结构](../../build/reference/structure-of-a-library.md)