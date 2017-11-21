---
title: "编译器警告 （等级 1） C4090 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4090
dev_langs: C++
helpviewer_keywords: C4090
ms.assetid: baad469d-23d4-45aa-ad9c-305b32d61e9a
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 3b508e27d72454568e26d2f1d173b05c8a65c250
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-1-c4090"></a>编译器警告 （等级 1） C4090
operation： 不同的 modifier 限定符  
  
 使用指定修饰符，防止它被修改不检测由编译器定义是在操作中使用的变量。 编译表达式时不进行修改。  
  
 时指向的指针，则可能引发此警告**const**或`volatile`项分配给未声明为指向指针**const**或`volatile`。  
  
 对于 C 程序发出此警告。 在 c + + 程序中，编译器会发出错误： [C2440](../../error-messages/compiler-errors-1/compiler-error-c2440.md)。  
  
 下面的示例生成 C4090:  
  
```  
// C4090.c  
// compile with: /W1  
int *volatile *p;  
int *const *q;  
int **r;  
  
int main() {  
   p = q;   // C4090  
   p = r;  
   q = p;   // C4090  
   q = r;  
   r = p;   // C4090  
   r = q;   // C4090  
}  
```