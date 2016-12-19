---
title: "预定义的宏 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "_ATL_VER"
  - "__ATOM__"
  - "__AVX__"
  - "__AVX2__"
  - "_CHAR_UNSIGNED"
  - "__CLR_VER"
  - "_CONTROL_FLOW_GUARD"
  - "__COUNTER__"
  - "__cplusplus"
  - "__cplusplus_cli"
  - "__cplusplus_winrt"
  - "_CPPRTTI"
  - "_CPPUNWIND"
  - "__DATE__"
  - "_DEBUG"
  - "_DLL"
  - "__FILE__"
  - "__FUNCDNAME__"
  - "__FUNCSIG__"
  - "__FUNCTION__"
  - "_INTEGRAL_MAX_BITS"
  - "_ISO_VOLATILE"
  - "_KERNEL_MODE"
  - "__LINE__"
  - "_M_AMD64"
  - "_M_ARM"
  - "_M_ARM_ARMV7VE"
  - "_M_ARM_FP"
  - "_M_ARM64"
  - "_M_CEE"
  - "_M_CEE_PURE"
  - "_M_CEE_SAFE"
  - "_M_FP_EXCEPT"
  - "_M_FP_FAST"
  - "_M_FP_PRECISE"
  - "_M_FP_STRICT"
  - "_M_IX86"
  - "_M_IX86_FP"
  - "_M_X64"
  - "_MANAGED"
  - "_MFC_VER"
  - "_MSC_BUILD"
  - "_MSC_EXTENSIONS"
  - "_MSC_FULL_VER"
  - "_MSC_VER"
  - "_MSVC_LANG"
  - "__MSVC_RUNTIME_CHECKS"
  - "_MT"
  - "_NATIVE_WCHAR_T_DEFINED"
  - "_NO_SIZED_DEALLOCATION"
  - "_OPENMP"
  - "_PREFAST_"
  - "_RESUMABLE_FUNCTIONS_SUPPORTED"
  - "_RTC_CONVERSION_CHECKS_ENABLED"
  - "__STDC__"
  - "__STDC_HOSTED__"
  - "__STDCPP_THREADS__"
  - "__TIME__"
  - "__TIMESTAMP__"
  - "__VA_ARGS__"
  - "_VC_NODEFAULTLIB"
  - "_WCHAR_T_DEFINED"
  - "_WIN32"
  - "_WIN64"
  - "_WINRT_DLL"
  - "__func__"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "时间戳，预处理器宏"
  - "cl.exe 编译器版本号"
  - "版本号，C/c + + 编译器 (cl.exe)"
  - "宏，预定义的 c + +"
  - "预处理器，宏"
  - "预定义的宏"
  - "_ATL_VER 宏"
  - "__ATOM__ 宏"
  - "__AVX__ 宏"
  - "__AVX2__ 宏"
  - "_CHAR_UNSIGNED 宏"
  - "__CLR_VER 宏"
  - "_CONTROL_FLOW_GUARD 宏"
  - "__COUNTER__ 宏"
  - "__cplusplus 宏"
  - "__cplusplus_cli 宏"
  - "__cplusplus_winrt 宏"
  - "_CPPRTTI 宏"
  - "_CPPUNWIND 宏"
  - "__DATE__ 宏"
  - "_DEBUG 宏"
  - "_DLL 宏"
  - "__FILE__ 宏"
  - "__FUNCDNAME__ 宏"
  - "__FUNCSIG__ 宏"
  - "__FUNCTION__ 宏"
  - "_INTEGRAL_MAX_BITS 宏"
  - "_ISO_VOLATILE 宏"
  - "_KERNEL_MODE 宏"
  - "__LINE__ 宏"
  - "_M_AMD64 宏"
  - "_M_ARM 宏"
  - "_M_ARM_ARMV7VE 宏"
  - "_M_ARM_FP 宏"
  - "_M_ARM64 宏"
  - "_M_CEE 宏"
  - "_M_CEE_PURE 宏"
  - "_M_CEE_SAFE 宏"
  - "_M_FP_EXCEPT 宏"
  - "_M_FP_FAST 宏"
  - "_M_FP_PRECISE 宏"
  - "_M_FP_STRICT 宏"
  - "_M_IX86 宏"
  - "_M_IX86_FP 宏"
  - "_M_X64 宏"
  - "_MANAGED 宏"
  - "_MFC_VER 宏"
  - "_MSC_BUILD 宏"
  - "_MSC_EXTENSIONS 宏"
  - "_MSC_FULL_VER 宏"
  - "_MSC_VER 宏"
  - "_MSVC_LANG 宏"
  - "__MSVC_RUNTIME_CHECKS 宏"
  - "_MT 宏"
  - "_NATIVE_WCHAR_T_DEFINED 宏"
  - "_NO_SIZED_DEALLOCATION 宏"
  - "_OPENMP 宏"
  - "_PREFAST_ 宏"
  - "_RESUMABLE_FUNCTIONS_SUPPORTED 宏"
  - "_RTC_CONVERSION_CHECKS_ENABLED 宏"
  - "__STDC__ 宏"
  - "__STDC_HOSTED__ 宏"
  - "__STDCPP_THREADS__ 宏"
  - "__TIME__ 宏"
  - "__TIMESTAMP__ 宏"
  - "__VA_ARGS__ 宏"
  - "_VC_NODEFAULTLIB 宏"
  - "_WCHAR_T_DEFINED 宏"
  - "_WIN32 宏"
  - "_WIN64 宏"
  - "_WINRT_DLL 宏"
  - "__func__ 标识符"
