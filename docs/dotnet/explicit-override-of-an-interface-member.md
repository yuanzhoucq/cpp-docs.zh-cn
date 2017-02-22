---
title: "接口成员的显式重写 | Microsoft Docs"
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
  - "虚函数的显式重写"
  - "函数 [C++], 重写"
  - "接口成员, 显式重写"
  - "重写函数"
  - "虚函数, 显式重写"
ms.assetid: 46f1f536-bf43-4311-9a17-ff2282e528a9
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# 接口成员的显式重写
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

声明显式重写类中接口成员的语法已从 Managed Extensions for C\+\+ 更改为 [!INCLUDE[cpp_current_long](../Token/cpp_current_long_md.md)]。  
  
 经常需要在实现接口的类中提供两个接口成员的实例 — 其中一个在通过接口句柄操作类对象时使用，而另一个在通过类接口使用类对象时使用。  例如：  
  
```  
public __gc class R : public ICloneable {  
   // to be used through ICloneable  
   Object* ICloneable::Clone();  
  
   // to be used through an R  
   R* Clone();  
};  
```  
  
 在托管扩展中，通过用接口名称限定的方法名称来提供接口方法的显式声明来实现此目的。  未限定特定的类的实例。  在此示例中，当通过 `R` 的实例显式调用 `Clone` 时，将消除向下转换其返回值的需要。  
  
 在新的语法中，引入了一个通用重写机制代替托管扩展语法。  将重写我们的示例，如下所示：  
  
```  
public ref class R : public ICloneable {  
public:  
   // to be used through ICloneable  
   virtual Object^ InterfaceClone() = ICloneable::Clone;  
  
   // to be used through an R  
   virtual R^ Clone();  
};  
```  
  
 此版本要求在类中为正显式重写的接口成员赋予一个唯一名称。  在此，我提供了一个有些笨拙的 `InterfaceClone` 的名称。  行为仍然相同 — 通过 `ICloneable` 接口的调用将调用重新命名的 `InterfaceClone,`，而通过类型 `R` 的一个对象的调用将调用第二个 `Clone` 实例。  
  
## 请参阅  
 [类或接口中的成员声明 \(C\+\+\/CLI\)](../dotnet/member-declarations-within-a-class-or-interface-cpp-cli.md)   
 [显式重写](../windows/explicit-overrides-cpp-component-extensions.md)