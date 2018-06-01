---
title: 如何： 将迁移到的 clr： 安全 (C + + /cli CLI) |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- migration [C++], verifiable assemblies
- upgrading Visual C++ applications, verifiable assemblies
- verifiable assemblies [C++], migrating to
- /clr compiler option [C++], migrating to /clr:safe
ms.assetid: 75f9aae9-1dcc-448a-aa11-2d96f972f9d2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: d72be19eb893a74a17a988e8c14c6bdaba766cbc
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/01/2018
ms.locfileid: "34704509"
---
# <a name="how-to-migrate-to-clrsafe-ccli"></a>如何：迁移到 /clr:safe (C++/CLI)

> [!IMPORTANT]
> **/Clr: pure**和 **/clr: safe**编译器选项是在 Visual Studio 2015 中已过时，在 Visual Studio 2017 中不支持。 如果您需要安全 CLR 程序集，我们建议移植对 C# 代码。

如果你使用的早期版本的 Visual Studio 2017 之前从 Visual c + + 编译器工具集，你可以通过使用生成可验证组件 **/clr: safe**，这将导致编译器错误生成每个非可验证代码构造。

## <a name="remarks"></a>备注

以下问题将生成可验证性错误：

- 本机类型。 即使未使用的本机类、 结构、 指针或数组的声明将阻止编译。

- 全局变量

- 对任何非托管库，包括公共语言运行时函数调用的函数调用

- 可验证函数不能包含[static_cast 运算符](../cpp/static-cast-operator.md)的向下转换。 [Static_cast 运算符](../cpp/static-cast-operator.md)可以用于基元类型之间强制转换而向下转换[safe_cast](../windows/safe-cast-cpp-component-extensions.md)或 C 样式强制转换 (实现为[safe_cast](../windows/safe-cast-cpp-component-extensions.md))必须使用。

- 可验证函数不能包含[reinterpret_cast 运算符](../cpp/reinterpret-cast-operator.md)（或任何 C 样式强制转换等效项）。

- 可验证函数无法对执行算术[interior_ptr (C + + /cli CLI)](../windows/interior-ptr-cpp-cli.md)。 它仅可向其分配和取消引用指针。

- 可验证函数只能引发或捕获指向引用类型，因此必须在引发之前装箱值类型。

- 可验证函数只能调用可验证函数 (例如，不允许对公共语言运行时调用，包括`AtEntry` / `AtExit`，，因此不允许全局构造函数)。

- 可验证的类不能使用<xref:System.Runtime.InteropServices.LayoutKind>。

- 如果生成 EXE，一个主函数不能因此声明任何参数，<xref:System.Environment.GetCommandLineArgs%2A>必须用于检索命令行自变量。

- 在非虚拟调用虚函数。 例如：

   ```cpp
   // not_verifiable.cpp
   // compile with: /clr
   ref struct A {
      virtual void Test() {}
   };

   ref struct B : A {};

   int main() {
      B^ b1 = gcnew B;
      b1->A::Test();   // Non-virtual call to virtual function
   }
   ```

此外，可验证代码不能用于以下关键字：

- [非托管](../preprocessor/managed-unmanaged.md)和[包](../preprocessor/pack.md)杂注

- [裸](../cpp/naked-cpp.md)和[对齐](../cpp/align-cpp.md) [__declspec](../cpp/declspec.md)修饰符

- [__asm](../assembler/inline/asm.md)

- [__based](../cpp/based-grammar.md)

- [__try](../cpp/try-except-statement.md)和 `__except`

## <a name="see-also"></a>请参阅

- [纯代码和可验证代码 (C++/CLI)](../dotnet/pure-and-verifiable-code-cpp-cli.md)
