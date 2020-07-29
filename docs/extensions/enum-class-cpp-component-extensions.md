---
title: enum class（C++/CLI 和 C++/CX）
ms.date: 10/12/2018
ms.topic: reference
ms.assetid: 8010fa8c-bad6-45b4-8214-b4db64d7ffe1
ms.openlocfilehash: a1b99cb2265c9a9bdb40a7239a21412123772570
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87219711"
---
# <a name="enum-class--ccli-and-ccx"></a>enum class（C++/CLI 和 C++/CX）

在命名空间范围内声明枚举，该枚举是用户定义的类型，其包含称为枚举数的一组命名常数。

## <a name="all-runtimes"></a>所有运行时

### <a name="remarks"></a>备注

C++/CX 和 C++/CLI 支持 public enum class**** 和 private enum class****，它们与标准 C++ enum class**** 类似，不同之处在于增加了可访问性说明符。 在 /clr**** 下，允许使用 C++11 enum class**** 类型，但会生成警告 C4472，这是为了确保你确认自己确实需要使用 ISO 枚举类型，而不是 C++/CX 和 C++/CLI 类型。 有关 ISO 标准 c + + 关键字的详细信息 **`enum`** ，请参阅[枚举](../cpp/enumerations-cpp.md)。

## <a name="windows-runtime"></a>Windows 运行时

### <a name="syntax"></a>语法

```cpp
      access
      enum class
      enumeration-identifier
      [:underlying-type] { enumerator-list } [var];
accessenum structenumeration-identifier[:underlying-type] { enumerator-list } [var];
```

### <a name="parameters"></a>参数

*access*<br/>
枚举的可访问性，可以是 **`public`** 或 **`private`** 。

*enumeration-identifier*<br/>
枚举的名称。

*underlying-type*<br/>
（可选）枚举的基础类型。

（可选。 仅 Windows 运行时）枚举的基础类型，可以是、、、、、、、 **`bool`** **`char`** `char16` `int16` `uint16` **`int`** `uint32` `int64` 或 `uint64` 。

*枚举器列表*<br/>
以逗号分隔的枚举器名称列表。

每个枚举器的值都是由编译器隐式定义或由表示法*枚举器* `=` *常量表达式*显式定义的常量表达式。 如果隐式定义第一个枚举器，则其值为零。 每个后续的隐式定义的枚举器值是前一个枚举器的值 + 1。

*var*<br/>
（可选）枚举类型的变量的名称。

### <a name="remarks"></a>备注

有关详细信息和示例，请参阅 [枚举](../cppcx/enums-c-cx.md)。

请注意，如果可定义枚举器的值的常数表达式不能由 *underlying-type*表示，则编译器将发出错误消息。  但是，编译器不会报告不适用于基础类型的值的错误。 例如：

- 如果 *underlying-type* 是数字，并且枚举器指定了该类型的最大值，则不会显示下一个隐式定义的枚举值。

- 如果*基础类型*为 **`bool`** ，并且隐式定义了两个以上的枚举器，则不能表示前两个枚举器。

- 如果 *underlying-type* 是 `char16`，且枚举值的范围是从 0xD800 到 0xDFFF，则可显示该值。 但是，该值出现逻辑错误，因为它表示半个 Unicode 代理项对，且不会以分隔形式显示。

### <a name="requirements"></a>要求

编译器选项：`/ZW`

## <a name="common-language-runtime"></a>公共语言运行时

### <a name="syntax"></a>语法

```cpp
      access
      enum class
      name [:type] { enumerator-list } var;
accessenum structname [:type] { enumerator-list } var;
```

### <a name="parameters"></a>参数

*access*<br/>
枚举的可访问性。 可以是 **`public`** 或 **`private`** 。

*枚举器列表*<br/>
枚举中以逗号分隔的标识符（枚举器）列表。

*name*<br/>
枚举的名称。 不允许匿名托管枚举。

*type*<br/>
（可选）identifiers** 的基础类型。 这可以是任何标量类型，如、或的已签名或未签名的版本 **`int`** **`short`** **`long`** 。  **`bool`****`char`** 也允许使用或。

*var*<br/>
（可选）枚举类型的变量的名称。

### <a name="remarks"></a>备注

**enum class** 和 **enum struct** 是等效声明。

有两种枚举：托管或 C++/CX 枚举和标准枚举。

托管或 C++/CX 枚举可能有如下定义，

```cpp
public enum class day {sun, mon };
```

并且在语义上等效于：

```cpp
ref class day {
public:
   static const int sun = 0;
   static const int mon = 1;
};
```

标准枚举可能有如下定义：

```cpp
enum day2 { sun, mon };
```

并且在语义上等效于：

```cpp
static const int sun = 0;
static const int mon = 1;
```

托管枚举器名称 (*identifiers*) 注入到定义枚举的作用域；必须完全限定对枚举器的所有引用 (*name*`::`*identifier*)。  为此，你不能定义匿名托管的枚举。

将标准枚举的枚举器强注入到封闭作用域。  即，如果存在名称与封闭作用域中的枚举器名称相同的另一个符号，则编译器将生成错误。

在 Visual Studio 2002 和 Visual Studio 2003 中，枚举器是弱插入（在封闭作用域中可见，除非还有同名的标识符）。

如果定义了标准 c + + 枚举（无 **`class`** 或 **`struct`** ），则使用进行编译 `/clr` 将导致枚举编译为托管枚举。  枚举仍然具有非托管枚举的语义。  请注意，编译器插入特性 `Microsoft::VisualC::NativeEnumAttribute`，以标识程序员要将枚举变为本机枚举的意图。  其他编译器只会将标准枚举视为托管枚举。

使用 `/clr` 编译的已命名标准枚举在程序集中作为托管枚举可见，可供其他任何托管编译器使用。   但是，未命名的标准枚举不会在程序集中公开可见。

在 Visual Studio 2002 和 Visual Studio 2003 中，用作函数参数中类型的标准枚举：

```cpp
// mcppv2_enum.cpp
// compile with: /clr
enum E { a, b };
void f(E) {System::Console::WriteLine("hi");}

int main() {
   E myi = b;
   f(myi);
}
```

将发出 MSIL 形式的以下内容用于函数签名：

```cpp
void f(int32);
```

但是，在当前版本的编译器中，标准枚举将作为属性为 [NativeEnumAttribute] 的托管枚举以及采用 MSIL 形式的以下内容发出，以用于函数签名：

```cpp
void f(E)
```

有关本机枚举的更多信息，请参见 [C++ 枚举声明](../cpp/enumerations-cpp.md)。

有关 CLR 枚举的更多信息，请参阅：

- [枚举的基础类型。](../dotnet/how-to-define-and-consume-enums-in-cpp-cli.md)

### <a name="requirements"></a>要求

编译器选项：`/clr`

### <a name="examples"></a>示例

```cpp
// mcppv2_enum_2.cpp
// compile with: /clr
// managed enum
public enum class m { a, b };

// standard enum
public enum n { c, d };

// unnamed, standard enum
public enum { e, f } o;

int main()
{
   // consume managed enum
   m mym = m::b;
   System::Console::WriteLine("no automatic conversion to int: {0}", mym);
   System::Console::WriteLine("convert to int: {0}", (int)mym);

   // consume standard enum
   n myn = d;
   System::Console::WriteLine(myn);

   // consume standard, unnamed enum
   o = f;
   System::Console::WriteLine(o);
}
```

```Output
no automatic conversion to int: b

convert to int: 1

1

1
```

## <a name="see-also"></a>另请参阅

[适用于 .NET 和 UWP 的组件扩展](component-extensions-for-runtime-platforms.md)
