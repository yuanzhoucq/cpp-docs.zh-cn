---
title: 预定义的宏
ms.custom: update_every_version
ms.date: 11/12/2018
f1_keywords:
- _ATL_VER
- __ATOM__
- __AVX__
- __AVX2__
- _CHAR_UNSIGNED
- __CLR_VER
- _CONTROL_FLOW_GUARD
- __COUNTER__
- __cplusplus
- __cplusplus_cli
- __cplusplus_winrt
- _CPPRTTI
- _CPPUNWIND
- __DATE__
- _DEBUG
- _DLL
- __FILE__
- __FUNCDNAME__
- __FUNCSIG__
- __FUNCTION__
- _INTEGRAL_MAX_BITS
- _ISO_VOLATILE
- _KERNEL_MODE
- __LINE__
- _M_AMD64
- _M_ARM
- _M_ARM_ARMV7VE
- _M_ARM_FP
- _M_ARM64
- _M_CEE
- _M_CEE_PURE
- _M_CEE_SAFE
- _M_FP_EXCEPT
- _M_FP_FAST
- _M_FP_PRECISE
- _M_FP_STRICT
- _M_IX86
- _M_IX86_FP
- _M_X64
- _MANAGED
- _MFC_VER
- _MSC_BUILD
- _MSC_EXTENSIONS
- _MSC_FULL_VER
- _MSC_VER
- _MSVC_LANG
- __MSVC_RUNTIME_CHECKS
- _MT
- _NATIVE_WCHAR_T_DEFINED
- _NO_SIZED_DEALLOCATION
- _OPENMP
- _PREFAST_
- _RESUMABLE_FUNCTIONS_SUPPORTED
- _RTC_CONVERSION_CHECKS_ENABLED
- __STDC__
- __STDC_HOSTED__
- __STDCPP_THREADS__
- __TIME__
- __TIMESTAMP__
- __VA_ARGS__
- _VC_NODEFAULTLIB
- _WCHAR_T_DEFINED
- _WIN32
- _WIN64
- _WINRT_DLL
- __func__
helpviewer_keywords:
- timestamps, preprocessor macro
- cl.exe compiler, version number
- version numbers, C/C++ compiler (cl.exe)
- macros, predefined C++
- preprocessor, macros
- predefined macros
- _ATL_VER macro
- __ATOM__ macro
- __AVX__ macro
- __AVX2__ macro
- _CHAR_UNSIGNED macro
- __CLR_VER macro
- _CONTROL_FLOW_GUARD macro
- __COUNTER__ macro
- __cplusplus macro
- __cplusplus_cli macro
- __cplusplus_winrt macro
- _CPPRTTI macro
- _CPPUNWIND macro
- __DATE__ macro
- _DEBUG macro
- _DLL macro
- __FILE__ macro
- __FUNCDNAME__ macro
- __FUNCSIG__ macro
- __FUNCTION__ macro
- _INTEGRAL_MAX_BITS macro
- _ISO_VOLATILE macro
- _KERNEL_MODE macro
- __LINE__ macro
- _M_AMD64 macro
- _M_ARM macro
- _M_ARM_ARMV7VE macro
- _M_ARM_FP macro
- _M_ARM64 macro
- _M_CEE macro
- _M_CEE_PURE macro
- _M_CEE_SAFE macro
- _M_FP_EXCEPT macro
- _M_FP_FAST macro
- _M_FP_PRECISE macro
- _M_FP_STRICT macro
- _M_IX86 macro
- _M_IX86_FP macro
- _M_X64 macro
- _MANAGED macro
- _MFC_VER macro
- _MSC_BUILD macro
- _MSC_EXTENSIONS macro
- _MSC_FULL_VER macro
- _MSC_VER macro
- _MSVC_LANG macro
- __MSVC_RUNTIME_CHECKS macro
- _MT macro
- _NATIVE_WCHAR_T_DEFINED macro
- _NO_SIZED_DEALLOCATION macro
- _OPENMP macro
- _PREFAST_ macro
- _RESUMABLE_FUNCTIONS_SUPPORTED macro
- _RTC_CONVERSION_CHECKS_ENABLED macro
- __STDC__ macro
- __STDC_HOSTED__ macro
- __STDCPP_THREADS__ macro
- __TIME__ macro
- __TIMESTAMP__ macro
- __VA_ARGS__ macro
- _VC_NODEFAULTLIB macro
- _WCHAR_T_DEFINED macro
- _WIN32 macro
- _WIN64 macro
- _WINRT_DLL macro
- __func__ identifier
ms.assetid: 1cc5f70a-a225-469c-aed0-fe766238e23f
ms.openlocfilehash: 9dcc0922f3715d1e583605a071535f51fa8b2f57
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/05/2019
ms.locfileid: "59032448"
---
# <a name="predefined-macros"></a>预定义的宏

