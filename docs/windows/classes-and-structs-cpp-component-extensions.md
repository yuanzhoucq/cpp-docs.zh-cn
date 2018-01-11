---
title: "类和结构 （c + + 组件扩展） |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: C++
helpviewer_keywords:
- ref class keyword [C++]
- value class keyword [C++]
- value struct keyword [C++]
- ref struct keyword [C++]
ms.assetid: 5c360764-b229-49c6-9357-66213afbc372
caps.latest.revision: "32"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 8d75bc7f0935ef7444d37f3708379598a549417e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="classes-and-structs--c-component-extensions"></a>类和结构（C++ 组件扩展）
声明类或结构其*对象生存期*自动进行管理。 当对象不再可访问或超出范围时，Visual C++ 会自动放弃分配给对象的内存。  
  
## <a name="all-runtimes"></a>所有运行时  
 **语法**  
  
```  
  
      class_access  
      ref class  
      name  
      modifier :  inherit_accessbase_type {};  
class_accessref structnamemodifier :  inherit_accessbase_type {};  
class_accessvalue classnamemodifier :  inherit_accessbase_type {};  
class_accessvalue structnamemodifier :  inherit_accessbase_type {};  
  
```  
  
 **参数**  
  
 *class_access* （可选）  
 程序集外部的类或结构的可访问性。 可能的值为**公共**和`private`(`private`是默认设置)。 嵌套的类或结构不能具有*class_access*说明符。  
  
 *name*  
 类或结构的名称。  
  
 *修饰符*（可选）  
 [抽象](../windows/abstract-cpp-component-extensions.md)和[密封](../windows/sealed-cpp-component-extensions.md)是有效修饰符。  
  
 *inherit_access* （可选）  
 `base_type` 的可访问性。 唯一允许的可访问性是 `public`（`public` 是默认值）。  
  
 *base_type* （可选）  
 基类型。 但是，值类型不能充当基类型。  
  
 有关详细信息，请参阅中的 Windows 运行时和公共语言 Runtimesections 此参数的特定于语言的说明。  
  
 **备注**  
  
 使用声明的对象的默认成员可访问性**ref 类**或**值类**是`private`。 和使用的默认成员可访问性对象的声明**ref 结构**或**值结构**是`public`。  
  
 当引用类型继承自另一个引用类型时，基类中的虚函数显式必须重写。 (与[重写](../windows/override-cpp-component-extensions.md)) 或隐藏 (使用[新 (新 vtable 中的槽）](../windows/new-new-slot-in-vtable-cpp-component-extensions.md))。 派生类函数还必须显式标记为 `virtual`。  
  
 若要在编译时检测类型是否是类型`ref class`或`ref struct`，或`value class`或`value struct`，使用`__is_ref_class (type)`， `__is_value_class (type)`，或`__is_simple_value_class (type)`。 有关详细信息，请参阅[编译器支持类型特征](../windows/compiler-support-for-type-traits-cpp-component-extensions.md)。  
  
 有关类和结构的详细信息，请参阅  
  
-   [实例化类和结构](../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md)  
  
 
  
-   [参考类型的 C++ 堆栈语义](../dotnet/cpp-stack-semantics-for-reference-types.md)  
  
-   [类、 结构和联合](../cpp/classes-and-structs-cpp.md)  
  
-   [析构函数和终结器中如何： 定义和使用类和结构 (C + + /cli CLI)](../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Destructors_and_finalizers)  
  
-   [用户定义的运算符 (C++/CLI)](../dotnet/user-defined-operators-cpp-cli.md)  
  
-   [用户定义的转换 (C++/CLI)](../dotnet/user-defined-conversions-cpp-cli.md)  
  
-   [如何：包装本机类以供 C# 使用](../dotnet/how-to-wrap-native-class-for-use-by-csharp.md)  
  
-   [泛型类 (C++/CLI)](../windows/generic-classes-cpp-cli.md)  
  
## <a name="windows-runtime"></a>Windows 运行时  
 **备注**  
  
 请参阅[Ref 类和结构](http://msdn.microsoft.com/library/windows/apps/hh699870.aspx)和[值类和结构](http://msdn.microsoft.com/library/windows/apps/hh699861.aspx)。  
  
 **参数**  
  
 *base_type* （可选）  
 基类型。 `ref class` 或 `ref struct` 可以继承自零个或多个接口以及零种或一种 `ref` 类型。 `value class` 或 `value struct` 只能继承自零个或多个接口。  
  
 使用 `ref class` 或 `ref struct` 关键字声明对象时，对象通过对象句柄进行访问；即，指向对象的引用计数器指针。 声明的变量超出范围时，编译器会自动删除基础对象。 当对象在调用中用作参数或存储在变量中时，实际是在传递或存储该对象的句柄。  
  
 使用 `value class` 或 `value struct` 关键字声明对象时，不会监督声明的对象的对象生存期。 该对象如同任何其他标准 C++ 类或结构一样。  
  
### <a name="requirements"></a>惠?  
 编译器选项： **/ZW**  
  
## <a name="common-language-runtime"></a>公共语言运行时 
 **备注**  
  
 下表列出了与所示的语法差异**所有运行时**部分特定于 C + + /cli CLI。  
  
 **参数**  
  
 *base_type* （可选）  
 基类型。 `ref class` 或 `ref struct` 可以继承自零个或多个托管接口以及零种或一种 ref 类型。 `value class` 或 `value struct` 只能继承自零个或多个托管接口。  
  
 `ref class` 和 `ref struct` 关键字会告知编译器要在堆上分配类或结构。 当对象在调用中用作参数或存储在变量中时，实际是在传递或存储该对象的引用。  
  
 `value class`和`value struct`关键字告知编译器的已分配的类或结构的值是传递给函数或存储在成员。  
  
### <a name="requirements"></a>惠?  
 编译器选项： **/clr**  
  
## <a name="see-also"></a>请参阅  
 [适用于运行时平台的组件扩展](../windows/component-extensions-for-runtime-platforms.md)