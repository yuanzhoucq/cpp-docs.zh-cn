---
title: -宽松-（标准一致性） |Microsoft 文档
ms.date: 06/21/2018
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /permissive
- VC.Project.VCCLCompilerTool.ConformanceMode
dev_langs:
- C++
helpviewer_keywords:
- /permissive compiler options [C++]
- -permissive compiler options [C++]
- Standards conformance compiler options
- permissive compiler options [C++]
ms.assetid: db1cc175-6e93-4a2e-9396-c3725d2d8f71
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3e1a9c407779b6bf441ea1375026af6ac04bb8c8
ms.sourcegitcommit: e013acba70aa29fed60ae7945162adee23e19c3b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/22/2018
ms.locfileid: "36322259"
---
# <a name="permissive--standards-conformance"></a>/ 宽松-（标准一致性）

指定到编译器的标准一致性模式。 使用此选项可帮助你标识和修复代码，以使其更正确并更易于移植中的一致性问题。

## <a name="syntax"></a>语法

> **/permissive-**

## <a name="remarks"></a>备注

你可以使用 **/ 宽松-** 编译器选项来指定符合标准的编译器行为。 此选项禁用宽松行为，并设置[/Zc](../../build/reference/zc-conformance.md)严格一致性的编译器选项。 在 IDE 中，此选项还使 IntelliSense 引擎下划线不符合要求代码。

默认情况下， **/ 宽松-** 在通过 Visual Studio 2017 版本 15.5 和更高版本创建的新项目中设置选项。 未设置默认情况下，在早期版本中。 当将选项设置，编译器将生成诊断错误或警告非标准语言构造时是否检测到你的代码时，在预包括一些常见的 bug 的 C + + 11 代码。