ms.assetid: 1cc5f70a-a225-469c-aed0-fe766238e23f
caps.latest.revision: 75
caps.handback.revision: 75
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 预定义的宏
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Visual c + + 编译器预定义某些预处理器宏，具体取决于语言 （C 或 c + +）、 编译目标，以及选择的编译器选项。  
  
 Visual c + + 支持 ANSI/ISO C99 标准和 ISO C + + 14 标准所指定的所需预定义的预处理器宏。 该实现还支持几个更多特定于 Microsoft 的预处理器宏。 仅针对特定的生成环境或编译器选项定义一些宏，宏。 除非另有说明，宏的定义整个翻译单元如同它们指定为 **/D** 编译器选项参数。 在定义时，宏是由预处理器在编译前扩展为指定的值。 预定义的宏不采用任何参数，并且不能重新定义。  
  
## <a name="standard-predefined-identifier"></a>标准的预定义的标识符  
 编译器支持 ISO C99 和 ISO C + + 11 中指定此预定义的标识符。  
  
-   **__func\_\_** 为函数本地将封闭函数的未限定和未修饰名称 `static``const` 数组 `char`。  
  
    ```cpp  
    void example(){  
        printf("%s\n", __func__);  
    } // prints "example"  
    ```  
  
## <a name="standard-predefined-macros"></a>标准预定义的宏  
 编译器支持 ISO C99 和 ISO C + + 14 标准所指定的这些预定义的宏。  
  
-   **__cplusplus** 翻译单元将作为 c + + 编译时定义为整数文字值。 否则，未定义。  
  
-   **__DATE\_\_** 当前源文件的编译日期。 日期是一个固定长度的字符串文字的窗体 *Mmm dd yyyy*。 月份名称 *Mmm* 等同于中的缩写的月份名称生成的 C 运行库日期 [asctime](../c-runtime-library/reference/asctime-wasctime.md) 函数。 日期的第一个字符 *dd* 是一个空间，如果值是小于 10。 始终定义此宏。  
  
-   **__FILE\_\_** 当前源文件的名称。 **__FILE\_\_** 扩展到字符的字符串文字。 若要确保显示该文件的完整路径，请使用 [/FC （完整路径的源代码文件中诊断程序）](../build/reference/fc-full-path-of-source-code-file-in-diagnostics.md)。 始终定义此宏。  
  
-   **__LINE\_\_** 定义为当前源文件中的整数行号。 值 **__LINE\_\_** 宏可通过使用更改 `#line` 指令。 始终定义此宏。  
  
