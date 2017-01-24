---
title: "override 说明符 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "override 标识符"
ms.assetid: b286fb46-9374-4ad8-b2e7-4607119b6133
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# override 说明符
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

您可使用 `override` 关键字来指定在基类中重写虚函数的成员函数。  
  
## 语法  
  
```  
  
function-declaration override;  
```  
  
## 备注  
 `override` 仅在成员函数声明之后使用时才是区分上下文的且具有特殊含义；否则，它不是保留的关键字。  
  
## 示例  
 使用 `override` 有助于防止您的代码中出现意外的继承行为。  以下示例演示在未使用 `override` 的情况下，可能不打算使用派生类的成员函数行为。  编译器不会发出此代码的任何错误。  
  
```cpp  
class BaseClass  
{  
    virtual void funcA();  
    virtual void funcB() const;  
    virtual void funcC(int = 0);  
    void funcD();  
};  
  
class DerivedClass: public BaseClass  
{  
    virtual void funcA(); // ok, works as intended  
  
    virtual void funcB(); // DerivedClass::funcB() is non-const, so it does not  
                          // override BaseClass::funcB() const and it is a new member function  
  
    virtual void funcC(double = 0.0); // DerivedClass::funcC(double) has a different  
                                      // parameter type than BaseClass::funcC(int), so  
                                      // DerivedClass::funcC(double) is a new member function  
  
};  
  
```  
  
 当使用 `override` 时，编译器会生成错误，而不会在不提示的情况下创建新的成员函数。  
  
```cpp  
class BaseClass  
{  
    virtual void funcA();  
    virtual void funcB() const;  
    virtual void funcC(int = 0);  
    void funcD();  
};  
  
class DerivedClass: public BaseClass  
{  
    virtual void funcA() override; // ok  
  
    virtual void funcB() override; // compiler error: DerivedClass::funcB() does not   
                                   // override BaseClass::funcB() const  
  
    virtual void funcC( double = 0.0 ) override; // compiler error:   
                                                 // DerivedClass::funcC(double) does not   
                                                 // override BaseClass::funcC(int)  
  
    void funcD() override; // compiler error: DerivedClass::funcD() does not   
                           // override the non-virtual BaseClass::funcD()  
};  
  
```  
  
 若要指定不能重写函数且不能继承类，请使用 [final](../cpp/final-specifier.md) 关键字。  
  
## 请参阅  
 [final 说明符](../cpp/final-specifier.md)   
 [C\+\+ 关键字](../cpp/keywords-cpp.md)   
 [\(NOTINBUILD\) C\+\+ Type Names](http://msdn.microsoft.com/zh-cn/b53ba470-e583-4e5c-b634-6018f6110674)