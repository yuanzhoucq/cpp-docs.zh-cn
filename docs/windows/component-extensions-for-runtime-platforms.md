---
title: "适用于运行时平台的组件扩展 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "关键字 [C++]"
  - "C++ 托管扩展, 替代语法"
  - "Visual C++, 关键字"
  - "新增功能 [C++], 关键字"
  - "新增功能 [C++], 语言功能"
ms.assetid: 1e400ee6-3ac9-4910-a608-9d3d5993e423
caps.latest.revision: 77
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 77
---
# 适用于运行时平台的组件扩展
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Visual C\+\+ 提供多种语言扩展，可帮助你面向运行时平台编程。  通过使用 [!INCLUDE[cppwrt](../build/reference/includes/cppwrt_md.md)] \([!INCLUDE[cppwrt_short](../build/reference/includes/cppwrt_short_md.md)]\)，可以对编译为本机代码的 [!INCLUDE[win8_appname_long](../build/includes/win8_appname_long_md.md)]应用和组件编程。  虽然可以通过面向 [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)] COM 接口直接编程来创建 [!INCLUDE[win8_appname_long](../build/includes/win8_appname_long_md.md)]应用，但是，通过使用 [!INCLUDE[cppwrt_short](../build/reference/includes/cppwrt_short_md.md)]，可以使用构造函数、异常和其他现代 C\+\+ 编程习语。  要在 .NET 平台上的托管执行环境中启用 C\+\+ 编程，可以使用 [!INCLUDE[cppcli](../build/reference/includes/cppcli_md.md)]。  
  
 **两个运行时，一组扩展**  
  
 [!INCLUDE[cppwrt_short](../build/reference/includes/cppwrt_short_md.md)] 是 [!INCLUDE[cppcli](../build/reference/includes/cppcli_md.md)] 的子集。  对于 [!INCLUDE[cppwrt_short](../build/reference/includes/cppwrt_short_md.md)] 和 [!INCLUDE[cppcli](../build/reference/includes/cppcli_md.md)] 共有的扩展，其语义取决于是面向公共语言运行时 \(CLR\) 还是面向 [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)]。  要将应用编译为在 [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)]上运行，请指定 **\/ZW** 编译器选项。  要将其编译为在 CLR 上运行，请指定 **\/clr** 编译器选项。  当使用 Visual Studio 创建项目时，将自动设置这些开关。  
  
 有关如何在 C\+\+ 中创建 [!INCLUDE[win8_appname_long](../build/includes/win8_appname_long_md.md)]应用的详细信息，请参阅[使用 C\+\+ 的 Windows 运行时应用的路线图](http://msdn.microsoft.com/library/windows/apps/hh700360.aspx)。  
  
 [!INCLUDE[cppcli](../build/reference/includes/cppcli_md.md)] 扩展了 ISO\/ANSI C\+\+ 标准，并在 Ecma [!INCLUDE[cppcli](../build/reference/includes/cppcli_md.md)] 标准下定义。  有关详细信息，请参阅 [使用 C\+\+\/CLI 进行 .NET 编程](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)。  
  
## 数据类型关键字  
 语言扩展包括*“聚合关键字”*，这类关键字由使用空格分隔的两个标记组成。  标记单独使用时可能表示一种含义，一起使用时可能表示另一种含义。  例如，单词“ref”是一个普通的标识符，单词“class”是一个声明本机类的关键字。  但将这两个单词组合成 `ref class` 时，得到的聚合关键字则声明一个称为*“运行时类”*的实体。  
  
 扩展还包括*“区分上下文”*的关键字。  某个关键字被视为区分上下文，即表示其语义取决于包含它的语句类型及其在该语句中的位置。  例如，标记“property”既可以是标识符，也可以声明特殊类型的公共类成员。  
  
 下表列出了 C\+\+ 语言扩展中的关键字。  
  
|关键字|区分上下文|用途|引用|  
|---------|-----------|--------|--------|  
|`ref class`<br /><br /> `ref struct`|否|声明类。|[类和结构 \(托管\)](../windows/classes-and-structs-cpp-component-extensions.md)|  
|`value class`<br /><br /> `value struct`|否|声明值类。|[类和结构 \(托管\)](../windows/classes-and-structs-cpp-component-extensions.md)|  
|`interface class`<br /><br /> `interface struct`|否|声明接口。|[接口类](../windows/interface-class-cpp-component-extensions.md)|  
|`enum class`<br /><br /> `enum struct`|否|声明枚举。|[enum class](../windows/enum-class-cpp-component-extensions.md)|  
|`property`|是|声明属性。|[属性](../windows/property-cpp-component-extensions.md)|  
|`delegate`|是|声明委托。|[委托](../windows/delegate-cpp-component-extensions.md)|  
|`event`|是|声明事件。|[event](../windows/event-cpp-component-extensions.md)|  
  
## 重写说明符  
 可以使用下列关键字来限定派生的替代行为。  虽然 `new` 关键字不是 C\+\+ 的扩展，但仍列于此处，因为它可以在附加上下文中使用。  某些说明符还可用于本机编程。  有关详细信息，请参阅[如何：在本机编译中声明重写说明符](../dotnet/how-to-declare-override-specifiers-in-native-compilations-cpp-cli.md)。  
  
|关键字|区分上下文|用途|引用|  
|---------|-----------|--------|--------|  
|`abstract`|是|指示函数或类是抽象的。|[abstract](../windows/abstract-cpp-component-extensions.md)|  
|`new`|否|指示函数不替代基类版本。|[新的 \(在 vtable 的新槽\)](../windows/new-new-slot-in-vtable-cpp-component-extensions.md)|  
|`override`|是|指示方法必须替代基类版本。|[override](../windows/override-cpp-component-extensions.md)|  
|`sealed`|是|防止类用作基类。|[sealed](../windows/sealed-cpp-component-extensions.md)|  
  
## 泛型关键字  
 已添加下列关键字来支持泛型类型。  有关详细信息，请参阅[泛型](../windows/generics-cpp-component-extensions.md)。  
  
|关键字|区分上下文|目标|  
|---------|-----------|--------|  
|`generic`|否|声明泛型类型。|  
|`where`|是|指定应用于泛型类型参数的约束。|  
  
## 杂项关键字  
 C\+\+ 扩展中已添加下列关键字。  
  
|关键字|区分上下文|用途|引用|  
|---------|-----------|--------|--------|  
|`finally`|是|指示默认异常处理行为。|[异常处理](../windows/exception-handling-cpp-component-extensions.md)|  
|`for each, in`|否|枚举集合元素。|[for each，in](../dotnet/for-each-in.md)|  
|`gcnew`|否|分配垃圾回收堆上的类型。  而不是使用 `new` 和 `delete`。|[gcnew](../windows/ref-new-gcnew-cpp-component-extensions.md)|  
|`ref new`|是|分配 [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)]类型。  而不是使用 `new` 和 `delete`。|[gcnew](../windows/ref-new-gcnew-cpp-component-extensions.md)|  
|`initonly`|是|指示只能在声明时或在静态构造函数中初始化成员。|[initonly](../dotnet/initonly-cpp-cli.md)|  
|`literal`|是|创建文本变量。|[文本](../windows/literal-cpp-component-extensions.md)|  
|`nullptr`|否|指示图柄或指针不指向对象。|[nullptr](../windows/nullptr-cpp-component-extensions.md)|  
  