Visual c + + 编译器预定义某些预处理器宏，具体取决于语言 （C 或 c + +）、 编译目标，以及所选的编译器选项。

Visual c + + 支持由 ANSI/ISO C99 标准和 ISO C + + 14 标准指定的所需预定义的预处理器宏。 实现还支持多个更多特定于 Microsoft 的预处理器宏。 仅为特定的生成环境或编译器选项定义一些宏。 除非另有说明，如同它们指定为整个翻译单元定义宏 **/D**编译器选项参数。 在定义时，宏扩展到指定的值由编译之前预处理器。 预定义的宏不采用自变量，并且不能重新定义。

## <a name="standard-predefined-identifier"></a>预定义的标准标识符

编译器支持指定的 ISO C99 和 ISO C + + 11 此预定义的标识符。

- **&#95;&#95;func&#95; &#95;** 函数本地的封闭函数的非限定和无修饰名称**静态常量**数组**char**。

    ```cpp
    void example(){
        printf("%s\n", __func__);
    } // prints "example"
    ```

## <a name="standard-predefined-macros"></a>标准预定义的宏

编译器支持 ISO C99 和 ISO C + + 17 标准来指定这些预定义的宏。

- **&#95;&#95;cplusplus**在翻译单元作为 c + + 编译时定义为整数文字值。 否则，未定义。

- **&#95;&#95;日期&#95;&#95;** 当前源文件的编译日期。 日期是一个常量的长度的字符串文字的窗体*Mmm dd yyyy*。 月份名称*Mmm*等同于中的缩写的月份名称生成的 C 运行时库日期[asctime](../c-runtime-library/reference/asctime-wasctime.md)函数。 日期的第一个字符*dd*如果值小于 10 是一个空格。 始终定义此宏。

- **&#95;&#95;文件&#95;&#95;** 当前源文件的名称。 **&#95;&#95;文件&#95;&#95;** 扩展到字符的字符串文字。 若要确保显示文件的完整路径，请使用[/FC （完整的源代码文件路径中诊断）](../build/reference/fc-full-path-of-source-code-file-in-diagnostics.md)。 始终定义此宏。

- **&#95;&#95;行&#95;&#95;** 定义为当前源文件中的整数行号。 值 **&#95;&#95;行&#95;&#95;** 可以使用更改宏`#line`指令。 始终定义此宏。

- **&#95;&#95;STDC&#95; &#95;** 定义为 1，仅在作为 C 编译时，如果[/Za](../build/reference/za-ze-disable-language-extensions.md)编译器选项指定。 否则，未定义。

- **&#95;&#95;STDC&#95;HOSTED&#95; &#95;** 定义为 1，如果实现是*托管实现*，另一个支持整个所需的标准库。 否则，其定义为 0。

- **&#95;&#95;STDCPP&#95;线程&#95;&#95;** 定义为 1，当且仅当一个程序可以有多个线程的执行，并编译为 c + +。 否则，未定义。

