---
title: "编译器错误 C3860 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C3860"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3860"
ms.assetid: 1fb5110d-594e-4f1c-8773-888233af1313
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# 编译器错误 C3860
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

类类型名称后面的类型参数列表必须按类型参数列表中使用的顺序列出参数  
  
 泛型或模板参数列表的格式错误。  
  
 下面的示例生成 C3860：  
  
```  
// C3860.cpp  
// compile with: /LD  
template <class T1, class T2>  
struct A {  
   void f();  
};  
  
template <class T2, class T1>  
void A<T1, T2>::f() {}   // C3860  
```  
  
 可能的解决方案：  
  
```  
// C3860b.cpp  
// compile with: /c  
template <class T1, class T2>  
struct A {  
   void f();  
};  
  
template <class T2, class T1>  
void A<T2, T1>::f() {}  
```  
  
 使用以下泛型时也可能发生 C3860 错误：  
  
```  
// C3860c.cpp  
// compile with: /clr  
generic<class T,class U>  
ref struct GC {  
   void f();  
};  
  
generic<class T, class U>  
void GC<T,T>::f() {}   // C3860  
```  
  
 可能的解决方案：  
  
```  
// C3860d.cpp  
// compile with: /clr /c  
generic<class T,class U>  
ref struct GC {  
   void f();  
};  
  
generic<class T, class U>  
void GC<T,U>::f() {}  
```