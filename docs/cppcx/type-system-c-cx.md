---
title: 类型系统 (C++/CX)
ms.date: 02/03/2017
ms.assetid: b67bee8a-b526-4872-969e-ef22724e88fe
ms.openlocfilehash: fbc7a178621624e396c80509703ce1b5b4c19162
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62392084"
---
# <a name="type-system-ccx"></a>类型系统 (C++/CX)

通过使用 Windows 运行时体系结构，你可以使用C++/CX，Visual Basic 中，视觉对象C#和 JavaScript 编写应用程序和组件的直接访问 Windows API 并与其他 Windows 运行时应用和组件进行互操作。 通用 Windows 平台编写的应用程序中C++编译为直接在 CPU 中运行的本机代码。 通用 Windows 平台编写的应用程序在 C# 或 Visual Basic 中为 Microsoft 中间语言 (MSIL) 并执行公共语言运行时 (CLR) 中。 在运行时环境中执行的以 JavaScript 编写通用 Windows 平台应用。 Windows 运行时操作系统组件本身用C++和运行为本机代码。 所有这些组件和通用 Windows 平台应用程序直接通过 Windows 运行时应用程序二进制接口 (ABI) 进行通信。

在现代中启用对 Windows 运行时支持C++惯用语法，Microsoft 创建C++/CX。 C++/CX 提供内置基类型和实现的基本 Windows 运行时类型，使C++应用程序和组件能够跨 ABI 与用其他语言编写的应用程序进行通信。 您可以使用任何 Windows 运行时类型，或创建类、 结构、 接口和其他可供其他通用 Windows 平台应用和组件的用户定义类型。 通用 Windows 平台应用中编写的C++/CX 还可以定期使用C++类和结构，只要它们不具有公共可访问性。

有关 C++/CX 语言投影的深度讨论以及它在后台如何工作，请参阅以下博客帖子：

