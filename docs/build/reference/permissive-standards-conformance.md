---
title: /permissive-（标准符合性）
ms.date: 03/08/2019
f1_keywords:
- /permissive
- VC.Project.VCCLCompilerTool.ConformanceMode
helpviewer_keywords:
- /permissive compiler options [C++]
- -permissive compiler options [C++]
- Standards conformance compiler options
- permissive compiler options [C++]
ms.assetid: db1cc175-6e93-4a2e-9396-c3725d2d8f71
ms.openlocfilehash: aca0fbc6a2ca36ceae26ba060b5bf92fea79c32c
ms.sourcegitcommit: fd0f8839da5c6a3663798a47c6b0bb6e63b518bd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/04/2019
ms.locfileid: "70273728"
---
# <a name="permissive--standards-conformance"></a>/permissive-（标准符合性）

指定编译器的标准一致性模式。 使用此选项可帮助您识别和修复代码中的符合性问题，使其更正确且更具可移植性。

## <a name="syntax"></a>语法

> **/permissive-**

## <a name="remarks"></a>备注

Visual Studio 2017 及更高版本支持此选项。

可以使用 **/permissive-** 编译器选项指定符合标准的编译器行为。 此选项将禁用许可行为，并为严格一致性设置[/zc](zc-conformance.md)编译器选项。 在 IDE 中，此选项还使 IntelliSense 引擎为不一致的代码添加下划线。

默认情况下，在 Visual Studio 2017 版本15.5 及更高版本创建的新项目中设置 **/permissive-** 选项。 默认情况下，它在早期版本中未设置。 设置该选项后，当在代码中检测到非标准语言构造时，编译器将生成诊断错误或警告，其中包括 C + + 11 代码中的一些常见错误。

**/Permissive-** 选项与最近的 windows 工具包中的几乎所有头文件（例如软件开发工具包（SDK）或 Windows 驱动程序工具包（WDK））兼容，从 Windows 秋季创建者 SDK （10.0.16299.0）开始。 由于各种源代码一致性原因，SDK 的早期版本可能无法在 **/permissive-** 下编译。 编译器和 Sdk 随附在不同的发布时间线上，因此存在一些剩余问题。 有关特定标头文件的问题，请参阅下面的[Windows 标题问题](#windows-header-issues)。

**/Permissive-** 选项将[/zc： referenceBinding](zc-referencebinding-enforce-reference-binding-rules.md)、 [/zc： strictStrings](zc-strictstrings-disable-string-literal-type-conversion.md)和[/zc： rvalueCast](zc-rvaluecast-enforce-type-conversion-rules.md)选项设置为一致的行为。 这些选项默认为不一致的行为。 可以在命令行中的 **/permissive-** 后传递特定的 **/zc**选项，以覆盖此行为。

在版本的编译器中，从 Visual Studio 2017 版本15.3 开始， **/permissive-** 选项设置[/zc：三元](zc-ternary.md)选项。 编译器还实现了两阶段名称查找的更多要求。 如果设置了 **/permissive-** 选项，则编译器会分析函数和类模板定义，并标识模板中使用的依赖项和非依赖名称。 在此版本中，只执行名称依赖项分析。

标准留给实现的环境特定扩展和语言区域不受 **/permissive-** 的影响。 例如，Microsoft 特定`__declspec`的调用约定和结构化异常处理关键字，以及特定于编译器的杂注指令或属性在 **/permissive-** 模式下不由编译器标记。

**/Permissive-** 选项使用当前编译器版本中的一致性支持来确定哪些语言构造是不一致的。 选项不确定您的代码是否符合特定的C++标准版本。 若要为最新草案标准启用所有实现的编译器支持，请使用[/std：最新](std-specify-language-standard-version.md)选项。 若要将编译器支持限制为当前实现的 c + + 17 标准，请使用[/std： c + + 17](std-specify-language-standard-version.md)选项。 若要使编译器支持更接近 c + + 14 标准，请使用[/std： c + + 14](std-specify-language-standard-version.md)选项，这是默认值。

并非所有版本的 Visual Studio 2017 的 MSVC 编译器都支持 c + + 11、c + + 14 或 c + + 17 标准一致代码。 根据 Visual Studio 的版本， **/permissive-** 选项可能无法检测到两个阶段名称查找的某些方面的问题，请将非常量引用绑定到临时，将副本 init 视为直接初始化，从而允许多个用户定义初始化中的转换或逻辑运算符的替代标记，以及其他不支持的一致性区域。 有关 Visual C++ 中一致性问题的详细信息，请参阅 [Nonstandard Behavior](../../cpp/nonstandard-behavior.md)。 若要充分利用 **/permissive-** ，请将 Visual Studio 更新到最新版本。

### <a name="how-to-fix-your-code"></a>如何修复代码

下面是在使用 **/permissive-** 时检测为不一致的代码示例，以及解决问题的建议方法。

#### <a name="use-default-as-an-identifier-in-native-code"></a>在本机代码中使用 default 作为标识符

```cpp
void func(int default); // Error C2321: 'default' is a keyword, and
                        // cannot be used in this context
```

#### <a name="look-up-members-in-dependent-base"></a>查找依赖基准中的成员

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

#### <a name="use-of-qualified-names-in-member-declarations"></a>在成员声明中使用限定名

```cpp
struct A {
    void A::f() { } // error C4596: illegal qualified name in member
                    // declaration.
                    // Remove redundant 'A::' to fix.
};
```

#### <a name="initialize-multiple-union-members-in-a-member-initializer"></a>在成员初始值设定项中初始化多个联合成员

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

#### <a name="hidden-friend-name-lookup-rules"></a>隐藏的 friend name 查找规则

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
    f(S); // Hidden friend now found via argument-dependent lookup.
}
```

#### <a name="use-scoped-enums-in-array-bounds"></a>在数组边界内使用范围枚举

```cpp
enum class Color {
    Red, Green, Blue
};