## 模板构造  
 下列语言构造作为模板而非关键字实现。  如果指定 **\/ZW** 编译器选项，它们将在 `lang` 命名空间中定义。  如果指定 **\/clr** 编译器选项，它们将在 `cli` 命名空间中定义。  
  
|关键字|用途|引用|  
|---------|--------|--------|  
|`array`|声明数组。|[数组](../windows/arrays-cpp-component-extensions.md)|  
|`interior_ptr`|（仅限 CLR）指向引用类型中的数据。|[interior\_ptr \(C\+\+\/CLI\)](../windows/interior-ptr-cpp-cli.md)|  
|`pin_ptr`|（仅限 CLR）指向 CLR 引用类型以便暂时抑制垃圾回收系统。|[pin\_ptr \(C\+\+\/CLI\)](../windows/pin-ptr-cpp-cli.md)|  
|`safe_cast`|确定并执行运行时类型的最佳转换方法。|[safe\_cast](../windows/safe-cast-cpp-component-extensions.md)|  
|`typeid`|（仅限 CLR）检索用于描述给定类型或对象的 <xref:System.Type?displayProperty=fullName> 对象。|[typeid](../windows/typeid-cpp-component-extensions.md)|  
  
## 声明符  
 下列类型声明符指示运行时自动管理已分配对象的生存期和删除。  
  
