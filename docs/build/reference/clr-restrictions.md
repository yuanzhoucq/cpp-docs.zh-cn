---
title: "-clr 限制 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: /clr compiler option [C++], restrictions
ms.assetid: 385f6462-2c68-46d6-810e-469553ead447
caps.latest.revision: "27"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: aa0bdc6a5a62b517c252a35d8f1193b34d6e0d32
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="clr-restrictions"></a>/clr 限制
请注意以下限制的使用**/clr**:  
  
-   在结构化的异常处理程序中，有的使用限制`_alloca`编译时**/clr**。 有关详细信息，请参阅[_alloca](../../c-runtime-library/reference/alloca.md)。  
  
-   运行时错误检查的使用是不与有效**/clr**。 有关详细信息，请参阅[如何：使用本机运行时检查](/visualstudio/debugger/how-to-use-native-run-time-checks)。  
  
-   当**/clr**是用于编译仅使用标准 c + + 语法的程序，以下准则适用于内联程序集的使用：  
  
    -   假定的本机堆栈布局的知识的内联程序集代码，调用当前函数或其他低级别的有关计算机的信息的外部的约定如果可能会失败知识应用于托管函数的堆栈帧。 包含内联程序集代码的函数将生成为非托管函数，就像它们已放置在单独模块而无需编译**/clr**。  
  
    -   不支持内联程序集代码中传递复制构造函数参数的函数。  
  
-   [Vprintf 函数](../../c-runtime-library/vprintf-functions.md)从编译的程序不能调用**/clr**。  
  
-   [裸](../../cpp/naked-cpp.md) [__declspec](../../cpp/declspec.md)修饰符忽略在 /clr 下。  
  
-   通过设置的转换器函数[_set_se_translator](../../c-runtime-library/reference/set-se-translator.md)将影响仅非托管代码中的 catch 语句。 请参阅[异常处理](../../windows/exception-handling-cpp-component-extensions.md)有关详细信息。  
  
-   在不允许的函数指针比较**/clr**。  
  
-   在不允许使用未完全保持原型的函数**/clr**。  
  
