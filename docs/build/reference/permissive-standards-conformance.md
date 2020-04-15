---
title: /permissive-（标准符合性）
description: 微软C++/允许（标准一致性）编译器选项的参考指南。
ms.date: 04/14/2020
f1_keywords:
- /permissive
- VC.Project.VCCLCompilerTool.ConformanceMode
helpviewer_keywords:
- /permissive compiler options [C++]
- -permissive compiler options [C++]
- Standards conformance compiler options
- permissive compiler options [C++]
ms.assetid: db1cc175-6e93-4a2e-9396-c3725d2d8f71
ms.openlocfilehash: 695f84e64f07128ac7744dc99e736f2a71ab3e79
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81337405"
---
# <a name="permissive--standards-conformance"></a>/permissive-（标准符合性）

指定与编译器的标准一致性模式。 使用此选项可帮助您识别和修复代码中的一致性问题，使其更加正确和可移植。

## <a name="syntax"></a>语法

> **/允许-**

## <a name="remarks"></a>备注

Visual Studio 2017 及更高版本支持此选项。

可以使用 **/允许编译器**选项指定符合标准的编译器行为。 此选项禁用允许行为，并设置[/Zc](zc-conformance.md)编译器选项以严格一致性。 在 IDE 中，此选项还使 IntelliSense 引擎对不符合的代码进行下划线。

默认情况下 **，/允许选项**设置在 Visual Studio 2017 版本 15.5 和更高版本创建的新项目中。 默认情况下，它未在早期版本中设置。 设置该选项后，当在代码中检测到非标准语言构造（包括 C++11 代码前的某些常见错误）时，编译器将生成诊断错误或警告。

