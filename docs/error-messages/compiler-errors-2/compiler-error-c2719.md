---
title: "编译器错误 C2719 | Microsoft Docs"
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
  - "C2719"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2719"
ms.assetid: ea6236d3-8286-45cc-9478-c84ad3dd3c8e
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器错误 C2719
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“parameter”：不对齐具有 \_\_declspec\(align\('\#'\)\) 的形参  
  
 函数参数上不允许使用[对齐](../../cpp/align-cpp.md) `__declspec` 修饰符。  函数参数的对齐方式由所使用的调用约定控制。  有关详细信息，请参阅[调用约定](../../cpp/calling-conventions.md)。  
  
 以下示例将生成 C2719，并演示如何修复此错误：  
  
```  
// C2719.cpp  
void func(int __declspec(align(32)) i);   // C2719  
// try the following line instead  
// void func(int i);  
```