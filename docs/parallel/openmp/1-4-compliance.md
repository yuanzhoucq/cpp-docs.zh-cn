---
title: "1.4 遵从性 | Microsoft Docs"
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
ms.assetid: 662ad260-b9a1-43b7-b269-ef6ff0714e05
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 1.4 遵从性
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

OpenMP C/c + + API 实现 *OpenMP 符合* 如果它识别为分布在各章 1、 2、 3、 4、 保留的本规范中，所有元素的语义和附录 C.附录 A、 B、 D、 E 和 F 适用于信息为目的并不是该规范的一部分。 仅包含一个子集的 api 的实现都不是符合 OpenMP。  
  
 OpenMP C 和 c + + API 是对支持的实现的基本语言的扩展。 如果基本语言不在本文档中支持的语言构造或扩展，将出现，OpenMP 实现不需要支持它。  
  
 所有标准的 C 和 c + + 库函数和内置函数 （即，编译器具有特定的知识的函数） 必须是线程安全的。 未同步的使用的是不同的线程并行区域内线程 – 安全函数不生成未定义的行为。 但是，该行为可能不是与串行区域中的相同。 （随机数生成函数是一个示例。）  
  
 OpenMP C/c + + API 指定特定的行为是 *实现定义。* 符合标准的 OpenMP 实现时需要定义并记录其在这些情况下的行为。 请参阅 [附录 E](../../parallel/openmp/e-implementation-defined-behaviors-in-openmp-c-cpp.md), ，页上 97 中，为实现定义的行为的列表。