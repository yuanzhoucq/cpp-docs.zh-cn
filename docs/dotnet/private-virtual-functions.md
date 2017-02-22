---
title: "私有虚函数 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "访问修饰符 [C++], 对于类成员"
  - "派生类, 虚函数"
  - "成员访问 [C++], 虚拟成员"
  - "虚函数, private"
ms.assetid: 04448086-bf72-44be-9c1f-dfda1744949e
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 10
---
# 私有虚函数
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

从 C\+\+ 托管扩展到 [!INCLUDE[cpp_current_long](../Token/cpp_current_long_md.md)]，处理派生类中私有虚函数的方式已发生更改。  
  
 在托管扩展中，虚函数的访问级别不约束它在派生类内部被重写的能力。  在新语法中，虚函数无法重写无法访问的基类虚函数。  例如：  
  
```  
__gc class MyBaseClass {  
   // inaccessible to a derived class   
   virtual void g();  
};  
  
__gc class MyDerivedClass : public MyBaseClass {  
public:  
   // okay in Managed Extensions; g() overrides MyBaseClass::g()  
   // error in new syntax; cannot override: MyBaseClass::g() is inaccessible …  
   void g();  
};  
```  
  
 新语法上没有此类设计的真正映射。  只得使基类成员可访问 — 即非私有基类。  继承的方法不必具有相同的访问。  在下面的示例中，侵害性最小的更改是使 MyBaseClass 成员 `protected`。  这样，仍会禁止常规程序通过 MyBaseClass 访问该方法。  
  
```  
ref class MyBaseClass {  
protected:  
   virtual void g();  
};  
  
ref class MyDerivedClass : MyBaseClass {  
public:  
   virtual void g() override;  
};  
```  
  
 请注意：在新语法中，基类中没有显式 `virtual` 关键字将生成警告消息。  
  
## 请参阅  
 [类或接口中的成员声明 \(C\+\+\/CLI\)](../dotnet/member-declarations-within-a-class-or-interface-cpp-cli.md)   
 [成员可见性](../misc/member-visibility.md)