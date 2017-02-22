---
title: "链接器工具错误 LNK2001 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "LNK2001"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "LNK2001"
ms.assetid: dc1cf267-c984-486c-abd2-fd07c799f7ef
caps.latest.revision: 21
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 21
---
# 链接器工具错误 LNK2001
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

无法解析的外部符号“symbol”  
  
 代码引用了链接器无法在库和对象文件中找到的内容（如函数、变量或标签）。  
  
 该错误消息之后为错误 [LNK1120](../../error-messages/tool-errors/linker-tools-error-lnk1120.md)。  
  
 **可能的原因**  
  
-   在从 Visual C\+\+ 2003 升级托管库或 Web 服务项目时，**\/Zl** 编译器选项将添加到**“命令行”**属性页中。  这将导致 LNK2001。  
  
     若要消除此错误，请将 msvcrt.lib 和 msvcmrt.lib 添加到链接器的“附加依赖项”属性中。  或者，从**“命令行”**属性页中移除 **\/Zl**。  有关更多信息，请参见[\/Zl（省略默认库名）](../../build/reference/zl-omit-default-library-name.md)和[如何：打开项目属性页](../../misc/how-to-open-project-property-pages.md)。  
  
-   代码请求的内容不存在（例如，符号拼写错误或使用错误的大小写）。  
  
-   代码请求的内容错误（使用的是混合版本的库，一些库来自产品的一个版本，而其他则来自另一个版本）。  
  
 **具体原因**  
  
 **代码问题**  
  
-   如果 LNK2001 诊断文本报告 `__check_commonlanguageruntime_version` 是无法解析的外部符号，则请参见 [LNK2019](../../error-messages/tool-errors/linker-tools-error-lnk2019.md) 获得有关如何解决该问题的信息。  
  
-   成员模板的定义超出了类的范围。  Visual C\+\+ 的一个限制是，成员模板的定义必须完全位于封闭类内。  有关 LNK2001 和成员模板的更多信息，请参见知识库文章 Q239436。  
  
-   代码或模块定义 \(.def\) 文件中的大小写不匹配会导致 LNK2001。  例如，当在一个 C\+\+ 源文件中将一个变量命名为 `var1`，并尝试在另一个源文件中以 `VAR1` 访问该变量时。  
  
-   如果项目使用[函数内联](../../error-messages/tool-errors/function-inlining-problems.md)，但在 .cpp 文件而非头文件中定义函数，则会导致 LNK2001。  
  
-   从 C\+\+ 程序调用 C 函数但不使用 `extern` "C"（这导致编译器使用 C 命名约定）会导致 LNK2001。  编译器选项 [\/Tp](../../build/reference/tc-tp-tc-tp-specify-source-file-type.md) 和 [\/Tc](../../build/reference/tc-tp-tc-tp-specify-source-file-type.md) 使编译器将文件分别编译为 C\+\+ 或 C，与文件扩展名无关。  这些选项会导致函数名与您所期望的名称不同。  
  
-   尝试引用没有外部链接的函数或数据会导致 LNK2001。  在 C\+\+ 中，内联函数和 `const` 数据具有内部链接，除非被显式指定为 `extern`。  
  
-   [缺少函数主体或变量](../../error-messages/tool-errors/missing-function-body-or-variable.md)会导致 LNK2001。  如果只有函数原型或 `extern` 声明，编译器继续运行而不会出现任何错误，但由于没有保留函数代码或变量空间，链接器将无法解析地址调用或变量引用。  
  
-   调用参数类型与函数声明中的参数类型不匹配的函数会导致 LNK2001。  [名称修饰](../../error-messages/tool-errors/name-decoration.md)将函数参数合并到最终修饰函数名中。  
  
-   错误包含的原型导致编译器需要没有提供的函数体，这样会导致 LNK2001。  如果同时具有函数 `F` 的类实现和非类实现，请注意 C\+\+ 范围解析规则。  
  
-   在使用 C\+\+ 时，将函数原型包含在类定义中但未能[包含实现](../../error-messages/tool-errors/missing-function-body-or-variable.md)（该类的此函数的实现）会导致 LNK2001。  
  
-   尝试从抽象基类的构造函数或析构函数调用纯虚函数会导致 LNK2001。  纯虚函数没有基类实现。  
  
-   尝试在函数范围外使用用该函数声明的变量（[局部变量](../../error-messages/tool-errors/automatic-function-scope-variables.md)）会导致 LNK2001。  
  
