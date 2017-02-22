---
title: "链接器工具警告 LNK4210 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "LNK4210"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "LNK4210"
ms.assetid: db48cff8-a2be-4a77-8d03-552b42c228fa
caps.latest.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 12
---
# 链接器工具警告 LNK4210
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

存在 section 节；可能有未处理的静态初始值设定项或结束符  
  
 某些代码引入了静态初始值设定项或结束符，但 CRT 或其等效项（需要运行静态初始值设定项或结束符）在应用程序启动时没有运行。  会导致此警告的代码示例：  
  
-   具有构造函数、析构函数或虚函数表的全局类变量。  
  
-   用非编译时常数初始化的全局变量。  
  
 若要修复此问题，请执行以下操作之一：  
  
-   移除所有包含静态初始值设定项的代码。  
  
-   不要使用 [\/NOENTRY](../../build/reference/noentry-no-entry-point.md)。在移除 \/NOENTRY 后，可能还必须将 msvcrt.lib、libcmt.lib 或 libcmtd.lib 添加到链接器命令行中。  
  
-   将 msvcrt.lib、libcmt.lib 或 libcmtd.lib 添加到链接器命令行中。  
  
-   当从 \/clr:pure 编译切换到 \/clr 时，请从链接器行中移除 [\/ENTRY](../../build/reference/entry-entry-point-symbol.md) 选项。  这将启用 CRT 初始化，使静态初始值设定项在应用程序启动时执行。  
  
-   如果项目是使用 [\/ENTRY](../../build/reference/entry-entry-point-symbol.md) 生成的，而且如果将 \/ENTRY 传递给 `_DllMainCRTStartup` 之外的函数，那么该函数必须调用 CRT\_INIT。  参见知识库文章 [运行库行为](../../build/run-time-library-behavior.md) 和 Q94248，[http:\/\/support.microsoft.com\/default.aspx?scid\=kb;en\-us;94248](http://support.microsoft.com/default.aspx?scid=kb;en-us;94248) 需要更多信息。  
  
 [\/GS](../../build/reference/gs-buffer-security-check.md) 编译器选项需要 CRT 启动代码。  
  
## 请参阅  
 [设置链接器选项](../../build/reference/setting-linker-options.md)