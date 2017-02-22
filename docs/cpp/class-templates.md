---
title: "类模板 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "类模板"
  - "类 [C++], 针对类型的操作"
  - "模板, 类模板"
ms.assetid: 633a53c8-24ee-4c23-8c88-e7c3cb0b7ac3
caps.latest.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# 类模板
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

可以使用类模板创建一系列操作类型的类。  类模板是参数化类型。  它们指示可以为每个传入的参数（称作模板参数）的可能的值创建单独的类。  
  
 模板参数可以是类型或特定类型的常量值。  例如：  
  
```  
// class_templates.cpp  
template <class T, int i> class TempClass   
{  
public:  
    TempClass( void );  
    ~TempClass( void );  
    int MemberSet( T a, int b );  
private:  
    T Tarray[i];  
    int arraysize;  
};  
  
int main()  
{  
}  
```  
  
 在此示例中，模板化类使用两个参数：类型 `T` 和 int `i`。  `T` 参数可以是传递的任何类型，包括结构和类。  必须为 `i` 参数传递整数常量。  由于 `i` 是在编译时定义的常量，因此您可以使用标准数组声明定义大小 `i` 的成员数组。  
  
 有关详细信息，请参阅：  
  
-   [类模板的成员](../Topic/Members%20of%20Class%20Templates.md)  
  
-   [类成员的模板](../Topic/Templates%20for%20Class%20Members.md)  
  
-   [模板类的成员函数](../Topic/Member%20Functions%20of%20Template%20Classes.md)  
  
-   [嵌套类模板](../Topic/Nested%20Class%20Templates.md)  
  
-   [类模板实例化](../Topic/Class%20Template%20Instantiation.md)  
  
-   [类模板的显式专用化](../Topic/Explicit%20Specialization%20of%20Class%20Templates.md)  
  
-   [类模板的部分专用化](../cpp/template-specialization-cpp.md)  
  
-   [类模板的默认参数](../Topic/Default%20Arguments%20for%20Class%20Templates.md)  
  
-   [模板友元](../cpp/template-friends.md)  
  
## 请参阅  
 [模板](../cpp/templates-cpp.md)