---
title: LIB 概述
ms.date: 11/04/2016
f1_keywords:
- Lib
helpviewer_keywords:
- LIB [C++], modes
ms.assetid: e997d423-f574-434f-8b56-25585d137ee0
ms.openlocfilehash: 97d7b8892574fbe485a8d6c5e344e4a77aaf8519
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/14/2019
ms.locfileid: "57820216"
---
# <a name="overview-of-lib"></a>LIB 概述

LIB 创建标准库、 导入库和导出的文件可用于[链接](linker-options.md)时生成程序。 在命令提示符下运行 LIB。

在以下模式，可使用 LIB:

- [生成或修改 COFF 库](managing-a-library.md)

- [提取到文件的成员对象](extracting-a-library-member.md)

- [创建一个导出文件和导入库](working-with-import-libraries-and-export-files.md)

这些模式是互斥的;一次只有一种模式中都可以使用 LIB。

## <a name="lib-options"></a>Lib 选项

下表列出了 lib.exe，其中包含指向详细信息的选项。

|选项|描述|
|-|-|
|**/DEF**|创建导入库和导出文件。<br/><br/>有关详细信息请参阅[生成导入库和导出文件](building-an-import-library-and-export-file.md)。|
|**/ERRORREPORT**|   内部错误的 lib.exe 向 Microsoft 发送信息。<br/><br/>有关详细信息请参阅[运行 LIB](running-lib.md)。|
|**/EXPORT**|   从你的程序中导出函数。<br/><br/>有关详细信息请参阅[生成导入库和导出文件](building-an-import-library-and-export-file.md)。|
|**/EXTRACT**|   创建一个包含一份现有库的成员的对象 (.obj) 文件。<br/><br/>有关详细信息请参阅[提取库成员](extracting-a-library-member.md)。|
|**/INCLUDE**|   将符号添加到符号表。<br/><br/>有关详细信息请参阅[生成导入库和导出文件](building-an-import-library-and-export-file.md)。|
|**/LIBPATH**|   重写环境库路径。<br/><br/>有关详细信息请参阅[管理库](managing-a-library.md)。|
|**/LIST**|   到标准输出将显示有关输出库的信息。<br/><br/>有关详细信息请参阅[管理库](managing-a-library.md)。|
|**/LTCG**|   导致要生成使用链接时间代码生成库。<br/><br/>有关详细信息请参阅[运行 LIB](running-lib.md)。|
|**/MACHINE**|   指定程序的目标平台。<br/><br/>有关详细信息请参阅[运行 LIB](running-lib.md)。|
|**/NAME**|   当生成导入库，指定正在为其生成导入库的 DLL 的名称。<br/><br/>有关详细信息请参阅[管理库](managing-a-library.md)。|
|**/NODEFAULTLIB**|   从其解析外部引用时搜索的库列表中删除一个或多个默认库。<br/><br/>有关详细信息请参阅[管理库](managing-a-library.md)。|
|**/NOLOGO**|   取消显示 LIB 版权消息和版本，并防止回显命令文件。<br/><br/>有关详细信息请参阅[运行 LIB](running-lib.md)。|
|**/OUT**|   重写默认输出文件名。<br/><br/>有关详细信息请参阅[管理库](managing-a-library.md)。|
|**/REMOVE**|   忽略输出库中的对象。<br/><br/>有关详细信息请参阅[管理库](managing-a-library.md)。|
|**/SUBSYSTEM**|   告知操作系统如何运行通过链接到输出库创建的程序。<br/><br/>有关详细信息请参阅[管理库](managing-a-library.md)。|
|**/VERBOSE**|   显示有关进度的会话，包括要添加的.obj 文件的名称的详细信息。<br/><br/>有关详细信息请参阅[运行 LIB](running-lib.md)。|
|**/WX**|   将警告视为错误。<br/><br/>有关详细信息请参阅[运行 LIB](running-lib.md)。|

## <a name="see-also"></a>请参阅

[LIB 引用](lib-reference.md)<br/>
[LIB 输入文件](lib-input-files.md)<br/>
[LIB 输出文件](lib-output-files.md)<br/>
[其他 LIB 输出](other-lib-output.md)<br/>
[库结构](structure-of-a-library.md)
