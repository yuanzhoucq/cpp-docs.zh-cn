---
title: "Visual C++ 64 位迁移的常见问题 | Microsoft Docs"
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
  - "32 位代码迁移 [C++]"
  - "64 位应用程序 [C++]"
  - "64 位编译器 [C++], 迁移"
  - "64 位编译器 [C++], 迁移 32 位代码"
  - "64 位编程 [C++], 迁移"
  - "迁移 [C++], 64 位代码问题"
  - "将 32 位代码迁移到 64 位代码"
  - "升级 Visual C++ 应用程序, 32 位代码"
  - "Win64 [C++]"
ms.assetid: d17fb838-7513-4e2d-8b27-a1666f17ad76
caps.latest.revision: 19
caps.handback.revision: 17
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Visual C++ 64 位迁移的常见问题
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

用 Visual C\+\+ 创建在 64 位 Windows 操作系统中运行的应用程序时，应注意以下问题：  
  
-   在 64 位 Windows 操作系统中，`int` 和 `long` 是 32 位值。  对于计划为 64 位平台编译的程序，应注意不要将指针赋给 32 位变量。  在 64 位平台上，指针为 64 位，如果将该指针赋给 32 位变量，则将截断该指针值。  
  
-   在 64 位 Windows 操作系统中，`size_t`、`time_t` 和  `ptrdiff_t` 是 64 位值。  
  
-   在 Visual C\+\+ 2005 之前的 Visual C\+\+ 版本中，`time_t` 在 32 位 Windows 操作系统中是 32 位值。  默认情况下，`time_t` 现在为 64 位整数。  有关详细信息，请参阅[时间管理](../c-runtime-library/time-management.md)。  
  
     应注意代码在哪里采用 `int` 值并将其作为 `size_t` 或 `time_t` 值处理。  数字有可能增长得比 32 位数大，并且数据在被传递回 `int` 存储时将被截断。  
  
 在 64 位 Windows 操作系统中，%X（十六进制 `int` 格式）`printf` 修饰符将不会按预期方式工作。  它将只对传递给它的值的前 32 位值执行操作。  
  
-   使用 %I32x，以十六进制格式显示 32 位整数类型。  
  
-   使用 %I64x，以十六进制格式显示 64 位整数类型。  
  
-   在 64 位 Windows 操作系统中，%p（指针的十六进制格式）将按预期方式工作。  
  
 有关详细信息，请参见:  
  
-   [编译器选项](../build/reference/compiler-options.md)  
  
-   [\<caps:sentence id\="tgt18" sentenceid\="8228b16e9fef41dbba1af1d78bf0cc87" class\="tgtSentence"\>迁移提示\<\/caps:sentence\>](http://msdn.microsoft.com/library/windows/desktop/aa384214)  
  
## 请参阅  
 [配置 64 位的程序](../build/configuring-programs-for-64-bit-visual-cpp.md)   
 [移植程序](http://msdn.microsoft.com/zh-cn/c36c44b3-5a9b-4bb4-9b7a-469aa770ed00)