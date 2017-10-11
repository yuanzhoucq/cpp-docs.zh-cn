---
title: "编译器错误 C2587 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2587
dev_langs:
- C++
helpviewer_keywords:
- C2587
ms.assetid: 7637a2c7-35d4-4b5a-a8f2-515a7bda98fd
caps.latest.revision: 8
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: dd0590e6d1fe6a41a3725e74d3d501fce6d509b6
ms.contentlocale: zh-cn
ms.lasthandoff: 10/10/2017

---
# <a name="compiler-error-c2587"></a>编译器错误 C2587
identifier： 非法用作本地变量的默认参数  
  
 本地变量不允许作为默认参数。  
  
 下面的示例生成 C2587:  
  
```  
// C2587.cpp  
// compile with: /c  
int i;  
void func() {  
   int j;  
   extern void func2( int k = j );  // C2587 -- local variable  
   extern void func3( int k = i );   // OK  
}  
```
