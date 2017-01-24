---
title: "void (C++) | Microsoft Docs"
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
  - "void"
  - "void_cpp"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "函数 [C++], void"
  - "指针, void"
  - "void 关键字 [C++]"
ms.assetid: d203edba-38e6-4056-8b89-011437351057
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# void (C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

用作函数返回类型时，`void` 关键字指定函数不返回值。  当用于函数的参数列表时，void 将指定函数不采用任何参数。  用于指针声明时，void 指定该指针为“通用”。  
  
 如果指针类型为 **void \***，则该指针可以指向任何未使用 **const** 或 `volatile` 关键字声明的变量。  void 指针不能取消引用，除非它被强制转换为另一种类型。  void 指针可以转换为任何其他类型的数据指针。  
  
 void 指针可以指向函数，但不能指向 C\+\+ 中的类成员。  
  
 不能声明 void 类型的变量。  
  
## 示例  
  
```  
// void.cpp  
void vobject;   // C2182  
void *pv;   // okay  
int *pint; int i;  
int main() {  
   pv = &i;  
   // Cast optional in C required in C++  
   pint = (int *)pv;  
}   
```  
  
## 请参阅  
 [C\+\+ 关键字](../cpp/keywords-cpp.md)   
 [指向 void 类型的指针](../misc/pointers-to-type-void.md)   
 [基本类型](../cpp/fundamental-types-cpp.md)