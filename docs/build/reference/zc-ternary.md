---
title: /Zc:ternary（强制实施条件运算符规则）
ms.date: 09/12/2019
f1_keywords:
- /Zc:ternary
helpviewer_keywords:
- /Zc:ternary
- Zc:ternary
- -Zc:ternary
ms.openlocfilehash: 7c95f061e195ccf7fef8a6a21d193b257baa5f39
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81335682"
---
# <a name="zcternary-enforce-conditional-operator-rules"></a>/Zc:ternary（强制实施条件运算符规则）

启用C++标准规则，用于条件运算符表达式中第二个和第三个操作数的类型和 const 或易失性 （cv） 限定。

## <a name="syntax"></a>语法

> **/Zc：三元****-*** |

## <a name="remarks"></a>备注

从 Visual Studio 2017 开始，编译器支持C++标准*条件运算符***（？：**） 行为。 它也被称为*三元运算符*。 C++标准要求三元操作数满足三个条件之一：操作数必须相同类型和**条件**或**挥发性**限定（cv 限定），或者只有一个操作数必须明确转换为与另一种类型和 cv 限定相同的操作数。 或者，一个或两个操作数必须是引发表达式。 在 Visual Studio 2017 版本 15.5 之前的版本中，编译器允许按标准认为不明确的转换。

指定 **/Zc：三元**选项时，编译器符合标准。 它拒绝不符合匹配类型规则的代码以及第二个和第三个操作数的 cv 限定。

**/Zc：三元**选项在 Visual Studio 2017 中默认处于关闭状态。 使用 **/Zc：三元**来启用符合性行为，或 **/Zc：三元-** 显式指定以前的不符合编译器行为。 [/允许-](permissive-standards-conformance.md)选项隐式启用此选项，但可以使用 **/Zc：ternary-** 重写它。

### <a name="examples"></a>示例

此示例显示提供类型非显式初始化和转换为类型的类如何导致不明确的转换。 默认情况下，编译器接受此代码，但在指定 **/Zc：三元**或 **/允许时**拒绝。

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

要修复此代码，请对首选公共类型进行显式强制转换，或防止类型转换的一个方向。 通过显式表示转换，可以使编译器与类型转换匹配。

此常见模式的一个重要例外是，当操作数的类型是 null 终止字符串类型之一，如`const char*`，`const char16_t*`等。 您还可以使用数组类型及其衰减到的指针类型重现效果。 当实际的第二个或第三个操作数`?:`为相应类型的字符串文本时的行为取决于所使用的语言标准。 C++17 已更改此案例的语义，从 C++14。 因此，编译器在默认 **/std：c++14**下接受以下示例中的代码，但在指定 **/std：c++17**时拒绝它。

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

要修复此代码，请显式转换其中一个操作数。

在 **/Zc：ternary**下，编译器拒绝条件运算符，其中一个参数的类型为**void，** 另一个不是引发表达式。 此模式的常见用在 ASSERT 类似宏中：

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

典型的解决方案是用 替换非 void 参数。 `void()`

此示例显示在 **/Zc：三元**和 **/Zc：三元 -** 下生成错误的代码：

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

此代码以前给出此错误：

```Output
error C2446: ':': no conversion from 'foo::<lambda_f6cd18702c42f6cd636bfee362b37033>' to 'foo::<lambda_717fca3fc65510deea10bc47e2b06be4>'
note: No user-defined-conversion operator available that can perform this conversion, or the operator cannot be called
```

随着 **/Zc：三元，** 失败的原因变得更加清晰。 可以使用多个实现定义的调用约定中的任何一个生成每个 lambda。 但是，编译器没有首选项规则来消除可能的 lambda 签名的歧义。 新输出如下所示：

```Output
error C2593: 'operator ?' is ambiguous
note: could be 'built-in C++ operator?(bool (__cdecl *)(int,int), bool (__cdecl *)(int,int))'
note: or       'built-in C++ operator?(bool (__stdcall *)(int,int), bool (__stdcall *)(int,int))'
note: or       'built-in C++ operator?(bool (__fastcall *)(int,int), bool (__fastcall *)(int,int))'
note: or       'built-in C++ operator?(bool (__vectorcall *)(int,int), bool (__vectorcall *)(int,int))'
note: while trying to match the argument list '(foo::<lambda_717fca3fc65510deea10bc47e2b06be4>, foo::<lambda_f6cd18702c42f6cd636bfee362b37033>)'
```

**/Zc：ternary**发现的问题的常见来源来自模板元编程中使用的条件运算符。 某些结果类型在此开关下更改。 下面的示例演示了两种情况，其中 **/Zc：ternary**在非元编程上下文中更改条件表达式的结果类型：

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

典型的解决方法是在结果类型上应用`std::remove_reference`特征，在需要的地方保留旧行为。

有关 Visual C++ 中一致性问题的详细信息，请参阅 [Nonstandard Behavior](../../cpp/nonstandard-behavior.md)。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此编译器选项

1. 打开项目的“属性页” **** 对话框。 有关详细信息，请参阅[在 Visual Studio 中设置 C++ 编译器和生成属性](../working-with-project-properties.md)。

1. 选择**配置属性** > **C/C++** > **命令行**属性页。

1. 修改 **"附加选项"** 属性以包括 **/Zc：三元**或 **/Zc：三元-** 然后选择 **"确定**"。

## <a name="see-also"></a>另请参阅

[/Zc（一致性）](zc-conformance.md)
