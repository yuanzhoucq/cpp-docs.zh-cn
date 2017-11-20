---
title: "编译器警告 （等级 1） C4552 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4552
dev_langs: C++
helpviewer_keywords: C4552
ms.assetid: ebbbb5ee-1c19-45bd-b386-41a19630fc76
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 6e7b19b59653d8fa670bddf8674051422b94cf1e
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-1-c4552"></a>编译器警告（等级 1）C4552
operator： 运算符起任何作用;预期带副作用的运算符  
  
 如果表达式语句作为表达式顶部有一个没有任何副作用的运算符，它可能是一个错误。  
  
 若要覆盖此警告，请将表达式放在括号中。  
  
 下面的示例生成 C4552:  
  
```  
// C4552.cpp  
// compile with: /W1  
int main() {  
   int i, j;  
   i + j;   // C4552  
   // try the following line instead  
   // (i + j);  
}  
```