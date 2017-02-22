---
title: "Windows 运行时不支持的 CRT 函数 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "不支持的 CRT 函数, Windows 运行时"
  - "Windows 运行时, 不支持的 CRT 函数"
ms.assetid: bb8386d6-0ef8-460c-88d8-addff009b6f1
caps.latest.revision: 14
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 14
---
# Windows 运行时不支持的 CRT 函数
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

许多 C 运行时 \(CRT\) API 都不能用于在 [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)] 中执行的 [!INCLUDE[win8_appname_long](../build/includes/win8_appname_long_md.md)] 的应用。  这些应用是使用 \/ZW 编译器标志生成的。  有关不受支持的 CRT 函数的列表，请参阅 [不受 \/ZW 支持的 CRT 函数](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx)。  
  
 文档的[按字母顺序的函数参考](../c-runtime-library/reference/crt-alphabetical-function-reference.md)部分介绍了所有 CRT API。  
  
## 请参阅  
 [按类别分的运行时例程](../c-runtime-library/run-time-routines-by-category.md)   
 [按字母顺序的函数参考](../c-runtime-library/reference/crt-alphabetical-function-reference.md)