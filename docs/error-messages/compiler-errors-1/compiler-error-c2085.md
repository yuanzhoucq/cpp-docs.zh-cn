---
title: "编译器错误 C2085 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2085
dev_langs:
- C++
helpviewer_keywords:
- C2085
ms.assetid: 0a86785c-8e6f-481b-8c7b-412220c1950d
caps.latest.revision: 7
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: 45805bbea2eca77ae81922088471e99de26be1e4
ms.contentlocale: zh-cn
ms.lasthandoff: 10/09/2017

---
# <a name="compiler-error-c2085"></a>编译器错误 C2085
identifier： 形参列表中没有  
  
 函数定义中但不是在形参列表中，已声明该标识符。 (仅适用于 ANSI C)  
  
 下面的示例生成 C2085:  
  
```  
// C2085.c  
void func1( void )  
int main( void ) {}   // C2085  
```  
  
 可能的解决方法：  
  
```  
// C2085b.c  
void func1( void );  
int main( void ) {}  
```  
  
 用分号缺失`func1()`看起来像函数定义，而不是原型，因此`main`中定义`func1()`，标识符中生成错误 C2085 `main`。
