---
title: 编译器警告 （等级 1） C4813 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4813
dev_langs:
- C++
helpviewer_keywords:
- C4813
ms.assetid: c30bf877-ab04-4fe4-897e-8162092426f0
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 310c4c3a0d4be35e45c9593dc4f3cc1de00077d5
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33283245"
---
# <a name="compiler-warning-level-1-c4813"></a>编译器警告（等级 1）C4813
“function”：局部类的友元函数必须之前已经声明  
  
 内部类中的友元函数未在外部类中声明。  
  
 以下示例生成 C4813：  
  
```  
// C4813.cpp  
// compile with: /W1 /LD  
void MyClass()  
{  
   // void func();  
   class InnerClass  
   {  
      friend void func();   // C4813 uncomment declaration above  
   };  
}  
```