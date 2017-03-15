---
title: "命令行错误 D8045 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "D8045"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "D8045"
ms.assetid: 01c8808c-bac1-4b4d-8a90-b595f95e9318
caps.latest.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 9
---
# 命令行错误 D8045
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

无法使用 \/clr 选项编译 C 文件“file”  
  
 只有 C\+\+ 源代码文件可以传递给使用 **\/clr** 的编译。使用 **\/TP** 以将 .c 文件编译为 .cpp 文件，请参见 [\/Tc、\/Tp、\/TC、\/TP（指定源文件类型）](../../build/reference/tc-tp-tc-tp-specify-source-file-type.md) 以获得更多信息。  
  
 有关详细信息，请参阅[\/clr（公共语言运行时编译）](../../build/reference/clr-common-language-runtime-compilation.md)。  
  
 如果您使用 Visual C\+\+ 来编译 ATL 应用程序，也可能会发生 D8045。  有关更多信息，请参见[如何：迁移到 \/clr](../../dotnet/how-to-migrate-to-clr.md)。