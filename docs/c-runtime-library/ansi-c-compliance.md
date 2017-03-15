---
title: "ANSI C 遵从性 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "Ansi"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ANSI [C++], C 标准"
  - "兼容性 [C++], ANSI C"
  - "符合 ANSI C"
  - "约定 [C++], Microsoft 扩展"
  - "Microsoft 扩展命名约定"
  - "命名规则 [C++], Microsoft 库"
  - "下划线"
  - "下划线, 前导"
ms.assetid: 6be271bf-eecf-491a-a928-0ee2dd60e3b9
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# ANSI C 遵从性
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

在运行时系统中，所有特定的 Microsoft 标识符的命名规则 \(如函数、宏、常数、变量和类型定义\) 是符合 ANSI 标准的。  在本文档中，任何运行时函数遵循 ANSI\/ISO C 标准被标记是兼容的 ANSI。  符合 ANSI 标准的应用程序应仅使用 ANSI 兼容性函数。  
  
 特定于 Microsoft 的函数和全局变量名称是以一个下划线开头。  在代码的范围中，这些名称只能在本地被重写。  例如，当包括 Microsoft 运行时头文件时，则通过声明同名的局部变量重写特定于 Microsoft 的函数命名为   `_open`。  但是，不能为全局函数或全局变量设置该命名。  
  
 特定于 Microsoft 的宏以及清单常数名称以两个下划线开头，或以一个前导下划线紧跟大写字母。  这些标识符的范围是绝对的。  例如，不能为此使用特定于 Microsoft 的标识符 **\_UPPER** 。  
  
## 请参阅  
 [兼容性](../c-runtime-library/compatibility.md)