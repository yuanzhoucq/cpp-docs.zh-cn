---
title: "何时预编译源代码 | Microsoft Docs"
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
  - "pch"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "预编译的头文件, 何时预编译"
  - "源代码, 预编译"
ms.assetid: eb8ba193-fd87-40d3-9545-c75deabe37cb
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 何时预编译源代码
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

预编译代码有助于在开发周期中缩短编译时间，特别是在以下情况中：  
  
-   总是使用不经常改动的大型代码体。  
  
-   程序由多个模块组成，所有模块都使用一组标准的包含文件和相同的编译选项。  在这种情况下，可以将所有包含文件预编译为一个预编译头。  
  
 用于创建预编译头文件的第一次编译所花费的时间比后面的编译稍长一些。  通过包含预编译代码可以加快后面的编译速度。  
  
 C 和 C\+\+ 程序都可以预编译。  在 C\+\+ 编程中，常见的做法是将类接口信息分别放到不同的头文件中。  此后就可以将这些头文件包含在使用该类的程序中。  通过预编译这些头文件，可以缩短程序的编译时间。  
  
> [!NOTE]
>  尽管每个源文件只能使用一个预编译头 \(.pch\) 文件，但在一个项目中可以使用多个 .pch 文件。  
  
## 请参阅  
 [创建预编译的头文件](../../build/reference/creating-precompiled-header-files.md)