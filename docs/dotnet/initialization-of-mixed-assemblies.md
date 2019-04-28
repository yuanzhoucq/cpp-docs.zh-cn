---
title: 混合程序集的初始化
ms.date: 03/09/2018
helpviewer_keywords:
- mixed assemblies [C++], loader lock
- loader lock [C++]
- initializing mixed assemblies
- deadlocks [C++]
- .cctor [C++]
- custom locales [C++]
- mixed assemblies [C++], initilizing
ms.assetid: bfab7d9e-f323-4404-bcb8-712b15f831eb
ms.openlocfilehash: 1f4ea7f5cfc6e99390c93ba9c2beadc46fce8584
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62339034"
---
# <a name="initialization-of-mixed-assemblies"></a>混合程序集的初始化

Windows 开发人员必须始终为持谨慎态度的加载程序锁时运行过程中的代码`DllMain`。 但是，有处理时派上用场的一些其他注意事项C++/clr 混合模式程序集。

[DllMain](/windows/desktop/Dlls/dllmain) 中的代码不能访问 CLR。 这意味着 `DllMain` 不应直接或间接调用托管函数；在 `DllMain`中不应声明或实现托管代码；并且在 `DllMain`中不应发生垃圾回收或自动库加载。

## <a name="causes-of-loader-lock"></a>加载程序锁定的原因

随着 .NET 平台的引入，出现了两个截然不同的加载执行模块（EXE 或 DLL）的机制：一个适用于 Windows，用于非托管模块；另一个适用于 .NET 公共语言运行库 (CLR)，加载 .NET 程序集。 混合 DLL 加载问题与 Microsoft Windows OS 加载程序密切相关。

当将一个仅包含 .NET 结构的程序集加载到进程中时，CLR 加载程序可以独立执行所有必要的加载和初始化任务。 而对于混合程序集，由于它们可能包含本机代码和数据，因此还必须使用 Windows 加载程序。

Windows 加载程序可保证：在 DLL 被初始化之前，没有代码可以访问该 DLL 中的代码或数据，并且在 DLL 被部分初始化时，没有代码可以不必要地加载该 DLL。 为此，Windows 加载程序使用一个进程全局临界区（通常称为“加载程序锁定”）来防止模块初始化期间的不安全访问。 因此，加载进程容易受到许多典型死锁情况的攻击。 对于混合程序集来说，下面的两种情况增加了死锁风险：

- 首先，当加载程序锁被保留时，如果用户试图执行编译为 Microsoft 中间语言 (MSIL) 的函数（例如从 `DllMain` 中或在静态初始值设定项中），这会导致死锁。 试考虑这样一种情况：MSIL 函数引用未加载的程序集中的类型。 CLR 会尝试自动加载该程序集，这可能要求 Windows 加载程序在加载程序锁上阻止。 由于加载程序锁已经在之前的调用序列中被代码保留，所以产生死锁。 但是，在有加载程序锁时执行 MSIL 不一定会发生死锁，这使得很难诊断和修复这种死锁情况。 在某些情况下，例如在被引用类型的 DLL 不包含本机结构且它的所有依赖项都不包含本机结构时，加载被引用类型的 .NET 程序集并不需要 Windows 加载程序。 此外，所需的程序集或其混合本机/.NET 依赖项可能已经由其他代码加载了。 因此，死锁情况很难预测，它在很大程度上取决于目标计算机的配置。

- 其次，在 .NET Framework 1.0 和 1.1 版中加载 DLL 时，CLR 假定不保留加载程序锁，因此执行了一些在有加载程序锁时无效的操作。 不保留加载程序锁对于单纯的 .NET DLL 来说是一个合理的假定，但对于混合 DLL 而言，由于它们执行本机初始化例程，因此需要本机 Windows 加载程序以及加载程序锁。 因此，即使开发人员在 DLL 初始化期间并未尝试执行任何 MSIL 函数，.NET Framework 1.0 和 1.1 版中仍有可能发生不确定的死锁。

已经从混合 DLL 加载进程中消除了所有的不确定性。 这是通过以下更改实现的：

- CLR 在加载混合 DLL 时不再作出错误的假定。

- 非托管初始化和托管初始化在两个不同的阶段执行。 首先进行非托管初始化（通过 DllMain），之后进行托管初始化（通过一个名为 *.cctor*的 .NET 支持的结构）。 后者对于用户完全透明，除非使用的是 **/Zl** 或 **/NODEFAULTLIB** 。 有关更多信息，请参阅[/NODEFAULTLIB (Ignore Libraries)](../build/reference/nodefaultlib-ignore-libraries.md) 和 [/Zl (Omit Default Library Name)](../build/reference/zl-omit-default-library-name.md) 。

