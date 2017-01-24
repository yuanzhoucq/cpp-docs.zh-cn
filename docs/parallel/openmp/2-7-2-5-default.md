---
title: "2.7.2.5 default | Microsoft Docs"
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
ms.assetid: c856df07-705c-4ad3-9105-a268dd33e939
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 2.7.2.5 default
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

**默认** 子句允许用户影响变量数据共享属性。  **默认** 子句的语法如下所示:  
  
```  
default(shared | none)  
```  
  
 ，除非它是 **threadprivate** 或 **cons**\- 限定，的`t`指定 **默认 \(共享\)** 用方括号括在 **共享** 子句中的每个当前可见的变量是等效的。  在没有显式 **默认** 子句时，默认行为是相同的，就象 **默认 \(共享\)** 指定了。  
  
 指定 **默认 \(无\)** 需要至少一列绑定适用于每对并行构造的词法区域的变量:  
  
-   该变量位于包含引用结构化数据共享属性子句显式列表。  
  
-   变量在并行构造中声明。  
  
-   该变量是 **threadprivate**。  
  
-   该变量具有 **const**\- 限定类型。  
  
-   该变量是紧跟在 **为** 或 **并行。** 指令的 **为** 循环的循环控制变量，因此，该变量引用出现在循环内。  
  
 指定变量在 **firstprivate**， **lastprivate**或一个包含指令的 **减少** 在子句中的上下文导致隐式对该变量。  此类隐式引用也受到列表的要求的限制上面。  
  
 唯一 **默认** 子句。 **并行** 指令可以指定。  
  
 使用 **专用**、 **firstprivate**、 **lastprivate**、 **减少**和 **共享** 子句，变量的默认数据共享可以重写属性，如演示的由以下示例:  
  
```  
#pragma  omp  parallel  for  default(shared)  firstprivate(i)\  
   private(x)  private(r)  lastprivate(i)  
```