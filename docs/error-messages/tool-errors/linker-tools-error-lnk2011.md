---
title: "链接器工具错误 LNK2011 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "LNK2011"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "LNK2011"
ms.assetid: 04991ef5-49d5-46c7-8eee-a9d1d3fc541e
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# 链接器工具错误 LNK2011
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

未链接预编译对象；映像可能不能运行  
  
 如果使用预编译头，LINK 要求必须链接所有与预编译头一起创建的对象文件。  如果您有用来生成用于其他源文件的预编译头的源文件，现在必须包括与预编译头一起创建的对象文件。  
  
 例如，如果编译一个名为 STUB.cpp 的文件，以创建用于其他源文件的预编译头，则必须与 STUB.obj 链接，否则就会得到此错误。  在下列命令行中，第一行用于创建预编译头 COMMON.pch，它与第二行和第三行中的 PROG1.cpp 和 PROG2.cpp 一起使用。  文件 STUB.cpp 只包含 `#include` 行（与 PROG1.cpp 和 PROG2.cpp 中的 `#include` 行相同），并只用于生成预编译头。  在最后一行中，必须链接 STUB.obj 以避免 LNK2011。  
  
```  
cl /c /Yccommon.h stub.cpp  
cl /c /Yucommon.h prog1.cpp  
cl /c /Yucommon.h prog2.cpp  
link /out:prog.exe stub.obj prog1.obj prog2.obj  
```