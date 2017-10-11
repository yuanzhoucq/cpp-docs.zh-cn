---
title: "编译器错误 C2975 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2975
dev_langs:
- C++
helpviewer_keywords:
- C2975
ms.assetid: 526f6b9d-6c76-4c12-9252-1b1d7c1e06c7
caps.latest.revision: 10
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: 07b2b96cd79364215c9a859a9fd0282768ff45e4
ms.contentlocale: zh-cn
ms.lasthandoff: 10/10/2017

---
# <a name="compiler-error-c2975"></a>编译器错误 C2975
arg: type，预期的编译时常量表达式的模板参数无效  
  
 模板自变量与模板声明中; 不匹配常量表达式应出现在尖括号中。 变量不允许作为模板自变量。 请检查模板定义，以找到正确的类型。  
  
 下面的示例生成 C2975:  
  
```  
// C2975.cpp  
template<int I>  
class X {};  
  
int main() {  
   int i = 4, j = 2;  
   X<i + j> x1;   // C2975  
   X<6> x2;   // OK  
}  
```  
  
 当你使用 __LINE 时也会发生 C2975\_ \_作为编译时常量[/ZI](../../build/reference/z7-zi-zi-debug-information-format.md)。 一个解决方案是使用进行编译[/Zi](../../build/reference/z7-zi-zi-debug-information-format.md)而不是**/ZI**。  
  
```  
// C2975b.cpp  
// compile with: /ZI  
// processor: x86  
template<long line>   
void test(void) {}  
  
int main() {  
   test<__LINE__>();   // C2975  
}  
```
