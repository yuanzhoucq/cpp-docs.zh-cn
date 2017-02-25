---
title: "字符集可迁移性的好处 | Microsoft Docs"
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
  - "字符集 [C++], 优点"
  - "可迁移性 [C++], 字符集"
ms.assetid: bd60b925-1498-4e4f-897b-4c8ce66edcf7
caps.latest.revision: 8
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
caps.handback.revision: 8
---
# 字符集可迁移性的好处
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

即使目前不打算国际化应用程序，也可以从使用 MFC 和 C 运行时可移植性功能中获益：  
  
-   编写可移植代码使基本代码更灵活。  以后可以很容易地将代码移动到 Unicode 或 MBCS。  
  
-   使用 Unicode 能提高用于 Windows 2000 的应用程序的效率。  由于 Windows 2000 使用 Unicode，因此与操作系统之间传递的非 Unicode 字符串必须进行转换，这会增加系统开销。  
  
-   使用 MBCS 使您得以在 Windows 2000 以外的 Win32 平台（如 Windows 95 或 Windows 98）上支持国际市场。  
  
## 请参阅  
 [Unicode 和 MBCS](../text/unicode-and-mbcs.md)   
 [支持 Unicode](../text/support-for-unicode.md)