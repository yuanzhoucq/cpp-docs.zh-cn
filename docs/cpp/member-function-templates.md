---
title: "成员函数模板 | Microsoft Docs"
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
  - "函数模板, 成员函数"
ms.assetid: 83d51835-6a27-40ed-997c-7d90dc9182d8
caps.latest.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# 成员函数模板
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

术语成员模板引用了成员函数模板和嵌套类模板。  成员函数模板是类或类模板的成员的模板函数。  有关详细信息，请参阅[嵌套类模板](../Topic/Nested%20Class%20Templates.md)。  
  
 成员函数可以是多个环境中的函数模板。  类模板的所有函数都是泛型的，但却不称为成员模板或成员函数模板。  如果这些成员函数采用其自己的模板参数，则将它们视为成员函数模板。  有关详细信息，请参阅[模板类的成员函数](../Topic/Member%20Functions%20of%20Template%20Classes.md)。  
  
## 示例  
 非模板或模板类的成员函数模板将声明为带有其模板参数的函数模板。  
  
```  
// member_function_templates.cpp  
struct X  
{  
   template <class T> void mf(T* t) {}  
};  
  
int main()  
{  
   int i;  
   X* x = new X();  
   x->mf(&i);  
}  
```  
  
## 示例  
 以下示例显示模板类的成员函数模板。  
  
```  
// member_function_templates2.cpp  
template<typename T>  
class X  
{  
public:  
   template<typename U>  
   void mf(const U &u)  
   {  
   }  
};  
  
int main()  
{  
}  
```  
  
## 示例  
 此外，在 Visual Studio .NET 2003 及更高版本中，成员模板也可以在类的外部定义。  
  
```  
// defining_member_templates_outside_class.cpp  
template<typename T>  
class X  
{  
public:  
   template<typename U>  
   void mf(const U &u);  
};  
  
template<typename T> template <typename U>  
void X<T>::mf(const U &u)  
{  
}  
  
int main()  
{  
}  
```  
  
## 示例  
 局部类不允许具有成员模板。  
  
 当使用与基类虚函数相同的名称进行声明时，成员模板函数不能是虚函数并且不能从基类重写虚函数。  
  
 Visual C\+\+ .NET 2003 引入了对模板化的用户定义转换的支持。  以下示例按照以下标准中的规定在 Visual C\+\+ .NET 2003 中运行。  
  
```  
// templated_user_defined_conversions.cpp  
template <class T>  
struct S  
{  
   template <class U> operator S<U>()  
   {  
      return S<U>();  
   }  
};  
  
int main()  
{  
   S<int> s1;  
   S<long> s2 = s1;  // Convert s1 using UDC and copy constructs S<long>.  
}  
```  
  
## 请参阅  
 [函数模板](../cpp/function-templates.md)