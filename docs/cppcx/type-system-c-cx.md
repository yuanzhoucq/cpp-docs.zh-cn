---
title: "类型系统 (C++/CX) | Microsoft Docs"
ms.custom: ""
ms.date: "02/03/2017"
ms.prod: "windows-client-threshold"
ms.technology: ""
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b67bee8a-b526-4872-969e-ef22724e88fe
caps.latest.revision: 28
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
caps.handback.revision: 28
---
# 类型系统 (C++/CX)
通过使用 [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)]体系结构，你可以用 [!INCLUDE[cppwrt_short](../cppcx/includes/cppwrt-short-md.md)]、Visual Basic、Visual C\# 和 JavaScript 编写直接访问 Windows API 并与其他 [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)]应用和组件互操作的应用和组件。 用 C\+\+ 编写的 [!INCLUDE[win8_appname_long](../cppcx/includes/win8-appname-long-md.md)]应用编译为直接在 CPU 中执行的本机代码。 用 C\# 或 Visual Basic 编写的 [!INCLUDE[win8_appname_long](../cppcx/includes/win8-appname-long-md.md)]应用程序编译为 Microsoft 中间语言 \(MSIL\) 并在公共语言运行时 \(CLR\) 中执行。 用 JavaScript 编写的 [!INCLUDE[win8_appname_long](../cppcx/includes/win8-appname-long-md.md)]应用程序在一个运行时环境中执行。[!INCLUDE[wrt](../cppcx/includes/wrt-md.md)]操作系统组件本身用 C\+\+ 编写并作为本机代码运行。 所有这些组件和 [!INCLUDE[win8_appname_long](../cppcx/includes/win8-appname-long-md.md)]应用程序都直接通过 [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)]应用程序二进制接口 \(ABI\) 通信。  
  
 为在现代 C\+\+ 惯例中实现对 [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)]的支持，Microsoft 创建了 [!INCLUDE[cppwrt](../cppcx/includes/cppwrt-md.md)] \([!INCLUDE[cppwrt_short](../cppcx/includes/cppwrt-short-md.md)]\)。[!INCLUDE[cppwrt_short](../cppcx/includes/cppwrt-short-md.md)] 提供基础 [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)]类型的内置基类型和实现，这些基础类型使得 C\+\+ 应用程序和组件能够通过 ABI 与用其他语言编写的应用程序通信。 可以使用任何 [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)]类型，或者创建可供其他 [!INCLUDE[win8_appname_long](../cppcx/includes/win8-appname-long-md.md)]应用程序和组件使用的类、结构、接口以及其他用户定义的类型。 只要没有公共可访问性，用 [!INCLUDE[win8_appname_long](../cppcx/includes/win8-appname-long-md.md)] 编写的 [!INCLUDE[cppwrt_short](../cppcx/includes/cppwrt-short-md.md)]应用程序也能使用常规 C\+\+ 类和结构。  
  
 有关 C\+\+\/CX 语言投影的深度讨论以及它在后台如何工作，请参阅以下博客帖子：  
  
