---
title: 托管类型 (C++/CLI)
ms.date: 11/04/2016
helpviewer_keywords:
- data types [C++], managed
- managed data types [C++]
- .NET Framework [C++], managed types
- data types [C++], .NET feature access
- main function, in managed applications
- managed code, main() function
- .NET Framework [C++], C++ equivalents
- __nogc type declarations
- __value keyword, issues when nesting
- equality, testing for
- versioning, diagnosing conflicts
- versioning
- exceptions, diagnosing odd behavior
- compatibility, between assemblies
ms.assetid: 679b8ed3-d966-4a0c-b627-2a3f3ec96b74
ms.openlocfilehash: c542151bda780e5306db35049d988e6514fffd62
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87225600"
---
# <a name="managed-types-ccli"></a>托管类型 (C++/CLI)

Visual C++ 允许通过托管类型访问 .NET 功能，这些类型支持公共语言运行时的功能，并且受运行时的优点和限制的限制。

## <a name="managed-types-and-the-main-function"></a><a name="main_functions"></a>托管类型和 main 函数

当使用编写应用程序时 **`/clr`** ， **main （）** 函数的参数不能是托管类型。

正确签名的示例如下：

```cpp
// managed_types_and_main.cpp
// compile with: /clr
int main(int, char*[], char*[]) {}
```

## <a name="net-framework-equivalents-to-c-native-types"></a><a name="dotnet"></a>与 c + + 本机类型等效 .NET Framework

下表显示了内置 Visual C++ 类型的关键字，这些关键字是**System**命名空间中预定义类型的别名。

|Visual C++ 类型|.NET Framework 类型|
|-----------------------|-------------------------|
|**`void`**|<xref:System.Void?displayProperty=nameWithType>|
|**`bool`**|<xref:System.Boolean?displayProperty=nameWithType>|
|**`signed char`** |<xref:System.SByte?displayProperty=nameWithType>|
|**`unsigned char`**|<xref:System.Byte?displayProperty=nameWithType>|
|**`wchar_t`**|<xref:System.Char?displayProperty=nameWithType>|
|**`short`** 和 **`signed short`**|<xref:System.Int16?displayProperty=nameWithType>|
|**`unsigned short`**|<xref:System.UInt16?displayProperty=nameWithType>|
|**`int`**、 **`signed int`** 、 **`long`** 和**`signed long`**|<xref:System.Int32?displayProperty=nameWithType>|
|**`unsigned int`** 和 **`unsigned long`**|<xref:System.UInt32?displayProperty=nameWithType>|
|**`__int64`** 和 **`signed __int64`**|<xref:System.Int64?displayProperty=nameWithType>|
|**`unsigned __int64`**|<xref:System.UInt64?displayProperty=nameWithType>|
|**`float`**|<xref:System.Single?displayProperty=nameWithType>|
|**`double`** 和 **`long double`**|<xref:System.Double?displayProperty=nameWithType>|

有关编译器选项默认为或的详细信息 **`signed char`** **`unsigned char`** ，请参阅[ `/J` （默认 **`char`** 类型为 **`unsigned`** ）](../build/reference/j-default-char-type-is-unsigned.md)。

## <a name="version-issues-for-value-types-nested-in-native-types"></a><a name="version_issues"></a>嵌套在本机类型中的值类型的版本问题

考虑用于生成客户端程序集的已签名（强名称）程序集组件。 组件包含一个值类型，该类型在客户端中用作本机联合、类或数组的成员的类型。 如果组件的未来版本更改了值类型的大小或布局，则必须重新编译该客户端。

使用[sn.exe](/dotnet/framework/tools/sn-exe-strong-name-tool) （）创建 keyfile `sn -k mykey.snk` 。

### <a name="example"></a>示例

下面的示例是组件。

```cpp
// nested_value_types.cpp
// compile with: /clr /LD
using namespace System::Reflection;
[assembly:AssemblyVersion("1.0.0.*"),
assembly:AssemblyKeyFile("mykey.snk")];

public value struct S {
   int i;
   void Test() {
      System::Console::WriteLine("S.i = {0}", i);
   }
};
```

### <a name="example"></a>示例

此示例是客户端：

```cpp
// nested_value_types_2.cpp
// compile with: /clr
#using <nested_value_types.dll>

struct S2 {
   S MyS1, MyS2;
};

int main() {
   S2 MyS2a, MyS2b;
   MyS2a.MyS1.i = 5;
   MyS2a.MyS2.i = 6;
   MyS2b.MyS1.i = 10;
   MyS2b.MyS2.i = 11;

   MyS2a.MyS1.Test();
   MyS2a.MyS2.Test();
   MyS2b.MyS1.Test();
   MyS2b.MyS2.Test();
}
```

### <a name="output"></a>输出

```Output
S.i = 5
S.i = 6
S.i = 10
S.i = 11
```

### <a name="comments"></a>注释

