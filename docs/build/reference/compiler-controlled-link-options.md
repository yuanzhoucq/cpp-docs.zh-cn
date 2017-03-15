---
title: "编译器控制的 LINK 选项 | Microsoft Docs"
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
  - "cl.exe 编译器 [C++], 控制链接器"
  - "cl.exe 编译器 [C++], 影响链接的功能"
  - "LINK 工具 [C++], 编译器控制的选项"
  - "链接器 [C++], CL 编译器控件"
  - "链接 [C++], 受 CL 功能的影响"
ms.assetid: e4c03896-c99c-4599-8502-e0f4bebe69d0
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# 编译器控制的 LINK 选项
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

除非指定 \/c 选项，否则 CL 编译器自动调用 LINK。  CL 通过命令行选项和参数实现对链接器的某些控制。  下表总结了 CL 中影响链接的功能。  
  
|CL 规范|影响 LINK 的 CL 操作|  
|-----------|---------------------|  
|除 .c、.cxx、.cpp 或 .def 之外的任何文件扩展名|将文件名作为输入传递给 LINK|  
|*filename*.def|传递 \/DEF:*filename*.def|  
|\/F`number`|传递 \/STACK:`number`|  
|\/Fd*filename*|传递 \/PDB:*filename*|  
|\/Fe*filename*|传递 \/OUT:*filename*|  
|\/Fm*filename*|传递 \/MAP:*filename*|  
|\/Gy|创建封装函数 \(COMDAT\)；启用函数级链接|  
|\/LD|传递 \/DLL|  
|\/LDd|传递 \/DLL|  
|\/link|将命令行的其余部分传递到 LINK|  
|\/MD 或 \/MT|将默认库名放在 .obj 文件中|  
|\/MDd 或 \/MTd|将默认库名放在 .obj 文件中。  定义符号 **\_DEBUG**|  
|\/nologo|传递 \/NOLOGO|  
|\/Zd|传递 \/DEBUG|  
|\/Zi 或 \/Z7|传递 \/DEBUG|  
|\/Zl|忽略 .obj 文件中的默认库名|  
  
 有关更多信息，请参见[编译器选项](../../build/reference/compiler-options.md)。  
  
## 请参阅  
 [设置链接器选项](../../build/reference/setting-linker-options.md)   
 [链接器选项](../../build/reference/linker-options.md)