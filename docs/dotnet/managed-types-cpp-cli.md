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
ms.openlocfilehash: c61f3fdd434a1b746c024b1a98d1d71f04df7e5b
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/11/2019
ms.locfileid: "57746912"
---
# <a name="managed-types-ccli"></a>托管类型 (C++/CLI)

Visual c + + 允许对通过托管类型，为公共语言运行时功能提供支持，同时受影响的优点和限制的运行时的.NET 功能的访问。

## <a name="main_functions"></a> 托管的类型和 main 函数

编写应用程序中使用时 **/clr**的参数**main （)** 函数不能为托管类型。

正确签名的一个示例是：

```cpp
// managed_types_and_main.cpp
// compile with: /clr
int main(int, char*[], char*[]) {}
```

## <a name="dotnet"></a> 对应于 c + + 本机类型的.NET framework

下表显示了内置的 Visual c + + 类型，它们是预定义类型的别名的关键字在**系统**命名空间。

|Visual c + + 类型|.NET Framework 类型|
|-----------------------|-------------------------|
|**bool**|**System.Boolean**|
|**签名 char** (请参阅[/J](../build/reference/j-default-char-type-is-unsigned.md)有关详细信息)|**System.SByte**|
|**unsigned char**|**System.Byte**|
|**wchar_t**|**System.Char**|
|**双精度**和**长双精度**|**System.Double**|
|**float**|**System.Single**|
|**int**，**带符号整型**，**长**，并**长签名**|**System.Int32**|
|**无符号的整型**和**无符号长**|**System.UInt32**|
|**__int64**和**签名 __int64**|**System.Int64**|
|unsigned __int64|**System.UInt64**|
|**短**和**短签名**|**System.Int16**|
|**unsigned short**|**System.UInt16**|
|**void**|**System.Void**|

## <a name="version_issues"></a> 嵌套在本机类型中的值类型的版本问题

请考虑用于生成客户端程序集签名 （强名称） 程序集组件。 该组件包含用于在客户端中作为类型的本机的并集、 类或数组成员的值类型。 如果该组件的未来版本发生更改的大小或值类型的布局，则必须重新编译客户端。

创建与 keyfile [sn.exe](/dotnet/framework/tools/sn-exe-strong-name-tool) (`sn -k mykey.snk`)。

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

但是，如果您添加到另一个成员`struct S`nested_value_types.cpp 中, (例如， `double d;`) 和无需重新编译客户端重新编译该组件，则结果为未处理的异常 (类型的<xref:System.IO.FileLoadException?displayProperty=fullName>)。

## <a name="test_equality"></a> 操作说明：确定相等性的测试

在下面的示例中，使用 Managed Extensions for c + + 的相等性测试基于句柄的引用。

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

此程序的 IL 显示返回值通过使用 op_Equality 调用实现。

```MSIL
IL_0012:  call       bool [mscorlib]System.String::op_Equality(string,
                                                               string)
```

## <a name="diagnose_fix"></a> 操作说明：诊断和修复程序集兼容性问题

本主题介绍了在编译时引用的程序集的版本与在运行时，引用的程序集的版本不匹配时可能发生以及如何避免此问题。

编译为程序集时，可能被其他程序集引用与`#using`语法。 在编译期间，由编译器访问这些程序集。 这些程序集中的信息用于进行优化的决策。

但是，如果引用的程序集已更改并且重新编译，并且不重新编译依赖于它的引用程序集，这些程序集可能不是兼容。 在有效的优化决策首先可能不是相对于新的程序集版本正确。 由于这些不兼容性可能会发生各种运行时错误。 没有将这种情况下不生成任何特定异常。 在运行时报告失败的方式取决于导致问题的代码更改的特性。

只要你的产品发行版本重新生成整个应用程序时，这些错误不应为最终的生产代码中的问题。 发布给公众的程序集应标有正式版本号，这将确保避免这些问题。 有关详细信息，请参阅[程序集版本控制](/dotnet/framework/app-domains/assembly-versioning)。

### <a name="diagnosing-and-fixing-an-incompatibility-error"></a>诊断和解决不兼容性错误

1. 如果您遇到运行时异常或发生在代码中引用另一个程序集的其他错误情况并且没有其他标识的原因，您可能会处理过期的程序集。

1. 首先，隔离和重现或其他错误情况的异常。 由于过时的异常发生的问题，应可重现。

1. 检查任何引用的程序集在应用程序中的时间戳。

1. 如果任何引用的程序集的时间戳晚于应用程序的最后一个编译的时间戳，您的应用程序已过期。 如果发生这种情况，重新编译应用程序与最新程序集，并进行所需的任何代码更改。

1. 重新运行该应用程序中，执行重现该问题，并验证该异常不会发生的步骤。

### <a name="example"></a>示例

以下程序演示了通过减少的一种方法，可访问性并尝试访问另一个程序集中该方法无需重新编译该问题。 请尝试编译`changeaccess.cpp`第一个。 这是所引用的程序集，这将更改。 然后，编译`referencing.cpp`。 编译成功。 现在，减少所调用的方法的可访问性。 重新编译`changeaccess.cpp`标志`/DCHANGE_ACCESS`。 这样，该方法受保护，而不是私有的因此它可以再合法调用。 无需重新编译`referencing.exe`，重新运行该应用程序。 异常<xref:System.MethodAccessException>将导致。

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

## <a name="see-also"></a>请参阅

[使用 C++/CLI (Visual C++) 进行 .NET 编程](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)<br/>
[与其他 .NET 语言的互操作性 (C++/CLI)](../dotnet/interoperability-with-other-dotnet-languages-cpp-cli.md)<br/>
[托管类型 (C++/CLI)](../dotnet/managed-types-cpp-cli.md)<br/>
[#using 指令](../preprocessor/hash-using-directive-cpp.md)
