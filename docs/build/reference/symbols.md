---
title: "/SYMBOLS | Microsoft Docs"
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
  - "/symbols"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/SYMBOLS dumpbin 选项"
  - "公共符号"
  - "符号表"
  - "SYMBOLS dumpbin 选项"
  - "-SYMBOLS dumpbin 选项"
  - "symbols, 显示 COFF 符号表"
  - "symbols, 转储"
ms.assetid: 34bcae90-4561-4c77-a80c-065508dec39a
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /SYMBOLS
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

```  
/SYMBOLS  
```  
  
 此选项显示 COFF 符号表。  符号表存在于所有对象文件中。  而对于图像文件，只有当它是与 \/DEBUG 链接的时，它才包含 COFF 符号表。  
  
 下面是关于 \/SYMBOLS 输出的说明。  通过查阅 winnt.h（IMAGE\_SYMBOL 和 IMAGE\_AUX\_SYMBOL）或 COFF 文档，可找到有关 \/SYMBOLS 输出含义的附加信息。  
  
 假设有下列示例转储：  
  
```  
Dump of file main.obj  
File Type: COFF OBJECT  
  
COFF    SYMBOL    TABLE  
000    00000000   DEBUG      notype      Filename      | .file  
      main.cpp  
002   000B1FDB   ABS      notype      Static      | @comp.id  
003   00000000   SECT1      notype      Static      | .drectve  
      Section length       26, #relocs   0, #linenums    0, checksum 722C964F  
005   00000000   SECT2      notype      Static      | .text  
      Section length      23, #relocs      1, #linenums    0, checksum 459FF65F, selection    1 (pick no duplicates)  
007   00000000   SECT2      notype ()   External      | _main  
008   00000000   UNDEF      notype ()   External      | ?MyDump@@YAXXZ (void __cdecl MyDump(void))  
  
String Table Size = 0x10 bytes  
  
Summary  
  
      26 .drectve  
      23 .text  
```  
  
## 备注  
 对于以符号号码开头的行，下列说明描述了含有与用户相关的信息的列：  
  
-   开头的 3 位数字是符号索引\/号码。  
  
-   如果第三列包含 SECT*x*，则符号在对象文件的那一节中定义。  但如果出现 UNDEF，则它不在那个对象中定义并且必须在其他地方被解析。  
  
-   第五列 \(Static, External\) 说明符号是否只在那个对象的内部可见，或者是否是公共的（外部可见）。  静态符号 \_sym 不会链接到公共符号 \_sym；这些符号是名为 \_sym 的函数的两种不同实例。  
  
 编号行中的最后一列是符号名（修饰名和未修饰名）。  
  
 只有 [\/HEADERS](../../build/reference/headers.md) DUMPBIN 选项可用于由 [\/GL](../../build/reference/gl-whole-program-optimization.md) 编译器选项产生的文件。  
  
## 请参阅  
 [DUMPBIN 选项](../../build/reference/dumpbin-options.md)