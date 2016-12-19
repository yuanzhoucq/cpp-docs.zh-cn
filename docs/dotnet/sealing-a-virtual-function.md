---
title: "密封虚函数 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__sealed 关键字"
  - "派生类, 虚函数"
  - "sealed 关键字 [C++]"
  - "虚函数, 密封"
ms.assetid: 0e9fae03-6425-4512-9a24-8ccb6dc8a0d4
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 密封虚函数
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

从 C\+\+ 托管扩展到 [!INCLUDE[cpp_current_long](../Token/cpp_current_long_md.md)]，密封虚函数的语法已发生更改。  
  
 在托管扩展中，`__sealed` 用于修改引用类型，不允许派生类中该方法后续重写（请参见 [托管类类型的声明](../dotnet/declaration-of-a-managed-class-type.md)），或者用于修改虚函数，不允许派生类中该方法的后续重写。  例如：  
  
```  
__gc class base { public: virtual void f(); };  
__gc class derived : public base {  
public:  
   __sealed void f();  
};  
```  
  
 在本例中，`derived::f()` 基于函数原型的精确匹配重写 `base::f()` 实例。  `__sealed` 关键字指示从派生类继承的后续类无法提供 `derived::f()` 的重写。  
  
 在新语法中，`sealed` 放置在签名后面，而不允许出现在实际函数原型之前的任何位置（这在以前是允许的）。  此外，`sealed` 的使用还要求显式使用 `virtual` 关键字。  也就是说，上述 `derived` 的正确转换如下：  
  
```  
ref class derived: public base {  
public:  
   virtual void f() override sealed;  
};  
```  
  
 此实例中缺少 `virtual` 关键字会导致错误。  在新语法中，上下文关键字 `abstract` 可用在 `=0` 的位置以指示一个纯虚函数。  托管扩展中不支持这样做。  例如：  
  
```  
__gc class base { public: virtual void f()=0; };  
```  
  
 可重新编写为  
  
```  
ref class base { public: virtual void f() abstract; };  
```  
  
## 请参阅  
 [类或接口中的成员声明 \(C\+\+\/CLI\)](../dotnet/member-declarations-within-a-class-or-interface-cpp-cli.md)   
 [sealed](../windows/sealed-cpp-component-extensions.md)