---
title: ref class 和 ref struct（C++/CLI 和 C++/CX）
ms.date: 10/12/2018
ms.topic: reference
helpviewer_keywords:
- ref class keyword [C++]
- value class keyword [C++]
- value struct keyword [C++]
- ref struct keyword [C++]
ms.assetid: 5c360764-b229-49c6-9357-66213afbc372
ms.openlocfilehash: fcc50109ce521e005e32a8c19b13aabe2230989b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "65516182"
---
# <a name="ref-class-and-ref-struct--ccli-and-ccx"></a>ref class 和 ref struct（C++/CLI 和 C++/CX）

ref class 或 ref struct 扩展声明了对象生存期受自动管理的类或结构。 当对象不再可访问或超出范围时，就会释放内存。

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

class_access<br/>
（可选）程序集外部类或结构的可访问性。 可取值为 public 和 private（private 是默认值）。 嵌套类或结构不得包含 class_access 说明符。

*name*<br/>
类或结构的名称。

modifier<br/>
（可选）[abstract](abstract-cpp-component-extensions.md) 和 [sealed](sealed-cpp-component-extensions.md) 是有效修饰符。

inherit_access<br/>
（可选）base_type 的可访问性。 唯一允许的可访问性是 public（public 是默认值）。

base_type<br/>
（可选）基类型。 但是，值类型不能充当基类型。

有关详细信息，请参阅“Windows 运行时”和“公共语言运行时”部分中对此参数的特定语言描述。

### <a name="remarks"></a>备注

使用 ref class 或 value class 声明的对象的默认成员可访问性是 private。 使用 ref struct 或 value struct 声明的对象的默认成员可访问性是 public。

如果引用类型继承自其他引用类型，必须显式重写（使用 [override](override-cpp-component-extensions.md)）或隐藏（使用 [new（vtable 中的新槽）](new-new-slot-in-vtable-cpp-component-extensions.md)）基类中的虚函数。 还必须将派生类函数显式标记为 virtual。

若要在编译时检测类型是 ref class 或 ref struct，还是 value class 或 value struct，请使用 `__is_ref_class (type)`、`__is_value_class (type)` 或 `__is_simple_value_class (type)`。 有关详细信息，请参阅[编译器对类型特征的支持](compiler-support-for-type-traits-cpp-component-extensions.md)。

有关类和结构的详细信息，请参阅

- [实例化类和结构](../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md)

- [参考类型的 C++ 堆栈语义](../dotnet/cpp-stack-semantics-for-reference-types.md)

- [类、结构和联合](../cpp/classes-and-structs-cpp.md)

- [“操作说明：定义和使用类和结构 (C++/CLI)”中的“析构函数和终结器”](../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Destructors_and_finalizers)

- [用户定义的运算符 (C++/CLI)](../dotnet/user-defined-operators-cpp-cli.md)

- [用户定义的转换 (C++/CLI)](../dotnet/user-defined-conversions-cpp-cli.md)

- [如何：包装本机类以供 C# 使用](../dotnet/how-to-wrap-native-class-for-use-by-csharp.md)

- [泛型类 (C++/CLI)](generic-classes-cpp-cli.md)

## <a name="windows-runtime"></a>Windows 运行时

### <a name="remarks"></a>备注

请参阅 [ref class 和 ref struct](../cppcx/ref-classes-and-structs-c-cx.md) 以及 [value class 和 value struct](https://msdn.microsoft.com/library/windows/apps/hh699861.aspx)。

### <a name="parameters"></a>参数

base_type<br/>
（可选）基类型。 ref class 或 ref struct 可以继承自零个或多个接口，也可以继承自零个或一个 ref 类型。 value class 或 value struct 只能继承自零个或多个接口。

如果你使用 ref class 或 ref struct 关键字声明对象，对象是通过指向对象的句柄（即指向对象的引用计数器指针）获得访问。 声明的变量超出范围时，编译器会自动删除基础对象。 当对象在调用中用作参数或存储在变量中时，实际是在传递或存储该对象的句柄。

如果你使用 value class 或 value struct 关键字声明对象，声明的对象的对象生存期不会受到监督。 该对象如同任何其他标准 C++ 类或结构一样。

### <a name="requirements"></a>要求

编译器选项：`/ZW`

## <a name="common-language-runtime"></a>公共语言运行时

### <a name="remarks"></a>备注

下表列出了与“所有运行时”部分中语法的 C++/CLI 专属区别。

### <a name="parameters"></a>参数

base_type<br/>
（可选）基类型。 ref class 或 ref struct 可以继承自零个或多个托管接口，也可以继承自零个或一个 ref 类型。 value class 或 value struct 只能继承自零个或多个托管接口。

ref class 或 ref struct 关键字指示编译器，要在堆上分配类或结构。 当对象在调用中用作参数或存储在变量中时，实际是在传递或存储该对象的引用。

value class 或 value struct 关键字指示编译器，已分配类或结构的值传递给函数或存储在成员中。

### <a name="requirements"></a>要求

编译器选项：`/clr`

## <a name="see-also"></a>请参阅

[ .NET 和 UWP 的组件扩展](component-extensions-for-runtime-platforms.md)