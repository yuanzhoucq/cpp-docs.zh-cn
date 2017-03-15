---
title: "编译器错误 C2248 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2248"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2248"
ms.assetid: 7a3ba0e8-d3b9-4bb9-95db-81ef17e31d23
caps.latest.revision: 22
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 22
---
# 编译器错误 C2248
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“member”: 无法访问在类“class”中声明的“access”成员  
  
 派生类的成员无法访问基类的 `private` 成员。  您无法访问类实例的 `private` 或 `protected` 成员。  
  
 有关 C2248 的更多信息，请参见知识库文章 KB243351。  
  
 下面的示例生成 C2248：  
  
```  
// C2248.cpp  
#include <stdio.h>  
class X {  
public:  
   int  m_pubMemb;  
   void setPrivMemb( int i ) {  
      m_privMemb = i;  
      printf_s("\n%d", m_privMemb);  
   }  
protected:  
   int  m_protMemb;  
  
private:  
   int  m_privMemb;  
} x;  
  
int main() {  
   x.m_pubMemb = 4;  
   printf_s("\n%d", x.m_pubMemb);  
   x.m_protMemb = 2;   // C2248 m_protMemb is protected  
   x.m_privMemb = 3;   // C2248  m_privMemb is private  
   x.setPrivMemb(0);   // OK uses public access function  
}  
```  
  
 公开 C2248 的另一个一致性问题是模板友元和专用化的使用。  有关更多信息，请参见[链接器工具错误 LNK2019](../../error-messages/tool-errors/linker-tools-error-lnk2019.md)。  
  
```  
// C2248_b.cpp  
template<class T>  
void f(T t) {  
   t.i;   // C2248  
}  
  
struct S {  
private:  
   int i;  
  
public:  
   S() {}  
   // Delete the following line to resolve.  
   friend void f(S);   // refer to the non-template function void f(S)  
  
   // Uncomment the following line to resolve.  
   // friend void f<S>(S);  
};  
  
int main() {  
   S s;  
   f<S>(s);  
}  
```  
  
 公开 C2248 的另一个一致性问题是尝试声明类的友元且该类对在类范围内的友元声明不可见。  在这种情况下，对封闭类授予友元身份可解决此错误。  
  
```  
// C2248_c.cpp  
// compile with: /c  
class T {  
   class S {  
      class E {};  
   };  
   friend class S::E;   // C2248  
};  
  
class A {  
   class S {  
      class E {};  
      friend class A;   // grant friendship to enclosing class  
   };  
   friend class S::E;   // OK  
};  
```