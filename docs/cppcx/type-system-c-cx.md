---
title: 类型系统 (C++/CX)
ms.date: 02/03/2017
ms.assetid: b67bee8a-b526-4872-969e-ef22724e88fe
ms.openlocfilehash: bc45a835e37ff4e3ea239d253078bf50eab1b2ff
ms.sourcegitcommit: 180f63704f6ddd07a4172a93b179cf0733fd952d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/06/2019
ms.locfileid: "70740908"
---
# <a name="type-system-ccx"></a>类型系统 (C++/CX)

通过使用 Windows 运行时的体系结构，可以使用C++/cx、Visual Basic、视觉C#对象和 JavaScript 来编写直接访问 Windows API 的应用程序和组件，并与其他 Windows 运行时应用程序和组件进行互操作。 通用 Windows 平台C++编译编写为直接在 CPU 中执行的本机代码的应用。 通用 Windows 平台编写的应用C#或 Visual Basic 编译为 Microsoft 中间语言（MSIL）并在公共语言运行时（CLR）中执行。 用 JavaScript 编写的通用 Windows 平台应用在运行时环境中执行。 操作系统组件本身 Windows 运行时用本机代码编写C++和运行。 所有这些组件和通用 Windows 平台应用直接通过 Windows 运行时应用程序二进制接口（ABI）进行通信。

为了在现代C++的用法中支持 Windows 运行时，Microsoft 创建了C++/cx C++/CX 提供了 Windows 运行时基本的基本类型和实现，它们使C++应用程序和组件能够与用其他语言编写的应用程序一起在 ABI 之间进行通信。 您可以使用任何 Windows 运行时类型，也可以创建类、结构、接口以及其他通用 Windows 平台应用程序和组件可以使用的其他用户定义的类型。 使用C++/cx 编写的通用 Windows 平台应用程序还可以使用常规C++类和结构，只要它们没有公共可访问性。

有关 C++/CX 语言投影的深度讨论以及它在后台如何工作，请参阅以下博客帖子：

