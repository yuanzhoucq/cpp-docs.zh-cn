---
title: 生成导入库和导出文件
ms.date: 09/05/2018
f1_keywords:
- VC.Project.VCLibrarianTool.ModuleDefinitionFile
- VC.Project.VCLibrarianTool.ExportNamedFunctions
- VC.Project.VCLibrarianTool.GenerateDebug
- VC.Project.VCLibrarianTool.ForceSymbolReferences
helpviewer_keywords:
- OUT library manager option
- INCLUDE library manager option
- /DEF library manager option
- exporting data
- import libraries, building
- -INCLUDE library manager option
- /OUT library manager option
- DEF library manager option
- -DEF library manager option
- -OUT library manager option
- /INCLUDE library manager option
- -EXPORT library manager option
- exporting data, export (.exp) files
- /EXPORT library manager option
- EXPORT library manager option
- .lib files
- EXP files
ms.assetid: 2fe4f30a-1dd6-4b05-84b5-0752e1dee354
ms.openlocfilehash: 5cb5224b3edaf84dbcb7c0429044a647fb5ac19a
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87229748"
---
# <a name="building-an-import-library-and-export-file"></a>生成导入库和导出文件

若要生成导入库和导出文件，请使用以下语法：

> **LIB/DEF**[**：**<em>deffile</em>] [*选项*] [*objfiles*] [*库*]

指定/DEF 时，LIB 将从在 LIB 命令中传递的导出规范创建输出文件。 有三种方法可以指定导出，按建议使用顺序列出：

1. **`__declspec(dllexport)`** 其中一个*objfiles*或*库*中的定义

1. LIB 命令行上的/EXPORT：*name*规范

1. *Deffile*中的**导出**语句的定义

这些方法与在链接导出程序时指定导出的方法相同。 程序可以使用多种方法。 可以在 LIB 命令的命令文件中指定 LIB 命令的各个部分（例如多个*objfiles*或/export 规范），就像在 LINK 命令中一样。

以下选项适用于构建导入库和导出文件：

> **/Out：** *导入*

重写正在创建的*导*入库的默认输出文件名。 如果未指定/OUT，则默认名称为 LIB 命令中第一个对象文件或库的基名称和扩展 .lib。 为导出文件提供与导入库相同的基名称和扩展名 .exp。

> **/Export：** *entryname* \[ **=** *internalname*] \[ ， **\@** <em>序数</em> \[ ， **NONAME**]] \[ ，**数据**]

从程序中导出函数，以允许其他程序调用函数。 您还可以导出数据（使用**data**关键字）。 通常，导出是在 DLL 中定义的。

*Entryname*是函数或数据项的名称，因为它将由调用程序使用。 还可以选择将*internalname*指定为定义程序中已知的函数;默认情况下， *internalname*与*entryname*相同。 *序号*指定从1到65535范围内的导出表中的索引;如果未指定*序数*，则 LIB 会分配一个。 **NONAME**关键字只将函数作为序号导出，而不包含*entryname*。 **Data**关键字用于导出仅限数据的对象。

> **/INCLUDE：** *符号*

将指定的*符号*添加到符号表中。 此选项可用于强制使用不会包括的库对象。

请注意，如果在初步步骤中创建了导入库，则在创建 .dll 之前，必须在生成 .dll 时传递相同的对象文件集，就像生成导入库时传递的一样。

## <a name="see-also"></a>另请参阅

[使用导入库和导出文件](working-with-import-libraries-and-export-files.md)