- **&#95;&#95;时间&#95;&#95;** 预处理过的翻译单元的转换的时间。 时间是一个字符串文字的窗体*hh: mm:*，返回由 C 运行时库的时间相同[asctime](../c-runtime-library/reference/asctime-wasctime.md)函数。 始终定义此宏。

## <a name="microsoft-specific-predefined-macros"></a>特定于 Microsoft 的预定义的宏

Microsoft Visual c + + 支持这些其他预定义的宏。

- **&#95;&#95;ATOM&#95; &#95;** 定义为 1 时[/favor:ATOM](../build/reference/favor-optimize-for-architecture-specifics.md)设置编译器选项和编译器目标是 x86 或 x64。 否则，未定义。

- **&#95;&#95;AVX&#95; &#95;** 定义为 1 时[/arch: avx](../build/reference/arch-x86.md)或[/arch:avx2](../build/reference/arch-x86.md)设置编译器选项，编译器目标为 x86 或 x64。 否则，未定义。

- **&#95;&#95;AVX2&#95; &#95;** 定义为 1 时[/arch:avx2](../build/reference/arch-x86.md)设置编译器选项和编译器目标是 x86 或 x64。 否则，未定义。

- **&#95;CHAR&#95;未签名**定义为 1，如果默认**char**类型是无符号。 此值设置何时[/J (默认 char 类型是无符号)](../build/reference/j-default-char-type-is-unsigned.md)设置编译器选项。 否则，未定义。

- **&#95;&#95;CLR&#95;VER**定义为一个表示公共语言运行时编译应用程序时使用的版本的整数文字。 该值在窗体中编码`Mmmbbbbb`，其中`M`是在运行时的主要版本`mm`是运行时，次要版本和`bbbbb`是生成号。 **&#95;&#95;CLR&#95;VER**如果定义[/clr](../build/reference/clr-common-language-runtime-compilation.md)设置编译器选项。 否则，未定义。

    ```cpp
    // clr_ver.cpp
    // compile with: /clr
    using namespace System;
    int main() {
       Console::WriteLine(__CLR_VER);
    }
    ```

- **&#95;控制&#95;数据流&#95;防止**定义为 1 时[/guard: cf （启用控制流保护）](../build/reference/guard-enable-control-flow-guard.md)设置编译器选项。 否则，未定义。

- **&#95;&#95;计数器&#95;&#95;** 展开此项为整数文字，从 0 开始和每次源代码文件中使用时按 1 递增，或者包含的源文件标头。 **&#95;&#95;计数器&#95;&#95;** 当你使用预编译标头时，会记住其状态。 始终定义此宏。

  此示例使用`__COUNTER__`将唯一标识符分配到相同类型的三个不同的对象。 `exampleClass`构造函数采用整数作为参数。 在中`main`，该应用程序声明类型的三个对象`exampleClass`，并使用`__COUNTER__`作为唯一标识符参数：

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

- **&#95;&#95;cplusplus&#95;cli**定义为整数文字值 200406 在作为 c + + 编译时和一个[/clr](../build/reference/clr-common-language-runtime-compilation.md)设置编译器选项。 否则，未定义。 在定义时，  **&#95; &#95;cplusplus&#95;cli**实际上是整个翻译单元。

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

- **&#95;&#95;cplusplus&#95;winrt**定义为整数文字值 201009 在作为 c + + 编译时和[/ZW （Windows 运行时编译）](../build/reference/zw-windows-runtime-compilation.md)设置编译器选项。 否则，未定义。

- **&#95;CPPRTTI**定义为 1，如果[/GR （启用运行时类型信息）](../build/reference/gr-enable-run-time-type-information.md)设置编译器选项。 否则，未定义。

- **&#95;CPPUNWIND**定义为 1，如果一个或多个[/GX （启用异常处理）](../build/reference/gx-enable-exception-handling.md)， [/clr （公共语言运行时编译）](../build/reference/clr-common-language-runtime-compilation.md)，或[/EH （异常处理模型）](../build/reference/eh-exception-handling-model.md)编译器选项设置。 否则，未定义。

