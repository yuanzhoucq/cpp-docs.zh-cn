---
title: 编译器错误 C3230 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3230
dev_langs:
- C++
helpviewer_keywords:
- C3230
ms.assetid: 5ec53f25-59f6-4801-81e7-7b68bf04994d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 494aa6a04b1ec4844e243807e103d4d106380739
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33252405"
---
# <a name="compiler-error-c3230"></a>编译器错误 C3230
“function”：“template”的模板类型参数不能包含泛型类型参数：“param”  
  
 模板在编译时实例化，而泛型在运行时实例化。 因此，不能生成可调用模板的泛型代码，因为当泛型类型在最后才已知时，模板不能在运行时实例化。  
  
 以下示例生成 C3230：  
  
```  
// C3230.cpp  
// compile with: /clr /LD  
template <class S>   
void f(S t);  
  
generic <class U>  
ref class C {  
   void f1(U x) {  
      f(x);   // C3230  
   }  
};  
```