-   在生成 ATL 项目的发布版本时，指示需要 CRT 启动代码。  若要修复，请执行下列操作之一：  
  
    -   将 `_ATL_MIN_CRT` 从预处理器定义的列表中移除，以允许包括 CRT 启动代码。  有关更多信息，请参见[常规配置设置属性页](../../ide/general-property-page-project.md)。  
  
    -   如果可能，移除对需要 CRT 启动代码的 CRT 函数的调用，  而是使用它们的 Win32 等效函数。  例如，使用 `lstrcmp`，而不要使用 `strcmp`。  需要 CRT 启动代码的已知函数是一些字符串和浮点函数。  
  
 **编译和链接问题**  
  
-   项目缺少对库 \(.LIB\) 或对象 \(.OBJ\) 文件的引用。  有关更多信息，请参见[用作链接器输入的 .lib 文件](../../build/reference/dot-lib-files-as-linker-input.md)。  
  
-   如果使用 [\/NODEFAULTLIB](../../build/reference/nodefaultlib-ignore-libraries.md) 或 [\/Zl](../../build/reference/zl-omit-default-library-name.md)，包含所需代码的库将不会链接到项目，除非已显式地包括了这些库。（在使用 **\/clr** 或 **\/clr:pure** 进行编译时，您将看到对 .cctor 的引用；有关更多信息，请参见 [混合程序集的初始化](../../dotnet/initialization-of-mixed-assemblies.md)。）  
  
-   如果正在使用 Unicode 和 MFC，如果没有创建 `wWinMainCRTStartup` 的入口点，将在 `_WinMain@16` 上得到无法解析的外部对象；请使用 [\/ENTRY](../../build/reference/entry-entry-point-symbol.md)。  请参见 [Unicode 编程摘要](../../text/unicode-programming-summary.md)。  
  
     有关更多信息，请参见下列位于 MSDN Library 中的知识库文章。  在 MSDN Library 中，单击**“搜索”**选项卡，将文章编号或文章标题粘贴到文本框中，然后单击**“列出主题”**。  如果按文章编号搜索，请确保清除**“仅搜索标题”**选项。  
  
    -   Q125750   “PRB: Error LNK2001: '\_WinMain@16': Unresolved External Symbol”  
  
    -   Q131204   “PRB: Wrong Project Selection Causes LNK2001 on \_WinMain@16”  
  
    -   Q100639   “Unicode Support in the Microsoft Foundation Class Library”  
  
    -   Q291952    “PRB: Link Error LNK2001: Unresolved External Symbol \_main”  
  
-   将用 \/MT 编译的代码与库 LIBC.lib 链接会在 `_beginthread`、`_beginthreadex`、`_endthread` 和 `_endthreadex` 上导致 LNK2001。  
  
-   链接需要多线程库的代码（任何 MFC 代码或用 [\/MT](../../build/reference/md-mt-ld-use-run-time-library.md) 编译的代码）会在 [\_beginthread](../../c-runtime-library/reference/beginthread-beginthreadex.md)、`_beginthreadex`、[\_endthread](../../c-runtime-library/reference/endthread-endthreadex.md) 和 `_endthreadex` 上导致 LNK2001。  有关更多信息，请参见下列知识库文章：  
  
    -   Q126646“PRB: Error Msg: LNK2001 on \_\_beginthreadex and \_\_endthreadex”  
  
    -   Q128641“INFO: \/Mx Compiler Options and the LIBC, LIBCMT, MSVCRT Libs”  
  
    -   Q166504“PRB: MFC and CRT Must Match in debug\/release and static\/dynamic”  
  
-   在用 **\/MD** 进行编译时，因为所有的运行时现在都存放在一个 DLL 中，所以源中的“func”引用在对象中变为“`__imp__func`”引用。  如果尝试与 LIBC.lib 或 LIBCMT.lib 静态库链接，则将在 `__imp__func` 上得到 LNK2001。  当不用 \/MD 进行编译时，如果尝试与 MSVCxx.lib 链接，则并非总是得到 LNK2001，但可能会有其他问题。  
  
-   在生成应用程序的调试版本时与发布模式库链接会导致 LNK2001。  同样，使用 **\/Mxd** 选项（**\/MTd** 或 **\/MDd**）和\/或定义 `_DEBUG`，然后再与版本库链接，将可能会产生无法解析的外部对象（同时还会出现其他问题）。  将发布模式生成与调试库链接同样会导致类似问题。  
  
