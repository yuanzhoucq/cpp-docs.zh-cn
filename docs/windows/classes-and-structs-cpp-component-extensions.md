---
title: 类和结构 （c + + 组件扩展） |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- ref class keyword [C++]
- value class keyword [C++]
- value struct keyword [C++]
- ref struct keyword [C++]
ms.assetid: 5c360764-b229-49c6-9357-66213afbc372
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 33fba76d39811b0fed777f057c5936a29f8c8a1a
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/22/2018
ms.locfileid: "42595088"
---
# <a name="classes-and-structs--c-component-extensions"></a>类和结构（C++ 组件扩展）

声明类或结构的*对象生存期*自动进行管理。 当对象不再可访问或超出范围时，Visual C++ 会自动放弃分配给对象的内存。

## <a name="all-runtimes"></a>所有运行时

### <a name="syntax"></a>语法

```cpp
      class_access
      ref class
      name
      modifier :  inherit_accessbase_type {};
class_accessref structnamemodifier :  inherit_accessbase_type {};
class_accessvalue classnamemodifier :  inherit_accessbase_type {};
class_accessvalue structnamemodifier :  inherit_accessbase_type {};

```

### <a name="parameters"></a>参数

*class_access* （可选）  
程序集外部的类或结构的可访问性。 可能的值为**公共**并**专用**(**专用**是默认值)。 嵌套的类或结构不能有*class_access*说明符。

*name*  
类或结构的名称。

*修饰符*（可选）  
[抽象](../windows/abstract-cpp-component-extensions.md)并[密封](../windows/sealed-cpp-component-extensions.md)是有效修饰符。

*inherit_access* （可选）  
可访问性*base_type*。 仅允许可访问性是**公共**(**公共**是默认值)。

*base_type* （可选）  
基类型。 但是，值类型不能充当基类型。

有关详细信息，请参阅中的 Windows 运行时和通用语言 Runtimesections 此参数的特定于语言的说明。

### <a name="remarks"></a>备注

使用声明的对象的默认成员可访问性**ref 类**或**值类**是**专用**。 和使用的默认成员可访问性对象的声明**ref 结构**或**值结构**是**公共**。

如果引用类型继承自另一个引用类型，必须显式重写基类中的虚函数 (与[重写](../windows/override-cpp-component-extensions.md)) 或隐藏 (使用[新 (新 vtable 中的槽）](../windows/new-new-slot-in-vtable-cpp-component-extensions.md))。 此外必须将派生的类函数显式标记为**虚拟**。

若要在编译时类型是否为检测**ref 类**或**ref 结构**，或**值类**或者**值结构**，使用`__is_ref_class (type)`，`__is_value_class (type)`，或`__is_simple_value_class (type)`。 有关详细信息，请参阅[编译器支持类型特征](../windows/compiler-support-for-type-traits-cpp-component-extensions.md)。

有关类和结构的详细信息，请参阅

- [实例化类和结构](../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md)

- [参考类型的 C++ 堆栈语义](../dotnet/cpp-stack-semantics-for-reference-types.md)

- [类、 结构和联合](../cpp/classes-and-structs-cpp.md)

- [析构函数和终结器中如何： 定义和使用类和结构 (C + + CLI)](../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Destructors_and_finalizers)

- [用户定义的运算符 (C++/CLI)](../dotnet/user-defined-operators-cpp-cli.md)

- [用户定义的转换 (C++/CLI)](../dotnet/user-defined-conversions-cpp-cli.md)

- [如何：包装本机类以供 C# 使用](../dotnet/how-to-wrap-native-class-for-use-by-csharp.md)

- [泛型类 (C++/CLI)](../windows/generic-classes-cpp-cli.md)

## <a name="windows-runtime"></a>Windows 运行时

### <a name="remarks"></a>备注

请参阅[Ref 类和结构](../cppcx/ref-classes-and-structs-c-cx.md)并[值类和结构](http://msdn.microsoft.com/library/windows/apps/hh699861.aspx)。

### <a name="parameters"></a>参数

*base_type* （可选）  
基类型。 一个**ref 类**或**ref 结构**可以继承自零个或多个接口以及零个或一个**ref**类型。 一个**值类**或**值结构**只能继承自零个或多个接口。

当使用声明对象**ref 类**或**ref 结构**关键字，该对象被访问的对象的句柄; 即，指向对象的引用计数器指针。 声明的变量超出范围时，编译器会自动删除基础对象。 当对象在调用中用作参数或存储在变量中时，实际是在传递或存储该对象的句柄。

当使用声明对象**值类**或**值结构**关键字，不会监督声明的对象的对象生存期。 该对象如同任何其他标准 C++ 类或结构一样。

### <a name="requirements"></a>要求

编译器选项：`/ZW`

## <a name="common-language-runtime"></a>公共语言运行时

### <a name="remarks"></a>备注

下表列出了与中所示的语法差异**所有运行时**部分特定于 C + + /cli CLI。

### <a name="parameters"></a>参数

*base_type* （可选）  
基类型。 一个**ref 类**或**ref 结构**可以继承自零个或多个托管接口以及零个或一个 ref 类型。 一个**值类**或**值结构**只能继承自零个或多个托管接口。

**Ref 类**并**ref 结构**关键字会告知编译器的类或结构是在堆上分配。 当对象在调用中用作参数或存储在变量中时，实际是在传递或存储该对象的引用。

**值类**并**值结构**关键字告知编译器的已分配的类或结构的值是传递给函数或存储在成员。

### <a name="requirements"></a>要求

编译器选项：`/clr`

## <a name="see-also"></a>请参阅

[适用于运行时平台的组件扩展](../windows/component-extensions-for-runtime-platforms.md)