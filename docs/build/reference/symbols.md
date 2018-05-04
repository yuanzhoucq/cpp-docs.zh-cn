---
title: -SYMBOLS |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /symbols
dev_langs:
- C++
helpviewer_keywords:
- symbols, dumping
- public symbols
- symbols, displaying COFF symbol table
- symbol tables
- SYMBOLS dumpbin option
- /SYMBOLS dumpbin option
- -SYMBOLS dumpbin option
ms.assetid: 34bcae90-4561-4c77-a80c-065508dec39a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5a0cc59ee730fcfad47d758dec73cb8646210934
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="symbols"></a>/SYMBOLS
```  
/SYMBOLS  
```  
  
 此选项显示 COFF 符号表。 对象的所有文件中存在符号表。 仅当使用 /DEBUG 链接，COFF 符号表将显示在图像文件。  
  
 下面是输出的 /SYMBOLS 的说明。 可以通过查看在 winnt.h （IMAGE_SYMBOL 和 IMAGE_AUX_SYMBOL） 或 COFF 文档中找到含义的 /SYMBOLS 输出的其他信息。  
  
 给定下面的示例转储：  
  
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
  
## <a name="remarks"></a>备注  
 符号数字，开头的行的以下说明，说明了具有与用户相关的信息的列：  
  
-   第一个三位数字是符号编号。  
  
-   如果第三个列包含 SECT*x*，在对象文件的那一节中定义符号。 但如果 UNDEF 出现，它不在该对象中定义，因此必须在其他位置解决。  
  
-   第五列 （静态、 外部） 指示符号是否可见仅在该对象，或者它是否是公共 (可见外部)。 静态符号 _sym 不会链接到公共符号 _sym;这些将是名为 _sym 的函数的两个不同的实例。  
  
 编号行中的最后一列是符号名称，同时修饰和未修饰名。  
  
 仅[/HEADERS](../../build/reference/headers.md) DUMPBIN 选项是可供产生的文件的使用[/GL](../../build/reference/gl-whole-program-optimization.md)编译器选项。  
  
## <a name="see-also"></a>请参阅  
 [DUMPBIN 选项](../../build/reference/dumpbin-options.md)