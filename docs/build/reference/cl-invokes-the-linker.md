---
title: "CL 调用链接器 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "cl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "cl.exe 编译器 [C++], 编译而不链接"
  - "cl.exe 编译器 [C++], 控制链接器"
  - "编译源代码 [C++], 不链接"
  - "从编译器调用链接器"
  - "LINK 工具 [C++], 从 CL 编译器调用"
ms.assetid: eae47ef7-09eb-40c9-b318-7c714cd452fc
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# CL 调用链接器
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

除非使用 \/c 选项，否则 CL 在编译之后将自动调用链接器。  CL 向链接器传递在编译期间创建的 .obj 文件的名称，以及在命令行上指定的任何其他文件的名称。  链接器使用在 LINK 环境变量中列出的选项。  可以使用 \/link 选项在 CL 命令行上指定链接器选项。  \/link 选项后面的选项重写 LINK 环境变量中的选项。  下表中的选项取消链接。  
  
|选项|说明|  
|--------|--------|  
|\/c|编译但不链接|  
|\/E、\/EP、\/P|预处理但不编译或链接|  
|\/Zg|生成函数原型|  
|\/Zs|检查语法|  
  
 有关链接的更详细的信息，请参见[链接器选项](../../build/reference/linker-options.md)。  
  
## 示例  
 假设您正在编译三个 C 源文件：MAIN.c、MOD1.c 和 MOD2.c。  每个文件包括对在不同文件中定义的函数的调用：  
  
-   MAIN.c 调用 MOD1.c 中的函数 `func1` 和 MOD2.c 中的函数 `func2`。  
  
-   MOD1.c 调用标准库函数 `printf_s` 和 `scanf_s`。  
  
-   MOD2.c 调用名为 `myline` 和 `mycircle` 的图形函数，这些函数是在名为 MYGRAPH.lib 的库中定义的。  
  
 要生成此程序，使用下列命令行进行编译：  
  
```  
CL MAIN.c MOD1.C MOD2.C MYGRAPH.lib  
```  
  
 CL 先编译 C 源文件，然后创建对象文件 MAIN.obj、MOD1.obj 和 MOD2.obj。  编译器将标准库的名称放在每个 .obj 文件中。  有关更详细的信息，请参见[使用运行库](../../build/reference/md-mt-ld-use-run-time-library.md)。  
  
 CL 将 .obj 文件的名称和名称 MYGRAPH.lib 一起传递给链接器。  链接器解析外部引用，如下所示：  
  
1.  在 MAIN.obj 中，使用 MOD1.obj 中的定义解析对 `func1` 的引用；使用 MOD2.obj 中的定义解析对 `func2` 的引用。  
  
2.  在 MOD1.obj 中，使用链接器找到的、在 MOD1.obj 内命名的库中的定义解析对 `printf_s` 和 `scanf_s` 的引用。  
  
3.  在 MOD2.obj 中，使用 MYGRAPH.lib 中的定义解析对 `myline` 和 `mycircle` 的引用。  
  
## 请参阅  
 [编译器选项](../../build/reference/compiler-options.md)   
 [设置编译器选项](../../build/reference/setting-compiler-options.md)