---
title: "2.8 Directive Binding | Microsoft Docs"
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
ms.assetid: 7bdac45e-ab55-42f0-bd47-a2e3d5bbab3e
caps.latest.revision: 4
caps.handback.revision: 4
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 2.8 Directive Binding
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

指令动态绑定必须遵循下列规则:  
  
-   **为**、 **部分**、 **单个**、 **母版**和 **障碍** 指令绑定到动态封闭 **并行**，，如果存在，无论可能存在指令中的任何 **如果** 子句中的值。  如果并行区域当前未执行，指令由团队执行组成只能由主线程。  
  
-   **排序** 指令绑定到动态封闭 **为**。  
  
-   **基本** 指令强制独占访问有关所有线程的 **基本** 指令，而不仅仅是当前团队。  
  
-   **重要** 指令强制独占访问有关所有线程的 **重要** 指令，而不仅仅是当前团队。  
  
-   指令不能绑定到任何指令在最接近的动态封闭 **并行**之外。