-   **__STDC\_\_** 定义为 1，仅当作为 C 编译，如果 [/Za](../build/reference/za-ze-disable-language-extensions.md) 指定编译器选项。 否则，未定义。  
  
-   **__STDC_HOSTED\_\_** 定义为 1，如果实现是 *承载实现*, ，属于支持整个所需的标准库的支持。 否则，定义为 0。  
  
-   **__STDCPP_THREADS\_\_** 定义为 1，当且仅当一个程序可以有多个线程的执行，并且编译为 c + +。 否则，未定义。  
  
-   **__TIME\_\_** 预处理过的翻译单元的转换的时间。 时间是字符的字符串文字的窗体 *︰ 分︰ 秒*, ，由 C 运行时库返回的时间相同 [asctime](../c-runtime-library/reference/asctime-wasctime.md) 函数。 始终定义此宏。  
  
## <a name="microsoft-specific-predefined-macros"></a>Microsoft 专用预定的义宏  
 Microsoft Visual c + + 支持这些其他预定义的宏。  
  
-   **__ATOM\_\_** 定义为 1 时 [/favor:ATOM](../build/reference/favor-optimize-for-architecture-specifics.md) 设置编译器选项和编译器目标是 x86 或 x64。 否则，未定义。  
  
-   **__AVX\_\_** 定义为 1 时 [/arch:AVX](../build/reference/arch-x86.md) 或 [/arch: avx2 可以](../build/reference/arch-x86.md) 设置编译器选项和编译器目标是 x86 或 x64。 否则，未定义。  
  
-   **__AVX2\_\_** 定义为 1 时 [/arch: avx2 可以](../build/reference/arch-x86.md) 设置编译器选项和编译器目标是 x86 或 x64。 否则，未定义。  
  
-   **_CHAR_UNSIGNED** 默认值定义为 1 如果 `char` 类型是无符号。 此值设置时 [/J (默认 char 类型是无符号)](../build/reference/j-default-char-type-is-unsigned.md) 设置编译器选项。 否则，未定义。  
  
-   **__CLR_VER** 定义为整数文字表示在已编译的应用程序时使用的公共语言运行时版本。 在窗体中编码的值 `Mmmbbbbb`, ，其中 `M` 是运行时，主要版本 `mm` 是运行时的次要版本和 `bbbbb` 为内部版本号。 **__CLR_VER** 如果定义 [/clr](../build/reference/clr-common-language-runtime-compilation.md) 设置编译器选项。 否则，未定义。  
  
    ```cpp  
    // clr_ver.cpp  
    // compile with: /clr  
    using namespace System;  
    int main() {  
       Console::WriteLine(__CLR_VER);  
    }  
    ```  
  
-   **_CONTROL_FLOW_GUARD** 定义为 1 时 [/guard:cf （启用控制流防护）](../build/reference/guard-enable-control-flow-guard.md) 设置编译器选项。 否则，未定义。  
  
-   **__COUNTER\_\_** Expands 为整数文字，从 0 开始的和每次在源文件中使用，就会递增 1，或者包含的源文件标头。 **__COUNTER\_\_** 会记住其状态时使用预编译的头。 始终定义此宏。  
  
     此示例使用 `__COUNTER__` 要分配给同一类型的三个不同的对象的唯一标识符。  `exampleClass` 构造函数采用一个整数作为参数。 在 `main`, ，应用程序声明了三个对象类型的 `exampleClass`, ，并使用 `__COUNTER__` 用作唯一标识符参数︰  
  
    ```cpp  
    // macro__COUNTER__.cpp  
    // Demonstration of __COUNTER__, assigns unique identifiers to  
    // different objects of the same type.  
    // Compile by using: cl /EHsc /W4 macro__COUNTER__.cpp  
    #include <stdio.h>  
  
    class exampleClass {  
        int m_nID;  
    public:  
        // initialize object with a read-only unique ID  
        exampleClass(int nID) : m_nID(nID) {}  
        int GetID(void) { return m_nID; }  
    };  
  
    int main()  
    {  
        // __COUNTER__ is initially defined as 0  
        exampleClass e1(__COUNTER__);  
  
        // On the second reference, __COUNTER__ is now defined as 1  
        exampleClass e2(__COUNTER__);  
  
        // __COUNTER__ is now defined as 2  
        exampleClass e3(__COUNTER__);  
  
        printf("e1 ID: %i\n", e1.GetID());  
        printf("e2 ID: %i\n", e2.GetID());  
        printf("e3 ID: %i\n", e3.GetID());  
  
        // Output  
        // ------------------------------  
        // e1 ID: 0  
        // e2 ID: 1  
        // e3 ID: 2  
  
        return 0;  
    }  
    ```  
  
