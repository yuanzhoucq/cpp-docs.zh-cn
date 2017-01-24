---
title: "生成导入库和导出文件 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VC.Project.VCLibrarianTool.ModuleDefinitionFile"
  - "VC.Project.VCLibrarianTool.ExportNamedFunctions"
  - "VC.Project.VCLibrarianTool.GenerateDebug"
  - "VC.Project.VCLibrarianTool.ForceSymbolReferences"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - ".lib 文件"
  - "/DEF 库管理器选项"
  - "/EXPORT 库管理器选项"
  - "/INCLUDE 库管理器选项"
  - "/OUT 库管理器选项"
  - "DEF 库管理器选项"
  - "-DEF 库管理器选项"
  - "EXP 文件"
  - "EXPORT 库管理器选项"
  - "-EXPORT 库管理器选项"
  - "导出数据"
  - "导出数据, 导出 (.exp) 文件"
  - "导入库, 生成"
  - "INCLUDE 库管理器选项"
  - "-INCLUDE 库管理器选项"
  - "OUT 库管理器选项"
  - "-OUT 库管理器选项"
ms.assetid: 2fe4f30a-1dd6-4b05-84b5-0752e1dee354
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 生成导入库和导出文件
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

若要生成导入库和导出文件，请使用下列语法：  
  
```  
LIB /DEF[:deffile] [options] [objfiles] [libraries]  
```  
  
 若指定了 \/DEF，则 LIB 从 LIB 命令中传递的导出规范创建输出文件。  有三种指定导出的方法，按照建议的使用顺序依次为：  
  
1.  *objfiles* 或 *libraries* 之一中的 **\_\_declspec\(dllexport\)** 定义  
  
2.  LIB 命令行中的 \/EXPORT:*name* 规范  
  
3.  `deffile` 的 **EXPORTS** 语句中的定义  
  
 这些方法与链接导出程序时用来指定导出的方法相同。  程序可使用一种以上的方法。  与在 LINK 命令中一样，在 LIB 命令的命令文件中也可以指定 LIB 命令的各部分（如多个 *objfiles* 或 \/EXPORT 规范）。  
  
 下列选项适用于生成导入库和导出文件：  
  
 \/OUT:*import*  
 重写正在创建的 *import* 库的默认输出文件名。  未指定 \/OUT 时，默认名称是 LIB 命令中第一个对象文件或库的基文件名和扩展名 .lib。  导出文件的基文件名和导入库相同，扩展名是 .exp。  
  
 \/EXPORT:*entryname*\[\=*internalname*\]\[,@`ordinal`\[,**NONAME**\]\]\[,**DATA**\]  
 从程序中导出函数，以允许其他程序调用该函数。  也可导出数据（使用 **DATA** 关键字）。  通常在 DLL 中定义导出。  
  
 *entryname* 是将由调用程序使用的函数名或数据项名。  或者，可将 *internalname* 指定为定义程序中的已知函数；默认情况下，*internalname* 与 *entryname* 相同。  `ordinal` 在 1 到 65,535 的范围内指定导出表中的索引；如果没有指定 `ordinal`，LIB 将分配一个。  **NONAME** 关键字只将函数导出为序号，没有 *entryname*。  **DATA** 关键字用于导出纯数据对象。  
  
 \/INCLUDE:`symbol`  
 将指定符号添加到符号表中。  此选项对强制使用本来不会包括在内的库对象很有用。  
  
 请注意，如果您在预备步骤中创建了导入库，则在创建 .dll 之前，生成 .dll 时必须传递生成导入库时所传递的同一组对象文件。  
  
## 请参阅  
 [使用导入库和导出文件](../../build/reference/working-with-import-libraries-and-export-files.md)