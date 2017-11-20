---
title: "编译器警告 （等级 1） C4717 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4717
dev_langs: C++
helpviewer_keywords: C4717
ms.assetid: 5ef3c6c7-8599-4714-a973-0f5b69cdab3c
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 63c67ff3bc00a62c94f82a0cf90f50ddfb9571b3
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-1-c4717"></a>编译器警告（等级 1）C4717
function： 所有控制路径的递归，函数将导致运行时堆栈溢出  
  
 通过函数的每个路径包含对函数的调用。 由于没有无法退出而不本身的第一个调用函数以递归方式，将永远不会退出该函数。  
  
 下面的示例生成 C4717:  
  
```  
// C4717.cpp  
// compile with: /W1 /c  
// C4717 expected  
int func(int x) {  
   if (x > 1)  
      return func(x - 1); // recursive call  
   else {  
      int y = func(0) + 1; // recursive call  
      return y;  
   }  
}  
  
int main(){  
   func(1);  
}  
```