1. [C++第0部分（ \[共\]n 部分）：简介](https://blogs.msdn.microsoft.com/vcblog/2012/08/29/ccx-part-0-of-n-an-introduction)

1. [C++第1部分（ \[共\]n 部分）：简单类](https://blogs.msdn.microsoft.com/vcblog/2012/09/05/ccx-part-1-of-n-a-simple-class)

1. [C++/Cx 第2部分\[（\]共 n 部分）：磨损头衔的类型](https://blogs.msdn.microsoft.com/vcblog/2012/09/17/ccx-part-2-of-n-types-that-wear-hats)

1. [C++第3部分（ \[共\]n 部分）：正在构造](https://blogs.msdn.microsoft.com/vcblog/2012/10/05/ccx-part-3-of-n-under-construction/)

1. [C++第4部分（ \[共\]n 部分）：静态成员函数](https://blogs.msdn.microsoft.com/vcblog/2012/10/19/ccx-part-4-of-n-static-member-functions)

## <a name="windows-metadata-winmd-files"></a>Windows 元数据 (.winmd) 文件

在编译用编写的通用 Windows 平台应用程序时C++，编译器将生成本机计算机代码中的可执行文件，并且还会生成一个单独的 Windows 元数据（winmd）文件，其中包含公共 Windows 运行时的说明。类型，包括类、结构、枚举、接口、参数化接口和委托。 元数据的格式类似于在 .NET Framework 程序集中使用的格式。  在 C++ 组件中，.winmd 文件只包含元数据；可执行代码位于单独的文件中。 Windows 附带的 Windows 运行时组件就是这种情况。 WinMD 文件名必须与源代码中的根命名空间的前缀匹配或为该前缀。 （对于 .NET Framework 语言，.winmd 文件同时包含代码和元数据，正如一个 .NET Framework 程序集。）

.winmd 文件中的元数据表示你的代码的已发布图面。 无论这些其他应用程序用什么语言编写，已发布的类型对其他通用 Windows 平台均可见。 因此，元数据（或已发布的代码）只能包含由 Windows 运行时类型系统指定的类型。 特定于 C++ 的语言构造（如规则类、数组、模板或 STL 容器）不能在元数据中发布，因为 Javascript 或 C# 客户端应用程序不知道如何处理它们。

类型或方法在元数据中是否可见取决于应用于它们的可访问性修饰符。 若要可见，必须在命名空间中声明类型，而且必须声明为公共类型。 允许在你的代码中将非公共 ref 类作为内部帮助程序类型，它在元数据中正好不可见。 即使在公共 ref 类中，也非所有成员都必然可见。 下表列出了公共 ref 类C++中的访问说明符与 Windows 运行时元数据可见性之间的关系：

|||
|-|-|
|**在元数据中发布**|**未在元数据中发布**|
|public|private|
|protected|internal|
|公共受保护|私有受保护|

可以使用 **“对象浏览器”** 查看 .winmd 文件的内容。 Windows 附带的 Windows 运行时组件位于 Windows winmd 文件中。 默认 winmd 文件包含/Cx 中C++使用的基本类型，而 Platform.string 包含平台命名空间中的其他类型。 默认情况下，这三个 winmd 文件包含在通用 Windows 平台C++应用的每个项目中。

> [!TIP]
> [Platform::Collections Namespace](../cppcx/platform-collections-namespace.md) 中的类型没有出现在 .winmd 文件中，因为它们不是公共类型。 它们是 `Windows::Foundation::Collections`中定义的接口的私有 C++ 特定实现。 用 JavaScript 编写的 Windows 运行时应用程序C#不知道[Platform：：集合：： Vector 类](../cppcx/platform-collections-vector-class.md)的定义，但它`Windows::Foundation::Collections::IVector`可以使用。 `Platform::Collections` 类型在 collection.h 中定义。

## <a name="windows-runtime-type-system-in-ccx"></a>/Cx 中的C++Windows 运行时类型系统

以下各节介绍 Windows 运行时类型系统的主要功能及其在/Cx 中C++的支持方式

### <a name="namespaces"></a>命名空间

所有 Windows 运行时类型都必须在命名空间内声明;Windows API 本身按命名空间组织。 .winmd 文件必须具有和根命名空间相同的名称。 例如，名为 A.B.C.MyClass 的类只有在名为 A.winmd 或 A.B.winmd 或 A.B.C.winmd 的元数据文件中定义后才能实例化。 DLL 的名称不必与 .winmd 文件名匹配。

Windows API 本身已重创为按命名空间组织的分解类库。  所有 Windows 运行时组件都在 Windows. * 命名空间中声明。

有关详细信息，请参阅[命名空间和类型可见性](../cppcx/namespaces-and-type-visibility-c-cx.md)。

### <a name="fundamental-types"></a>基本类型

Windows 运行时定义以下基本类型： UInt8、Int16、UInt16、Int32、UInt32、Int64、UInt64、Single、Double、Char16、Boolean 和 String。 C++/CX 支持其默认命名空间中的基本数值类型，如 uint16、uint32、uint64、int16、int32、int64、float32、float64 和 char16。 布尔值和字符串也在平台命名空间中定义。

C++/Cx 还定义了 uint8，它`unsigned char`等效于，这在 Windows 运行时不受支持，因此不能用于公共 api。

可通过将基础类型包装在 [Platform::IBox Interface](../cppcx/platform-ibox-interface.md) 接口中来使其可以为 null。 有关更多信息，请参见 [值类和结构](../cppcx/value-classes-and-structs-c-cx.md)中定义的接口的私有 C++ 特定实现。

有关基础类型的更多信息，请参见 [基础类型](../cppcx/fundamental-types-c-cx.md)

### <a name="strings"></a>字符串

Windows 运行时字符串是16位 UNICODE 字符的不可变序列。 Windows 运行时的字符串被投影为`Platform::String^`。 此类为字符串构造、处理和在 `wchar_t`间来回转换提供方法。

有关更多信息，请参见 [字符串](../cppcx/strings-c-cx.md)中定义的接口的私有 C++ 特定实现。

### <a name="arrays"></a>数组

Windows 运行时支持任何类型的一维数组。 不支持数组的数组。  在C++/cx 中，Windows 运行时数组投影为[Platform：： Array 类](../cppcx/platform-array-class.md)。

有关详细信息，请参阅[Array And WriteOnlyArray](../cppcx/array-and-writeonlyarray-c-cx.md)

### <a name="ref-classes-and-structs"></a>Ref 类和结构

Windows 运行时类被投影C++为 ref 类或 ref 结构，因为它们按引用进行复制。 ref 类和 ref 结构的内存管理通过引用计数透明地处理。 当对对象的最后引用超出范围时，对象被销毁。 ref 类或 ref 结构可以：

- 作为成员构造函数、方法、属性和事件而包含。 这些成员可以具有公共、私有、受保护或内部可访问性。

- 可以包含私有嵌套枚举、结构或类定义。

- 可直接从基类继承，并且可以实现任意数量的接口。 所有 ref 类都可以隐式转换为 [Platform::Object Class](../cppcx/platform-object-class.md) ，并且可重写其虚拟方法，如 [Object::ToString](../cppcx/platform-object-class.md#tostring)。

为防止进一步派生，必须将具有公共构造函数的 ref 类声明为密封类。

有关更多信息，请参见 [Ref 类和结构](../cppcx/ref-classes-and-structs-c-cx.md)

### <a name="value-classes-and-structs"></a>值类和结构

值类或值结构表示基本数据结构，它们只包含字段，这可能是值类、值结构或类型 `Platform::String^`。  值结构和值类通过值复制。

可通过将值结构包装在 IBox 接口中来使其可以为 null。

有关更多信息，请参见 [值类和结构](../cppcx/value-classes-and-structs-c-cx.md)中定义的接口的私有 C++ 特定实现。

### <a name="partial-classes"></a>分部类

分部类功能可使你对多个文件定义一个类。 这主要用于使代码生成工具（如 XAML 编辑器）能够在不影响你所编辑文件的情况下修改一个文件。

有关更多信息，请参见 [分部类](../cppcx/partial-classes-c-cx.md)

### <a name="properties"></a>属性

属性是任何 Windows 运行时类型的公共数据成员，并实现为 get/set 方法对。 客户端代码访问属性，就好像属性是一个公共字段。 不需要自定义 get 或 set 代码的属性称为 *平常属性* ，无需显式 get 或 set 方法即可声明它们。

有关更多信息，请参见 [属性](../cppcx/properties-c-cx.md)中定义的接口的私有 C++ 特定实现。

### <a name="windows-runtime-collections-in-ccx"></a>/Cx 中的C++Windows 运行时集合

Windows 运行时为每种语言以自己的方式实现的集合类型定义一组接口。 C++/CX 在[Platform：： collection：： Vector 类](../cppcx/platform-collections-vector-class.md)、 [Platform：： Collection：： Map 类](../cppcx/platform-collections-map-class.md)和其他相关具体集合类型（与其标准模板库（STL）对应项）之间提供实现。

有关详细信息，请参阅[集合](../cppcx/collections-c-cx.md)。

### <a name="template-ref-classes"></a>模板 ref 类

可以模板化和专用化私有和内部 ref 类。

有关更多信息，请参见 [模板 ref 类](../cppcx/template-ref-classes-c-cx.md)中定义的接口的私有 C++ 特定实现。

### <a name="interfaces"></a>接口

如果 ref 类或 ref 结构继承自接口，则 Windows 运行时接口定义一组公共属性、方法和事件。

有关详细信息，请参阅[接口](../cppcx/interfaces-c-cx.md)。

### <a name="enums"></a>枚举

Windows 运行时中的枚举类类似于中C++的范围枚举。 基础类型为 int32（除非应用 [标志] 特性，此情况下的基础类型为 uint32）。

有关更多信息，请参见 [枚举](../cppcx/enums-c-cx.md)中定义的接口的私有 C++ 特定实现。

### <a name="delegates"></a>委托

Windows 运行时中的委托类似于中C++的 std：： function 对象。 它是特殊的 ref 类，用于调用具有兼容签名的客户端提供的函数。  委托最常用于 Windows 运行时作为事件的类型。

有关详细信息，请参阅[委托](../cppcx/delegates-c-cx.md)。

### <a name="exceptions"></a>Exceptions

在 C++/CX 中，可以捕获自定义异常类型、 [std::exception](../standard-library/exception-class.md) 类型和 [Platform::Exception](../cppcx/platform-exception-class.md) 类型。

有关更多信息，请参见 [异常](../cppcx/exceptions-c-cx.md)中定义的接口的私有 C++ 特定实现。

### <a name="events"></a>事件

事件是其类型为委托类型的 ref 类或 ref 结构中的公共成员。 事件只能被调用，即，被所属类触发。 但是，客户端代码可以提供自己的函数（即事件处理程序）并在所属类触发事件时被调用。

有关更多信息，请参见 [事件](../cppcx/events-c-cx.md)中定义的接口的私有 C++ 特定实现。

### <a name="casting"></a>强制转换

C++/CX 支持标准 C++ 强制转换运算符 [static_cast](../cpp/static-cast-operator.md)、 [dynamic_cast](../cpp/dynamic-cast-operator.md)和 [reinterpret_cast](../cpp/reinterpret-cast-operator.md)，以及特定于 C++/CX 的 **safe_cast** 运算符。

有关更多信息，请参见 [强制转换](../cppcx/casting-c-cx.md)中定义的接口的私有 C++ 特定实现。

### <a name="boxing"></a>装箱

装箱变量是在需要引用语义的情况下，包装在引用类型中的值类型。

有关更多信息，请参见 [装箱](../cppcx/boxing-c-cx.md)中定义的接口的私有 C++ 特定实现。

### <a name="attributes"></a>特性

特性是可以应用于任何 Windows 运行时类型或类型成员并且可以在运行时进行检查的元数据值。 Windows 运行时定义`Windows::Foundation::Metadata`命名空间中的一组公共特性。 此版本中的 Windows 运行时不支持公共接口上的用户定义属性。

## <a name="api-deprecation"></a>API 弃用

描述如何使用 Windows 运行时系统类型使用的同一特性将公共 Api 标记为已弃用。

有关详细信息，请参阅[弃用类型和成员](../cppcx/deprecating-types-and-members-c-cx.md)。

## <a name="see-also"></a>请参阅

[C++/CX 语言参考](../cppcx/visual-c-language-reference-c-cx.md)
