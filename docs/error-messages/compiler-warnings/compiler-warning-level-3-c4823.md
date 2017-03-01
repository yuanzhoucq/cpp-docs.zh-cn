---
title: "编译器警告 （等级 3） C4823 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C4823
dev_langs:
- C++
helpviewer_keywords:
- C4823
ms.assetid: 8a77560d-dcea-4cae-aebb-8ebf1b4cef85
caps.latest.revision: 12
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: c243063a9770542f137d5950e8a269f771960f74
ms.openlocfilehash: ea03723f9ccae2348a47ae4894097f5cd9f8b5a1
ms.lasthandoff: 02/24/2017

---
# <a name="compiler-warning-level-3-c4823"></a>编译器警告（等级 3）C4823
function︰ 钉住指针但展开的使用情况下不启用语义。 请考虑使用 /EHa  
  
若要取消固定在块范围中声明钉住指针指向托管堆上的对象，编译器将模拟"伪装"钉住指针包含使该指针无效的析构函数的局部类的析构函数的行为。 若要在引发异常后启用对析构函数的调用，您必须启用对象展开，可以通过执行此操作[/EHsc](../../build/reference/eh-exception-handling-model.md)。  
  
可以手动取消固定对象，并忽略该警告。  
  
## <a name="example"></a>示例  
下面的示例生成 C4823。  
  
```  
// C4823.cpp  
// compile with: /clr /W3 /EHa-  
using namespace System;  
  
ref struct G {  
   int m;  
};  
  
void f(G ^ pG) {  
   try {  
      pin_ptr<int> p = &pG->m;  
      // manually unpin, ignore warning  
      // p = nullptr;  
      throw gcnew Exception;  
   }  
   catch(Exception ^) {}  
}   // C4823 warning  
  
int main() {  
   f( gcnew G );  
}  
```  

