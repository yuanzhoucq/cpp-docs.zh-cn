---
title: "编译器警告（等级 1）C4799 | Microsoft Docs"
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
  - "C4799"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4799"
ms.assetid: 8ecbd06f-c778-4371-a2fb-c690b6743ec8
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器警告（等级 1）C4799
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

函数“function”的末尾处没有 EMMS  
  
 函数至少有一个 MMX 指令，但没有 EMMS 指令。  在使用多媒体指令时，还应使用 EMMS 指令来清除 MMX 代码结尾处的多媒体标记字。  有关 EMMS 指令的更多信息，请参见[关于何时使用 EMMS 的指南](http://msdn.microsoft.com/zh-cn/a0c3b1e4-01a4-419c-a58f-ff1e97dea7d3)。  
  
 使用 ivec.h 时可能收到 C4799，指示未正确使用代码，应在返回前执行 EMMS 指令。  这是对这些标题的假警告。  在 ivec.h 中定义 \_SILENCE\_IVEC\_C4799 可以关闭这些警告。  但要知道，这也会使编译器不能对此类型给出正确警告。  
  
 有关相关信息，请参见 [Intel 的 MMX 指令集](../../assembler/inline/intel-s-mmx-instruction-set.md)。