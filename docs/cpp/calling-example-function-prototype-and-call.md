---
title: "调用示例：函数原型和调用 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "调用约定, 示例 [C++]"
  - "示例 [C++], 调用约定"
ms.assetid: e4275d1f-df2e-4bfc-a162-eb43ec69554a
caps.latest.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# 调用示例：函数原型和调用
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

## Microsoft 专用  
 以下示例显示了使用各种调用约定执行函数调用的结果。  
  
 此示例基于以下函数主干。  将 `calltype` 替换为适当的调用约定。  
  
```  
void    calltype MyFunc( char c, short s, int i, double f );  
.  
.  
.  
void    MyFunc( char c, short s, int i, double f )  
    {  
    .  
    .  
    .  
    }  
.  
.  
.  
MyFunc ('x', 12, 8192, 2.7183);  
```  
  
 有关详细信息，请参阅[调用结果示例](../cpp/results-of-calling-example.md)。  
  
## 结束 Microsoft 专用  
  
## 请参阅  
 [调用约定](../cpp/calling-conventions.md)