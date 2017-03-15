---
title: "错误 C1854 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C1854"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C1854"
ms.assetid: 8c21a9cc-1737-475c-9e57-8725cd8937c1
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# 错误 C1854
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

无法覆盖在创建对象文件“filename”的预编译头过程中形成的信息  
  
 您对同一文件指定 **\/Yc**（创建预编译头文件）选项后指定了 **\/Yu**（使用预编译头文件）选项。  某些声明（如包括 `__declspec` `dllexport` 的声明）使此操作无效。