加载程序锁还是会出现，但现在它的出现是重复出现的，因而可以检测到。 如果`DllMain`包含 MSIL 指令，编译器将生成警告[编译器警告 （等级 1） C4747](../error-messages/compiler-warnings/compiler-warning-level-1-c4747.md)。 CRT 或 CLR 都将尝试检测并报告在加载程序锁下执行 MSIL 的企图。 CRT 检测导致运行时诊断 C 运行时错误 R6033。

本文档的其余部分介绍了其他可以在有加载程序锁时执行 MSIL 的情况、在这些情况下解决问题的方案以及调试技术。

## <a name="scenarios-and-workarounds"></a>情况和解决方法

在几种不同情况下，用户代码可在加载程序锁定下执行 MSIL。 开发人员必须确保在实现用户代码时不尝试在其中的每种情况下执行 MSIL 指令。 下面各小节描述了所有的可能性，并讨论了如何解决最常见的情况中的问题。

### <a name="dllmain"></a>DllMain

`DllMain` 函数是 DLL 的用户定义入口点。 除非用户指定，否则，每当进程或线程附加到包含 DLL 或从包含 DLL 中分离时，都会调用 `DllMain` 。 由于这种调用可以在加载程序锁被保留时发生，因此不应将用户提供的 `DllMain` 函数编译为 MSIL。 此外，以 `DllMain` 为根的调用树中的函数不能编译为 MSIL。 若要在此处解决问题，则应使用 #pragma `DllMain` 来修改定义 `unmanaged`的代码块。 对于由 `DllMain` 调用的每个函数，应执行同样的操作。

如果这些函数必须调用的某个函数需要一个用于其他调用上下文的 MSIL 实现，可以使用一个会创建同一函数的 .NET 版本和本机版本的复制策略。

或者，如果不需要 `DllMain` 或者不需要在有加载程序锁时执行它，则可以删除用户提供的 `DllMain` 实现，这样便可以消除此问题。

如果 DllMain 尝试直接执行 MSIL，则会导致 [Compiler Warning (level 1) C4747](../error-messages/compiler-warnings/compiler-warning-level-1-c4747.md) 。 但是，编译器无法检测到这样的情况：即 DllMain 调用另一个模块中的一个函数，该函数再尝试执行 MSIL。

有关此情形的详细信息，请参阅“妨碍诊断的情况”。

### <a name="initializing-static-objects"></a>初始化静态对象

如果需要动态初始值设定项，初始化静态对象会导致死锁。 对于简单的情况，例如只是将一个静态变量分配给一个在编译时已知的值，则不需要动态初始化，因此不存在死锁风险。 但是，由函数调用、构造函数调用或无法在编译时计算的表达式初始化的静态变量都要求在初始化模块时执行代码。

下面的代码演示了需要动态初始化的静态初始值设定项的示例：一个函数调用、对象构造和一个指针初始化。 （这些示例不是静态的，而是假定为在具有同样效果的全局范围内定义。）

```cpp
// dynamic initializer function generated
int a = init();
CObject o(arg1, arg2);
CObject* op = new CObject(arg1, arg2);
```

死锁风险取决于包含的模块是否使用 **/clr** 编译，以及是否会执行 MSIL。 具体来说，如果静态变量不使用 **/clr** 编译（或驻留在 #pragma `unmanaged` 块中），而初始化它所需的动态初始值设定项导致执行 MSIL 指令，则可能发生死锁。 这是因为对于不使用 **/clr**编译的模块，静态变量的初始化由 DllMain 执行。 相反，对于使用 **/clr** 编译的静态变量，它在完成了非托管初始化阶段并且释放了加载程序锁之后由 .cctor 初始化。

有许多解决方案可以解决由动态初始化静态变量引起的死锁（大致按照修复问题所需的时间顺序排列）：

- 可使用 **/clr**编译包含静态变量的源文件。

- 可使用 #pragma `unmanaged` 指令将将静态变量调用的所有函数都编译为本机代码。

- 手动克隆静态变量所依赖的代码，以提供具有不同名称的 .NET 版本和本机版本。 这样，开发人员就可以从本机静态初始值设定项调用本机版本，而从其他位置调用 .NET 版本。

### <a name="user-supplied-functions-affecting-startup"></a>影响启动的用户提供的函数

在启动过程中，库依赖一些由用户提供的函数进行初始化。 例如，当中全局重载运算符C++如`new`并`delete`运算符，用户提供的版本随处使用，包括中的C++标准库初始化和析构。 因此，C++标准库和用户提供的静态初始值设定项将调用这些运算符的任何用户提供的版本。

