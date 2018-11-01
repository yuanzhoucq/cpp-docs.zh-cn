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
ms.openlocfilehash: e5e7a60bf4607be55525b587df4942875126b50e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50556671"
---
# <a name="building-an-import-library-and-export-file"></a>生成导入库和导出文件

若要生成的导入库和导出文件，使用以下语法：

> **LIB /DEF**[**:**<em>deffile</em>] [*选项*] [*objfiles*] [*库*]

当指定 /DEF 时，LIB 从 LIB 命令中传递的导出规范创建输出文件。 有三种方法用于指定导出，建议使用的顺序依次列出：

1. 一个 **__declspec （dllexport)** 中的一个定义*objfiles*或*库*

1. /EXPORT 规范：*名称*LIB 命令行上

1. 中的定义**导出**中的语句*deffile*

这些是用于链接的导出程序时，指定导出的相同方法。 程序可以使用多个方法。 您可以指定部件的 LIB 命令 (如多个*objfiles*或 /EXPORT 规范) 中的 LIB 命令中的命令文件，正如您可以在 LINK 命令中。

以下选项将应用于生成导入库和导出文件：

> **/ 输入输出：** *导入*

重写默认输出文件名*导入*创建库。 默认名称如果未指定 /OUT，是第一个对象文件或库中的 LIB 命令和扩展的基名称。 lib。 导出的文件都有相同的基名称作为导入库和扩展。 exp。

> **/Export:** *entryname* \[ **=** *internalname*]\[，**\@**<em>序号</em>\[， **NONAME**]]\[，**数据**]

从你的程序，使其他程序可以调用该函数中导出函数。 您还可以导出数据 (使用**数据**关键字)。 通常在 DLL 中定义导出。

*Entryname*是函数或数据的项的名称，因为它是由调用程序。 或者，您可以指定*internalname*与函数定义的程序中; 默认情况下，已知*internalname*相同*entryname*。 *序号*如果不指定到的导出表中 1 到 65,535; 范围内指定索引*序号*，LIB 将分配一个。 **NONAME**关键字仅作为序号，导出该函数不带*entryname*。 **数据**关键字用于导出仅限数据的对象。

> **/INCLUDE:** *符号*

添加指定*符号*到符号表。 此选项可用于强制库对象，否则不会包含的使用。

请注意，是否创建.dll 之前，可以在初始步骤中，创建导入库，则必须通过同一组对象文件时生成.dll 文件，为通过生成导入库时。

## <a name="see-also"></a>请参阅

[使用导入库和导出文件](../../build/reference/working-with-import-libraries-and-export-files.md)
