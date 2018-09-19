---
title: __clrcall |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- __clrcall_cpp
dev_langs:
- C++
helpviewer_keywords:
- __clrcall keyword [C++]
ms.assetid: 92096695-683a-40ed-bf65-0c8443572152
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9631ac9beb0e6263ac1cf7e60e11e498aa4c7667
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46019752"
---
# <a name="clrcall"></a>__clrcall

**Microsoft 专用**

指定只能从托管代码调用的函数。  使用 **__clrcall**只会从托管代码调用的所有虚拟函数。 但是，此调用约定不能用于从本机代码调用的函数。

使用 **__clrcall**以调用从托管函数到虚拟托管函数或从托管函数指针通过托管函数时提高性能。

入口点是编译器生成的单独函数。 如果函数同时具有本机和托管入口点，则其中一个将是具有函数实现的实际函数。 其他函数将是调用到实际函数的单独函数（形式转换 (thunk)）并允许公共语言运行时执行 PInvoke。 当函数标记为 **__clrcall**，指示函数实现必须是 MSIL，并且将不会生成本机入口点函数。

当采用本机函数的地址，如果 **__clrcall**未指定，则编译器将使用本机入口点。 **__clrcall**指示函数为托管，并且没有不需要经历从托管到本机。 在这种情况下，编译器将使用托管入口点。

当`/clr`(不`/clr:pure`或`/clr:safe`) 使用并 **__clrcall**是未使用，始终采用一个函数的地址返回本机入口点函数的地址。 当 **__clrcall**是使用本机入口点函数不会创建，因此获得托管函数，而不是入口点转换 （thunk） 函数的地址。 有关详细信息，请参阅[双重形式转换](../dotnet/double-thunking-cpp.md)。 **/Clr: pure**并 **/clr: safe**编译器选项在 Visual Studio 2015 中弃用，在 Visual Studio 2017 中不受支持。

[/clr （公共语言运行时编译）](../build/reference/clr-common-language-runtime-compilation.md)意味着，所有函数和函数指针都是 **__clrcall** ，编译器将不允许将编译单位以外的任何标记中的函数 **__clrcall**。 当 **/clr: pure**使用，则 **__clrcall**只能在函数指针和外部声明上指定。

可以直接调用 **__clrcall**函数从使用已编译的现有 c + + 代码 **/clr** ，只要该函数具有 MSIL 实现。 **__clrcall**不能直接从具有内联 asm，例如，调用特定于 CPU 的 intrinisics 的函数调用函数，即使这些函数将编译使用`/clr`。

**__clrcall**函数指针仅用于在其中创建应用程序域中使用。  而不是传入 **__clrcall**函数指针跨应用程序域，请使用<xref:System.CrossAppDomainDelegate>。 有关详细信息，请参阅[应用程序域和 Visual C++](../dotnet/application-domains-and-visual-cpp.md)。

## <a name="example"></a>示例

请注意，当声明的函数 **__clrcall**，在需要时将生成代码; 例如，在调用函数时。

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

## <a name="see-also"></a>请参阅

[自变量传递和命名约定](../cpp/argument-passing-and-naming-conventions.md)<br/>
[关键字](../cpp/keywords-cpp.md)