-   **__cplusplus_cli** 定义为整数文字值 200406 在作为 c + + 编译时和 [/clr](../build/reference/clr-common-language-runtime-compilation.md), ，[/clr: pure](../build/reference/clr-common-language-runtime-compilation.md), ，或 [/clr: safe](../build/reference/clr-common-language-runtime-compilation.md) 设置编译器选项。 否则，未定义。 在定义时， **__cplusplus_cli** 有效范围是整个翻译单元。  
  
    ```cpp  
    // cplusplus_cli.cpp  
    // compile by using /clr  
    #include "stdio.h"  
    int main() {  
       #ifdef __cplusplus_cli  
          printf("%d\n", __cplusplus_cli);  
       #else  
          printf("not defined\n");  
       #endif  
    }  
    ```  
  
-   **__cplusplus_winrt** 定义为整数文字值 201009 在作为 c + + 编译时和 [/ZW （Windows 运行时编译）](../build/reference/zw-windows-runtime-compilation.md) 设置编译器选项。 否则，未定义。  
  
-   **_CPPRTTI** 定义为 1 如果 [/GR （启用运行时类型信息）](../build/reference/gr-enable-run-time-type-information.md) 设置编译器选项。 否则，未定义。  
  
-   **_CPPUNWIND** 定义为 1，如果一个或多个 [/GX （启用异常处理）](../build/reference/gx-enable-exception-handling.md), ，[/clr （公共语言运行时编译）](../build/reference/clr-common-language-runtime-compilation.md), ，或 [/EH （异常处理模型）](../build/reference/eh-exception-handling-model.md) 设置编译器选项。 否则，未定义。  
  
-   **_DEBUG** 定义为 1 时 [/LDd](../build/reference/md-mt-ld-use-run-time-library.md), ，[/MDd](../build/reference/md-mt-ld-use-run-time-library.md), ，或 [/MTd](../build/reference/md-mt-ld-use-run-time-library.md) 设置编译器选项。 否则，未定义。  
  
-   **_DLL** 定义为 1 时 [/MD](../build/reference/md-mt-ld-use-run-time-library.md) 或 [/MDd](../build/reference/md-mt-ld-use-run-time-library.md) 设置 (多线程 DLL) 编译器选项。 否则，未定义。  
  
