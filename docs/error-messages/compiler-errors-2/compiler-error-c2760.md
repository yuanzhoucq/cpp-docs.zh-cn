---
title: 编译器错误 C2760 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2760
dev_langs:
- C++
helpviewer_keywords:
- C2760
ms.assetid: 585757fd-d519-43f3-94e5-50316ac8b90b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: beee34b7dfa31365e9bdf79c843cca501a930e02
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c2760"></a>编译器错误 C2760
语法错误： 预期 name1 不 name2  
  
 强制转换运算符用于无效的运算符。  
  
 下面的示例生成 C2760:  
  
```  
// C2760.cpp  
class B {};  
class D : public B {};  
  
void f(B* pb) {  
    D* pd1 = static_cast<D*>(pb);  
    D* pd2 = static_cast<D*>=(pb);  // C2760  
    D* pd3 = static_cast<D*=(pb);   // C2760  
}  
```