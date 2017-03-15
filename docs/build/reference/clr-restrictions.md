---
title: "/clr 限制 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/clr 编译器选项 [C++], 限制"
ms.assetid: 385f6462-2c68-46d6-810e-469553ead447
caps.latest.revision: 27
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 27
---
# /clr 限制
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

请注意下列对使用 **\/clr** 的限制：  
  
-   在结构化异常处理程序中，当使用 **\/clr** 进行编译时，存在对使用 `_alloca` 的限制。  有关更多信息，请参见 [\_alloca](../../c-runtime-library/reference/alloca.md)。  
  
-   用 **\/clr** 时，使用运行时错误检查无效。  有关更多信息，请参见[运行时错误检查](../Topic/How%20to:%20Use%20Native%20Run-Time%20Checks.md)。  
  
-   当 **\/clr** 用于编译仅使用标准 C\+\+ 语法的程序时，下列原则适用于内联程序集的使用：  
  
    -   如果内联程序集代码假定有关本机堆栈布局、当前函数外部的调用约定或其他有关计算机的低级别信息的知识，则如果将该知识应用于托管函数的堆栈帧，则此内联程序集代码可能失败。  包含内联程序集代码的函数被生成为非托管函数，就像它们放在不使用 **\/clr** 编译的单独模块中一样。  
  
    -   传递复制构造函数参数的函数中的内联程序集代码不受支持。  
  
-   不能从用 **\/clr** 编译的程序调用 [vprintf 函数](../../c-runtime-library/vprintf-functions.md)。  
  
-   [naked](../../cpp/naked-cpp.md) [\_\_declspec](../../cpp/declspec.md) 修饰符在 \/clr 下被忽略。  
  
-   [\_set\_se\_translator](../../c-runtime-library/reference/set-se-translator.md) 设置的转换器函数将只影响非托管代码中的 Catch。  有关更多信息，请参见[异常处理](../../windows/exception-handling-cpp-component-extensions.md)。  
  
-   在 **\/clr** 下不允许比较函数指针。  
  
-   在 **\/clr** 下不允许使用未完全保持原型的函数。  
  
