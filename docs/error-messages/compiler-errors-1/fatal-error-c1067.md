---
title: "错误 C1067 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C1067"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C1067"
ms.assetid: e2c94be6-4573-4571-aac9-73d657fe9f96
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# 错误 C1067
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

编译器限制: 已超出类型记录的 64K 大小限制  
  
 如果符号的修饰名超过 247 个字符，则可能发生该错误。若要解决此问题，请缩短符号名。  
  
 在编译器生成调试信息时，它会发出类型记录以定义在源代码中遇到的类型。例如，类型记录包括函数的简单结构和参数列表。这些类型记录中有的记录可能是大型列表。  
  
 任何类型记录都存在一个 64K 的大小限制。如果超出了 64K 限制，就会发生此错误。  
  
 如果有许多长名称的符号，或是某个类、结构或联合具有过多成员，也可能发生 C1067 错误。