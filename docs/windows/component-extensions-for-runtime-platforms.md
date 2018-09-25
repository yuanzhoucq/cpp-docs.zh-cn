---
title: 运行时平台的组件扩展 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- what's new [C++], keywords
- what's new [C++], language features
- C++, keywords
- keywords [C++]
- Managed Extensions for C++, replacement syntax
ms.assetid: 1e400ee6-3ac9-4910-a608-9d3d5993e423
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 0619585a0a5b59ffb6b8cfbe22e7930909369b23
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46386743"
---
# <a name="component-extensions-for-runtime-platforms"></a>适用于运行时平台的组件扩展

Visual C++ 提供多种语言扩展，可帮助你面向运行时平台编程。 通过使用 C + + /CX 中，您可以编写通用 Windows 平台应用程序和编译为本机代码的组件。 虽然可以通过对 Windows 运行时 COM 接口直接编程创建通用 Windows 平台应用，通过使用 C + + /CX 中，您可以使用构造函数、 异常和其他现代 c + + 编程惯例。 若要启用.NET 平台上的托管的执行环境中的 c + + 编程，可使用 C + + /cli CLI。

### <a name="two-runtimes-one-set-of-extensions"></a>两个运行时，一组扩展

C + + /cli CX 是子集 C + + /cli CLI。 扩展插件所共有的 C + + /CX 和 C + + /cli CLI，其语义取决您面向的公共语言运行时 (CLR) 或 Windows 运行时。 若要编译您的应用程序在 Windows 运行时上运行，请指定`/ZW`编译器选项。 要将其编译为在 CLR 上运行，请指定 `/clr` 编译器选项。 当使用 Visual Studio 创建项目时，将自动设置这些开关。

