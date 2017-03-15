---
title: "链接器工具错误 LNK2001 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- LNK2001
dev_langs:
- C++
helpviewer_keywords:
- LNK2001
ms.assetid: dc1cf267-c984-486c-abd2-fd07c799f7ef
caps.latest.revision: 21
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 9dee257bec0f09bd729bf10c4a1468ecb20dfa61
ms.openlocfilehash: 3629075e5659cb89ab751b011f3ce2cbf89397cc
ms.lasthandoff: 02/24/2017

---
# <a name="linker-tools-error-lnk2001"></a>链接器工具错误 LNK2001
无法解析的外部符号"symbol"  
  
 代码引用链接器无法在库和对象文件中找到的内容 （如函数、 变量或标签）。  
  
 此错误消息之后为致命错误[LNK1120](../../error-messages/tool-errors/linker-tools-error-lnk1120.md)。  
  
 **可能的原因**  
  
-   从 Visual c + + 2003 中，升级托管的库或 web 服务项目时**/Zl**编译器选项添加到**命令行**属性页。 这将导致 LNK2001。  
  
     若要解决此错误，或者添加 msvcrt.lib 和 msvcmrt.lib 链接器的附加依赖项属性。 或者，删除**/Zl**从**命令行**属性页。 有关详细信息，请参阅[/Zl （省略默认库名）](../../build/reference/zl-omit-default-library-name.md)和[使用项目属性](../../ide/working-with-project-properties.md)。  
  
-   代码的请求的不存在 （符号拼写错误，或使用错误的大小写，例如）。  
  
-   代码请求的内容错误 （使用的混合的版本的库，有些是从一个版本的产品，而其他则来自另一个版本）。  
  
 **具体的原因**  
  
 **编码问题**  
  
-   如果 LNK2001 诊断文本报告`__check_commonlanguageruntime_version`是无法解析的外部符号，请参阅[LNK2019](../../error-messages/tool-errors/linker-tools-error-lnk2019.md)有关如何解决的信息。  
  
-   成员模板的定义是在类的外部。 Visual c + + 具有顺序成员模板必须完全定义封闭类中的限制。 请参阅知识库文章 Q239436 有关 LNK2001 和成员模板的详细信息。  
  
-   大小写不匹配在您的代码或模块定义 (.def) 文件可能导致 LNK2001。 例如，如果名为变量`var1`在一个 c + + 源文件，并尝试访问其作为`VAR1`在另一个。  
  
-   使用的项目[函数内联](../../error-messages/tool-errors/function-inlining-problems.md)尚未在.cpp 文件中定义的函数，而不是在标头文件会导致 LNK2001。  
  
-   从 c + + 程序中调用 C 函数，而无需使用`extern`"C"（这将导致编译器使用 C 命名约定） 会导致 LNK2001。 编译器选项[/Tp](../../build/reference/tc-tp-tc-tp-specify-source-file-type.md)和[/Tc](../../build/reference/tc-tp-tc-tp-specify-source-file-type.md)会导致编译器文件分别编译为 c + + 或 C，而不考虑文件扩展名。 这些选项会导致与您期望的不同的函数名称。  
  
-   正在尝试引用函数或不具有外部链接的数据会导致 LNK2001。 在 c + + 内联函数和`const`数据具有内部链接，除非显式指定为`extern`。  
  
-   一个[缺少函数体或变量](../../error-messages/tool-errors/missing-function-body-or-variable.md)会导致 LNK2001。 只有函数原型或`extern`声明编译器可以继续未生成错误，但由于没有函数代码或变量保留的空间，链接器将无法解析到某个地址的调用或对变量引用。  
  
-   调用的函数具有与函数声明中不匹配的参数类型会导致 LNK2001。 [名称修饰](../../error-messages/tool-errors/name-decoration.md)将函数的参数合并到最终修饰的函数名。  
  
-   错误包含的原型，这会使编译器需要未提供的函数体可以导致 LNK2001。 如果您有一个类和非类的函数实现的`F`，请注意 c + + 范围解析规则。  
  
-   在使用 c + + 时，在类定义中包括函数原型和故障转移到[包括实施](../../error-messages/tool-errors/missing-function-body-or-variable.md)个此类函数会导致 LNK2001。  
  
-   尝试从构造函数或析构函数的抽象基类调用纯虚函数会导致 LNK2001。 一个纯虚函数不具有基类实现。  
  
