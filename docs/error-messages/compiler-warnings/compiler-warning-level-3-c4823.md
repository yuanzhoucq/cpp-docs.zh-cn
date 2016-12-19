---
title: "编译器警告（等级 3）C4823 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4823"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4823"
ms.assetid: 8a77560d-dcea-4cae-aebb-8ebf1b4cef85
caps.latest.revision: 12
caps.handback.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器警告（等级 3）C4823
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“function”: 使用钉住指针，但未启用展开语义。请考虑使用 \/EHa  
  
 若要断开通过在块范围中声明的钉住指针所指向的托管堆上的对象，编译器将模拟局部类的析构函数的行为，“假装”钉住指针具有使该指针无效的析构函数。  若要在引发异常后启用对析构函数的调用，必须启用对象展开，您可以通过使用 [\/EHsc](../../build/reference/eh-exception-handling-model.md) 来启用对象展开。  
  
 还可以手动断开对象并忽略此警告。  
  
## 示例  
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
  
## 示例  
 使用 **\/clr:oldSyntax** 也会生成 C4823。  下面的示例生成 C4823。  
  
```  
// C4823_b.cpp  
// compile with: /clr:oldSyntax /W3 /EHa-  
using namespace System;  
  
__gc struct G {  
   int m;  
};  
  
void f(G* pG) {  
   try {  
      int __pin* p = &pG->m;  
      // manually unpin, ignore warning  
      // p = 0;  
      throw new Exception;  
   }  
   catch(Exception*) {}  
}   // C4823  
  
int main() {  
   f( new G );  
}  
```