int data[Color::Blue]; // error C3411: 'Color' is not valid as the size
                       // of an array as it is not an integer type.
                       // Cast to type size_t or int to fix.
```

#### <a name="use-for-each-in-native-code"></a>在本机代码中使用

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

#### <a name="use-of-atl-attributes"></a>ATL 属性的使用

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

#### <a name="ambiguous-conditional-operator-arguments"></a>条件运算符参数不明确

在 Visual Studio 2017 版本15.3 之前的编译器版本中，编译器接受由标准视为不明确的条件运算符（或三元`?:`运算符）的自变量。 在 **/permissive-** 模式下，编译器现在会在编译时发出一个或多个诊断，在早期版本中不进行诊断。

此更改可能导致的常见错误包括：

- 错误 C2593： "operator？" 不明确

- 错误 C2679：二进制 "？"：没有找到接受类型 "B" 的右操作数的运算符（或没有可接受的转换）

- 错误 C2678：二进制 "？"：没有找到接受类型为 "A" 的左操作数的运算符（或没有可接受的转换）

- 错误 C2446： "："：没有从 "B" 到 "A" 的转换

如果某个类 C 同时提供了另一类型 T 中的非显式构造函数和类型 T 的非显式转换运算符，则可能导致此问题的一种典型的代码模式。在这种情况下，第二个参数的类型转换为第三个参数的类型，第三个参数的转换为第二个参数的类型，是有效的转换。 由于两者都是有效的，因此它不明确，这一点与标准有所不同。

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

当 T 表示以`const char *` `?:` null 结尾的字符串类型之一（例如`const char16_t *`，、等），并且的实际自变量为相应类型的字符串文字时，此通用模式存在重要的例外情况。 C + + 17 已更改 c + + 14 的语义。 因此，在 **/std： c + + 14**下接受示例2中的代码，并在 **/std： c + + 17 （** 当使用 **/zc：三元**或 **/permissive-** 时被拒绝。

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

另外一种情况下，你可能会发现错误位于类型`void`为的参数的条件运算符中。 这种情况在类似断言的宏中可能很常见。

```cpp
// Example 3: void arguments
void myassert(const char* text, const char* file, int line);
// Accepted when /Zc:ternary or /permissive- is not used:
#define ASSERT_A(ex) (void)((ex) ? 1 : myassert(#ex, __FILE__, __LINE__))
// Accepted always:
#define ASSERT_B(ex) (void)((ex) ? void() : myassert(#ex, __FILE__, __LINE__))
```

你可能还会在模板元编程中看到错误，其中条件运算符结果类型可能在 **/zc：三元**和 **/permissive-** 下更改。 解决此问题的一种方法是对结果类型使用[std：： remove_reference](../../standard-library/remove-reference-class.md) 。

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

如果设置了 **/permissive-** 选项，则编译器会分析函数和类模板定义，并根据需要为两阶段名称查找所需的模板中的依赖项和非相关名称标识。 在 Visual Studio 2017 版本15.3 中，执行名称依赖项分析。 特别是，在模板定义上下文中未声明的非依赖名称会导致 ISO C++标准要求诊断消息。 在 Visual Studio 2017 版本15.7 中，还完成了在定义上下文中需要依赖于参数的查找的非依赖项名称的绑定。

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

如果你希望对两阶段查找执行旧行为，但又想要 **/permissive-** 行为，请添加 **/zc： twoPhase** 。

### <a name="windows-header-issues"></a>Windows 标题问题

Windows 秋季创意者更新 SDK （10.0.16299.0）或 Windows 驱动程序工具包（WDK）版本1709之前的 Windows 工具包版本的 **/permissive-** 选项过严格。 建议更新到最新版本的 Windows 工具包，以便在 Windows 或设备驱动程序代码中使用 **/permissive-** 。

Windows 2018 年4月更新 SDK （10.0.17134.0）、Windows 秋季创意者更新 SDK （10.0.16299.0）或 Windows 驱动程序工具包（WDK）1709中的某些头文件仍然存在使它们与使用 **/permissive-** 不兼容的问题。 若要解决这些问题，我们建议你仅将这些标头的使用限制为那些需要它们的源代码文件，并在编译这些特定源代码文件时删除 **/permissive-** 选项。

在 Windows 2018 年4月的更新 SDK （10.0.17134.0）中发布的这些 WinRT WRL 标头与 **/permissive-** 并不完全相同。 若要解决这些问题，请不要使用 **/permissive-** ，或将 **/permissive-** 与 **/zc： twoPhase**配合使用：

- Winrt/wrl/async 中的问题

   ```Output
   C:\Program Files (x86)\Windows Kits\10\Include\10.0.17134.0\winrt\wrl\async.h(483): error C3861: 'TraceDelegateAssigned': identifier not found
   C:\Program Files (x86)\Windows Kits\10\Include\10.0.17134.0\winrt\wrl\async.h(491): error C3861: 'CheckValidStateForDelegateCall': identifier not found
   C:\Program Files (x86)\Windows Kits\10\Include\10.0.17134.0\winrt\wrl\async.h(509): error C3861: 'TraceProgressNotificationStart': identifier not found
   C:\Program Files (x86)\Windows Kits\10\Include\10.0.17134.0\winrt\wrl\async.h(513): error C3861: 'TraceProgressNotificationComplete': identifier not found
   ```

- Winrt/wrl/实现 .h 中的问题

   ```Output
   C:\Program Files (x86)\Windows Kits\10\include\10.0.17134.0\winrt\wrl\implements.h(2086): error C2039: 'SetStrongReference': is not a member of 'Microsoft::WRL::Details::WeakReferenceImpl'
   ```

在 Windows 2018 年4月的更新 SDK （10.0.17134.0）中发布的这些用户模式标头不会与 **/permissive-** 完全相同。 若要解决这些问题，请在使用这些标头时不要使用 **/permissive-** ：

- Um/调整 .h 中的问题

   ```Output
   C:\ProgramFiles(x86)\Windows Kits\10\include\10.0.17134.0\um\tune.h(139): error C3861: 'Release': identifier not found
   C:\Program Files (x86)\Windows Kits\10\include\10.0.17134.0\um\tune.h(559): error C3861: 'Release': identifier not found
   C:\Program Files (x86)\Windows Kits\10\include\10.0.17134.0\um\tune.h(1240): error C3861: 'Release': identifier not found
   C:\Program Files (x86)\Windows Kits\10\include\10.0.17134.0\um\tune.h(1240): note: 'Release': function declaration must be available as none of the arguments depend on a template parameter
   ```

- Um/spddkhlp 中的问题

   ```Output
   C:\Program Files (x86)\Windows Kits\10\include\10.0.17134.0\um\spddkhlp.h(759): error C3861: 'pNode': identifier not found
   ```

- Um/refptrco 中的问题

   ```Output
   C:\Program Files (x86)\Windows Kits\10\include\10.0.17134.0\um\refptrco.h(179): error C2760: syntax error: unexpected token 'identifier', expected 'type specifier'
   C:\Program Files (x86)\Windows Kits\10\include\10.0.17134.0\um\refptrco.h(342): error C2760: syntax error: unexpected token 'identifier', expected 'type specifier'
   C:\Program Files (x86)\Windows Kits\10\include\10.0.17134.0\um\refptrco.h(395): error C2760: syntax error: unexpected token 'identifier', expected 'type specifier'
   ```

这些问题特定于 Windows 秋季创意者更新 SDK （10.0.16299.0）中的用户模式标头：

- Um/Query 中的问题

   使用 **/permissive-** 编译器开关时，由于 case `tagRESTRICTION` （RTOr）成员 "or"，结构不进行编译。

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

   若要解决此问题，请在不带 **/permissive-** 选项的情况下编译包含 Query 的文件。

- Um/cellularapi_oem 中的问题

   使用 **/permissive-** 编译器开关时，的`enum UICCDATASTOREACCESSMODE`前向声明会导致警告：

   ```cpp
   typedef enum UICCDATASTOREACCESSMODE UICCDATASTOREACCESSMODE; // C4471
   ```

   未区分范围的枚举的前向声明是 Microsoft 扩展。 若要解决此问题，请在不使用 **/permissive-** 选项的情况下编译包含 cellularapi_oem 的文件，或使用[/wd](compiler-option-warning-level.md)选项静音警告 C4471。

- Um/omscript 中的问题

   在 c + + 03 中，已弃用从字符串文本到 BSTR （即 typedef 到 "wchar_t *"）的转换，但允许使用该转换。 在 c + + 11 中，不再允许转换。

   ```cpp
   virtual /* [id] */ HRESULT STDMETHODCALLTYPE setExpression(
       /* [in] */ __RPC__in BSTR propname,
       /* [in] */ __RPC__in BSTR expression,
       /* [in][defaultvalue] */ __RPC__in BSTR language = L"") = 0; // C2440
   ```

   若要解决此问题，请在不使用 **/permissive-** 选项的情况下编译包含 omscript 的文件，或改用 **/zc： strictStrings** 。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此编译器选项

在 Visual Studio 2017 版本15.5 及更高版本中，使用此过程：

1. 打开项目的 "**属性页**" 对话框。

1. 选择 "**配置属性** > " " > **C/C++** **语言**" 属性页。

1. 将**一致性模式**属性值更改为 **"是（/permissive-）"** 。 选择 **"确定" 或 "** **应用**" 保存更改。

在 Visual Studio 2017 版本15.5 之前的版本中，使用此过程：

1. 打开项目的 "**属性页**" 对话框。

1. 选择“配置属性” > “C/C++” > “命令行”属性页。

1. 在 "**附加选项**" 框中输入 **/permissive-** 编译器选项。 选择 **"确定" 或 "** **应用**" 保存更改。

### <a name="to-set-this-compiler-option-programmatically"></a>以编程方式设置此编译器选项

- 请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>。

## <a name="see-also"></a>请参阅

[MSVC 编译器选项](compiler-options.md)\
[MSVC 编译器命令行语法](compiler-command-line-syntax.md)
