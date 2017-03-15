---
title: "编译器错误 C2027 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2027"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2027"
ms.assetid: a39150c0-ec04-45ec-934c-a838bfe76627
caps.latest.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 9
---
# 编译器错误 C2027
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

使用了未定义类型“type”  
  
 类型只有经过定义才能使用。  若要解决该错误，请确保在引用类型前已对其进行了完全定义。  
  
## 示例  
 下面的示例生成 C2027。  
  
```  
// C2027.cpp  
class C;  
class D {  
public:  
   void func() {  
   }  
};  
  
int main() {  
   C *pC;  
   pC->func();   // C2027  
  
   D *pD;  
   pD->func();  
}  
```  
  
## 示例  
 有可能声明一个指向已声明但未定义的类型的指针。但是 Visual C\+\+ 不允许引用未定义的类型。  
  
 下面的示例生成 C2027。  
  
```  
// C2027_b.cpp  
class A;  
A& CreateA();  
  
class B;  
B* CreateB();  
  
int main() {  
   CreateA();   // C2027  
   CreateB();   // OK  
}  
```