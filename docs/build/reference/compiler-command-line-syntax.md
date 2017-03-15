---
title: "编译器命令行语法 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "cl.exe 编译器, 命令行语法"
  - "语法, CL 编译器命令行"
ms.assetid: acba2c1c-0803-4a3a-af25-63e849b930a2
caps.latest.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 10
---
# 编译器命令行语法
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

CL 命令行使用下列语法：  
  
```  
CL [option...] file... [option | file]... [lib...] [@command-file] [/link link-opt...]  
```  
  
 下表说明对 CL 命令的输入。  
  
|Entry|含义|  
|-----------|--------|  
|*选项*|一个或多个 [CL 选项](../../build/reference/compiler-options.md)。  请注意，所有选项都应用于所有指定的源文件。  选项是由一个正斜杠 \(\/\) 或一个短划线 \(–\) 指定的。  如果某个选项带有参数，则该选项的说明指定在选项和参数之间是否允许有空格。  选项名（\/HELP 选项除外）区分大小写。  有关更多信息，请参见 [CL 选项的顺序](../../build/reference/order-of-cl-options.md)。|  
|`file`|一个或多个源文件、.obj 文件或库的名称。  CL 编译源文件并将 .obj 文件和库的名称传递给链接器。  有关更多信息，请参见 [CL 文件名语法](../../build/reference/cl-filename-syntax.md)。|  
|*lib*|一个或多个库名。  CL 将这些名称传递给链接器。|  
|*command\-file*|包含多个选项和文件名的文件。  有关更多信息，请参见 [CL 命令文件](../../build/reference/cl-command-files.md)。|  
|*link\-opt*|一个或多个[链接器选项](../../build/reference/linker-options.md)。  CL 将这些选项传递给链接器。|  
  
 您可以指定任意数目的选项、文件名和库名，条件是命令行上的字符数不超过 1024，该限制是操作系统指定的。  
  
 有关 cl.exe 的返回值的信息，请参见 [cl.exe 的返回值](../../build/reference/return-value-of-cl-exe.md)。  
  
> [!NOTE]
>  不保证 1024 个字符的命令行输入限制在 Windows 的未来版本中保持不变。  
  
## 请参阅  
 [设置编译器选项](../../build/reference/setting-compiler-options.md)   
 [编译器选项](../../build/reference/compiler-options.md)