-   将 Microsoft 库版本和编译器产品版本混合可能会有问题。  新编译器版本的库可能包含早期版本的库中没有的新符号。  可能需要更改搜索路径中的目录顺序，或将它们更改为指向当前版本。  
  
     使用库文件选择下的“工具”&#124;“选项”&#124;“项目”&#124;“VC\+\+ 目录”对话框，可以更改搜索顺序。  项目的“属性页”对话框中的“链接器”文件夹可能也包含可能已过期的路径。  
  
     当安装了新的 SDK（可能在不同的位置），但没有将搜索顺序更新为指向新位置时，可能会出现此问题。  通常情况下，应将新 SDK 的 include 目录和 lib 目录的路径放在默认 Visual C\+\+ 位置的前面。  另外，包含嵌入路径的项目可能仍然指向旧路径，这些路径是有效的，但对于安装到不同位置的新版本所添加的新功能已过期。  
  
-   编译器供应商之间、甚至同一编译器的不同版本之间当前没有 [C\+\+ 命名](../../error-messages/tool-errors/name-decoration.md)标准。  因此，链接用其他编译器编译的对象文件可能无法生成相同的命名方案，从而导致错误 LNK2001。  
  
-   在不同模块上[混合内联和非内联编译选项](../../error-messages/tool-errors/function-inlining-problems.md)会导致 LNK2001。  如果创建 C\+\+ 库时打开了函数内联（**\/Ob1** 或 **\/Ob2**），但描述函数的相应头文件的内联是关闭的（没有 `inline` 关键字），则将发生此错误。  若要防止此问题，请在要包含到其他文件中的头文件中用 `inline` 定义内联函数。  
  
-   如果使用 `#pragma inline_depth` 编译器指令，请确保具有 [设置为 2 或更大的值](../../error-messages/tool-errors/function-inlining-problems.md)，并确保使用 [\/Ob1](../../build/reference/ob-inline-function-expansion.md) 或 [\/Ob2](../../build/reference/ob-inline-function-expansion.md) 编译器选项。  
  
-   在创建纯资源 DLL 时省略 LINK 选项 \/NOENTRY 将导致 LNK2001。  
  
-   使用不正确的 \/SUBSYSTEM 或 \/ENTRY 设置会导致 LNK2001。  例如，如果编写基于字符的应用程序（控制台应用程序）并指定 \/SUBSYSTEM:WINDOWS，您将得到无法解析的 `WinMain` 外部对象。  有关这些选项和入口点的更多信息，请参见 [\/SUBSYSTEM](../../build/reference/subsystem-specify-subsystem.md) 和 [\/ENTRY](../../build/reference/entry-entry-point-symbol.md) 链接器选项。  
  
 **导出问题**  
  
-   当将应用程序从 16 位移植到 32 位或 64 位时，会发生 LNK2001。  当前的模块定义 \(.def\) 文件语法要求 `__cdecl`、`__stdcall` 和 `__fastcall` 函数列在 EXPORTS 节中，并且不带下划线（不修饰）。  这不同于 16 位语法，这些函数在 16 位语法中列出时必须带下划线（修饰）。  有关更多信息，请参见模块定义文件 [EXPORTS](../../build/reference/exports.md) 节的说明。  
  
-   在 .def 文件中列出但未找到的任何导出将导致 LNK2001。  这可能是因为导出不存在、拼写错误或使用了 C\+\+ 修饰名（.def 文件不采用修饰名）。  
  
 **解释输出**  
  
 如果符号无法解析，通过下列指南可获得有关函数的信息：  
  
 在 x86 平台上，用 C 编译的名称或 C\+\+ 中的 extern "C" 名称的调用约定修饰是：  
  
 `__cdecl`  
 函数具有下划线 \(\_\) 前缀。  
  
 `__stdcall`  
 函数具有下划线 \(\_\) 前缀和 @ 后缀，后跟堆栈上参数的双倍字长对齐大小。  
  
 `__fastcall`  
 函数具有 @ 前缀和 @ 后缀，后跟堆栈上参数的双倍字长对齐大小。  
  
 使用 undname.exe 获取修饰名的未修饰格式。  
  
 有关上面列出的某些原因的更多信息，请参见[名称修饰](../../error-messages/tool-errors/name-decoration.md)。