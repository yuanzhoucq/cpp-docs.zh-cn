---
title: 编译器错误 C2683 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2683
dev_langs:
- C++
helpviewer_keywords:
- C2683
ms.assetid: db605e4f-601b-4d05-92a1-c43ca24de08d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 35619d93200c2f0e61dbf903f56a70bbe0c48d73
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33233641"
---
# <a name="compiler-error-c2683"></a>编译器错误 C2683
cast: type 不是多态类型  
  
 不能使用[dynamic_cast](../../cpp/dynamic-cast-operator.md)将从非多态类 （具有没有虚函数的类） 转换。  
  
 你可以使用[static_cast](../../cpp/static-cast-operator.md)来执行非多态类型的转换。 但是，`static_cast`不执行运行时检查。  
  
 下面的示例生成 C2683:  
  
```  
// C2683.cpp  
// compile with: /c  
class B { };  
class D : public B { };  
  
void f(B* pb) {  
   D* pd1 = dynamic_cast<D*>(pb);  // C2683  
   D* pd1 = static_cast<D*>(pb);   // OK  
}  
```