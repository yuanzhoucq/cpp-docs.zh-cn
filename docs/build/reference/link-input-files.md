---
title: "LINK 输入文件 | Microsoft Docs"
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
  - "对链接器文件的命令输入 [C++]"
  - "文件 [C++], LINK"
  - "导入库 [C++], 链接器文件"
  - "输入文件 [C++], LINK"
  - "LINK 工具 [C++], 输入文件"
  - "链接器 [C++], 输入文件"
  - "模块定义文件"
  - "模块定义文件, 链接器文件"
  - "资源 [C++], 链接器文件"
ms.assetid: bb26fcc5-509a-4620-bc3e-b6c6e603a412
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# LINK 输入文件
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

向链接器提供包含对象、导入库和标准库、资源、模块定义和命令输入的文件。  LINK 不使用文件扩展名对文件内容进行假定。  相反，LINK 检查每一个输入文件以确定它是何种类型的文件。  
  
 命令行中的对象文件按照这些文件在命令行中出现的顺序进行处理。  同样按命令行顺序搜索库，但应注意以下事项：将首先在库中搜索从该库中引入对象文件时无法解析的符号，然后是命令行和 [\/DEFAULTLIB（指定默认库）](../../build/reference/defaultlib-specify-default-library.md) 指令中所跟的库，接下来是在命令行开头处的所有库。  
  
> [!NOTE]
>  LINK 不再接受分号（或任何其他字符）作为响应文件和顺序文件中注释的开始。  分号在模块定义文件 \(.def\) 中仅被识别为注释的开始。  
  
 LINK 使用以下类型的输入文件：  
  
-   [.obj 文件](../../build/reference/dot-obj-files-as-linker-input.md)  
  
-   [.netmodule 文件](../../build/reference/netmodule-files-as-linker-input.md)  
  
-   [.lib 文件](../../build/reference/dot-lib-files-as-linker-input.md)  
  
-   [.exp 文件](../../build/reference/dot-exp-files-as-linker-input.md)  
  
-   [.def 文件](../../build/reference/dot-def-files-as-linker-input.md)  
  
-   [.pdb 文件](../../build/reference/dot-pdb-files-as-linker-input.md)  
  
-   [.res 文件](../../build/reference/dot-res-files-as-linker-input.md)  
  
-   [.exe 文件](../../build/reference/dot-exe-files-as-linker-input.md)  
  
-   [.txt 文件](../../build/reference/dot-txt-files-as-linker-input.md)  
  
-   [.ilk 文件](../../build/reference/dot-ilk-files-as-linker-input.md)  
  
## 请参阅  
 [设置链接器选项](../../build/reference/setting-linker-options.md)   
 [链接器选项](../../build/reference/linker-options.md)