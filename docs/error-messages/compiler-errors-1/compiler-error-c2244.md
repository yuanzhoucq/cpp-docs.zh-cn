---
title: "编译器错误 C2244 | Microsoft Docs"
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
  - "C2244"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2244"
ms.assetid: d9911c12-ceb5-4f93-ac47-b44a485215c2
caps.latest.revision: 10
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器错误 C2244
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“identifier”: 无法将函数定义与现有的声明匹配  
  
 在没有括号的函数调用前使用了一元 \+ 运算符的异常用法。  
  
 此错误仅发生在 C\+\+ 项目中。  
  
 下面的示例生成 C2244：  
  
```  
// C2244.cpp  
int func(char) {  
   return 0;  
}   
  
int func(int) {  
   return 0;  
}  
  
int main() {  
   +func;   // C2244  
}  
```  
  
 在将不正确的函数签名用于类模板的成员函数时也会发生 C2244 错误。  
  
```  
// C2244b.cpp  
// compile with: /c  
template<class T>   
class XYZ {  
   void func(T t);  
};  
  
template<class T>  
void XYZ<T>::func(int i) {}   // C2244 wrong function signature  
// try the following line instead  
// void XYZ<T>::func(T t) {}  
```  
  
 在将不正确的函数签名用于成员函数模板时也会发生 C2244 错误。  
  
```  
// C2244c.cpp  
// compile with: /c  
class ABC {  
   template<class T>   
   void func(int i, T t);  
};  
  
template<class T>  
void ABC::func(int i) {}   // C2244 wrong signature  
// try the following line instead  
// void ABC::func(int i, T t) {}  
```  
  
 无法使函数模板部分专用化。  
  
```  
// C2244d.cpp  
template<class T, class U>  
class QRS {  
   void func(T t, U u);  
};  
  
template<class T>  
void QRS<T,int>::func(T t, int u) {}   // C2244  
```