但是，如果将另一个成员添加到 `struct S` nested_value_types .cpp 中（例如 `double d;` ），并重新编译该组件而不重新编译该客户端，则结果是未经处理的异常（类型为 <xref:System.IO.FileLoadException?displayProperty=fullName> ）。

## <a name="how-to-test-for-equality"></a><a name="test_equality"></a>如何：测试相等性

在下面的示例中，使用 Managed Extensions for C++ 的相等性测试基于句柄引用的内容。

### <a name="example"></a>示例

```cpp
// mcppv2_equality_test.cpp
// compile with: /clr /LD
using namespace System;

bool Test1() {
   String ^ str1 = "test";
   String ^ str2 = "test";
   return (str1 == str2);
}
```

此程序的 IL 显示返回值是通过调用 op_Equality 实现的。

```MSIL
IL_0012:  call       bool [mscorlib]System.String::op_Equality(string,
                                                               string)
```

## <a name="how-to-diagnose-and-fix-assembly-compatibility-problems"></a><a name="diagnose_fix"></a>如何：诊断和修复程序集兼容性问题

本主题说明在编译时引用的程序集的版本与运行时引用的程序集的版本不匹配以及如何避免此问题可能会发生的情况。

编译程序集时，可以使用语法来引用其他程序集 `#using` 。 在编译期间，编译器将访问这些程序集。 这些程序集中的信息用于做出优化决策。

但是，如果对被引用的程序集进行了更改和重新编译，并且未重新编译依赖于它的引用程序集，则这些程序集可能仍不兼容。 对于新的程序集版本，最初有效的优化决策可能不正确。 由于这些不兼容性，可能会发生各种运行时错误。 这种情况下不会产生任何特定的异常。 在运行时报告失败的方式取决于导致问题的代码更改的性质。

只要为产品的发布版本重新生成整个应用程序，这些错误就不会成为最终生产代码中的问题。 发布到公共的程序集应使用官方版本号进行标记，这将确保避免这些问题。 有关详细信息，请参阅[程序集版本控制](/dotnet/framework/app-domains/assembly-versioning)。

### <a name="diagnosing-and-fixing-an-incompatibility-error"></a>诊断和修复不兼容错误

1. 如果遇到运行时异常或在引用另一个程序集的代码中出现的其他错误条件，但没有其他标识的原因，则您可能正在处理过期的程序集。

1. 首先，隔离并重现异常或其他错误情况。 由于过时的异常而出现的问题应该可以重现。

1. 检查应用程序中引用的任何程序集的时间戳。

1. 如果任何引用的程序集的时间戳晚于应用程序的上次编译时间戳，则您的应用程序已过期。 如果发生这种情况，请使用最新的程序集重新编译应用程序，并进行任何所需的代码更改。

1. 重新运行该应用程序，执行重现该问题的步骤，并验证是否没有出现该异常。

### <a name="example"></a>示例

下面的程序通过降低方法的可访问性，并尝试在不重新编译的情况下访问另一个程序集中的方法来说明此问题。 首先尝试编译 `changeaccess.cpp` 。 这是将更改的引用程序集。 然后编译 `referencing.cpp` 。 编译成功。 现在，降低所调用方法的可访问性。 `changeaccess.cpp`用标志进行重新编译 `/DCHANGE_ACCESS` 。 这使得该方法是受保护的，而不是私有的，因此可以更长时间被合法地调用。 如果不进行 `referencing.exe` 重新编译，请重新运行该应用程序。 <xref:System.MethodAccessException>将导致异常。

```cpp
// changeaccess.cpp
// compile with: /clr:safe /LD
// After the initial compilation, add /DCHANGE_ACCESS and rerun
// referencing.exe to introduce an error at runtime. To correct
// the problem, recompile referencing.exe

public ref class Test {
#if defined(CHANGE_ACCESS)
protected:
#else
public:
#endif

  int access_me() {
    return 0;
  }

};
```

```cpp
// referencing.cpp
// compile with: /clr:safe
#using <changeaccess.dll>

// Force the function to be inline, to override the compiler's own
// algorithm.
__forceinline
int CallMethod(Test^ t) {
  // The call is allowed only if access_me is declared public
  return t->access_me();
}

int main() {
  Test^ t = gcnew Test();
  try
  {
    CallMethod(t);
    System::Console::WriteLine("No exception.");
  }
  catch (System::Exception ^ e)
  {
    System::Console::WriteLine("Exception!");
  }
  return 0;
}
```

## <a name="see-also"></a>另请参阅

[用 c + +/CLI 进行 .NET 编程（Visual C++）](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)<br/>
[与其他 .NET 语言的互操作性 (C++/CLI)](../dotnet/interoperability-with-other-dotnet-languages-cpp-cli.md)<br/>
[托管类型 (C++/CLI)](../dotnet/managed-types-cpp-cli.md)<br/>
[#using 指令](../preprocessor/hash-using-directive-cpp.md)
