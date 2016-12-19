---
title: "编译器错误 C2681 | Microsoft Docs"
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
  - "C2681"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2681"
ms.assetid: eb42da6d-8d2c-43fd-986b-e73e2b004885
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器错误 C2681
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“type”: 名称的表达式类型无效  
  
 某转换运算符尝试从无效类型转换。  例如，如果使用 [dynamic\_cast](../../cpp/dynamic-cast-operator.md) 运算符将表达式转换为指针类型，则该源表达式必须是指针。  
  
 下面的示例生成 C2681：  
  
```  
// C2681.cpp  
class A { virtual void f(); };  
  
void g(int i) {  
    A* pa;  
    pa = dynamic_cast<A*>(i);  // C2681  
}  
```