-   **__FUNCDNAME\_\_** 定义为一个字符串，它包含 [修饰名](../build/reference/decorated-names.md) 将封闭函数。 仅在函数内定义宏。  **__FUNCDNAME\_\_** 如果您使用不扩展宏 [/EP](../build/reference/ep-preprocess-to-stdout-without-hash-line-directives.md) 或 [/P](../build/reference/p-preprocess-to-a-file.md) 编译器选项。  
  
     此示例使用 `__FUNCDNAME__`, ，`__FUNCSIG__`, ，和 `__FUNCTION__` 宏来显示函数信息。  
  
     [!code-cpp[NVC_Predefined_Macros_Examples#1](../preprocessor/codesnippet/CPP/predefined-macros_1.cpp)]  
  
-   **__FUNCSIG\_\_** 定义为一个字符串，它包含封闭函数的签名。 仅在函数内定义宏。  **__FUNCSIG\_\_** 如果您使用不扩展宏 [/EP](../build/reference/ep-preprocess-to-stdout-without-hash-line-directives.md) 或 [/P](../build/reference/p-preprocess-to-a-file.md) 编译器选项。 当针对 64 位目标编译，调用约定是 `__cdecl` 默认情况下。 有关用法的示例，请参阅 `__FUNCDNAME__` 宏。  
  
-   **__FUNCTION\_\_** 定义为包含封闭函数的未修饰的名称的字符串文字。 仅在函数内定义宏。  **__FUNCTION\_\_** 如果您使用不扩展宏 [/EP](../build/reference/ep-preprocess-to-stdout-without-hash-line-directives.md) 或 [/P](../build/reference/p-preprocess-to-a-file.md) 编译器选项。 有关用法的示例，请参阅 `__FUNCDNAME__` 宏。  
  
-   **_INTEGRAL_MAX_BITS** 为整数文字值 64 的定义、 非向量整型的最大大小 （以位为单位）。 始终定义此宏。  
  
    ```cpp  
    // integral_max_bits.cpp  
    #include <stdio.h>  
    int main() {  
       printf("%d\n", _INTEGRAL_MAX_BITS);  
    }  
    ```  
  
-   **__INTELLISENSE\_\_** 定义为 1 期间 IntelliSense 编译器将传递在 Visual Studio IDE 中。 否则，未定义。 可以使用此宏来保护的代码 IntelliSense 编译器不了解，或使用它来生成和智能感知编译器之间切换。 有关详细信息，请参阅 [的智能感知缓慢疑难解答提示](https://blogs.msdn.microsoft.com/vcblog/2011/03/29/troubleshooting-tips-for-intellisense-slowness/)。  
  
-   **_ISO_VOLATILE** 为 1 如果定义 [/volatile: iso](../build/reference/volatile-volatile-keyword-interpretation.md) 设置编译器选项。 否则，未定义。  
  
-   **_KERNEL_MODE** 为 1 如果定义 [/kernel （创建内核模式二进制）](../build/reference/kernel-create-kernel-mode-binary.md) 设置编译器选项。 否则，未定义。  
  
-   **_M_AMD64** 定义为整数文字值 100 的编译该面向 x64 处理器。 否则，未定义。  
  
-   **_M_ARM** 为整数文字值 7 面向 ARM 处理器的编译进行定义。 否则，未定义。  
  
-   **_M_ARM_ARMV7VE** 定义为 1 时 [/arch: armv7ve](../build/reference/arch-arm.md) 面向 ARM 处理器的编译进行设置编译器选项。 否则，未定义。  
  
-   **_M_ARM_FP** 定义为整数文字值，该值指示该 [/arch](../build/reference/arch-arm.md) 编译器选项已设置，如果编译目标，则 ARM 处理器。 否则，未定义。  
  
    -   如果不是 30-39 的范围中 **/arch** ARM 选项已指定，对于 ARM 中指示的默认体系结构已设置 (`VFPv3`)。  
  
    -   在范围内 40-49 if **/arch: vfpv4** 设置。  
  
    -   请参阅 [/arch (ARM)](../build/reference/arch-arm.md) 有关详细信息。  
  
-   **_M_ARM64** 定义为 1 的面向 64 位 ARM 处理器的编译。 否则，未定义。  
  
-   **_M_CEE** 定义为 001 如果任何 [/clr （公共语言运行时编译）](../build/reference/clr-common-language-runtime-compilation.md) 设置编译器选项。 否则，未定义。  
  
-   **_M_CEE_PURE** 定义为 001 if [/clr: pure](../build/reference/clr-common-language-runtime-compilation.md) 设置编译器选项。 否则，未定义。  
  
-   **_M_CEE_SAFE** 定义为 001 if [/clr: safe](../build/reference/clr-common-language-runtime-compilation.md) 设置编译器选项。 否则，未定义。  
  
-   **_M_FP_EXCEPT** 定义为 1 如果 [/fp︰ 除](../build/reference/fp-specify-floating-point-behavior.md) 或 [/fp: strict](../build/reference/fp-specify-floating-point-behavior.md) 设置编译器选项。 否则，未定义。  
  
-   **_M_FP_FAST** 定义为 1 如果 [/fp:fast](../build/reference/fp-specify-floating-point-behavior.md) 设置编译器选项。 否则，未定义。  
  
-   **_M_FP_PRECISE** 定义为 1 如果 [/fp︰ 精确](../build/reference/fp-specify-floating-point-behavior.md) 设置编译器选项。 否则，未定义。  
  
-   **_M_FP_STRICT** 定义为 1 如果 [/fp: strict](../build/reference/fp-specify-floating-point-behavior.md) 设置编译器选项。 否则，未定义。  
  
-   **_M_IX86** 定义为整数文字值 600 的编译该面向 x86 处理器。 没有为 x64 或 ARM 编译目标定义此宏。  
  
-   **_M_IX86_FP** 定义为整数文字值，该值指示 [/arch](../build/reference/arch-arm.md) 编译器选项的设置，则默认值。 此宏始终定义的编译目标时 x86 处理器。 否则，未定义。 在定义时，其值为︰  
  
    -   0 **/arch:IA32** 编译器选项已设置。  
  
    -   1 如果 **/arch:SSE** 编译器选项已设置。  
  
    -   2 如果 **/arch:SSE2**, ，**/arch:AVX** 或 **/arch: avx2 可以** 编译器选项已设置。 如果此值为默认值 **/arch** 未指定编译器选项。 当 **/arch:AVX** 指定，则该宏 **__AVX\_\_** 也进行了定义。 当 **/arch: avx2 可以** 指定，则同时 **__AVX\_\_** 和 **__AVX2\_\_** 还定义了。  
  
    -   请参阅 [/arch (x86)](../build/reference/arch-x86.md) 有关详细信息。  
  
-   **_M_X64** 定义为整数文字值 100 的编译该面向 x64 处理器。 否则，未定义。  
  
-   **_MANAGED** 指 1 [/clr](../build/reference/clr-common-language-runtime-compilation.md) 设置编译器选项。 否则，未定义。  
  
-   **_MSC_BUILD** 定义为整数文字，其中包含编译器的版本号的修订号元素。 修订版本号是版本号的句点分隔的第四个元素。 例如，如果 Visual c + + 编译器的版本号为 15.00.20706.01， **_MSC_BUILD** 宏计算结果为 1。 始终定义此宏。  
  
-   **_MSC_EXTENSIONS** 定义为 1 如果 [/Ze （启用语言扩展）](../build/reference/za-ze-disable-language-extensions.md) 设置编译器选项，这是默认设置。 否则，未定义。  
  
-   **_MSC_FULL_VER** 定义为整数文本进行编码主要，次版本号和内部数字元素的数目的编译器的版本号。 主版本号是句点分隔的版本号的第一个元素、 次版本号是第二个元素和内部版本号是第三个元素。 例如，如果 Visual c + + 编译器的版本号为 15.00.20706.01， **_MSC_FULL_VER** 宏计算结果为 150020706。 输入 **cl /？** 通过在命令行查看编译器的版本号。 始终定义此宏。  
  
-   **_MSC_VER** 作为整形文本进行编码编译器的版本号的主要和次要数字元素定义。 主版本号是句点分隔的版本号的第一个元素和次版本号是第二个元素。 例如，如果 Visual c + + 编译器的版本号为 17.00.51106.1， **_MSC_VER** 宏计算结果为 1700年。 输入 **cl /？** 通过在命令行查看编译器的版本号。 始终定义此宏。  
  
-   **_MSVC_LANG** 定义为一个整数，指定由编译器针对 c + + 语言标准。 如果宏时编译为 c + +，为整数型值 201402 [/std:c + + 14](../Topic/-std%20\(Specify%20Language%20Standard%20Version\).md) 编译器选项是否设置，默认情况下，它是设置为更高时，未指定时，值 [/std:c + + 中最新](../Topic/-std%20\(Specify%20Language%20Standard%20Version\).md) 设置编译器选项。 否则，该宏是不确定的。  **_MSVC_LANG** 宏和 [/std （指定语言标准版本）](../Topic/-std%20\(Specify%20Language%20Standard%20Version\).md) 编译器选项是在 Visual Studio 2015 更新 3 开始。  
  
-   **__MSVC_RUNTIME_CHECKS** 定义为 1，如果其中的 [/RTC](../build/reference/rtc-run-time-error-checks.md) 设置编译器选项。 否则，未定义。  
  
-   **_MT** 定义为 1 时 [/MD 或 /MDd](../build/reference/md-mt-ld-use-run-time-library.md) (多线程 DLL) 或 [/MT 或 /MTd](../build/reference/md-mt-ld-use-run-time-library.md) 指定 （多线程）。 否则，未定义。  
  
-   **_NATIVE_WCHAR_T_DEFINED** 定义为 1 时 [/zc: wchar_t](../build/reference/zc-wchar-t-wchar-t-is-native-type.md) 设置编译器选项。 否则，未定义。  
  
-   **_OPENMP** 定义为整数文字 200203 表示由 Visual c + + 中实现的 OpenMP 规范的日期，如果 [/openmp （启用 OpenMP 2.0 支持）](../build/reference/openmp-enable-openmp-2-0-support.md) 设置编译器选项。 否则，未定义。  
  
    ```cpp  
    // _OPENMP_dir.cpp  
    // compile with: /openmp   
    #include <stdio.h>   
    int main() {  
       printf("%d\n", _OPENMP);  
    }  
    ```  
  
-   **_PREFAST\_** 定义为 1 时 [/ 分析](../build/reference/analyze-code-analysis.md) 设置编译器选项。 否则，未定义。  
  
-   **__TIMESTAMP\_\_** 作为一个字符串，它包含的日期和时间的当前源文件返回的 C 运行库的缩写，常量长度窗体的上次修改定义 [asctime](../c-runtime-library/reference/asctime-wasctime.md) 正常工作，例如， `Fri 19 Aug 13:32:58 2016`。 始终定义此宏。  
  
-   **_VC_NODEFAULTLIB** 定义为 1 时 [/Zl （省略默认库名）](../build/reference/zl-omit-default-library-name.md) 设置编译器选项。 否则，未定义。  
  
-   **_WCHAR_T_DEFINED** 定义为 1 时默认 [/zc: wchar_t](../build/reference/zc-wchar-t-wchar-t-is-native-type.md) 设置编译器选项。  **_WCHAR_T_DEFINED** 宏定义，但如果不具有任何值 **/Zc:wchar_t-** 设置编译器选项，并 `wchar_t` 项目中包含的系统标头文件中定义。 否则，未定义。  
  
-   **_WIN32** 定义为 1 时编译目标是 32 位 ARM x86，在 64 位 ARM 或 x64。 否则，未定义。  
  
-   **_WIN64** 编译目标为 64 位 ARM 或 x64 时定义为 1。 否则，未定义。  
  
-   **_WINRT_DLL** 定义为 1 时编译为 c + + 和 [/ZW （Windows 运行时编译）](../build/reference/zw-windows-runtime-compilation.md) 和 [/LD 或 /LDd](../build/reference/md-mt-ld-use-run-time-library.md) 设置编译器选项。 否则，未定义。  
  
 用于确定 ATL 或 MFC 库版本的预处理器宏不是由编译器预定义的。 因此它们未定义的预处理器指令中包含必需的标头之前，这些宏的定义在库的标头。  
  
-   **_ATL_VER** \< atldef.h > 中定义为整数文本进行编码的 ATL 版本编号。  
  
-   **_MFC_VER** \< afxver_.h > 中定义为整数文本进行编码的 MFC 版本编号。  
  
## <a name="see-also"></a>另请参阅  
 [宏 （C/c + +）](../preprocessor/macros-c-cpp.md)   
 [预处理器运算符](../preprocessor/preprocessor-operators.md)   
 [预处理器指令](../preprocessor/preprocessor-directives.md)