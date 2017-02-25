---
title: "编译器警告（等级 1）C4142 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4142"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4142"
ms.assetid: 1fdfc3dc-60a2-4f00-b133-20e400f9b7a6
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# 编译器警告（等级 1）C4142
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

类型的良性重定义  
  
 重新定义类型的方式对生成的代码没有任何影响。  
  
 通过检查下面的可能原因进行修复：  
  
-   派生类的成员函数与相应的基类成员函数有不同的返回类型。  
  
-   使用不同语法重新定义用 `typedef` 命令定义的类型。  
  
 下面的示例生成 C4142：  
  
```  
// C4142.c  
// compile with: /W1  
float X2;  
X2 = 2.0 + 1.0;   // C4142  
  
int main() {  
   float X2;  
   X2 = 2.0 + 1.0;   // OK  
}  
```