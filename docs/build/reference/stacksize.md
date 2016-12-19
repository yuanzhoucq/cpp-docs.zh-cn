---
title: "STACKSIZE | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "STACKSIZE"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "STACKSIZE .def 文件语句"
ms.assetid: 4d8c79bd-1cb4-4e4d-90f2-b5a7a4d20e7a
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# STACKSIZE
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

设置堆栈的大小（以字节为单位）。  
  
```  
STACKSIZE reserve[,commit]  
```  
  
## 备注  
 另一种设置堆栈的方法是使用[堆栈分配](../../build/reference/stack-stack-allocations.md) \(\/STACK\) 选项。  有关 *reserve* 和 `commit` 参数的详细信息，请参见关于该选项的文档。  
  
 该选项对 DLL 无效。  
  
## 请参阅  
 [模块定义语句的规则](../../build/reference/rules-for-module-definition-statements.md)