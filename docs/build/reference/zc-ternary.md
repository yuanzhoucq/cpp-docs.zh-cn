---
title: "/Zc:ternary （强制实施条件运算符规则） |Microsoft 文档"
ms.date: 3/06/2018
ms.technology:
- cpp-tools
ms.topic: article
f1_keywords:
- /Zc:ternary
dev_langs:
- C++
helpviewer_keywords:
- /Zc:ternary
- Zc:ternary
- -Zc:ternary
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 198da679e9d0d7bd58e034ca9c04c3102748af20
ms.sourcegitcommit: eeb2b5ad8d3d22514a7b9bd7d756511b69ae0ccf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/15/2018
---
# <a name="zcternary-enforce-conditional-operator-rules"></a>/Zc:ternary （强制实施条件运算符规则）

启用强制类型的 c + + 标准规则和 const 或 volatile (cv) 限定的条件运算符的表达式中的第二个和第三个操作数。

## <a name="syntax"></a>语法

> **/Zc:ternary**[**-**]

## <a name="remarks"></a>备注

Visual Studio 版本 15.3 支持编译器的 c + + 标准的条件 （或三元） 运算符 (**？:**) 行为。 C + + 标准要求的任一操作数是相同类型和 cv 限定，或只有一个操作数可以明确地转换为相同的类型和与其他的 cv 限定或 throw 表达式的一个或两个操作数。 在 Visual Studio 版本 15.5 之前的版本中，编译器允许由标准被视为不明确的转换。 当**/Zc:ternary**指定选项，编译器符合标准，并拒绝不满足用于匹配的类型和的第二个和第三个操作数的 cv 限定的规则的代码。

**/Zc:ternary**选项默认处于关闭状态。 使用**/Zc:ternary**以启用符合标准行为，或**/Zc:ternary-**显式指定以前的不符合要求编译器行为。 [/ 宽松-](permissive-standards-conformance.md)选项隐式启用此选项，但它可以通过重写**/Zc:ternary-**。

### <a name="examples"></a>示例

此示例演示如何从类型和到类型转换提供两个非显式初始化的类可能会导致不明确的转换。 默认情况下，由编译器接受此代码，但拒绝时**/Zc:ternary**或**/ 宽松-**指定。

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

所需解决方法是使显式强制转换为首选的公共类型，或通过将转换为显式阻止从编译器搜索类型匹配项中的参与转换的一个方向。

此通用模式的重要唯一例外是操作数的类型后一种 null 结尾的字符串类型，例如`const char*`， `const char16_t*`，依次类推。 你可以再现这与数组的类型和它们到 decay 将指针类型。 行为时的实际第二个或第三个操作数？: 是字符串文本的相应的类型取决于使用标准的语言。 C + + 17 已从 C + + 14 更改这种情况下的语义。 因此，下面的示例中的代码接受下**/std:c + + 14** （编译器默认值），但较拒绝时**/std:c + + 17**指定。

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

若要修复此代码，请将显式转换其中一个操作数。

下**/Zc:ternary**、 其中的自变量之一是编译器拒绝条件运算符类型 void 和另一个则不引发表达式。 这些常见用法是在类似于断言的宏：

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

典型的解决方案是只需替换 void() 非空自变量。

此示例显示生成下都错误的代码**/Zc:ternary**和**/Zc:ternary-**:

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

此代码之前为提供此错误：

```Output
error C2446: ':': no conversion from 'foo::<lambda_f6cd18702c42f6cd636bfee362b37033>' to 'foo::<lambda_717fca3fc65510deea10bc47e2b06be4>'
note: No user-defined-conversion operator available that can perform this conversion, or the operator cannot be called
```

与**/Zc:ternary**失败的原因变得更为清晰; 其中几个实现定义的调用任何的约定可用来生成每个 lambda 的体系结构，编译器将表示在它们之间没有首选项无法消除歧义可能 lambda 签名。 新的输出如下所示：

```Output
error C2593: 'operator ?' is ambiguous
note: could be 'built-in C++ operator?(bool (__cdecl *)(int,int), bool (__cdecl *)(int,int))'
note: or       'built-in C++ operator?(bool (__stdcall *)(int,int), bool (__stdcall *)(int,int))'
note: or       'built-in C++ operator?(bool (__fastcall *)(int,int), bool (__fastcall *)(int,int))'
note: or       'built-in C++ operator?(bool (__vectorcall *)(int,int), bool (__vectorcall *)(int,int))'
note: while trying to match the argument list '(foo::<lambda_717fca3fc65510deea10bc47e2b06be4>, foo::<lambda_f6cd18702c42f6cd636bfee362b37033>)'
```

采用与相关问题的常见来源**/Zc:ternary**来自模板元编程中的条件运算符的使用，如更改此交换机下的一些结果类型。 下面的示例演示两种情况下其中**/Zc:ternary**更改非元编程上下文中的条件表达式的结果类型：

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

典型分辨率以这种情况下，将应用`std::remove_reference`保留旧行为所需结果的特征类型。

有关 Visual C++ 中一致性问题的详细信息，请参阅 [Nonstandard Behavior](../../cpp/nonstandard-behavior.md)。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此编译器选项

1. 打开项目的“属性页”  对话框。 有关详细信息，请参阅[使用项目属性](../../ide/working-with-project-properties.md)。

1. 选择**配置属性** > **C/c + +** > **命令行**属性页。

1. 修改**其他选项**属性以包含**/Zc:ternary**或**/Zc:ternary-** ，然后选择**确定**。

## <a name="see-also"></a>请参阅

[/Zc（一致性）](../../build/reference/zc-conformance.md)  
