---
title: 编译器错误 C2422 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2422
dev_langs:
- C++
helpviewer_keywords:
- C2422
ms.assetid: ef0ec302-4028-4778-b134-0b8cea4bcad9
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 89a808e4b324b11c88be38ae7d8815bee4e232cd
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c2422"></a>编译器错误 C2422
操作数中的非法段重写  
  
 内联程序集代码错误地使用操作数段重写运算符 （冒号）。  可能的原因包括：  
  
-   该运算符前面寄存器不段寄存器。  
  
-   该运算符前面寄存器不是操作数中的唯一段寄存器。  
  
-   段重写运算符将显示在间接寻址运算符 （括号）。  
  
-   跟后面段重写运算符的表达式不是即时操作数或内存操作数。  
  
 下面的示例生成 C2422:  
  
```  
// C2422.cpp  
// processor: x86  
int main() {  
   _asm {  
      mov AX, [BX:ES]   // C2422  
      mov AX, ES   // OK  
   }  
}  
```