**/允许-** 选项与最新的 Windows 工具包（如软件开发工具包 （SDK） 或 Windows 驱动程序工具包 （WDK））中的几乎所有标头文件兼容，这些配置文件从 Windows 秋季创建器 SDK （10.0.16299.0） 开始。 由于各种源代码一致性的原因，旧版本的 SDK 可能无法在 **/允许下**编译。 编译器和 SDK 在不同的发布时间线上提供，因此存在一些剩余问题。 有关特定的标头文件问题，请参阅下面的[Windows 标头问题](#windows-header-issues)。

**/允许-** 选项将[/Zc：引用绑定](zc-referencebinding-enforce-reference-binding-rules.md)[、/Zc：严格字符串](zc-strictstrings-disable-string-literal-type-conversion.md)和[/Zc：rvalueCast](zc-rvaluecast-enforce-type-conversion-rules.md)选项设置为符合行为。 这些选项默认为不符合项行为。 您可以在命令行 **/允许**后传递特定的 **/Zc**选项以覆盖此行为。

在 Visual Studio 2017 版本 15.3 中开始的编译器版本中 **，/允许-** 选项设置[/Zc：三元](zc-ternary.md)选项。 编译器还实现了两阶段名称查找的更多要求。 设置 **/允许选项**时，编译器将分析函数和类模板定义，并标识模板中使用的从属和非从属名称。 在此版本中，仅执行名称依赖项分析。

特定于环境的扩展和语言区域，标准留给实施不受 **/允许 -** 的影响。 例如，特定于 Microsoft`__declspec`的调用约定和结构化异常处理关键字以及编译器特定的杂注指令或属性不由编译器在 **/允许模式下**标记。

**/允许-** 选项使用当前编译器版本中的一致性支持来确定哪些语言构造不符合。 该选项不确定代码是否符合C++标准的特定版本。 要启用对最新标准草案的所有已实现编译器支持，请使用[/std：最新](std-specify-language-standard-version.md)选项。 要将编译器支持限制为当前实现的 C++17 标准，请使用[/std：c++17](std-specify-language-standard-version.md)选项。 要将编译器支持限制为更紧密地匹配 C++14 标准，请使用[/std：c++14](std-specify-language-standard-version.md)选项，这是默认值。

并非所有 C++11、C++14 或 C++17 标准符合的代码都受 Visual Studio 2017 所有版本中的 MSVC 编译器的支持。 根据 Visual Studio 的版本 **，/允许-** 选项可能无法检测有关两阶段名称查找的某些方面的问题，将对临时名称查找的非引用绑定为直接 init，允许在初始化中允许多个用户定义的转换，或逻辑运算符的替代令牌以及其他不支持的符合性区域。 有关 Visual C++ 中一致性问题的详细信息，请参阅 [Nonstandard Behavior](../../cpp/nonstandard-behavior.md)。 要充分利用 **/允许-**，请将 Visual Studio 更新到最新版本。

### <a name="how-to-fix-your-code"></a>如何修复代码

下面是一些在使用 **/允许时**检测到不符合要求的代码示例，以及修复问题的建议方法。

#### <a name="use-default-as-an-identifier-in-native-code"></a>在本机代码中使用默认值作为标识符

```cpp
void func(int default); // Error C2321: 'default' is a keyword, and
                        // cannot be used in this context
```

#### <a name="look-up-members-in-dependent-base"></a>查找从属基中的成员

```cpp
template <typename T>
struct B {
    void f();
};

template <typename T>
struct D : public B<T> // B is a dependent base because its type
                       // depends on the type of T.
{
    // One possible fix is to uncomment the following line.
    // If this is a type, don't forget the 'typename' keyword.
    // using B<T>::f;

    void g() {
        f(); // error C3861: 'f': identifier not found
             // Another fix is to change it to 'this->f();'
    }
};

void h() {
    D<int> d;
    d.g();
}
```

#### <a name="use-of-qualified-names-in-member-declarations"></a>在成员声明中使用合格名称

```cpp
struct A {
    void A::f() { } // error C4596: illegal qualified name in member
                    // declaration.
                    // Remove redundant 'A::' to fix.
};
```

#### <a name="initialize-multiple-union-members-in-a-member-initializer"></a>在成员初始化器中初始化多个工会成员

```cpp
union U
{
    U()
        : i(1), j(1) // error C3442: Initializing multiple members of
                     // union: 'U::i' and 'U::j'.
                     // Remove all but one of the initializations to fix.
    {}
    int i;
    int j;
};
```

#### <a name="hidden-friend-name-lookup-rules"></a>隐藏好友姓名查找规则

```cpp
// Example 1
struct S {
    friend void f(S *);
};
// Uncomment this declaration to make the hidden friend visible:
// void f(S *); // This declaration makes the hidden friend visible

using type = void (*)(S *);
type p = &f; // error C2065: 'f': undeclared identifier.
```

```cpp
// Example 2
struct S {
    friend void f(S *);
};
void g() {
    // Using nullptr instead of S prevents argument dependent lookup in S
    f(nullptr); // error C3861: 'f': identifier not found

    S *p = nullptr;
    f(p); // Hidden friend now found via argument-dependent lookup.
}
```

#### <a name="use-scoped-enums-in-array-bounds"></a>在数组边界中使用作用域枚举

```cpp
enum class Color {
    Red, Green, Blue
};

int data[Color::Blue]; // error C3411: 'Color' is not valid as the size
                       // of an array as it is not an integer type.
                       // Cast to type size_t or int to fix.
```

#### <a name="use-for-each-in-native-code"></a>在本机代码中为每个使用

```cpp
void func() {
    int array[] = {1, 2, 30, 40};
    for each (int i in array) // error C4496: nonstandard extension
                              // 'for each' used: replace with
                              // ranged-for statement:
                              // for (int i: array)
    {
        // ...
    }
}
```

#### <a name="use-of-atl-attributes"></a>使用 ATL 属性

```cpp
// Example 1
[uuid("594382D9-44B0-461A-8DE3-E06A3E73C5EB")]
class A {};
```

```cpp
// Fix for example 1
class __declspec(uuid("594382D9-44B0-461A-8DE3-E06A3E73C5EB")) B {};
```

```cpp
// Example 2
[emitidl];
[module(name="Foo")];

[object, local, uuid("9e66a290-4365-11d2-a997-00c04fa37ddb")]
__interface ICustom {
    HRESULT Custom([in] longl, [out, retval] long*pLong);
    [local] HRESULT CustomLocal([in] longl, [out, retval] long*pLong);
};

[coclass, appobject, uuid("9e66a294-4365-11d2-a997-00c04fa37ddb")]
class CFoo : public ICustom
{};
```

```cpp
// Fix for example 2
// First, create the *.idl file. The vc140.idl generated file can be
// used to automatically obtain a *.idl file for the interfaces with
// annotation. Second, add a midl step to your build system to make
// sure that the C++ interface definitions are outputted.
// Last, adjust your existing code to use ATL directly as shown in
// the atl implementation section.

-- IDL  FILE--
import "docobj.idl";

[object, local, uuid(9e66a290-4365-11d2-a997-00c04fa37ddb)]
interface ICustom : IUnknown {
    HRESULT Custom([in] longl, [out,retval] long*pLong);
    [local] HRESULT CustomLocal([in] longl, [out,retval] long*pLong);
};

[ version(1.0), uuid(29079a2c-5f3f-3325-99a1-3ec9c40988bb) ]
library Foo {
    importlib("stdole2.tlb");
    importlib("olepro32.dll");

    [version(1.0), appobject, uuid(9e66a294-4365-11d2-a997-00c04fa37ddb)]
    coclass CFoo { interface ICustom; };
}

-- ATL IMPLEMENTATION--
#include <idl.header.h>
#include <atlbase.h>

class ATL_NO_VTABLE CFooImpl : public ICustom,
    public ATL::CComObjectRootEx<CComMultiThreadModel>
{
    public:BEGIN_COM_MAP(CFooImpl)
    COM_INTERFACE_ENTRY(ICustom)
    END_COM_MAP()
};
```

#### <a name="ambiguous-conditional-operator-arguments"></a>模糊的条件运算符参数

在 Visual Studio 2017 版本 15.3 之前编译器的版本中，编译器接受条件运算符（或三元运算符）`?:`的参数，该参数被标准认为不明确。 在 **/允许模式下**，编译器现在在在早期版本中编译时没有诊断的情况下发出一个或多个诊断。

此更改可能导致的常见错误包括：

- 错误 C2593：" "操作员？" 模棱两可

- 错误 C2679： 二进制 '？'： 未找到采用"B"类型右侧操作数的运算符（或没有可接受的转换）

- 错误 C2678： 二进制 '？'： 未找到采用类型为"A"的左侧操作数的运算符（或没有可接受的转换）

- 错误 C2446：'：'：没有从"B"转换为"A"

可能导致此问题的典型代码模式是，某些类 C 同时提供另一种类型的 T 的非显式构造函数和类型 T 的非显式转换运算符。在这种情况下，将第二个参数转换为第三个参数的类型以及将第三个参数转换为第二个参数的类型都是有效的转换。 由于两者都有效，因此根据标准，它不明确。

```cpp
// Example 1: class that provides conversion to and initialization from some type T
struct A
{
    A(int);
    operator int() const;
};

extern bool cond;

A a(42);
// Accepted when /Zc:ternary or /permissive- is not used:
auto x = cond ? 7 : a; // A: permissive behavior prefers A(7) over (int)a
// Accepted always:
auto y = cond ? 7 : int(a);
auto z = cond ? A(7) : a;
```

当 T 表示 null 终止字符串类型之一（例如， `const char *`、 `const char16_t *`、 等） 和 实际`?:`参数为相应类型的字符串文本时，此常见模式有一个重要例外。 C++17 的语义从 C++14 进行了更改。 因此，在 **/std：c++14**下接受示例 2 中的代码，并在**使用 /Zc：terna**或 **/允许时**在 **/std：c++17**下拒绝。

```cpp
// Example 2: exception from the above
struct MyString
{
    MyString(const char* s = "") noexcept;  // from char*
    operator const char* () const noexcept; //   to char*
};

extern bool cond;

MyString s;
// Using /std:c++14, /permissive- or /Zc:ternary behavior
// is to prefer MyString("A") over (const char*)s
// but under /std:c++17 this line causes error C2445:
auto x = cond ? "A" : s;
// You can use a static_cast to resolve the ambiguity:
auto y = cond ? "A" : static_cast<const char*>(s);
```

另一个可能看到错误的情况是条件运算符中，其中有一个`void`类型的参数。 这种情况在类似 ASSERT 的宏中可能很常见。

```cpp
// Example 3: void arguments
void myassert(const char* text, const char* file, int line);
// Accepted when /Zc:ternary or /permissive- is not used:
#define ASSERT_A(ex) (void)((ex) ? 1 : myassert(#ex, __FILE__, __LINE__))
// Accepted always:
#define ASSERT_B(ex) (void)((ex) ? void() : myassert(#ex, __FILE__, __LINE__))
```

您可能还会在模板元编程中看到错误，其中条件运算符结果类型可能在 **/Zc：terna**和 **/允许 -** 下更改。 解决此问题的一种方法是在生成的类型上使用[std：：remove_reference。](../../standard-library/remove-reference-class.md)

```cpp
// Example 4: different result types
extern bool cond;
extern int count;
char  a = 'A';
const char  b = 'B';
decltype(auto) x = cond ? a : b; // char without, const char& with /Zc:ternary
const char (&z)[2] = count > 3 ? "A" : "B"; // const char* without /Zc:ternary
```

#### <a name="two-phase-name-look-up"></a>两阶段名称查找

设置 **/允许选项**时，编译器将分析函数和类模板定义，根据两阶段名称查找所需的身份标识模板中使用的从属名称和非从属名称。 在 Visual Studio 2017 版本 15.3 中，将执行名称依赖项分析。 特别是，未在模板定义上下文中声明的非依赖名称会导致 ISO C++标准所要求的诊断消息。 在 Visual Studio 2017 版本 15.7 中，还绑定了需要在定义上下文中查找与参数相关的名称。

```cpp
// dependent base
struct B {
    void g() {}
};

template<typename T>
struct D : T {
    void f() {
        // The call to g was incorrectly allowed in VS2017:
        g();  // Now under /permissive-: C3861
        // Possible fixes:
        // this->g();
        // T::g();
    }
};

int main()
{
    D<B> d;
    d.f();
}
```

如果希望对两阶段查找具有旧行为，但希望 **/允许行为**，则添加 **/Zc：双相选项**。

### <a name="windows-header-issues"></a>Windows 标头问题

**/允许-** 选项对于 Windows 秋季创建者更新 SDK （10.0.16299.0） 或 Windows 驱动程序工具包 （WDK） 版本 1709 之前的 Windows 工具包版本太严格。 我们建议您更新到最新版本的 Windows 工具包，以便在 Windows 或设备驱动程序代码中使用 **/允许。**

Windows 2018 年 4 月更新 SDK （10.0.17134.0）、Windows 秋季创建者更新 SDK （10.0.16299.0） 或 Windows 驱动程序工具包 （WDK） 1709 中的某些标题文件仍然存在问题，使它们与**使用 /允许 -** 不兼容。 为了解决这些问题，我们建议您将这些标头的使用限制为仅需要它们的源代码文件，并在编译这些特定的源代码文件时删除 **/允许选项**。

在 Windows 2018 年 4 月更新 SDK （10.0.17134.0） 中发布的这些 WinRT WRL 标头与 **/允许 -** 不干净。 要解决这些问题，请使用 **/允许 -** 或使用 **/Zc：两阶段** **-** 当您使用这些标头时：

- winrt/wrl/异步中的问题

   ```Output
   C:\Program Files (x86)\Windows Kits\10\Include\10.0.17134.0\winrt\wrl\async.h(483): error C3861: 'TraceDelegateAssigned': identifier not found
   C:\Program Files (x86)\Windows Kits\10\Include\10.0.17134.0\winrt\wrl\async.h(491): error C3861: 'CheckValidStateForDelegateCall': identifier not found
   C:\Program Files (x86)\Windows Kits\10\Include\10.0.17134.0\winrt\wrl\async.h(509): error C3861: 'TraceProgressNotificationStart': identifier not found
   C:\Program Files (x86)\Windows Kits\10\Include\10.0.17134.0\winrt\wrl\async.h(513): error C3861: 'TraceProgressNotificationComplete': identifier not found
   ```

- 在 winrt/wrl/机具中发出问题。

   ```Output
   C:\Program Files (x86)\Windows Kits\10\include\10.0.17134.0\winrt\wrl\implements.h(2086): error C2039: 'SetStrongReference': is not a member of 'Microsoft::WRL::Details::WeakReferenceImpl'
   ```

在 Windows 2018 更新 SDK （10.0.17134.0） 中发布的这些用户模式标头与 **/允许 -** 不干净。 要解决这些问题，在使用这些标头时，不要使用 **/允许**：

- 问题在 um/Tune.h

   ```Output
   C:\ProgramFiles(x86)\Windows Kits\10\include\10.0.17134.0\um\tune.h(139): error C3861: 'Release': identifier not found
   C:\Program Files (x86)\Windows Kits\10\include\10.0.17134.0\um\tune.h(559): error C3861: 'Release': identifier not found
   C:\Program Files (x86)\Windows Kits\10\include\10.0.17134.0\um\tune.h(1240): error C3861: 'Release': identifier not found
   C:\Program Files (x86)\Windows Kits\10\include\10.0.17134.0\um\tune.h(1240): note: 'Release': function declaration must be available as none of the arguments depend on a template parameter
   ```

- 问题在嗯/spddkhlp.h

   ```Output
   C:\Program Files (x86)\Windows Kits\10\include\10.0.17134.0\um\spddkhlp.h(759): error C3861: 'pNode': identifier not found
   ```

- 问题在嗯/refptrco.h

   ```Output
   C:\Program Files (x86)\Windows Kits\10\include\10.0.17134.0\um\refptrco.h(179): error C2760: syntax error: unexpected token 'identifier', expected 'type specifier'
   C:\Program Files (x86)\Windows Kits\10\include\10.0.17134.0\um\refptrco.h(342): error C2760: syntax error: unexpected token 'identifier', expected 'type specifier'
   C:\Program Files (x86)\Windows Kits\10\include\10.0.17134.0\um\refptrco.h(395): error C2760: syntax error: unexpected token 'identifier', expected 'type specifier'
   ```

这些问题特定于 Windows 秋季创建者更新 SDK （10.0.16299.0） 中的用户模式标头：

- 在 um/Query.h 中出现问题

   使用 **/允许 -** 编译器开关时，`tagRESTRICTION`结构不会编译，因为 case（RTOr） 成员"或"。

   ```cpp
   struct tagRESTRICTION
   {
       ULONG rt;
       ULONG weight;
       /* [switch_is][switch_type] */ union _URes
       {
           /* [case()] */ NODERESTRICTION ar;
           /* [case()] */ NODERESTRICTION or;  // error C2059: syntax error: '||'
           /* [case()] */ NODERESTRICTION pxr;
           /* [case()] */ VECTORRESTRICTION vr;
           /* [case()] */ NOTRESTRICTION nr;
           /* [case()] */ CONTENTRESTRICTION cr;
           /* [case()] */ NATLANGUAGERESTRICTION nlr;
           /* [case()] */ PROPERTYRESTRICTION pr;
           /* [default] */  /* Empty union arm */
       } res;
   };
   ```

   要解决此问题，请编译包含 Query.h 的文件，而不使用 **/允许选项**。

- 问题在嗯/cellularapi_oem.h

   使用 **/允许 -** 编译器开关时，转发`enum UICCDATASTOREACCESSMODE`声明会导致警告：

   ```cpp
   typedef enum UICCDATASTOREACCESSMODE UICCDATASTOREACCESSMODE; // C4471
   ```

   未示影的枚举的正向声明是 Microsoft 扩展。 要解决此问题，请编译包含 cellularapi_oem.h 的文件，而不使用 **/允许选项**，或使用[/wd](compiler-option-warning-level.md)选项来静音警告 C4471。

- 问题在 um/omscript.h

   在 C++03 中，从字符串文本转换为 BSTR（即 typedef 转换为"wchar_t +"）被弃用，但允许。 在 C++11 中，不再允许转换。

   ```cpp
   virtual /* [id] */ HRESULT STDMETHODCALLTYPE setExpression(
       /* [in] */ __RPC__in BSTR propname,
       /* [in] */ __RPC__in BSTR expression,
       /* [in][defaultvalue] */ __RPC__in BSTR language = L"") = 0; // C2440
   ```

   要解决此问题，请编译包含 omscript.h 的文件，而不使用 **/允许选项**，或者使用 **/Zc：严格字符串-**

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此编译器选项

在 Visual Studio 2017 版本 15.5 和更高版本中，使用以下步骤：

1. 打开项目**的属性页**对话框。

1. 选择**配置属性** > **C/C++** > **语言**属性页。

1. 将 **"一致性模式**"属性值更改为 **"是"（/允许-）**。 选择 **"确定"** 或 **"应用"** 以保存更改。

在 Visual Studio 2017 版本 15.5 之前的版本中，使用以下步骤：

1. 打开项目**的属性页**对话框。

1. 选择**配置属性** > **C/C++** > **命令行**属性页。

1. 在 **"附加选项**"框中输入 **/允许-** 编译器选项。 选择 **"确定"** 或 **"应用"** 以保存更改。

### <a name="to-set-this-compiler-option-programmatically"></a>以编程方式设置此编译器选项

- 请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>。

## <a name="see-also"></a>另请参阅

[MSVC 编译器选项](compiler-options.md)\
[MSVC 编译器命令行语法](compiler-command-line-syntax.md)
