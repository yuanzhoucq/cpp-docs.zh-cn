---
title: 适用于 .NET 和 UWP 的组件扩展
ms.date: 10/12/2018
ms.topic: overview
helpviewer_keywords:
- what's new [C++], keywords
- what's new [C++], language features
- C++, keywords
- keywords [C++]
- Managed Extensions for C++, replacement syntax
ms.assetid: 1e400ee6-3ac9-4910-a608-9d3d5993e423
ms.openlocfilehash: aa6e5d1ea7d1bc2d7ebfaf07c7c9f808b37e9804
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87219763"
---
# <a name="component-extensions-for-net-and-uwp"></a>适用于 .NET 和 UWP 的组件扩展

C++ 标准允许编译器供应商向语言提供非标准扩展。 Microsoft 提供了有助于将本机 C++ 代码连接到 .NET Framework 或通用 Windows 平台 (UWP) 上运行的代码的扩展。 .NET 扩展称为“C++/CLI”，并生成在 .NET 托管执行环境（称为“公共语言运行时 (CLR)”）中执行的代码。 UWP 扩展称为“C++/CX”，并生成本机代码。

> [!NOTE]
> 对于新应用程序，建议使用 C++/WinRT，而不是 C++/CX。 C++/ WinRT 是 Windows 运行时 API 的新标准 C++17 语言投影。 我们将继续支持 C++/CX 和 WRL，但强烈建议新应用程序使用 C++/WinRT。 有关详细信息，请参阅[c + +/WinRT](/windows/uwp/cpp-and-winrt-apis/index)。

### <a name="two-runtimes-one-set-of-extensions"></a>两个运行时，一组扩展

