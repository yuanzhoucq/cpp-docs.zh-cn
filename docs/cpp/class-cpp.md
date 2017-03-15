---
title: "class (C++) | Microsoft Docs"
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
  - "class_cpp"
  - "class"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "class 关键字 [C++]"
  - "类类型, class 语句"
ms.assetid: dd23c09f-6598-4069-8bff-69c7f2518b9f
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# class (C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

`class` 关键字声明类类型或定义类类型的对象。  
  
## 语法  
  
```  
  
      [template-spec]  
       class [ms-decl-spec] [tag [: base-list ]]  
{  
   member-list  
} [declarators];  
[ class ] tag declarators;  
```  
  
#### 参数  
 `template-spec`  
 可选模板说明。  有关更多信息，请参见 [模板规范](../Topic/Template%20Specifications.md)。  
  
 `class`  
 `class` 关键字。  
  
 `ms-decl-spec`  
 可选存储类说明  有关更多信息，请参考关键字 [\_\_declspec](../cpp/declspec.md)。  
  
 `tag`  
 给定于类的类型名称。  在类范围内的标记成为了保留字。  标志是可选项。  如果省略，定义匿名类。  有关更多信息，请参见 [Anonymous Class Types](../cpp/anonymous-class-types.md)。  
  
 `base-list`  
 此类派生其成员的类或结构的可选列表。  有关更多信息，请参见[基类](../cpp/base-classes.md)。  每个基类或结构名称可以在访问说明符 \([公用](../cpp/public-cpp.md)、 [专用](../cpp/private-cpp.md)， [保护](../cpp/protected-cpp.md)\) 和 [虚拟](../cpp/virtual-cpp.md) 关键字之前。  有的更多信息，请参见 [Controlling Access to Class Members](../misc/controlling-access-to-class-members.md)（控制访问类成员）中的成员访问表。  
  
 `member-list`  
 类成员列表。  有关更多信息，请参考 [类成员概述](../cpp/class-member-overview.md)。  
  
 `declarators`  
 指定类类型一个或多个实例名称的声明符列表。  如果类的所有数据成员是 `public`，声明符可以包含初始值设定项列表。  这在数据成员被默认为 `public` 的结构中比在类中更常见.  有关更多信息，请参见[声明符概述](../cpp/overview-of-declarators.md)。  
  
## 备注  
 一般有关类的更多信息，请参见以下主题之一：  
  
-   [struct](../cpp/struct-cpp.md)  
  
-   [union](../cpp/unions.md)  
  
-   [\_\_multiple\_inheritance](../cpp/inheritance-keywords.md)  
  
-   [\_\_single\_inheritance](../cpp/inheritance-keywords.md)  
  
-   [\_\_virtual\_inheritance](../cpp/inheritance-keywords.md)  
  
 有关托管类和结构的信息，请参见 [Classes and Structs](../windows/classes-and-structs-cpp-component-extensions.md)  
  
## 示例  
  
```  
// class.cpp  
// compile with: /EHsc  
// Example of the class keyword  
// Exhibits polymorphism/virtual functions.  
  
#include <iostream>  
#include <string>  
#define TRUE = 1  
using namespace std;  
  
class dog  
{  
public:  
   dog()  
   {  
      _legs = 4;  
      _bark = true;  
   }  
  
   void setDogSize(string dogSize)  
   {  
      _dogSize = dogSize;  
   }  
   virtual void setEars(string type)      // virtual function  
   {  
      _earType = type;  
   }  
  
private:  
   string _dogSize, _earType;  
   int _legs;  
   bool _bark;  
  
};  
  
class breed : public dog  
{  
public:  
   breed( string color, string size)  
   {  
      _color = color;  
      setDogSize(size);  
   }  
  
   string getColor()  
   {  
      return _color;  
   }  
  
   // virtual function redefined  
   void setEars(string length, string type)  
   {  
      _earLength = length;  
      _earType = type;  
   }  
  
protected:  
   string _color, _earLength, _earType;  
};  
  
int main()  
{  
   dog mongrel;  
   breed labrador("yellow", "large");  
   mongrel.setEars("pointy");  
   labrador.setEars("long", "floppy");  
   cout << "Cody is a " << labrador.getColor() << " labrador" << endl;  
}  
```  
  
## 请参阅  
 [C\+\+ 关键字](../cpp/keywords-cpp.md)   
 [类和结构](../cpp/classes-and-structs-cpp.md)