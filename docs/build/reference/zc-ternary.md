---
title: '/Zc: ternary （强制实施条件运算符规则）'
ms.date: 3/06/2018
f1_keywords:
- /Zc:ternary
helpviewer_keywords:
- /Zc:ternary
- Zc:ternary
- -Zc:ternary
ms.openlocfilehash: cb9a4f8468a9cb57af711cdca36ee343e5092493
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/14/2019
ms.locfileid: "57816485"
---
# <a name="zcternary-enforce-conditional-operator-rules"></a>/Zc: ternary （强制实施条件运算符规则）

启用强制类型的 c + + 标准规则和条件运算符表达式中的第二个和第三个操作数的 const 或 volatile (cv) 限定。

## <a name="syntax"></a>语法

> **/Zc:ternary**[**-**]

## <a name="remarks"></a>备注

Visual Studio 版本 15.3 启用编译器支持的 c + + 标准条件 （或三元） 运算符 (**？:**) 行为。 C + + 标准要求任一操作数是相同的类型和 cv 限定，或只有一个操作数是明确转换为相同的类型和 cv 限定为其他，或一个或两个操作数均为 throw 表达式。 在 Visual Studio 版本 15.5 之前的版本中，编译器允许由标准被视为不明确的转换。 当 **/zc: ternary**指定选项，编译器符合标准，并拒绝不满足匹配的类型和的第二个和第三个操作数的 cv 限定的规则的代码。

**/Zc: ternary**选项默认情况下处于关闭状态。 使用 **/zc: ternary**若要启用符合标准行为，或 **/Zc:ternary-** 显式指定以前的不符合要求的编译器行为。 [触发-](permissive-standards-conformance.md)选项隐式启用此选项，但它可以通过重写 **/Zc:ternary-**。

### <a name="examples"></a>示例

此示例演示如何从类型和转换为类型提供这两个非显式初始化的类可能会导致不明确的转换。 此代码默认情况下，编译器接受，但被拒绝时 **/zc: ternary**或**触发的**指定。

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

所需的解决方法是首选的公共类型，请显式强制转换或转换完成显式防止从编译器搜索类型匹配项中的参与转换的一个方向。

此通用模式的重要唯一例外是当操作数的类型为一个以 null 结尾的字符串类型，如`const char*`， `const char16_t*`，依次类推。 你可以重现此数组类型和它们到 decay 指针类型。 行为时的实际第二个或第三个操作数？: 相应的类型的字符串文字取决于所使用的语言标准。 C + + 17 已从 C + + 14 中更改这种情况下的语义。 因此，在下面的示例代码接受下 **/std: c + + 14** （编译器默认值），但较拒绝时 **/std: c + + 17**指定。

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

若要修复此代码，强制显式转换操作数之一。

下 **/zc: ternary**、 编译器拒绝条件运算符其中一个参数是 void 类型和其他不是 throw 表达式。 其中一个常见用途是在类似于 ASSERT 的宏：

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

典型的解决方案是只需替换 void() 非 void 参数。

此示例显示了代码生成错误下都 **/zc: ternary**并 **/Zc:ternary-**:

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

此代码之前为提供了此错误：

```Output
error C2446: ':': no conversion from 'foo::<lambda_f6cd18702c42f6cd636bfee362b37033>' to 'foo::<lambda_717fca3fc65510deea10bc47e2b06be4>'
note: No user-defined-conversion operator available that can perform this conversion, or the operator cannot be called
```

与 **/zc: ternary**失败的原因变得更为清晰; 其中多个实现定义的调用任何的约定可用于生成每个 lambda 体系结构，编译器将表示在它们之间没有首选项可以消除可能 lambda 签名。 新的输出如下所示：

```Output
error C2593: 'operator ?' is ambiguous
note: could be 'built-in C++ operator?(bool (__cdecl *)(int,int), bool (__cdecl *)(int,int))'
note: or       'built-in C++ operator?(bool (__stdcall *)(int,int), bool (__stdcall *)(int,int))'
note: or       'built-in C++ operator?(bool (__fastcall *)(int,int), bool (__fastcall *)(int,int))'
note: or       'built-in C++ operator?(bool (__vectorcall *)(int,int), bool (__vectorcall *)(int,int))'
note: while trying to match the argument list '(foo::<lambda_717fca3fc65510deea10bc47e2b06be4>, foo::<lambda_f6cd18702c42f6cd636bfee362b37033>)'
```

采用与相关问题的常见根源 **/zc: ternary**来自模板元编程中的条件运算符的使用，在此交换机下的结果类型的一些更改。 下面的示例演示两种情况下， **/zc: ternary**更改非元编程上下文中的条件表达式的结果类型：

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

在这种情况下典型的解决方法是将应用`std::remove_reference`特征对结果的保留旧行为所需类型。

有关 Visual C++ 中一致性问题的详细信息，请参阅 [Nonstandard Behavior](../../cpp/nonstandard-behavior.md)。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此编译器选项

1. 打开项目的“属性页”  对话框。 有关详细信息，请参阅[Visual Studio 中的设置 c + + 编译器和生成属性](../working-with-project-properties.md)。

1. 选择**配置属性** > **C/c + +** > **命令行**属性页。

1. 修改**其他选项**属性以包含 **/zc: ternary**或 **/Zc:ternary-** ，然后选择**确定**。

## <a name="see-also"></a>请参阅

[/Zc（一致性）](zc-conformance.md)
