---
title: "Visual C++ 更改历史记录（2003 - 2015）| Microsoft Docs"
ms.custom: 
ms.date: 08/30/2017
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: breaking changes [C++]
ms.assetid: b38385a9-a483-4de9-99a6-797488bc5110
caps.latest.revision: "124"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 8a2207b086b608fd601517c938572248147669ff
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="visual-c-change-history-2003---2015"></a>Visual C++ 更改历史记录（2003 - 2015）
本文介绍从 Visual Studio 2003 到 Visual Studio 2015 的所有重大更改。在本文中，术语“新行为”或“现在”指 Visual Studio 2015 及更高版本。 术语“旧行为”和“之前”指 Visual Studio 2013 和早期版本。 
 
 有关 Visual Studio 2017 的信息，请参阅 [Visual Studio 2017 中 Visual C++ 的新增功能](../what-s-new-for-visual-cpp-in-visual-studio.md)和 [Visual Studio 2017 中 Visual C++ 的符合性改进](../cpp-conformance-improvements-2017.md)。 
 > [!NOTE]
 > Visual Studio 2015 和 Visual Studio 2017 之间没有二进制的重大更改。

当你升级到 Visual C++ 编译器的新版本后，可能会在之前编译并正常运行的代码中遇到编译和/或运行时错误。 新版本中会引起这类问题的更改称为 *重大更改*，通常，修改 C++ 语言标准、函数签名或内存中的对象布局时需要进行这种更改。  
  
 若要避免难以检测和诊断的运行时错误，我们建议你永远不静态链接到使用不同编译器版本编译的二进制文件。 此外，当你升级 EXE 或 DLL 项目时，请确保升级它所链接的库。 如果使用 CRT（C 运行时）或 C++ 标准库（C++ 标准库）类型，请勿在使用不同编译器版本编译的二进制文件（包括 DLL）之间传递这些类型。 有关详细信息，请参阅[跨 DLL 边界传递 CRT 对象的潜在错误](../c-runtime-library/potential-errors-passing-crt-objects-across-dll-boundaries.md)。  
  
 我们进一步建议，你在编写代码时永远不依赖除 COM 接口或 POD 对象以外的特定对象布局。 如果确实要编写此类代码，则必须在升级后确保其正常运行。 有关详细信息，请参阅 [ABI 边界处的可移植性](../cpp/portability-at-abi-boundaries-modern-cpp.md)。  
  
 此外，对编译器符合性的不断改进有时会改变编译器理解现有源代码的方式。 发生这种情况时，可能会在生成过程中遇到新的或不同的错误，甚至以前生成且似乎运行正常的代码也可能出现行为差异。 虽然这些不是本文档中所讨论的重大更改，但可能需要更改源代码来解决这些问题。  
  
  