- **&#95;调试**定义为 1 时[/LDd](../build/reference/md-mt-ld-use-run-time-library.md)， [/MDd](../build/reference/md-mt-ld-use-run-time-library.md)，或[/MTd](../build/reference/md-mt-ld-use-run-time-library.md)设置编译器选项。 否则，未定义。

- **&#95;DLL**定义为 1 时[/MD](../build/reference/md-mt-ld-use-run-time-library.md)或[/MDd](../build/reference/md-mt-ld-use-run-time-library.md)设置 (多线程 DLL) 编译器选项。 否则，未定义。

- **&#95;&#95;FUNCDNAME&#95; &#95;** 定义为字符串文字包含[修饰名](../build/reference/decorated-names.md)封闭函数。 仅在函数内定义宏。 **&#95; &#95;FUNCDNAME&#95; &#95;** 如果你使用不扩展宏[/EP](../build/reference/ep-preprocess-to-stdout-without-hash-line-directives.md)或者[/P](../build/reference/p-preprocess-to-a-file.md)编译器选项。

   此示例使用`__FUNCDNAME__`， `__FUNCSIG__`，和`__FUNCTION__`宏，以显示函数的信息。

   [!code-cpp[NVC_Predefined_Macros_Examples#1](../preprocessor/codesnippet/CPP/predefined-macros_1.cpp)]

- **&#95;&#95;FUNCSIG&#95; &#95;** 定义为字符串文字包含封闭函数的签名。 仅在函数内定义宏。 **&#95; &#95;FUNCSIG&#95; &#95;** 如果你使用不扩展宏[/EP](../build/reference/ep-preprocess-to-stdout-without-hash-line-directives.md)或者[/P](../build/reference/p-preprocess-to-a-file.md)编译器选项。 当为 64 位目标编译，调用约定是`__cdecl`默认情况下。 有关用法的示例，请参阅`__FUNCDNAME__`宏。

- **&#95;&#95;函数&#95;&#95;** 定义为包含封闭函数的未修饰的名的字符串文字。 仅在函数内定义宏。 **&#95;&#95;函数&#95;&#95;** 如果你使用不扩展宏[/EP](../build/reference/ep-preprocess-to-stdout-without-hash-line-directives.md)或者[/P](../build/reference/p-preprocess-to-a-file.md)编译器选项。 有关用法的示例，请参阅`__FUNCDNAME__`宏。

- **&#95;整数&#95;MAX&#95;位**定义为整数文字值 64、 非向量整型类型的最大大小 （以位为单位）。 始终定义此宏。

   ```cpp
   // integral_max_bits.cpp
   #include <stdio.h>
   int main() {
      printf("%d\n", _INTEGRAL_MAX_BITS);
   }
   ```

- **&#95;&#95;INTELLISENSE&#95; &#95;** 定义为 1 期间 IntelliSense 编译器将在 Visual Studio IDE 中传递。 否则，未定义。 可以使用此宏来防止的代码 IntelliSense 编译器不了解，或使用它来生成和智能感知编译器之间切换。 有关详细信息，请参阅[IntelliSense 速度缓慢问题的疑难解答提示](https://blogs.msdn.microsoft.com/vcblog/2011/03/29/troubleshooting-tips-for-intellisense-slowness/)。

- **&#95;ISO&#95;可变**定义为 1，如果[/volatile: iso](../build/reference/volatile-volatile-keyword-interpretation.md)设置编译器选项。 否则，未定义。

- **&#95;内核&#95;模式**定义为 1，如果[/kernel （创建内核模式二进制）](../build/reference/kernel-create-kernel-mode-binary.md)设置编译器选项。 否则，未定义。

- **&#95;M&#95;AMD64**定义为整数值 100 的编译该面向 x64 处理器。 否则，未定义。

- **&#95;M&#95;ARM**定义为整数文字值 7 对于面向 ARM 处理器的编译。 否则，未定义。

- **&#95;M&#95;ARM&#95;ARMV7VE**定义为 1 时[/arch:armv7ve](../build/reference/arch-arm.md)面向 ARM 处理器的编译设置编译器选项。 否则，未定义。

- **&#95;M&#95;ARM&#95;FP**定义为整数文字值，该值指示这[/arch](../build/reference/arch-arm.md)编译器选项已设置，如果编译目标是 ARM 处理器。 否则，未定义。

  - 在范围内如果未 30-39 `/arch` ARM 选项指定了、 已设置，通过该值指示默认体系结构 ARM (`VFPv3`)。

  - 在范围内 40-49 如果`/arch:VFPv4`设置。

  - 请参阅[/arch (ARM)](../build/reference/arch-arm.md)有关详细信息。

- **&#95;M&#95;ARM64**定义为 1 以 64 位 ARM 处理器为目标的编译。 否则，未定义。

- **&#95;M&#95;CEE**定义为 001 如果任何[/clr （公共语言运行时编译）](../build/reference/clr-common-language-runtime-compilation.md)设置编译器选项。 否则，未定义。

- **&#95;M&#95;CEE&#95;纯**已开始在 Visual Studio 2015 中的弃用。 定义为 001 if [/clr: pure](../build/reference/clr-common-language-runtime-compilation.md)设置编译器选项。 否则，未定义。

- **&#95;M&#95;CEE&#95;安全**已开始在 Visual Studio 2015 中的弃用。 定义为 001 if [/clr: safe](../build/reference/clr-common-language-runtime-compilation.md)设置编译器选项。 否则，未定义。

- **&#95;M&#95;FP&#95;EXCEPT**定义为 1，如果[/fp： 除](../build/reference/fp-specify-floating-point-behavior.md)或[/fp: strict](../build/reference/fp-specify-floating-point-behavior.md)设置编译器选项。 否则，未定义。

- **&#95;M&#95;FP&#95;快速**定义为 1，如果[/fp: fast](../build/reference/fp-specify-floating-point-behavior.md)设置编译器选项。 否则，未定义。

- **&#95;M&#95;FP&#95;精确**定义为 1，如果[/fp： 精确](../build/reference/fp-specify-floating-point-behavior.md)设置编译器选项。 否则，未定义。

- **&#95;M&#95;FP&#95;STRICT**定义为 1，如果[/fp: strict](../build/reference/fp-specify-floating-point-behavior.md)设置编译器选项。 否则，未定义。

- **&#95;M&#95;IX86**定义为整数文本值 600 编译该面向 x86 处理器。 没有为 x64 或 ARM 编译目标定义此宏。

- **&#95;M&#95;IX86&#95;FP**定义为整数文字值，该值指示[/arch](../build/reference/arch-arm.md)编译器选项的集或默认值。 此宏始终定义编译目标为 x86 处理器。 否则，未定义。 在定义时，值为：

  - 0`/arch:IA32`编译器选项已设置。

  - 1，如果`/arch:SSE`编译器选项已设置。

  - 2 个 if `/arch:SSE2`，`/arch:AVX`或`/arch:AVX2`编译器选项已设置。 此值是默认值，如果`/arch`未指定编译器选项。 当`/arch:AVX`指定，则该宏 **&#95; &#95;AVX&#95; &#95;** 还定义。 当`/arch:AVX2`指定，则这两 **&#95; &#95;AVX&#95; &#95;** 并 **&#95; &#95;AVX2&#95; &#95;** 也被定义。

  - 请参阅[/arch (x86)](../build/reference/arch-x86.md)有关详细信息。

- **&#95;M&#95;X64**定义为整数值 100 的编译该面向 x64 处理器。 否则，未定义。

- **&#95;托管**定义为 1 时[/clr](../build/reference/clr-common-language-runtime-compilation.md)设置编译器选项。 否则，未定义。

- **&#95;MSC&#95;生成**定义为一个包含编译器的版本号的修订号元素的整数文字。 修订版本号是版本号的句点分隔的第四个元素。 例如，如果 Visual c + + 编译器的版本号为 15.00.20706.01，  **&#95;MSC&#95;生成**宏计算结果为 1。 始终定义此宏。

- **&#95;MSC&#95;扩展插件**定义为 1，如果[/Ze （启用语言扩展）](../build/reference/za-ze-disable-language-extensions.md)编译器选项设置，这是默认设置。 否则，未定义。

- **&#95;MSC&#95;完整&#95;VER**定义为整数文本进行编码主要，次要版本号和生成的编译器的版本号的数字元素。 主版本号是句点分隔的版本号的第一个元素、 次版本号是第二个元素和内部版本号是第三个元素。 例如，如果 Visual c + + 编译器的版本号为 15.00.20706.01，  **&#95;MSC&#95;完全&#95;VER**宏计算结果为 150020706。 输入`cl /?`在命令行查看编译器的版本号。 始终定义此宏。

- **&#95;MSC&#95;VER**定义为整数文本进行编码的编译器的版本号的主要和次要编号元素。 主版本号是句点分隔的版本号的第一个元素和次版本号是第二个元素。 例如，如果 Visual c + + 编译器的版本号为 17.00.51106.1，  **&#95;MSC&#95;VER**宏计算结果为 1700年。 输入`cl /?`在命令行查看编译器的版本号。 始终定义此宏。

   |Visual Studio 版本|&#95;MSC&#95;VER|
   |-|-|
   |Visual Studio 6.0|1200|
   |Visual Studio.NET 2002 (7.0)|1300|
   |Visual Studio.NET 2003 (7.1)|1310|
   |Visual Studio 2005 (8.0)|1400|
   |Visual Studio 2008 (9.0)|1500|
   |Visual Studio 2010 (10.0)|1600|
   |Visual Studio 2012 (11.0)|1700|
   |Visual Studio 2013 (12.0)|1800|
   |Visual Studio 2015 (14.0)|1900|
   |Visual Studio 2017 RTW (15.0)|1910|
   |Visual Studio 2017 版本 15.3|1911|
   |Visual Studio 2017 版本 15.5|1912|
   |Visual Studio 2017 版本 15.6|1913|
   |Visual Studio 2017 15.7 版|1914|
   |Visual Studio 2017 版本 15.8|1915|
   |Visual Studio 2017 版本 15.9|1916|

   若要测试的编译器版本或更新的 Visual Studio 或之后的给定版本中，使用 **>=** （大于或等于） 运算符比较 **&#95;MSC&#95;VER**针对已知的版本。 如果有多个版本进行比较以互相排斥的方式，我们建议你进行排序以降序版本号比较。 例如，此代码检查为编译器发布 Visual Studio 2015 及更高版本，然后编译器发布中或之后 Visual Studio 2013 中，然后，将所有编译器 Visual Studio 2013 之前发布的一项操作：

   ```cpp
   #if _MSC_VER >= 1900
   // . . .
   #elif _MSC_VER >= 1800
   // . . .
   #else
   // . . .
   #endif
   ```

   有关详细信息，请参阅[Visual c + + 编译器版本](https://blogs.msdn.microsoft.com/vcblog/2016/10/05/visual-c-compiler-version/)Visual c + + 团队博客中。

- **&#95;MSVC&#95;LANG**定义为整数，指定由编译器针对 c + + 语言标准。 如果宏时编译为 c + +，为整数文字值 201402 L [/std: c + + 14](../build/reference/std-specify-language-standard-version.md)编译器选项设置，或默认情况下; 如果它设置为 201703 L [/std: c + + 17](../build/reference/std-specify-language-standard-version.md)设置编译器选项; 并且设置为更高版本中，未指定值时[/std: c + + 最新](../build/reference/std-specify-language-standard-version.md)。 否则，该宏是不确定的。  **&#95;MSVC&#95;LANG**宏和[/std （指定语言标准版本）](../build/reference/std-specify-language-standard-version.md)编译器选项是在 Visual Studio 2015 Update 3 开始提供。

- **&#95;&#95;MSVC&#95;运行时&#95;检查**定义为 1 时的[/RTC](../build/reference/rtc-run-time-error-checks.md)设置编译器选项。 否则，未定义。

- **&#95;MT**定义为 1 时[/MD 或 /MDd](../build/reference/md-mt-ld-use-run-time-library.md) (多线程 DLL) 或[/MT 或 /MTd](../build/reference/md-mt-ld-use-run-time-library.md)指定 （多线程）。 否则，未定义。

- **&#95;本机&#95;WCHAR&#95;T&#95;定义**定义为 1 时[/zc: wchar_t](../build/reference/zc-wchar-t-wchar-t-is-native-type.md)编译器选项设置。 否则，未定义。

- **&#95;OPENMP**定义为表示由 Visual c + +，实现的 OpenMP 规范日期，如果整数文本 200203 [/openmp （启用 OpenMP 2.0 支持）](../build/reference/openmp-enable-openmp-2-0-support.md)设置编译器选项。 否则，未定义。

   ```cpp
   // _OPENMP_dir.cpp
   // compile with: /openmp
   #include <stdio.h>
   int main() {
      printf("%d\n", _OPENMP);
   }
   ```

- **&#95;PREFAST&#95;** 定义为 1 时[/analyze](../build/reference/analyze-code-analysis.md)设置编译器选项。 否则，未定义。

- **&#95;&#95;时间戳&#95;&#95;** 定义为字符串，其中包含的日期和时间返回 C 运行时库的缩写，常量长度为窗体中的当前的源文件的上次修改[asctime](../c-runtime-library/reference/asctime-wasctime.md)函数，例如， `Fri 19 Aug 13:32:58 2016`。 始终定义此宏。

- **&#95;VC&#95;NODEFAULTLIB**定义为 1 时[/Zl （省略默认库名）](../build/reference/zl-omit-default-library-name.md)设置编译器选项。 否则，未定义。

- **&#95;WCHAR&#95;T&#95;定义**定义为 1 时，默认[/zc: wchar_t](../build/reference/zc-wchar-t-wchar-t-is-native-type.md)设置编译器选项。  **&#95;WCHAR&#95;T&#95;定义**宏定义的但如果不具有任何值`/Zc:wchar_t-`编译器选项设置，并**wchar_t**中包含的系统标头文件中定义应用项目。 否则，未定义。

- **&#95;WIN32**定义为 1 编译目标为 32 位 ARM x86，在 64 位 ARM 或 x64。 否则，未定义。

- **&#95;WIN64**编译目标为 64 位 ARM 或 x64 时定义为 1。 否则，未定义。

- **&#95;WINRT&#95;DLL**定义为 1 时编译为 c + + 和同时[/ZW （Windows 运行时编译）](../build/reference/zw-windows-runtime-compilation.md)并[/LD 或 /LDd](../build/reference/md-mt-ld-use-run-time-library.md)编译器选项设置。 否则，未定义。

用于确定 ATL 或 MFC 库版本的预处理器宏不是由编译器预定义的。 这些宏是在库、 标头中定义，因此它们未定义的预处理器指令中包含必需的标头之前。

- **&#95;ATL&#95;VER**中定义\<atldef.h > 作为整形文本进行编码的 ATL 版本编号。

- **&#95;MFC&#95;VER**中定义\<afxver_.h > 作为整形文本进行编码的 MFC 版本编号。

## <a name="see-also"></a>请参阅

[宏 (C/C++)](../preprocessor/macros-c-cpp.md)<br/>
[预处理器运算符](../preprocessor/preprocessor-operators.md)<br/>
[预处理器指令](../preprocessor/preprocessor-directives.md)