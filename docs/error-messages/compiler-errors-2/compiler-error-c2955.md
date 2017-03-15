---
title: "编译器错误 C2955 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2955"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2955"
ms.assetid: 77709fb6-d69b-46fd-a62f-e8564563d01b
caps.latest.revision: 15
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 15
---
# 编译器错误 C2955
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“标识符”：类模板或别名泛型的使用需要模板或泛型参数列表  
  
 在没有模板和泛型参数列表的情况下，你不能将类模板或类泛型用作标识符。  
  
 有关详细信息，请参阅[类模板](../../cpp/class-templates.md)。  
  
 下面的示例生成 C2955，并演示如何修复此错误：  
  
```  
// C2955.cpp  
// compile with: /c  
template<class T>   
class X {};  
  
X x1;   // C2955  
X<int> x2;   // OK - this is how to fix it.  
```  
  
 当尝试为类模板中声明的函数进行超行定义时，也可能发生 C2955：  
  
```  
// C2955_b.cpp  
// compile with: /c  
template <class T>  
class CT {  
public:  
   void CTFunc();  
   void CTFunc2();  
};  
  
void CT::CTFunc() {}   // C2955  
  
// OK - this is how to fix it  
template <class T>  
void CT<T>::CTFunc2() {}  
  
```  
  
 使用泛型时也可能发生 C2955：  
  
```  
// C2955_c.cpp  
// compile with: /clr  
generic <class T>   
ref struct GC {   
   T t;  
};  
  
int main() {  
   GC^ g;   // C2955  
   GC <int>^ g;  
}  
```