1.  [C 运行时 (CRT) 库的重大更改](#BK_CRT)  
  
2.  [标准 C++ 和 C++ 标准库的重大更改](#BK_STL)  
  
3.  [MFC 和 ATL 的重大更改](#BK_MFC)  
  
4.  [并发运行时重大更改](#BK_ConcRT)  
  
## <a name="VC_2015"></a>Visual C++ 2015 符合性更改  
  
###  <a name="BK_CRT"></a>C 运行时库 (CRT)  
  
#### <a name="general-changes"></a>常规更改  
  
-   **重构的二进制文件** CRT 库被重构为两个不同的二进制文件、一个通用 CRT (ucrtbase)（其中包含大多数标准功能）和一个 VC 运行时库 (vcruntime)（其中包含与编译器相关的功能，如异常处理和内部函数）。 如果你使用的是默认项目设置，则此更改不会对你产生影响，因为链接器将自动使用新的默认库。 如果将项目的“链接器”  属性“忽略所有默认库”  设置为“是”  ，或你使用的是命令行上的 /NODEFAULTLIB 链接器选项，则必须更新库的列表（位于“附加依赖项”  属性）以包括新的重构库。 将旧的 CRT 库（libcmt.lib、libcmtd.lib、msvcrt.lib、msvcrtd.lib）替换为等效的重构库。 对于两个中的每个重构库，都存在静态 (.lib) 和动态 (.dll) 版本，发行（无后缀）和调试版本（使用“d”后缀）。 动态版本具有与之链接的导入库。 两个重构库是通用的 CRT（特别是 ucrtbase.dll 或 .lib、ucrtbased.dll 或 .lib）和 VC 运行时库（libvcruntime.lib、vcruntime*version*.dll、libvcruntimed.lib 和 vcruntimed*version*.dll）。 *version* 在 Visual Studio 2015 和 Visual Studio 2017 中均为 140。 请参阅 [CRT 库的功能](../c-runtime-library/crt-library-features.md)。  
  
#### <a name="localeh"></a>\<locale.h>  
  
-   **localeconv** 启用[按线程区域设置](../parallel/multithreading-and-locales.md)后，在 locale.h 中声明的 [localeconv](../c-runtime-library/reference/localeconv.md) 函数现在可以正常工作。 在早期版本的库中，此函数将返回全局区域设置（而不是线程的区域设置）的 lconv 数据。  
  
     如果使用每个线程区域设置，应该检查 localeconv 的使用以查看你的代码是否假定返回的 lconv 数据代表全局区域设置，并相应地对其进行修改。  
  
#### <a name="mathh"></a>\<math.h>  
  
-   **数学库函数的 C++ 重载** 在早期版本中，\<math.h> 定义数学库函数的部分（非全部） C++ 重载。 \<cmath> 定义了其余的重载，因此为了获取所有重载，其中一个需要包括 \<cmath> 标头。 这就会导致只包括 \<math.h> 的代码中的函数重载解析出现问题。 现在，已从 \<math.h> 中删除了所有 C++ 重载，现在仅包含在 \<cmath> 中。  
  
     若要解决错误，请包括 <cmath>cmath> 以获取已从 \<math.h> 中删除的函数的声明。 下表列出了移动的函数。  
  
     移动的函数：  
  
    1.  双精度型 abs(double) 和浮点型 abs(float)  
  
    2.  双精度型 pow(double, int)、浮点型 pow(float, float)、浮点型 pow(float, int)、长双精度型 pow(long double, long double)、长双精度型 pow(long double, int)  
  
    3.  浮点型和长双精度型版本的浮点函数 acos、acosh、asin、asinh、atan、atanh、atan2、cbrt、ceil、copysign、cos、cosh、erf、erfc、exp、exp2、expm1、fabs、fdim、floor、fma、fmax、fmin、fmod、frexp、hypot、ilogb、ldexp、lgamma、llrint、llround、log、log10、log1p、log2、lrint、lround、modf、nearbyint、nextafter、nexttoward、remainder、remquo、rint、round、scalbln、scalbn、sin、sinh、sqrt、tan、tanh、tgamma、trunc  
  
     如果你的代码使用具有仅包含 math.h 标头的浮点型的 abs，则浮点版本将不再可用，因此调用（即使具有浮点参数）现在已解析为 abs(int)。 这将产生错误：  
  
    ```Output  
    warning C4244: 'argument' : conversion from 'float' to 'int', possible loss of data  
    ```  
  
     此警告的解决方法是将对 abs 的调用替换为浮点版本的 abs（例如双精度型自变量的 fabs 或浮点型自变量的 fabsf）或包含 cmath 标头并继续使用 abs。  
  
-   **浮点符合性** 对数学库所做的许多更改都用以使特例输入（如 NaN 和无穷大）更符合 IEEE-754 和 C11 附录 F 规范。 例如，在早期版本的库中通常被视为错误的 quiet NaN 输入已不再被视为错误。 请参阅 [IEEE 754 标准](http://grouper.ieee.org/groups/754) 和 [C11 标准](http://www.iso-9899.info/wiki/The_Standard)的附录 F。  
  
     这些更改不会导致编译时错误，但可能会根据标准使程序以不同的方式更准确地运行。  
  
-   **FLT_ROUNDS** 在 Visual Studio 2013 中，FLT_ROUNDS 宏扩展为常量表达式，这是错误的，因为舍入模式在运行时是可配置的，例如，通过调用 fesetround。 FLT_ROUNDS 宏现在是动态的，并正确反映当前的舍入模式。  
  
#### <a name="new-and-newh"></a>\<new> 和 \<new.h>  
  
-   **new 和 delete** In previous versions of the library, the implementation-defined operator new 和 delete functions were exported from the runtime library DLL (for example, msvcr120.dll). 这些运算符函数现在始终以静态方式链接到二进制文件，即使是使用运行时库 DLL 时也是如此。  
  
     这对于本机或混合代码 (/clr) 而言不是一项重大更改，但是对于编译为 [/clr:pure](../build/reference/clr-common-language-runtime-compilation.md) 的代码而言，这可能会导致代码无法进行编译。 如果将代码编译为 /clr:pure，可能需要添加 #include \<new> 或 #include \<new.h> 以解决由于此更改导致的生成错误。 请注意，/clr:pure 在 Visual Studio 2015 中已被弃用，并且可能在未来版本中删除。  
  
#### <a name="processh"></a>\<process.h>  
  
-   **_beginthread 和 _beginthreadex** 现在，[_beginthread](../c-runtime-library/reference/beginthread-beginthreadex.md) 和 [_beginthreadex](../c-runtime-library/reference/beginthread-beginthreadex.md) 函数保存对模块的引用，在该模块中，已针对线程持续时间定义了线程过程。 这有助于确保线程在完成运行之后才卸载模块。  
  
#### <a name="stdargh"></a>\<stdarg.h>  
  
-   **va_start 和引用类型** 编译 C++ 代码时，[va_start](../c-runtime-library/reference/va-arg-va-copy-va-end-va-start.md) 现在会在编译时验证传递给它的参数是否为引用类型。 C++ 标准禁止引用类型的参数。  
  
#### <a name="stdioh-and-conioh"></a>\<stdio.h> 和 \<conio.h>  
  
-   **Printf 和 scanf 系列函数现在采用内联方式进行定义。** 所有 printf 和 scanf 函数的定义已以内联方式移动到 \<stdio.h>、\<conio.h> 和其他 CRT 标头中。 这项重大更改会导致本地声明这些函数（没有适当的 CRT 标头）的任何程序发生链接器错误（LNK2019、无法解析的外部符号）。 如果可能，应更新代码以包括 CRT 标头（即，添加 #include \<stdio.h>）和内联函数，但如果不想修改代码以包括这些标头文件，则可以选择将其他库添加到链接器输入 (legacy_stdio_definitions.lib)。  
  
     若要将此库添加到 IDE 中的链接器输入，请打开项目节点的上下文菜单，选择“属性” ，然后在“项目属性”  对话框中选择“链接器” ，编辑“链接器输入”  以将 legacy_stdio_definitions.lib 添加到用分号隔开的列表。  
  
     如果项目链接的静态库是使用早于 2015 的 Visual C++ 版本编译的，则链接器可能会报告无法解析的外部符号。 这些错误可能会引用 _imp\_* 窗体中某些 stdio 函数的 _iob、_iob_func 或相关导入的内部 stdio 定义。 Microsoft 建议在升级项目时使用最新版本的 Visual C++ 编译器和库编译所有静态库。 如果库是第三方库并且第三方库的源不可用，则应请求来自第三方更新后的二进制文件，或者将你对此库的用法封装到单独的 DLL（使用旧版 Visual C++ 或库编译的）。  
  
    > [!WARNING]
    >  如果你链接的是 Windows SDK 8.1 或更早版本，可能会遇到这些无法解析的外部符号错误。 在这种情况下，应通过将 legacy_stdio_definitions.lib 添加到链接器输入（如上文所述）来解决该错误。  
  
     若要解决无法解析的符号错误，可以尝试使用 [dumpbin.exe](../build/reference/dumpbin-reference.md) 来检查二进制文件中定义的符号。 请尝试使用下面的命令行来查看在库中定义的符号。  
  
    ```cpp  
    dumpbin.exe /LINKERMEMBER somelibrary.lib  
    ```  
  
-    **get 和 _getws**  已删除 [get](../c-runtime-library/gets-getws.md) 和 [ _getws](../c-runtime-library/gets-getws.md) 函数。 已从 C11 中的 C 标准库删除 gets 函数，因为其不能安全使用。 _getws 函数是与 gets 等效（但可用于宽字符串）的 Microsoft 扩展。 作为这些函数的替代，请考虑使用 [fgets](../c-runtime-library/reference/fgets-fgetws.md)、[fgetws](../c-runtime-library/reference/fgets-fgetws.md)、[gets_s](../c-runtime-library/reference/gets-s-getws-s.md) 和 [_getws_s](../c-runtime-library/reference/gets-s-getws-s.md)。  
  
-   **_cgets 和 _cgetws** 已删除 [_cgets](../c-runtime-library/cgets-cgetws.md) 和 [_cgetws](../c-runtime-library/cgets-cgetws.md) 函数。 作为这些函数替代，请考虑使用 [_cgets_s](../c-runtime-library/reference/cgets-s-cgetws-s.md) 和 [_cgetws_s](../c-runtime-library/reference/cgets-s-cgetws-s.md)。  
  
-   **无穷大和 NaN 格式设置** 在早期版本中，可以使用 Visual C++ 特定的 sentinel 字符串集进行无穷大和 NaN 格式设置。  
  
    -   无穷大：1.#INF  
  
    -   静默 NaN：1.#QNAN  
  
    -   信号 NaN：1.#SNAN  
  
    -   无穷大 NaN：1.#IND  
  
     这些字符串的任何一种都可能已采用符号作为前缀并且格式设置也可能略有不同，具体取决于字段宽度和精度（有时会起到不寻常的作用，例如，printf("%.2f\n", INFINITY) 可以打印 1.#J，因为 #INF 会“四舍五入”为 2 位数的精度）。 C99 引入了有关如何设置无穷大和 NaN 格式的新要求。 现在，Visual C++ 实现符合这些要求。 新字符串如下所示：  
  
    -   无穷大：inf  
  
    -   静默 NaN：nan  
  
    -   信号 NaN：nan(snan)  
  
    -   不定 NaN：nan(ind)  
  
     可能以符号作为其中任何一种字符串的前缀。 如果使用了大写格式说明符（%F 而不是 %f），则字符串将按要求以大写字母形式（INF 而不是 inf）打印。  
  
     已修改 [scanf](../c-runtime-library/reference/scanf-scanf-l-wscanf-wscanf-l.md) 函数以便分析这些新的字符串，因此这些字符串会通过 printf 和 scanf 往返。  
  
-   **浮点格式设置和分析** 引入了新浮点格式设置和分析算法以提高正确性。 此更改会影响 [printf](../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md) 和 [scanf](../c-runtime-library/reference/scanf-scanf-l-wscanf-wscanf-l.md) 系列函数，以及像 [strtod](../c-runtime-library/reference/strtod-strtod-l-wcstod-wcstod-l.md) 这样的函数。  
  
     旧的格式设置算法将仅生成有限数量的数字，然后将用零填充其余的小数位数。 这是通常足以生成将往返回原始浮点值的字符串，但如果你想要精确值（或最接近十进制的表示），则不够完美。 新的格式设置算法会尽可能多地生成数字来表示值（或填充指定的精度）。 作为改进的一个例子；打印两个中指数较大的一个时，请考虑结果：  
  
    ```cpp  
    printf("%.0f\n", pow(2.0, 80))  
  
    ```  
  
    ```Output  
        Old:  1208925819614629200000000    New:  1208925819614629174706176  
    ```  
  
     旧版本分析算法考虑的输入字符串中有效位数仅达 17，并将丢弃其余数位。 这不足以生成由字符串表示的近似值，结果通常是非常接近正确舍入的结果。 新版本的实现会考虑所有存在的数字，并生成所有输入（长度多达 768 位）的正确舍入的结果。 此外，这些函数现在遵循舍入模式（可通过 fesetround 控制）。  这可能是重大的行为更改，因为这些函数可能会输出不同的结果。 新版本的结果始终比旧版本的结果更准确。  
  
-   **十六进制和无穷大/NaN 浮点分析** 浮点分析算法现在将分析十六进制浮点字符串（例如，那些由 %a 和 %A printf 格式说明符生成的字符串）和由 printf 函数生成的所有无穷大和 NaN 字符串（如上文所述）。  
  
-   **%A 和 %a 零填充** %a 和 %A 格式说明符将浮点数转化为十六进制的尾数和二进制指数。 在早期版本中，printf 函数可能会错误地用零填充字符串。 例如，printf ("%07.0a\n", 1.0) 可能会打印 00x1p+0，而它本应打印 0x01p+0。 已解决此问题。  
  
-   **%A 和 %a 精度** 在早期版本的库中，%A 和 %a 格式说明符的默认精度是 6。 为了符合 C 标准，现在默认精度为 13。  
  
     这是使用带 %A 或 %a 的格式字符串的任一函数输出中的运行时行为更改。 在旧版本行为中，使用 %A 说明符的输出可能是“1.1A2B3Cp+111”。 现在相同值的输出是“1.1A2B3C4D5E6F7p+111”。 若要获取旧版本行为，则可以指定精度（例如，%.6A）。 请参阅[精度规范](../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md#precision)。  
  
-   **%F 说明符** 现在支持 %F 格式/转换说明符。 它在功能上等效于 %f 格式说明符，但使用大写字母形式进行格式设置的无穷大和 Nan 除外。  
  
     在早期版本中，实现过去通常将 F 和 N 分析为长度修饰符。 此行为追溯到分段地址空间的时代：这些长度修饰符分别用于指示或近或远的指针（如 %Fp 或 %Ns 中所示）。 此行为已被删除。 如果遇到 %F，现在则将其视为 %F 格式说明符；如果遇到 %N，现在则将其视为无效的参数。  
  
-   **指数格式设置** %e 和 %E 格式说明符将浮点数转化为十进制的尾数和指数。 %g 和 %G 格式说明符在某些情况下也以此形式设置格式位数。 在早期版本中，CRT 会始终生成具有三个数字指数的字符串。 例如，printf ("%e\n", 1.0) 可能会打印 1.000000e+000。 这是错误的：根据 C 要求，如果可使用一个或两个数字表示指数，则仅打印两个数字。  
  
     Visual Studio 2005 中添加了全局符合性切换：[_set_output_format](../c-runtime-library/set-output-format.md)。 程序可以调用参数为 _TWO_DIGIT_EXPONENT 的此函数，以启用符合标准的指数打印。 已将默认行为更改为符合标准的指数打印模式。  
  
-   **格式字符串验证** 在早期版本中，printf 和 scanf 函数以静默方式接受许多无效格式字符串，有时会起到不寻常的作用。 例如，%hlhlhld 将被视为 %d。 现在所有无效格式字符串都被视为无效的参数。  
  
-   **fopen 模式字符串验证**  
  
     在早期版本中，fopen 系列函数以静默方式接受某些无效的模式字符串（例如，r+b+）。 现在可检测无效的模式字符串并将其视为无效的参数。  
  
-   **_O_U8TEXT 模式**  
  
     [_setmode](../c-runtime-library/reference/setmode.md) 函数现在可以准确报告在 in_O_U8TEXT 模式中打开的流模式。 在早期版本的库中，它将报告正在 _O_WTEXT 中打开的此类流。  
  
     如果你的代码解释其中编码为 UTF-8 的流的 _O_WTEXT 模式，这则是一项重大更改。 如果你的应用程序不支持 UTF_8，请考虑为此越来越常见的编码添加支持。  
  
-   **snprintf 和 vsnprintf** 现在已实现 [snprintf](../c-runtime-library/reference/snprintf-snprintf-snprintf-l-snwprintf-snwprintf-l.md) 和 [vsnprintf](../c-runtime-library/reference/vsnprintf-vsnprintf-vsnprintf-l-vsnwprintf-vsnwprintf-l.md) 函数。 较旧的代码通常为宏版本的这些函数提供定义，因为它们未由 CRT 库实现，但在较新版本中则不再需要这些。 如果将 [snprintf](../c-runtime-library/reference/snprintf-snprintf-snprintf-l-snwprintf-snwprintf-l.md) 或 [vsnprintf](../c-runtime-library/reference/vsnprintf-vsnprintf-vsnprintf-l-vsnwprintf-vsnwprintf-l.md) 在包括 \<stdio.h> 之前定义为宏，则现在编译失败并显示错误，该错误指示定义了宏的位置。  
  
     通常情况下，解决此问题的方法是删除用户代码中 snprintf 或 vsnprintf 的任何声明。  
  
-   **tmpnam 生成可用文件名** 在早期版本中，tmpnam 和 tmpnam_s 函数在驱动器根目录（如 \sd3c）中生成文件名。 这些函数现在在临时目录中生成可用的文件名路径。  
  
-   **文件封装** 在早期版本中，FILE 类型在 \< stdio.h> 中完全定义，因此有可能用户代码可以访问 FILE 并修改其内部。 已对 stdio 库进行了更改以隐藏实现细节。 作为此操作的一部分，\<stdio.h> 中所定义的 FILE 现在是不透明类型且无法从 CRT 自身的外部访问其成员。  
  
-   **_outp 和 _inp** 已删除函数 [_outp](../c-runtime-library/outp-outpw-outpd.md)、[_outpw](../c-runtime-library/outp-outpw-outpd.md)、[_outpd](../c-runtime-library/outp-outpw-outpd.md)、[_inp](../c-runtime-library/inp-inpw-inpd.md)、[_inpw](../c-runtime-library/inp-inpw-inpd.md) 和 [_inpd](../c-runtime-library/inp-inpw-inpd.md)。  
  
#### <a name="stdlibh-malloch-and-sysstath"></a>\<stdlib.h>、\<malloc.h> 和 \<sys/stat.h>  
  
-   **strtof 和 wcstof** The strtof 和 wcstof functions failed to set errno to ERANGE when the value was not representable as a float. 已解决此问题。 （请注意此错误只特定于这两个函数；strtod、wcstod、strtold 和 wcstold 函数不受影响。）这是运行时重大更改。  
  
-   **对齐的分配函数** 在早期版本中，对齐的分配函数（_aligned_malloc、_aligned_offset_malloc 等）以静默方式接受带 0 的对齐方式的块的请求。 请求的对齐方式幂必须是 2（而不是零）。 已解决此问题，且请求的 0 的对齐方式现在被视为无效的参数。 这是运行时重大更改。  
  
-   **堆函数** 删除了 _heapadd、_heapset 和 _heapused 函数。 这些函数已不起作用，因为 CRT 已更新为使用 Windows 堆。  
  
-   **smallheap** 删除了 smalheap 链接选项。 请参阅[链接选项](../c-runtime-library/link-options.md)。  
  
#### <a name="stringh"></a>\<string.h>  
  
-   **wcstok** 更改了 wcstok 函数的签名，以便匹配 C 标准所要求的内容。 在早期版本的库中，此函数的签名为：  
  
    ```cpp  
    wchar_t* wcstok(wchar_t*, wchar_t const*)  
    ```  
  
     它使用内部的每个线程上下文来跟踪跨状态调用（就像为 strtok 所进行的操作一样）。 该函数现在具有签名 wchar_t* wcstok(wchar_t\*、wchar_t const\*、wchar_t\*\*)，并要求调用方将上下文作为第三个自变量传递给函数。  
  
     添加了新的 _wcstok 函数，并具有旧签名以便进行迁移。 编译 C++ 代码时，还存在具有旧签名的 wcstok 的内联重载。 已声明弃用此重载。 在 C 代码中，你可能会定义 _CRT_NON_CONFORMING_WCSTOK 以使 _wcstok 用于替换 wcstok。  
  
#### <a name="timeh"></a>\<time.h>  
  
-   **clock** 在早期版本中，已使用 Windows API[GetSystemTimeAsFileTime](http://msdn.microsoft.com/library/windows/desktop/ms724397.aspx) 实现了 [clock](../c-runtime-library/reference/clock.md) 函数。 使用此实现，clock 函数对系统时间比较敏感，因此不一定是单一的。 已根据 [QueryPerformanceCounter](https://msdn.microsoft.com/library/windows/desktop/ms644904.aspx) 重新实现了 clock 函数，现在它是单一的。  
  
-   **fstat 和 _utime** 在早期版本中，[_stat](../c-runtime-library/reference/stat-functions.md)、[fstat](../c-runtime-library/reference/fstat-fstat32-fstat64-fstati64-fstat32i64-fstat64i32.md) 和 [_utime](../c-runtime-library/reference/utime-utime32-utime64-wutime-wutime32-wutime64.md) 函数对夏时制的处理方式不正确。 在 Visual Studio 2013 之前的版本中，所有这些函数错误调整标准时时间，就像处于夏时制时间内一样。  
  
     在 Visual Studio 2013 中，解决了 _stat 系列函数中的此问题，但未解决 fstat 和 _utime 系列函数中的类似问题。 这就导致了由于问题函数之间的不一致引起的问题。 现在已修复 fstat 和 _utime 系列函数，因此所有这些函数现在可正确且一致地处理夏时制。  
  
-   **asctime** 在早期版本中，[asctime](../c-runtime-library/reference/asctime-wasctime.md) 函数会以前导零填充单位数的日期（例如：Fri Jun 06 08:00:00 2014）。 规范要求此类日期应以前导空格填充，例如 Fri Jun  6 08:00:00 2014。 已解决此问题。  
  
-   **strftime 和 wcsftime** The strftime 和 wcsftime functions now support the %C, %D, %e, %F, %g, %G, %h, %n, %r, %R, %t, %T, %u, and %V format specifiers. 此外，分析但忽略了 E 和 O 修饰符。  
  
     指定 %c 格式说明符生成当前区域设置的“相应的日期和时间表示形式”。 在 C 区域设置中，要求这种表示形式与 %a %b %e %T %Y 相同。 这与 asctime 生成的形式相同。 在早期版本中，使用 MM/DD/YY HH:MM:SS 表示形式，%c 格式说明符设置的时间格式不正确。 已解决此问题。  
  
-   **timespec 和 TIME_UTC** \< time.h> 标头现在按照 C11 标准定义 timespec 类型和 timespec_get 函数。 此外，现在可定义与 timespec_get 函数连用的 TIME_UTC 宏。 这对于在任一这些方面具有冲突定义的代码而言，是一项重大更改。  
  
-   **CLOCKS_PER_SEC** 现在，CLOCKS_PER_SEC 宏根据 C 语言要求扩展为整数类型 clock_t。  
  
####  <a name="BK_STL"></a>C++ 标准库  
 为了实现新的优化和调试检查，C++ 标准库的 Visual Studio 实现特意破坏了连续两个版本之间的二进制兼容性。 因此，在使用 C++ 标准库时，使用不同版本编译的对象文件和静态库不能混合在同一二进制文件（EXE 或 DLL）中，并且不能在使用不同版本编译的二进制文件之间传递 C++ 标准库对象。 这样混合会发出关于 _MSC_VER 不匹配的链接器错误。 （_MSC_VER 是包含编译器主版本的宏，例如，Visual Studio 2013 的 1800。）此检查无法检测 DLL 混合，也无法检测涉及 Visual C++ 2008 或早期版本的混合。  
  
-   **C++ 标准库包含文件** 对 C++ 标准库标头中的包含结构进行了一些更改。 允许 C++ 标准库标头以未指定的方式相互包含。 一般情况下，编写代码应根据 C++ 标准，谨慎包括需要的所有标头，而不是依赖于哪些 C++ 标准库标头包含哪些其他 C++ 标准库标头。 这使得代码可跨版本和平台进行移植。 至少更改 Visual Studio 2015 的两个标头才会影响用户代码。 首先，\<string> 不再包括 \<iterator>。 第二，\<tuple> 现在用于声明 std::array 但不包括所有 \<array>，这可能中断代码通过以下代码构造的组合：代码具有名为“array”的变量、你具有 using 指令“using namespace std;”，和你包括了含有 \<tuple> 的 C++ 标准库标头（如 \<functional>），其现在用于声明 std::array。  
  
-   **steady_clock** 已更改 [steady_clock](../standard-library/steady-clock-struct.md) 的 \<chrono> 实现，以便满足 C++ 标准对稳定性和单一性的需求。 steady_clock 现在以 [QueryPerformanceCounter](https://msdn.microsoft.com/library/windows/desktop/ms644904.aspx) 为基础，而 high_resolution_clock 现在是 steady_clock 的 typedef。 因此，在 Visual C++ 中，steady_clock::time_point 现在是 chrono::time_point<steady_clock> 的 typedef；但是，其他实现不一定是这种情况。  
  
-   **分配器和 const** 现在，我们要求分配器进行相等/不等比较，以接受两端上的 const 参数。  如果你的分配器如下定义这些运算符：  
  
    ```cpp  
    bool operator==(const MyAlloc& other)  
    ```  
  
     你应更新这些以将它们声明为 const 成员。  
  
    ```cpp  
    bool operator==(const MyAlloc& other) const  
    ```  
  
-   **const 元素** C++ 标准始终禁止 const 元素（如 vector\<const T> 或 set\<const T>）的容器。 Visual C++ 2013 及更早版本接受此类容器。 在当前版本中，此类容器无法编译。  
  
-   **std::allocator::deallocate** 在 Visual C++ 2013 和早期版本中，std::allocator::deallocate(p, n) 忽略了传入用于 n 的参数。  C + + 标准始终要求 n 应等于作为第一个参数传递给调用分配（返回 p）的值。 但是，在当前版本中将检查 n 的值。 在运行时，为 n 传递不同于标准要求的参数的代码可能会崩溃。  
  
-   hash_map 和 hash_set 非标准标头文件 hash_map 和 hash_set 在 Visual Studio 2015 中已被弃用，并且将在未来版本中删除。 请改用 unordered_map 和 unordered_set。  
  
-   **comparators 和 operator()** 关联容器（\<map> 系列）现在要求其比较运算符具有可调用 const 的函数调用运算符。 现在比较运算符类声明中的以下代码无法进行编译：  
  
    ```cpp  
    bool operator()(const X& a, const X& b)  
    ```  
  
     若要解决此错误，请将函数声明更改为：  
  
    ```cpp  
    bool operator()(const X& a, const X& b) const  
    ```  
  
-   **类型特征** The old names for 类型特征 from an earlier version of the C++ draft standard have been removed. C++11 中已对这些内容进行了更改，并且已更新为 Visual Studio 2015 中的 C++11 值。 下表显示了旧名称和新名称。  
  
    |旧名称|新名称|  
    |--------------|--------------|  
    |add_reference|add_lvalue_reference|  
    |has_default_constructor|is_default_constructible|  
    |has_copy_constructor|is_copy_constructible|  
    |has_move_constructor|is_move_constructible|  
    |has_nothrow_constructor|is_nothrow_default_constructible|  
    |has_nothrow_default_constructor|is_nothrow_default_constructible|  
    |has_nothrow_copy|is_nothrow_copy_constructible|  
    |has_nothrow_copy_constructor|is_nothrow_copy_constructible|  
    |has_nothrow_move_constructor|is_nothrow_move_constructible|  
    |has_nothrow_assign|is_nothrow_copy_assignable|  
    |has_nothrow_copy_assign|is_nothrow_copy_assignable|  
    |has_nothrow_move_assign|is_nothrow_move_assignable|  
    |has_trivial_constructor|is_trivially_default_constructible|  
    |has_trivial_default_constructor|is_trivially_default_constructible|  
    |has_trivial_copy|is_trivially_copy_constructible|  
    |has_trivial_move_constructor|is_trivially_move_constructible|  
    |has_trivial_assign|is_trivially_copy_assignable|  
    |has_trivial_move_assign|is_trivially_move_assignable|  
    |has_trivial_destructor|is_trivially_destructible|  
  
-   **launch::any 和 launch::sync 策略** The nonstandard launch::any 和 launch::sync 策略 were removed. 对于 launch::any，请使用 launch:async | launch:deferred。 对于 launch::sync，请使用 launch::deferred。 请参阅 [launch 枚举](../standard-library/future-enums.md#launch)。  
  
####  <a name="BK_MFC"></a>MFC 和 ATL  
  
-   **Microsoft 基础类 (MFC)** 由于其尺寸大不再包含在 Visual Studio 的“典型”安装中。 若要安装 MFC，请在 Visual Studio 2015 安装程序中选择自定义安装选项。 如果你已安装 Visual Studio 2015，可以通过重新运行 Visual Studio 安装程序，选择自定义安装选项，并选择 Microsoft 基础类来安装 MFC。 可从控制面板、程序和功能，或从安装媒体重新运行 Visual Studio 安装程序。  
  
     Visual C++ 可再发行组件包仍包含此库。  
  
####  <a name="BK_ConcRT"></a>并发运行时  
  
-   **与 concurrency::Context::Yield 冲突的 Windows.h 中的 Yield 宏** 并发运行时之前使用 #undef 来取消定义 Yield 宏，以避免 Windows.h h 中定义的 Yield 宏和 concurrency::Context::Yield 函数之间的冲突。 已删除此 #undef，并添加了新的非冲突等效 API 调用 [concurrency::Context::YieldExecution](../parallel/concrt/reference/context-class.md#yieldexecution)。 若要解决与 Yield 的冲突，可以改为更新代码以调用 YieldExecution 函数，或在调用站点用括号将 Yield 函数名括起来，如下例所示：  
  
    ```cpp  
    (concurrency::Context::Yield)();  
    ```  
  
## <a name="compiler-conformance-improvements-in-visual-c-2015"></a>Visual C++ 2015 中的编译器符合性改进  
 从早期版本升级代码时，可能会遇到由 Visual C++ 2015 中符合性改进引起的编译器错误。 这些改进不会破坏 Visual C++ 早期版本的二进制文件兼容性，但可能会产生之前未出现过的编译器错误。 有关详细信息，请参阅 [Visual C++ 新增功能（2003 - 2015）](../porting/visual-cpp-what-s-new-2003-through-2015.md)。  
  
 在 Visual C++ 2015 中，对编译器符合性的持续改进有时会改变编译器理解现有源代码的方式。 发生这种情况时，可能会在生成过程中遇到新的或不同的错误，甚至以前生成且似乎运行正常的代码也可能出现行为差异。  
  
 幸运的是，这些差异对大部分源代码没有影响或影响极小，而且需要更改源代码或进行其他更改以解决这些差异时，修补程序通常小型且简单。 我们列出了以前可接受、现在可能需要更改的许多源代码示例（之前）及其修补程序（之后）。  
  
 虽然这些差异可能会影响源代码或其他生成项目，但其不会影响 Visual C++ 版本更新之间的二进制文件兼容性。 重大更改是严重性较高的更改，可能会影响二进制文件兼容性，但此类二进制文件兼容性中断问题仅发生在 Visual C++ 的主版本之间。 例如，在 Visual C ++ 2013 和 Visual C ++ 2015 之间。 有关 Visual C++ 2013 和 Visual C++ 2015 之间的重大更改的详细信息，请参阅 [Visual C++ 2015 符合性更改](#VC_2015)。  
  
-   [Visual C++ 2015 中的符合性改进](#VS_RTM)  
  
-   [更新 1 中的符合性改进](#VS_Update1)  
  
-   [更新 2 中的符合性改进](#VS_Update2)  
  
-   [更新 3 中的符合性改进](#VS_Update3)  
  
###  <a name="VS_RTM"></a>Visual C++ 2015 中的符合性改进  
  
-   /Zc:forScope- 选项  
  
     编译器选项 **/Zc:forScope-** 已弃用，并且将在将来版本中删除。  
  
    ```cpp  
    Command line warning  D9035: option 'Zc:forScope-' has been deprecated and will be removed in a future release  
    ```  
  
     以前会经常用到此选项，以便允许非标准代码在点的位置之后使用循环变量，根据标准规范，这些变量本应该在范围之外。 仅当使用 /Za 选项进行编译时才需要，因为没有 /Za，将始终允许在循环结束后使用 for 循环变量。 如果你不关心标准符合性（例如，如果你的代码不是为了移植到其他编译器），你可以关闭 /Za 选项（或将“禁用语言扩展”属性设置为“否”）。 如果你确实关心编写可移植且符合标准的代码，则应重写代码，以便通过将此类变量的声明移到循环以外的点使其符合标准。  
  
    ```cpp  
    // C2065 expected  
    int main() {  
        // Uncomment the following line to resolve.  
        // int i;  
        for (int i = 0; i < 1; i++);  
        i = 20;   // i has already gone out of scope under /Za  
    }  
  
    ```  
  
-   **/Zg 编译器选项**  
  
     /Zg 编译器选项（生成函数原型）不再可用。 此此编译器选项已被弃用。  
  
-   你无法再使用 mstest.exe 从命令行运行 C++/CLI 单元测试。 请改用 vstest.console.exe。 请参阅 [VSTest.Console.exe 命令行选项](/devops-test-docs/test/vstest-console-exe-command-line-options)。  
  
-   **可变关键字**  
  
     在之前其正确编译的位置，不再允许存在 `mutable` 存储类说明符。 现在，编译器报告错误 C2071（非法存储类）。 根据标准，可变说明符仅可应用于类数据成员的名称，不能应用于声明为 const 或 static 的名称，也不能应用于引用成员。  
  
     例如，考虑以下代码：  
  
    ```cpp  
    struct S   
    {  
        mutable int &r;  
    };  
  
    ```  
  
     早期版本的 Visual C++ 编译器接受此代码，但现在编译器则报告以下错误：  
  
    ```Output  
    error C2071: 'S::r': illegal storage class  
    ```  
  
     若要修复此错误，只需删除冗余的可变关键字。  
  
-   **char_16_t 和 char32_t**  
  
     你不能再使用 `char16_t` 或 `char32_t` 作为 typedef 中的别名，因为这些类型现在被视为内置。 用户和库作者通常会将 char16_t 和 char32_t 分别定义为 uint16_t 和 uint32_t 的别名。  
  
    ```cpp  
    #include <cstdint>  
  
    typedef uint16_t char16_t; //C2628  
    typedef uint32_t char32_t; //C2628  
  
    int main(int argc, char* argv[])  
    {  
        uint16_t x = 1; uint32_t y = 2;  
        char16_t a = x;  
        char32_t b = y;  
        return 0;  
    }  
  
    ```  
  
     若要更新你的代码，请删除 typedef 声明，并重命名与这些名称发生冲突的任何其他标识符。  
  
-   **非类型模板参数**  
  
     现在会在提供显式模板参数时准确检查包含非类型模板参数的某些代码的类型符合性。 例如，在早期版本的 Visual C++ 中正确编译的以下代码。  
  
    ```cpp  
    struct S1  
    {  
        void f(int);  
        void f(int, int);  
    };  
  
    struct S2  
    {  
        template <class C, void (C::*Function)(int) const> void f() {}  
    };  
  
    void f()  
    {  
        S2 s2;  
        s2.f<S1, &S1::f>();  
    }  
  
    ```  
  
     当前编译器可以准确报告错误，因为模板参数类型不匹配模板参数（该参数是指向 const 成员的指针，但函数为非 const）：  
  
    ```Output  
    error C2893: Failed to specialize function template 'void S2::f(void)'note: With the following template arguments:note: 'C=S1'note: 'Function=S1::f'  
    ```  
  
     若要在代码中修复此错误，请确保你使用的模板自变量类型匹配模板参数声明的类型。  
  
-   **__declspec(align)**  
  
     编译器不再接受函数上的 `__declspec(align)` 。 以前会始终忽略此项，但现在会产生编译器错误。  
  
    ```cpp  
    error C3323: 'alignas' and '__declspec(align)' are not allowed on function declarations  
    ```  
  
     若要解决此问题，请从函数声明中删除 `__declspec(align)` 。 因为它不起作用，将其删除不会更改任何内容。  
  
-   **异常处理**  
  
     有几个对异常处理的更改。 首先，异常对象必须可复制或可移动。 在 [!INCLUDE[cpp_dev12_long](../build/reference/includes/cpp_dev12_long_md.md)] 中编译的以下代码却不能在 [!INCLUDE[cpp_dev14_long](../porting/includes/cpp_dev14_long_md.md)] 中进行编译：  
  
    ```cpp  
    struct S  
    {  
    public:  
        S();  
    private:  
        S(const S &);  
    };  
  
    int main()  
    {  
        throw S(); // error  
    }  
  
    ```  
  
     问题在于，复制构造函数是私有的，因此对象无法像处理异常的标准过程那样进行复制。 当复制构造函数为声明的 `explicit`时，这同样适用。  
  
    ```cpp  
    struct S  
    {  
        S();  
        explicit S(const S &);  
    };  
  
    int main()  
    {  
        throw S(); // error  
    }  
  
    ```  
  
     若要更新你的代码，请确保异常对象的复制构造函数是公用的且未标记为 `explicit`。  
  
     通过值捕获异常还要求异常对象可复制。 在 [!INCLUDE[cpp_dev12_long](../build/reference/includes/cpp_dev12_long_md.md)] 中编译的以下代码却不能在 [!INCLUDE[cpp_dev14_long](../porting/includes/cpp_dev14_long_md.md)] 中进行编译：  
  
    ```cpp  
    struct B  
    {  
    public:  
        B();  
    private:  
        B(const B &);  
    };  
  
    struct D : public B {};  
  
    int main()  
    {  
        try  
        {  
        }  
        catch (D d) // error  
        {  
        }  
    }  
  
    ```  
  
     可以通过将 `catch` 的参数类型更改为引用来解决此问题。  
  
    ```cpp  
    catch (D& d)  
    {  
    }  
  
    ```  
  
-   **后跟宏的字符串文本**  
  
     编译器现在支持用户定义的文本。 因此，宏之前没有任何干预空格的字符串文本被视为用户定义的文本，这可能会产生错误或意外结果。 例如，在早期的编译器中，成功编译了以下代码：  
  
    ```cpp  
    #define _x "there"  
    char* func() {  
        return "hello"_x;  
    }  
    int main()  
    {  
        char * p = func();  
        return 0;  
    }  
  
    ```  
  
     编译器将此视为后跟宏的字符串文本“hello”，该宏是展开的“there”，然后两个字符串串联成一个。 在 [!INCLUDE[cpp_dev14_long](../porting/includes/cpp_dev14_long_md.md)] 中，编译器将此解释为用户定义的文字，但由于没有定义匹配的用户定义的 _x 文本，它将报告错误。  
  
    ```Output  
    error C3688: invalid literal suffix '_x'; literal operator or literal operator template 'operator ""_x' not found  
    note: Did you forget a space between the string literal and the prefix of the following string literal?  
    ```  
  
     若要解决此问题，请在字符串文本和宏之间添加一个空格。  
  
-   **相邻字符串文本**  
  
     与上文类似，由于字符串分析中的相关变化，没有任何空格的相邻字符串文本（或宽或窄的字符字符串文本）被视为 Visaul C++ 早期版本中的单个串联字符串。 在 [!INCLUDE[cpp_dev14_long](../porting/includes/cpp_dev14_long_md.md)] 中，现在必须在两个字符串之间添加空格。 例如，必须更改以下代码：  
  
    ```cpp  
    char * str = "abc""def";  
    ```  
  
     只需在两个字符串之间添加空间。  
  
    ```cpp  
    char * str = "abc" "def";  
    ```  
  
-   **placement new 和 placement delete**  
  
     对 delete 运算符做出更改以使其符合 C++14 标准。 标准更改的详细信息位于 [C++ 调整了大小的释放](http://isocpp.org/files/papers/n3778.html)。 这些更改将添加采用大小参数的全局 delete 运算符的形式。 重大更改为，如果你之前使用的是具有相同签名的运算符 delete（以与 placement new 运算符对应），你将收到编译器错误（C2956，在使用 placement new 的点位置出现，因为在代码中的该位置，编译器会尝试标识适当匹配的 delete 运算符）。  
  
     函数 `void operator delete(void *, size_t)` 是与 C++11 中的 placement new 函数“void \* operator new(size_t, size_t)”对应的 placement delete 运算符。 使用 C++14 调整了大小的释放，此 delete 函数现在是 *常用释放函数* （全局 delete 运算符）。 标准要求为，如果使用 placement new 查找相应的 delete 函数和常用释放函数，则程序会出现格式错误。  
  
     例如，假设你的代码同时定义了 placement new 和 placement delete：  
  
    ```cpp  
    void * operator new(std::size_t, std::size_t);  
    void operator delete(void*, std::size_t) noexcept;  
  
    ```  
  
     由于定义的 placement delete 运算符和新的全局调整大小的 delete 运算符之间的函数签名匹配，因此就会出现问题。 考虑是否可以使用任何 placement new 和 placement delete 运算符的其他类型（size_t 除外）。  请注意，size_t typedef 的类型取决于编译器；在 Visual C++ 中，它是一个无符号整型的 typedef。 较好的解决办法就是使用如下的枚举类型：  
  
    ```cpp  
    enum class my_type : size_t {};  
  
    ```  
  
     然后，更改你对 placement new 和 placement delete 的定义，以使用此类型作为第二个参数（而不是 size_t）。 你还需要更新对 placement new 的调用以传递新类型（例如，通过使用 `static_cast<my_type>` 从整数值转换）并更新 new 和 delete 的定义以强制转换回整数类型。 你无需为此使用枚举；具有 size_t 成员的类类型也将起作用。  
  
     你还可以将 placement new 全部消除作为备选解决方案。 如果你的代码使用 placement new 实现内存池，其中位置参数是分配或删除的对象的大小，则调整了大小的释放功能可能适合替换你自定义的内存池代码，且你可以去掉位置函数，仅使用自己两个参数的 delete 运算符（而不是位置函数）。  
  
     如果你不想立即更新代码，可以通过使用编译器选项 /Zc:sizedDealloc- 恢复到旧行为。 如果使用此选项，则不存在两个参数的 delete 函数，并且也不会导致与 placement delete 运算符发生冲突。  
  
-   **联合数据成员**  
  
     联合数据成员不再具有引用类型。 以下代码在 [!INCLUDE[cpp_dev12_long](../build/reference/includes/cpp_dev12_long_md.md)]中成功编译，但在 [!INCLUDE[cpp_dev14_long](../porting/includes/cpp_dev14_long_md.md)] 中产生错误。  
  
    ```cpp  
    union U1   
    {  
        const int i;  
    };  
    union U2  
    {  
        int & i;  
    };  
    union U3  
    {  
        struct { int & i; };  
    };  
  
    ```  
  
     前面的代码产生以下错误：  
  
    ```Output  
  
    test.cpp(67): error C2625: 'U2::i': illegal union member; type 'int &' is reference type  
    test.cpp(70): error C2625: 'U3::i': illegal union member; type 'int &' is reference type  
  
    ```  
  
     若要解决此问题，请将引用类型更改为指针或值。 更改指针类型需要对使用联合字段的代码进行更改。 将代码更改为值将更改存储在联合中的数据，这会影响其他字段，因为联合类型中的字段共享相同的内存。 根据值的大小，它还可能更改联合的大小。  
  
-   匿名联合现在更符合标准。 早期版本的编译器生成了匿名联合的显式构造函数和析构函数。 这些在 [!INCLUDE[cpp_dev14_long](../porting/includes/cpp_dev14_long_md.md)] 中已删除。  
  
    ```cpp  
    struct S   
    {  
        S();  
    };  
  
    union   
    {  
        struct   
        {  
            S s;  
        };  
    } u; // C2280  
  
    ```  
  
     前面的代码在 [!INCLUDE[cpp_dev14_long](../porting/includes/cpp_dev14_long_md.md)] 中生成以下错误：  
  
    ```cpp  
    error C2280: '<unnamed-type-u>::<unnamed-type-u>(void)': attempting to reference a deleted function  
    note: compiler has generated '<unnamed-type-u>::<unnamed-type-u>' here  
  
    ```  
  
     若要解决此问题，请提供你对构造函数和/或析构函数的定义。  
  
    ```cpp  
    struct S   
    {  
        // Provide a default constructor by adding an empty function body.  
        S() {}  
    };  
  
    union   
    {  
        struct   
        {  
            S s;  
        };  
    } u;  
  
    ```  
  
-   **具有匿名结构的联合**  
  
     为了符合标准，已对联合中的匿名结构的成员更改了运行时行为。 创建此类联合时，将不再隐式调用联合中的匿名结构成员的构造函数。 此外，联合超出范围时，不再隐式调用联合中的匿名结构成员的析构函数。 请考虑以下代码，其中联合 U 包含一个匿名结构，此匿名结构包含的成员是一个具有析构函数的命名结构 S。  
  
    ```cpp  
    #include <stdio.h>  
    struct S   
    {  
        S() { printf("Creating S\n"); }  
        ~S() { printf("Destroying S\n"); }  
    };  
    union U   
    {  
        struct {  
            S s;  
        };  
        U() {}  
        ~U() {}  
    };  
  
    void f()  
    {  
        U u;  
        // Destructor implicitly called here.  
    }  
  
    int main()  
    {  
        f();  
  
        char s[1024];  
        printf("Press any key.\n");  
        gets_s(s);  
        return 0;  
    }  
  
    ```  
  
     在 [!INCLUDE[cpp_dev12_long](../build/reference/includes/cpp_dev12_long_md.md)] 中，创建联合时会调用 S 的构造函数，清理函数 f 的堆栈时会调用 S 的析构函数。 但在 [!INCLUDE[cpp_dev14_long](../porting/includes/cpp_dev14_long_md.md)] 中，不会调用构造函数和析构函数。 编译器会对关于此行为的更改发出警告。  
  
    ```Output  
    warning C4587: 'U::s': behavior change: constructor is no longer implicitly calledwarning C4588: 'U::s': behavior change: destructor is no longer implicitly called  
    ```  
  
     若要还原原始行为，请赋予匿名结构一个名称。 无论编译器版本为何，非匿名结构的运行时行为都是相同的。  
  
    ```cpp  
    #include <stdio.h>  
  
    struct S   
    {  
        S() { printf("Creating S.\n"); }  
        ~S() { printf("Destroying S\n"); }  
    };  
    union U   
    {  
        struct   
        {  
            S s;  
        } namedStruct;  
        U() {}  
        ~U() {}  
    };  
  
    void f()  
    {  
        U u;  
    }  
  
    int main()  
    {  
        f();  
  
        char s[1024];  
        printf("Press any key.\n");  
        gets_s(s);  
        return 0;  
    }  
  
    ```  
  
     或者，尝试将构造函数和析构函数代码移到新的函数中，并从联合的构造函数和析构函数添加对这些函数的调用。  
  
    ```cpp  
    #include <stdio.h>  
  
    struct S   
    {  
        void Create() { printf("Creating S.\n"); }  
        void Destroy() { printf("Destroying S\n"); }  
    };  
    union U   
    {  
        struct   
        {  
            S s;  
        };  
        U() { s.Create(); }  
        ~U() { s.Destroy(); }  
    };  
  
    void f()  
    {  
        U u;  
    }  
  
    int main()  
    {  
        f();  
  
        char s[1024];  
        printf("Press any key.\n");  
        gets_s(s);  
        return 0;  
    }  
  
    ```  
  
-   **模板解析**  
  
     对模板的名称解析进行了更改。 在 C++ 中，考虑名称解析的候选对象时，可能会出现作为潜在匹配项考虑的一个或多个名称生成无效的模板实例化的情况。 这些无效的实例化通常不会导致编译器错误，这被称为 SFINAE（替换失败不是错误）原则。  
  
     现在，如果 SFINAE 要求编译器将类模板专用化进行实例化，则在此过程中发生的任何错误都是编译器错误。 在早期版本中，编译器会忽略此类错误。 例如，考虑以下代码：  
  
    ```cpp  
    #include <type_traits>  
  
    template< typename T>  
    struct S  
    {  
        S() = default;  
        S(const S&);  
        S(S& &);  
  
        template< typename U, typename = typename std::enable_if< std::is_base_of< T, U> ::value> ::type>  
        S(S< U> & &);  
    };  
  
    struct D;  
  
    void f1()  
    {  
        S< D> s1;  
        S< D> s2(s1);  
    }  
  
    struct B  
    {  
    };  
  
    struct D : public B  
    {  
    };  
  
    void f2()  
    {  
        S< D> s1;  
        S< D> s2(s1);  
    }  
  
    ```  
  
     如果使用当前编译器进行编译，将得到以下错误：  
  
    ```Output  
  
    type_traits(1110): error C2139: 'D': an undefined class is not allowed as an argument to compiler intrinsic type trait '__is_base_of'  
    ..\t331.cpp(14): note: see declaration of 'D'  
    ..\t331.cpp(10): note: see reference to class template instantiation 'std::is_base_of<T,U>' being compiled  
    with  
    [  
        T=D,  
        U=D  
    ]  
  
    ```  
  
     这是因为在第一次调用 is_base_of 时，尚未定义类“D”。  
  
     在这种情况下，解决方法是在定义类之前，不使用此类类型特征。 如果将 D 和 B 的定义移到代码文件的开头，错误将得到解决。 如果定义位于标头文件中，请检查标头文件的 include 语句的顺序，以确保在使用有问题的模板之前，对任何类定义进行了编译。  
  
-   **复制构造函数**  
  
     在 [!INCLUDE[vs_dev12](../atl-mfc-shared/includes/vs_dev12_md.md)] 和 Visual Studio 2015 中，如果该类具有用户定义的移动构造函数，但没有用户定义的复制构造函数，则编译器生成类的复制构造函数。 在 Dev14 中，此隐式生成的复制构造函数也标记为“= delete”。  

<!--From here to VS_Update1 added 04/21/2017-->

-   **声明为 extern "C" 的 main 现在需要有返回类型。**  

下面的代码现在生成错误 C4430。 
```cpp
extern "C" __cdecl main(){} // C4430
```
若要修复此错误，请添加返回类型：
```cpp
extern "C" int __cdecl main(){} // OK
```

 -   **不允许在成员初始值设定项中使用 typename**  

下面的代码现在生成错误 C2059：
 ```cpp
template<typename T>
struct S1 : public T::type
{
    S1() : typename T::type() // C2059
    {
    }
};

struct S2 {
    typedef S2 type;
};

S1<S2> s;
```
若要修复此错误，请从初始值设定项中删除 `typename`：
```cpp
S1() : T::type() // OK
...
```

-   **忽略显式专用化上的存储类。** 

在下面的代码中，忽略静态存储类说明符 
```cpp
template <typename T>
void myfunc(T h)
{
}

template<>
static void myfunc(double h) // static is ignored
{
}

```

-   **在类模板内的 static_assert 中使用的常量始终都会失败。**  

在下面的代码中，static_assert 始终都会失败：
```cpp
template <size_t some_value>
struct S1
{
    static_assert(false, "default not valid"); // always invoked

};

//other partial specializations here
```

若要解决此问题，请在结构中包装值：
```cpp
template <size_t some_value>
struct constant_false {
    static const bool value = false;
};

template <size_t some_value>
struct S1
{
    static_assert(constant_false<some_value>::value, "default not valid");
};

//other partial specializations here
```

-   **对前向声明强制执行规则。（仅适用于 C。）**  

下面的代码现在生成错误 C2065：
```cpp
struct token_s;
typedef int BOOL;
typedef int INT;



typedef int(*PFNTERM)(PTOKEN, BOOL, INT); // C2065: 'PTOKEN' : undeclared identifier
```

若要解决此问题，请添加合适的前向声明：

```cpp
struct token_s;
typedef int BOOL;
typedef int INT;

// forward declarations:
typedef struct token_s TOKEN; 
typedef TOKEN *PTOKEN;

typedef int(*PFNTERM)(PTOKEN, BOOL, INT);
```

-   **更一致地强制执行函数指针类型**  

下面的代码现在生成错误 C2197：

```cpp
typedef int(*F1)(int);
typedef int(*F2)(int, int);

void func(F1 f, int v1, int v2)
{
    f(v1, v2); // C2197
}
```

-   **对重载函数的调用不明确**  

下面的代码现在生成错误 C266："N::bind":对重载函数的调用不明确
```cpp 
template<typename R, typename T, typename T1, typename A1>
void bind(R(T::*)(T1), A1&&);

namespace N
{
    template <typename T, typename R, typename ... Tx>
    void bind(R(T::*)(Tx...), T* ptr);
}

using namespace N;

class Manager
{
public:
    void func(bool initializing);

    void mf()
    {
        bind(&Manager::func, this); //C2668
    }
};
```

若要修复此错误，可以将调用完全限定到绑定：N::bind(...)。不过，如果此更改是通过未声明的标识符 (C2065) 显现出来，修复此错误的适当做法是改用“using”声明。

此模式的发生通常与 Microsoft::WRL 命名空间中的 ComPtr 和其他类型有关。

-   **修复不正确的地址**  

下面的代码现在生成错误 C2440："=":无法从 "type *" 转换成 "type"。 若要修复此错误，请将 &(type) 更改为 (type)，并将 (&f()) 更改为 (f())。
 
```cpp
\\ C
typedef void (*type)(void);
 
void f(int i, type p);
void g(int);
void h(void)
{
    f(0, &(type)g);
}
 
\\ C++
typedef void(*type)(void);
 
type f();
 
void g(type);
 
void h()
{
    g(&f());
}

```

-   **字符串文本是常量数组**  

下面的代码现在生成错误 C2664："void f(void *":无法将自变量 1 从 "const char (*)[2]" 更改为 "void *"。
```cpp
void f(void *);
 
void h(void)
{
    f(&__FUNCTION__); 
    void *p = &"";
}
```

若要修复此错误，请将函数参数类型更改为“const void*”；否则，请按如下所示更改 h 的主体：

```cpp
void h(void)
{
    char name[] = __FUNCTION__;
    f( name); 
    void *p = &"";
}

```

-   **C++11 UDL 字符串**  

下面的代码现在生成错误 C3688：文本后缀 "L" 无效; 找不到文本运算符或文本运算符模板运算符 ""L


```cpp
#define MACRO

#define STRCAT(x, y) x\#\#y

int main(){

    auto *val1 = L"string"MACRO;
    auto *val2 = L"hello "L"world";

    std::cout << STRCAT(L"hi ", L"there");
}
```
若要修复此错误，请将代码更改为如下所示：

```cpp
#define MACRO

// Remove ##. Strings are automatically
// concatenated so they are not needed
#define STRCAT(x, y) x y

int main(){
    //Add space after closing quote
    auto *val1 = L"string" MACRO;
    auto *val2 = L"hello " L"world";

    std::cout << STRCAT(L"hi ", L"there");
}

```
在上面的示例中，不再将 `MACRO` 分析为两个标记（后跟宏的字符串）。  现在，将它分析为一个标记 UDL。  这同样适用于 L""L""，之前将其分析为 L"" 和 L""，现在分析为 L""L 和 ""。

为了符合标准，还引入了字符串串联规则；也就是说，L"a" "b" 等效于 L"ab"。 旧版 Visual Studio 不接受串联字符宽度不同的字符串。


-   **删除了 C++11 空字符**  

下面的代码现在生成错误 C2137：空字符常量

```cpp
bool check(wchar_t c){
    return c == L''; //implicit null character
}
```

若要修复此错误，请将代码更改为如下所示：

```cpp
bool check(wchar_t c){
    return c == L'\0';
}
```

-   **值无法捕获 MFC 异常，因为此类异常无法复制**  

MFC 应用程序中的以下代码现在生成错误 C2316："D":无法被捕获，因为析构函数和/或复制构造函数不可访问或已遭删除

```cpp
struct B {
public:
    B();
private:
    B(const B &);
};

struct D : public B {
};

int main()
{
    try
    {
    }
    catch (D) // C2316
    {
    }
}

```
若要修复此代码，可以将 catch 块更改为“catch (const D &)”，但更好的解决方案通常是使用 MFC TRY/CATCH 宏。

-   **alignof 现在是关键字**  

下面的代码现在生成错误 C2332："class":缺少标记名称。 若要修复此代码，必须重命名类；或者，如果类执行的工作与 alignof 相同，只需将类替换成新的关键字即可。
```cpp
class alignof{}
```

-   **constexpr 现在是关键字**  

下面的代码现在生成错误 C2059：语法错误: ")"。 若要修复此代码，必须重命名任何名为“constexpr”的函数或变量名称。 
```cpp
int constexpr() {return 1;}
```

-   **可移动类型不能为常量**  

当函数返回预期要移动的类型时，其返回类型不得为常量。

-   **已删除复制构造函数**  

下面的代码现在生成错误 C2280："S::S(S &&)":正在尝试引用已删除的函数。

```cpp
struct S{
    S(int, int);
    S(const S&) = delete;
    S(S&&) = delete;
};

S s2 = S(2, 3); //C2280
```
若要修复此错误，请对 S2 使用直接初始化：
```cpp
struct S{
    S(int, int);
    S(const S&) = delete;
    S(S&&) = delete;
};

S s2 = {2,3}; //OK
```

-   **仅在未捕获 lambda 时生成函数指针转换**  

下面的代码在 Visual Studio 2015 中生成错误 C2664。 

```cpp
void func(int(*)(int)) {}

int main() {

    func([=](int val) { return val; });
}
```
若要修复此错误，请从捕获列表中删除 `=`。

-   **涉及转换运算符的不明确调用**  

下面的代码现在生成错误 C2440：“类型转换”:无法从 "S2" 转换成 "S1"。

```cpp 
struct S1 {
    S1(int);
};

struct S2 {
    operator S1();
    operator int();
};

void f(S2 s2)
{

    (S1)s2;

}
```
若要修复此错误，请显式调用转换运算符：

```cpp
void f(S2 s2)
{
    //Explicitly call the conversion operator
    s2.operator S1();
    // Or
    S1((int)s2);
}

```

下面的代码现在生成错误 C2593："operator =" 不明确。

```cpp
struct S1 {};

struct S2 {
    operator S1&();
    operator S1() const;
};

void f(S1 *p, S2 s)
{
    *p = s;
}
```
若要修复此错误，请显式调用转换运算符：
```cpp
void f(S1 *p, S2 s)
{
       *p = s.operator S1&();
}
```

-   **修复非静态数据成员初始化 (NSDMI) 中的无效复制初始化**  

下面的代码现在生成错误 C2664："S1::S1(S1 &&)":无法将自变量 1 从 "bool" 转换成 "const S1 &"。
```cpp
struct S1 {
    explicit S1(bool);
};

struct S2 {
    S1 s2 = true; // error
};
```
若要修复此错误，请使用直接初始化：
```cpp
struct S2 {
S1 s1{true}; // OK
};
```

-   **访问 decltype 语句内部的构造函数**  

下面的代码现在生成错误 C2248："S::S":无法访问类 "S" 中声明的私有成员。
```cpp
class S {
    S();
public:
    int i;
};

class S2 {
    auto f() -> decltype(S().i);
};
```
若要修复此错误，请在 S 中为 S2 添加友元声明：
```cpp
class S {
    S();
    friend class S2; // Make S2 a friend
public:
    int i;
};
```

-   **lambda 的默认构造函数被隐式删除**  

下面的代码现在生成错误 C3497：无法构造 lambda 实例。
```cpp
void func(){
    auto lambda = [](){};    
 
    decltype(lambda) other;
}
```
若要修复此错误，请消除对要调用的默认构造函数的需求。 如果 lambda 未捕获任何内容，可以将其转换成函数指针。

-   **Lambda 中的赋值运算符已遭删除**  

下面的代码现在生成错误 C2280：

```cpp
#include <memory>
#include <type_traits>

template <typename T, typename D>
std::unique_ptr<T, typename std::remove_reference<D &&>::type> wrap_unique(T *p, D &&d);

void f(int i)
{
    auto encodedMsg = wrap_unique<unsigned char>(nullptr, [i](unsigned char *p) {
    });
    encodedMsg = std::move(encodedMsg);
}
```
若要修复此错误，请将 lambda 替换成 functor 类，或消除对赋值运算符的使用需求。

-   **尝试使用已删除的复制构造函数移动对象**  

下面的代码现在生成错误 C2280："moveable::moveable(const moveable &)":正在尝试引用已删除的函数
```cpp
struct moveable {

    moveable() = default;
    moveable(moveable&&) = default;
    moveable(const moveable&) = delete;
};

struct S {
    S(moveable && m) :
        m_m(m)//copy constructor deleted
    {}
    moveable m_m;
};

```
若要修复此错误，请改用 std::move：
```cpp
S(moveable && m) :
    m_m(std::move(m))
```
-   **局部类无法引用之后在同一函数中定义的其他局部类**  

下面的代码现在生成错误 C2079："s" 使用未定义的结构 "main::S2"
```cpp
int main()
{
    struct S2;
    struct S1 {
        void f() {
            S2 s;
        }
    };
    struct S2 {};
}
```
若要修复此错误，请提升 S2 的定义：
```cpp
int main()
{
    struct S2 { //moved up
    };
 
struct S1 {
    void f() {
        S2 s;
        }
    };
}
```

-   **无法在派生构造函数的主体中调用受保护的基构造函数。**  

下面的代码现在生成错误 C2248："S1::S1":无法访问类 "S1" 中声明的受保护成员
```cpp
struct S1 {
protected:
    S1();
};

struct S2 : public S1 {
    S2() {
        S1();
    }
};
```
若要修复此错误，请在 S2 中删除构造函数对 S1() 的调用；如有必要，将其置于其他函数中。

-   **{} 防止发生指针转换**  

下面的代码现在生成错误 C2439："S::p":无法初始化成员   
```cpp
struct S {
    S() : p({ 0 }) {}
    void *p;
};
```
若要修复此错误，请删除 0 两边的大括号；否则，改用 `nullptr`，如以下示例所示：
```cpp
struct S {
    S() : p(nullptr) {}
    void *p;
};
```

-   **使用括号的宏定义和用法不正确**  

下面的示例现在生成错误 C2008：";":宏定义出现异常
```cpp
#define A; //cause of error

struct S {
    A(); // error
};
```
若要解决此问题，请将最上面的代码行更改为 `#define A();`

下面的代码生成错误 C2059：语法错误: ")"
```cpp

//notice the space after 'A'
#define A () ;

struct S {
    A();
};
```
若要修复此代码，请删除 A 和 () 之间的空格。

下面的代码生成错误 C2091：函数返回函数。

```cpp

#define DECLARE void f()

struct S {
    DECLARE();
};
```
若要修复此错误，请删除 S 中 DECLARE 后的括号：`DECLARE;`。

下面的代码生成错误 C2062："int" 不是预期类型

```cpp
#define A (int)

struct S {
    A a;
};
```
若要解决此问题，请定义 A，如下所示：
```cpp
#define A int
```

-   **声明中的多余括号**  

下面的代码生成错误 C2062："int" 不是预期类型
```cpp

struct S {
    int i;
    (int)j;
};
```
若要修复此错误，请删除 `j` 中的括号。 如果为明确起见而需要使用括号，请使用 typedef。

-   **编译器生成的构造函数和 __declspec(novtable)**  

在 Visual Studio 2015 中，含有虚拟基类的抽象类的编译器生成的内联构造函数更有可能会公开与 __declspec(dllimport) 结合使用的 __declspec(novtable) 的不当使用。

-   **auto 要求在直接列表初始化中使用一个表达式** 下面的代码现在生成错误 C3518："testPositions":在直接列表初始化上下文中，"auto" 的类型只能通过一个初始值设定项表达式进行推断

```cpp
auto testPositions{
    std::tuple<int, int>{13, 33},
    std::tuple<int, int>{-23, -48},
    std::tuple<int, int>{38, -12},
    std::tuple<int, int>{-21, 17}
};
```
若要修复此错误，一种可取方法是按如下所示初始化 testPositions：

```cpp
std::tuple<int, int> testPositions[]{
    std::tuple<int, int>{13, 33},
    std::tuple<int, int>{-23, -48},
    std::tuple<int, int>{38, -12},
    std::tuple<int, int>{-21, 17}
};
```

-   **检查 is_convertible 的类型与类型指针**  

下面的代码现在导致静态断言失败。 

```cpp
struct B1 {
private:
    B1(const B1 &);
};
struct B2 : public B1 {};
struct D : public B2 {};

static_assert(std::is_convertible<D, B2>::value, "fail");
```
若要修复此错误，请将 static_assert 更改为比较 D 与 B2 指针：

```cpp
static_assert(std::is_convertible<D*, B2*>::value, "fail");
```

-   **declspec(novtable) 声明必须保持一致**  

declspec 声明必须跨所有库保持一致。 下面的代码现在生成单个定义规则 (ODR) 冲突：

```cpp

//a.cpp
class __declspec(dllexport)
    A {
public:
    A();
    A(const A&);
    virtual ~A();
private:
    int i;
};

A::A() {}
A::~A() {}
A::A(const A&) {}

//b.cpp
// compile with cl.exe /nologo /LD /EHsc /Osx b.cpp
#pragma comment(lib, "A")
class __declspec(dllimport) A
{
public: A();
         A(const A&);
         virtual ~A();
private:
    int i;
};

struct __declspec(novtable) __declspec(dllexport) B
    : virtual public A {
    virtual void f() = 0;
};

//c.cpp
#pragma comment(lib, "A")
#pragma comment(lib, "B")
class __declspec(dllimport) A
{
public:
    A();
    A(const A&);
    virtual ~A();
private:
    int i;
};
struct  /* __declspec(novtable) */ __declspec(dllimport) B // Error. B needs to be novtable here also.
    : virtual public A
{
    virtual void f() = 0;
};

struct C : virtual B
{
    virtual void f();
};

void C::f() {}
C c;
```


  
###  <a name="VS_Update1"></a>更新 1 中的符合性改进  
  
-   **私有虚拟基类和间接继承**  
  
     早期版本的编译器允许派生类调用 *间接派生*`private virtual` 基类的成员函数。 这种旧行为不正确，也不符合 C++ 标准。 编译器不再接受这种方式编写的代码，因此会发出编译器错误 C2280。  
  
    ```Output  
  
    error C2280: 'void *S3::__delDtor(unsigned int)': attempting to reference a deleted function  
  
    ```  
  
     示例（之前）  
  
    ```cpp  
    class base  
    {  
    protected:  
        base();  
        ~base();  
    };  
  
    class middle : private virtual base {}; class top : public virtual middle {};   
  
    void destroy(top *p)  
    {  
        delete p;  //  
    }  
  
    ```  
  
     示例（之后）  
  
    ```cpp  
    class base;  // as above  
  
    class middle : protected virtual base {};  
    class top : public virtual middle {};  
  
    void destroy(top *p)  
    {  
        delete p;  
    }  
  
    ```  
  
     - 或 -  
  
    ```cpp  
    class base;  // as above  
  
    class middle : private virtual base {};  
    class top : public virtual middle, private virtual bottom {};  
  
    void destroy(top *p)  
    {  
        delete p;  
    }  
  
    ```  
  
-   **重载的 new 运算符和 delete 运算符**  
  
     早期版本的编译器允许非成员 `operator new` 和非成员 `operator delete` 声明为静态，并在全局命名空间之外的命名空间中声明。  这种旧行为会引发风险，导致程序无法按按程序员的预期调用 `new` 或 `delete` 运算符实现，从而导致无提示的运行时行为错误。 编译器不再接受这种方式编写的代码，因此会发出编译器错误 C2323。  
  
    ```Output  
  
    error C2323: 'operator new': non-member operator new or delete functions may not be declared static or in a namespace other than the global namespace.  
  
    ```  
  
     示例（之前）  
  
    ```cpp  
    static inline void * __cdecl operator new(size_t cb, const std::nothrow_t&)  // error C2323  
  
    ```  
  
     示例（之后）  
  
    ```cpp  
    void * __cdecl operator new(size_t cb, const std::nothrow_t&)  // removed 'static inline'  
  
    ```  
  
     此外，尽管编译器不能进行具体诊断，但内联运算符 new 会被视为格式不正确。  
  
-   **对非类类型调用“operator *type*()”（用户定义的转换）**  
  
     早期版本的编译器允许以无提示忽略的方式对非类类型调用“operator *type*()”。 这种旧行为会导致无提示代码生成错误风险，从而导致不可预知的运行时行为。 编译器不再接受这种方式编写的代码，因此会发出编译器错误 C2228。  
  
    ```Output  
  
    error C2228: left of '.operator type' must have class/struct/union  
  
    ```  
  
     示例（之前）  
  
    ```cpp  
    typedef int index_t;  
    void bounds_check(index_t index);  
    void login(int column)  
    {  
        bounds_check(column.operator index_t());  // error C2228  
    }  
  
    ```  
  
     示例（之后）  
  
    ```cpp  
    typedef int index_t;  
    void bounds_check(index_t index);  
    void login(int column)  
    {  
        bounds_check(column);  // removed cast to 'index_t', 'index_t' is an alias of 'int'  
    }  
  
    ```  
  
-   **详细的类型说明符中的多余 typename**  
  
     早期版本的编译器允许详细的类型说明符中出现 `typename` ；用这种方式编写的代码在语义上不正确。 编译器不再接受这种方式编写的代码，因此会发出编译器错误 C3406。  
  
    ```Output  
    error C3406: 'typename' cannot be used in an elaborated type specifier  
    ```  
  
     示例（之前）  
  
    ```cpp  
    template <typename class T>  
    class container;  
  
    ```  
  
     示例（之后）  
  
    ```cpp  
    template <class T>  // alternatively, could be 'template <typename T>'; 'typename' is not elaborating a type specifier in this case  
    class container;  
  
    ```  
  
-   **初始值设定项列表中数组的类型推断**  
  
     早期版本的编译器不支持对初始值设定项列表中的数组进行类型推断。 编译器现在支持这种形式的类型推断，因此调用使用初始值设定项列表的函数模板现在可能会不明确，或者选择一个与以前版本的编译器不同的重载。 要解决这些问题，程序现在必须显式指定程序员所需的重载。  
  
     当这一新行为导致重载解决方法要考虑与以往候选一样好的其他候选时，调用变得不明确，编译器会发出编译器错误 C2668。  
  
    ```Output  
  
    error C2668: 'function' : ambiguous call to overloaded function.  
  
    ```  
  
     示例 1： 对重载函数的调用不明确（之前）  
  
    ```cpp  
    // In previous versions of the compiler, code written in this way would unambiguously call f(int, Args...)  
    template < typename... Args>  
    void f(int, Args...);  //  
  
    template < int N, typename... Args>  
    void f(const int(&)[N], Args...);  
  
    int main()  
    {  
        // The compiler now considers this call ambiguous, and issues a compiler error  
         f({ 3 });   error C2668 : 'f' ambiguous call to overloaded function  
    }  
  
    ```  
  
     示例 1： 对重载函数的调用不明确（之后）  
  
    ```cpp  
    template < typename... Args>  
    void f(int, Args...);  //  
  
    template < int N, typename... Args>  
    void f(const int(&)[N], Args...);  
  
    int main()  
    {  
        // To call f(int, Args...) when there is just one expression in the initializer list, remove the braces from it.  
        f(3);   
    }  
  
    ```  
  
     这一新行为会导致重载解决方法要考虑比以往候选更适合的其他候选时，调用将明确地解析为新候选，导致程序行为的更改可能与程序员的需要有所不同。  
  
     示例 2：重载解决方法的更改（之前）  
  
    ```cpp  
    // In previous versions of the compiler, code written in this way would unambiguously call f(S, Args...)  
    struct S  
    {  
        int i;  
        int j;  
    };  
  
    template < typename... Args>  
    void f(S, Args...);  
  
    template < int N, typename... Args>  
    void f(const int *&)[N], Args...);  
  
    int main()  
    {  
        // The compiler now resolves this call to f(const int (&)[N], Args...) instead  
         f({ 1, 2 });   
    }  
  
    ```  
  
     示例 2：重载解决方法的更改（之后）  
  
    ```cpp  
    struct S;  // as before  
  
    template < typename... Args>  
    void f(S, Args...);  
  
    template < int N, typename... Args>  
    void f(const int *&)[N], Args...);  
  
    int main()  
    {  
        // To call f(S, Args...), perform an explicit cast to S on the initializer list.  
        f(S{ 1, 2 });   
    }  
  
    ```  
  
-   **switch 语句警告的还原**  
  
     前一个版本的编译器删除了之前存在的与 `switch` 语句相关的警告；现在已还原所有这些警告。 编译器现在将发出还原的警告，并且现在会在包含有问题用例的行中发出与特定用例（包括默认情况下）相关的警告，而不是在 switch 语句的最后一行发出。 因此，现在发出这些警告的行与过去不同，按照需要使用 `#pragma warning(disable:####)` 可不再禁止显示以前禁止显示的警告。 要按照需要禁止显示这些警告，可能需要将 `#pragma warning(disable:####)` 指令移到第一个可能有问题的用例上面的行。 以下是还原的警告。  
  
    ```Output  
    warning C4060: switch statement contains no 'case' or 'default' labels  
    ```  
  
    ```Output  
  
    warning C4061: enumerator 'bit1' in switch of enum 'flags' is not explicitly handled by a case label  
  
    ```  
  
    ```Output  
  
    warning C4062: enumerator 'bit1' in switch of enum 'flags' is not handled  
  
    ```  
  
    ```Output  
  
    warning C4063: case 'bit32' is not a valid value for switch of enum 'flags'  
  
    ```  
  
    ```Output  
  
    warning C4064: switch of incomplete enum 'flags'  
  
    ```  
  
    ```Output  
    warning C4065: switch statement contains 'default' but no 'case' labels  
    ```  
  
    ```Output  
  
    warning C4808: case 'value' is not a valid value for switch condition of type 'bool'  
  
    ```  
  
    ```Output  
    Warning C4809: switch statement has redundant 'default' label; all possible 'case' labels are given  
    ```  
  
     C4063 示例（之前）  
  
    ```cpp  
    class settings  
    {  
    public:  
        enum flags  
        {  
            bit0 = 0x1,  
            bit1 = 0x2,  
            ...  
        };  
        ...  
    };  
  
    int main()  
    {  
        auto val = settings::bit1;  
  
        switch (val)  
        {  
        case settings::bit0:  
            break;  
  
        case settings::bit1:  
            break;  
  
             case settings::bit0 | settings::bit1:  // warning C4063  
                break;  
        }  
    };  
  
    ```  
  
     C4063 示例（之后）  
  
    ```cpp  
    class settings { ... };  // as above  
    int main()  
    {  
        // since C++11, use std::underlying_type to determine the underlying type of an enum  
        typedef std::underlying_type< settings::flags> ::type flags_t;   
  
            auto val = settings::bit1;  
  
        switch (static_cast< flags_t> (val))  
        {  
        case settings::bit0:  
            break;  
  
        case settings::bit1:  
            break;  
  
        case settings::bit0 | settings::bit1:  // ok  
            break;  
        }  
    };  
  
    ```  
  
     在其文档中提供了其他还原警告的示例。  
  
-   **#include：在路径名中使用父目录说明符“..”** （只影响 /Wall/WX）  
  
     早期版本的编译器没有检测到使用父目录说明符“..” （在  `#include` 指令的路径名中）。 以这种方式编写的代码通常用于包含因不正确使用项目相对路径而留在项目外的标头。 这一旧行为会引发风险，导致编译程序时包含了程序员不需要的源文件来，或这些相对路径不能移植到其他生成环境中。 编译器现在会检测以这种方式编写的代码并通知程序员，并发出可选编译器警告 C4464（如果已启用）。  
  
    ```Output  
    warning C4464: relative include path contains '..'  
    ```  
  
     示例（之前）  
  
    ```cpp  
    #include "..\headers\C4426.h"  // emits warning C4464  
  
    ```  
  
     示例（之后）  
  
    ```cpp  
    #include "C4426.h"  // add absolute path to 'headers\' to your project's include directories  
  
    ```  
  
     此外，虽然编译器并不会进行具体诊断，但建议不应将父目录说明符“..”用于指定项目的包含目录。  
  
-   **#pragma optimize() 超出标头文件的末尾** （只影响 /Wall/WX）  
  
     早期版本的编译器无法检测到对转义翻译单元中包含的标头文件的优化标志设置的更改。 编译器现在会检测以这种方式编写的代码并通知程序员，并在有问题的 `#include`的位置发出可选编译器警告 C4426（如果已启用）。 只有更改与编译器命令行参数设置的优化标志发生冲突时，才发出此警告。  
  
    ```Output  
    warning C4426: optimization flags changed after including header, may be due to #pragma optimize()  
    ```  
  
     示例（之前）  
  
    ```cpp  
    // C4426.h  
    #pragma optimize("g", off)  
    ...  
    // C4426.h ends  
  
    // C4426.cpp  
    #include "C4426.h"  // warning C4426  
  
    ```  
  
     示例（之后）  
  
    ```cpp  
    // C4426.h  
    #pragma optimize("g", off)  
                ...  
    #pragma optimize("", on)  // restores optimization flags set via command-line arguments  
    // C4426.h ends  
  
    // C4426.cpp  
    #include "C4426.h"  
  
    ```  
  
-   **#pragma warning(push)** 和 **#pragma warning(pop)** （只影响 /Wall/WX）  
  
     早期版本的编译器无法检测到不同源文件中与 `#pragma warning(pop)` 状态更改配对的 `#pragma warning(push)` 状态更改，这并不是我们所预期的。 这种旧行为会引发风险，导致程序编译时会启用一组程序员不希望出现的警告，可能会导致无提示的运行时行为错误。 编译器现在能够检测以这种方式编写的代码并通知程序员，并在匹配 `#pragma warning(pop)` 位置发出可选编译器警告 C5031（如果已启用）。 此警告包括引用相应 #pragma warning(push) 的位置的注释。  
  
    ```Output  
    warning C5031: #pragma warning(pop): likely mismatch, popping warning state pushed in different file  
    ```  
  
     示例（之前）  
  
    ```cpp  
    // C5031_part1.h  
    #pragma warning(push)  
    #pragma warning(disable:####)  
    ...  
    // C5031_part1.h ends without #pragma warning(pop)  
  
    // C5031_part2.h  
    ...  
    #pragma warning(pop)  // pops a warning state not pushed in this source file  
    ...  
    // C5031_part1.h ends  
  
    // C5031.cpp  
    #include "C5031_part1.h" // leaves #pragma warning(push) 'dangling'  
    ...  
    #include "C5031_part2.h" // matches 'dangling' #pragma warning(push), resulting in warning C5031  
    ...  
  
    ```  
  
     示例（之后）  
  
    ```cpp  
    // C5031_part1.h  
    #pragma warning(push)  
    #pragma warning(disable:####)  
    ...  
    #pragma warning(pop)  // pops the warning state pushed in this source file  
    // C5031_part1.h ends without #pragma warning(pop)  
  
    // C5031_part2.h  
    #pragma warning(push)  // pushes the warning state pushed in this source file  
    #pragma warning(disable:####)  
    ...  
    #pragma warning(pop)  
    // C5031_part1.h ends  
  
    // C5031.cpp  
    #include "C5031_part1.h" // #pragma warning state changes are self-contained and independent of other source files or their #include order.  
    ...  
    #include "C5031_part2.h"  
    ...  
  
    ```  
  
     虽然不常见，但是有时会故意以这种方式编写代码。 以这种方式编写的代码对于 `#include` 顺序的更改比较敏感；如果可能，我们建议源代码文件以自包含的方式管理警告状态。  
  
-   **#pragma warning(push) 不匹配** （只影响 /Wall/WX）  
  
     早期版本的编译器无法检测到翻译单元末尾出现的不匹配 `#pragma warning(push)` 状态更改。 编译器现在能够检测以这种方式编写的代码并通知程序员，并在不匹配的 #pragma warning(push) 位置发出可选编译器警告 C5032（如果已启用）。 只有翻译单元中没有任何编译错误时，才会发出此警告。  
  
    ```Output  
    warning C5032: detected #pragma warning(push) with no corresponding #pragma warning(pop)  
    ```  
  
     示例（之前）  
  
    ```cpp  
    // C5032.h  
    #pragma warning(push)  
    #pragma warning(disable:####)  
    ...  
    // C5032.h ends without #pragma warning(pop)  
  
    // C5032.cpp  
    #include "C5032.h"  
    ...  
    // C5032.cpp ends -- the translation unit is completed without #pragma warning(pop), resulting in warning C5032 on line 1 of C5032.h  
  
    ```  
  
     示例（之后）  
  
    ```cpp  
    // C5032.h  
    #pragma warning(push)  
    #pragma warning(disable:####)  
    ...  
    #pragma warning(pop) // matches #pragma warning (push) on line 1  
    // C5032.h ends  
  
    // C5032.cpp  
    #include "C5032.h"  
    ...  
    // C5032.cpp ends -- the translation unit is completed without unmatched #pragma warning(push)  
  
    ```  
  
-   **#pragma 警告状态跟踪改进后可能会发出更多警告**  
  
     早期版本的编译器无法有效跟踪 #pragma 警告状态更改，因而无法发出所有所需的警告。 这种行为会引发风险，导致在程序不希望的情况下有效禁止显示某些警告。 编译器现在能够更加可靠地跟踪 #pragma 警告状态，尤其与模板内部的 #pragma 警告状态更改相关，并选择性发出新警告 C5031 和 C5032，旨在帮助程序员找到意外使用 `#pragma warning(push)` 和 `#pragma warning(pop)`。  
  
     由于改进了 #pragma 警告状态更改跟踪，现在可能会发出以前错误地禁止显示的警告或与以前误诊问题的相关警告。  
  
-   **对无法访问代码标识的改进**  
  
     针对早期版本的编译器进行的 C++ 标准库的更改和内联函数调用能力改进可能会使编译器能够证明某些代码现在无法访问。 这一新行为可能导致新警告并更频繁地发出警告 C4720 实例。  
  
    ```Output  
    warning C4720: unreachable code  
    ```  
  
     在许多情况下，只有启用优化进行编译时，才会发出此警告，因为优化可能嵌入更多函数调用，消除冗余代码或者能够确定某些代码是否无法访问。 我们观察到，警告 C4720 的新实例在 try/catch 块中经常发生，尤其是在使用 [std::find](assetId:///std::find?qualifyHint=False&autoUpgrade=True)时。  
  
     示例（之前）  
  
    ```cpp  
    try  
    {  
        auto iter = std::find(v.begin(), v.end(), 5);  
    }  
    catch (...)  
    {  
        do_something();   // ok  
    }  
    ```  
  
     示例（之后）  
  
    ```cpp  
    try  
    {  
        auto iter = std::find(v.begin(), v.end(), 5);  
    }  
    catch (...)  
    {  
        do_something();   // warning C4702: unreachable code  
    }  
    ```  
  
###  <a name="VS_Update2"></a>更新 2 中的符合性改进  
  
-   **可能会因对表达式 SFINAE 的部分支持而发出其他警告和错误**  
  
     由于缺少对表达式 SFINAE 的支持，编译器的早期版本无法分析 `decltype` 说明符中特定类型的表达式。 这种旧行为不正确，也不符合 C++ 标准。 由于持续的符合性改进，此编译器现已可分析这些表达式，并能为表达式 SFINAE 提供部分支持。 因此，此编译器现在可发出在编译器的早期版本无法分析的表达式中找到的警告和错误。  
  
     此新行为分析包含尚未声明类型的 `decltype` 表达式时，将导致编译器发出编译器错误 C2039。  
  
    ```Output  
  
    error C2039: 'type': is not a member of '`global namespace''  
    ```  
  
     示例 1：使用未声明的类型（之前）  
  
    ```cpp  
    struct s1  
    {  
        template < typename T>  
        auto f() - > decltype(s2< T> ::type::f());  // error C2039  
  
        template< typename>  
        struct s2 {};  
    }  
  
    ```  
  
     示例 1（之后）  
  
    ```cpp  
    struct s1  
    {  
        template < typename>  // forward declare s2struct s2;   
  
            template < typename T>  
        auto f() - > decltype(s2< T> ::type::f());  
  
        template< typename>  
        struct s2 {};  
    }  
  
    ```  
  
     此新行为分析 `decltype` 表达式时（该表达式缺少将依赖名称指定为类型所必须使用的关键字 `typename`），编译器将发出编译器警告 C4346 和编译器错误 C2923。  
  
    ```Output  
  
    warning C4346: 'S2<T>::Type': dependent name is not a type  
  
    ```  
  
    ```Output  
  
    error C2923: 's1': 'S2<T>::Type' is not a valid template type argument for parameter 'T'  
    ```  
  
     示例 2：依赖名称不是类型（之前）  
  
    ```cpp  
    template < typename T>  
    struct s1  
    {  
        typedef T type;  
    };  
  
    template < typename T>  
    struct s2  
    {  
        typedef T type;  
    };  
  
    template < typename T>  
    T declval();  
  
    struct s  
    {  
        template < typename T>  
        auto f(T t) - > decltype(t(declval< S1< S2< T> ::type> ::type> ()));  // warning C4346, error C2923  
    };  
  
    ```  
  
     示例 2（之后）  
  
    ```cpp  
    template < typename T> struct s1 { ... };  // as above  
    template < typename T> struct s2 { ... };  // as above  
  
    template < typename T>  
    T declval();  
  
    struct s  
    {  
        template < typename T>  
        auto f(T t) - > decltype(t(declval< S1< typename S2< T> ::type> ::type> ()));  
    };  
  
    ```  
  
-   `volatile` **成员变量将防止出现隐式定义的构造函数和赋值运算符**  
  
     编译器的早期版本允许具有 `volatile` 成员变量的类自动生成默认复制/移动构造函数和默认复制/移动赋值运算符。 这种旧行为不正确，也不符合 C++ 标准。 编译器现在认为拥有可变成员变量的类具有非常用构造函数和赋值运算符，这将防止自动生成这些运算符的默认实现。  当此类为某一联合（或类中的匿名联合）的成员时，会将联合（或包含匿名联合的类）的复制/移动构造函数和复制/移动赋值运算符的隐式定义为已删除。 尝试构造或复制联合（或包含匿名联合的类）而不显式定义它们是错误的，将导致编译器发出编译器错误 C2280。  
  
    ```Output  
  
    error C2280: 'B::B(const B &)': attempting to reference a deleted function  
  
    ```  
  
     示例（之前）  
  
    ```cpp  
    struct A  
    {  
        volatile int i;  
        volatile int j;  
    };  
  
    extern A* pa;  
  
    struct B  
    {  
        union  
        {  
            A a;  
            int i;  
        };  
    };  
  
    B b1{ *pa };  
    B b2(b1);  // error C2280  
    ```  
  
     示例（之后）  
  
    ```cpp  
    struct A  
    {  
        int i; int j;   
    };  
  
    extern volatile A* pa;  
  
    A getA()  // returns an A instance copied from contents of pa  
    {  
        A a;  
        a.i = pa - > i;  
        a.j = pa - > j;  
        return a;  
    }  
  
    struct B;  // as above  
  
    B b1{ GetA() };  
    B b2(b1);  // error C2280  
    ```  
  
-   **静态成员函数不支持 cv 限定符。**  
  
     Visual C++ 2015 的早期版本允许静态成员函数具有 cv 限定符。 此行为是由于 Visual C++ 2015 和 Visual C++ 2015 Update 1 中的回归而导致的；Visual C++ 2013 和 Visual C++ 的早期版本拒绝接受以这种方式编写的代码。 Visual C++ 2015 和 Visual C++ 2015 Update 1 的行为不正确且不符合 C++ 标准。  Visual Studio 2015 Update 2 拒绝接受以这种方式编写的代码，并改为发出编译器错误 C2511。  
  
    ```Output  
    error C2511: 'void A::func(void) const': overloaded member function not found in 'A'  
    ```  
  
     示例（之前）  
  
    ```cpp  
    struct A  
    {  
        static void func();  
    };  
  
    void A::func() const {}  // C2511  
  
    ```  
  
     示例（之后）  
  
    ```cpp  
    struct A  
    {  
        static void func();  
    };  
  
    void A::func() {}  // removed const  
  
    ```  
  
-   **WinRT 代码中不允许枚举的前向声明**（仅影响 /ZW）  
  
     为 Windows 运行时 (WinRT) 编译的代码不允许前向声明 `enum` 类型，这与使用 /clr 编译器开关为 .Net Framework 编译托管 C++ 代码时相似。 此行为可确保枚举大小始终为已知，并可将其正确映射到 WinRT 类型系统。 编译器将拒绝接受以这种方式编写的代码，并发出编译器错误 C2599 和编译器错误 C3197。  
  
    ```Output  
  
    error C2599: 'CustomEnum': the forward declaration of a WinRT enum is not allowed  
  
    ```  
  
    ```Output  
  
    error C3197: 'public': can only be used in definitions  
  
    ```  
  
     示例（之前）  
  
    ```cpp  
    namespace A {  
        public enum class CustomEnum : int32;  // forward declaration; error C2599, error C3197  
    }  
  
    namespace A {  
        public enum class CustomEnum : int32  
        {  
            Value1  
        };  
    }  
  
    public ref class Component sealed  
    {  
    public:  
        CustomEnum f()  
        {  
            return CustomEnum::Value1;  
        }  
    };  
  
    ```  
  
     示例（之后）  
  
    ```cpp  
              // forward declaration of CustomEnum removed  
  
    namespace A {  
        public enum class CustomEnum : int32  
        {  
            Value1  
        };  
    }  
  
    public ref class Component sealed  
    {  
    public:  
        CustomEnum f()  
        {  
            return CustomEnum::Value1;  
        }  
    };  
  
    ```  
  
-   **重载的非成员运算符 new 和运算符 delete 可能不是以内联方式声明的**（默认开启等级 1 (/W1)）  
  
     当以内联方式声明非成员运算符 new 和运算符 delete 函数时，编译器的早期版本不会发出警告。 以这种方式编写的代码格式不正确（无需诊断），并且可能由于不匹配的 new 和 delete 运算符（尤其是与调整了大小的释放共同使用时）而导致难以诊断的内存问题。   编译器现将发出编译器警告 C4595 以帮助识别以这种方式编写的代码。  
  
    ```Output  
  
    warning C4595: 'operator new': non-member operator new or delete functions may not be declared inline  
  
    ```  
  
     示例（之前）  
  
    ```cpp  
              inline void* operator new(size_t sz)  // warning C4595  
    {  
        ...  
    }  
  
    ```  
  
     示例（之后）  
  
    ```cpp  
              void* operator new(size_t sz)  // removed inline  
    {  
        ...  
    }  
  
    ```  
  
     修复以这种方式编写的代码可能需要将运算符定义从头文件移动到相应的源文件中。  
  
###  <a name="VS_Update3"></a>更新 3 中的符合性改进  
  
-   **现在，std::is_convertable 可以检测自我赋值**（标准库）  
  
     以前版本的 `std::is_convertable` type-trait 在其复制构造函数被删除或私有时，无法正确检测类类型的自我赋值。 现在，当应用于具有已删除或私有复制构造函数的类类型时，`std::is_convertable<>::value` 已正确设置为 `false`。  
  
     没有与此更改相关联的编译器诊断。  
  
     示例  
  
    ```cpp  
    #include <type_traits>  
  
                class X1  
    {  
                public:  
                X1(const X1&) = delete;  
                };  
  
                class X2  
    {  
                private:  
                X2(const X2&);  
                };  
  
    static_assert(std::is_convertible<X1&, X1>::value, "BOOM");static_assert(std::is_convertible<X2&, X2>::value, "BOOM");  
    ```  
  
     在以前版本的 Visual C++ 中，此示例底部的静态断言可传递，因为 `std::is_convertable<>::value` 错误地设置为 `true`。 现在，`std::is_convertable<>::value` 正确设置为 `false`，使静态断言失败。  
  
-   **默认设置或已删除的日常复制和移动构造函数遵从访问说明符**  
  
     对于默认设置或已删除的日常复制和移动构造函数的访问说明符，早期版本的编译器在允许调用之前不进行检查。 这种旧行为不正确，也不符合 C++ 标准。 在某些情况下，这种旧行为会导致无提示代码生成错误风险，从而导致不可预知的运行时行为。 现在，编译器检查默认设置或已删除的日常复制和移动构造函数的访问说明符，以确定是否能调用它，如果不能，则发出编译器警告 C2248。  
  
    ```Output  
  
    error C2248: 'S::S' cannot access private member declared in class 'S'  
    ```  
  
     示例（之前）  
  
    ```cpp  
    class S {  
    public:  
        S() = default;  
    private:  
        S(const S&) = default;  
    };  
  
    void f(S);  // pass S by value  
  
    int main()  
    {  
        S s;  
        f(s);  // error C2248, can't invoke private copy constructor  
    }  
  
    ```  
  
     示例（之后）  
  
    ```cpp  
    class S {  
    public:  
        S() = default;  
    private:  
        S(const S&) = default;  
    };  
  
    void f(const S&);  // pass S by reference  
  
    int main()  
    {  
        S s;  
        f(s);   
    }  
  
    ```  
  
-   **弃用属性化 ATL 代码支持**（默认开启等级 1 (/W1)）  
  
     以前版本的编译器支持属性化 ATL 代码。 由于下一阶段将删除[从 Visual C++ 2008](https://msdn.microsoft.com/library/bb384632\(v=vs.90\).aspx) 开始的属性化 ATL 代码支持，所以已弃用属性化 ATL 代码。 编译器现将发出编译器警告 C4467 以帮助识别这类已弃用的代码。  
  
    ```Output  
    warning C4467: Usage of ATL attributes is deprecated  
    ```  
  
     若要在编译器删除支持之前继续使用属性化 ATL 代码，可以通过将 `/Wv:18` 或 `/wd:4467` 命令行参数传递给编译器或在源代码中添加 `#pragma warning(disable:4467)` 来禁用此警告。  
  
     示例 1（之前）  
  
    ```cpp  
              [uuid("594382D9-44B0-461A-8DE3-E06A3E73C5EB")]  
    class A {};  
  
    ```  
  
     示例 1（之后）  
  
    ```cpp  
    __declspec(uuid("594382D9-44B0-461A-8DE3-E06A3E73C5EB")) A {};  
  
    ```  
  
     有时需要创建 IDL 文件以避免使用已弃用的 ATL 属性，如以下示例代码所示  
  
     示例 2（之前）  
  
    ```cpp  
    [emitidl];  
    [module(name = "Foo")];  
  
    [object, local, uuid("9e66a290-4365-11d2-a997-00c04fa37ddb")]  
    __interface ICustom {  
        HRESULT Custom([in] long l, [out, retval] long *pLong);  
        [local] HRESULT CustomLocal([in] long l, [out, retval] long *pLong);  
    };  
  
    [coclass, appobject, uuid("9e66a294-4365-11d2-a997-00c04fa37ddb")]  
    class CFoo : public ICustom  
    {  
        // ...  
    };  
  
    ```  
  
     首先，创建 *.idl 文件；vc140.idl 生成的文件可用于获取包含接口和注释的 \*.idl文件。  
  
     然后，将 MIDL 步骤添加到生成中以确保生成 C++ 接口定义。  
  
     示例 2 IDL（之后）  
  
    ```cpp  
    import "docobj.idl";  
  
    [  
        object, local, uuid(9e66a290 - 4365 - 11d2 - a997 - 00c04fa37ddb)  
    ]  
  
    interface ICustom : IUnknown {  
        HRESULT  Custom([in] long l, [out, retval] long *pLong);  
        [local] HRESULT  CustomLocal([in] long l, [out, retval] long *pLong);  
    };  
  
    [version(1.0), uuid(29079a2c - 5f3f - 3325 - 99a1 - 3ec9c40988bb)]  
    library Foo  
    {  
        importlib("stdole2.tlb");  
    importlib("olepro32.dll");  
    [  
        version(1.0),  
        appobject,uuid(9e66a294 - 4365 - 11d2 - a997 - 00c04fa37ddb)  
    ]  
  
    coclass CFoo {  
        interface ICustom;  
    };  
    }  
  
    ```  
  
     然后，在实现文件中直接使用 ATL，如以下示例代码所示。  
  
     示例 2 实现（之后）  
  
    ```cpp  
    #include <idl.header.h>  
    #include <atlbase.h>  
  
    class ATL_NO_VTABLE CFooImpl :  
        public ICustom,  
        public ATL::CComObjectRootEx< CComMultiThreadModel>  
    {  
    public:  
        BEGIN_COM_MAP(CFooImpl)  
            COM_INTERFACE_ENTRY(ICustom)  
        END_COM_MAP()  
    };  
  
    ```  
  
-   **预编译标头 (PCH) 文件和不匹配的 #include 指令**（仅影响 /Wall /WX）  
  
     使用预编译标头 (PCH) 文件时，以前版本的编译器接受 `-Yc` 和 `-Yu` 编译之间的源文件中不匹配的 `#include` 指令。 编译器不再接受以这种方式编写的代码。   使用 PCH 文件时，编译器现将发出编译器警告 CC4598 以帮助识别不匹配的 `#include` 指令。  
  
    ```Output  
  
    warning C4598: 'b.h': included header file specified for Ycc.h at position 2 does not match Yuc.h at that position  
  
    ```  
  
     示例（之前）：  
  
     X.cpp (-Ycc.h)  
  
    ```cpp  
    #include "a.h"  
    #include "b.h"  
    #include "c.h"  
  
    ```  
  
     Z.cpp (-Yuc.h)  
  
    ```cpp  
    #include "b.h"  
    #include "a.h"  // mismatched order relative to X.cpp  
    #include "c.h"  
  
    ```  
  
     示例（之后）  
  
     X.cpp (-Ycc.h)  
  
    ```cpp  
    #include "a.h"  
    #include "b.h"   
    #include "c.h"  
  
    ```  
  
     Z.cpp (-Yuc.h)  
  
    ```cpp  
    #include "a.h"  
    #include "b.h" // matched order relative to X.cpp  
    #include "c.h"  
  
    ```  
  
-   **预编译标头 (PCH) 文件和不匹配的包含目录**（仅影响 /Wall /WX）  
  
     使用预编译标头 (PCH) 文件时，对于 `-Yc` 和 `-Yu` 编译之间的编译器，以前版本的编译器接受不匹配的包含目录 (`-I`) 命令行参数。 编译器不再接受以这种方式编写的代码。   使用 PCH 文件时，编译器现将发出编译器警告 CC4599 以帮助识别不匹配的包含目录 (`-I`) 命令行参数。  
  
    ```Output  
  
    warning C4599: '-I..' : specified for Ycc.h at position 1 does not match Yuc.h at that position  
  
    ```  
  
     示例（之前）  
  
    ```ms-dos  
  
    cl /c /Wall /Ycc.h -I.. X.cpp  
    cl /c /Wall /Yuc.h Z.cpp  
  
    ```  
  
     示例（之后）  
  
    ```ms-dos  
  
    cl /c /Wall /Ycc.h -I.. X.cpp  
    cl /c /Wall /Yuc.h -I.. Z.cpp  
  
    ```  
  
## <a name="visual-c-2013-conformance-changes"></a>Visual C++ 2013 符合性更改  
  
### <a name="compiler"></a>编译器  
  
-   最终关键字现在会在它以前编译过的位置生成未解析的符号错误：  
  
    ```cpp  
    struct S1 {  
        virtual void f() = 0;  
    };  
  
    struct S2 final : public S1 {  
        virtual void f();  
    };  
  
    int main(S2 *p)  
    {  
        p->f();  
    }  
  
    ```  
  
     在早期版本中，由于调用为虚调用，因此未发出错误；但程序可能在运行时崩溃。 现在，由于类已知为最终的类，因此将发出链接器错误。 在此示例中，若要修复错误，请针对包含 S2::f 定义的对象进行链接。  
  
-   在使用命名空间中的友元函数时，必须先重新声明该友元函数，然后再对其进行引用，否则将收到错误，因为编译器现在遵循 ISO C++ 标准。 例如，此代码不再编译：  
  
    ```cpp  
    namespace NS {  
        class C {  
            void func(int);  
            friend void func(C* const) {}  
        };  
  
        void C::func(int) {  
            NS::func(this);  // error  
        }  
    }  
  
    ```  
  
     若要更正此代码，请声明友元函数：  
  
    ```cpp  
    namespace NS {  
        class C {  
            void func(int);  
            friend void func(C* const) {}  
        };  
  
        void func(C* const);  // conforming fix  
  
        void C::func(int) {  
            NS::func(this);  
        }  
  
    ```  
  
-   C++ 标准不允许类中存在显式专用化。 虽然 Visual C++ 在某些情况下会允许，但在诸如下列示例的情况下，现在会生成错误，因为编译器不会将第二个函数视为第一个函数的专用化。  
  
    ```cpp  
    template < int N>  
    class S {  
    public:  
        template  void f(T& val);  
        template < > void f(char val);  
    };  
  
    template class S< 1>;  
  
    ```  
  
     若要更正此代码，请修改第二个函数：  
  
    ```cpp  
    template <> void f(char& val);  
  
    ```  
  
-   Visual C++ 不再尝试消除下面示例中的两个函数，而是会发出错误：  
  
    ```cpp  
    template< typename T> void Func(T* t = nullptr);  
    template< typename T> void Func(...);  
  
    int main() {  
        Func< int>(); // error  
    }  
  
    ```  
  
     若要更正此代码，请阐明调用：  
  
    ```cpp  
    template< typename T> void Func(T* t = nullptr);  
    template< typename T> void Func(...);  
  
    int main() {  
        Func< int>(nullptr); // ok  
    }  
  
    ```  
  
-   在使编译器与 ISO C++11 兼容之前，必须先编译以下代码并使 x 解析为类型 int：  
  
    ```cpp  
    auto x = {0};  
    int y = x;  
  
    ```  
  
     此代码现在将 x 解析为 std::initializer_list\<int> 类型并会导致在尝试将 x 分配到 int 类型的下一行上出错。（默认情况下，不存在转换。）若要更正此代码，请使用 int 替换 auto：  
  
    ```cpp  
    int x = {0};  
    int y = x;  
  
    ```  
  
-   当右侧值的类型与要初始化的左侧值的类型不匹配时，不再允许聚合初始化，并且将发出错误，原因是 ISO C++11 标准要求统一初始化，以便在不进行收缩转换的情况下正常运行。 之前，如果收缩转换可用，则会发出[编译器警告（等级 4）C4242](../error-messages/compiler-warnings/compiler-warning-level-4-c4242.md) 警告，而不会发出错误。  
  
    ```cpp  
    int i = 0;  
    char c = {i}; // error  
  
    ```  
  
     若要更正此代码，请添加显式收缩转换：  
  
    ```cpp  
    int i = 0;  
    char c = {static_cast<char>(i)};  
  
    ```  
  
-   不再允许以下初始化：  
  
    ```cpp  
    void *p = {{0}};  
  
    ```  
  
     若要更正此代码，请采用下列任一格式：  
  
    ```cpp  
    void *p = 0;  
    // or  
    void *p = {0};  
  
    ```  
  
-   名称查找已更改。 以下代码在 Visual Studio 2012 中 Visual C++ 和 Visual Studio 2013 中 Visual C++ 内的解析方式不同：  
  
    ```cpp  
    enum class E1 { a };  
    enum class E2 { b };  
  
    int main()  
    {  
        typedef E2 E1;  
        E1::b;  
    }  
  
    ```  
  
     在 Visual Studio 2012 的 Visual C++ 中，表达式 E1::b 中的 E1 在全局范围内解析为 ::E1。 在 Visual Studio 2013 的 Visual C++ 中，表达式 E1::b 中的 E1 在 main() 中解析为 typedef E2 定义并具有类型 ::E2。  
  
-   对象布局已发生更改。 在 x64 上，类的对象布局可能在早期版本基础上发生了更改。 如果它具有一个虚拟函数，但它不具有拥有虚拟函数的基类，则编译器的对象模型会将一个指针插入到数据成员布局之后的虚拟函数表。 这意味着布局可能不会在所有情况下都达到最优。 在以前版本中，x64 优化会尝试改善布局，但由于它在复杂代码情况下不能正常运行，因此 Visual Studio 2013 的 Visual C++ 中已将其删除。 例如，考虑此代码：  
  
    ```cpp  
    __declspec(align(16)) struct S1 {  
    };  
  
    struct S2 {  
        virtual ~S2();  
        void *p;  
        S1 s;  
    };  
  
    ```  
  
-   在 Visual Studio 2013 的 Visual C++ 中，x64 上 sizeof(S2) 的结果为 48，但在以前版本中，计算结果为 32。 若要使它在 x64 Visual Studio 2013 的 Visual C++ 中的计算结果为 32，请添加具有虚拟函数的虚拟基类：  
  
    ```cpp  
    __declspec(align(16)) struct S1 {  
    };  
  
    struct dummy {  
        virtual ~dummy() {}  
    };  
    struct S2 : public dummy {  
        virtual ~S2();  
        void *p;  
        S1 s;  
    };  
  
    ```  
  
     若要在代码中查找早期版本将会优化的位置，请将该版本的编译器与 /W3 编译器选项一起使用，并打开警告 4370。 例如:  
  
    ```cpp  
    #pragma warning(default:4370)  
  
    __declspec(align(16)) struct S1 {  
    };  
  
    struct S2 {  
        virtual ~S2();  
        void *p;  
        S1 s;  
    };  
  
    ```  
  
     在 Visual Studio 2013 中 Visual C++ 之前的 Visual C++ 编译器中，此代码输出以下消息：警告 C4370: 'S2' : 为了更好地封装，类的布局与早期版本的编译器已有所不同  
  
     在所有版本的 Visual C++ 中，x86 编译器具有相同的次优布局问题。 例如，如果为 x86 编译以下代码：  
  
    ```cpp  
    struct S {  
        virtual ~S();  
        int i;  
        double d;  
    };  
  
    ```  
  
     sizeof(S) 的结果为 24。 但是，如果使用刚才提到的 x64 变通方案，则此结果可以减少到 16：  
  
    ```cpp  
    struct dummy {  
        virtual ~dummy() {}  
    };  
  
    struct S : public dummy {  
        virtual ~S();  
        int i;  
        double d;  
    };  
  
    ```  
  
### <a name="standard-library"></a>标准库  
 Visual Studio 2013 中的 Visual C++ 可以检测到 _ITERATOR_DEBUG_LEVEL 中的不匹配（这是在 Visual C++ 2010 中实现的），以及 RuntimeLibrary 不匹配。 当编译器选项 /MT（静态发布）、/MTd（静态调试）、/MD（动态发布）和 /MDd（动态调试）相混合时，将会发生这些问题。  
  
-   如果你的代码承认以前版本的模拟别名模板，则必须对其进行更改。 例如，必须使用 allocator_traits\<A>::rebind_alloc\<U>，而不是使用 allocator_traits\<A>::rebind_alloc\<U>::other。 虽然 ratio_add\<R1, R2>::type 不是必须的，我们现在建议使用 ratio_add\<R1, R2>，但前者仍会进行编译，因为 ratio\<N, D> 需要具有一个“type”typedef 以用于缩减比（如果已缩减，将为相同的类型）。  
  
-   调用 std::min() 或 std::max() 时，必须使用 #include \<algorithm>。  
  
-   如果现有的代码使用之前版本的模拟范围枚举（包装在命名空间中的传统的非范围枚举），则需对其进行更改。 例如，如果引用类型 std::future_status::future_status，现在必须使用 std::future_status。 但是，大多数代码不受影响，例如，std::future_status::ready 仍将编译。  
  
-   显式运算符 bool() 比运算符 unspecified-bool-type() 更严格。 显式运算符 bool() 允许显式转换为 bool，例如，在给定 shared_ptr\<X> sp 的情况下，static_cast\<bool>(sp) 和 bool b(sp) 都有效；允许对 bool 进行布尔值可测试的“上下文转换”，例如，if (sp)、!sp、sp && whatever。 但是，显式运算符 bool() 禁止隐式转换为 bool，因此不能使用 bool b = sp，对于给定的 bool 返回类型，不能使用 return sp。  
  
-   现在已实现实际可变参数模板，_VARIADIC_MAX 和相关宏无效。 如果你仍在定义 _VARIADIC_MAX，请将其忽略。 如果确认了旨在以任何其他方式支持模拟的可变参数模板的宏机制，则必须更改代码。  
  
-   除普通关键字以外，C++ 标准库标头现在禁止宏化区分上下文的关键字“override”和“final”。  
  
-   reference_wrapper/ref()/cref() 现在禁止绑定到临时对象。  
  
-   \<random> 现在严格强制实施其编译时间的前置条件。  
  
-   不同的 C++ 标准库类型特征共有的前置条件是“T 应为完整类型”。 虽然编译器更严格地强制此功能，但不会在所有情形中进行强制。 （由于 C++ 标准库前置条件违反了触发器未定义的行为，因此无法保证能执行此标准。）  
  
-   C++ 标准库不支持 /clr:oldSyntax。  
  
-   common_type<> 的 C++11 规范导致不需要的意外后果；具体而言，它使 common_type\<int, int>::type 返回 int&&。 因此，Visual C++ 可实现针对库工作组问题 2141 的建议的解决方法，这将使 common_type\<int, int="">::type 返回 int。  
  
     作为此更改的副作用，标识用例不再起作用（common_type\<T> 并不总是产生 T 类型）。 这将遵循建议的解决方法，但其将中断依赖于先前行为的所有代码。  
  
     如果需要标识类型特征，请不要使用 <type_traits> 中定义的非标准 std::identity，因为它对 \<void> 无效。 相反，实现你自己的标识类型特征以满足你的需求。 以下是一个示例：  
  
    ```cpp  
    template < typename T> struct Identity {  
        typedef T type;  
    };  
  
    ```  
  
### <a name="mfc-and-atl"></a>MFC 和 ATL  
  
-  **仅 Visual Studio 2013**：Visual Studio 中不再包括 MFC MBCS 库，因为 Unicode 很受欢迎，大大减少了 MBCS 的使用。 此更改也使 MFC 与 Windows SDK 本身更加紧密联合在一起，因为许多新控件和消息都仅支持 Unicode。 但是，如果必须继续使用 MFC MBCS 库，可以从 MSDN 下载中心下载，下载位置：[适用于 Visual Studio 2013 的多字节 MFC 库](https://www.microsoft.com/en-us/download/details.aspx?id=40770)（Multibyte MFC Library for Visual Studio 2013）。 Visual C++ 可再发行组件包仍包含此库。  （请注意：Visual Studio 2015 及更高版本的 Visual C++ 安装组件中包含 MBCS DLL）。
  
-   MFC 功能区的辅助功能已更改。  现在显示的是分层体系结构，而不是一级体系结构。 仍然可以通过调用 CRibbonBar::EnableSingleLevelAccessibilityMode() 来使用旧行为。  
  
-   删除 CDatabase::GetConnect 方法。 为了提高安全性，连接字符串现在进行加密存储并只根据需要进行解密；它不能返回为纯文本。  可使用 CDatabase::Dump 方法来获取此字符串。  
  
-   CWnd::OnPowerBroadcast 签名已更改。 此消息处理程序的签名更改为采用 LPARAM 作为第二个参数。  
  
-   更改签名以适应消息处理程序。 已更改以下函数的参数列表，以使用新添加的 ON_WM_* 消息处理程序：  
  
    -   CWnd :: OnDisplayChange 更改为 (UINT, int, int) 而不是 (WPARAM, LPARAM)，以便可以在消息映射中使用新的 ON_WM_DISPLAYCHANGE 宏。  
  
    -   CFrameWnd::OnDDEInitiate 更改为 (CWnd*, UINT, UNIT) 而不是 (WPARAM, LPARAM)，以便可以在消息映射中使用新的 ON_WM_DDE_INITIATE 宏。  
  
    -   CFrameWnd::OnDDEExecute 更改为 (CWnd*, HANDLE) 而不是 (WPARAM, LPARAM)，以便可以在消息映射中使用新的 ON_WM_DDE_EXECUTE 宏。  
  
    -   CFrameWnd::OnDDETerminate 更改为使用 (CWnd*) 而不是 (WPARAM, LPARAM) 作为参数，以便可以在消息映射中使用新的 ON_WM_DDE_TERMINATE 宏。  
  
    -   CMFCMaskedEdit::OnCut 更改为无参数而不是使用 (WPARAM, LPARAM) 作为参数，以便可以在消息映射中使用新的 ON_WM_CUT 宏。  
  
    -   CMFCMaskedEdit::OnClear 更改为无参数而不是使用 (WPARAM, LPARAM) 作为参数，以便可以在消息映射中使用新的 ON_WM_CLEAR 宏。  
  
    -   CMFCMaskedEdit::OnPaste 更改为无参数而不是使用 (WPARAM, LPARAM) 作为参数，以便可以在消息映射中使用新的 ON_WM_PASTE 宏。  
  
-   已移除 MFC 头文件中的 \#ifdef。 与 Windows 不受支持的版本 (WINVER &lt; 0x0501) 相关的 MFC 头文件中的许多 #ifdef 已移除。  
  
-   ATL DLL (atl120.dll) 已移除。 ATL 现在作为标头和静态库 (atls.lib) 提供。  
  
-   Atlsd.lib、atlsn.lib 和 atlsnd.lib 已移除。 Atls.lib 不再具有字符集依赖项或专用于调试/发布的代码。 由于它与 Unicode/ANSI 和调试/发布的工作原理相同，因此，只需要库的一个版本。  
  
-   ATL/MFC 跟踪工具已被移除（连同 ATL DLL），并且跟踪机制已得到简化。 CTraceCategory 构造函数现在采用一个参数（类别名称），TRACE 宏调用 CRT 调试报告函数。  
  
## <a name="visual-c-2012-breaking-changes"></a>Visual C++ 2012 重大更改  
  
### <a name="compiler"></a>编译器  
  
-   /Yl 编译器选项已更改。 默认情况下，编译器将使用此选项，这可能会导致在某些情况下出现 LNK2011 错误。 有关详细信息，请参阅 [/Yl（为调试库插入 PCH 引用）](../build/reference/yl-inject-pch-reference-for-debug-library.md)。  
  
-   在使用 /clr 编译的代码中，枚举类关键字定义 C++11 枚举，而不是公共语言运行时 (CLR) 枚举。 若要定义 CLR 枚举，必须明确其可访问性。  
  
-   使用模板关键字显式消除依赖名称的歧义（遵从 C++ 语言标准）。 在以下示例中，突出显示的模板关键字是消除歧义所必需的。 有关详细信息，请参阅[依赖类型的名称解析](../cpp/name-resolution-for-dependent-types.md)。  
  
    ```cpp  
    template < typename X = "", typename = "" AY = "">  
    struct Container { typedef typename AY::template Rebind< X> ::Other AX; };  
  
    ```  
  
-   不再允许使用浮点类型的常数表达式作为模板参数，如以下示例所示。  
  
    ```cpp  
    template<float n=3.14>  
    struct B {};  // error C2993: 'float': illegal type for non-type template parameter 'n'  
  
    ```  
  
-   使用 /GS 命令行选项编译且具有差一漏洞的代码可能导致运行时进程终止，如以下伪代码示例所示。  
  
    ```cpp  
    char buf[MAX]; int cch; ManipulateString(buf, &cch); // ... buf[cch] = '\0'; // if cch >= MAX, process will terminate  
    ```  
  
-   x86 版本的默认体系结构更改为 SSE2，因此，编译器可以发出 SSE 指令，并且将使用 XMM 寄存器来执行浮点计算。 若要还原到以前的行为，请使用 /arch:IA32 编译器标志将体系结构指定为 IA32。  
  
-   编译器可能会在以前未发出警告的位置发出警告[编译器警告（等级 4）C4703](../error-messages/compiler-warnings/compiler-warning-level-4-c4703.md) 和 C4701。 编译器对使用指针类型的未初始化局部变量应用更强大的检查。  
  
-   指定新的链接器标志 /HIGHENTROPYVA 后，Windows 8 通常会使内存分配返回 64 位地址。                 （Windows 8 之前，此类分配通常会返回小于 2 GB 的地址。）这可能会暴露现有代码中的指针截断 bug。 默认情况下，此开关处于开启状态。  若要禁用此行为，请指定 /HIGHENTROPYVA:NO。  
  
-   托管的编译器 (Visual Basic/C#) 也支持托管生成的 /HIGHENTROPYVA。  但是，在这种情况下，/HIGHENTROPYVAswitch 默认处于关闭状态。  
  
### <a name="ide"></a>IDE  
  
-   虽然我们建议不要在 C++/CLI 中创建 Windows 窗体应用程序，但是仍然支持维护现有的 C++/CLI UI应用程序。 如果必须要创建 Windows 窗体应用程序或任何其他 .NET UI 应用程序，请使用 C# 或 Visual Basic。 仅将 C++/CLI 用于互操作性。  
  
### <a name="parallel-patterns-library-and-concurrency-runtime-library"></a>并行模式库和并发运行时库  
 UmsThreadDefault 的 SchedulerType 枚举已弃用。 UmsThreadDefault 的规范生成已弃用警告，并内部映射回 ThreadScheduler。  
  
### <a name="standard-library"></a>标准库  
  
-   根据 C++98/03 和 C++11 标准之间的重大更改，在 Visual Studio 2012 的 Visual C ++ 中，使用显式模板参数调用 make_pair()（例如 make_pair\<int, int>(x, y)）通常不编译。 相关解决方案是始终调用 make_pair()without 显式模板参数，例如 make_pair(x, y)。 提供显式模板参数会破坏函数的作用。 如果需要精确控制生成类型，请使用 pair 而不是 make_pair，例如 pair\<short, short>(int1, int2)。  
  
-   C++98/03 和 C++11 标准之间的另一重大更改是：如果 A 可隐式转换为 B，B 可隐式转换为 C，但 A 不能隐式转换为 C，则 C++98/03 和 Visual C++ 2010 允许 pair\<A, X>（隐式或显式）转换为 pair\<C, X>。 （此处不关注另一种类型 X，这不针对此对中的第一种类型。）由于 C++11 和 Visual Studio 2012 中的 Visual C++ 检测到 A 不能隐式转换为 C，所以从重载解析中删除了对转换。 这对许多方案来说是有益的更改。 例如，重载 func(const pair\<int, int>&) 和 func(const pair\<string, string>&) 以及调用具有 pair\<const char *, const char \*> 的 func() 将按照此更改进行编译。 但是，此更改会中断依赖主动对转换的代码。 通常可以通过显示执行部分转换来修复这些代码，例如，将 make_pair(static_cast\<B>(a), x) 传递给需要 pair\<C, X> 的函数。  
  
-   Visual C++ 2010 模拟可变参数模板（如 make_shared\<T>(arg1, arg2, argN)）通过使用预处理器机制杜绝重载和专用化，将参数个数限制为最多 10 个。 在 Visual Studio 2012 的 Visual C++ 中，此限制减少到 5 个参数，以减少大多数用户的编译时间和编译器内存消耗。 但是，可以通过在项目范围内将 _VARIADIC_MAX 显式定义为 10 来设置之前的限制。  
  
-   C++11 17.6.4.3.1 [macro.names]/2 禁止在包含 C++ 标准库标头时宏化关键字。 如果检测到宏化关键字，标头现将发出编译器错误。 （虽然通过定义 _ALLOW_KEYWORD_MACROS 可允许此类代码进行编译，但我们强烈建议不要这样做。）但有一个例外，即默认允许宏化的 new，因为标头通过使用 #pragma push_macro("new")/#undef new/#pragma pop_macro("new") 进行全面自我防护。 定义 _ENFORCE_BAN_OF_MACRO_NEW 所执行的操作正如其名称所示。  
  
-   为了实现各种优化和调试检查，C++ 标准库实现特意中断了 Visual Studio 各版本（2005、2008、2010、2012）中的二进制文件兼容性。 如果使用 C++ 标准库，则使用不同版本编译的对象文件和静态库无法混合在同一二进制文件（EXE 或 DLL）中，并且无法在使用不同版本编译的二进制文件之间传递 C++ 标准库对象。 对象文件和静态库的混合（使用由 Visual C++ 2010 编译的 C++ 标准库和由 Visual Studio 2012 中的 Visual C++ 编译的库）会发出有关 _MSC_VER 不匹配的链接器错误，其中 _MSC_VER 是包含编译器主版本（对于 Visual Studio 2012 中的 Visual C++ 是 1700）的宏。 此检查无法检测 DLL 混合，也无法检测涉及 Visual C++ 2008 或早期版本的混合。  
  
-   除了检测 _ITERATOR_DEBUG_LEVEL 不匹配项（在 Visual C++ 2010 中实现），Visual Studio 2012 中的 Visual C++ 还可以检测运行时库不匹配项。 当编译器选项 /MT（静态发布）、/MTd（静态调试）、/MD（动态发布）和 /MDd（动态调试）相混合时，将会发生这些问题。  
  
-   operator\<()、operator>()、operator\<=() 和 operator>=() 以前适用于容器的 std::unordered_map andstdext::hash_map 系列，但是其实现实际上没用。 这些非标准运算符已在 Visual Studio 2012 中的 Visual C++ 中删除。 此外，thestd::unordered_map 系列的 operator==() 和 operator!=() 的实现已扩展到包括 stdext::hash_map 系列。 （建议不要在新代码中使用 thestdext::hash_map 系列。）  
  
-   C++11 22.4.1.4 [locale.codecvt] 指定 codecvt::length() 和 codecvt::do_length() 应采用可修改的 stateT&parameters，但 Visual C++ 2010 采用了 const stateT&。 根据标准，Visual Studio 2012 中的 Visual C++ 强制采用 stateT&。 这一区别对于尝试替代虚拟函数 do_length() 的任何人来说都非常重要。  
  
### <a name="crt"></a>CRT  
  
-   用于 new 和 malloc() 的 C 运行时 (CRT) 堆，不再是私有的。 现在，CRT 使用进程堆。 这意味着卸载 DLL 时，不会销毁堆，因此静态链接到 CRT 的 DLL 必须确保 DLL 代码分配的内存在卸载之前被清除。  
  
-   iscsymf() 函数使用负值断言。  
  
-   已更改 threadlocaleinfostruct 结构以适应区域设置函数的更改。  
  
-   具有相应内部函数（如 memxxx()、strxxx()）的 CRT 函数，已从 intrin.h 删除。 如果以前仅对这些函数包含 intrin.h，则现在必须包含相应的 CRT 标头。  
  
### <a name="mfc-and-atl"></a>MFC 和 ATL  
  
-   已删除 Fusion 支持 (afxcomctl32.h)，因此，已删除 afxcomctl32.h 中定义的所有方法。 头文件 afxcomctl32.h 和 afxcomctl32.inl 已删除。  
  
-   已将 CDockablePane::RemoveFromDefaultPaneDivider 的名称更改为 CDockablePane::RemoveFromDefaultPaneDividier。  
  
-   已更改 CFileDialog::SetDefExt 的签名以使用 LPCTSTR，因此，Unicode 版本受到影响。  
  
-   已删除过时的 ATL 跟踪类别。  
  
-   已更改 CBasePane::MoveWindow 的签名以使用 const CRect。  
  
-   已更改 CMFCEditBrowseCtrl::EnableBrowseButton 的签名。  
  
-   已从 CMFCBaseTabCtrl 删除 m_fntTabs 和 m_fntTabsBold。  
  
-   已将一个参数添加到 CMFCRibbonStatusBarPane 构造函数。 （因为它是默认参数，所以不会破坏源代码。）  
  
-   已将一个参数添加到 CMFCRibbonCommandsListBox 构造函数。 （因为它是默认参数，所以不会破坏源代码。）  
  
-   已删除 AFXTrackMouse API（和相关计时器进程）。 改用 Win32 TrackMouseEvent API。  
  
-   已将一个参数添加到 CFolderPickerDialog 构造函数。 （因为它是默认参数，所以不会破坏源代码。）  
  
-   已更改 CFileStatus 结构大小：m_attribute 成员从 BYTE 更改为 DWORD（以匹配从 GetFileAttributes 返回的值）。  
  
-   在 Unicode 版本中，CRichEditCtrl 和 CRichEditView 使用 MSFTEDIT_CLASS（RichEdit 4.1 控件），而不是使用 RICHEDIT_CLASS（RichEdit 3.0 控件）。  
  
-   已删除 AFX_GLOBAL_DATA::IsWindowsThemingDrawParentBackground，因为它在 Windows Vista、Windows 7 和 Windows 8 上始终为 TRUE。  
  
-   已删除 AFX_GLOBAL_DATA::IsWindowsLayerSupportAvailable，因为它在 Windows Vista、Windows 7 和 Windows 8 上始终为 TRUE。  
  
-   已删除 AFX_GLOBAL_DATA::DwmExtendFrameIntoClientArea。 在 Windows Vista、Windows 7 和 Windows 8 上直接调用 Windows API。  
  
-   已删除 AFX_GLOBAL_DATA::DwmDefWindowProc。 在 Windows Vista、Windows 7 和 Windows 8 上直接调用 Windows API。  
  
-   已将 AFX_GLOBAL_DATA::DwmIsCompositionEnabled 重命名为 IsDwmCompositionEnabled 以消除名称冲突。  
  
-   已更改大量 MFC 内部计时器的标识符并将定义移到 afxres.h (AFX_TIMER_ID_*)。  
  
-   已更改 OnExitSizeMove 方法的签名以便与 ON_WM_EXITSIZEMOVE 宏保持一致：  
  
    -   CFrameWndEx  
  
    -   CMDIFrameWndEx  
  
    -   CPaneFrameWnd  
  
-   已更改 OnDWMCompositionChanged 的名称和签名以便与 ON_WM_DWMCOMPOSITIONCHANGED 宏保持一致：  
  
    -   CFrameWndEx  
  
    -   CMDIFrameWndEx  
  
    -   CPaneFrameWnd  
  
-   已更改 OnMouseLeave 方法的签名以便与 ON_WM_MOUSELEAVE 宏保持一致：  
  
    -   CMFCCaptionBar  
  
    -   CMFCColorBar  
  
    -   CMFCHeaderCtrl  
  
    -   CMFCProperySheetListBox  
  
    -   CMFCRibbonBar  
  
    -   CMFCRibbonPanelMenuBar  
  
    -   CMFCRibbonRichEditCtrl  
  
    -   CMFCSpinButtonCtrl  
  
    -   CMFCToolBar ReplaceThisText  
  
    -   CMFCToolBarComboBoxEdit  
  
    -   CMFCToolBarEditCtrl  
  
    -   CMFCAutoHideBar  
  
-   已更改 OnPowerBroadcast 方法的签名以便与 ON_WM_POWERBROADCAST 宏保持一致：  
  
    -   CFrameWndEx  
  
    -   CMDIFrameWndEx  
  
-   已更改 OnStyleChanged 方法的签名以便与 ON_WM_STYLECHANGED 宏保持一致：  
  
    -   CMFCListCtrl  
  
    -   CMFCStatusBar  
  
-   已将内部方法 FontFamalyProcFonts 重命名为 FontFamilyProcFonts。  
  
-   已删除大量全局静态 CString 对象以消除某些情况下的内存泄漏（替换为 #defines），且已删除以下类成员变量：  
  
    -   CKeyBoardManager::m_strDelimiter  
  
    -   CMFCPropertyGridProperty::m_strFormatChar  
  
    -   CMFCPropertyGridProperty::m_strFormatShort  
  
    -   CMFCPropertyGridProperty::m_strFormatLong  
  
    -   CMFCPropertyGridProperty::m_strFormatUShort  
  
    -   CMFCPropertyGridProperty::m_strFormatULong  
  
    -   CMFCPropertyGridProperty::m_strFormatFloat  
  
    -   CMFCPropertyGridProperty::m_strFormatDouble  
  
    -   CMFCToolBarImages::m_strPngResType  
  
    -   CMFCPropertyGridProperty::m_strFormat  
  
-   已更改 CKeyboardManager::ShowAllAccelerators 的签名，并删除加速器的 delimiter 参数。  
  
-   已添加 CPropertyPage::GetParentSheet，在 CPropertyPage 类中调用它（而不是 GetParent）以获取正确的父表窗口，该窗口可能是 CPropertyPage 的父窗口或祖父窗口。 可能需要更改代码以调用 GetParentSheet 而不是 ofGetParent。  
  
-   已修复 ATLBASE.H 中会导致错误禁用警告的不均衡的 #pragma warning(push)。 现在，分析 ATLBASE.H 后，可以正确地启用这些警告。  
  
-   已将与 D2D 相关的方法从 AFX_GLOBAL_DATA 移至 _AFX_D2D_STATE:  
  
    -   GetDirectD2dFactory  
  
    -   GetWriteFactory  
  
    -   GetWICFactory  
  
    -   InitD2D  
  
    -   ReleaseD2DRefs  
  
    -   IsD2DInitialized  
  
    -   D2D1MakeRotateMatrix  
  
    -   调用 AfxGetD2DState->IsD2DInitialized 而不是调用 afxGlobalData.IsD2DInitialized 等。  
  
-   已从 \atlmfc\include\ 文件夹删除过时的 ATL*.CPP 文件。  
  
-   已将 afxGlobalData 初始化移动到按需而不是 CRT 初始化时间，以满足 DLLMain 要求。  
  
-   已将 RemoveButtonByIndex 方法添加到 CMFCOutlookBarPane 类。  
  
-   已将 CMFCCmdUsageCount::IsFreqeuntlyUsedCmd 更正为 IsFrequentlyUsedCmd。  
  
-   已将一些实例的 RestoreOriginalstate 更正为 RestoreOriginalState (CMFCToolBar、CMFCMenuBar、CMFCOutlookBarPane)。  
  
-   已从 CDockablePane: SetCaptionStyle、IsDrawCaption、IsHideDisabledButtons、GetRecentSiblingPaneInfo 和 CanAdjustLayout 删除未使用的方法。  
  
-   已删除 CDockablePane 静态成员变量 m_bCaptionText 和 m_bHideDisabledButtons。  
  
-   已将 DeleteString 替代方法添加到 CMFCFontComboBox。  
  
-   已从 CPane: GetMinLength 和 IsLastPaneOnLastRow 删除未使用的方法。  
  
-   已将 CPane::GetDockSiteRow(CDockingPanesRow *) 重命名为 CPane::SetDockSiteRow。  
  
## <a name="visual-c-2010-breaking-changes"></a>Visual C++ 2010 重大更改  
  
### <a name="compiler"></a>编译器  
  
-   auto 关键字具有新的默认含义。 因为使用旧含义的情况很少见，所以大多数应用程序不会受到此更改的影响。  
  
-   引入了新关键字 static_assert，如果代码中已经有该名称的标识符，则会导致名称冲突。  
  
-   对新的 lambda 表示法的支持不包括支持对 IDL uuid 属性中的未引用 GUID 进行编码。  
  
-   .NET Framework 4 引入了损坏状态异常的概念，这是指使进程处于不可恢复损坏状态的异常。 默认情况下，无法捕获损坏状态异常，即使使用可捕获所有其他异常的 /EHa 编译器选项，也是如此。                 若要显式捕获损坏状态异常，请使用 __try-\__except 语句。 或者，应用 [HandledProcessCorruptedStateExceptions] 属性以启用捕获损坏状态异常的函数。  此更改主要影响可能必须捕获损坏状态异常的系统程序员。 八个例外是 STATUS_ACCESS_VIOLATION、STATUS_STACK_OVERFLOW、EXCEPTION_ILLEGAL_INSTRUCTION、EXCEPTION_IN_PAGE_ERROR、EXCEPTION_INVALID_DISPOSITION、EXCEPTION_NONCONTINUABLE_EXCEPTION、EXCEPTION_PRIV_INSTRUCTION、STATUS_UNWIND_CONSOLIDATE。                 有关这些异常的详细信息，请参阅 [GetExceptionCode](https://msdn.microsoft.com/en-us/library/windows/desktop/ms679356.aspx) 宏。  
  
-   修改后的 /GS 编译器选项比早期版本更全面地防止缓冲区溢出。 此版本可能会在可能导致性能下降的堆栈中插入额外的安全检查。 使用新关键字 __declspec(safebuffers) 指示编译器不要为特定函数插入安全检查。  
  
-   如果使用 /GL （全程序优化）和 /clr（公共语言运行时编译）编译器选项进行编译，则将忽略 /GLoption。 进行此更改是因为组合编译器选项的作用微乎其微。 得益于此更改，生成的性能得到改进。  
  
-   默认情况下，Visual C++ 2010 中禁用对三元祖的支持。 使用 /Zc: trigraphs 编译器选项以启用三元祖支持。 三元祖由两个连续的问号（“??”）后跟一个唯一的第三个字符组成。 编译器将三元祖替换为相应的标点字符。 例如，编译器会将三元祖“??=”替换为字符“#”。 可以在使用字符集的 C 源文件中使用三元祖，该字符集不包含一些标点字符的方便图形表示。  
  
-   链接器不再支持针对 Windows 98 的优化。 如果指定 /OPT:WIN98 或 /OPT:NOWIN98，则 /OPT（优化）选项将生成编译时错误。  
  
-   已更改由 RuntimeLibrary 和 DebugInformationFormat 版本系统属性指定的默认编译器选项。 默认情况下，在由 Visual C++ 版本 7.0 到 10.0 创建的项目中指定这些版本属性。 如果迁移由 Visual C++ 6.0 创建的项目，请考虑是否指定这些属性的值。  
  
-   在 Visual C++ 2010 中，RuntimeLibrary = MultiThreaded (/MD) 且 DebugInformationFormat = ProgramDatabase (/Zi)。 在 Visual C++ 9.0 中，RuntimeLibrary = MultiThreaded (/MT) 且 DebugInformationFormat = Disabled。  
  
### <a name="clr"></a>CLR  
  
-   Microsoft C# 和 Visual Basic 编译器现在可以生成非主互操作程序集 (no-PIA)。 no-PIA 程序集可以使用 COM 类型，无需部署相关的主互操作程序集 (PIA)。 使用 Visual C# 或 Visual Basic 生成的 no-PIA 程序集时，必须在引用使用该库的任何 no-PIA 程序集之前，在编译命令中引用 PIA 程序集。  
  
### <a name="visual-c-projects-and-msbuild"></a>Visual C++ 项目和 MSBuild  
  
-   Visual C++ 项目现在基于 MSBuild 工具。 因此，项目文件使用新的 XML 文件格式和 .vcxproj 文件后缀。 Visual C++ 2010 会自动将项目文件从 Visual Studio 的早期版本转换为新的文件格式。 如果现有项目依赖于以前的生成工具 VCBUILD.exe 或项目文件后缀 .vcproj，则会受到影响。  
  
-   在早期版本中，Visual C ++ 支持对属性表进行后期求值。 例如，父属性表可以导入子属性表，且父级可以使用子级中定义的变量定义其他变量。 后期求值使父级在导入子属性表之前就可以使用子变量。 Visual C++ 2010 中，项目表变量在其被定义前不能使用，因为 MSBuild 仅支持早期求值。  
  
### <a name="ide"></a>IDE  
  
-   应用程序终止对话框不再终止应用程序。 在早期版本中，当 abort() 或 terminate() 函数关闭应用程序的零售内部版本时，C 运行时库将在控制台窗口或对话框中显示应用程序终止消息。 此消息的一部分为“该应用程序已请求运行时以非常规方式终止它。 有关详细信息，请与应用程序的支持团队联系。”                 应用程序终止消息是多余的，因为 Windows 随后会显示当前的终止处理程序，通常为 Windows 错误报告 (Dr.Watson) 对话框或 Visual Studio 调试程序。 从 Visual Studio 2010 开始，C 运行时库不显示此消息。 此外，运行时阻止应用程序在调试器启动前结束。 只有在依赖应用程序终止消息的以前行为的情况下，这才是一项重大更改。  
  
-   特别对于 Visual Studio 2010，IntelliSense 不适用于 C++/CLI 代码或属性，“查找所有引用”不适用于局部变量，并且代码模型不从导入的程序集中检索类型名称或将类型解析为其完全限定名称。  
  
### <a name="libraries"></a>库  
  
-   SafeInt 类包括在 Visual C++ 中，不再需要单独下载。 仅当已开发同样名为“SafeInt”的类时，这才是重大更改。  
  
-   库部署模型不再使用清单来查找动态链接库的特定版本。 每个动态链接库的名称中包含其版本号，可以使用该名称来查找库。  
  
-   在以前版本的 Visual Studio 中，可以重新生成运行时库。 Visual C++ 2010 不再支持生成你自己的 C 运行时库文件的副本。  
  
### <a name="standard-library"></a>标准库  
  
-   许多其他头文件不再自动包括 \<iterator> 标头。 如果需要针对在现有项目中定义的独立迭代器的支持，且该标头依赖于以前的生成工具 VCBUILD.exe 或项目文件后缀 .vcproj.interator> 标头，请显式包括该标头。  
  
-   在 \<algorithm> 标头中，已删除 checked_* 和 unchecked_\* 函数。 在 \<iterator>> 标头中，已删除 checked_iteratorclass 且添加 unchecked_array_iterator 类。  
  
-   删除 CComPtr::CComPtr(int) 构造函数。 该构造函数允许从 NULL 宏构造 CComPtr 对象（但这是不必要的），并允许从非零整数构造无意义结构。  
  
     CComPtr 仍然可以从 NULL（其定义为 0）构造，但如果从文本 0 之外的整数构造，将失败。 请改用 nullptr。  
  
-   删除以下 ctype 成员函数：ctype::_Do_narrow_s、ctype::_Do_widen_s、ctype::_narrow_s 和 ctype::_widen_s。 如果应用程序使用这些成员函数之一，必须将其替换为相应的非安全版本：ctype:: do_narrow、ctype:: do_widen、ctype:: narrow、ctype:: widen。  
  
### <a name="crt-mfc-and-atl-libraries"></a>CRT、MFC 和 ATL 库  
  
-   删除生成 CRT、MFC 和 ATL 库的用户支持。 例如，不提供相应的 nmake 文件。                 但是，用户仍然可以访问这些库的源代码。 并且，Visual C++ 团队博客可能会发布关于 MSBuild 选项的文档，Microsoft 用这些 MSBuild 选项来构建这些库。  
  
-   删除 IA64 的 MFC 支持。 但是，仍提供对 IA64 上 CRT 和 ATL 的支持。  
  
-   在 MFC 模块定义 (.def) 文件中，序号不能再重复使用。 此更改意味着次要版本之间的序号不会有所不同，并且服务包和快速修复工程版本的二进制文件兼容性将得到改进。  
  
-   新的虚拟函数已添加到 CDocTemplate 类。 此新虚拟函数是 [CDocTemplate 类](../mfc/reference/cdoctemplate-class.md)。 以前版本的 OpenDocumentFile 有两个参数。 新版本有三个参数。 若要支持重启管理器，从 CDocTemplate 派生的任何类必须实现有三个参数的版本。 新参数为 bAddToMRU。  
  
### <a name="macros-and-environment-variables"></a>宏和环境变量  
  
-   不再支持环境变量 __MSVCRT_HEAP_SELECT。 删除此环境变量且无替代项。  
  
### <a name="microsoft-macro-assembler-reference"></a>Microsoft 宏汇编程序参考  
  
-   从 Microsoft 宏汇编程序参考编译器删除多个指令。 删除的指令是 .186、.286、.286P、.287、.8086、.8087 和 .NO87。  
  
## <a name="visual-c-2008-breaking-changes"></a>Visual C++ 2008 重大更改  
  
### <a name="compiler"></a>编译器  
  
-   不再支持 Windows 95、Windows 98、Windows ME 和 Windows NT 平台。 这些操作系统已从目标平台列表中删除。  
  
-   编译器不再支持与 ATL Server 直接关联的多个属性。 不再支持以下属性：  
  
    -   perf_counter  
  
    -   perf_object  
  
    -   perfmon  
  
    -   request_handler  
  
    -   soap_handler  
  
    -   soap_header  
  
    -   soap_method  
  
    -   tag_name  
  
### <a name="visual-c-projects"></a>Visual C++ 项目  
  
-   从 Visual Studio 的早期版本升级项目时，可能需要修改 WINVER 和 _WIN32_WINNT 宏，使其值大于或等于 0x0500。  
  
-   从 Visual Studio 2008 开始，新建项目向导没有创建 C++ SQL Server 项目的选项。 使用 Visual Studio 早期版本创建的 SQL Server 项目仍将编译并正常运行。  
  
-   Windows API 头文件 Winable.h 已删除。 改为包含 Winuser.h。  
  
-   Windows API 库 Rpcndr.lib 已删除。 改为与 rpcrt4.lib 链接。  
  
### <a name="crt"></a>CRT  
  
-   删除对 Windows 95、Windows 98、Windows Millennium Edition 和 Windows NT 4.0 的支持。  
  
-   已删除以下全局变量：  
  
    -   _osplatform  
  
    -   _osver  
  
    -   _winmajor  
  
    -   _winminor  
  
    -   _winver  
  
-   已删除下列函数。 改为使用 Windows API 函数 GetVersion 或 GetVersionEx：  
  
    -   _get_osplatform  
  
    -   _get_osver  
  
    -   _get_winmajor  
  
    -   _get_winminor  
  
    -   _get_winver  
  
-   已更改 SAL 注释的语法。 有关详细信息，请参见 [SAL 注释](../c-runtime-library/sal-annotations.md)。  
  
-   IEEE 筛选器现在支持 SSE 4.1 指令集。 有关详细信息，请参阅 [_fpieee_flt](../c-runtime-library/reference/fpieee-flt.md)_fpieee_flt。  
  
-   Visual Studio 附带的 C 运行时库将不再依赖于系统 DLL msvcrt.dll。  
  
### <a name="standard-library"></a>标准库  
  
-   删除对 Windows 95、Windows 98、Windows Millennium Edition 和 Windows NT 4.0 的支持。  
  
-   在已定义 _HAS_ITERATOR_DEBUGGING 的调试模式下（Visual Studio 2010 之后由 [_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md) 取代）进行编译时，现在如果迭代器尝试超过基础容器的边界递增或递减，应用程序将断言。  
  
-   现在堆栈类的成员变量 c 声明为受保护。 以前，此成员变量声明为公用。  
  
-   更改 Money_get:: do_get 的行为。 以前，分析比 frac_digits 要求的小数位数更多的货币金额时，do_get 通常使用全部。 现在，do_get 在使用大多数 frac_digits 字符后停止分析。  
  
### <a name="atl"></a>ATL  
  
-   ATL 无法不依赖 CRT 生成。 在 Visual Studio 的早期版本中，可以使用 #define ATL_MIN_CRT 使 ATL 项目对 CRT 的依赖最小化。 在 Visual C++ 2008 中，无论是否定义 ATL_MIN_CRT，所有 ATL 项目对 CRT 的依赖程度都为最小。  
  
-   ATL 服务器基本代码已在 CodePlex 上作为共享源项目发布，不作为 Visual Studio 的一部分安装。 保留来自 atlenc.h 的数据编码和解码类以及来自 atlutil.h 和 atlpath.h 的实用工具函数和类，它们属于 ATL 库。 与 ATL 服务器相关联的多个文件不再属于 Visual Studio。  
  
-   某些函数不再包含在 DLL 中。 它们仍位于导入库中。 这不会影响静态使用这些函数的代码。 仅影响动态使用这些函数的代码。  
  
-   由于安全原因，已弃用宏 PROP_ENTRY 和 PROP_ENTRY_EX，替换为宏 PROP_ENTRY_TYPE 和 PROP_ENTRY_TYPE_EX。  
  
### <a name="atlmfc-shared-classes"></a>ATL/MFC 共享类  
  
-   ATL 无法不依赖 CRT 生成。 在 Visual Studio 的早期版本中，可以使用 #define ATL_MIN_CRT 使 ATL 项目对 CRT 的依赖最小化。 在 Visual C++ 2008 中，无论是否定义 ATL_MIN_CRT，所有 ATL 项目对 CRT 的依赖程度都为最小。  
  
-   ATL 服务器基本代码已在 CodePlex 上作为共享源项目发布，不作为 Visual Studio 的一部分安装。 保留来自 atlenc.h 的数据编码和解码类以及来自 atlutil.h 和 atlpath.h 的实用工具函数和类，它们属于 ATL 库。 与 ATL 服务器相关联的多个文件不再属于 Visual Studio。  
  
-   某些函数不再包含在 DLL 中。 它们仍位于导入库中。 这不会影响静态使用这些函数的代码。 仅影响动态使用这些函数的代码。  
  
### <a name="mfc"></a>MFC  
  
-   CTime 类：CTime 类现在接受从 1900/1/1 C.E 开始的日期。 而不是 1970/1/1 C.E。              
-   MFC 对话框中控件的 Tab 键顺序：如果按 Tab 键顺序插入 MFC ActiveX 控件，则 MFC 对话框中多个控件的正确 Tab 键顺序会受到干扰。 此更改可以解决该问题。  
  
     例如，创建具有 1 个 ActiveX 控件和多个编辑控件的 MFC 对话框应用程序。 将 ActiveX 控件放置在编辑控件的 Tab 键顺序的中间。 启动应用程序，单击其 Tab 键顺序在 ActiveX 控件之后的编辑控件，然后单击 Tab。在此更改前，焦点将转到 ActiveX 控件后的编辑控件，而不是 Tab 键顺序中的下一个编辑控件。  
  
-   CFileDialog 类：CFileDialog 类的自定义模板无法自动移植到 Windows Vista。 该模板仍然可用，但将不具有 Windows Vista 样式对话框的其他功能或外观。  
  
-   CWnd 类和 CFrameWnd 类：CWnd::GetMenuBarInfo 方法已删除。  
  
     CFrameWnd::GetMenuBarInfo 方法现在是非虚拟方法。 有关详细信息，请参阅 Windows SDK 中的 GetMenuBarInfo 函数。  
  
-   MFC ISAPI 支持：MFC 不再支持使用 Internet 服务器应用程序编程接口 (ISAPI) 生成应用程序。 若要生成 ISAPI 应用程序，请直接调用 ISAPI 扩展。  
  
-   弃用的 ANSI API：已弃用某些 MFC 方法的 ANSI 版本。 请在以后的应用程序中使用这些方法的 Unicode 版本。 有关详细信息，请参阅“Windows Vista 公共控件的生成要求”。  
  
## <a name="visual-c-2005-breaking-changes"></a>Visual C++ 2005 重大更改  
  
### <a name="crt"></a>CRT  
  
-   已弃用许多函数。 请参阅“弃用的 CRT 函数”。  
  
-   现在，许多函数验证其参数，如果给定参数无效，则停止执行。 这可能会中断传递无效参数并依赖函数将其忽略或返回错误代码的代码。 请参阅“参数验证”。  
  
-   现在，文件描述符值 -2 用于指示 stdout 和 stderr 不可用于输出，例如，在没有控制台窗口的 Windows 应用程序中。 以前使用的值是 -1。 有关详细信息，请参阅 [_fileno](../c-runtime-library/reference/fileno.md)。  
  
-   删除单线程 CRT 库、libc.lib 和 libcd.lib。 使用多线程 CRT 库。 不再支持 /ML 编译器标志。 在多线程代码和单线程代码之间的性能差异可能很大的情景中，添加了一些函数的非锁定版本。  
  
-   为了更符合标准，删除了 pow、double pow(int, int) 的重载。  
  
-   任何 printf 系列函数中不再默认支持 %n 格式说明符，因为这在本质上是不安全的。 如果遇到 %n，默认行为是调用无效参数处理程序。 若要启用 %n 支持，请使用 _set_printf_count_output，也可以使用 see_get_printf_count_output。  
  
-   现在，sprintf 打印带符号的零的负号。  
  
-   已更改 swprintf 以符合标准；它现在需要大小参数。 已弃用不带大小参数的 swprintf 格式。  
  
-   删除 _set_security_error_handler。 删除对该函数的任何调用；默认处理程序是一种处理安全错误的更安全方法。  
  
-   time_t 现在是 64 位值（除非已定义 _USE_32BIT_TIME_T）。  
  
-   按照 C 标准的规定，如果成功，_spawn 和 _wspawn 函数现在保持 errno 不变。  
  
-   RTC 现在默认使用宽字符。  
  
-   对于使用 /CLR 或 /CLR:PURE 编译的应用程序，已弃用浮点控制字支持函数。 受影响的函数是 _clear87、_clearfp、_control87、_controlfp、_fpreset、_status87、_statusfp。 可以通过定义 _CRT_MANAGED_FP_NO_DEPRECATE 来禁用弃用警告，但在托管代码中使用这些函数是不可预测且不受支持的。  
  
-   一些函数现在返回 const 指针。 可以通过定义 _CONST_RETURN 恢复旧的非 const 行为。 受影响的函数是  
  
    1.  memchr、wmemchr  
  
    2.  strchr、wcschr、_mbschr、_mbschr_l  
  
    3.  strpbrk、wcspbrk、_mbspbrk、_mbspbrk_l  
  
    4.  strrchr、wcsrchr、_mbsrchr、_mbsrchr_l  
  
    5.  strstr、wcsstr、_mbsstr、_mbsstr_l  
  
-   与 Setargv.obj 或 Wsetargv.obj 链接时，不再可能通过将通配符字符放在双引号中来抑制命令行上的通配符字符的扩展。 有关详细信息，请参阅[扩展通配符参数](../c-language/expanding-wildcard-arguments.md)。  
  
### <a name="standard-library-2005"></a>标准库（2005 年）  
  
-   异常类（位于 \<exception> 标头中）已移动到 std 命名空间。 在早期版本中，此类位于全局命名空间中。 要解决指示无法找到异常类的错误，请将以下 using 语句添加到代码中：using namespace std;  
  
-   调用 valarray::resize() 时，valarray 的内容将会丢失，并将替换为默认值。 resize() 方法旨在重新初始化 valarray，而不是使其像向量一样动态增长。  
  
-   调试迭代器：使用 C 运行时库的调试版本生成和错误使用迭代器的应用程序可能会在运行时开始看到断言。 若要禁用这些断言，必须将 _HAS_ITERATOR_DEBUGGING（Visual Studio 2010 之后由 [_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md) 取代）定义为 0。 有关详细信息，请参阅[调试迭代器支持](../standard-library/debug-iterator-support.md)  
  
## <a name="visual-c-net-2003-breaking-changes"></a>Visual C++ .NET 2003 重大更改  
  
### <a name="compiler"></a>编译器  
  
-   现在，已定义的预处理器指令 (C2004) 需要右括号。  
  
-   显式专用化不再从主模板中查找模板参数（[编译器错误 C2146](../error-messages/compiler-errors-1/compiler-error-c2146.md)）。  
  
-   只能通过类 (B) 的成员函数访问受保护成员 (n)，类 (B) 继承自 (n) 是其成员的类 (A)（[编译器错误 C2247](../error-messages/compiler-errors-1/compiler-error-c2247.md)）。  
  
-   现在，编译器中改进的可访问性检查检测不可访问的基类（[编译器错误 C2248](../error-messages/compiler-errors-1/compiler-error-c2248.md)）。  
  
-   如果析构函数和/或复制构造函数不可访问，则无法捕获异常（C2316）。  
  
-   不再允许函数指针的默认参数（[编译器错误 C2383](../error-messages/compiler-errors-1/compiler-error-c2383.md)）。  
  
-   静态数据成员无法通过派生类初始化（[编译器错误 C2477](../error-messages/compiler-errors-1/compiler-error-c2477.md)）。  
  
-   根据标准，现在不允许 Typedef 的初始化，并且将生成编译器错误（[编译器错误 C2513](../error-messages/compiler-errors-2/compiler-error-c2513.md)）。  
  
-   现在，bool 是正确的类型（[编译器错误 C2632](../error-messages/compiler-errors-2/compiler-error-c2632.md)）。  
  
-   现在，UDC 可以使用重载的运算符创建多义性 ([C2666](../error-messages/compiler-errors-2/compiler-error-c2666.md))。  
  
-   现在将多个表达式视为有效的空指针常量（[编译器错误 C2668](../error-messages/compiler-errors-2/compiler-error-c2668.md)）。  
  
-   现在，在以前编译器暗含的位置需要使用 template<>（[编译器错误 C2768](../error-messages/compiler-errors-2/compiler-error-c2768.md)）。  
  
-   如果已经通过模板类专用化显式专用化函数，则类外的成员函数的显式专用化无效（[编译器错误 C2910](../error-messages/compiler-errors-2/compiler-error-c2910.md)）。  
  
-   不再允许浮点非类型模板参数（[编译器错误 C2993](../error-messages/compiler-errors-2/compiler-error-c2993.md)）。  
  
-   不允许类模板作为模板类型参数 (C3206)。  
  
-   不再将友元函数名称引入内含命名空间（[编译器错误 C3767](../error-messages/compiler-errors-2/compiler-error-c3767.md)）。  
  
-   编译器不再接受宏中的额外逗号 (C4002)。  
  
-   使用 () 形式的初始化表达式构造的 POD 类型的对象将被默认初始化 (C4345)。  
  
-   如果将依赖名称视为类型，则现在需要 typename（[编译器警告（等级 1）C4346](../error-messages/compiler-warnings/compiler-warning-level-1-c4346.md)）。  
  
-   以前错误地被视为模板专用化的函数，现在不再被视为模板专用化 (C4347)。  
  
-   静态数据成员无法通过派生类初始化 (C4356)。  
  
-   类模板专用化需要在用于返回类型之前定义（[编译器警告（等级 3）C4686](../error-messages/compiler-warnings/compiler-warning-level-3-c4686.md)）。  
  
-   现在，编译器会报告无法访问的代码 (C4702)。  
  
## <a name="see-also"></a>请参阅  
[Visual Studio 中 Visual C++ 的新增功能](../what-s-new-for-visual-cpp-in-visual-studio.md)