1.  [C\+\+\/CX \[n\] 的第 0 部分：简介](http://blogs.msdn.com/b/vcblog/archive/2012/08/29/cxxcxpart00anintroduction.aspx)  
  
2.  [C\+\+\/CX \[n\] 的第 0 部分：简介](http://blogs.msdn.com/b/vcblog/archive/2012/08/29/cxxcxpart00anintroduction.aspx)  
  
3.  [C\+\+\/CX \[n\] 的第 2 部分：带尖角符号的类型](http://blogs.msdn.com/b/vcblog/archive/2012/09/17/cxxcxpart02typesthatwearhats.aspx)  
  
4.  [C\+\+\/CX \[n\] 的第 3 部分：正在构造](http://blogs.msdn.com/b/vcblog/archive/2012/10/05/cxxcxpart03underconstruction.aspx)  
  
5.  [C\+\+\/CX \[n\] 的第 4 部分：静态成员函数](http://blogs.msdn.com/b/vcblog/archive/2012/10/19/cxxcxpart04staticmemberfunctions.aspx)  
  
## Windows 元数据 \(.winmd\) 文件  
 编译用 C\+\+ 编写的 [!INCLUDE[win8_appname_long](../cppcx/includes/win8-appname-long-md.md)]应用程序时，编译器生成本机代码的可执行文件，以及包含公共 [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)]类型（包括类、结构、枚举、接口、参数化接口和委托）描述的单独 Windows 元数据 \(.winmd\) 文件。 元数据的格式类似于在 .NET Framework 程序集中使用的格式。  在 C\+\+ 组件中，.winmd 文件只包含元数据；可执行代码位于单独的文件中。 这属于 Windows 附带的 [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)]组件的情形。 WinMD 文件名必须与源代码中的根命名空间的前缀匹配或为该前缀。 （对于 .NET Framework 语言，.winmd 文件同时包含代码和元数据，正如一个 .NET Framework 程序集。）  
  
 .winmd 文件中的元数据表示你的代码的已发布图面。 发布类型对其他 [!INCLUDE[win8_appname_long](../cppcx/includes/win8-appname-long-md.md)]可见，无论这些应用程序是用什么语言编写的。 因此，元数据或你的发布代码都只能包含 [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)]类型系统指定的类型。 特定于 C\+\+ 的语言构造（如规则类、数组、模板或 STL 容器）不能在元数据中发布，因为 Javascript 或 C\# 客户端应用程序不知道如何处理它们。  
  
 类型或方法在元数据中是否可见取决于应用于它们的可访问性修饰符。 若要可见，必须在命名空间中声明类型，而且必须声明为公共类型。 允许在你的代码中将非公共 ref 类作为内部帮助程序类型，它在元数据中正好不可见。 即使在公共 ref 类中，也非所有成员都必然可见。 下表列出了公共 ref 类中 C\+\+访问说明符与 [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)]元数据可见性之间的关系：  
  
|||  
|-|-|  
|**在元数据中发布**|**未在元数据中发布**|  
|public|private|  
|protected|internal|  
|公共受保护|私有受保护|  
  
 可以使用**“对象浏览器”**查看 .winmd 文件的内容。 Windows 附带的 [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)]组件在 Windows.winmd 文件中。 default.winmd 文件包含 [!INCLUDE[cppwrt_short](../cppcx/includes/cppwrt-short-md.md)] 中使用的基础类型，platform.winmd 包含来自平台命名空间的其他类型。 默认情况下，这三个 .winmd 文件包括在 [!INCLUDE[win8_appname_long](../cppcx/includes/win8-appname-long-md.md)]应用程序的每个 C\+\+ 项目中。  
  
> [!TIP]
>  [Platform::Collections 命名空间](../cppcx/platform-collections-namespace.md) 中的类型没有出现在 .winmd 文件中，因为它们不是公共类型。 它们是 `Windows::Foundation::Collections` 中定义的接口的私有 C\+\+ 特定实现。 用 JavaScript 或 C\# 编写的 [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)]应用程序不知道 [Platform::Collections::Vector 类](../cppcx/platform-collections-vector-class.md) 是什么，但是它可以使用 `Windows::Foundation::Collections::IVector`。`Platform::Collections` 类型在 collection.h 中定义。  
  
## [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)] 中的 [!INCLUDE[cppwrt_short](../cppcx/includes/cppwrt-short-md.md)]类型系统  
 以下各节介绍 [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)]类型系统的主要功能，以及 [!INCLUDE[cppwrt_short](../cppcx/includes/cppwrt-short-md.md)] 如何支持它们。  
  
### 命名空间  
 必须在命名空间内声明所有 [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)]类型，Windows API 本身按命名空间组织。 .winmd 文件必须具有和根命名空间相同的名称。 例如，名为 A.B.C.MyClass 的类只有在名为 A.winmd 或 A.B.winmd 或 A.B.C.winmd 的元数据文件中定义后才能实例化。 DLL 的名称不必与 .winmd 文件名匹配。  
  
 Windows API 本身已重创为按命名空间组织的分解类库。  所有 [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)]组件都在 Windows.\* 命名空间声明。  
  
 有关更多信息，请参见[命名空间和类型可见性](../cppcx/namespaces-and-type-visibility-c-cx.md)。  
  
