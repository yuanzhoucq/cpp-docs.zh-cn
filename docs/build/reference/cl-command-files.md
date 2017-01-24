---
title: "CL 命令文件 | Microsoft Docs"
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
  - "cl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "cl.exe 编译器, 命令文件"
  - "命令文件"
  - "命令文件, CL 编译器"
ms.assetid: ec3cea06-2af0-4fe9-a94c-119c9d31b3a9
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# CL 命令文件
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

命令文件是一个文本文件，它包含您另外在[命令行](../../build/reference/compiler-command-line-syntax.md)上键入或使用 [CL 环境变量](../../build/reference/cl-environment-variables.md)指定的选项和文件名。  CL 接受在 CL 环境变量中或命令行上用作参数的编译器命令文件。  与命令行或 CL 环境变量不同，命令文件允许使用多行选项和文件名。  
  
 命令文件中的选项和文件名将根据 CL 环境变量中或命令行上的命令文件名的位置被进行处理。  但是，如果 \/link 选项出现在命令文件中，则该行其余部分的所有选项将被传递给链接器。  命令文件的后面几行中的选项和命令行上命令文件调用之后的选项仍被作为编译器选项接受。  有关选项的顺序如何影响其解释的更多信息，请参见 [CL 选项的顺序](../../build/reference/order-of-cl-options.md)。  
  
 命令文件一定不能包含 CL 命令。  每个选项必须在同一行上开始和结束；不能使用反斜杠 \(\\\) 跨行组合一个选项。  
  
 命令文件用一个“at”符 \(@\) 后接一个文件名指定；该文件名可指定绝对路径或相对路径。  
  
 例如，如果下面的命令位于名为 RESP 的文件中：  
  
```  
/Og /link LIBC.LIB  
```  
  
 并且指定下列 CL 命令：  
  
```  
CL /Ob2 @RESP MYAPP.C  
```  
  
 则到 CL 的命令如下：  
  
```  
CL /Ob2 /Og MYAPP.C /link LIBC.LIB  
```  
  
 请注意，命令行和命令文件命令被有效地结合在一起。  
  
## 请参阅  
 [设置编译器选项](../../build/reference/setting-compiler-options.md)   
 [编译器选项](../../build/reference/compiler-options.md)