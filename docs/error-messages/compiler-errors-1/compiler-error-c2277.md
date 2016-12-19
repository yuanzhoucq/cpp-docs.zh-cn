---
title: "编译器错误 C2277 | Microsoft Docs"
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
  - "C2277"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2277"
ms.assetid: 15a83b07-8731-4524-810b-267f65a7844f
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器错误 C2277
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“identifier”: 无法获取该成员函数的地址  
  
 无法获取成员函数的地址。  
  
 下面的示例生成 C2277：  
  
```  
// C2277.cpp  
class A {  
public:  
   A();  
};  
(*pctor)() = &A::A;   // C2277   
```