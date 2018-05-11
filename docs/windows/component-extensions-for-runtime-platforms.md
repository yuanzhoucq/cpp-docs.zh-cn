---
title: 运行时平台的组件扩展 |Microsoft 文档
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
- Visual C++, keywords
- keywords [C++]
- Managed Extensions for C++, replacement syntax
ms.assetid: 1e400ee6-3ac9-4910-a608-9d3d5993e423
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: e60a1285f54de6b1cbfe311d4d9cbbc547785176
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/08/2018
---
# <a name="component-extensions-for-runtime-platforms"></a>适用于运行时平台的组件扩展
Visual C++ 提供多种语言扩展，可帮助你面向运行时平台编程。 通过使用 C + + /CX 中，你可以编程通用 Windows 平台应用程序和编译为本机代码的组件。 虽然你可以通过针对 Windows 运行时 COM 接口直接编程来创建通用 Windows 平台应用程序，通过使用 C + + /CX 中，你可以使用构造函数、 异常和其他现代 c + + 编程习语。 若要启用.NET 平台上的托管的执行环境中的 c + + 编程，你可以使用 C + + /cli CLI。  
  
 **两个运行时，一组扩展**  
  
 C + + /cli CX 是子集的 C + + /cli CLI。 扩展的共有的 C + + /CX 和 C + + /cli CLI，语义取决于你面向的公共语言运行时 (CLR) 或 Windows 运行时。 若要编译应用程序在 Windows 运行时上运行，指定 **/ZW**编译器选项。 若要对其进行编译在 CLR 上运行，指定 **/clr**编译器选项。 当使用 Visual Studio 创建项目时，将自动设置这些开关。  
  
 有关如何在 c + + 中创建通用 Windows 平台应用程序的详细信息，请参阅[路线图 for Windows Runtime 应用程序使用 c + +](http://msdn.microsoft.com/library/windows/apps/hh700360.aspx)。  
  
 C + + /cli CLI 扩展 ISO/ANSI c + + 标准，并定义在 Ecma C + + /cli CLI 标准。 有关详细信息，请参阅[.NET 编程使用 C + + /cli （Visual c + +）](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)。  
  
## <a name="data-type-keywords"></a>数据类型关键字  
 语言扩展包括*聚合关键字*，这类关键字的用空格分隔的两个标记组成。 标记单独使用时可能表示一种含义，一起使用时可能表示另一种含义。 例如，单词“ref”是一个普通的标识符，单词“class”是一个声明本机类的关键字。 但当将这些单词组合成`ref class`，得到的聚合关键字声明的实体中被称为*运行时类*。  
  
 扩展还包括*上下文相关*关键字。 某个关键字被视为区分上下文，即表示其语义取决于包含它的语句类型及其在该语句中的位置。 例如，标记“property”既可以是标识符，也可以声明特殊类型的公共类成员。  
  
 下表列出了 C++ 语言扩展中的关键字。  
  
|关键字|区分上下文|目标|参考|  
|-------------|-----------------------|-------------|---------------|  
|`ref class`<br /><br /> `ref struct`|否|声明类。|[类和结构](../windows/classes-and-structs-cpp-component-extensions.md)|  
|`value class`<br /><br /> `value struct`|否|声明值类。|[类和结构](../windows/classes-and-structs-cpp-component-extensions.md)|  
|`interface class`<br /><br /> `interface struct`|否|声明接口。|[接口类](../windows/interface-class-cpp-component-extensions.md)|  
|`enum class`<br /><br /> `enum struct`|否|声明枚举。|[枚举类](../windows/enum-class-cpp-component-extensions.md)|  
|`property`|是|声明属性。|[属性](../windows/property-cpp-component-extensions.md)|  
|`delegate`|是|声明委托。|[委托（C++ 组件扩展）](../windows/delegate-cpp-component-extensions.md)|  
|`event`|是|声明事件。|[event](../windows/event-cpp-component-extensions.md)|  
  
## <a name="override-specifiers"></a>重写说明符  
 可以使用下列关键字来限定派生的替代行为。 虽然 `new` 关键字不是 C++ 的扩展，但仍列于此处，因为它可以在附加上下文中使用。 某些说明符还可用于本机编程。 有关详细信息，请参阅[如何： 在本机编译中声明重写说明符 (C + + /cli CLI)](../dotnet/how-to-declare-override-specifiers-in-native-compilations-cpp-cli.md)。  
  
|关键字|区分上下文|目标|参考|  
|-------------|-----------------------|-------------|---------------|  
|`abstract`|是|指示函数或类是抽象的。|[abstract](../windows/abstract-cpp-component-extensions.md)|  
|`new`|否|指示函数不替代基类版本。|[新 (新 vtable 中的槽）](../windows/new-new-slot-in-vtable-cpp-component-extensions.md)|  
|`override`|是|指示方法必须替代基类版本。|[override](../windows/override-cpp-component-extensions.md)|  
|`sealed`|是|防止类用作基类。|[sealed](../windows/sealed-cpp-component-extensions.md)|  
  
## <a name="keywords-for-generics"></a>泛型关键字  
 已添加下列关键字来支持泛型类型。 有关详细信息，请参阅[泛型](../windows/generics-cpp-component-extensions.md)。  
  
|关键字|区分上下文|目标|  
|-------------|-----------------------|-------------|  
|`generic`|否|声明泛型类型。|  
|`where`|是|指定应用于泛型类型参数的约束。|  
  
## <a name="miscellaneous-keywords"></a>杂项关键字  
 C++ 扩展中已添加下列关键字。  
  
|关键字|区分上下文|目标|参考|  
|-------------|-----------------------|-------------|---------------|  
|`finally`|是|指示默认异常处理行为。|[异常处理](../windows/exception-handling-cpp-component-extensions.md)|  
|`for each, in`|否|枚举集合元素。|[for each, in](../dotnet/for-each-in.md)|  
|`gcnew`|否|分配垃圾回收堆上的类型。 而不是使用 `new` 和 `delete`。|[ref new、 gcnew](../windows/ref-new-gcnew-cpp-component-extensions.md)|  
|`ref new`|是|分配 Windows 运行时类型。 而不是使用 `new` 和 `delete`。|[ref new、 gcnew](../windows/ref-new-gcnew-cpp-component-extensions.md)|  
|`initonly`|是|指示只能在声明时或在静态构造函数中初始化成员。|[initonly (C++/CLI)](../dotnet/initonly-cpp-cli.md)|  
|`literal`|是|创建文本变量。|[文本](../windows/literal-cpp-component-extensions.md)|  
|`nullptr`|否|指示图柄或指针不指向对象。|[nullptr](../windows/nullptr-cpp-component-extensions.md)|  
  
## <a name="template-constructs"></a>模板构造  
 下列语言构造作为模板而非关键字实现。 如果指定 **/ZW**编译器选项，它们在定义`lang`命名空间。 如果指定 **/clr**编译器选项，它们在定义`cli`命名空间。  
  
|关键字|目标|参考|  
|-------------|-------------|---------------|  
|`array`|声明数组。|[数组](../windows/arrays-cpp-component-extensions.md)|  
|`interior_ptr`|（仅限 CLR）指向引用类型中的数据。|[interior_ptr (C++/CLI)](../windows/interior-ptr-cpp-cli.md)|  
|`pin_ptr`|（仅限 CLR）指向 CLR 引用类型以便暂时抑制垃圾回收系统。|[pin_ptr (C++/CLI)](../windows/pin-ptr-cpp-cli.md)|  
|`safe_cast`|确定并执行运行时类型的最佳转换方法。|[safe_cast](../windows/safe-cast-cpp-component-extensions.md)|  
|`typeid`|（仅限 CLR）检索用于描述给定类型或对象的 <xref:System.Type?displayProperty=fullName> 对象。|[typeid](../windows/typeid-cpp-component-extensions.md)|  
  
## <a name="declarators"></a>声明符  
 下列类型声明符指示运行时自动管理已分配对象的生存期和删除。  
  
|运算符|目标|参考|  
|--------------|-------------|---------------|  
|`^`|声明的对象; 句柄即，不再可用时将自动删除的 Windows 运行时或 CLR 对象的指针。|[对象句柄运算符 (^)](../windows/handle-to-object-operator-hat-cpp-component-extensions.md)|  
|`%`|声明跟踪引用;即，不再可用时将自动删除的 Windows 运行时或 CLR 对象的引用。|[跟踪引用运算符](../windows/tracking-reference-operator-cpp-component-extensions.md)|  
  
## <a name="additional-constructs-and-related-topics"></a>其他构造和相关主题  
 本节列出了其他编程构造以及与 CLR 相关的主题。  
  
|主题|描述|  
|-----------|-----------------|  
|[__identifier (C++/CLI)](../windows/identifier-cpp-cli.md)|（Windows 运行时和 CLR）可以用作标识符的关键字的使用。|  
|[变量自变量列表 (...) (C++/CLI)](../windows/variable-argument-lists-dot-dot-dot-cpp-cli.md)|（Windows 运行时和 CLR）允许函数采用数量可变的自变量。|  
|[对应于 C++ 本机类型的 .NET Framework 类型 (C++/CLI)](../dotnet/dotnet-framework-equivalents-to-cpp-native-types-cpp-cli.md)|列出替代 C++ 整型类型的 CLR 类型。|  
|[appdomain](../cpp/appdomain.md) `__declspec`修饰符|`__declspec` 修饰符规定每个 appdomain 都存在静态和全局变量。|  
|[/Clr 下的 C 样式强制转换 (C + + /cli CLI)](../windows/c-style-casts-with-clr-cpp-cli.md)|描述如何解释 C 样式转换。|  
|[__clrcall](../cpp/clrcall.md)调用约定|指示符合 CLS 的调用约定。|  
|`__cplusplus_cli`|[预定义宏](../preprocessor/predefined-macros.md)|  
|[自定义特性](../windows/custom-attributes-cpp.md)|描述如何定义自己的 CLR 属性。|  
|[异常处理](../windows/exception-handling-cpp-component-extensions.md)|概述异常处理。|  
|[显式重写](../windows/explicit-overrides-cpp-component-extensions.md)|演示成员函数如何替代任意成员。|  
|[友元程序集 (C++)](../dotnet/friend-assemblies-cpp.md)|讨论客户端程序集如何访问程序集组件中的所有类型。|  
|[装箱](../windows/boxing-cpp-component-extensions.md)|演示值类型进行装箱的条件。|  
|[编译器支持类型特征](../windows/compiler-support-for-type-traits-cpp-component-extensions.md)|讨论如何在编译时检测类型的特征。|  
|[managed、 unmanaged](../preprocessor/managed-unmanaged.md)杂注|演示 managed 和 unmanaged 函数如何共存于同一模块中。|  
|[进程](../cpp/process.md)`__declspec`修饰符|`__declspec` 修饰符规定每个 process 都存在静态和全局变量。|  
|[反射 (C++/CLI)](../dotnet/reflection-cpp-cli.md)|演示运行时类型信息的 CLR 版本。|  
|[字符串](../windows/string-cpp-component-extensions.md)|讨论编译器如何将字符串文本转换为 <xref:System.String>。|  
|[类型转发 (C++/CLI)](../windows/type-forwarding-cpp-cli.md)|允许将一个传送程序集中的类型移动到另一个程序集，从而使客户端代码无需重新编译。|  
|[用户定义的特性](../windows/user-defined-attributes-cpp-component-extensions.md)|演示用户定义的属性。|  
|[#using 指令](../preprocessor/hash-using-directive-cpp.md)|导入外部程序集。|  
|[XML 文档](../ide/xml-documentation-visual-cpp.md)|使用解释基于 XML 的代码文档[/doc （处理文档注释） （C/c + +）](../build/reference/doc-process-documentation-comments-c-cpp.md)|  
  
## <a name="see-also"></a>请参阅  
 [.NET 编程使用 C + + /cli （Visual c + +）](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)   
 [本机和 .NET 的互操作性](../dotnet/native-and-dotnet-interoperability.md)