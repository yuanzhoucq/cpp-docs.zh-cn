---
title: "按类别列出的编译器选项 | Microsoft Docs"
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
  - "编译器选项, C++"
ms.assetid: c4750dcf-dba0-4229-99b6-45cdecc11729
caps.latest.revision: 64
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 64
---
# 按类别列出的编译器选项
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

本文包含编译器选项的分类列表。 有关按字母顺序排序的列表，请参见[按字母顺序列出的编译器选项](../../build/reference/compiler-options-listed-alphabetically.md)。  
  
### 优化  
  
|选项|用途|  
|--------|--------|  
|[\/O1](../../build/reference/o1-o2-minimize-size-maximize-speed.md)|创建小代码。|  
|[\/O2](../../build/reference/o1-o2-minimize-size-maximize-speed.md)|创建快速代码。|  
|[\/Ob](../../build/reference/ob-inline-function-expansion.md)|控制内联展开。|  
|[\/Od](../../build/reference/od-disable-debug.md)|禁用优化。|  
|[\/Og](../../build/reference/og-global-optimizations.md)|已否决。 使用全局优化。|  
|[\/Oi](../../build/reference/oi-generate-intrinsic-functions.md)|生成内部函数。|  
|[\/Os](../../build/reference/os-ot-favor-small-code-favor-fast-code.md)|代码大小优先。|  
|[\/Ot](../../build/reference/os-ot-favor-small-code-favor-fast-code.md)|代码速度优先。|  
|[\/Ox](../../build/reference/ox-full-optimization.md)|使用最大优化 \(\/Ob2gity \/Gs\)。|  
|[\/Oy](../../build/reference/oy-frame-pointer-omission.md)|省略帧指针。 \(仅限 x86\)|  
|[\/favor](../../build/reference/favor-optimize-for-architecture-specifics.md)|生成针对一个指定体系结构或一系列体系结构进行优化的代码。|  
  
### 代码生成  
  
