---
title: "国际化策略 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "字符集 [C++], 国际编程策略"
  - "全球化 [C++], 字符集"
  - "语言可迁移代码 [C++]"
  - "本地化 [C++], 字符集"
  - "MBCS [C++], 国际化策略"
  - "Unicode [C++], 全球化应用程序"
  - "Win32 [C++], 国际编程策略"
  - "Windows API [C++], 国际编程策略"
ms.assetid: b09d9854-0709-4b9a-a00c-b0b8bc4199b1
caps.latest.revision: 8
caps.handback.revision: 8
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# 国际化策略
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

根据您的目标操作系统和市场，有几个国际化策略：  
  
-   应用程序使用 Unicode，因此在 Windows 2000 和 Windows NT（但不能在 Windows 95 或 Windows 98）上运行。  
  
     使用 Unicode 特定的功能并且所有字符都为 16 位宽（尽管可以出于特殊目的在程序的某些部分使用 ANSI 字符）。  C 运行库提供仅使用 Unicode 编程的函数、宏和数据类型。  MFC 则完全支持 Unicode。  
  
-   如果应用程序使用 MBCS 则可以在任何 Win32 平台上运行。  
  
     使用特定于 MBCS 的功能。  字符串可以包含单字节字符、双字节字符或同时包含这两种字符。  C 运行库提供仅使用 MBCS 编程的函数、宏和数据类型。  MFC 则完全支持 MBCS。  
  
-   编写的应用程序的源代码具有完全可移植性。通过定义 **\_UNICODE** 符号或 **\_MBCS** 符号来重新编译应用程序，可以生成使用其中任何一种字符的版本。  有关更多信息，请参见 [Tchar.h 中的一般文本映射](../text/generic-text-mappings-in-tchar-h.md)。  
  
-   应用程序对 Windows 95、Windows 98 和 Windows ME 上缺少的 Unicode 函数使用包装库，类似 [设计一个在 Windows 98 和 Windows 2000](http://go.microsoft.com/fwlink/p/?LinkId=250770)上都运行的 Unicode 应用程序 中所描述的包装库。  包装库还可通过商业手段获得。  
  
     使用完全可移植的 C 运行时函数、宏和数据类型。  MFC 的灵活性支持所有这些策略。  
  
 这些主题的其余部分着重说明如何编写可生成为 Unicode 应用程序或 MBCS 应用程序的完全可移植代码。  
  
## 请参阅  
 [Unicode 和 MBCS](../text/unicode-and-mbcs.md)   
 [区域设置和代码页](../text/locales-and-code-pages.md)