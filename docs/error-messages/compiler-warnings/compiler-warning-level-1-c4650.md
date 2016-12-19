---
title: "编译器警告（等级 1）C4650 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4650"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4650"
ms.assetid: 3190b3e3-dcd6-4846-939b-f900ab652b2a
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器警告（等级 1）C4650
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

调试信息不在预编译头中；只有头中的全局符号可用  
  
 预编译头文件不是用 Microsoft 符号调试信息编译的。  
  
 链接后，所得到的可执行文件或动态链接库文件将不包括包含在预编译头中的本地符号的调试信息。  
  
 用 [\/Zi](../../build/reference/z7-zi-zi-debug-information-format.md) 命令行选项重新编译预编译头文件可以避免此警告。