1. [C++/CX 的第 0 部分\[n\]:简介](https://blogs.msdn.microsoft.com/vcblog/2012/08/29/ccx-part-0-of-n-an-introduction)

1. [C++/CX 的第 1 部分\[n\]:一个简单的类](https://blogs.msdn.microsoft.com/vcblog/2012/09/05/ccx-part-1-of-n-a-simple-class)

1. [C++/CX 的第 2 部分\[n\]:带尖角符号的类型](https://blogs.msdn.microsoft.com/vcblog/2012/09/17/ccx-part-2-of-n-types-that-wear-hats)

1. [C++/CX 的第 3 部分\[n\]:正在施工中](https://blogs.msdn.microsoft.com/vcblog/2012/10/05/ccx-part-3-of-n-under-construction/)

1. [C++/CX 的第 4 部分\[n\]:静态成员函数](https://blogs.msdn.microsoft.com/vcblog/2012/10/19/ccx-part-4-of-n-static-member-functions)

## <a name="windows-metadata-winmd-files"></a>Windows 元数据 (.winmd) 文件

通用 Windows 平台编写的应用程序是在编译时C++，编译器将在本机代码，生成可执行文件并还会生成包含公共 Windows 运行时的说明的单独 Windows 元数据 (.winmd) 文件类型，包括类、 结构、 枚举、 接口、 参数化的接口和委托。 元数据的格式类似于在 .NET Framework 程序集中使用的格式。  在 C++ 组件中，.winmd 文件只包含元数据；可执行代码位于单独的文件中。 这是 Windows 附带的 Windows 运行时组件。 WinMD 文件名必须与源代码中的根命名空间的前缀匹配或为该前缀。 （对于 .NET Framework 语言，.winmd 文件同时包含代码和元数据，正如一个 .NET Framework 程序集。）

.winmd 文件中的元数据表示你的代码的已发布图面。 已发布的类型会向其他通用 Windows 平台编写这些其他应用程序所无论何种语言。 因此，元数据或已发布的代码中，只能包含由 Windows 运行时类型系统指定的类型。 特定于 C++ 的语言构造（如规则类、数组、模板或 STL 容器）不能在元数据中发布，因为 Javascript 或 C# 客户端应用程序不知道如何处理它们。

类型或方法在元数据中是否可见取决于应用于它们的可访问性修饰符。 若要可见，必须在命名空间中声明类型，而且必须声明为公共类型。 允许在你的代码中将非公共 ref 类作为内部帮助程序类型，它在元数据中正好不可见。 即使在公共 ref 类中，也非所有成员都必然可见。 下表列出了之间的关系C++访问中的公共 ref 类和 Windows 运行时元数据可见性说明符：

|||
|-|-|
|**在元数据中发布**|**未在元数据中发布**|
|public|private|
|protected|internal|
|公共受保护|私有受保护|

可以使用 **“对象浏览器”** 查看 .winmd 文件的内容。 Windows 附带的 Windows 运行时组件在 Windows.winmd 文件中。 Default.winmd 文件包含在中使用的基础类型C++/CX 和 platform.winmd 包含来自平台命名空间的其他类型。 默认情况下，这三个.winmd 文件包含在每个C++适用于通用 Windows 平台应用项目。

> [!TIP]
> [Platform::Collections Namespace](../cppcx/platform-collections-namespace.md) 中的类型没有出现在 .winmd 文件中，因为它们不是公共类型。 它们是 `Windows::Foundation::Collections`中定义的接口的私有 C++ 特定实现。 在 JavaScript 或 C# 编写的 Windows 运行时应用不知道什么[类](../cppcx/platform-collections-vector-class.md)，但是它可以使用`Windows::Foundation::Collections::IVector`。 `Platform::Collections` 类型在 collection.h 中定义。

## <a name="windows-runtime-type-system-in-ccx"></a>在 Windows 运行时类型系统C++/CX

以下部分介绍的主要功能的 Windows 运行时类型系统和中的支持C++/CX。

### <a name="namespaces"></a>命名空间

所有 Windows 运行时类型必须都声明命名空间; 内Windows API 本身按命名空间。 .winmd 文件必须具有和根命名空间相同的名称。 例如，名为 A.B.C.MyClass 的类只有在名为 A.winmd 或 A.B.winmd 或 A.B.C.winmd 的元数据文件中定义后才能实例化。 DLL 的名称不必与 .winmd 文件名匹配。

Windows API 本身已重创为按命名空间组织的分解类库。  所有 Windows 运行时组件中的 windows.* 命名空间都声明。

有关详细信息，请参阅[命名空间和类型可见性](../cppcx/namespaces-and-type-visibility-c-cx.md)。

### <a name="fundamental-types"></a>基本类型

Windows 运行时定义以下基础类型、 UInt8、 Int16、 UInt16、 Int32、 UInt32、 Int64、 UInt64、 单、 Double、 Char16、 布尔值和字符串。 C++/CX uint16、 uint32、 uint64、 int16、 int32、 int64、 float32、 float64 和 char16 作为其默认命名空间中支持基本数值类型。 布尔值和字符串也在平台命名空间中定义。

C++/CX 还定义 uint8，等效于`unsigned char`，它不支持在 Windows 运行时中并不能在公共 Api 中使用。

可通过将基础类型包装在 [Platform::IBox Interface](../cppcx/platform-ibox-interface.md) 接口中来使其可以为 null。 有关更多信息，请参见 [值类和结构](../cppcx/value-classes-and-structs-c-cx.md)中定义的接口的私有 C++ 特定实现。

有关基础类型的更多信息，请参见 [基础类型](../cppcx/fundamental-types-c-cx.md)

### <a name="strings"></a>字符串

Windows 运行时字符串是 16 位 UNICODE 字符的不可变序列。 Windows 运行时字符串表现为`Platform::String^`。 此类为字符串构造、处理和在 `wchar_t`间来回转换提供方法。

有关更多信息，请参见 [字符串](../cppcx/strings-c-cx.md)中定义的接口的私有 C++ 特定实现。

### <a name="arrays"></a>数组

Windows 运行时支持任何类型的一维的数组。 不支持数组的数组。  在C++/CX，Windows 运行时数组被投影为[platform:: array 类](../cppcx/platform-array-class.md)。

有关详细信息，请参阅[Array 和 WriteOnlyArray](../cppcx/array-and-writeonlyarray-c-cx.md)

### <a name="ref-classes-and-structs"></a>Ref 类和结构

Windows 运行时类在中进行投影C++/CX ref 类或 ref 结构，因为它们按引用进行复制。 ref 类和 ref 结构的内存管理通过引用计数透明地处理。 当对对象的最后引用超出范围时，对象被销毁。 ref 类或 ref 结构可以：

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

属性是任何 Windows 运行时类型的公共数据成员，实现为 get/set 方法对。 客户端代码访问属性，就好像属性是一个公共字段。 不需要自定义 get 或 set 代码的属性称为 *平常属性* ，无需显式 get 或 set 方法即可声明它们。

有关更多信息，请参见 [属性](../cppcx/properties-c-cx.md)中定义的接口的私有 C++ 特定实现。

### <a name="windows-runtime-collections-in-ccx"></a>Windows 运行时集合中的C++/CX

Windows 运行时定义一组自己的方式实现每种语言的集合类型的接口。 C++/CX 中提供实现[类](../cppcx/platform-collections-vector-class.md)， [3&gt;platform::collections::map 类](../cppcx/platform-collections-map-class.md)，和其他相关具体集合类型，与兼容其标准模板库 (STL) 对应项。

有关详细信息，请参阅[集合](../cppcx/collections-c-cx.md)。

### <a name="template-ref-classes"></a>模板 ref 类

可以模板化和专用化私有和内部 ref 类。

有关更多信息，请参见 [模板 ref 类](../cppcx/template-ref-classes-c-cx.md)中定义的接口的私有 C++ 特定实现。

### <a name="interfaces"></a>接口

Windows 运行时接口定义一组公共属性、 方法和 ref 类或 ref 结构必须实现如果从接口继承的事件。

有关详细信息，请参阅[接口](../cppcx/interfaces-c-cx.md)。

### <a name="enums"></a>枚举

Windows 运行时中的枚举类类似于中的范围的枚举C++。 基础类型为 int32（除非应用 [标志] 特性，此情况下的基础类型为 uint32）。

有关更多信息，请参见 [枚举](../cppcx/enums-c-cx.md)中定义的接口的私有 C++ 特定实现。

### <a name="delegates"></a>委托

在 Windows 运行时委托是类似于中的 std:: function 对象C++。 它是特殊的 ref 类，用于调用具有兼容签名的客户端提供的函数。  委托是最常用的 Windows 运行时中作为事件的类型。

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

属性是可以应用于任何 Windows 运行时类型或类型成员，并且可以在运行时检查的元数据值。 Windows 运行时定义一组中的常见特性`Windows::Foundation::Metadata`命名空间。 用户定义公共接口上的属性不在此版本中支持由 Windows 运行时。

## <a name="api-deprecation"></a>API 弃用

介绍如何将公共 Api 标记为通过使用 Windows 运行时系统类型使用的同一特性已弃用。

有关详细信息，请参阅[弃用的类型和成员](../cppcx/deprecating-types-and-members-c-cx.md)。

## <a name="see-also"></a>请参阅

[VisualC++语言参考](../cppcx/visual-c-language-reference-c-cx.md)