-   不支持以下编译器选项**/clr**:  
  
    -   **/ EHsc**和**/EHs** (**/clr**意味着**/EHa** (请参阅[/EH （异常处理模型）](../../build/reference/eh-exception-handling-model.md))  
  
    -   **/fp: strict**和**/fp： 除**(请参阅[/fp （指定浮点行为）](../../build/reference/fp-specify-floating-point-behavior.md))  
  
    -   [/Zd](../../build/reference/z7-zi-zi-debug-information-format.md)  
  
    -   [/Gm](../../build/reference/gm-enable-minimal-rebuild.md)  
  
    -   [/MT](../../build/reference/md-mt-ld-use-run-time-library.md)  
  
    -   [/RTC](../../build/reference/rtc-run-time-error-checks.md)  
  
    -   **/ZI**  
  
-   组合`_STATIC_CPPLIB`预处理器定义 (`/D_STATIC_CPPLIB`) 和**/clr**或**/clr: pure**编译器选项不支持。 这是因为此定义会使你的应用程序与静态多线程 c + + 标准库链接，这不受支持。 有关详细信息，请参阅[/MD、 /MT、 /LD （使用运行时库）](../../build/reference/md-mt-ld-use-run-time-library.md)主题。  
  
-   [/J](../../build/reference/j-default-char-type-is-unsigned.md)不支持**/clr: safe**或**/clr: pure**。 **/clr:pure** 和 **/clr:safe** 编译器选项在 Visual Studio 2015 中已弃用。  
  
-   纯模式下编译不支持 ATL 和 MFC 库 (**/clr: pure**)。 你可以使用**/clr: pure**使用 c + + 标准库和 CRT 如果还使用进行编译**/MD**或**/MDd**。  
  
-   使用时**/Zi**与**/clr**，但会性能产生影响。 有关详细信息，请参阅[/Zi](../../build/reference/z7-zi-zi-debug-information-format.md)。  
  
-   将宽字符传递到.NET Framework 而无需还指定输出例程[/zc: wchar_t](../../build/reference/zc-wchar-t-wchar-t-is-native-type.md)或不带强制转换为字符`__wchar_t`将显示为输出`unsigned short int`。 例如:  
  
    ```  
    Console::WriteLine(L' ')              // Will output 32.  
    Console::WriteLine((__wchar_t)L' ')   // Will output a space.  
    ```  
  
-   [/GS](../../build/reference/gs-buffer-security-check.md)与编译时将忽略**/clr**，除非函数是在`#pragma`[非托管](../../preprocessor/managed-unmanaged.md)或如果该函数必须编译为本机，在这种情况下编译器将生成警告 C4793，默认情况下处于关闭状态。  
  
-   请参阅[/ENTRY](../../build/reference/entry-entry-point-symbol.md)托管应用程序的函数签名要求。  
  
-   使用编译的应用程序**/openmp**和**/clr**仅在单个 appdomain 进程中运行。  请参阅[/openmp （启用 OpenMP 2.0 支持）](../../build/reference/openmp-enable-openmp-2-0-support.md)有关详细信息。  
  
-   采用数量可变的参数 (varargs) 的函数将生成为本机函数中。 变量自变量位置中的任何托管的数据类型将封送到本机类型中。 请注意，<xref:System.String?displayProperty=fullName>类型都是实际的宽字符字符串，但它们被封送到单字节字符字符串。 因此如果 printf 说明符 %S （wchar_t *），它将封送处理为 %s 字符串相反。  
  
-   当使用 va_arg 宏，使用编译时，你可能会收到意外的结果**/clr: pure**。  有关详细信息，请参阅[va_arg、 va_copy、 va_end、 va_start](../../c-runtime-library/reference/va-arg-va-copy-va-end-va-start.md)。  
  
-   如果你的应用程序传递的类型自变量[va_list](../../c-runtime-library/reference/va-arg-va-copy-va-end-va-start.md)函数声明为采用数目可变的参数，并且你的应用程序可以编译使用**/clr: pure**，CLR 将引发<xref:System.NotSupportedException>。 如果**/clr**使用相反，受影响的函数编译为本机代码，并正确执行。 如果**/clr: safe**是使用，则会发出诊断错误。  
  
-   你不应调用，从托管代码，检查堆栈来获取参数信息 （函数参数），则任何函数P/Invoke 层会导致该信息来进一步入堆栈。  例如，不编译代理/存根 （stub） 与**/clr**。  
  
-   函数将编译为托管代码，只要有可能，但不是所有 c + + 构造可以转换为托管代码。  函数通过函数地作出此决定。 如果函数的任何部分不能转换为托管代码中，将转换整个函数为本机代码。 以下情况下阻止编译器生成托管的代码。  
  
    -   编译器生成的 thunk 或帮助器函数。 对于通过函数指针，其中包括虚拟函数的调用任何函数调用将生成本机 thunk。  
  
    -   函数该调用`setjmp`或`longjmp`。  
  
    -   使用某些内部函数的例程来直接操作计算机资源的函数。 例如，使用`__enable`和`__disable`，`_ReturnAddress`和`_AddressOfReturnAddress`，或多媒体内部函数将在本机代码中的所有结果。  
  
    -   后面的函数`#pragma unmanaged`指令。 (请注意，逆， `#pragma managed`，也支持。)  
  
    -   包含对引用的函数对齐类型，即，声明类型使用`__declspec(align(...))`。  
  
-   不能使用[编译器 COM 支持](../../cpp/compiler-com-support.md)类与**/clr: pure**或**/clr: safe**。  
  
## <a name="see-also"></a>请参阅  
 [/cgthreads（公共语言运行时编译）](../../build/reference/clr-common-language-runtime-compilation.md)