---
title: "类和结构 (托管) | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "public"
  - "ref struct"
  - "value_CPP"
  - "ref class"
  - "value struct"
  - "ref struct_cpp"
  - "ref class_cpp"
  - "value class_cpp"
  - "value struct_cpp"
  - "value class"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ref 类关键字 [C++]"
  - "ref 结构关键字 [C++]"
  - "值 class 关键字 [C++]"
  - "值结构关键字 [C++]"
ms.assetid: 5c360764-b229-49c6-9357-66213afbc372
caps.latest.revision: 32
caps.handback.revision: 32
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 类和结构 (托管)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

声明其对象生存期自动进行管理的类或结构。  当对象不再可访问或超出范围时，Visual C\+\+ 会自动放弃分配给对象的内存。  
  
## 所有运行时  
 **语法**  
  
```  
  
          class_access ref class    name modifier :  inherit_access base_type {};  
class_access ref struct   name modifier :  inherit_access base_type {};  
class_access value class  name modifier :  inherit_access base_type {};  
class_access value struct name modifier :  inherit_access base_type {};  
  
```  
  
 **参数**  
  
 *class\_access*（可选）  
 程序集外部的类或结构的可访问性。  可能值是 **public** 和 `private`（`private` 是默认值）。  嵌套类或结构不能具有 *class\_access* 说明符。  
  
 *name*  
 类或结构的名称。  
  
 *modifier*（可选）  
 [abstract](../windows/abstract-cpp-component-extensions.md) 和 [sealed](../windows/sealed-cpp-component-extensions.md) 是有效修饰符。  
  
 *inherit\_access*（可选）  
 `base_type` 的可访问性。  唯一允许的可访问性是 `public`（`public` 是默认值）。  
  
 *base\_type*（可选）  
 基类型。  但是，值类型不能充当基类型。  
  
 有过详细信息，请参阅 [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)] 和 [!INCLUDE[clr_for_headings](../dotnet/includes/clr_for_headings_md.md)] 部分中此参数的特定于语言的描述。  
  
 **备注**  
  
 使用 **ref class** 或 **value class** 声明的对象的默认成员可访问性是 `private`。  而使用 **ref struct** 或 **value struct** 声明的对象的默认成员可访问性是 `public`。  
  
 当某种引用类型继承自其他引用类型时，基类中的虚函数必须显式重写（使用 [override](../windows/override-cpp-component-extensions.md)）或隐藏（使用 [新的 \(在 vtable 的新槽\)](../windows/new-new-slot-in-vtable-cpp-component-extensions.md)）。  派生类函数还必须显式标记为 `virtual`。  
  
 若要在编译时检测类型是 `ref class` 还是 `ref struct`，或是 `value class` 还是 `value struct`，请使用 `__is_ref_class (``type``)`、`__is_value_class (``type``)` 或  `__is_simple_value_class (``type``)`。  有关详细信息，请参阅[编译器使用类型特征支持](../windows/compiler-support-for-type-traits-cpp-component-extensions.md)。  
  
 有关类和结构的详细信息，请参阅  
  
-   [实例化类和结构](../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md)  
  
-   [此指针在值和引用类型中的语义](../misc/semantics-of-the-this-pointer-in-value-and-reference-types.md)  
  
-   [参考类型的 C\+\+ 堆栈语义](../dotnet/cpp-stack-semantics-for-reference-types.md)  
  
-   [类、结构和联合](../cpp/classes-and-structs-cpp.md)  
  
-   [本机类上的公共和私有](../misc/how-to-declare-public-and-private-on-native-classes.md)  
  
-   [隐式抽象类](../misc/implicitly-abstract-classes.md)  
  
-   [在类或结构中定义静态构造函数](../misc/how-to-define-static-constructors-in-a-class-or-struct.md)  
  
-   [未能生成复制构造函数](../misc/copy-constructor-may-not-be-generated.md)  
  
-   [引用类型中的按签名隐藏函数](../misc/hide-by-signature-functions-in-reference-types.md)  
  
-   [Visual C\+\+ 中的析构函数和终结器](../misc/destructors-and-finalizers-in-visual-cpp.md)  
  
-   [类型和成员可见性](../misc/type-and-member-visibility.md)  
  
-   [用户定义的运算符](../dotnet/user-defined-operators-cpp-cli.md)  
  
-   [用户定义的转换](../dotnet/user-defined-conversions-cpp-cli.md)  
  
-   [如何：包装本机类以供 C\# 使用](../dotnet/how-to-wrap-native-class-for-use-by-csharp.md)  
  
-   [泛型类 \(C\+\+\/CLI\)](../windows/generic-classes-cpp-cli.md)  
  
## [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)]  
 **备注**  
  
 请参阅 [Ref 类和结构](http://msdn.microsoft.com/library/windows/apps/hh699870.aspx)和 [Value 类和结构](http://msdn.microsoft.com/library/windows/apps/hh699861.aspx)。  
  
 **参数**  
  
 *base\_type*（可选）  
 基类型。  `ref class` 或 `ref struct` 可以继承自零个或多个接口以及零种或一种 `ref` 类型。  `value class` 或 `value struct` 只能继承自零个或多个接口。  
  
 使用 `ref class` 或 `ref struct` 关键字声明对象时，对象通过对象句柄进行访问；即，指向对象的引用计数器指针。  声明的变量超出范围时，编译器会自动删除基础对象。  当对象在调用中用作参数或存储在变量中时，实际是在传递或存储该对象的句柄。  
  
 使用 `value class` 或 `value struct` 关键字声明对象时，不会监督声明的对象的对象生存期。  该对象如同任何其他标准 C\+\+ 类或结构一样。  
  
### 要求  
 编译器选项：**\/ZW**  
  
## [!INCLUDE[clr_for_headings](../dotnet/includes/clr_for_headings_md.md)]  
 **备注**  
  
 下表列出与**所有运行时**部分中显示的语法之间的特定于 C\+\+\/CLI 的差异。  
  
 **参数**  
  
 *base\_type*（可选）  
 基类型。  `ref class` 或 `ref struct` 可以继承自零个或多个托管接口以及零种或一种 ref 类型。  `value class` 或 `value struct` 只能继承自零个或多个托管接口。  
  
 `ref class` 和 `ref struct` 关键字会告知编译器要在堆上分配类或结构。  当对象在调用中用作参数或存储在变量中时，实际是在传递或存储该对象的引用。  
  
 `value class` 和 `value struct` 关键字通知编译器，已分配类或结构的值已传递给函数或存储在成员中。  
  
### 要求  
 编译器选项：**\/clr**  
  
## 请参阅  
 [适用于运行时平台的组件扩展](../windows/component-extensions-for-runtime-platforms.md)