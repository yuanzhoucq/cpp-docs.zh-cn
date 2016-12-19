---
title: "在 Visual C++ 的一般概述 | Microsoft Docs"
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
  - "构造类型"
  - "构造类型, 关闭 [C++]"
  - "构造类型, 打开 [C++]"
  - "默认初始值设定项 [C++]"
  - "普通 [C++], 关于泛型"
  - "打开构造类型 [C++]"
  - "键入参数 [C++]"
  - "键入参数 [C++]"
ms.assetid: 21f10637-0fce-4916-b925-6c86a126d3aa
caps.latest.revision: 21
caps.handback.revision: 21
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 在 Visual C++ 的一般概述
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

泛型是公共语言运行时所支持的类型参数化。  参数化类型是定义与未知的类型参数指定类型，则使用泛型。  
  
## 为什么泛型？  
 C\+\+ 支持模板、模板和泛型支持参数化类型创建类型化的集合类。  但是，该模板提供编译时进行参数化。  您不能引用包含模板所定义的程序集以及创建新模板的专用化。  编译之后，专用的模板看起来与其他任何类或方法。  相比之下，泛型在 MSIL 发出是在运行时已知的参数化类型是参数化类型；引用包含泛型类型的程序集的源代码可以创建泛型类型的专用化。  有关 Visual C\+\+ 模板和泛型比较的更多信息，请参见 [型和模板](../windows/generics-and-templates-visual-cpp.md)。  
  
