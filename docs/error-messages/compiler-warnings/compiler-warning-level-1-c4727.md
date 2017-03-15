---
title: "编译器警告（等级 1）C4727 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4727"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4727"
ms.assetid: 991b0087-3a50-40f5-9cdb-cdc367cd472c
caps.latest.revision: 3
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 3
---
# 编译器警告（等级 1）C4727
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

在 obj\_file\_1 和 obj\_file\_2 中找到具有相同时间戳的名为 pch\_file 的 PCH。使用第一个 PCH。  
  
 如果用 **\/Yc** 编译多个 compiland，并且其中的编译器能够用相同的 .pch 时间戳标记所有的 .obj 文件，将发生 C4727。  
  
 要消除此警告，请用 **\/Yc \/c** 编译一个源文件（创建 pch），并用 **\/Yu \/c** 分别编译其他的源文件（使用 pch），然后再将它们链接到一起。  
  
 因此，如果使用了下面的选项就会生成 C4727：  
  
 **cl \/clr \/GL a.cpp b.cpp c.cpp \/Ycstdafx.h**  
  
 您可改用下面的选项：  
  
 **cl \/clr \/GL a.cpp \/Ycstdafx.h \/c**  
  
 **cl \/clr \/GL b.cpp c.cpp \/Yustdafx.h \/link a.obj**  
  
 有关更多信息，请参见  
  
-   [\/Yc（创建预编译的头文件）](../../build/reference/yc-create-precompiled-header-file.md)  
  
-   [\/Yu（使用预编译的头文件）](../../build/reference/yu-use-precompiled-header-file.md)