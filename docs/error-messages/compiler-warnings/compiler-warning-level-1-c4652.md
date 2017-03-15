---
title: "编译器警告（等级 1）C4652 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4652"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4652"
ms.assetid: 2cf2c666-8cdd-4dd9-bda0-662921498b03
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# 编译器警告（等级 1）C4652
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

编译器选项“option”与预编译头不一致；当前命令行选项将重写预编译头中定义的选项  
  
 给定命令行选项与创建预编译头 \(.pch\) 时的给定命令行选项不同。  使用的是当前命令行中指定的选项。  
  
 用给定命令行选项重新生成预编译头可以避免此警告。