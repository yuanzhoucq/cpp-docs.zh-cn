---
title: 编译器警告 （等级 3） C4823 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4823
dev_langs:
- C++
helpviewer_keywords:
- C4823
ms.assetid: 8a77560d-dcea-4cae-aebb-8ebf1b4cef85
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c29499a82601dcf653ff2f003441935f1d6841a6
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-3-c4823"></a>编译器警告（等级 3）C4823
function： 使用钉住指针但展开语义不会启用。 请考虑使用 /EHa  
  
要解锁的块范围中声明钉住指针指向托管堆上的对象，编译器将模拟"伪装"钉住指针具有析构函数，使该指针无效的本地类的析构函数的行为。 若要启用对析构函数的调用引发异常后，你必须启用对象展开，则你可以通过使用[/EHsc](../../build/reference/eh-exception-handling-model.md)。  
  
可以手动取消固定对象也可以忽略该警告。  
  
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
