---
title: "protected (C++) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "protected"
  - "protected_cpp"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "protected 关键字 [C++]"
  - "protected 关键字 [C++], 成员访问"
ms.assetid: 863d299f-fc0d-45d5-a1a7-bd24b7778a93
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# protected (C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

## 语法  
  
```  
protected:  
   [member-list]  
protected base-class  
```  
  
## 备注  
 `protected` 关键字指定对 *member\-list* 中的成员直到下一个访问说明符（**public** 或 `private`）或类定义的末尾的访问。  只能通过以下项使用声明为 `protected` 的类成员：  
  
-   最初声明这些成员的类的成员函数。  
  
-   最初声明这些成员的类的友元。  
  
-   使用公共或受保护访问（派生自最初声明这些成员的类）派生的类。  
  
-   也对受保护成员具有专用访问权限的以私有方式派生的直接类。  
  
 当以基类的名称开头时，`protected` 关键字指定基类的公共成员和保护成员是其派生类的保护成员。  
  
 保护成员不像 `private` 成员那样专用，private 成员仅对从中声明它们的类的成员可访问，但保护成员也不像 **public** 成员那样公开，public 成员在任何函数中均可访问。  
  
 也声明为 **static** 的保护成员对派生类的任何友元或成员函数均可访问。  也声明为 **static** 的保护成员对派生类中的友元或成员函数可访问，但只能通过指向派生类的指针、对派生类的引用或派生类的对象。  
  
 若要获得相关信息，请参阅[控制对类成员的访问](../cpp/friend-cpp.md)中的 [friend](../cpp/public-cpp.md)、[public](../cpp/private-cpp.md)、[private](../misc/controlling-access-to-class-members.md) 和成员访问表。  
  
## \/clr 专用  
 在 CLR 类型中，C\+\+访问说明符关键字（**public**、`private` 和 `protected`）可能影响与程序集相关的类型和方法的可见性。  有关详细信息，请参阅[类型和成员可见性](../misc/type-and-member-visibility.md)。  
  
> [!NOTE]
>  使用 [\/LN](../build/reference/ln-create-msil-module.md) 编译的文件不受此行为的影响。  在这种情况下，所有托管类（公共或私有）都将可见。  
  
## END \/clr 专用  
  
## 示例  
  
```  
// keyword_protected.cpp  
// compile with: /EHsc  
#include <iostream>  
  
using namespace std;  
class X {  
public:  
   void setProtMemb( int i ) { m_protMemb = i; }  
   void Display() { cout << m_protMemb << endl; }  
protected:  
   int  m_protMemb;  
   void Protfunc() { cout << "\nAccess allowed\n"; }  
} x;  
  
class Y : public X {  
public:  
   void useProtfunc() { Protfunc(); }  
} y;  
  
int main() {  
   // x.m_protMemb;         error, m_protMemb is protected  
   x.setProtMemb( 0 );   // OK, uses public access function  
   x.Display();  
   y.setProtMemb( 5 );   // OK, uses public access function  
   y.Display();  
   // x.Protfunc();         error, Protfunc() is protected  
   y.useProtfunc();      // OK, uses public access function  
                        // in derived class  
}  
```  
  
## 请参阅  
 [控制对类成员的访问](../misc/controlling-access-to-class-members.md)   
 [C\+\+ 关键字](../cpp/keywords-cpp.md)