### 基础类型  
 [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)]定义以下基础类型：UInt8、Int16、UInt16、UInt32、Int32、Int64、UInt64、单精度、双精度、Char16、布尔值和字符串。[!INCLUDE[cppwrt_short](../cppcx/includes/cppwrt-short-md.md)] 在其默认命名空间中支持基本数值类型，如 uint16、uint32、uint64、int16、int32、int64、float32、float64 和 char16。 布尔值和字符串也在平台命名空间中定义。  
  
 [!INCLUDE[cppwrt_short](../cppcx/includes/cppwrt-short-md.md)] 还定义 uint8，它等效于 `unsigned char`（在 [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)]中不受支持，也不能用于公共 API）。  
  
 可通过将基础类型包装在 [Platform::IBox Interface](../cppcx/platform-ibox-interface.md) 接口中来使其可以为 null。 有关更多信息，请参见[值类和结构](../cppcx/value-classes-and-structs-c-cx.md)。  
  
 有关基础类型的更多信息，请参见[基本类型](../cppcx/fundamental-types-c-cx.md)。  
  
### 字符串  
 [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)]字符串是 16 位 UNICODE 字符的一个不可变序列。[!INCLUDE[wrt](../cppcx/includes/wrt-md.md)]字符串表现为 `Platform::String^`。 此类为字符串构造、处理和在 `wchar_t` 间来回转换提供方法。  
  
 有关更多信息，请参见[字符串](../cppcx/strings-c-cx.md)。  
  
### 数组  
 [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)]支持任何类型的一维数组。 不支持数组的数组。  在 [!INCLUDE[cppwrt_short](../cppcx/includes/cppwrt-short-md.md)] 中，[!INCLUDE[wrt](../cppcx/includes/wrt-md.md)]数组被投影为 [Platform::Array 类](../cppcx/platform-array-class.md)。  
  
 有关更多信息，请参见[Array 和 WriteOnlyArray](../cppcx/array-and-writeonlyarray-c-cx.md)  
  
### Ref 类和结构  
 [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)]类在 [!INCLUDE[cppwrt_short](../cppcx/includes/cppwrt-short-md.md)] 中表现为 ref 类或 ref 结构，因为它们通过引用复制。 ref 类和 ref 结构的内存管理通过引用计数透明地处理。 当对对象的最后引用超出范围时，对象被销毁。 ref 类或 ref 结构可以：  
  
-   作为成员构造函数、方法、属性和事件而包含。 这些成员可以具有公共、私有、受保护或内部可访问性。  
  
-   可以包含私有嵌套枚举、结构或类定义。  
  
-   可直接从基类继承，并且可以实现任意数量的接口。 所有 ref 类都可以隐式转换为 [Platform::Object 类](../cppcx/platform-object-class.md)，并且可重写其虚拟方法，如 [Object::ToString](../cppcx/object-tostring-method-c-cx.md)。  
  
 为防止进一步派生，必须将具有公共构造函数的 ref 类声明为密封类。  
  
 有关更多信息，请参见[Ref 类和结构](../cppcx/ref-classes-and-structs-c-cx.md)  
  
### 值类和结构  
 值类或值结构表示基本数据结构，它们只包含字段，这可能是值类、值结构或类型 `Platform::String^`。  值结构和值类通过值复制。  
  
 可通过将值结构包装在 IBox 接口中来使其可以为 null。  
  
 有关更多信息，请参见[值类和结构](../cppcx/value-classes-and-structs-c-cx.md)。  
  
### 分部类  
 分部类功能可使你对多个文件定义一个类。 这主要用于使代码生成工具（如 XAML 编辑器）能够在不影响你所编辑文件的情况下修改一个文件。  
  
 有关更多信息，请参见[分部类](../cppcx/partial-classes-c-cx.md)  
  
### 属性  
 属性是任何 [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)]类型的一个公共数据成员并实现为 get\/set 方法对。 客户端代码访问属性，就好像属性是一个公共字段。 不需要自定义 get 或 set 代码的属性称为*平常属性*，无需显式 get 或 set 方法即可声明它们。  
  
 有关更多信息，请参见[属性](../cppcx/properties-c-cx.md)。  
  
