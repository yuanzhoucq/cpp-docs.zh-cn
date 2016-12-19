---
title: "编译器错误 C3859 | Microsoft Docs"
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
  - "C3859"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3859"
ms.assetid: 40e93b25-4393-4467-90de-035434a665c7
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器错误 C3859
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

超过了 PCH 的虚拟内存范围；请使用“\-Zmvalue”或更大的命令行选项重新编译  
  
 预编译头对于编译器尝试放入其中的数据量太小。  使用 **\/Zm** 编译器标志可为预编译头文件指定更大值。  有关详细信息，请参阅 [\/Zm（指定预编译头的内存分配限额）](../../build/reference/zm-specify-precompiled-header-memory-allocation-limit.md)。