---
title: "1. Introduction | Microsoft Docs"
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
ms.assetid: c42e72bc-0e31-4b1c-b670-cd82673c0c5a
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 1. Introduction
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

文档指定编译器指令、库函数和在 C 和 C\+\+ 程序可用于指定共享内存并行的环境变量的集合。  中描述的功能文档统称为 *OpenMP C\/C\+\+ 应用程序结口 \(API\)*。  这允许程序移植到不同供应商的共享内存体系结构之间此规范的目标是并行编程提供设计。  OpenMP C\/C\+\+ API 将由许多供应商的编译器支持。  有关 OpenMP 的更多信息，包括 *OpenMP FORTRAN 应用程序结口*，可在以下网站中找到:  
  
 [http:\/\/www.openmp.org](http://www.openmp.org)  
  
 中定义的指令、库函数和环境变量文档将允许用户创建和管理并行程序，同时允许可移植性时。  指令扩展了唯一程序的多个数据 \(SPMD\)结构的工作划分、构造和同步构造的 C 和 C\+\+ 顺序编程模型，并且，它们提供数据的共享和私有化支持。  支持 OpenMP C 和 C\+\+ API 的编译器会包括命令行选项为 " 活动 " 并允许所有 OpenMP 编译器指令的解释的编译器。