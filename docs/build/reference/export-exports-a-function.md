---
title: "/EXPORT（导出函数） | Microsoft Docs"
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
  - "VC.Project.VCLinkerTool.ExportFunctions"
  - "/export"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/EXPORT 链接器选项"
  - "EXPORT 链接器选项"
  - "-EXPORT 链接器选项"
ms.assetid: 0920fb44-a472-4091-a8e6-73051f494ca0
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /EXPORT（导出函数）
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

```  
/EXPORT:entryname[,@ordinal[,NONAME]][,DATA]  
```  
  
## 备注  
 使用该选项，可以从程序导出函数，以便其他程序可以调用该函数。  也可以导出数据。  通常在 DLL 中定义导出。  
  
 *entryname* 是将由调用程序使用的函数名或数据项名。  `ordinal` 在 1 到 65,535 的范围内指定导出表中的索引；如果没有指定 `ordinal`，LINK 将分配一个。  **NONAME** 关键字只将函数导出为序号，没有 *entryname*。  
  
 **DATA** 关键字指定导出项为数据项。  客户程序中的数据项必须用 **extern \_\_declspec\(dllimport\)** 来声明。  
  
 有三种导出定义的方法，按照建议的使用顺序依次为：  
  
1.  源代码中的 [\_\_declspec\(dllexport\)](../../cpp/dllexport-dllimport.md)  
  
2.  .def 文件中的 [EXPORTS](../../build/reference/exports.md) 语句  
  
3.  LINK 命令中的 \/EXPORT 规范  
  
 所有这三种方法可以用在同一个程序中。  LINK 在生成包含导出的程序时还创建导入库，除非生成中使用了 .exp 文件。  
  
 LINK 使用标识符的修饰形式。  编译器在创建 .obj 文件时修饰标识符。  如果 *entryname* 以其未修饰的形式指定给链接器（与其在源代码中一样），则 LINK 将尝试匹配该名称。  如果无法找到唯一的匹配名称，则 LINK 发出错误信息。  当需要将标识符指定给链接器时，请使用 [Dumpbin](../../build/reference/dumpbin-reference.md) 工具获取该标识符的[修饰名](../../build/reference/decorated-names.md)形式。  
  
> [!NOTE]
>  不要指定声明为 `__cdecl` 或 `__stdcall` 的 C 标识符的修饰形式。  
  
### 在 Visual Studio 开发环境中设置此链接器选项  
  
1.  打开项目的**“属性页”**对话框。  有关详细信息，请参见[设置 Visual C\+\+ 项目属性](../../ide/working-with-project-properties.md)。  
  
2.  单击“链接器”文件夹。  
  
3.  单击**“命令行”**属性页。  
  
4.  将该选项键入**“附加选项”**框中。  
  
### 以编程方式设置此链接器选项  
  
-   请参见<xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>。  
  
## 请参阅  
 [设置链接器选项](../../build/reference/setting-linker-options.md)   
 [链接器选项](../../build/reference/linker-options.md)