**/ 宽松-** 选项适用于几乎所有最新的 Windows 套件，如软件开发工具包 (SDK) 或 Windows 驱动程序工具包 (WDK)，从 Windows 秋季创建者 SDK (10.0.16299.0) 开始的标头文件。 较旧版本的 SDK 可能无法在下编译 **/ 宽松-** 各种源代码一致性方面的考虑。 编译器和不同的发布时间线上的 Sdk 装运因此有一些剩余的问题。 有关特定标头文件问题，请参阅[Windows 标头问题](#windows-header-issues)下面。

**/ 宽松-** 选项集[/zc: strictstrings](../../build/reference/zc-conformance.md)和[/zc: rvaluecast](../../build/reference/zc-conformance.md)符合标准行为的选项。 它们默认为不符合要求的行为。 你可以将传递特定 **/Zc**选项后 **/ 宽松-** 重写此行为在命令行上。

在版本的 Visual Studio 2017 版本 15.3，在编译器开始 **/ 宽松-** 选项集[/Zc:ternary](../../build/reference/zc-ternary.md)选项。 编译器还实现两阶段的名称查找的要求的详细信息。 当 **/ 宽松-** 设置选项，编译器分析函数和类模板定义中，标识了模板中使用的相关和非依赖名称。 在此版本中，执行仅名称依赖项分析。

不受特定于环境的扩展和标准离开的实现的语言区域 **/ 宽松-**。 例如，特定于 Microsoft 的`__declspec`，不会调用约定和结构化的异常处理关键字，和特定于编译器的杂注指令或属性中的编译器将标记 **/ 宽松-** 模式。

**/ 宽松-** 选项使用的一致性支持当前的编译器版本中来确定哪些语言构造是不符合要求。 选项不确定你的代码是否符合 c + + 标准的特定版本。 若要启用针对最新草稿标准的所有实现的编译器支持，使用[/std:latest](../../build/reference/std-specify-language-standard-version.md)选项。 若要限制对当前实现 C + + 17 标准编译器支持，请使用[/std:c + + 17](../../build/reference/std-specify-language-standard-version.md)选项。 若要限制以更接近 C + + 14 标准的编译器支持，使用[/std:c + + 14](../../build/reference/std-specify-language-standard-version.md)选项，这是默认值。

未列出所有 C + + 11、 C + + 14 中或 C + + 17 符合标准的代码支持 Visual Studio 自 2017 年中的 Visual c + + 编译器。 具体取决于 Visual Studio 中，版本 **/ 宽松-** 选项可能无法检测到问题有关的两阶段的名称查找某些方面，绑定到临时的非常量引用，将复制 init 视为直接 init，允许多个用户定义的转换中初始化或备用令牌对于逻辑运算符和其他不受支持的一致性区域。 有关 Visual C++ 中一致性问题的详细信息，请参阅 [Nonstandard Behavior](../../cpp/nonstandard-behavior.md)。 若要充分利用获取 **/ 宽松-**，更新到最新版本的 Visual Studio。

### <a name="how-to-fix-your-code"></a>如何修复你的代码

下面是一些示例检测为不符合要求时使用的代码 **/ 宽松-**，以及建议如何修复问题。

#### <a name="use-default-as-an-identifier-in-native-code"></a>使用默认值为本机代码中的标识符

```cpp
void func(int default); // Error C2321: 'default' is a keyword, and
                        // cannot be used in this context
```

#### <a name="lookup-members-in-dependent-base"></a>查找依赖基中的成员

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

#### <a name="use-of-qualified-names-in-member-declarations"></a>使用成员声明中的限定名称

```cpp
struct A {
    void A::f() { } // error C4596: illegal qualified name in member
                    // declaration.
                    // Remove redundant 'A::' to fix.
};
```

#### <a name="initialize-multiple-union-members-in-a-member-initializer"></a>初始化成员初始值设定项中的多个联合成员

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

#### <a name="hidden-friend-name-lookup-rules"></a>隐藏的友元名称查找规则

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

#### <a name="use-scoped-enums-in-array-bounds"></a>在数组边界内使用区分范围的枚举

```cpp
enum class Color {
    Red, Green, Blue
};

int data[Color::Blue]; // error C3411: 'Color' is not valid as the size
                       // of an array as it is not an integer type.
                       // Cast to type size_t or int to fix.
```

#### <a name="use-for-each-in-native-code"></a>使用本机代码中的 for each

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

#### <a name="ambiguous-conditional-operator-arguments"></a>不明确的条件运算符的自变量

在 Visual Studio 2017 版本 15.3 之前编译器的版本中，编译器接受的条件运算符 （或三元运算符） 参数`?:`，它们将被视为不明确的标准。 在 **/ 宽松-** 模式下，编译器现将发出一个或多个诊断在编译而无需在早期版本中的诊断的情况下。

此更改，可能会导致的常见错误包括：

- 错误 C2593: operator？ 不明确

- 错误 C2679： 二进制？： 没有找到运算符采用 B 的右操作数的类型 （或没有可接受的转换）

- 错误 C2678： 二进制？： 未找到接受的左操作数的类型 A （或没有可接受的转换）

- 错误 C2446::： 从 B 不转换为 A

C 的某个类为类型为 t。 提供从另一种类型 T 的隐式构造函数和非显式转换运算符时可能会导致此问题的典型代码模式在这种情况下，第二个自变量转换的一种第三和第三个自变量到的第二个类型的转换是有效的转换，从而使不明确根据标准。

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

没有为此通用模式重要异常时 T 表示 null 结尾的字符串类型之一 (例如， `const char *`， `const char16_t *`，依次类推) 和实际自变量`?:`是字符串文本的相应的类型。 C + + 17 已从 C + + 14 更改语义。 因此，示例 2 中的代码接受下 **/std:c + + 14**和拒绝下 **/std:c + + 17**时 **/Zc:ternary**或 **/permissive-** 使用。

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

其中可能会看到错误的另一种是在带有一个自变量的类型的条件运算符`void`。 这种情况下可能很常见中断言类似宏。

```cpp
// Example 3: void arguments
void myassert(const char* text, const char* file, int line);
// Accepted when /Zc:ternary or /permissive- is not used:
#define ASSERT_A(ex) (void)((ex) ? 1 : myassert(#ex, __FILE__, __LINE__))
// Accepted always:
#define ASSERT_B(ex) (void)((ex) ? void() : myassert(#ex, __FILE__, __LINE__))
```

您还可能看到的模板元编程，条件运算符的结果类型在其中下可能更改中的错误 **/Zc:ternary**和 **/ 宽松-**。 解决此问题是使用一种方法[std::remove_reference](../../standard-library/remove-reference-class.md)上生成的类型。

```cpp
// Example 4: different result types
extern bool cond;
extern int count;
char  a = 'A';
const char  b = 'B';
decltype(auto) x = cond ? a : b; // char without, const char& with /Zc:ternary
const char (&z)[2] = count > 3 ? "A" : "B"; // const char* without /Zc:ternary
```

#### <a name="two-phase-name-look-up"></a>两阶段的名称查找

当 **/ 宽松-** 设置选项，编译器分析函数和类模板定义中，标识所需的模板中用于两阶段的名称查找的相关和非依赖名称。 在 Visual Studio 2017 版本 15.3，执行名称依赖项分析。 具体而言，未在模板定义的上下文中声明的非相关名称导致作为按 ISO c + + 标准所需的诊断消息。 在 Visual Studio 2017 15.7 版，还完成的需要自变量依赖查找定义上下文中的非依赖名称的绑定。

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

如果希望将旧行为两阶段 lookup 来说，但否则 **/ 宽松-** 行为，添加 **/Zc:twoPhase-** 选项。

### <a name="windows-header-issues"></a>Windows 标头问题

**/ 宽松-** 选项设置为之前 Windows 秋季创建者更新 SDK (10.0.16299.0)，Windows 工具包的版本或 Windows 驱动程序工具包 (WDK) 版本 1709年太严格。 我们建议你更新到最新版本的 Windows 套件，以便使用 **/ 宽松-** 在 Windows 或设备驱动程序代码。

某些 Windows 年 4 月 2018年更新 SDK (10.0.17134.0)、 Windows 秋季创建者更新 SDK (10.0.16299.0) 或 Windows 驱动程序工具包 (WDK) 1709 中的标头文件仍具有使它们与使用的不兼容的问题 **/permissive-**. 若要解决这些问题，我们建议你将使用这些标头限制到源代码的那些文件，需要它们，并删除 **/ 宽松-** 选项编译这些特定的源代码文件时。

发布这些 WinRT WRL 标头在窗口中年 4 月 2018年更新 SDK (10.0.17134.0) 不是使用干净 **/ 宽松-**。 若要解决这些问题，请不要将 **/ 宽松-**，或使用 **/ 宽松-** 与 **/Zc:twoPhase-** 时使用这些标头：

- Winrt/wrl/async.h 中的问题

   ```Output
   C:\Program Files (x86)\Windows Kits\10\Include\10.0.17134.0\winrt\wrl\async.h(483): error C3861: 'TraceDelegateAssigned': identifier not found
   C:\Program Files (x86)\Windows Kits\10\Include\10.0.17134.0\winrt\wrl\async.h(491): error C3861: 'CheckValidStateForDelegateCall': identifier not found
   C:\Program Files (x86)\Windows Kits\10\Include\10.0.17134.0\winrt\wrl\async.h(509): error C3861: 'TraceProgressNotificationStart': identifier not found
   C:\Program Files (x86)\Windows Kits\10\Include\10.0.17134.0\winrt\wrl\async.h(513): error C3861: 'TraceProgressNotificationComplete': identifier not found
   ```

- 发出 winrt/wrl/implements.h 中

   ```Output
   C:\Program Files (x86)\Windows Kits\10\include\10.0.17134.0\winrt\wrl\implements.h(2086): error C2039: 'SetStrongReference': is not a member of 'Microsoft::WRL::Details::WeakReferenceImpl'
   ```

发布这些用户模式下标头在窗口中年 4 月 2018年更新 SDK (10.0.17134.0) 不是使用干净 **/ 宽松-**。 若要解决这些问题，不要使用 **/ 宽松-** 时使用这些标头：

- Um/Tune.h 中的问题

   ```Output
   C:\ProgramFiles(x86)\Windows Kits\10\include\10.0.17134.0\um\tune.h(139): error C3861: 'Release': identifier not found
   C:\Program Files (x86)\Windows Kits\10\include\10.0.17134.0\um\tune.h(559): error C3861: 'Release': identifier not found
   C:\Program Files (x86)\Windows Kits\10\include\10.0.17134.0\um\tune.h(1240): error C3861: 'Release': identifier not found
   C:\Program Files (x86)\Windows Kits\10\include\10.0.17134.0\um\tune.h(1240): note: 'Release': function declaration must be available as none of the arguments depend on a template parameter
   ```

- 发出 um/spddkhlp.h 中

   ```Output
   C:\Program Files (x86)\Windows Kits\10\include\10.0.17134.0\um\spddkhlp.h(759): error C3861: 'pNode': identifier not found
   ```

- Um/refptrco.h 中的问题

   ```Output
   C:\Program Files (x86)\Windows Kits\10\include\10.0.17134.0\um\refptrco.h(179): error C2760: syntax error: unexpected token 'identifier', expected 'type specifier'
   C:\Program Files (x86)\Windows Kits\10\include\10.0.17134.0\um\refptrco.h(342): error C2760: syntax error: unexpected token 'identifier', expected 'type specifier'
   C:\Program Files (x86)\Windows Kits\10\include\10.0.17134.0\um\refptrco.h(395): error C2760: syntax error: unexpected token 'identifier', expected 'type specifier'
   ```

这些问题是特定于用户模式下在 Windows 秋季创建者更新 SDK (10.0.16299.0) 中的标头：

- 发出 um/Query.h 中

   使用时 **/ 宽松-** 编译器开关，`tagRESTRICTION`结构不能编译由于 case(RTOr) 成员 '。

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

   若要解决此问题，程序文件编译包括而无需 Query.h **/ 宽松-** 选项。

- 发出 um/cellularapi_oem.h 中

   使用时 **/ 宽松-** 编译器开关、 的前向声明`enum UICCDATASTOREACCESSMODE`导致警告：

   ```cpp
   typedef enum UICCDATASTOREACCESSMODE UICCDATASTOREACCESSMODE; // C4471
   ```

   未区分范围的前向声明是枚举的 Microsoft 扩展。 若要解决此问题，编译包含而无需 cellularapi_oem.h 文件 **/ 宽松-** 选项，或使用[/wd](../../build/reference/compiler-option-warning-level.md)静音警告 C4471 的选项。

- 发出 um/omscript.h 中

   在 C + + 03 中，从字符串转换为 BSTR (即的 typedef wchar_t *) 是不推荐使用，但允许。 在 C + + 11 中，不再允许转换。

   ```cpp
   virtual /* [id] */ HRESULT STDMETHODCALLTYPE setExpression(
       /* [in] */ __RPC__in BSTR propname,
       /* [in] */ __RPC__in BSTR expression,
       /* [in][defaultvalue] */ __RPC__in BSTR language = L"") = 0; // C2440
   ```

   若要解决此问题，程序文件编译包括而无需 omscript.h **/ 宽松-** 选项，或使用 **/Zc:strictStrings-** 相反。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此编译器选项

在 Visual Studio 2017 版本 15.5 和更高版本中，使用此过程：

1. 打开你的项目的**属性页**对话框。

1. 选择**配置属性** > **C/c + +** > **语言**属性页。

1. 更改**一致性模式**属性值设置为**是 (/ 宽松-)**。 选择**确定**或**应用**以保存所做的更改。

在 Visual Studio 2017 版本 15.5 之前的版本，使用此过程：

1. 打开你的项目的**属性页**对话框。

1. 选择**配置属性** > **C/c + +** > **命令行**属性页。

1. 输入 **/ 宽松-** 中的编译器选项**其他选项**框。 选择**确定**或**应用**以保存所做的更改。

### <a name="to-set-this-compiler-option-programmatically"></a>以编程方式设置此编译器选项

- 请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>。

## <a name="see-also"></a>请参阅

- [编译器选项](../../build/reference/compiler-options.md)
- [设置编译器选项](../../build/reference/setting-compiler-options.md)
