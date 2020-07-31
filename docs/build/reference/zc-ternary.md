---
title: /Zc:ternary（强制实施条件运算符规则）
ms.date: 09/12/2019
f1_keywords:
- /Zc:ternary
helpviewer_keywords:
- /Zc:ternary
- Zc:ternary
- -Zc:ternary
ms.openlocfilehash: 04bd0c49528d86ddd4d1e6c77804cf64278db188
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87211874"
---
# <a name="zcternary-enforce-conditional-operator-rules"></a>`/Zc:ternary`（强制条件运算符规则）

为条件运算符表达式中的第二个和第三个操作数启用 c + + 标准规则的强制实施。

## <a name="syntax"></a>语法

> **`/Zc:ternary`**[**`-`**]

## <a name="remarks"></a>备注

从 Visual Studio 2017 开始，编译器支持 c + + 标准*条件运算符*（ **`?:`** ）行为。 它也称为*三元运算符*。 C + + 标准要求三元操作数满足以下三个条件之一：操作数必须具有相同的类型和 **`const`** 或 **`volatile`** 限定（cv 限定），或者只有一个操作数必须可明确转换为同一类型和 cv 限定。 或者，一个或两个操作数必须是 throw 表达式。 在 Visual Studio 2017 版本15.5 之前的版本中，编译器允许由标准视为不明确的转换。

当 **`/Zc:ternary`** 指定选项时，编译器将符合标准。 它拒绝不满足匹配类型和第二个和第三个操作数的 cv 限定规则的代码。

**`/Zc:ternary`** 默认情况下，此选项在 Visual Studio 2017 中处于关闭状态。 使用 **`/Zc:ternary`** 启用一致的行为，或 **`/Zc:ternary-`** 显式指定以前的不一致编译器行为。 [`/permissive-`](permissive-standards-conformance.md)选项隐式启用此选项，但可以使用重写它 **`/Zc:ternary-`** 。

### <a name="examples"></a>示例

此示例演示如何从类型提供非显式初始化并转换为类型的类可能导致不明确的转换。 默认情况下，编译器接受此代码，但在 **/`Zc:ternary`** 指定了或时被拒绝 **`/permissive-`** 。

```cpp
// zcternary1.cpp
// Compile by using: cl /EHsc /W4 /nologo /Zc:ternary zcternary1.cpp

struct A
{
   long l;
   A(int i) : l{i} {}    // explicit prevents conversion of int
   operator int() const { return static_cast<int>(l); }
};

int main()
{
   A a(42);
   // Accepted when /Zc:ternary (or /permissive-) is not used
   auto x = true ? 7 : a;  // old behavior prefers A(7) over (int)a
   auto y = true ? A(7) : a;   // always accepted
   auto z = true ? 7 : (int)a; // always accepted
   return x + y + z;
}
```

若要修复此代码，请显式强制转换为首选的通用类型，或防止出现类型转换的一个方向。 可以通过显式转换来保持编译器与类型转换的匹配。

当操作数的类型为以 null 结尾的字符串类型之一（例如、等）时，这种常见模式是一个重要的例外情况 `const char*` `const char16_t*` 。 你还可以通过数组类型以及它们所衰减到的指针类型来重现该效果。 当实际的第二个或第三个操作数为 `?:` 相应类型的字符串文字时，行为取决于所使用的语言标准。 C + + 17 已更改了 c + + 14 中此情况的语义。 因此，编译器接受默认的以下示例中的代码 **`/std:c++14`** ，但在指定时将其拒绝 **`/std:c++17`** 。

```cpp
// zcternary2.cpp
// Compile by using: cl /EHsc /W4 /nologo /Zc:ternary /std:c++17 zcternary2.cpp

struct MyString
{
   const char * p;
   MyString(const char* s = "") noexcept : p{s} {} // from char*
   operator const char*() const noexcept { return p; } // to char*
};

int main()
{
   MyString s;
   auto x = true ? "A" : s; // MyString: permissive prefers MyString("A") over (const char*)s
}
```

若要修复此代码，请显式强制转换其中一个操作数。

