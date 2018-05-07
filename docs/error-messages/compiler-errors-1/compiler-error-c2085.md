---
title: 编译器错误 C2085 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2085
dev_langs:
- C++
helpviewer_keywords:
- C2085
ms.assetid: 0a86785c-8e6f-481b-8c7b-412220c1950d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c0fe489dbdd0934926a056bbc7e5539f40ca1ba8
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
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