-   **\/clr** 不支持下列编译器选项：  
  
    -   **\/EHsc** 和 **\/EHs** \(**\/clr** 意味着 **\/EHa**（请参见 [\/EH（异常处理模型）](../../build/reference/eh-exception-handling-model.md)）  
  
    -   **\/fp:strict** 和 **\/fp:except**（请参见 [\/fp（指定浮点行为）](../../build/reference/fp-specify-floating-point-behavior.md)）  
  
    -   [\/Zd](../../build/reference/z7-zi-zi-debug-information-format.md)  
  
    -   [\/Gm](../../build/reference/gm-enable-minimal-rebuild.md)  
  
    -   [\/MT](../../build/reference/md-mt-ld-use-run-time-library.md)  
  
    -   [\/RTC](../../build/reference/rtc-run-time-error-checks.md)  
  
    -   **\/ZI**  
  
-   不支持 `_STATIC_CPPLIB` 预处理器定义 \(`/D_STATIC_CPPLIB`\) 和 **\/clr** 或 **\/clr:pure** 编译器选项的组合。  这是因为此定义会使您的应用程序与静态多线程标准 C\+\+ 库链接，而此库不受支持。  有关更多信息，请参见主题[\/MD、\/MT、\/LD（使用运行库）](../../build/reference/md-mt-ld-use-run-time-library.md)。  
  
-   **\/clr:safe** 或 **\/clr:pure** 不支持 [\/J](../../build/reference/j-default-char-type-is-unsigned.md)。  
  
-   纯模式编译 \(**\/clr:pure**\) 不支持 ATL 和 MFC 库。  如果您还使用 **\/MD** 或 **\/MDd** 进行编译，则可以将 **\/clr:pure** 与标准 C\+\+ 库和 CRT 一起使用。  
  
-   当 **\/Zi** 与 **\/clr** 一起使用时，存在性能的含义。  有关更多信息，请参见 [\/Zi](../../build/reference/z7-zi-zi-debug-information-format.md)。  
  
-   如果将宽字符传递给 .NET Framework 输出例程，但没有同时指定 [\/Zc:wchar\_t](../../build/reference/zc-wchar-t-wchar-t-is-native-type.md) 或没有将字符强制转换为 `__wchar_t`，将导致输出显示为 `unsigned short int`。  例如：  
  
    ```  
    Console::WriteLine(L' ')              // Will output 32.  
    Console::WriteLine((__wchar_t)L' ')   // Will output a space.  
    ```  
  
-   在用 **\/clr** 编译时将忽略 [\/GS](../../build/reference/gs-buffer-security-check.md)，除非函数在 `#pragma` [非托管](../../preprocessor/managed-unmanaged.md)下面，或者函数必须编译到本机（在这种情况下，编译器将生成警告 C4793，而默认情况下该警告是关闭的）。  
  
-   有关托管应用程序的函数签名要求，请参见 [\/ENTRY](../../build/reference/entry-entry-point-symbol.md)。  
  
-   用 **\/openmp** 和 **\/clr** 编译的应用程序只能在单个 appdomain 进程中运行。有关更多信息，请参见[\/openmp（启用 OpenMP 2.0 支持）](../../build/reference/openmp-enable-openmp-2-0-support.md)。  
  
-   采用数量不固定的参数的函数 \(varargs\) 将作为本机函数生成。  可变参数位置中的任何托管数据类型都将被封送为本机类型。  请注意，<xref:System.String?displayProperty=fullName> 类型实际上是宽字符字符串，但它们被封送为单字节字符字符串。  因此，如果 printf 说明符是 %S \(wchar\_t\*\)，它将改为封送为 %s 字符串。  
  
-   使用 va\_arg 宏时，用 **\/clr:pure** 编译可能会获得意外的结果。有关详细信息，请参阅[va\_arg、va\_copy、va\_end、va\_start](../../c-runtime-library/reference/va-arg-va-copy-va-end-va-start.md)。  
  
-   如果您的应用程序将 [va\_list](../../c-runtime-library/reference/va-arg-va-copy-va-end-va-start.md) 类型的参数传递给声明为采用[参数的变量数量](../../misc/variable-argument-lists.md)的函数，并且使用 **\/clr:pure** 编译应用程序，则 CLR 将引发 <xref:System.NotSupportedException>。  如果改用 **\/clr** ，受影响的功能被编译为本机代码，并正确执行。  如果使用 **\/clr:safe**，则发出错误诊断。  
  
-   不应从托管代码调用任何浏览堆栈以获取参数信息（函数变量）的函数；P\/Invoke 层使这些信息处于堆栈的较低位置。例如，不要使用 **\/clr** 编译代理\/存根。  
  
-   函数将尽可能编译为托管代码，但并非所有 C\+\+ 构造都可转换为托管代码。这取决于具体函数。  如果函数的任何部分都无法转换为托管代码，则整个函数将转换为本机代码。  下列情况会阻止编译器生成托管代码。  
  
    -   编译器生成的 thunk 或 helper 函数。  对于通过函数指针的任何函数调用（包括虚函数调用），将生成本机 thunk。  
  
    -   调用 `setjmp` 或 `longjmp` 的函数。  
  
    -   使用特定内部例程直接操作计算机资源的函数。  例如，使用 `__enable` 和 `__disable`、`_ReturnAddress` 和 `_AddressOfReturnAddress` 或多媒体内部例程都将生成本机代码。  
  
    -   跟在 `#pragma unmanaged` 指令后面的函数。（请注意，也支持反向的 `#pragma managed`。）  
  
    -   包含引用对齐类型（即使用 `__declspec(align(...))` 声明的类型）的函数。  
  
-   不能将 [编译器 COM 支持](../../cpp/compiler-com-support.md) 类与 **\/clr:pure** 或 **\/clr:safe** 一起使用。  
  
## 请参阅  
 [\/clr（公共语言运行时编译）](../../build/reference/clr-common-language-runtime-compilation.md)