|选项|用途|  
|--------|--------|  
|[\/arch](../../build/reference/arch-x86.md)|使用 SSE 或 SSE2 指令生成代码。 \(仅限 x86\)|  
|[\/clr](../../build/reference/clr-common-language-runtime-compilation.md)|生成要在公共语言运行时上运行的输出文件。|  
|[\/EH](../../build/reference/eh-exception-handling-model.md)|指定异常处理模型。|  
|[\/fp](../../build/reference/fp-specify-floating-point-behavior.md)|指定浮点行为。|  
|[\/GA](../../build/reference/ga-optimize-for-windows-application.md)|针对 Windows 应用程序进行优化。|  
|[\/Gd](../../build/reference/gd-gr-gv-gz-calling-convention.md)|使用 `__cdecl` 调用约定。 \(仅限 x86\)|  
|[\/Ge](../../build/reference/ge-enable-stack-probes.md)|已否决。 激活堆栈探测。|  
|[\/GF](../../build/reference/gf-eliminate-duplicate-strings.md)|启用字符串池。|  
|[\/Gh](../../build/reference/gh-enable-penter-hook-function.md)|调用挂钩函数 `_penter`。|  
|[\/GH](../../build/reference/gh-enable-pexit-hook-function.md)|调用挂钩函数 `_pexit`。|  
|[\/GL](../../build/reference/gl-whole-program-optimization.md)|启用全程序优化。|  
|[\/Gm](../../build/reference/gm-enable-minimal-rebuild.md)|启用最小重新生成。|  
|[\/GR](../../build/reference/gr-enable-run-time-type-information.md)|启用运行时类型信息 \(RTTI\)。|  
|[\/Gr](../../build/reference/gd-gr-gv-gz-calling-convention.md)|使用 `__fastcall` 调用约定。 \(仅限 x86\)|  
|[\/GS](../../build/reference/gs-buffer-security-check.md)|检查缓冲区安全性。|  
|[\/Gs](../../build/reference/gs-control-stack-checking-calls.md)|控制堆栈探测。|  
|[\/GT](../../build/reference/gt-support-fiber-safe-thread-local-storage.md)|支持使用静态线程本地存储分配的数据的纤程安全。|  
|[\/guard:cf](../../build/reference/guard-enable-control-flow-guard.md)|添加控制流防护安全检查。|  
|[\/Gv](../../build/reference/gd-gr-gv-gz-calling-convention.md)|使用 `__vectorcall` 调用约定。 （仅限 x86 和 x64）|  
|[\/Gw](../../build/reference/gw-optimize-global-data.md)|启用全程序全局数据优化。|  
|[\/GX](../../build/reference/gx-enable-exception-handling.md)|已否决。 启用同步异常处理。 改为使用 [\/EH](../../build/reference/eh-exception-handling-model.md)。|  
|[\/Gy](../../build/reference/gy-enable-function-level-linking.md)|启用函数级链接。|  
|[\/GZ](../../build/reference/gz-enable-stack-frame-run-time-error-checking.md)|已否决。 启用快速检查。 （与 [\/RTC1](../../build/reference/rtc-run-time-error-checks.md) 相同）|  
|[\/Gz](../../build/reference/gd-gr-gv-gz-calling-convention.md)|使用 `__stdcall` 调用约定。 \(仅限 x86\)|  
|[\/homeparams](../../build/reference/homeparams-copy-register-parameters-to-stack.md)|强制将传入寄存器的参数写入其在函数入口的堆栈上的位置。 此编译器选项仅适用于 [!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)] 编译器（本机编译和跨平台编译）。|  
|[\/hotpatch](../../build/reference/hotpatch-create-hotpatchable-image.md)|创建可热修补的映像。|  
|[\/Qfast\_transcendentals](../../build/reference/qfast-transcendentals-force-fast-transcendentals.md)|生成快速先验。|  
|[QIfist](../../build/reference/qifist-suppress-ftol.md)|已否决。 当需要从浮点型转换为整型时，取消调用 Helper 函数 `_ftol`。 \(仅限 x86\)|  
|[\/Qimprecise\_fwaits](../../build/reference/qimprecise-fwaits-remove-fwaits-inside-try-blocks.md)|移除 `fwait` 块中的 `try` 命令。|  
|[\/Qpar](../../build/reference/qpar-auto-parallelizer.md)|启用循环的自动并行化。|  
|[\/Qpar\-report](../../build/reference/qpar-report-auto-parallelizer-reporting-level.md)|启用自动并行化的报告级别。|  
|[\/Qsafe\_fp\_loads](../../build/reference/qsafe-fp-loads.md)|将整数移动指令用于浮点值，并禁用特定浮点加载优化。|  
|[\/Qvec\-report（自动矢量化程序报告等级）](../../build/reference/qvec-report-auto-vectorizer-reporting-level.md)|启用自动矢量化的报告级别。|  
|[\/RTC](../../build/reference/rtc-run-time-error-checks.md)|启用运行时错误检查。|  
|[\/volatile](../../build/reference/volatile-volatile-keyword-interpretation.md)|选择如何解释 volatile 关键字。|  
  
### 输出文件  
  
|选项|用途|  
|--------|--------|  
|[\/doc](../../build/reference/doc-process-documentation-comments-c-cpp.md)|将文档注释处理到一个 XML 文件中。|  
|[\/FA](../../build/reference/fa-fa-listing-file.md)|配置程序集列表文件。|  
|[\/Fa](../../build/reference/fa-fa-listing-file.md)|创建程序集列表文件。|  
|[\/Fd](../../build/reference/fd-program-database-file-name.md)|重命名程序数据库文件。|  
|[\/Fe](../../build/reference/fe-name-exe-file.md)|重命名可执行文件。|  
|[\/Fi](../../build/reference/fi-preprocess-output-file-name.md)|指定预处理输出文件名。|  
|[\/Fm](../../build/reference/fm-name-mapfile.md)|创建映射文件。|  
|[\/Fo](../../build/reference/fo-object-file-name.md)|创建对象文件。|  
|[\/Fp](../../build/reference/fp-name-dot-pch-file.md)|指定预编译头文件名。|  
|[\/FR](../../build/reference/fr-fr-create-dot-sbr-file.md) [\/Fr](../../build/reference/fr-fr-create-dot-sbr-file.md)|生成浏览器文件。|  
  
### 预处理器  
  
