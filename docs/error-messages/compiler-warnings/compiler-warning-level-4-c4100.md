---
title: 编译器警告 （等级 4） C4100 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4100
dev_langs:
- C++
helpviewer_keywords:
- C4100
ms.assetid: 478ed97d-e502-49e4-9afb-ac2a6c61194b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4d3cf831590af2e1f2f7cd13d93c9d13ba217e11
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33292800"
---
# <a name="compiler-warning-level-4-c4100"></a>编译器警告（等级 4）C4100
identifier： 未引用的形式参数  
  
 形式的参数未引用的函数体中。 忽略未引用的参数。  
  
 当代码在调用析构函数，还可以发出 C4100 否则未引用的基元类型的参数。  这是 Visual c + + 编译器的限制。  
  
 下面的示例生成 C4100:  
  
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