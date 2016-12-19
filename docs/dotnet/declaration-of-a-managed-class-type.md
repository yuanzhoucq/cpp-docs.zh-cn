---
title: "托管类类型的声明 | Microsoft Docs"
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
  - "__gc 类型"
  - "__value 关键字"
  - "class 关键字 [C++], CLR"
  - "类 [C++], 托管"
  - "interface class 关键字"
  - "托管类"
  - "ref 关键字 [C++]"
  - "value 关键字 [C++]"
  - "值类型, 声明"
ms.assetid: 16de9c94-91d7-492f-8ac7-f0729cc627e9
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 托管类类型的声明
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

从 C\+\+ 托管扩展到 [!INCLUDE[cpp_current_long](../Token/cpp_current_long_md.md)]，声明引用类类型的方式已更改。  
  
 在托管扩展中，引用类类型以 `__gc` 关键字开头。  在新语法中，`__gc` 关键字由两个带空格的关键字之一取代：`ref class` 或 `ref struct`。  选择 `struct` 或 `class` 表示在类型主体的初始未标记部分中声明的其成员的默认访问级别是公共的（对于 `struct`）还是私有的（对于 `class`）。  
  
 同样，在托管扩展中，值类类型以 `__value` 关键字开头。  在新语法中，`__value` 关键字由两个带空格的关键字之一取代：`value class` 或 `value struct`。  
  
 在托管扩展中，接口类型由关键字 `__interface` 指出。  在新语法中，它由 `interface class` 取代。  
  
 例如，以下是托管扩展中的类声明：  
  
```  
public __gc class Block {};     // reference class  
public __value class Vector {}; // value class  
public __interface IFooBar {};  // interface class  
```  
  
 其使用新语法的等效声明如下所示：  
  
```  
public ref class Block {};         // reference class  
public value class Vector {};      // value class  
public interface class IFooBar {}; // interface class  
```  
  
## 指定类为抽象类  
 在托管扩展中，您将关键字 `__abstract` 放在 `class` 关键字的前面（在 `__gc` 之前或之后），以指示该类是不完整的并且无法在程序中创建该类的对象：  
  
```  
public __gc __abstract class Shape {};  
public __gc __abstract class Shape2D: public Shape {};  
```  
  
 在新语法中，指定 `abstract` 上下文关键字在类名之后，并且在类主体、基类派生列表或分号之前。  
  
```  
public ref class Shape abstract {};  
public ref class Shape2D abstract : public Shape{};  
```  
  
 当然，语义的含义没有更改。  
  
## 指定类为密封类  
 在托管扩展中，您将关键字 `__sealed` 放在 `class` 关键字的前面（在 `__gc` 之前或之后），以指示该类的对象无法从其他位置继承：  
  
```  
public __gc __sealed class String {};  
```  
  
 在新语法中，指定 `sealed` 上下文关键字在类名之后，并且在类主体、基类派生列表或分号之前。  
  
 您可以既派生类又密封类。  例如，`String` 类是从 `Object` 隐式派生的。  密封类的好处是：它支持静态解析（即在编译时）通过密封的引用类对象的所有虚函数调用。  这是因为 `sealed` 说明符保证 `String` 跟踪句柄不能引用随后的派生类，该派生类可能提供正被调用的虚方法的一个重写实例。  下面是一个用新语法表示的密封类的示例：  
  
```  
public ref class String sealed {};  
```  
  
 还可以指定类既为抽象类又为密封类 — 这是指示静态类的一个特殊情况。  它在 CLR 文档中进行了描述，如下所示：  
  
 “既是 `abstract` 又是 `sealed` 的类型应仅有静态成员，并且它起到其他语言中称为命名空间的作用。”  
  
 例如，以下是使用托管扩展语法的抽象密封类的声明：  
  
```  
public __gc __sealed __abstract class State {  
public:  
   static State() {}  
   static bool inParamList();  
  
private:  
   static bool ms_inParam;  
};  
```  
  
 而以下是转为使用新语法的此声明：  
  
```  
public ref class State abstract sealed {  
public:  
   static State();  
   static bool inParamList();  
  
private:  
   static bool ms_inParam;  
};  
```  
  
## CLR 继承：指定基类  
 在 CLR 对象模型下，仅支持公共单一继承。  但是，托管扩展保留了在指定私有派生时不使用访问关键字的基类的 ISO\-C\+\+ 默认解释。  这意味着每个 CLR 继承声明为了重写默认解释而必须提供 `public` 关键字。  
  
```  
// Managed Extensions: error: defaults to private derivation  
__gc class Derived : Base {};  
```  
  
 在新语法定义中，缺少访问关键字表示 CLR 继承定义中存在公共派生。  因此，`public` 访问关键字现在为可选。  尽管这不需要对 C\+\+ 托管扩展代码进行任何修改，但出于完整性的考虑，我还是在这里列出了此更改。  
  
```  
// New syntax: ok: defaults to public derivation  
ref class Derived : Base{};  
```  
  
## 请参阅  
 [托管类型 \(C\+\+\/CL\)](../dotnet/managed-types-cpp-cl.md)   
 [类和结构 \(托管\)](../windows/classes-and-structs-cpp-component-extensions.md)   
 [abstract](../windows/abstract-cpp-component-extensions.md)   
 [sealed](../windows/sealed-cpp-component-extensions.md)