|运算符|用途|引用|  
|---------|--------|--------|  
|`^`|声明对象句柄；即，指向 [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)]或 CLR 对象的指针，不再可用时将自动删除。|[对象句柄运算符 \(^\)](../windows/handle-to-object-operator-hat-cpp-component-extensions.md)|  
|`%`|声明跟踪引用；即，对 [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)]或 CLR 对象的引用，不再可用时将自动删除。|[% \(跟踪引用\)](../windows/tracking-reference-operator-cpp-component-extensions.md)|  
  
## 其他构造和相关主题  
 本节列出了其他编程构造以及与 CLR 相关的主题。  
  
|主题|说明|  
|--------|--------|  
|[\_\_identifier](../windows/identifier-cpp-cli.md)|（[!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)]和 CLR）允许使用关键字作为标识符。|  
|[变量参数列表 \(...\) \(C\+\+\/CLI\)](../windows/variable-argument-lists-dot-dot-dot-cpp-cli.md)|（[!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)]和 CLR）允许函数采用数目可变的参数。|  
|[对应于 C\+\+ 本机类型的 .NET Framework 类型](../dotnet/dotnet-framework-equivalents-to-cpp-native-types-cpp-cli.md)|列出替代 C\+\+ 整型类型的 CLR 类型。|  
|[appdomain](../cpp/appdomain.md) `__declspec` 修饰符|`__declspec` 修饰符规定每个 appdomain 都存在静态和全局变量。|  
|[C 风格的强制转换和 \/clr \(C\+\+\/CLI\)](../windows/c-style-casts-with-clr-cpp-cli.md)|描述如何解释 C 样式转换。|  
|[\_\_clrcall](../cpp/clrcall.md) 调用约定|指示符合 CLS 的调用约定。|  
|`__cplusplus_cli`|[预定义的宏](../preprocessor/predefined-macros.md)|  
|[Custom Attributes](../windows/custom-attributes-cpp.md)|描述如何定义自己的 CLR 属性。|  
|[异常处理](../windows/exception-handling-cpp-component-extensions.md)|概述异常处理。|  
|[显式重写](../windows/explicit-overrides-cpp-component-extensions.md)|演示成员函数如何替代任意成员。|  
|[友元程序集 \(C\+\+\)](../dotnet/friend-assemblies-cpp.md)|讨论客户端程序集如何访问程序集组件中的所有类型。|  
|[装箱](../windows/boxing-cpp-component-extensions.md)|演示值类型进行装箱的条件。|  
|[编译器使用类型特征支持](../windows/compiler-support-for-type-traits-cpp-component-extensions.md)|讨论如何在编译时检测类型的特征。|  
|[managed、unmanaged](../preprocessor/managed-unmanaged.md) 杂注|演示 managed 和 unmanaged 函数如何共存于同一模块中。|  
|[进程](../cpp/process.md) `__declspec` 修饰符|`__declspec` 修饰符规定每个 process 都存在静态和全局变量。|  
|[反射](../dotnet/reflection-cpp-cli.md)|演示运行时类型信息的 CLR 版本。|  
|[String](../windows/string-cpp-component-extensions.md)|讨论编译器如何将字符串文本转换为 <xref:System.String>。|  
|[类型转发 \(C\+\+\/CLI\)](../windows/type-forwarding-cpp-cli.md)|允许将一个传送程序集中的类型移动到另一个程序集，从而使客户端代码无需重新编译。|  
|[用户定义的特性](../windows/user-defined-attributes-cpp-component-extensions.md)|演示用户定义的属性。|  
|[\#using 指令](../preprocessor/hash-using-directive-cpp.md)|导入外部程序集。|  
|[XML 文档](../ide/xml-documentation-visual-cpp.md)|使用 [\/doc（处理文档注释）](../build/reference/doc-process-documentation-comments-c-cpp.md) 解释基于 XML 的代码文档|  
  
## 请参阅  
 [使用 C\+\+\/CLI 进行 .NET 编程](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)   
 [本机和 .NET 的互操作性](../dotnet/native-and-dotnet-interoperability.md)