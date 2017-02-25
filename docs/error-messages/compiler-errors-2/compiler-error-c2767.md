---
title: "编译器错误 C2767 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2767"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2767"
ms.assetid: e8f84178-a160-4d71-a236-07e4fcc11e96
caps.latest.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 12
---
# 编译器错误 C2767
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

托管数组或 WinRT 数组维度不匹配：应有 N 个参数，提供了 M 个  
  
 托管数组或 WinRT 数组的声明的格式不正确。  有关详细信息，请参阅[数组](../../windows/arrays-cpp-component-extensions.md)。  
  
 下面的示例生成 C2767，并演示如何修复此错误：  
  
```  
// C2767.cpp  
// compile with: /clr  
int main() {  
   array<int> ^p1 = new array<int>(2,3); // C2767  
   array<int> ^p2 = new array<int>(2);   // OK  
}  
```