有关如何在 c + + 中创建通用 Windows 平台应用的详细信息，请参阅[路线图的 Windows 运行时应用使用 c + +](https://msdn.microsoft.com/library/windows/apps/hh700360.aspx)。

C + + /cli CLI 扩展了 ISO/ANSI c + + 标准，并且定义在 Ecma C + + /cli 标准 CLI。 有关详细信息，请参阅[.NET 编程使用 C + + /cli （Visual c + +）](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)。

## <a name="data-type-keywords"></a>数据类型关键字

语言扩展包括*聚合关键字*，这类包含通过空白分隔的两个令牌的关键字。 标记单独使用时可能表示一种含义，一起使用时可能表示另一种含义。 例如，单词“ref”是一个普通的标识符，单词“class”是一个声明本机类的关键字。 但当两个单词组合到窗体**ref 类**，得到的聚合关键字声明名为的实体*运行时类*。

扩展还包括*上下文相关*关键字。 某个关键字被视为区分上下文，即表示其语义取决于包含它的语句类型及其在该语句中的位置。 例如，标记“property”既可以是标识符，也可以声明特殊类型的公共类成员。

下表列出了 C++ 语言扩展中的关键字。

|关键字|区分上下文|目标|参考|
|-------------|-----------------------|-------------|---------------|
|**ref 类**<br /><br /> **ref 结构**|否|声明类。|[类和结构](../windows/classes-and-structs-cpp-component-extensions.md)|
|**值类**<br /><br /> **值结构**|否|声明值类。|[类和结构](../windows/classes-and-structs-cpp-component-extensions.md)|
|**接口类**<br /><br /> **接口结构**|否|声明接口。|[接口类](../windows/interface-class-cpp-component-extensions.md)|
|**枚举类**<br /><br /> **enum 结构**|否|声明枚举。|[枚举类](../windows/enum-class-cpp-component-extensions.md)|
|**属性**|是|声明属性。|[属性](../windows/property-cpp-component-extensions.md)|
|**delegate**|是|声明委托。|[委托（C++ 组件扩展）](../windows/delegate-cpp-component-extensions.md)|
|**event**|是|声明事件。|[event](../windows/event-cpp-component-extensions.md)|

## <a name="override-specifiers"></a>重写说明符

可以使用下列关键字来限定派生的替代行为。 尽管**新**关键字不是 c + + 的扩展，因为它可以在其他上下文中使用此处列出。 某些说明符还可用于本机编程。 有关详细信息，请参阅[如何： 在本机编译中声明重写说明符 (C + + CLI)](../dotnet/how-to-declare-override-specifiers-in-native-compilations-cpp-cli.md)。

|关键字|区分上下文|目标|参考|
|-------------|-----------------------|-------------|---------------|
|**abstract**|是|指示函数或类是抽象的。|[abstract](../windows/abstract-cpp-component-extensions.md)|
|**new**|否|指示函数不替代基类版本。|[新 (新 vtable 中的槽）](../windows/new-new-slot-in-vtable-cpp-component-extensions.md)|
|**override**|是|指示方法必须替代基类版本。|[override](../windows/override-cpp-component-extensions.md)|
|**sealed**|是|防止类用作基类。|[sealed](../windows/sealed-cpp-component-extensions.md)|

## <a name="keywords-for-generics"></a>泛型关键字

已添加下列关键字来支持泛型类型。 有关详细信息，请参阅[泛型](../windows/generics-cpp-component-extensions.md)。

|关键字|区分上下文|目标|
|-------------|-----------------------|-------------|
|**泛型**|否|声明泛型类型。|
|**where**|是|指定应用于泛型类型参数的约束。|

## <a name="miscellaneous-keywords"></a>杂项关键字

C++ 扩展中已添加下列关键字。

|关键字|区分上下文|目标|参考|
|-------------|-----------------------|-------------|---------------|
|**finally**|是|指示默认异常处理行为。|[异常处理](../windows/exception-handling-cpp-component-extensions.md)|
|**for each, in**|否|枚举集合元素。|[for each, in](../dotnet/for-each-in.md)|
|**gcnew**|否|分配垃圾回收堆上的类型。 而不是使用**新**并**删除**。|[ref new、 gcnew](../windows/ref-new-gcnew-cpp-component-extensions.md)|
|**新的 ref**|是|分配的 Windows 运行时类型。 而不是使用**新**并**删除**。|[ref new、 gcnew](../windows/ref-new-gcnew-cpp-component-extensions.md)|
|**initonly**|是|指示只能在声明时或在静态构造函数中初始化成员。|[initonly (C++/CLI)](../dotnet/initonly-cpp-cli.md)|
|**文本**|是|创建文本变量。|[文本](../windows/literal-cpp-component-extensions.md)|
|**nullptr**|否|指示图柄或指针不指向对象。|[nullptr](../windows/nullptr-cpp-component-extensions.md)|

## <a name="template-constructs"></a>模板构造

下列语言构造作为模板而非关键字实现。 如果指定 `/ZW` 编译器选项，它们将在 `lang` 命名空间中定义。 如果指定 `/clr` 编译器选项，它们将在 `cli` 命名空间中定义。

|关键字|目标|参考|
|-------------|-------------|---------------|
|**array**|声明数组。|[数组](../windows/arrays-cpp-component-extensions.md)|
|**interior_ptr**|（仅限 CLR）指向引用类型中的数据。|[interior_ptr (C++/CLI)](../windows/interior-ptr-cpp-cli.md)|
|**pin_ptr**|（仅限 CLR）指向 CLR 引用类型以便暂时抑制垃圾回收系统。|[pin_ptr (C++/CLI)](../windows/pin-ptr-cpp-cli.md)|
|**safe_cast**|确定并执行运行时类型的最佳转换方法。|[safe_cast](../windows/safe-cast-cpp-component-extensions.md)|
|**typeid**|（仅限 CLR）检索用于描述给定类型或对象的 <xref:System.Type?displayProperty=fullName> 对象。|[typeid](../windows/typeid-cpp-component-extensions.md)|

## <a name="declarators"></a>声明符

下列类型声明符指示运行时自动管理已分配对象的生存期和删除。

|运算符|目标|参考|
|--------------|-------------|---------------|
|`^`|声明的句柄的对象;也就是说，不再可用时将自动删除的 Windows 运行时或 CLR 对象的指针。|[对象句柄运算符 (^)](../windows/handle-to-object-operator-hat-cpp-component-extensions.md)|
|`%`|声明跟踪引用;也就是说，不再可用时将自动删除的 Windows 运行时或 CLR 对象的引用。|[跟踪引用运算符](../windows/tracking-reference-operator-cpp-component-extensions.md)|

## <a name="additional-constructs-and-related-topics"></a>其他构造和相关主题

本节列出了其他编程构造以及与 CLR 相关的主题。

|主题|描述|
|-----------|-----------------|
|[__identifier (C++/CLI)](../windows/identifier-cpp-cli.md)|（Windows 运行时和 CLR）可以使用关键字用作标识符。|
|[变量自变量列表 (...) (C++/CLI)](../windows/variable-argument-lists-dot-dot-dot-cpp-cli.md)|（Windows 运行时和 CLR）允许函数采用可变数量的参数。|
|[对应于 C++ 本机类型的 .NET Framework 类型 (C++/CLI)](../dotnet/dotnet-framework-equivalents-to-cpp-native-types-cpp-cli.md)|列出替代 C++ 整型类型的 CLR 类型。|
|[appdomain](../cpp/appdomain.md) **__declspec**修饰符|**__declspec**修饰符规定每个 appdomain 都存在静态和全局变量。|
|[C 样式强制转换和 /clr (C + + CLI)](../windows/c-style-casts-with-clr-cpp-cli.md)|描述如何解释 C 样式转换。|
|[__clrcall](../cpp/clrcall.md)调用约定|指示符合 CLS 的调用约定。|
|`__cplusplus_cli`|[预定义宏](../preprocessor/predefined-macros.md)|
|[自定义属性](../windows/custom-attributes-cpp.md)|描述如何定义自己的 CLR 属性。|
|[异常处理](../windows/exception-handling-cpp-component-extensions.md)|概述异常处理。|
|[显式重写](../windows/explicit-overrides-cpp-component-extensions.md)|演示成员函数如何替代任意成员。|
|[友元程序集 (C++)](../dotnet/friend-assemblies-cpp.md)|讨论客户端程序集如何访问程序集组件中的所有类型。|
|[装箱](../windows/boxing-cpp-component-extensions.md)|演示值类型进行装箱的条件。|
|[编译器支持类型特征](../windows/compiler-support-for-type-traits-cpp-component-extensions.md)|讨论如何在编译时检测类型的特征。|
|[managed、 unmanaged](../preprocessor/managed-unmanaged.md)杂注|演示 managed 和 unmanaged 函数如何共存于同一模块中。|
|[进程](../cpp/process.md) **__declspec**修饰符|**__declspec**修饰符规定每个进程都存在静态和全局变量。|
|[反射 (C++/CLI)](../dotnet/reflection-cpp-cli.md)|演示运行时类型信息的 CLR 版本。|
|[字符串](../windows/string-cpp-component-extensions.md)|讨论编译器如何将字符串文本转换为 <xref:System.String>。|
|[类型转发 (C++/CLI)](../windows/type-forwarding-cpp-cli.md)|允许将一个传送程序集中的类型移动到另一个程序集，从而使客户端代码无需重新编译。|
|[用户定义的特性](../windows/user-defined-attributes-cpp-component-extensions.md)|演示用户定义的属性。|
|[#using 指令](../preprocessor/hash-using-directive-cpp.md)|导入外部程序集。|
|[XML 文档](../ide/xml-documentation-visual-cpp.md)|介绍通过使用基于 XML 的代码文档[/doc （处理文档注释） （C/c + +）](../build/reference/doc-process-documentation-comments-c-cpp.md)|

## <a name="see-also"></a>请参阅

[使用 C++/CLI (Visual C++) 进行 .NET 编程](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)<br/>
[本机和 .NET 的互操作性](../dotnet/native-and-dotnet-interoperability.md)