如果将用户提供的版本编译为 MSIL，这些初始值设定项在加载程序锁被保留时会尝试执行 MSIL 指令。 用户提供`malloc`具有同样的结果。 若要解决此问题，必须使用 #pragma `unmanaged` 指令将所有这些重载或用户提供的定义实现为本机代码。

有关此情形的详细信息，请参阅“妨碍诊断的情况”。

### <a name="custom-locales"></a>自定义区域设置

如果用户提供了一个自定义全局区域设置，该区域设置将用于初始化将来的所有 I/O 流，包括静态初始化的 I/O 流。 如果将该全局区域设置对象编译为 MSIL，就可以在加载程序锁被保留时调用编译为 MSIL 的区域设置对象成员函数。

有三种方式可解决此问题：

可使用 **/clr** 选项编译包含所有全局 I/O 流定义的源文件。 这可以防止在有加载程序锁时执行其静态初始值设定项。

可使用 #pragma `unmanaged` 指令将自定义区域设置函数的定义都编译为本机代码。

在加载程序锁被释放之前，避免将自定义区域设置设为全局区域设置。 当加载程序锁被释放后，使用自定义区域设置显式配置在初始化期间创建的 I/O 流。

## <a name="impediments-to-diagnosis"></a>妨碍诊断的情况

在某些情况下，很难检测到死锁的来源。 下面各小节讨论了这些情况以及解决这些问题的途径。

### <a name="implementation-in-headers"></a>头文件中的实现

在某些情况下，头文件中的函数实现会使诊断变得复杂。 内联函数和模板代码都要求在头文件中指定函数。  C++ 语言指定单一定义规则，该规则强制具有相同名称的函数的所有实现在语义上相等。 因此，C++ 链接器在合并具有给定函数的重复实现的对象文件时没有任何特别注意事项。

在 Visual Studio 2005 中之前, 链接器只需选择这些在语义上等效的定义，则还以适应前向声明和方案，不同的优化选项用于不同的源文件时的最大值。 对于混合本机 .NET DLL 来说，这就会产生问题。

因为相同的标头可能包含C++文件的工具 **/clr**启用和禁用，或 #include 可以被包装在 #pragma`unmanaged`块中，就可以具有 MSIL 和本机版本的函数，提供了标头中的实现。 MSIL 和本机实现在有加载程序锁时的初始化方面具有不同的语义，而这实际上违反了单一定义规则。 因此，当链接器选择最大的实现时，即使在其他位置使用 #pragma unmanaged 指令将一个函数显式编译为本机代码，它也可能选择该函数的 MSIL 版本。 为确保模板或内联函数的 MSIL 版本永远不会在有加载程序锁时被调用，在有加载程序锁时调用的每个此类函数的每个定义都必须用 #pragma `unmanaged` 指令进行修改。 如果头文件来自第三方，实现此操作的最简单的方法是为有问题的头文件推送 #pragma unmanaged 指令，然后在 #include 指令周围弹出 #pragma unmanaged 指令。 (请参阅[managed、 unmanaged](../preprocessor/managed-unmanaged.md)有关的示例。)但是，对于那些包含必须直接调用 .NET API 的其他代码的头文件，该策略无效。

为方便用户处理加载程序锁，当两种版本同时出现时，链接器将选择本机实现，而不选择托管实现。 这样可以避免上述问题。 但是，由于编译器中有两个未解决的问题，所以在此发行版中此规则有两种例外情况：

- 对内联函数的调用通过全局静态函数指针来实现。 这种情况特别值得注意，因为虚函数就是通过全局函数指针调用的。 例如，应用于对象的

```cpp
#include "definesmyObject.h"
#include "definesclassC.h"

typedef void (*function_pointer_t)();

function_pointer_t myObject_p = &myObject;

#pragma unmanaged
void DuringLoaderlock(C & c)
{
    // Either of these calls could resolve to a managed implementation,
    // at link-time, even if a native implementation also exists.
    c.VirtualMember();
    myObject_p();
}
```

### <a name="diagnosing-in-debug-mode"></a>在调试模式下诊断

加载程序锁问题的所有诊断都应该在调试版本中进行。 发布版本可能不生成诊断，同时在发布模式下执行的优化可能会掩盖某些在有加载程序锁时执行 MSIL 的情况。

## <a name="how-to-debug-loader-lock-issues"></a>如何调试加载程序锁定问题

