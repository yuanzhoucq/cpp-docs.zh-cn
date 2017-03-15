---
title: "1.1 Scope | Microsoft Docs"
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
ms.assetid: a8570a3c-1dd6-4c3d-b368-a10fcb3534a6
caps.latest.revision: 4
caps.handback.revision: 4
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 1.1 Scope
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

此规范只包括用户操作进行并行化，，用户显式指定编译器和运行时系统将采用的事件以并行执行程序。  不需要 OpenMP C 和 C\+\+ 实现检查依赖项、冲突、死锁、争用条件，或者导致错误程序执行的其他问题。  用户负责确保使用 OpenMP C 和 C\+\+ API 的应用程序构造正确执行。  编译器生成的自动并行化和指令为帮助这样并行化的编译器中未复盖的文档。