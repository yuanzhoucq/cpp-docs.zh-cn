---
title: "2.7.2.3 lastprivate | Microsoft Docs"
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
ms.assetid: 77f6a5c9-704f-4a88-8476-29db852ed800
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 2.7.2.3 lastprivate
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

`lastprivate` 子句提供 `private` 子句提供的功能的扩展。  `lastprivate` 子句的语法如下所示:  
  
```  
lastprivate(variable-list)  
```  
  
 在 *变量中* 指定的变量具有 `private` 子句语义。  当 `lastprivate` 子句出现在标识的工作划分构造、每个 `lastprivate` 变量的值以关联的循环顺序次迭代的或词法上一节指令的指令时，分配给变量的原始对象。  未赋值。 **为** 或 **并行。**最后一个迭代，或被 **部分** 或 **并行部分** 指令的词法上一节的变量，具有不确定的值在构造之后。  未指定的子对象还有一个不确定的值在构造之后。  
  
 为 `lastprivate` 子句的限制如下所示:  
  
-   `private` 的所有限制。  
  
-   使用指定的类类型的变量，当 `lastprivate` 必须具有访问，明确的复制赋值运算符。  
  
-   在并行区域内是专用或显示 **并行** 指令的 `reduction` 子句的变量。 `lastprivate` 子句不能指定在绑定到并行构造的工作划分指令。