## 泛型类型和成员  
 类类型，因此，只要它们是托管类型，可以为泛型。  此示例可能是 `List` 类。  一个对象的类型列表中的是类型参数。  如果需要对象的许多不同类型的 `List` 类，在泛型类型的项目，采用 **System::Object** 作为可能使用 `List` 之前。  但这允许任何对象 \(错误的类型包括对象\) 在列表。  此列表将称为"类型化集合类。  在最佳情况下，您可以检查的类型在运行时并引发异常。  或者，可能使用了模板，则将丢失其常规质量当编译到程序集中。  程序集的使用者不可能创建这些模板的专用化。  泛型使您得以创建类型化集合类，添加将生成编译时错误。`List<int>` \(读取为“int 列表”\) 以及 `List<double>` \(双重“列表”\)，如果您尝试将尚未设计接受集合到类型化的集合的类型。  此外，在编译后，这些类型仍然是泛型。  
  
 泛型类语法中显示的 [泛型类 \(C\+\+\/CLI\)](../windows/generic-classes-cpp-cli.md)一个新的`.` 命名空间，<xref:System.Collections.Generic>能找到，引入了一组被参数化的集合类型 \(包括 <xref:System.Collections.Generic.Dictionary%602>、<xref:System.Collections.Generic.List%601> 和 <xref:System.Collections.Generic.LinkedList%601>。  有关更多信息，请参见[.NET Framework 类库中的泛型](../Topic/Generics%20in%20the%20.NET%20Framework%20Class%20Library%20\(C%23%20Programming%20Guide\).md)。  
  
 实例和静态类成员函数，委托，并且全局函数也是泛型的。  泛型函数可能需要函数的参数是未知类型，或者函数是否必须具有泛型类型。  在许多情况下可以使用过去 **System::Object** 作为参数提供未知类型的对象位置，泛型类型参数可能为更类型安全的代码，使用。  任何尝试将在函数类型尚未设计将标记为编译时的错误。  使用 **System::Object** 作为函数参数，函数不打算处理不会检测的无意中将对象您将必须转换未知的对象类型的特定输入函数体，而考虑引发的可能性。  一般，尝试的代码传递给函数的对象会导致冲突类型，以便函数体确保正确的类型。  
  
 相同的优点应用于集合泛型生成的类。  集合类从前将使用 **System::Object** 存储集合中的元素。  类型对象的插入集合未被设计为在编译时未标记，并通常没有，即使对象插入。  通常，在处于集合中访问对象将转换为某其他类型。  在转换失败将检测意外类型。  泛型解决此问题在编译时将检测不符合类型插入的所有代码 \(或隐式转换\) 泛型集合的类型参数。  
  
 有关语法的说明，请参见 [泛型函数 \(C\+\+\/CLI\)](../windows/generic-functions-cpp-cli.md)。  
  
## 使用术语使用泛型  
  
##### 类型参数  
 一个泛型方法包含一个或多个未指定类型（称为*类型参数*）。  类型参数名称代表泛型声明主体中的类型。  类型参数名称代表泛型声明主体中的类型。  ListT 的通用声明\<\> 一个类型 T 参数。  
  
##### 类型参数  
 当一般为特定类型时，专用 *类型参数* 是用于替换类型参数的实际类型的位置使用。  例如，`int` 是 `List<int>`的类型参数。  值类型和句柄类型为泛型类型参数中允许使用的唯一类型。  
  
##### Constructed Type — 构造类型  
 从泛型类型构造的类型称为构造 *的类型*。  类型未完全指定，如 `List<T>` 为 *开放式构造类型*；类型完全指定，例如 `List<double>,` 为 *封闭式构造类型* 或 *专用类型*。  open 构造的类型可以被其他泛型类型或方法，并不能完全指定，直到封闭泛本身指定的定义。  例如，下面是对一打开构造类型的用作通用的基类：  
  
 `// generics_overview.cpp`  
  
 `// compile with: /clr /c`  
  
 `generic <typename T>`  
  
 `ref class List {};`  
  
 `generic <typename T>`  
  
 `ref class Queue : public List<T> {};`  
  
##### 约束  
 约束是在可以使用作为类型参数的类型的限制。  例如，特定常规类可能接受来自指定的类继承的类，或实现了指定接口。  有关详细信息，请参阅[约束](../windows/constraints-on-generic-type-parameters-cpp-cli.md)。  
  
## 值类型和引用类型  
 句柄类型和值类型能用作类型参数。  在泛型类型定义，要么可以使用语法，是引用类型。  例如，**\-\>** 运算符来访问类型参数的类型的成员。最后使用的类型是引用类型或值类型。  在值类型使用作为类型参数时，运行生成时使用值类型直接，而无须值类型装箱的代码。  
  
 在使用作为引用类型的泛型类型参数时，使用处理语法。  当使用值类型作为泛型类型参数时，将直接使用的类型名称。  
  
 `// generics_overview_2.cpp`  
  
 `// compile with: /clr`  
  
 `generic <typename T>`  
  
 `ref class GenericType {};`  
  
 `ref class ReferenceType {};`  
  
 `value struct ValueType {};`  
  
 `int main() {`  
  
 `GenericType<ReferenceType^> x;`  
  
 `GenericType<ValueType> y;`  
  
 `}`  
  
## 类型参数  
 在泛型类的参数类型像其他标识符。  但是，因为类型未知，在它们使用的限制。  例如，不能使用的成员，并且类型参数的类方法，除非已知类型参数支持这些成员。  即通过类型参数访问成员，必须添加包含成员为类型参数的约束列表的类型。  
  
 `// generics_overview_3.cpp`  
  
 `// compile with: /clr`  
  
```  
interface class I {  
   void f1();  
   void f2();  
};  
  
ref struct R : public I {  
   virtual void f1() {}  
   virtual void f2() {}   
   virtual void f3() {}   
};  
  
generic <typename T>  
where T : I  
void f(T t) {  
   t->f1();  
   t->f2();  
   safe_cast<R^>(t)->f3();  
}  
  
int main() {  
   f(gcnew R());  
}  
```  
  
 这些限制运算符。  当类型不支持这些运算符，一个不受约束的泛型类型参数不能使用类型参数 `==` 和 `!=` 运算符比较的两个实例。  这些检查是必需的为泛型，不适用于模板，因为泛型可以在专用具有足够约束的任何类的，在运行时，就来不及检查用于 void 的成员时。  
  
 通过使用 `()` 运算符，键入参数的默认实例的创建。  例如：  
  
 `T t = T();`  
  
 其中 `T` 是在一个泛型类或方法定义的类型参数，变量初始化为其默认值。  如果 `T` 为与 ref 类将是 null 指针；如果 `T` 是值类对象，初始化为零。  这称为 *默认*初始值。  
  
## 请参阅  
 [泛型](../windows/generics-cpp-component-extensions.md)