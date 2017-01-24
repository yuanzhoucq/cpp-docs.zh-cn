---
title: "编译器错误 C2739 | Microsoft Docs"
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
  - "C2739"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2739"
ms.assetid: 5b63e435-7631-43d7-805e-f2adefb7e517
caps.latest.revision: 11
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器错误 C2739
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“number”: 显式托管或 WinRT 数组维度必须介于 1 和 32 之间  
  
 数组维度不在 1 和 32 之间。  
  
 下面的示例生成 C2739，并演示如何修复此错误：  
  
```  
// C2739.cpp  
// compile with: /clr  
int main() {  
   array<int, -1>^a;   // C2739  
   // try the following line instead  
   // array<int, 2>^a;  
}  
```