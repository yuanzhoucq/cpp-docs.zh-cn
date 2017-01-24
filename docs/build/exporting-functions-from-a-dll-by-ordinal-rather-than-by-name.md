---
title: "按序号而不是按名称从 DLL 导出函数 | Microsoft Docs"
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
  - "NONAME"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "导出 DLL [C++], 序号值"
  - "导出函数 [C++], 序号值"
  - "NONAME 特性"
  - "序号导出 [C++]"
ms.assetid: 679719fd-d965-4df3-9f7a-7d86ad831702
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 按序号而不是按名称从 DLL 导出函数
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

从 DLL 导出函数的最简单方法是按名称导出它们。  例如，使用 **\_\_declspec\(dllexport\)** 时所采用的就是这种方法。  但也可以按序号导出函数。  使用此技术时，必须使用 .def 文件而不是 **\_\_declspec\(dllexport\)**。  若要指定函数的序号值，请将其序号追加到 .def 文件中的函数名。  有关指定序号的信息，请参见[使用 .def 文件从 DLL 导出](../build/exporting-from-a-dll-using-def-files.md)。  
  
> [!TIP]
>  如果希望优化 DLL 文件的大小，请对每个导出函数使用 **NONAME** 特性。  使用 **NONAME** 特性时，序号存储在 DLL 的导出表中而非函数名中。  如果导出许多函数，这样做可以节省相当多的空间。  
  
## 你希望做什么？  
  
-   [使用 .def 文件以便按序号导出](../build/exporting-from-a-dll-using-def-files.md)  
  
-   [使用 \_\_declspec\(dllexport\)](../build/exporting-from-a-dll-using-declspec-dllexport.md)  
  
## 请参阅  
 [从 DLL 导出](../build/exporting-from-a-dll.md)