-   尝试使用一个变量在函数内声明 ([局部变量](../../error-messages/tool-errors/automatic-function-scope-variables.md)) 之外，该函数的作用域会导致 LNK2001。  
  
-   在生成的 ATL 项目的发布版本时，表示需要 CRT 启动代码。 若要修复，请执行以下操作，  
  
    -   删除`_ATL_MIN_CRT`从列表中预处理器定义以允许 CRT 启动代码以将包括在内。 请参阅[常规配置设置属性页](../../ide/general-property-page-project.md)有关详细信息。  
  
    -   如果可能，请移除对需要 CRT 启动代码的 CRT 函数的调用。 相反，使用 Win32 等效物。 例如，使用`lstrcmp`而不是`strcmp`。 需要 CRT 启动代码的已知的函数是一些字符串和浮点函数。  
  
 **编译和链接问题**  
  
-   项目缺少对库的引用 (。LIB) 或对象 (。OBJ) 文件。 请参阅[用作链接器输入的.lib 文件](../../build/reference/dot-lib-files-as-linker-input.md)有关详细信息。  
  
-   如果您使用[/NODEFAULTLIB](../../build/reference/nodefaultlib-ignore-libraries.md)或[/Zl](../../build/reference/zl-omit-default-library-name.md)，包含必需的代码库链接将不会为项目除非显式包含了它们。 (使用编译时**/clr**或**/clr: pure**，您将看到对.cctor 的引用; 请参阅[初始化混合程序集的](../../dotnet/initialization-of-mixed-assemblies.md)有关详细信息。)  
  
-   如果使用 Unicode 和 MFC，您将收到有关无法解析的外部`_WinMain@16`如果你不创建到入口点`wWinMainCRTStartup`; 使用[/ENTRY](../../build/reference/entry-entry-point-symbol.md)。 请参阅[Unicode 编程摘要](../../text/unicode-programming-summary.md)。  
  
     请参阅以下知识库文章，位于 MSDN Library 中，有关详细信息。 在 MSDN 库中，单击**搜索**选项卡上，在文本框中，粘贴的文章编号或文章标题，然后单击**列出主题**。 如果您搜索的文章编号，请确保**只搜索标题**选项被清除。  
  
    -   Q125750"PRB︰ 错误 LNK2001:_WinMain@16︰ 无法解析的外部符号"  
  
    -   Q131204"PRB︰ 错误的项目所选内容上导致 LNK2001 _WinMain@16"  
  
    -   Q100639"Unicode 支持在 Microsoft 基础类库"  
  
    -   Q291952"PRB︰ 链接错误 LNK2001︰ 无法解析的外部符号 _main"  
  
-   链接与以下库 LIBC.lib 使用 /MT 编译的代码会导致 LNK2001 `_beginthread`， `_beginthreadex`， `_endthread`，和`_endthreadex`。  
  
-   链接要求多线程的库的代码 (任何 MFC 代码或使用编译的代码[/MT](../../build/reference/md-mt-ld-use-run-time-library.md)) 将导致 LNK2001 上[_beginthread](../../c-runtime-library/reference/beginthread-beginthreadex.md)， `_beginthreadex`， [_endthread](../../c-runtime-library/reference/endthread-endthreadex.md)，和`_endthreadex`。 请参阅以下知识库文章以了解详情︰  
  
    -   Q126646"PRB︰ 错误消息︰ 在 __beginthreadex LNK2001 和\__endthreadex"  
  
    -   Q128641"信息︰ /Mx 编译器选项和 LIBC、 LIBCMT、 MSVCRT Libs"  
  
    -   Q166504"PRB: MFC 和 CRT 必须在调试/发布和静态/动态匹配"  
  
-   使用编译时**/MD**，对您的源中的"func"的引用将变为一个引用"`__imp__func`"由于所有运行时现在都保留在 DLL 中的对象中。 如果您尝试与静态库 LIBC.lib 或 LIBCMT.lib 链接，您将收到有关 LNK2001 `__imp__func`。 如果您尝试在没有 /MD 的情况下编译时与 MSVCxx.lib 链接则不会始终获得 LNK2001，但您可能有其他问题。  
  
