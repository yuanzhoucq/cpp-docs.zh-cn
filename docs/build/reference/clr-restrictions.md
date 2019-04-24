---
title: /clr 限制
ms.date: 11/04/2016
helpviewer_keywords:
- /clr compiler option [C++], restrictions
ms.assetid: 385f6462-2c68-46d6-810e-469553ead447
ms.openlocfilehash: 21b7ead553871854c73021756eb2086f9e6e7393
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/18/2019
ms.locfileid: "58777813"
---
# <a name="clr-restrictions"></a>/clr 限制

请注意以下限制的使用 **/clr**:

- 在结构化的异常处理程序中，没有使用限制`_alloca`编译时 **/clr**。 有关详细信息，请参阅[_alloca](../../c-runtime-library/reference/alloca.md)。

- 使用运行时错误检查不是有效，且 **/clr**。 有关详细信息，请参阅[如何：使用本机运行时检查](/visualstudio/debugger/how-to-use-native-run-time-checks)

- 当 **/clr**用于编译仅使用标准的程序C++语法中，以下准则适用于内联程序集的使用：

  - 假定你了解本机堆栈布局的内联程序集代码，调用当前函数或有关计算机的其他低级别信息的外部约定可能会失败如果知识应用于托管函数的堆栈帧。 包含内联程序集代码的函数将生成为非托管函数，就像被放在单独的模块，而无需编译 **/clr**。

  - 不支持内联程序集代码中将复制构造函数参数传递的函数。

- [Vprintf 函数](../../c-runtime-library/vprintf-functions.md)不能从编译的程序调用 **/clr**。

- [裸](../../cpp/naked-cpp.md) [__declspec](../../cpp/declspec.md)在 /clr 下忽略修饰符。

- 通过设置的转换器函数[_set_se_translator](../../c-runtime-library/reference/set-se-translator.md)会影响仅非托管代码中的 catch 语句。 请参阅[异常处理](../../extensions/exception-handling-cpp-component-extensions.md)有关详细信息。

- 不允许使用函数指针的比较 **/clr**。

- 在不允许使用未完全保持原型的函数 **/clr**。

- 不支持以下编译器选项 **/clr**:

  - **/ EHsc**并 **/EHs** (**/clr**意味着 **/EHa** (请参阅[/EH （异常处理模型）](eh-exception-handling-model.md))

  - **/fp: strict**并 **/fp： 除**(请参阅[/fp （指定浮点行为）](fp-specify-floating-point-behavior.md))

  - [/Zd](z7-zi-zi-debug-information-format.md)

  - [/Gm](gm-enable-minimal-rebuild.md)

  - [/MT](md-mt-ld-use-run-time-library.md)

  - [/RTC](rtc-run-time-error-checks.md)

  - [/ZI](z7-zi-zi-debug-information-format.md)

- 组合`_STATIC_CPPLIB`预处理器定义 (`/D_STATIC_CPPLIB`) 和 **/clr**编译器选项不受支持。 这是因为此定义会使你的应用程序使用多线程静态链接C++标准库，这不受支持。 有关详细信息，请参阅[/MD、 /MT、 /LD （使用运行时库）](md-mt-ld-use-run-time-library.md)主题。

- 使用时 **/Zi**与 **/clr**，有性能产生影响。 有关详细信息，请参阅[/Zi](z7-zi-zi-debug-information-format.md)。

- 将宽字符传递到.NET Framework 但未指定输出例程[/zc: wchar_t](zc-wchar-t-wchar-t-is-native-type.md)或而无需强制转换到字符`__wchar_t`将导致输出显示为`unsigned short int`。 例如：

    ```cpp
    Console::WriteLine(L' ')              // Will output 32.
    Console::WriteLine((__wchar_t)L' ')   // Will output a space.
    ```

- [/GS](gs-buffer-security-check.md)进行编译时，将忽略 **/clr**，除非函数是下`#pragma`[非托管](../../preprocessor/managed-unmanaged.md)或如果该函数必须编译为本机，在这种情况下将生成编译器警告 C4793，默认情况下处于关闭状态。

- 请参阅[/ENTRY](entry-entry-point-symbol.md)函数的托管应用程序签名要求。

- 使用应用程序编译 **/openmp**并 **/clr**只能在单个 appdomain 的进程中运行。  请参阅[/openmp （启用 OpenMP 2.0 支持）](openmp-enable-openmp-2-0-support.md)有关详细信息。

- 采用可变数量的参数 (varargs) 的函数中将生成为本机函数。 变量自变量位置中的任何托管的数据类型将封送到本机类型中。 请注意，<xref:System.String?displayProperty=fullName>类型都是实际的宽字符字符串，但其封送到单字节字符字符串。 因此如果 printf 说明符 %S （wchar_t *），它将封送到 %s 字符串相反。

- 在使用 va_arg 宏，使用编译时，可能会收到意外的结果 **/clr: pure**。 有关详细信息，请参阅[va_arg、 va_copy、 va_end、 va_start](../../c-runtime-library/reference/va-arg-va-copy-va-end-va-start.md)。 **/Clr: pure**并 **/clr: safe**编译器选项在 Visual Studio 2015 中弃用，在 Visual Studio 2017 中不受支持。 必须为"纯"或"安全"的代码应移植到C#。

- 不应调用，从托管代码，遍历堆栈，以获得参数信息 （函数参数），则任何函数P/Invoke 层会导致该信息可以进一步在堆栈的下层。  例如，不编译与代理/存根 **/clr**。

- 函数将编译为托管的代码，只要有可能，但不是所有C++构造可以转换为托管代码。  在函数的函数的基础上作出此决定。 如果函数的任何部分不能转换为托管代码中，将转换整个函数为本机代码。 在以下情况下阻止编译器生成托管的代码。

  - 编译器生成的 thunk 或帮助器函数。 通过函数指针，其中包括虚拟函数调用任何函数调用将生成本机 thunk。

  - 函数调用`setjmp`或`longjmp`。

  - 使用某些内部函数的例程来直接操作计算机资源的函数。 例如，使用`__enable`并`__disable`，`_ReturnAddress`和`_AddressOfReturnAddress`，或多媒体内部函数将在本机代码中的所有结果。

  - 后面的函数`#pragma unmanaged`指令。 (请注意，反转后的`#pragma managed`，也支持。)

  - 包含对引用的函数对齐类型，即，声明类型使用`__declspec(align(...))`。

## <a name="see-also"></a>请参阅

- [/cgthreads（公共语言运行时编译）](clr-common-language-runtime-compilation.md)
