---
title: "编译器错误 C2785 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2785
dev_langs:
- C++
helpviewer_keywords:
- C2785
ms.assetid: d8d13360-0d00-4815-8475-b49c7f0dc0f3
caps.latest.revision: 11
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: a545935e06d958502fb3b97cb8969f92172ca6b6
ms.contentlocale: zh-cn
ms.lasthandoff: 10/10/2017

---
# <a name="compiler-error-c2785"></a>编译器错误 C2785
declaration1 和 declaration2 具有不同的返回类型  
  
 函数模板专用化的返回类型不同于主函数模板的返回类型。  
  
### <a name="to-correct-this-error"></a>更正此错误  
  
1.  检查一致性的函数模板的所有专用化。  
  
## <a name="example"></a>示例  
 下面的示例生成 C2785:  
  
```  
// C2785.cpp  
// compile with: /c  
template<class T> void f(T);  
  
template<> int f(int); // C2785  
template<> void f(int); // OK  
```