|选项|用途|  
|--------|--------|  
|[\/AI](../../build/reference/ai-specify-metadata-directories.md)|指定在解析传递到 [\#using](../../preprocessor/hash-using-directive-cpp.md) 指令的文件引用时搜索的目录。|  
|[\/C](../../build/reference/c-preserve-comments-during-preprocessing.md)|在预处理期间保留注释。|  
|[\/D](../../build/reference/d-preprocessor-definitions.md)|定义常数和宏。|  
|[\/E](../../build/reference/e-preprocess-to-stdout.md)|将预处理器输出复制到标准输出。|  
|[\/EP](../../build/reference/ep-preprocess-to-stdout-without-hash-line-directives.md)|将预处理器输出复制到标准输出。|  
|[\/FI](../../build/reference/fi-name-forced-include-file.md)|预处理指定的包含文件。|  
|[\/FU](../../build/reference/fu-name-forced-hash-using-file.md)|强制使用文件名，就像它已被传递到 [\#using](../../preprocessor/hash-using-directive-cpp.md) 指令一样。|  
|[\/Fx](../../build/reference/fx-merge-injected-code.md)|将插入的代码与源文件合并。|  
|[\/I](../../build/reference/i-additional-include-directories.md)|在目录中搜索包含文件。|  
|[\/P](../../build/reference/p-preprocess-to-a-file.md)|将预处理器输出写入文件。|  
|[\/U](../../build/reference/u-u-undefine-symbols.md)|移除预定义宏。|  
|[\/u](../../build/reference/u-u-undefine-symbols.md)|移除所有的预定义宏。|  
|[\/X](../../build/reference/x-ignore-standard-include-paths.md)|忽略标准包含目录。|  
  
### 语言  
  
|选项|用途|  
|--------|--------|  
|[\/openmp](../../build/reference/openmp-enable-openmp-2-0-support.md)|在源代码中启用 [\#pragma omp](../../preprocessor/omp.md)。|  
|[\/vd](../../build/reference/vd-disable-construction-displacements.md)|取消或启用隐藏的 `vtordisp` 类成员。|  
|[\/vmb](../../build/reference/vmb-vmg-representation-method.md)|对指向成员的指针使用最佳的基。|  
|[\/vmg](../../build/reference/vmb-vmg-representation-method.md)|对指向成员的指针使用完全一般性。|  
|[\/vmm](../../build/reference/vmm-vms-vmv-general-purpose-representation.md)|声明多重继承。|  
|[\/vms](../../build/reference/vmm-vms-vmv-general-purpose-representation.md)|声明单一继承。|  
|[\/vmv](../../build/reference/vmm-vms-vmv-general-purpose-representation.md)|声明虚拟继承。|  
|[\/Z7](../../build/reference/z7-zi-zi-debug-information-format.md)|生成与 C 7.0 兼容的调试信息。|  
|[\/Za](../../build/reference/za-ze-disable-language-extensions.md)|禁用语言扩展。|  
|[\/Zc](../../build/reference/zc-conformance.md)|指定在 [\/Ze](../../build/reference/za-ze-disable-language-extensions.md) 下的标准行为。|  
|[\/Ze](../../build/reference/za-ze-disable-language-extensions.md)|已否决。 启用语言扩展。|  
|[\/ZI](../../build/reference/z7-zi-zi-debug-information-format.md)|将调试信息包含在与“编辑并继续”兼容的程序数据库中。 \(仅限 x86\)|  
|[\/Zi](../../build/reference/z7-zi-zi-debug-information-format.md)|生成完整的调试信息。|  
|[\/Zl](../../build/reference/zl-omit-default-library-name.md)|从 .obj 文件中移除默认库名。|  
|[\/Zp](../../build/reference/zp-struct-member-alignment.md) *n*|封装结构成员。|  
|[\/Zs](../../build/reference/zs-syntax-check-only.md)|只检查语法。|  
|[\/ZW](../../build/reference/zw-windows-runtime-compilation.md)|生成要在 [!INCLUDE[wrt](../../atl/reference/includes/wrt_md.md)]上运行的输出文件。|  
  
### 链接  
  
|选项|用途|  
|--------|--------|  
|[\/F](../../build/reference/f-set-stack-size.md)|设置堆栈大小。|  
|[\/LD](../../build/reference/md-mt-ld-use-run-time-library.md)|创建动态链接库。|  
|[\/LDd](../../build/reference/md-mt-ld-use-run-time-library.md)|创建调试动态链接库。|  
|[\/link](../../build/reference/link-pass-options-to-linker.md)|将指定的选项传递给 LINK。|  
|[\/LN](../../build/reference/ln-create-msil-module.md)|创建 MSIL 模块。|  
|[\/MD](../../build/reference/md-mt-ld-use-run-time-library.md)|使用 MSVCRT.lib 编译以创建多线程 DLL。|  
|[\/MDd](../../build/reference/md-mt-ld-use-run-time-library.md)|使用 MSVCRTD.lib 编译以创建调试多线程 DLL。|  
|[\/MT](../../build/reference/md-mt-ld-use-run-time-library.md)|使用 LIBCMT.lib 编译以创建多线程可执行文件。|  
|[\/MTd](../../build/reference/md-mt-ld-use-run-time-library.md)|使用 LIBCMTD.lib 编译以创建调试多线程可执行文件。|  
  
### 预编译头  
  
|选项|用途|  
|--------|--------|  
|[\/Y\-](../../build/reference/y-ignore-precompiled-header-options.md)|忽略当前生成中的所有其他预编译头编译器选项。|  
|[\/Yc](../../build/reference/yc-create-precompiled-header-file.md)|创建预编译头文件。|  
|[\/Yd](../../build/reference/yd-place-debug-information-in-object-file.md)|将完整的调试信息放在所有对象文件中。|  
|[\/Yu](../../build/reference/yu-use-precompiled-header-file.md)|在生成期间使用预编译头文件。|  
  
### 杂项  
  
|选项|用途|  
|--------|--------|  
|[\/?](../../build/reference/help-compiler-command-line-help.md)|列出编译器选项。|  
|[@](../../build/reference/at-specify-a-compiler-response-file.md)|指定响应文件。|  
|[\/analyze](../../build/reference/analyze-code-analysis.md)|启用代码分析。|  
|[\/bigobj](../../build/reference/bigobj-increase-number-of-sections-in-dot-obj-file.md)|增加 .obj 文件中可寻址节的数目。|  
|[\/c](../../build/reference/c-compile-without-linking.md)|编译但不链接。|  
|[\/cgthreads](../../build/reference/cgthreads-code-generation-threads.md)|指定 cl.exe 线程数以用于优化和代码生成。|  
|[\/errorReport](../../build/reference/errorreport-report-internal-compiler-errors.md)|允许你将内部编译器错误 \(ICE\) 信息直接提供给 Visual C\+\+ 团队。|  
|[\/FC](../../build/reference/fc-full-path-of-source-code-file-in-diagnostics.md)|在诊断文本中显示传递给 cl.exe 的源代码文件的完整路径。|  
|[\/FS](../../build/reference/fs-force-synchronous-pdb-writes.md)|强制写入到程序数据库 \(PDB\) 文件以通过 MSPDBSRV.EXE 序列化。|  
|[\/H](../../build/reference/h-restrict-length-of-external-names.md)|已否决。 限制外部（公共）名称的长度。|  
|[\/HELP](../../build/reference/help-compiler-command-line-help.md)|列出编译器选项。|  
|[\/J](../../build/reference/j-default-char-type-is-unsigned.md)|更改默认的 `char` 类型。|  
|[\/kernel](../../build/reference/kernel-create-kernel-mode-binary.md)|编译器和链接器将创建可在 Windows 内核中执行的二进制文件。|  
|[\/MP](../../build/reference/mp-build-with-multiple-processes.md)|同时生成多个源文件。|  
|[\/nologo](../../build/reference/nologo-suppress-startup-banner-c-cpp.md)|取消显示登录版权标志。|  
|[\/sdl](../../build/reference/sdl-enable-additional-security-checks.md)|启用更多安全功能和警告。|  
|[\/showIncludes](../../build/reference/showincludes-list-include-files.md)|在编译期间显示所有包含文件的列表。|  
|[\/Tc](../../build/reference/tc-tp-tc-tp-specify-source-file-type.md) [\/TC](../../build/reference/tc-tp-tc-tp-specify-source-file-type.md)|指定 C 源文件。|  
|[\/Tp](../../build/reference/tc-tp-tc-tp-specify-source-file-type.md) [\/TP](../../build/reference/tc-tp-tc-tp-specify-source-file-type.md)|指定 C\+\+ 源文件。|  
|[\/V](../../build/reference/v-version-number.md)|已否决。 设置版本字符串。|  
|[\/w](../../build/reference/compiler-option-warning-level.md)|禁用所有警告。|  
|[\/W0、\/W1、\/W2、\/W3、\/W4](../../build/reference/compiler-option-warning-level.md)|设置输出警告级别。|  
|[\/W1、\/W2、\/W3、\/W4](../../build/reference/compiler-option-warning-level.md)|针对指定的警告设置警告级别。|  
|[\/Wall](../../build/reference/compiler-option-warning-level.md)|启用所有警告，包括默认情况下禁用的警告。|  
|[\/wd](../../build/reference/compiler-option-warning-level.md)|禁用指定的警告。|  
|[\/we](../../build/reference/compiler-option-warning-level.md)|将指定的警告视为错误。|  
|[\/WL](../../build/reference/wl-enable-one-line-diagnostics.md)|在从命令行编译 C\+\+ 源代码时启用错误消息和警告消息的单行诊断。|  
|[\/wo](../../build/reference/compiler-option-warning-level.md)|仅显示指定的警告一次。|  
|[\/Wp64](../../build/reference/wp64-detect-64-bit-portability-issues.md)|已过时。 检测 64 位可移植性问题。|  
|[\/Wv](../../build/reference/compiler-option-warning-level.md)|禁用更高版本的编译器引入的警告。|  
|[\/WX](../../build/reference/compiler-option-warning-level.md)|将警告视为错误。|  
|[\/Yd](../../build/reference/yd-place-debug-information-in-object-file.md)|已否决。 将完整的调试信息放在所有对象文件中。 改为使用 [\/Zi](../../build/reference/z7-zi-zi-debug-information-format.md)。|  
|[\/Yl](../../build/reference/yl-inject-pch-reference-for-debug-library.md)|创建调试库时插入 PCH 引用。|  
|[\/Zm](../../build/reference/zm-specify-precompiled-header-memory-allocation-limit.md)|指定预编译头内存分配限制。|  
  
### 已弃用并删除的编译器选项  
  
|选项|用途|  
|--------|--------|  
|[\/clr:noAssembly](../../build/reference/clr-common-language-runtime-compilation.md)|已否决。 请改用 [\/LN（创建 MSIL 模块）](../../build/reference/ln-create-msil-module.md)。|  
|[\/Fr](../../build/reference/fr-fr-create-dot-sbr-file.md)|已否决。 创建无局部变量的浏览信息文件。|  
|[\/Ge](../../build/reference/ge-enable-stack-probes.md)|已否决。 激活堆栈探测。 默认开启。|  
|[\/GX](../../build/reference/gx-enable-exception-handling.md)|已否决。 启用同步异常处理。 改为使用 [\/EH](../../build/reference/eh-exception-handling-model.md)。|  
|[\/GZ](../../build/reference/gz-enable-stack-frame-run-time-error-checking.md)|已否决。 启用快速检查。 改为使用 [\/RTC1](../../build/reference/rtc-run-time-error-checks.md)。|  
|[\/H](../../build/reference/h-restrict-length-of-external-names.md)|已否决。 限制外部（公共）名称的长度。|  
|[\/Og](../../build/reference/og-global-optimizations.md)|已否决。 使用全局优化。|  
|[QIfist](../../build/reference/qifist-suppress-ftol.md)|已否决。 曾用来指定如何从浮点类型转换到整型类型。|  
|[\/V](../../build/reference/v-version-number.md)|已否决。 设置 .obj 文件版本字符串。|  
|[\/Yd](../../build/reference/yd-place-debug-information-in-object-file.md)|已否决。 将完整的调试信息放在所有对象文件中。 改为使用 [\/Zi](../../build/reference/z7-zi-zi-debug-information-format.md)。|  
|[\/Zc:forScope\-](../../build/reference/zc-forscope-force-conformance-in-for-loop-scope.md)|已否决。 在 for 循环范围中禁用一致性。|  
|[\/Ze](../../build/reference/za-ze-disable-language-extensions.md)|已否决。 启用语言扩展。|  
|[\/Zg](../../build/reference/zg-generate-function-prototypes.md)|已在 Visual C\+\+ 2015 中删除。 生成函数原型。|  
  
## 请参阅  
 [C\/C\+\+ 生成参考](../../build/reference/c-cpp-building-reference.md)   
 [编译器选项](../../build/reference/compiler-options.md)   
 [设置编译器选项](../../build/reference/setting-compiler-options.md)