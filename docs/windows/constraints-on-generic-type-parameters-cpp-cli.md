---
title: "约束 | Microsoft Docs"
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
  - "where"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "约束, C++"
  - "如果关键字 [C++]"
ms.assetid: eb828cc9-684f-48a3-a898-b327700c0a63
caps.latest.revision: 25
caps.handback.revision: 23
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 约束
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

在泛型类型或方法声明，则可以限定使用约束的类型参数。  约束是类型的需要，则类型参数必须符合。  例如，绑定可能是类型参数必须实现某接口或从特定类继承。  
  
 约束是可选的；不指定约束。参数与该约束参数等效于 <xref:System.Object>。  
  
## 语法  
  
```  
  
where type-parameter: constraint list  
```  
  
#### 参数  
 类型参数。  
 一个参数，将类型约束。  
  
 *constraint list*  
 *约束列表* 为约束指定一个逗号分隔列表。  列表可以包含连接由类型参数实现。  
  
 列表也可以包含类。  对于参数满足类型的基类约束，它必须是相同的约束或从约束派生。  
  
 还可以指定 `gcnew()` 将参数类型必须具有公共的无参数构造函数；或者指示类型参数的 `ref class` 必须是引用类型 \(包括，任何类、接口、委托或数组类型；或者指示类型参数的 `value class` 必须是值类型。  可以指定除 \<\> 以外的任何值类型。  
  
 还可以指定作为泛型形参约束。  对于约束的类型参数提供的类型必须是或从约束的类型派生。  这称为裸类型约束。  
  
## 备注  
 约束子句包括类型参数、冒号\(**:**\)和紧跟的 **位置** 类型参数约束，在指定限制的性质。  [上下文相关的关键字](../windows/context-sensitive-keywords-cpp-component-extensions.md)。  处理空间的多个 **位置** 子句。  
  
 约束应用于类型参数可用作参数。泛型类型或方法的类型的位置限制。  
  
 类和接口约束指定参数必须是类型或从指定的类继承或实现了指定接口。  
  
 约束应用于泛型类型或方法的允许该类型或方法的约束的类型已知代码利用的功能。  例如，可以声明一个泛型类 **\<\>，这样，类型参数**  就可以实现接口：  
  
```  
// generics_constraints_1.cpp  
// compile with: /c /clr  
using namespace System;  
generic <typename T>  
where T : IComparable<T>  
ref class List {};  
```  
  
 此约束要求用于 `T` 类型参数实现 `IComparable<T>` 在编译时。  它还允许接口方法，例如 **CompareTo**调用。  平移是需要上类型参数的实例调用接口方法。  
  
 在类型参数的类的静态方法不能通过类型参数调用方法，它们可通过命名实际类型调用。  
  
 约束不能是一种值类型，包括内置类型 \(如 `int` 或 **双倍行距**。  由于值类型不能有派生类，因此，只有一类可以满足约束。  在这种情况下，重写具有特定值替换泛型类型的类型参数。  
  
 在某些情况下需要约束，因为编译器不允许使用方法或一种未知类型的其他功能，除非约束表示未知类型的支持方法或接口。  
  
 同一类型形参的多个约束在逗号分隔列表中指定  
  
```  
// generics_constraints_2.cpp  
// compile with: /c /clr  
using namespace System;  
using namespace System::Collections::Generic;  
generic <typename T>  
where T : List<T>, IComparable<T>  
ref class List {};  
```  
  
 对于多个类型参数，每个类型参数都使用一个 **位置** 子句。  例如：  
  
```  
// generics_constraints_3.cpp  
// compile with: /c /clr  
using namespace System;  
using namespace System::Collections::Generic;  
  
generic <typename K, typename V>  
   where K: IComparable<K>  
   where V: IComparable<K>  
ref class Dictionary {};  
```  
  
 摘要，请使用约束在代码根据下列规则：  
  
-   如果列出多个约束，约束以任何顺序可以列出。  
  
-   约束也可以是类类型，例如抽象基类。  但是，受约束不可为值类型或封装的类。  
  
-   约束自身不能是类型参数，但它们在打开构造类型涉及类型参数。  例如：  
  
    ```  
    // generics_constraints_4.cpp  
    // compile with: /c /clr  
    generic <typename T>  
    ref class G1 {};  
  
    generic <typename Type1, typename Type2>  
    where Type1 : G1<Type2>   // OK, G1 takes one type parameter  
    ref class G2{};  
    ```  
  
## 示例  
 下面的示例演示对类型参数的实例方法演示如何使用绑定。  
  
```  
// generics_constraints_5.cpp  
// compile with: /clr  
using namespace System;  
  
interface class IAge {  
   int Age();  
};  
  
ref class MyClass {  
public:  
   generic <class ItemType> where ItemType : IAge   
   bool isSenior(ItemType item) {  
      // Because of the constraint,  
      // the Age method can be called on ItemType.  
      if (item->Age() >= 65)   
         return true;  
      else  
         return false;  
   }  
};  
  
ref class Senior : IAge {  
public:  
   virtual int Age() {  
      return 70;  
   }  
};  
  
ref class Adult: IAge {  
public:  
   virtual int Age() {  
      return 30;  
   }  
};  
  
int main() {  
   MyClass^ ageGuess = gcnew MyClass();  
   Adult^ parent = gcnew Adult();  
   Senior^ grandfather = gcnew Senior();  
  
   if (ageGuess->isSenior<Adult^>(parent))  
      Console::WriteLine("\"parent\" is a senior");  
   else  
      Console::WriteLine("\"parent\" is not a senior");  
  
   if (ageGuess->isSenior<Senior^>(grandfather))  
      Console::WriteLine("\"grandfather\" is a senior");  
   else  
      Console::WriteLine("\"grandfather\" is not a senior");  
}  
```  
  
  **“父”不是前辈**  
**“祖父”是前辈**   
## 示例  
 当泛型类型参数用作约束时，将调用一 naked 类型约束。  在使用自己的类型参数的成员约束需要函数参数。包含的类型参数时，会使用类型约束 naked 很有用。  
  
 在下面的示例中，的类型 T 为裸绑定上下文添加方法中。  
  
 类型参数还可在泛型类定义中用作约束。  泛型类的类型参数约束的作用非常有限，因为编译器除了假设类型参数派生自 <xref:System.Object> 以外，不会做其他任何假设。  在希望强制两个类型参数之间的继承关系的情况下，可对泛型类使用参数类型约束。  
  
```  
// generics_constraints_6.cpp  
// compile with: /clr /c  
generic <class T>  
ref struct List {  
   generic <class U>  
   where U : T  
   void Add(List<U> items)  {}  
};  
  
generic <class A, class B, class C>  
where A : C  
ref struct SampleClass {};  
```  
  
## 请参阅  
 [泛型](../windows/generics-cpp-component-extensions.md)