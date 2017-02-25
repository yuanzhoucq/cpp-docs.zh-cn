---
title: "编译器错误 C3352 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C3352"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3352"
ms.assetid: f233bed7-474e-425f-aad2-7801578169d4
caps.latest.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 11
---
# 编译器错误 C3352
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“function”: 指定的函数与委托类型“type”不匹配  
  
 `function` 的参数列表和委托的参数列表不匹配。  
  
 有关详细信息，请参阅[委托](../../windows/delegate-cpp-component-extensions.md)。  
  
 下面的示例生成 C3352：  
  
```  
// C3352.cpp  
// compile with: /clr  
delegate int D( int, int );  
ref class C {  
public:  
   int mf( int ) {  
      return 1;  
   }  
  
   // Uncomment the following line to resolve.  
   // int mf(int, int) { return 1; }  
};  
  
int main() {  
   C^ pC = gcnew C;  
   System::Delegate^ pD = gcnew D( pC, &C::mf );   // C3352  
}  
```  
  
 下面的示例生成 C3352：  
  
```  
// C3352_2.cpp  
// compile with: /clr:oldSyntax  
__delegate int D(int, int);  
  
__gc class C {  
public:  
   int mf(int) {  
      return 1;  
   }  
  
   // Uncomment the following line to resolve.  
   // int mf(int, int) { return 1; }  
};  
  
int main() {  
   C *pC = new C;  
   System::Delegate *pD = new D(pC, &C::mf);   // C3352  
}  
```