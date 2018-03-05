---
title: "托管的类类型的声明 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- __gc types
- classes [C++], managed
- class keyword [C++], CLR
- __value keyword
- value types, declaring
- value keyword [C++]
- managed classes
- interface class keyword
- ref keyword [C++]
ms.assetid: 16de9c94-91d7-492f-8ac7-f0729cc627e9
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: c9e9aba6d2a0485a94385be5b8712d7552261ff1
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="declaration-of-a-managed-class-type"></a>托管类类型的声明
声明托管扩展中更改 c + + 为 Visual c + + 引用类类型的方法。  
  
 在托管扩展中，引用类类型开头为`__gc`关键字。 在新语法中，`__gc`关键字替换为两个空格分隔关键字之一：`ref class`或`ref struct`。 所选的`struct`或`class`指示公共 (有关`struct`) 或私有 (有关`class`) 类型的代码体的初始未标记节中声明其成员的默认访问级别。  
  
 同样，在托管扩展中，值类类型开头为`__value`关键字。 在新语法中，`__value`关键字替换为两个空格分隔关键字之一：`value class`或`value struct`。  
  
 接口类型，在托管扩展中，但使用关键字指定`__interface`。 在新语法中，这将替换`interface class`。  
  
 例如，以下类声明在托管扩展中：  
  
```  
public __gc class Block {};     // reference class  
public __value class Vector {}; // value class  
public __interface IFooBar {};  // interface class  
```  
  
 在新语法中的等效声明，如下所示：  
  
```  
public ref class Block {};         // reference class  
public value class Vector {};      // value class  
public interface class IFooBar {}; // interface class  
```  
  
## <a name="specifying-the-class-as-abstract"></a>指定为抽象类  
 在托管扩展中，你可以放置关键字`__abstract`之前`class`关键字 (之前或之后`__gc`) 以指示该类是不完整，且不能在程序中创建类的对象：  
  
```  
public __gc __abstract class Shape {};  
public __gc __abstract class Shape2D: public Shape {};  
```  
  
 在新语法中，你指定`abstract`以下类名，并且类主体、 基类派生列表中或分号之前的上下文关键字。  
  
```  
public ref class Shape abstract {};  
public ref class Shape2D abstract : public Shape{};  
```  
  
 当然，语义含义不会改变。  
  
## <a name="specifying-the-class-as-sealed"></a>指定类为密封类  
 在托管扩展中，你可以放置关键字`__sealed`之前`class`关键字 (之前或之后`__gc`) 以指示，不能从继承类的对象：  
  
```  
public __gc __sealed class String {};  
```  
  
 在新语法中，你指定`sealed`以下类名，并且类主体、 基类派生列表中或分号之前的上下文关键字。  
  
 可以派生一个类和密封它。 例如，`String`类隐式派生自`Object`。 密封类的好处是它支持的静态分辨率 (即，在编译时) 的所有虚函数调用通过密封的引用类对象。 这是因为`sealed`说明符可保证`String`跟踪句柄不能随后派生类可能会提供正在调用的虚拟方法重写实例的引用。 下面是新语法中的密封类的一个示例：  
  
```  
public ref class String sealed {};  
```  
  
 一个还可以指定一个类这两个抽象和密封-这是一个指示静态类的特殊情况。 这是文档中所述 CLR，如下所示：  
  
 "的类型，它是同时`abstract`和`sealed`应具有仅静态成员，并用作什么某些语言中调用一个命名空间。"  
  
 例如，下面是使用托管扩展语法抽象密封类的声明：  
  
```  
public __gc __sealed __abstract class State {  
public:  
   static State() {}  
   static bool inParamList();  
  
private:  
   static bool ms_inParam;  
};  
```  
  
 而以下是此声明转换为新的语法：  
  
```  
public ref class State abstract sealed {  
public:  
   static State();  
   static bool inParamList();  
  
private:  
   static bool ms_inParam;  
};  
```  
  
## <a name="clr-inheritance-specifying-the-base-class"></a>CLR 继承： 指定的基类  
 在 CLR 对象模式下支持仅公共单一继承。 但是，托管扩展保留而无需访问关键字作为指定私有派生的基类的 ISO c + + 默认解释。 这意味着，每个 CLR 继承声明必须提供`public`关键字来重写的默认解释。  
  
```  
// Managed Extensions: error: defaults to private derivation  
__gc class Derived : Base {};  
```  
  
 在新的语法定义中，没有访问关键字指示 CLR 继承定义中的公共派生。 因此，`public`访问关键字现在是可选的。 尽管这不要求 c + + 代码的托管扩展的任何修改，我将列出出于完整性考虑此更改。  
  
```  
// New syntax: ok: defaults to public derivation  
ref class Derived : Base{};  
```  
  
## <a name="see-also"></a>请参阅  
 [托管类型 (C + + /cli CL)](../dotnet/managed-types-cpp-cl.md)   
 [类和结构](../windows/classes-and-structs-cpp-component-extensions.md)   
 [abstract](../windows/abstract-cpp-component-extensions.md)   
 [sealed](../windows/sealed-cpp-component-extensions.md)