在下 **`/Zc:ternary`** ，编译器拒绝条件运算符，其中一个参数的类型为，另一个参数不 **`void`** 是 **`throw`** 表达式。 此模式的一种常见用法是类似于断言的宏：

```cpp
// zcternary3.cpp
// Compile by using: cl /EHsc /W4 /nologo /Zc:ternary /c zcternary3.cpp

void myassert(const char* text, const char* file, int line);
#define ASSERT(ex) (void)((ex) ? 0 : myassert(#ex, __FILE__, __LINE__))
// To fix, define it this way instead:
// #define ASSERT(ex) (void)((ex) ? void() : myassert(#ex, __FILE__, __LINE__))

int main()
{
   ASSERT(false);  // C3447
}
```

典型的解决方案是将非 void 参数替换为 `void()` 。

此示例显示了在和下生成错误的 **`/Zc:ternary`** 代码 **`/Zc:ternary-`** ：

```cpp
// zcternary4.cpp
// Compile by using:
//   cl /EHsc /W4 /nologo /Zc:ternary zcternary4.cpp
//   cl /EHsc /W4 /nologo /Zc:ternary zcternary4.cpp

int main() {
   auto p1 = [](int a, int b) { return a > b; };
   auto p2 = [](int a, int b) { return a > b; };
   auto p3 = true ? p1 : p2; // C2593 under /Zc:ternary, was C2446
}
```

此代码先前提供此错误：

```Output
error C2446: ':': no conversion from 'foo::<lambda_f6cd18702c42f6cd636bfee362b37033>' to 'foo::<lambda_717fca3fc65510deea10bc47e2b06be4>'
note: No user-defined-conversion operator available that can perform this conversion, or the operator cannot be called
```

对于 **`/Zc:ternary`** ，失败的原因变得更清晰。 可以使用多个实现定义的调用约定中的任何一个来生成每个 lambda。 但编译器没有首选项规则来消除可能的 lambda 签名。 新的输出如下所示：

```Output
error C2593: 'operator ?' is ambiguous
note: could be 'built-in C++ operator?(bool (__cdecl *)(int,int), bool (__cdecl *)(int,int))'
note: or       'built-in C++ operator?(bool (__stdcall *)(int,int), bool (__stdcall *)(int,int))'
note: or       'built-in C++ operator?(bool (__fastcall *)(int,int), bool (__fastcall *)(int,int))'
note: or       'built-in C++ operator?(bool (__vectorcall *)(int,int), bool (__vectorcall *)(int,int))'
note: while trying to match the argument list '(foo::<lambda_717fca3fc65510deea10bc47e2b06be4>, foo::<lambda_f6cd18702c42f6cd636bfee362b37033>)'
```

发现的问题的常见原因 **`/Zc:ternary`** 出自模板元编程中使用的条件运算符。 某些结果类型在此开关下发生变化。 下面的示例演示了两种情况 **`/Zc:ternary`** ：在非元编程上下文中更改条件表达式的结果类型：

```cpp
// zcternary5.cpp
// Compile by using: cl /EHsc /W4 /nologo /Zc:ternary zcternary5.cpp

int main(int argc, char**) {
   char a = 'A';
   const char b = 'B';
   decltype(auto) x = true ? a : b; // char without, const char& with /Zc:ternary
   const char(&z)[2] = argc > 3 ? "A" : "B"; // const char* without /Zc:ternary
   return x > *z;
}
```

典型的修复方法是 `std::remove_reference` 在需要保留旧行为的情况下，对结果类型应用特性。

有关 Visual C++ 中一致性问题的详细信息，请参阅 [Nonstandard Behavior](../../cpp/nonstandard-behavior.md)。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此编译器选项

1. 打开项目的“属性页”  对话框。 有关详细信息，请参阅[在 Visual Studio 中设置 C++ 编译器和生成属性](../working-with-project-properties.md)。

1. 选择 "**配置属性**" "  >  **c/c + +**  >  **命令行**" 属性页。

1. 修改 "**附加选项**" 属性以包含 **`/Zc:ternary`** 或 **`/Zc:ternary-`** ，然后选择 **"确定"**。

## <a name="see-also"></a>另请参阅

[`/Zc`度](zc-conformance.md)
