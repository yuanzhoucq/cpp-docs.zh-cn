---
title: "生成导入库和导出文件 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VC.Project.VCLibrarianTool.ModuleDefinitionFile
- VC.Project.VCLibrarianTool.ExportNamedFunctions
- VC.Project.VCLibrarianTool.GenerateDebug
- VC.Project.VCLibrarianTool.ForceSymbolReferences
dev_langs: C++
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
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 979e052147f058e6c46a1c10b1dd89cfd36ee362
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="building-an-import-library-and-export-file"></a>生成导入库和导出文件
若要生成导入库和导出文件，请使用以下语法：  
  
```  
LIB /DEF[:deffile] [options] [objfiles] [libraries]  
```  
  
 当指定 /DEF 时，LIB 从 LIB 命令中传递的导出规范创建输出文件。 有三种方法，用于指定导出，建议使用的顺序依次列出：  
  
1.  A **__declspec （dllexport)**之一定义*objfiles*或*库*  
  
2.  /EXPORT 规范：*名称*LIB 命令行上  
  
3.  中的定义**导出**中的语句`deffile`  
  
 这些是你用于链接的导出程序时，指定导出的相同方法。 程序可以使用多个方法。 你可以指定部分的 LIB 命令 (如多个*objfiles*或 /EXPORT 规范) 在 LIB 命令中的命令文件，就像你可以在 LINK 命令中。  
  
 以下选项适用于生成导入库和导出文件：  
  
 / 输入输出：*导入*  
 重写的默认输出文件名*导入*正在创建的库。 如果未指定 /OUT，默认名称是第一个对象文件或库中 LIB 命令和扩展名的基名称。 lib。 导出文件有相同的基名称作为导入库和扩展。 exp。  
  
 / 导出： *entryname*[= *internalname*] [，@ `ordinal`[， **NONAME**]] [，**数据**]  
 从程序，以允许其他程序调用该函数导出函数。 你还可以导出数据 (使用**数据**关键字)。 通常在 DLL 中定义导出。  
  
 *Entryname*是函数或数据项的名称，因为它是用于调用程序。 或者，可以指定*internalname*已知定义的程序中; 默认情况下，该函数作为*internalname*相同*entryname*。 `ordinal`到的导出表中 1 到 65535; 范围内指定索引，如果不指定`ordinal`，LIB 将分配一个。 **NONAME**关键字仅作为是执行序号，导出该函数不带*entryname*。 **数据**关键字用来导出仅包含数据的对象。  
  
 / 包括：`symbol`  
 将指定的符号添加到符号表。 此选项可用于强制库对象，否则不会包含的使用。  
  
 请注意，是否创建.dll 之前，可以在初步步骤中，创建你导入的库，你必须传递同一套对象文件时，生成.dll 为通过生成导入库时。  
  
## <a name="see-also"></a>请参阅  
 [使用导入库和导出文件](../../build/reference/working-with-import-libraries-and-export-files.md)