C++/CLI 扩展了 ISO/ANSI C++ 标准，并在 ECMA C++/CLI 标准下定义。 有关详细信息，请参阅[使用 C++/CLI 进行 .NET 编程 (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)。

C++/CX 扩展是 C++/CLI 的子集。 虽然扩展语法在大多数情况下是完全相同的，但具体生成什么代码还是取决于你是将 `/ZW` 编译器选项指定给目标 UWP，还是将 `/clr` 选项指定给目标 .NET。 当使用 Visual Studio 创建项目时，将自动设置这些开关。

## <a name="data-type-keywords"></a>数据类型关键字

语言扩展包括聚合关键字**，它是由用空格分隔的两个标记组成。 标记单独使用时可能表示一种含义，一起使用时可能表示另一种含义。 例如，单词“ref”是一个普通的标识符，单词“class”是一个声明本机类的关键字。 不过，如果将这两个字词组合成 ref class****，生成的聚合关键字声明称为“运行时类”** 的实体。

扩展还包括上下文相关** 关键字。 某个关键字被视为区分上下文，即表示其语义取决于包含它的语句类型及其在该语句中的位置。 例如，标记“property”既可以是标识符，也可以声明特殊类型的公共类成员。

下表列出了 C++ 语言扩展中的关键字。

|关键字|区分上下文|目标|参考|
|-------------|-----------------------|-------------|---------------|
|**ref class**<br /><br /> **ref struct**|否|声明类。|[类和结构](classes-and-structs-cpp-component-extensions.md)|
|**value class**<br /><br /> **value struct**|否|声明值类。|[类和结构](classes-and-structs-cpp-component-extensions.md)|
|**接口类**<br /><br /> **interface struct**|否|声明接口。|[接口类](interface-class-cpp-component-extensions.md)|
|**枚举类**<br /><br /> **enum struct**|否|声明枚举。|[枚举类](enum-class-cpp-component-extensions.md)|
|**`property`**|是|声明属性。|[property](property-cpp-component-extensions.md)|
|**delegate**|是|声明委托。|[delegate（C++/CLI 和 C++/CX）](delegate-cpp-component-extensions.md)|
|**event**|是|声明事件。|[event](event-cpp-component-extensions.md)|

## <a name="override-specifiers"></a>重写说明符

可以使用下列关键字来限定派生的替代行为。 尽管 **`new`** 关键字不是 c + + 的扩展，但它是在此处列出的，因为它可以在其他上下文中使用。 某些说明符还可用于本机编程。 有关详细信息，请参阅[如何：在本机编译中声明重写说明符（c + +/cli）](../dotnet/how-to-declare-override-specifiers-in-native-compilations-cpp-cli.md)。

|关键字|区分上下文|目标|参考|
|-------------|-----------------------|-------------|---------------|
|**abstract**|是|指示函数或类是抽象的。|[abstract](abstract-cpp-component-extensions.md)|
|**`new`**|否|指示函数不替代基类版本。|[新（vtable 中的新槽）](new-new-slot-in-vtable-cpp-component-extensions.md)|
|**override**|是|指示方法必须替代基类版本。|[override](override-cpp-component-extensions.md)|
|**sealed**|是|防止类用作基类。|[sealed](sealed-cpp-component-extensions.md)|

## <a name="keywords-for-generics"></a>泛型关键字

已添加下列关键字来支持泛型类型。 有关详细信息，请参阅[泛型](generics-cpp-component-extensions.md)。

|关键字|区分上下文|目标|
|-------------|-----------------------|-------------|
|**泛型**|否|声明泛型类型。|
|**where**|是|指定应用于泛型类型参数的约束。|

## <a name="miscellaneous-keywords"></a>杂项关键字

C++ 扩展中已添加下列关键字。

|关键字|区分上下文|目标|参考|
|-------------|-----------------------|-------------|---------------|
|**finally**|是|指示默认异常处理行为。|[异常处理](exception-handling-cpp-component-extensions.md)|
|**for each, in**|否|枚举集合元素。|[for each, in](../dotnet/for-each-in.md)|
|**gcnew**|否|分配垃圾回收堆上的类型。 使用而不是 **`new`** 和 **`delete`** 。|[ref new、gcnew](ref-new-gcnew-cpp-component-extensions.md)|
|**ref new**|是|分配 Windows 运行时类型。 使用而不是 **`new`** 和 **`delete`** 。|[ref new、gcnew](ref-new-gcnew-cpp-component-extensions.md)|
|**initonly**|是|指示只能在声明时或在静态构造函数中初始化成员。|[initonly (C++/CLI)](../dotnet/initonly-cpp-cli.md)|
|**字符**|是|创建文本变量。|[文本](literal-cpp-component-extensions.md)|
|**`nullptr`**|否|指示图柄或指针不指向对象。|[nullptr](nullptr-cpp-component-extensions.md)|

## <a name="template-constructs"></a>模板构造

下列语言构造作为模板而非关键字实现。 如果指定 `/ZW` 编译器选项，它们将在 `lang` 命名空间中定义。 如果指定 `/clr` 编译器选项，它们将在 `cli` 命名空间中定义。

|关键字|目标|参考|
|-------------|-------------|---------------|
|**array**|声明数组。|[数组](arrays-cpp-component-extensions.md)|
|**interior_ptr**|（仅限 CLR）指向引用类型中的数据。|[interior_ptr （c + +/CLI）](interior-ptr-cpp-cli.md)|
|**pin_ptr**|（仅限 CLR）指向 CLR 引用类型以便暂时抑制垃圾回收系统。|[pin_ptr （c + +/CLI）](pin-ptr-cpp-cli.md)|
|**safe_cast**|确定并执行运行时类型的最佳转换方法。|[safe_cast](safe-cast-cpp-component-extensions.md)|
|**`typeid`**|（仅限 CLR）检索用于描述给定类型或对象的 <xref:System.Type?displayProperty=fullName> 对象。|[typeid](typeid-cpp-component-extensions.md)|

## <a name="declarators"></a>声明符

下列类型声明符指示运行时自动管理已分配对象的生存期和删除。

|运算符|用途|参考|
|--------------|-------------|---------------|
|`^`|声明指向对象的句柄；即指向 Windows 运行时或不再可用时自动删除的 CLR 对象的指针。|[对象句柄运算符（^）](handle-to-object-operator-hat-cpp-component-extensions.md)|
|`%`|声明跟踪引用；即对 Windows 运行时或不再可用时自动删除的 CLR 对象的引用。|[跟踪引用运算符](tracking-reference-operator-cpp-component-extensions.md)|

## <a name="additional-constructs-and-related-topics"></a>其他构造和相关主题

本节列出了其他编程构造以及与 CLR 相关的主题。

|主题|描述|
|-----------|-----------------|
|[__identifier （c + +/CLI）](identifier-cpp-cli.md)|（Windows 运行时和 CLR）允许使用关键字作为标识符。|
|[变量参数列表（...）（C + +/CLI）](variable-argument-lists-dot-dot-dot-cpp-cli.md)|（Windows 运行时和 CLR）允许函数使用可变数量参数。|
|[对应于 C++ 本机类型的 .NET Framework 类型 (C++/CLI)](../dotnet/dotnet-framework-equivalents-to-cpp-native-types-cpp-cli.md)|列出替代 C++ 整型类型的 CLR 类型。|
|[appdomain](../cpp/appdomain.md) **`__declspec`** 组合键|**`__declspec`** 要求每个 appdomain 都存在静态和全局变量的修饰符。|
|[采用/clr 的 C 样式强制转换（c + +/CLI）](c-style-casts-with-clr-cpp-cli.md)|描述如何解释 C 样式转换。|
|[__clrcall](../cpp/clrcall.md) 调用约定|指示符合 CLS 的调用约定。|
|`__cplusplus_cli`|[预定义的宏](../preprocessor/predefined-macros.md)|
|[自定义属性](user-defined-attributes-cpp-component-extensions.md)|描述如何定义自己的 CLR 属性。|
|[异常处理](exception-handling-cpp-component-extensions.md)|概述异常处理。|
|[显式重写](explicit-overrides-cpp-component-extensions.md)|演示成员函数如何替代任意成员。|
|[友元程序集（c + +）](../dotnet/friend-assemblies-cpp.md)|讨论客户端程序集如何访问程序集组件中的所有类型。|
|[装箱](boxing-cpp-component-extensions.md)|演示值类型进行装箱的条件。|
|[编译器支持类型特征](compiler-support-for-type-traits-cpp-component-extensions.md)|讨论如何在编译时检测类型的特征。|
|[托管、非托管](../preprocessor/managed-unmanaged.md)杂注|演示 managed 和 unmanaged 函数如何共存于同一模块中。|
|[处理](../cpp/process.md) **`__declspec`** 组合键|**`__declspec`** 要求每个进程都存在静态和全局变量的修饰符。|
|[反射 (C++/CLI)](../dotnet/reflection-cpp-cli.md)|演示运行时类型信息的 CLR 版本。|
|[字符串](string-cpp-component-extensions.md)|讨论编译器如何将字符串文本转换为 <xref:System.String>。|
|[类型转发（c + +/CLI）](type-forwarding-cpp-cli.md)|允许将一个传送程序集中的类型移动到另一个程序集，从而使客户端代码无需重新编译。|
|[用户定义的属性](user-defined-attributes-cpp-component-extensions.md)|演示用户定义的属性。|
|[#using 指令](../preprocessor/hash-using-directive-cpp.md)|导入外部程序集。|
|[XML 文档](../build/reference/xml-documentation-visual-cpp.md)|使用 [/doc（处理文档注释）(C/C++)](../build/reference/doc-process-documentation-comments-c-cpp.md) 解释基于 XML 的代码文档|

## <a name="see-also"></a>另请参阅

[用 c + +/CLI 进行 .NET 编程（Visual C++）](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)<br/>
[本机和 .NET 互操作性](../dotnet/native-and-dotnet-interoperability.md)