在调用 MSIL 函数时，CLR 生成的诊断会导致 CLR 暂停执行。 反过来，在进程内运行调试对象时，这同样会导致 Visual C++ 混合模式的调试程序被挂起。 但是，当附加到进程时，不可能使用混合调试程序获取调试对象的托管调用堆栈。

为确定在有加载程序锁时调用的具体 MSIL 函数，开发人员应该完成以下步骤：

1. 确保 mscoree.dll 和 mscorwks.dll 的符号可用。

   有两种方法可以做到这一点。 首先，可将 mscoree.dll 和 mscorwks.dll 的 PDB 添加到符号搜索路径中。 为此，请打开符号搜索路径选项对话框。 (从**工具**菜单中，选择**选项**。 在左窗格中**选项**对话框中，打开**调试**节点，然后选择**符号**。)将 mscoree.dll 和 mscorwks.dll PDB 文件的路径添加到搜索列表中。 将这些 PDB 安装到 %VSINSTALLDIR%\SDK\v2.0\symbols 中。 选择 **“确定”**。

   其次，可以从 Microsoft Symbol Server 中下载 mscoree.dll 和 mscorwks.dll 的 PDB。 若要配置 Symbol Server，请打开符号搜索路径选项对话框。 (从**工具**菜单中，选择**选项**。 在左窗格中**选项**对话框中，打开**调试**节点，然后选择**符号**。)将下面的搜索路径添加到搜索列表： http://msdl.microsoft.com/download/symbols。 向符号服务器缓存文本框中添加一个符号缓存目录。 选择 **“确定”**。

1. 将调试程序模式设置为仅限本机模式。

   若要执行此操作，打开**属性**网格中解决方案的启动项目。 选择**配置属性** > **调试**。 设置**调试器类型**到**仅限本机的**。

1. 启动调试器 (F5)。

1. 当 **/clr**生成诊断中，选择**重试**，然后选择**中断**。

1. 打开“调用堆栈”窗口。 (在菜单栏上依次选择**调试** > **Windows** > **调用堆栈**。)有问题`DllMain`或带绿色箭头标识静态初始值设定项。 如果未标识出有问题的函数，必须执行以下步骤来找到该函数。

1. 打开**即时**窗口 (在菜单栏上依次选择**调试** > **Windows** > **即时**。)

1. 键入到.load sos.dll**即时**窗口以加载 SOS 调试服务。

1. 键入 ！ dumpstack**即时**时段以获取完整的内部列表 **/clr**堆栈。

1. 查找 _CorDllMain 的 （最接近堆栈的底部） 的第一个实例 (如果`DllMain`导致问题) 或 _VTableBootstrapThunkInitHelperStub 或 GetTargetForVTableEntry （如果静态初始值设定项导致问题）。 紧挨着位于此调用下方的堆栈项是 MSIL 实现的函数的调用，该函数曾试图在有加载程序锁时执行。

1. 转到的源文件和行号上一步中标识和正确使用方案和方案一节中所述的解决方案时的问题。

## <a name="example"></a>示例

### <a name="description"></a>描述

下面的示例演示如何通过将移动中的代码来避免加载程序锁`DllMain`到全局对象的构造函数。

在此示例中，没有其构造函数包含在最初的托管的对象的全局托管的对象`DllMain`。 该示例的第二部分引用程序集，并创建托管对象的一个实例以调用执行初始化的模块构造函数。

### <a name="code"></a>代码

```cpp
// initializing_mixed_assemblies.cpp
// compile with: /clr /LD
#pragma once
#include <stdio.h>
#include <windows.h>
struct __declspec(dllexport) A {
   A() {
      System::Console::WriteLine("Module ctor initializing based on global instance of class.\n");
   }

   void Test() {
      printf_s("Test called so linker does not throw away unused object.\n");
   }
};

#pragma unmanaged
// Global instance of object
A obj;

extern "C"
BOOL WINAPI DllMain(HINSTANCE hInstance, DWORD dwReason, LPVOID lpReserved) {
   // Remove all managed code from here and put it in constructor of A.
   return true;
}
```

此示例演示了混合程序集的初始化中的问题：

```cpp
// initializing_mixed_assemblies_2.cpp
// compile with: /clr initializing_mixed_assemblies.lib
#include <windows.h>
using namespace System;
#include <stdio.h>
#using "initializing_mixed_assemblies.dll"
struct __declspec(dllimport) A {
   void Test();
};

int main() {
   A obj;
   obj.Test();
}
```

此代码生成以下输出：

```Output
Module ctor initializing based on global instance of class.

Test called so linker does not throw away unused object.
```

## <a name="see-also"></a>请参阅

[混合（本机和托管）程序集](../dotnet/mixed-native-and-managed-assemblies.md)
