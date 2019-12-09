---
title: __clrcall
ms.date: 11/04/2016
f1_keywords:
- __clrcall_cpp
helpviewer_keywords:
- __clrcall keyword [C++]
ms.assetid: 92096695-683a-40ed-bf65-0c8443572152
ms.openlocfilehash: 6eb1a05eaf6669daa4cb7142ff16a57f7caf39cd
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "74857601"
---
# <a name="__clrcall"></a>__clrcall

指定只能从托管代码调用的函数。  将 **__clrcall**用于将仅从托管代码调用的所有虚拟函数。 但是，此调用约定不能用于从本机代码调用的函数。 **__Clrcall**修饰符是 Microsoft 特定的。

当从托管函数调用到虚拟托管函数或从托管函数到通过指针从托管函数调用时，可以使用 **__clrcall**来提高性能。

入口点是编译器生成的单独函数。 如果函数同时具有本机和托管入口点，则其中一个将是具有函数实现的实际函数。 其他函数将是调用到实际函数的单独函数（形式转换 (thunk)）并允许公共语言运行时执行 PInvoke。 将函数标记为 **__clrcall**时，指示函数实现必须为 MSIL 并且不会生成本机入口点函数。

如果未指定 **__clrcall** ，则采用本机函数的地址时，编译器将使用本地入口点。 **__clrcall**指示函数是托管的，不需要通过从托管到本机的转换。 在这种情况下，编译器将使用托管入口点。

如果使用 `/clr` （而不是 `/clr:pure` 或 `/clr:safe`），并且未使用 **__clrcall** ，则采用函数的地址将始终返回本机入口点函数的地址。 如果使用 **__clrcall** ，则不会创建本机入口点函数，因此你将获得托管函数的地址，而不是入口点 thunk 函数。 有关详细信息，请参阅[Double thunk](../dotnet/double-thunking-cpp.md)。 **/Clr： pure**和 **/clr： safe**编译器选项在 visual studio 2015 中已弃用，在 visual studio 2017 中不受支持。

[/clr （公共语言运行时编译）](../build/reference/clr-common-language-runtime-compilation.md)意味着所有函数和函数指针均 **__clrcall** ，编译器不允许将编译单位中的函数标记为除 **__clrcall**以外的任何内容。 使用 **/clr： pure**时，只能在函数指针和外部声明上指定 **__clrcall** 。

只要该函数具有 MSIL 实现，就C++可以直接从使用 **/clr**编译的现有代码调用 __clrcall 函数。 **__clrcall**函数不能直接从具有内联 asm 的函数中调用，也不能调用 CPU 特定的于，例如，即使这些函数是使用 `/clr`编译的。

**__clrcall**函数指针只应在创建它们的应用程序域中使用。  使用 <xref:System.CrossAppDomainDelegate>，而不是跨应用程序域传递 **__clrcall**的函数指针。 有关详细信息，请参阅[应用程序域和 Visual C++](../dotnet/application-domains-and-visual-cpp.md)。

## <a name="example"></a>示例

请注意，在使用 **__clrcall**声明函数时，将根据需要生成代码;例如，调用函数时。

```cpp
// clrcall2.cpp
// compile with: /clr
using namespace System;
int __clrcall Func1() {
   Console::WriteLine("in Func1");
   return 0;
}

// Func1 hasn't been used at this point (code has not been generated),
// so runtime returns the adddress of a stub to the function
int (__clrcall *pf)() = &Func1;

// code calls the function, code generated at difference address
int i = pf();   // comment this line and comparison will pass

int main() {
   if (&Func1 == pf)
      Console::WriteLine("&Func1 == pf, comparison succeeds");
   else
      Console::WriteLine("&Func1 != pf, comparison fails");

   // even though comparison fails, stub and function call are correct
   pf();
   Func1();
}
```

```Output
in Func1
&Func1 != pf, comparison fails
in Func1
in Func1
```

## <a name="example"></a>示例

以下示例显示，你可以定义函数指针以便将该函数指针声明为仅从托管代码调用。 这样，编译器便能直接调用托管函数并避免本机入口点（双形式转换 (thunk) 问题）。

```cpp
// clrcall3.cpp
// compile with: /clr
void Test() {
   System::Console::WriteLine("in Test");
}

int main() {
   void (*pTest)() = &Test;
   (*pTest)();

   void (__clrcall *pTest2)() = &Test;
   (*pTest2)();
}
```

## <a name="see-also"></a>另请参阅

[自变量传递和命名约定](../cpp/argument-passing-and-naming-conventions.md)<br/>
[关键字](../cpp/keywords-cpp.md)
