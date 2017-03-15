---
title: "编译器警告 C4355 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4355"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4355"
ms.assetid: b819ecab-8a07-42d7-8fa4-1180d51626c0
caps.latest.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 9
---
# 编译器警告 C4355
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“this”: 用于基成员初始值设定项列表  
  
 **this** 指针仅在非静态成员函数中有效。  它不能在基类的初始值设定项列表中使用。  
  
 基类构造函数和类成员构造函数先于 **this** 构造函数被调用。  实际上，您已将指向非构造对象的指针传递给了另一个构造函数。  如果那些其他的构造函数访问此构造函数上的任何成员或调用其上的成员函数，结果将是不确定的。  应一直不使用 **this** 指针，直到所有构造都已完成。  
  
 默认情况下关闭此警告。  有关更多信息，请参见[默认情况下处于关闭状态的编译器警告](../../preprocessor/compiler-warnings-that-are-off-by-default.md)。  
  
 下面的示例生成 C4355：  
  
```  
// C4355.cpp  
// compile with: /w14355 /c  
#include <tchar.h>  
  
class CDerived;  
class CBase {  
public:  
   CBase(CDerived *derived): m_pDerived(derived) {};  
   ~CBase();  
   virtual void function() = 0;  
  
   CDerived * m_pDerived;  
};  
  
class CDerived : public CBase {  
public:  
   CDerived() : CBase(this) {};   // C4355 "this" used in derived c'tor  
   virtual void function() {};  
};  
  
CBase::~CBase() {  
   m_pDerived -> function();  
}  
  
int main() {  
   CDerived myDerived;  
}  
```