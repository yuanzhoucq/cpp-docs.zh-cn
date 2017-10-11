---
title: "编译器错误 C3821 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C3821
dev_langs:
- C++
helpviewer_keywords:
- C3821
ms.assetid: 2b327c7a-5faf-443c-ae82-944fae25b4df
caps.latest.revision: 12
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: 47e0a2ed3c824ed1598f7e998d4966b95cc9233b
ms.contentlocale: zh-cn
ms.lasthandoff: 10/10/2017

---
# <a name="compiler-error-c3821"></a>编译器错误 C3821
function： 托管的类型或函数不能在非托管函数  
  
 使用内联程序集的函数或[setjmp](../../c-runtime-library/reference/setjmp.md)不能包含值类型或托管的类。 若要修复此错误，删除内联程序集和`setjmp`或删除托管的对象。  
  
 如果你尝试在 vararg 函数中使用自动存储，也可能发生 C3821。  有关详细信息，请参阅[变量自变量列表 （...）(C + + /CLI CLI)](../../windows/variable-argument-lists-dot-dot-dot-cpp-cli.md)和[对于引用类型的 c + + 堆栈语义](../../dotnet/cpp-stack-semantics-for-reference-types.md)。  
  
## <a name="example"></a>示例  
 下面的示例生成 C3821。  
  
```  
// C3821a.cpp  
// compile with: /clr /c  
public ref struct R {};  
void test1(...) {  
   R r;   // C3821  
}  
```  
  
## <a name="example"></a>示例  
 下面的示例生成 C3821。  
  
```  
// C3821b.cpp  
// compile with: /clr  
// processor: /x86  
ref class A {  
   public:  
   int i;  
};  
  
int main() {  
   // cannot use managed classes in this function  
   A ^a;     
  
   __asm {  
      nop  
   }  
} // C3821  
```  

