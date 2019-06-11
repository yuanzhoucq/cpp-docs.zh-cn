---
title: C++ 的符合性改进
ms.date: 05/16/2019
description: Visual Studio 2019 中的 Microsoft C++ 正朝着完全符合 C++20 语言标准的方向发展。
ms.technology: cpp-language
author: mikeblome
ms.author: mblome
ms.openlocfilehash: 02b778f10ad94342c922a4e79a856cc2a7d53076
ms.sourcegitcommit: 28eae422049ac3381c6b1206664455dbb56cbfb6
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/31/2019
ms.locfileid: "66451216"
---
# <a name="c-conformance-improvements-in-visual-studio-2019-rtw-and-version-161improvements161"></a>Visual Studio 2019 RTW 和版本 [16.1](#improvements_161) 中的 C++ 符合性改进

## <a name="improvements-in-visual-studio-2019-rtw"></a>Visual Studio 2019 RTW 中的改进

Visual Studio 2019 RTW 包含 Microsoft C++ 编译器 (MSVC) 的以下符合性改进、bug 修复和行为变更。

**注意：** C++20 功能将在 `/std:c++latest` 模式下提供，直到编译器和 IntelliSense 的 C++20 实现完成。 届时，将推出 `/std:c++20` 编译器模式。

### <a name="improved-modules-support-for-templates-and-error-detection"></a>针对模板和错误检测的改进模块支持

