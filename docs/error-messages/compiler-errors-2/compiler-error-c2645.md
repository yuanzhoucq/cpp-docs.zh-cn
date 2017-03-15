---
title: "编译器错误 C2645 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2645"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2645"
ms.assetid: 6609c2fa-c3b2-4a6b-8e8d-58fb52f67175
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# 编译器错误 C2645
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

指向成员的指针没有限定名\(找到“:: \*”\)  
  
 指向成员的指针的声明没有指定类。  
  
 下面的示例生成 C2645：  
  
```  
// C2645.cpp  
class A {};  
int main() {  
   int B::* bp;   // C2645 B not defined  
   int A::* ap;   // OK  
}  
```