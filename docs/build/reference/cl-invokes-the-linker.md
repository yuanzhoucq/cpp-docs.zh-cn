---
title: CL 调用链接器 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- cl
dev_langs:
- C++
helpviewer_keywords:
- compiling source code [C++], without linking
- invoking linker from the compiler
- LINK tool [C++], invoking from CL compiler
- cl.exe compiler [C++], compiling without linking
- cl.exe compiler [C++], controlling linker
ms.assetid: eae47ef7-09eb-40c9-b318-7c714cd452fc
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: bc9c5c4815dc83b37d0b7971d5fd0f31db51e39e
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="cl-invokes-the-linker"></a>CL 调用链接器
CL 编译除非使用 /c 选项后会自动调用链接器。 CL 将在编译期间创建的.obj 文件的名称和命令行上指定的任何其他文件的名称传递到链接器。 链接器使用 LINK 环境变量中列出的选项。 /Link 选项可用于指定 CL 命令行上的链接器选项。 /Link 选项后跟的选项将替代 LINK 环境变量中。 下表中的选项禁止显示链接。  
  
|选项|描述|  
|------------|-----------------|  
|/c|编译但不链接|  
|/ / E、 /EP，P|预处理而无需编译或链接|  
|/Zg|生成函数原型|  
|/Zs|请检查语法|  
  
 有关链接的更多详细信息，请参阅[链接器选项](../../build/reference/linker-options.md)。  
  
## <a name="example"></a>示例  
 假定您正在编译三个 C 源文件： MAIN.c、 MOD1.c 和 MOD2.c。 每个文件包括对在不同文件中定义的函数的调用：  
  
-   MAIN.c 调用函数`func1`MOD1.c 和函数中`func2`MOD2.c 中。  
  
-   MOD1.c 调用标准库函数`printf_s`和`scanf_s`。  
  
-   MOD2.c 调用名为的图形函数`myline`和`mycircle`，这在一个名为 MYGRAPH.lib 库中定义。  
  
 若要生成此程序，请使用下面的命令行编译：  
  
```  
CL MAIN.c MOD1.C MOD2.C MYGRAPH.lib  
```  
  
 CL 首先编译 C 源代码文件，并创建对象文件 MAIN.obj、 MOD1.obj 和 MOD2.obj。在每个.obj 文件，编译器将标准库的名称。 有关更多详细信息，请参阅[使用运行时库](../../build/reference/md-mt-ld-use-run-time-library.md)。  
  
 CL 将的.obj 文件，以及 MYGRAPH.lib 的名称的名称传递给链接器。 链接器解析外部引用，如下所示：  
  
1.  在 MAIN.obj，对引用`func1`MOD1.obj; 在使用定义程序解析对引用`func2`得到解决在 MOD2.obj 中使用的定义。  
  
2.  在 MOD1.obj，对引用`printf_s`和`scanf_s`MOD1.obj 中名为链接器查找库中使用定义解析。  
  
3.  在 MOD2.obj，对引用`myline`和`mycircle`MYGRAPH.lib 在使用定义解析。  
  
## <a name="see-also"></a>请参阅  
 [编译器选项](../../build/reference/compiler-options.md)   
 [设置编译器选项](../../build/reference/setting-compiler-options.md)