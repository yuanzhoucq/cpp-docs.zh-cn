---
title: /clr 限制
ms.date: 11/04/2016
helpviewer_keywords:
- /clr compiler option [C++], restrictions
ms.assetid: 385f6462-2c68-46d6-810e-469553ead447
ms.openlocfilehash: d0318ce2e23f92600d5a78d6472646ec91492152
ms.sourcegitcommit: a10c9390413978d36b8096b684d5ed4cf1553bc8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/17/2019
ms.locfileid: "65837378"
---
# <a name="clr-restrictions"></a>/clr 限制

请注意以下关于使用“/clr”的限制：

- 在结构化异常处理程序中，当使用“/clr”进行编译时，使用 `_alloca` 存在限制。 有关详细信息，请参阅 [_alloca](../../c-runtime-library/reference/alloca.md)。

- 运行时错误检查的使用对“/clr”无效。 有关详细信息，请参阅[如何：使用本机运行时检查](/visualstudio/debugger/how-to-use-native-run-time-checks)

- 当“/clr”用于编译仅使用标准 C++ 语法的程序时，以下准则适用于内联程序集的使用：

  - 内联程序集代码假定知道本机堆栈布局、当前函数外部的调用约定或其他有关计算机的低级别信息，如果知道的是应用于托管函数的堆栈帧，内联程序集代码可能会失败。 包含内联程序集代码的函数将生成为非托管函数，就像它们被放置在一个不使用“/clr”编译的单独模块中一样。

  - 不支持传递复制构造函数参数的函数中的内联程序集代码。

- 无法从使用“/clr”编译的程序中调用 [vprintf 函数](../../c-runtime-library/vprintf-functions.md)。

- /clr 下会忽略 [naked](../../cpp/naked-cpp.md) [__declspec](../../cpp/declspec.md) 修饰符。

- 由 [_set_se_translator](../../c-runtime-library/reference/set-se-translator.md) 设置的转换器函数将仅影响非托管代码中的 catch 语句。 有关详细信息，请参阅[异常处理](../../extensions/exception-handling-cpp-component-extensions.md)。

- 在“/clr”下不允许比较函数指针。

- 在“/clr”下不允许使用未完全原型化的函数。

- “/clr”不支持以下编译器选项：

  - “/EHsc”和“/EHs”（“/clr”意味着“/EHa”（请参阅[/EH（异常处理模型）](eh-exception-handling-model.md)）

  - “/fp:strict”和“/fp:except”（请参阅 [/fp （指定浮点行为）](fp-specify-floating-point-behavior.md)）

  - [/Zd](z7-zi-zi-debug-information-format.md)

  - [/Gm](gm-enable-minimal-rebuild.md)

  - [/MT](md-mt-ld-use-run-time-library.md)

  - [/RTC](rtc-run-time-error-checks.md)

  - [/ZI](z7-zi-zi-debug-information-format.md)

- 不支持 `_STATIC_CPPLIB` 预处理器定义 (`/D_STATIC_CPPLIB`) 和“/clr”编译器选项的组合。 这是因为定义会导致应用程序与静态多线程 C++ 标准库链接，此行为不受支持。 有关详细信息，请参阅 [/MD、/MT、/LD（使用运行时库）](md-mt-ld-use-run-time-library.md)主题。

- 将“/Zi”与“/clr”一起使用时，会影响性能。 有关详细信息，请参阅 [/Zi](z7-zi-zi-debug-information-format.md)。

- 在不指定 [/Zc:wchar_t](zc-wchar-t-wchar-t-is-native-type.md) 或不将字符强制转换为 `__wchar_t` 的情况下，将宽字符传递给 .NET Framework 输出例程会导致输出显示为 `unsigned short int`。 例如:

    ```cpp
    Console::WriteLine(L' ')              // Will output 32.
    Console::WriteLine((__wchar_t)L' ')   // Will output a space.
    ```

- [/GS](gs-buffer-security-check.md) 在使用“/clr”编译时被忽略，除非函数位于 `#pragma` [非托管](../../preprocessor/managed-unmanaged.md)下或者函数必须编译为本机，在这种情况下，编译器将生成警告 C4793，默认情况下该警告处于关闭状态 。

- 有关托管应用程序的函数签名要求，请参阅 [/ENTRY](entry-entry-point-symbol.md)。

- 使用“/openmp”和“/clr”编译的应用程序只能在单个 appdomain 进程中运行。  有关详细信息，请参阅 [/openmp（启用 OpenMP 2.0 支持）](openmp-enable-openmp-2-0-support.md)。

- 采用可变数量参数 (varargs) 的函数将作为本机函数生成。 变量参数位置中的任何托管数据类型都将被封送到本机类型。 请注意，<xref:System.String?displayProperty=fullName> 类型实际上是宽字符字符串，但其被封送到单字节字符串。 因此，如果 printf 说明符是 %S (wchar_t*)，它将被封送到 %s 字符串。

- 在使用 va_arg 宏时，使用“/clr:pure”编译可能会得到意外的结果。 有关详细信息，请参阅 [va_arg、va_copy、va_end、va_start](../../c-runtime-library/reference/va-arg-va-copy-va-end-va-start.md)。 “/clr:pure”和“/clr:safe”编译器选项在 Visual Studio 2015 中已弃用，并且在 Visual Studio 2017 和更高版本中不受支持。 “纯”代码或“安全”代码应移植到 C#。

- 不应从托管代码调用任何遍历堆栈以获取参数信息的函数（函数参数）；P/Invoke 层使该信息进一步深入堆栈。  例如，不要使用“/clr”编译代理/存根。

- 如果可能，函数将被编译为托管代码，但并非所有 C++ 构造都可以转换为托管代码。  应根据函数作出决定。 如果函数的任何部分无法转换为托管代码，则整个函数将转换为本机代码。 以下情况会阻止编译器生成托管代码。

  - 编译器生成的 thunk 或 helper 函数。 通过函数指针（包括虚拟函数调用）为任何函数调用生成本机 thunk。

  - 调用 `setjmp` 或 `longjmp` 的函数。

  - 使用某些内部例程直接处理机器资源的函数。 例如，使用 `__enable` 和 `__disable`、`_ReturnAddress` 和 `_AddressOfReturnAddress` 或多媒体内部函数都会产生本机代码。

  - 遵循 `#pragma unmanaged` 指令的函数。 （注意，也支持反转 `#pragma managed`。）

  - 包含对齐类型（即使用 `__declspec(align(...))` 声明的类型）引用的函数。

## <a name="see-also"></a>请参阅

- [/cgthreads（公共语言运行时编译）](clr-common-language-runtime-compilation.md)
