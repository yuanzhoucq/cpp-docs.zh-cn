---
title: "LINK 命令文件 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "link"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "命令文件 [C++]"
  - "命令文件 [C++], LINK"
  - "LINK 工具 [C++]"
  - "LINK 工具 [C++], 命令行语法"
  - "语法, LINK 命令文件"
  - "文本文件, 将参数传递到 LINK"
ms.assetid: 7154511c-32b9-4e5b-a515-3922fa9de48e
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# LINK 命令文件
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

可以用命令文件的形式将命令行参数传递给 LINK。  要将命令文件指定到链接器，可使用下列语法：  
  
```  
LINK @commandfile  
```  
  
 `commandfile` 是文本文件的名称。  在 @ 符和文件名之间不允许有空格或制表符。  不存在默认扩展名；必须指定完整的文件名，包括任何扩展名。  不能使用通配符。  可使用文件名指定绝对路径或相对路径。  LINK 不使用环境变量搜索文件。  
  
 在命令文件中，可用空格或制表符（像在命令行上一样）和换行符分隔参数。  
  
 可在命令文件中指定所有或部分命令行。  可在 LINK 命令中使用多个命令文件。  LINK 接受命令文件输入，如同它是在命令行中的那个位置指定的一样。  命令文件不能嵌套。  LINK 回显命令文件的内容，除非指定了 [\/NOLOGO](../../build/reference/nologo-suppress-startup-banner-linker.md) 选项。  
  
## 示例  
 下列生成 DLL 的命令传递不同命令文件中的对象文件和库的名称，并将第三个命令文件用于 \/EXPORTS 选项的指定：  
  
```  
link /dll @objlist.txt @liblist.txt @exports.txt  
```  
  
## 请参阅  
 [设置链接器选项](../../build/reference/setting-linker-options.md)   
 [链接器选项](../../build/reference/linker-options.md)