### [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)] 中的 [!INCLUDE[cppwrt_short](../cppcx/includes/cppwrt-short-md.md)]集合  
 [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)]为每种语言按自己的方式实现的集合类型定义一组接口。[!INCLUDE[cppwrt_short](../cppcx/includes/cppwrt-short-md.md)] 在 [Platform::Collections::Vector 类](../cppcx/platform-collections-vector-class.md)、[Platform::Collections::Map 类](../cppcx/platform-collections-map-class.md)中提供实现，并提供其他相关具体集合类型，这些类型与它们的标准模板库 \(STL\) 对等项兼容。  
  
 有关更多信息，请参见[集合](../cppcx/collections-c-cx.md)。  
  
### 模板 ref 类  
 可以模板化和专用化私有和内部 ref 类。  
  
 有关更多信息，请参见[模板 ref 类](../cppcx/template-ref-classes-c-cx.md)。  
  
### 接口  
 如果一个 ref 类或 ref 结构从 [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)]接口继承，则该接口定义该类或结构必须实现的一组公共属性、方法和事件。  
  
 有关更多信息，请参见[接口](../cppcx/interfaces-c-cx.md)。  
  
### 枚举  
 [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)]中的枚举类类似于 C\+\+ 中的范围枚举。 基础类型为 int32（除非应用 \[标志\] 特性，此情况下的基础类型为 uint32）。  
  
 有关更多信息，请参见[枚举](../cppcx/enums-c-cx.md)。  
  
### 委托  
 [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)]中的委托类似于 C\+\+ 中的 std::function 对象。 它是特殊的 ref 类，用于调用具有兼容签名的客户端提供的函数。  委托通常在 [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)]中用作事件类型。  
  
 有关更多信息，请参见[委托](../cppcx/delegates-c-cx.md)。  
  
### 异常  
 在 C\+\+\/CX 中，可以捕获自定义异常类型、[std::exception](../Topic/exception%20Class1.md) 类型和 [Platform::Exception](../cppcx/platform-exception-class.md) 类型。  
  
 有关更多信息，请参见[异常](../cppcx/exceptions-c-cx.md)。  
  
### 事件  
 事件是其类型为委托类型的 ref 类或 ref 结构中的公共成员。 事件只能被调用，即，被所属类触发。 但是，客户端代码可以提供自己的函数（即事件处理程序）并在所属类触发事件时被调用。  
  
 有关更多信息，请参见[事件](../cppcx/events-c-cx.md)。  
  
### 强制转换  
 C\+\+\/CX 支持标准 C\+\+ 强制转换运算符 [static\_cast](../cpp/static-cast-operator.md)、[dynamic\_cast](../cpp/dynamic-cast-operator.md) 和 [reinterpret\_cast](../cpp/reinterpret-cast-operator.md)，以及特定于 C\+\+\/CX 的 [safe\_cast](../Topic/safe_cast%20\(C++%20Component%20Extensions\).md) 运算符。  
  
 有关更多信息，请参见[强制转换](../cppcx/casting-c-cx.md)。  
  
### 装箱  
 装箱变量是在需要引用语义的情况下，包装在引用类型中的值类型。  
  
 有关更多信息，请参见[装箱](../cppcx/boxing-c-cx.md)。  
  
### 特性  
 特性是可以应用于任何 [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)]类型或类型成员并且可以在运行时检查的元数据值。[!INCLUDE[wrt](../cppcx/includes/wrt-md.md)]在 `Windows::Foundation::Metadata` 命名空间中定义了一组常见特性。 在此版本中，[!INCLUDE[wrt](../cppcx/includes/wrt-md.md)]不支持公共接口上的用户定义的特性。  
  
## API 弃用  
 描述如何使用由 [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)]系统类型使用的同一特性将公共 API 标记为已弃用。  
  
 有关更多信息，请参见[要弃用的类型和成员](../cppcx/deprecating-types-and-members-c-cx.md)。  
  
## 请参阅  
 [Visual C\+\+ 语言参考](../cppcx/visual-c-language-reference-c-cx.md)