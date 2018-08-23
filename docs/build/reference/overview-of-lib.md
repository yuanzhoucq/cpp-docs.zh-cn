---
title: LIB 概述 |Microsoft 文档
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
ms.openlocfilehash: d8fd3d370da4f841e85086e3d061508d68414e96
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
ms.locfileid: "32379193"
---
# <a name="overview-of-lib"></a>LIB 概述
LIB 创建标准库，导入库和导出的文件可与[链接](../../build/reference/linker-options.md)时生成程序。 从命令提示符运行 LIB。  
  
 在以下模式，可使用 LIB:  
  
-   [生成或修改 COFF 库](../../build/reference/managing-a-library.md)  
  
-   [提取到文件的成员对象](../../build/reference/extracting-a-library-member.md)  
  
-   [创建一个导出文件和导入库](../../build/reference/working-with-import-libraries-and-export-files.md)  
  
 这些模式是互斥;你可以一次只有一种模式中使用 LIB。  
  
## <a name="lib-options"></a>Lib 选项  
 下表列出了 lib.exe 的详细信息的链接的选项。  
  
 **/DEF**  
 创建导入库和导出文件。  
  
 有关详细信息请参阅[生成导入库和导出文件](../../build/reference/building-an-import-library-and-export-file.md)。  
  
 **/ERRORREPORT**  
 向 Microsoft 发送有关 lib.exe 内部错误的信息。  
  
 有关详细信息请参阅[运行 LIB](../../build/reference/running-lib.md)。  
  
 **/EXPORT**  
 从你的程序中导出函数。  
  
 有关详细信息请参阅[生成导入库和导出文件](../../build/reference/building-an-import-library-and-export-file.md)。  
  
 **/ 提取**  
 创建对象 (.obj) 文件包含的一个成员的现有库的副本。  
  
 有关详细信息请参阅[提取库成员](../../build/reference/extracting-a-library-member.md)。  
  
 **/INCLUDE**  
 将符号添加到符号表。  
  
 有关详细信息请参阅[生成导入库和导出文件](../../build/reference/building-an-import-library-and-export-file.md)。  
  
 **/LIBPATH**  
 重写环境库路径。  
  
 有关详细信息请参阅[管理库](../../build/reference/managing-a-library.md)。  
  
 **/ 列表**  
 到标准输出中显示有关输出库的信息。  
  
 有关详细信息请参阅[管理库](../../build/reference/managing-a-library.md)。  
  
 **/LTCG**  
 导致要生成使用的链接时代码生成的库。  
  
 有关详细信息请参阅[运行 LIB](../../build/reference/running-lib.md)。  
  
 **/ 机**  
 指定程序的目标平台。  
  
 有关详细信息请参阅[运行 LIB](../../build/reference/running-lib.md)。  
  
 **/ 名称**  
 在生成导入库时，指定正在为其生成导入库的 dll 的名称。  
  
 有关详细信息请参阅[管理库](../../build/reference/managing-a-library.md)。  
  
 **/NODEFAULTLIB**  
 从的解析外部引用时搜索的库的列表中移除一个或多个默认库。  
  
 有关详细信息请参阅[管理库](../../build/reference/managing-a-library.md)。  
  
 **/NOLOGO**  
 取消显示 LIB 版权消息和版本，并防止回显的命令文件。  
  
 有关详细信息请参阅[运行 LIB](../../build/reference/running-lib.md)。  
  
 **/ 输入输出**  
 重写默认输出文件名。  
  
 有关详细信息请参阅[管理库](../../build/reference/managing-a-library.md)。  
  
 **/ 删除**  
 忽略输出库中的对象。  
  
 有关详细信息请参阅[管理库](../../build/reference/managing-a-library.md)。  
  
 **/SUBSYSTEM**  
 通知操作系统如何运行通过链接到此输出库中创建的程序。  
  
 有关详细信息请参阅[管理库](../../build/reference/managing-a-library.md)。  
  
 **/VERBOSE**  
 显示有关会话，包括所添加的.obj 文件的名称的进度的详细信息。  
  
 有关详细信息请参阅[运行 LIB](../../build/reference/running-lib.md)。  
  
 **/WX**  
 将警告视为错误。  
  
 有关详细信息请参阅[运行 LIB](../../build/reference/running-lib.md)。  
  
## <a name="see-also"></a>请参阅  
 [LIB 引用](../../build/reference/lib-reference.md)   
 [LIB 输入的文件](../../build/reference/lib-input-files.md)   
 [LIB 输出文件](../../build/reference/lib-output-files.md)   
 [其他 LIB 输出](../../build/reference/other-lib-output.md)   
 [库结构](../../build/reference/structure-of-a-library.md)