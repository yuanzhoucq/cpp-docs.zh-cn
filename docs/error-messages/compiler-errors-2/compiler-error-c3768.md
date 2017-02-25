---
title: "编译器错误 C3768 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C3768"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3768"
ms.assetid: 091f0d53-1dff-43fd-813d-5c43c85b6ab0
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# 编译器错误 C3768
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

在纯托管代码中不能采用虚拟 vararg 函数的地址  
  
 当使用 `/clr:pure` 进行编译时，不能采用虚拟 `vararg` 函数的地址。  
  
 下面的示例生成 C3768：  
  
```  
// C3768.cpp  
// compile with: /clr:pure  
struct A  
{  
   virtual void f(...);  
};  
  
int main()  
{  
   &(A::f);   // C3768  
}  
```