---
title: "final 说明符 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "final"
  - "final_CPP"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "final 标识符"
ms.assetid: 649866d0-79d4-449f-ab74-f84b911b79a3
caps.latest.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# final 说明符
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

可以使用 `final` 关键字指定无法在派生类中重写的虚函数。  您还可以使用它指定无法继承的类。  
  
## 语法  
  
```  
  
function-declaration final;  
```  
  
```  
  
class class-name final base-classes  
```  
  
## 备注  
 `final` 只有在函数声明或类名称后使用时才是区分上下文的且具有特殊含义；否则，它不是保留的关键字。  
  
 在类声明中使用 `final` 时，`base-classes` 是声明的可选部分。  
  
## 示例  
 下面的示例使用 `final` 关键字指定无法重写虚函数。  
  
```cpp  
class BaseClass  
{  
    virtual void func() final;  
};  
  
class DerivedClass: public BaseClass  
{  
    virtual void func(); // compiler error: attempting to   
                         // override a final function  
};  
```  
  
 有关如何指定可以重写成员函数的信息，请参阅 [override 说明符](../cpp/override-specifier.md)"。  
  
 下一个示例使用 `final` 关键字指定无法继承类。  
  
```cpp  
class BaseClass final   
{  
};  
  
class DerivedClass: public BaseClass // compiler error: BaseClass is   
                                     // marked as non-inheritable  
{  
};  
```  
  
## 请参阅  
 [C\+\+ 关键字](../cpp/keywords-cpp.md)   
 [\(NOTINBUILD\) C\+\+ Type Names](http://msdn.microsoft.com/zh-cn/b53ba470-e583-4e5c-b634-6018f6110674)   
 [override 说明符](../cpp/override-specifier.md)