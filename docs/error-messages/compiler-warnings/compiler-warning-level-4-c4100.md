---
title: "编译器警告（等级 4）C4100 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4100"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4100"
ms.assetid: 478ed97d-e502-49e4-9afb-ac2a6c61194b
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# 编译器警告（等级 4）C4100
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“identifier”: 未引用的形参  
  
 未在函数体中引用此形参。  已忽略未引用的形参。  
  
 当代码在基元类型的未引用参数上调用析构函数时，也可能发出 C4100 错误。这是 Visual C\+\+ 编译器的一个限制。  
  
 下面的示例生成 C4100：  
  
```  
// C4100.cpp  
// compile with: /W4  
void func(int i) {   // C4100, delete the unreferenced parameter to  
                     //resolve the warning  
   // i;   // or, add a reference like this  
}  
  
int main()  
{  
   func(1);  
}  
```