模块现在正式采用 C++20 标准。 Visual Studio 2017 版本 15.9 中增加了改进的支持。 有关详细信息，请参阅 [MSVC 2017 版本 15.9 中针对 C++ 模块的更好模板支持和错误检测](https://devblogs.microsoft.com/cppblog/better-template-support-and-error-detection-in-c-modules-with-msvc-2017-version-15-9/)。

### <a name="modified-specification-of-aggregate-type"></a>修改了聚合类型的规范

C++20 中的聚合类型规范已更改（请参阅[禁止使用用户声明的构造函数聚合](https://wg21.link/p1008r1)）。 在 `/std:c++latest` 下的 Visual Studio 2019 中，具有任何用户声明的构造函数的类（例如，包括声明为 `= default` 或 `= delete` 的构造函数）均不是聚合。 之前，仅用户提供的构造函数才会使类失去成为聚合的资格。 此更改对如何初始化此类类型进行了额外限制。

在 Visual Studio 2017 中编译以下代码时不会引发错误，但在 `/std:c++latest` 下的 Visual Studio 2019 中会引发错误 C2280 和 C2440：

```cpp
struct A
{
    A() = delete; // user-declared ctor
};

struct B
{
    B() = default; // user-declared ctor
    int i = 0;
};

A a{}; // ill-formed in C++20, previously well-formed
B b = { 1 }; // ill-formed in C++20, previously well-formed
```

### <a name="partial-support-for-operator-"></a>对运算符 <=> 的部分支持

[P0515R3](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0515r3.pdf) C++20 引入 `<=>` 三向比较运算符，也称为“太空船运算符”。 `/std:c++latest` 模式下的 Visual Studio 2019 通过针对现在被禁用的语法引发错误，引入对运算符的部分支持。 例如，在 Visual Studio 2017 中编译以下代码时不会引发错误，但在 `/std:c++latest` 下的 Visual Studio 2019 中会引发多个错误：

```cpp
struct S
{
       bool operator<=(const S&) const { return true; }
};

template <bool (S::*)(const S&) const>
struct U { };
int main(int argc, char** argv)
{
       U<&S::operator<=> u; // In Visual Studio 2019 raises C2039, 2065, 2146.
}
```

若要避免这些错误，请在最后一个括号之前有问题的行中插入一个空格：`U<&S::operator<= > u;`。

### <a name="references-to-types-with-mismatched-cv-qualifiers"></a>对具有不匹配的 cv 限定符的类型的引用

MSVC 之前允许直接绑定来自具有顶级以下不匹配 cv 限定符的类型的引用。 此规则允许修改被引用所引用的假定 const 数据，且编译器现在会根据标准的要求创建临时数据。 在 Visual Studio 2017 中，编译以下代码时不会发出警告。 在 Visual Studio 2019 中，编译器引发警告 *C4172: \<func:#1 "?PData@X@@QBEABQBXXZ"> 返回局部变量或临时变量的地址*。

```cpp
struct X
{
    const void* const& PData() const
    {
        return _pv;
    }

    void* _pv;
};

int main()
{
    X x;
    auto p = x.PData(); // C4172
}
```
### <a name="reinterpretcast-from-an-overloaded-function"></a>来自重载函数的 `reinterpret_cast`

`reinterpret_cast` 的参数不属于允许使用重载函数地址的上下文。 在 Visual Studio 2017 中编译以下代码时不会引发错误，但在 Visual Studio 2019 中，它会引发 *C2440: 无法从 “overloaded-function” 转换为 “fp”* ：

```cpp
int f(int) { return 1; }
int f(float) { return .1f; }
using fp = int(*)(int);

int main()
{
    fp r = reinterpret_cast<fp>(&f);
}
```

若要避免该错误，请为此方案使用允许的强制转换：

```cpp
int f(int);
int f(float);
using fp = int(*)(int);

int main()
{
    fp r = static_cast<fp>(&f); // or just &f;
}
```

### <a name="lambda-closures"></a>Lambda 闭包

在 C++14 中，lambda 闭包类型不是文本。 此规则的主要后果是 lambda 可能不会分配给 `constexpr` 变量。 在 Visual Studio 2017 中编译以下代码时不会引发错误，但在 Visual Studio 2019 中，它会引发 *C2127: “l”: 使用非常量表达式非法初始化 “constexpr” 实体*：

```cpp
int main()
{
    constexpr auto l = [] {}; // C2127 in VS2019
}
```

若要避免该错误，请删除 `constexpr` 限定符，或将符合性模式更改为 `/std:c++17`。

### <a name="stdcreatedirectory-failure-codes"></a>std::create_directory 故障代码

根据 C++20 无条件地实现了 [P1164](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2019/p1164r1.pdf)。 这会更改 `std::create_directory` 来检查目标是否已经为故障目录。 之前，所有 ERROR_ALREADY_EXISTS 类型错误都会转换为成功但未创建目录的代码。

### <a name="operatorstdostream-nullptrt"></a>operator<<(std::ostream, nullptr_t)

根据 [LWG 2221](https://cplusplus.github.io/LWG/issue2221)，增加了 `operator<<(std::ostream, nullptr_t)` 用于将 nullptr 写入数据流。 

### <a name="additional-parallel-algorithms"></a>其他并行算法

`is_sorted`、`is_sorted_until`、`is_partitioned`、`set_difference`、`set_intersection`、`is_heap` 和 `is_heap_until` 的新并行版本。

### <a name="atomic-initialization"></a>原子初始化

[P0883“修复原子初始化”](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2018/p0883r1.pdf)将 `std::atomic` 更改为对包含的 T 进行值初始化，而不是默认初始化。 将 Clang/LLVM 与 Microsoft 标准库配合使用时，将启用此修复。 当前对 Microsoft C++ 编译器禁用此修复，以用作 constexpr 处理中 bug 的解决方法。

### <a name="removecvref-and-removecvreft"></a>remove_cvref 和 remove_cvref_t

根据 [P0550](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0550r2.pdf) 实现了 `remove_cvref` 和 `remove_cvref_t` 类型特征。 这些类型特征可从类型移除引用性和 cv 限定，而无需将函数和数组衰减为指针（与 `std::decay` 和 `std::decay_t` 不同）。

### <a name="feature-test-macros"></a>功能测试宏

[P0941R2 - 功能测试宏](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2018/p0941r2.html)已完成，支持 `__has_cpp_attribute`。 所有标准模式都支持功能测试宏。

### <a name="prohibit-aggregates-with-user-declared-constructors"></a>禁止使用用户声明的构造函数进行聚合

[C++20 P1008R1 - 禁止使用用户声明的构造函数进行聚合](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2018/p1008r1.pdf)已完成。

## <a name="improvements_161"></a>Visual Studio 2019 版本 16.1 中的改进

### <a name="char8t"></a>char8_t

[P0482r6](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2018/p0482r6.html)。 C++20 增加了新的字符类型，可用于表示 UTF-8 代码单元。 C++20 中的 u8 字符串文本具有 `const char8_t[N]` 类型而不是 `const char[N]` 类型，这是之前的情况。 在 [N2231](http://www.open-std.org/jtc1/sc22/wg14/www/docs/n2231.htm) 中已针对 C 标准提出了类似的更改。 在 [P1423r0](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2019/p1423r0.html) 中给出了有关 char8_t 后向兼容性修正的建议。 如果指定 **/Zc:char8_t** 编译器选项，Microsoft C++ 编译器会在 Visual Studio 2019 版本 16.1 中添加对 char8_t 的支持。 将来，[/std:c++latest](../../build/reference/std-specify-language-standard-version.md) 将支持它，其可通过 **/Zc:char8_t-** 还原为 C++17 行为。 为 IntelliSense 提供支持的 EDG 编译器尚不支持它，因此将看到虚假的仅限于 IntelliSense 的错误，这些错误不会影响实际编译。

#### <a name="example"></a>示例

```cpp
const char* s = u8"Hello"; // C++17
const char8_t* s = u8"Hello"; // C++20
```

### <a name="stdtypeidentity-metafunction-and-stdidentity-function-object"></a>std::type_identity 元函数和  std::identity 函数对象

[P0887R1 type_identity](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2018/p0887r1.pdf)。 弃用的 `std::identity` 类模板扩展已删除，并替换为 C++20 `std::type_identity` 元函数和 `std::identity` 函数对象。 两者仅在 [/std:c++latest](../../build/reference/std-specify-language-standard-version.md) 下可用。 

以下示例在 Visual Studio 2017 中针对 `std::identity`（在 \<type_traits> 中定义）生成弃用警告 C4996： 

```cpp
#include <type_traits>

using T = std::identity<int>::type;
T x, y = std::identity<T>{}(x);
int i = 42;
long j = std::identity<long>{}(i);
```

以下示例显示如何将新的 `std::identity`（在 \<functional> 中定义）与新的 `std::type_identity` 配合使用：

```cpp
#include <type_traits>
#include <functional>

using T = std::type_identity<int>::type;
T x, y = std::identity{}(x);
int i = 42;
long j = static_cast<long>(i);
```

### <a name="syntax-checks-for-generic-lambdas"></a>针对泛型 lambda 的语法检查

在 [/std:c++latest](../../build/reference/std-specify-language-standard-version.md) 下或在 **/experimental:newLambdaProcessor** 的任何其他语言模式下，新的 lambda 处理器在泛型 lambda 中启用部分符合性模式语法检查。 

在 Visual Studio 2017 中编译此代码时不会出现警告，但在 Visual Studio 2019 中，它会生成错误 *C2760 语法错误: 意外令牌 “\<id-expr>”，需要 “id-expression”* ：

```cpp
void f() {
    auto a = [](auto arg) {
        decltype(arg)::Type t;
    };
}
```

以下示例显示正确的语法，现在由编译器强制执行：

```cpp
void f() {
    auto a = [](auto arg) {
        typename decltype(arg)::Type t;
    };
}
```

### <a name="argument-dependent-lookup-for-function-calls"></a>函数调用的依赖于参数的查找

[P0846R0](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0846r0.html) (C++20) 增加了通过针对包含显式模板参数的函数调用表达式的依赖于参数的查找来查找函数模板的功能。 需要 **/std:c++latest**。

### <a name="designated-initialization"></a>指定的初始化

[P0329R4](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0329r4.pdf) (C++20) 指定的初始化允许在聚合初始化中通过使用 `Type t { .member = expr }` 语法选择特定成员。 需要 **/std:c++latest**。

### <a name="new-and-updated-standard-library-functions-c20"></a>新的和更新的标准库函数 (C++20)

- 用于 `basic_string` 和 `basic_string_view` 的 `starts_with()` 和 `ends_with()`。
- 关联容器的 `contains()`。
- 用于 ` list` 和 `forward_list` 的 `remove()`、`remove_if()` 和 `unique()` 现在返回 `size_type`。
- `shift_left()` 和 `shift_right()` 已添加到 \<algorithm> 中。

## <a name="bug-fixes-and-behavior-changes-in-visual-studio-2019-rtw"></a>Visual Studio 2019 RTW 中的 bug 修复和行为变更

### <a name="correct-diagnostics-for-basicstring-range-constructor"></a>basic_string 范围构造函数的正确诊断

在 Visual Studio 2019 中，`basic_string` 范围构造函数不再禁止显示包含 `static_cast` 的编译器诊断。 尽管在初始化 `out` 时可能会丢失从 `wchar_t` 到 `char` 的数据，但在 Visual Studio 2017 中编译以下代码时不会出现警告：

```cpp
std::wstring ws = /* … */;
std::string out(ws.begin(), ws.end());
```

Visual Studio 2019 正确引发 *C4244: “argument”: 从 “wchar_t” 转换到 “const _Elem”，可能会丢失数据*。 若要避免该警告，可初始化 std::string，如以下示例所示：

```cpp
std::wstring ws = L"Hello world";
std::string out;
for (wchar_t ch : ws)
{
    out.push_back(static_cast<char>(ch));
}
```

### <a name="incorrect-calls-to--and---under-clr-or-zw-are-now-correctly-detected"></a>现在可正确检测到在 /clr or /ZW 下对 += 和 -= 的不正确调用

Visual Studio 2017 中引入了一个 bug，其会导致编译器以静默方式忽略错误，并且不会为 `/clr` 或 `/ZW` 下对 += 和 -= 的无效调用生成代码。 在 Visual Studio 2017 中编译以下代码时不会引发错误，但在 Visual Studio 2019 中，它会正确引发错误 *C2845:“System::String ^”: 不允许在此类型中使用指针算数*：

```cpp
public enum class E { e };

void f(System::String ^s)
{
    s += E::e; // C2845 in VS2019
}
```

若要避免此示例中的错误，请将运算符与 ToString() 方法配合使用：`s += E::e.ToString();`。

### <a name="initializers-for-inline-static-data-members"></a>内联静态数据成员的初始化表达式

现在可正确检测到 `inline` 和 `static constexpr` 初始化表达式中的无效成员访问。 在 Visual Studio 2017 中编译以下示例时不会引发错误，但在 `/std:c++17` 模式下的 Visual Studio 2019 中，它会引发错误 *C2248: 无法访问在 “X” 类中声明的私有成员*。

```cpp
struct X
{
    private:
        static inline const int c = 1000;
};

struct Y : X
{
    static inline int d = c; // C2248 in Visual Studio 2019
};
```

若要避免该错误，请将 `X::c` 成员声明为受保护：

```cpp
struct X
{
    protected:
        static inline const int c = 1000;
};
```

### <a name="c4800-reinstated"></a>C4800 已恢复

MSVC 曾有一个关于隐式转换为布尔值的性能警告 C4800，该警告存在太多干扰且无法禁止显示，这导致我们在 Visual Studio 2017 中将其删除。 但是，在 Visual Studio 2017 的生命周期中，我们收到了大量关于其解决的有用案例的反馈。 我们在 Visual Studio 2019 中重新推出了精心定制的 C4800 及其随附的 C4165，两个警告都可以通过显式强制转换或与相应类型的 0 进行比较来轻松地禁止显示。 C4800 是默认关闭的 4 级警告，C4165 是默认关闭的 3 级警告。 使用 `/Wall` 编译器选项可以发现这两个警告。

以下示例在 `/Wall` 下引发 C4800 和 C4165：

```cpp
bool test(IUnknown* p)
{
    bool valid = p; // warning C4800: Implicit conversion from 'IUnknown*' to bool. Possible information loss
    IDispatch* d = nullptr;
    HRESULT hr = p->QueryInterface(__uuidof(IDispatch), reinterpret_cast<void**>(&d));
    return hr; // warning C4165: 'HRESULT' is being converted to 'bool'; are you sure this is what you want?
}
```

若要避免上一示例中的警告，可编写如下代码：

```cpp
bool test(IUnknown* p)
{
    bool valid = p != nullptr; // OK
    IDispatch* d = nullptr;
    HRESULT hr = p->QueryInterface(__uuidof(IDispatch), reinterpret_cast<void**>(&d));
    return SUCCEEDED(hr);  // OK
}
```

### <a name="local-class-member-function-doesnt-have-a-body"></a>局部类成员函数没有函数体

在 Visual Studio 2017 中，*C4822:局部类成员函数没有函数体*仅在显式设置编译器选项 `/w14822` 时才会引发；它不会随 `/Wall` 一起显示。 在 Visual Studio 2019 中，C4822 是默认关闭的警告，这使得其在 `/Wall` 下可被发现，而无需显式设置 `/w14822`。

```cpp
void foo()
{
    struct A
        {
            int boo(); // warning C4822
        };
}
```

### <a name="function-template-bodies-containing-constexpr-if-statements"></a>包含 constexpr if 语句的函数模板体

包含 `if constexpr` 语句的模板函数体启用了一些与 `/permissive-` 分析相关的检查。 例如，在 Visual Studio 2017 中，以下代码生成 *C7510:“Type”: 使用依赖类型名称时必须使用 “typename” 作为前缀*，但仅当未设置 `/permissive-` 选项时才会生成此错误。 在 Visual Studio 2019 中，无论是否设置了 `/permissive-` 选项，相同的代码都会引发错误：

```cpp
template <typename T>

int f()
{
    T::Type a; // error C7510

    if constexpr (T::val)
    {
        return 1;
    }
    else
    {
        return 2;
    }
}

struct X
{
    using Type = X;
    constexpr static int val = 1;
};

int main()
{
    return f<X>();
}

```

若要避免该错误，请将 `typename` 关键字添加到 `a` 的声明中：`typename T::Type a;`。

### <a name="inline-assembly-code-is-not-supported-in-a-lambda-expression"></a>lambda 表达式不支持内联程序集代码

Visual C++ 团队最近获悉一个安全问题，即在 lambda 中使用内联汇编程序可能会导致“ebp”（返回地址寄存器）在运行时损坏。 恶意攻击者可能能够利用此方案。 鉴于问题的本质、内联汇编程序仅在 x86 上受到支持这一事实，以及内联汇编程序与编译器其余部分之间的交互性较差，这一问题可能的最安全解决方案是在 lambda 表达式中禁用内联汇编程序。

注意：“wild”中在 lambda 表达式内使用内联汇编程序的唯一一种情况是用于捕获返回地址。 在此方案中，只需使用编译器内部函数 `_ReturnAddress()` 即可在所有平台上捕获返回地址。

以下代码在 Visual Studio 2017 15.9 和 Visual Studio 2019 中均会生成 *C7552: lambda 不支持内联汇编程序*错误：

```cpp
#include <cstdio>

int f()
{
    int y = 1724;
    int x = 0xdeadbeef;

    auto lambda = [&]
    {
        __asm {

            mov eax, x
            mov y, eax
        }
    };

    lambda();
    return y;
}
```

若要避免该错误，请将程序集代码移动到命名函数中，如以下示例所示：

```cpp
#include <cstdio>

void g(int& x, int& y)
{
    __asm {
        mov eax, x
        mov y, eax
    }
}

int f()
{
    int y = 1724;
    int x = 0xdeadbeef;
    auto lambda = [&]
    {
        g(x, y);
    };
    lambda();
    return y;
}

int main()
{
    std::printf("%d\n", f());
}
```

### <a name="iterator-debugging-and-stdmoveiterator"></a>迭代器调试和 std::move_iterator

已讲解如何使用迭代器调试功能来正确解包 `std::move_iterator`。 例如，`std::copy(std::move_iterator<std::vector<int>::iterator>, std::move_iterator<std::vector<int>::iterator>, int*)` 现在可占用 `memcpy` 快速路径。

### <a name="fixes-for-xkeycheckh-keyword-enforcement"></a>对 \<xkeycheck.h> 关键字强制执行问题的修复

修复了标准库的宏化关键字强制执行 \<xkeycheck.h>，以发出检测到的实际问题关键字，而不是通用消息。 它还支持 C++20 关键字，并可避免以欺骗手段使 IntelliSense 将随机关键字视为宏。

### <a name="allocator-types-un-deprecated"></a>分配器类型已取消弃用

`std::allocator<void>`、`std::allocator::size_type` 和 `std::allocator::difference_type` 已取消弃用。

### <a name="correct-warning-for-narrowing-string-conversions"></a>缩短字符串转换的正确警告

从 std::string 中删除了意外禁止显示 C4244 缩短警告的标准未调用的虚假 `static_cast`。 如果尝试调用 `std::string::string(const wchar_t*, const wchar_t*)`，现在将正确地发出 *C4244“正在将 wchar_t 缩短为 char。”*

### <a name="various-filesystem-correctness-fixes"></a>各种 \<filesystem> 正确性修复

- 修复了 `std::filesystem::last_write_time` 在尝试更改目录的上次写入时间时失败的问题。
- 如果提供不存在的目标路径，`std::filesystem::directory_entry` 构造函数现在会存储失败的结果，而不引发异常。
- `std::filesystem::create_directory` 的 2 个参数的版本已更改为调用 1 个参数的版本，因为当 existing_p 为符号链接时，基础 `CreateDirectoryExW` 函数会执行 `copy_symlink`。
- 遇到损坏的符号链接时，`std::filesystem::directory_iterator` 不再失败。
- `std::filesystem::space` 现在接受相对路径。
- `std::filesystem::path::lexically_relative` 不再因尾部反斜杠而产生混淆（报告为 [LWG 3096](https://cplusplus.github.io/LWG/issue3096)）。
- 解决了 `CreateSymbolicLinkW` 拒绝 `std::filesystem::create_symlink` 中包含正斜杠的路径的问题。
- 解决了 Windows 10 LTSB 1609 上存在 POSIX 删除模式 `delete` 功能，但实际上无法删除文件的问题。
- `std::boyer_moore_searcher` 和 `std::boyer_moore_horspool_searcher` 的复制构造函数和复制赋值运算符现在实际上会复制内容。

### <a name="parallel-algorithms-on-windows-8-and-later"></a>Windows 8 及更高版本上的并行算法

并行算法库现在可以在 Windows 8 及更高版本上正确使用真实的 `WaitOnAddress` 系列，而不是始终使用 Windows 7 及早期虚假版本。

### <a name="stdsystemcategorymessage-whitespace"></a>std::system_category::message() 空格

`std::system_category::message()` 现在会截断返回消息的尾随空格。

### <a name="stdlinearcongruentialengine-divide-by-zero"></a>std::linear_congruential_engine 被零除

导致 `std::linear_congruential_engine` 触发被 0 除的一些条件已得到修复。

### <a name="fixes-for-iterator-unwrapping"></a>修复迭代器解包问题

在 Visual Studio 2017 15.8 中首次公开的用于程序员-用户集成的迭代器解包机制（如 https://devblogs.microsoft.com/cppblog/stl-features-and-fixes-in-vs-2017-15-8/ 中所述）不再解包从标准库迭代器派生的迭代器。 例如，从 `std::vector<int>::iterator` 派生并尝试自定义行为的用户现在在调用标准库算法时会获得其自定义行为，而不是指针的行为。
无序容器保留功能现在实际上为 N 个元素保留，如 [LWG 2156](https://cplusplus.github.io/LWG/issue2156) 中所述。

### <a name="time-handling"></a>时间处理

- 之前，传递给并发库的某些时间值会溢出，例如，`condition_variable::wait_for(seconds::max())`。 这些溢出问题现已修复，其在一个看似随机的 29 天周期（当基础 Win32 API 接受的 uint32_t 毫秒溢出时）中改变了行为。

- 除在全局命名空间中声明 timespec 和 timespec_get 之外，<ctime> 标头现在还可在 namespace std 中正确地声明它们。

### <a name="various-fixes-for-containers"></a>针对容器的各种修复

- 许多标准库内部容器函数都已变为专用，以改善 IntelliSense 体验。 在后续版本的 MSVC 中，预期会提供将成员标记为私有的其他修复。

- 基于节点的容器（如 `list`、`map` 和 `unordered_map`）将损坏的异常安全正确性问题已修复。 在 `propagate_on_container_copy_assignment` 或 `propagate_on_container_move_assignment` 重新分配操作期间，我们将使用旧分配器释放容器的 sentinel 节点、通过旧分配器执行 POCCA/POCMA 分配，然后尝试从新分配器获取 sentinel 节点。 如果此分配失败，则容器会损坏且甚至可能无法销毁，因为拥有 sentinel 节点是硬数据结构所固有的特点。 修复此问题是为了在销毁现有 sentinel 节点之前通过源容器的分配器分配新的 sentinel 节点。

- 根据 `propagate_on_container_copy_assignment`、`propagate_on_container_move_assignment` 和 `propagate_on_container_swap`，容器固定为始终复制/移动/交换分配器，即使对于声明为 `is_always_equal` 的分配器也是如此。

- 根据 [P0083“拼接映射和集”](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0083r3.pdf)，为容器合并以及接受右值容器的提取成员函数添加了重载

### <a name="stdbasicistreamread-processing-of-rn--n"></a>\r\n => \n 的 std::basic_istream::read 处理

`std::basic_istream::read` 已修复为不作为 \r\n => \n 处理的一部分临时写入提供的缓冲区部分。 此修复放弃了 Visual Studio 2017 15.8 中获得的大小超过 4K 的读取操作的一些性能优势，但仍然因避免对每个字符进行 3 次虚拟调用而获得了效率提升。

### <a name="stdbitset-constructor"></a>std::bitset 构造函数

对于大型 bitset，`std::bitset` 的构造函数不再以相反的顺序读取 1 和 0。

### <a name="stdpairoperator-regression"></a>std::pair::operator= 回归

修复了在实现 [LWG 2729 “std::pair::operator= 上缺少 SFINAE”](https://cplusplus.github.io/LWG/issue2729)时引入的 `std::pair` 赋值运算符回归问题。 它现在能够再次正确接受可转换为 `std::pair` 的类型。

### <a name="non-deduced-contexts-for-addconstt"></a>add_const_t 的非导出上下文

修复了一个有关类型特征的小 bug，其中 `add_const_t` 和相关函数应该是非导出上下文。 换而言之，`typename add_const<T>::type` 的别名应该是 `add_const_t`，而不是 `const T`。

## <a name="see-also"></a>请参阅

[Visual Studio 2019 中的新增功能](../what-s-new-for-visual-cpp-in-visual-studio.md)