-   在生成应用程序的调试版本时，与发布模式库链接会导致 LNK2001。 同样，使用**/Mxd**选项 (**/MTd**，或**/MDd**) 和/或定义`_DEBUG`，然后与版本库链接便会提供 （还有其他问题） 可能无法解析的外部对象数量。 链接发布模式生成带有调试库也会导致类似问题。  
  
-   混合版本的 Microsoft 库和编译器产品可能会产生问题。 新的编译器版本的库可能包含不能在包括与以前版本的库中找到的新符号。 您可能想要更改的目录中的搜索路径，或更改它们的顺序，以指向当前版本。  
  
     这些工具 |选项 |项目 |VC + + 目录下对话框中，库文件的所选内容，可以更改搜索顺序。 在项目的属性页对话框中的链接器文件夹还可能包含可能已过期的路径。  
  
     （也许是到其他位置），安装新的 SDK 和搜索顺序不更新为指向新位置时，可能会出现此问题。 通常情况下，应将路径放到新的 Sdk 的 include 和 lib 目录默认 Visual c + + 位置的前面。 此外，包含嵌入的路径的项目可能仍然指向旧是有效的但已过期的新功能添加到另一个位置安装的新版本的路径。  
  
-   目前尚没有标准[c + + 命名](../../error-messages/tool-errors/name-decoration.md)编译器供应商之间、 甚至同一编译器的不同版本之间。 因此，链接用其他编译器编译的对象文件可能不会产生相同的命名方案，从而导致错误 LNK2001。  
  
-   [混合使用内联和非内联编译选项](../../error-messages/tool-errors/function-inlining-problems.md)在不同的模块，则可能导致 LNK2001。 如果打开了函数内联创建 c + + 库 (**/Ob1**或**/Ob2**) 但相应的头文件描述函数内联处于关闭状态 (没有`inline`关键字)，会出现此错误。 若要防止此问题，已定义内联函数与`inline`中要包括在其他文件中的头文件。  
  
-   如果您使用`#pragma inline_depth`编译器指令，请确保您有[2 或更高版本集的值](../../error-messages/tool-errors/function-inlining-problems.md)，并确保您使用[/Ob1](../../build/reference/ob-inline-function-expansion.md)或[/Ob2](../../build/reference/ob-inline-function-expansion.md)编译器选项。  
  
-   省略链接选项 /NOENTRY 时创建纯资源 DLL 会导致 LNK2001。  
  
-   使用 /SUBSYSTEM 或 /ENTRY 设置不正确可能导致 LNK2001。 例如，如果您编写基于字符的应用程序 （控制台应用程序），并指定 /SUBSYSTEM:WINDOWS，则会为无法解析的外部`WinMain`。 有关这些选项和入口点的详细信息，请参阅[/SUBSYSTEM](../../build/reference/subsystem-specify-subsystem.md)和[/ENTRY](../../build/reference/entry-entry-point-symbol.md)链接器选项。  
  
 **导出问题**  
  
-   当移植应用程序从 16 至 32 或 64 位时，会发生 LNK2001。 当前模块定义 (.def) 文件语法要求`__cdecl`， `__stdcall`，和`__fastcall`函数要导出一节中列出没有下划线 （未修饰名）。 这不同于 16 位语法，其中必须将它们列带下划线 （修饰）。 有关详细信息，请参阅说明[导出](../../build/reference/exports.md)模块定义文件部分。  
  
-   .Def 文件中列出，但找不到的任何导出将导致 LNK2001。 这可能是因为它不存在、 拼写不正确，或使用 c + + 修饰的名 （.def 文件不采用修饰的名）  
  
 **解释输出**  
  
 如果符号无法解析，可以通过下列指南来获取有关该函数的信息︰  
  
 在 x86 平台，名称的调用约定修饰编译在 C 中，或对于 extern"C"c + + 中的名称是︰  
  
 `__cdecl`  
 函数具有下划线 (_) 前缀。  
  
 `__stdcall`  
 函数具有下划线 (_) 前缀和 @ 后缀后, 跟 dword 对齐参数在堆栈上的大小。  
  
 `__fastcall`  
 函数具有 @ 前缀和 @ 后缀后, 跟 dword 对齐参数在堆栈上的大小。  
  
 使用 undname.exe 获取修饰名称的未修饰的形式。  
  
 一些上面列出的原因的详细信息，请参阅[名称修饰](../../error-messages/tool-errors/name-decoration.md)。
