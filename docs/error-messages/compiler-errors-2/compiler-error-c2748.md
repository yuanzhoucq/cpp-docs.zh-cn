---
title: "编译器错误 C2748 | Microsoft Docs"
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
  - "C2748"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2748"
ms.assetid: b63ac78b-a200-499c-afea-15af1a1e819e
caps.latest.revision: 11
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器错误 C2748
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

创建托管数组或 WinRT 数组时必须提供数组大小或数组初始值设定项  
  
 托管数组或 WinRT 数组的格式不正确。  有关详细信息，请参阅[数组](../../windows/arrays-cpp-component-extensions.md)。  
  
 下面的示例生成 C2748，并演示如何修复此错误：  
  
```  
// C2748.cpp  
// compile with: /clr  
int main() {  
   array<int> ^p1 = new array<int>();   // C2748  
   // try the following line instead  
   array<int> ^p2 = new array<int>(2);  
}  
```