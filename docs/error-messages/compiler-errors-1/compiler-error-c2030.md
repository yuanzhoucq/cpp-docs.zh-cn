---
title: "编译器错误 C2030 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2030"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2030"
ms.assetid: 5806cead-64df-4eff-92de-52c9a3f5ee62
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# 编译器错误 C2030
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

具有“protected private”可访问性的析构函数不能是声明为“sealed”的类的成员  
  
 声明为 `sealed` 的 Windows 运行时类不能具有受保护的私有析构函数。  已密封的类型上只允许使用公共虚拟和私有非虚拟析构函数。  有关详细信息，请参阅 [Ref 类和结构](../Topic/Ref%20classes%20and%20structs%20\(C++-CX\).md)。  
  
 若要修复此错误，请更改析构函数的可访问性。