---
title: 链接器选项
ms.date: 08/20/2018
f1_keywords:
- link
helpviewer_keywords:
- linker [C++]
- linker [C++], options listed
- libraries [C++], linking to COFF
- LINK tool [C++], linker options
ms.assetid: c1d51b8a-bd23-416d-81e4-900e02b2c129
ms.openlocfilehash: 22ac88ede7cc015efd12f1a996ffdf361b43f041
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50510105"
---
# <a name="linker-options"></a>链接器选项

LINK.exe 将通用对象文件格式 (COFF) 对象文件和库链接起来，以创建可执行 (.exe) 文件或动态链接库 (DLL)。

下表列出了 LINK.exe 的选项。 有关 LINK 的详细信息，请参阅：

- [编译器控制的 LINK 选项](../../build/reference/compiler-controlled-link-options.md)

- [LINK 输入文件](../../build/reference/link-input-files.md)

- [LINK 输出](../../build/reference/link-output.md)

- [保留字](../../build/reference/reserved-words.md)

在命令行中，不区分大小写; 链接器选项例如，/base 和 /BASE 的含义相同的操作。 有关如何在命令行或 Visual Studio 中指定每个选项的详细信息，请参阅适用于该选项的文档。

可以使用 [注释](../../preprocessor/comment-c-cpp.md) 杂注指定一些链接器选项。

|选项|目标|
|------------|-------------|
|[@](../../build/reference/at-specify-a-linker-response-file.md)|指定响应文件。|
|[/ALIGN](../../build/reference/align-section-alignment.md)|指定每一节的对齐方式。|
|[/ALLOWBIND](../../build/reference/allowbind-prevent-dll-binding.md)|指定 DLL 不能绑定。|
|[/ALLOWISOLATION](../../build/reference/allowisolation-manifest-lookup.md)|指定清单查找的行为。|
|[/APPCONTAINER](../../build/reference/appcontainer-windows-store-app.md)|指定应用是否必须在 appcontainer 进程环境中运行。|
|[/ASSEMBLYDEBUG](../../build/reference/assemblydebug-add-debuggableattribute.md)|将 <xref:System.Diagnostics.DebuggableAttribute> 添加到托管映像中。|
|[/ASSEMBLYLINKRESOURCE](../../build/reference/assemblylinkresource-link-to-dotnet-framework-resource.md)|创建指向托管资源的链接。|
|[/ASSEMBLYMODULE](../../build/reference/assemblymodule-add-a-msil-module-to-the-assembly.md)|指定应将 Microsoft 中间语言 (MSIL) 模块导入到程序集中。|
|[/ASSEMBLYRESOURCE](../../build/reference/assemblyresource-embed-a-managed-resource.md)|将托管资源文件嵌入程序集。|
|[/BASE](../../build/reference/base-base-address.md)|为程序设置基址。|
|[/CGTHREADS](../../build/reference/cgthreads-compiler-threads.md)|设置 cl.exe 线程数以在指定链接时代码生成后用于优化和代码生成。|
|[/CLRIMAGETYPE](../../build/reference/clrimagetype-specify-type-of-clr-image.md)|设置 CLR 映像的类型（IJW、纯或安全）。|
|[/CLRSUPPORTLASTERROR](../../build/reference/clrsupportlasterror-preserve-last-error-code-for-pinvoke-calls.md)|保留通过 P/Invoke 机制调用的函数的上一个错误代码。|
|[/CLRTHREADATTRIBUTE](../../build/reference/clrthreadattribute-set-clr-thread-attribute.md)|指定要应用于 CLR 程序入口点的线程特性。|
|[/CLRUNMANAGEDCODECHECK](../../build/reference/clrunmanagedcodecheck-add-suppressunmanagedcodesecurityattribute.md)|指定链接器是否将 SuppressUnmanagedCodeSecurity 特性应用于链接器生成的、从托管代码调用到本机 DLL 中的 PInvoke 存根。|
|[/DEBUG](../../build/reference/debug-generate-debug-info.md)|创建调试信息。|
|[/DEBUGTYPE](../../build/reference/debugtype-debug-info-options.md)|指定要包括在调试信息中的数据。|
|[/DEF](../../build/reference/def-specify-module-definition-file.md)|将模块定义 (.def) 文件传递到链接器。|
|[/DEFAULTLIB](../../build/reference/defaultlib-specify-default-library.md)|在解析外部引用时搜索指定的库。|
|[/DELAY](../../build/reference/delay-delay-load-import-settings.md)|控制 DLL 的延迟加载。|
|[/DELAYLOAD](../../build/reference/delayload-delay-load-import.md)|导致延迟加载指定的 DLL。|
|[/DELAYSIGN](../../build/reference/delaysign-partially-sign-an-assembly.md)|对程序集进行部分签名。|
|[/ DEPENDENTLOADFLAG](dependentloadflag.md)|设置依赖 DLL 加载默认标志。|
|[/DLL](../../build/reference/dll-build-a-dll.md)|生成 DLL。|
|[/DRIVER](../../build/reference/driver-windows-nt-kernel-mode-driver.md)|创建内核模式驱动程序。|
|[/DYNAMICBASE](../../build/reference/dynamicbase-use-address-space-layout-randomization.md)|使用地址空间布局随机化 (ASLR) 功能，指定是否生成可在加载时随机重新设定基址的可执行文件映像。|
|[/ENTRY](../../build/reference/entry-entry-point-symbol.md)|设置起始地址。|
|[/errorReport](../../build/reference/errorreport-report-internal-linker-errors.md)|向 Microsoft 报告内部链接器错误。|
|[/EXPORT](../../build/reference/export-exports-a-function.md)|导出函数。|
|[/FILEALIGN](../../build/reference/filealign.md)|对齐指定值的序列图上的输出文件中的部分。|
|[/FIXED](../../build/reference/fixed-fixed-base-address.md)|创建只能在其首选基址加载的程序。|
|[/FORCE](../../build/reference/force-force-file-output.md)|强制完成链接，即使符号无法解析或已定义多次。|
|[/FUNCTIONPADMIN](../../build/reference/functionpadmin-create-hotpatchable-image.md)|创建可进行热修补的映像。|
|[/GENPROFILE、/FASTGENPROFILE](../../build/reference/genprofile-fastgenprofile-generate-profiling-instrumented-build.md)|这两个选项均通过链接器指定 .pgd 文件的生成，以支持按配置文件优化 (PGO)。 /GENPROFILE 和 /FASTGENPROFILE 使用不同的默认参数。|
|[/GUARD](../../build/reference/guard-enable-guard-checks.md)|启用控制流防护保护。|
|[/HEAP](../../build/reference/heap-set-heap-size.md)|设置堆的大小（以字节为单位）。|
|[/HIGHENTROPYVA](../../build/reference/highentropyva-support-64-bit-aslr.md)|指定对高熵 64 位地址空间布局随机化 (ASLR) 的支持。|
|[/IDLOUT](../../build/reference/idlout-name-midl-output-files.md)|指定 .idl 文件和其他 MIDL 输出文件的名称。|
|[/IGNORE](../../build/reference/ignore-ignore-specific-warnings.md)|禁止显示指定链接器警告的输出。|
|[/IGNOREIDL](../../build/reference/ignoreidl-don-t-process-attributes-into-midl.md)|防止将特性信息处理到 .idl 文件中。|
|[/IMPLIB](../../build/reference/implib-name-import-library.md)|重写默认的导入库名。|
|[/INCLUDE](../../build/reference/include-force-symbol-references.md)|强制符号引用。|
|[/INCREMENTAL](../../build/reference/incremental-link-incrementally.md)|控制增量链接。|
|[/INTEGRITYCHECK](../../build/reference/integritycheck-require-signature-check.md)|指定模块需要在加载时进行签名检查。|
|[/KEYCONTAINER](../../build/reference/keycontainer-specify-a-key-container-to-sign-an-assembly.md)|指定用来对程序集进行签名的密钥容器。|
|[/KEYFILE](../../build/reference/keyfile-specify-key-or-key-pair-to-sign-an-assembly.md)|指定用来对程序集进行签名的密钥或密钥对。|
|[/LARGEADDRESSAWARE](../../build/reference/largeaddressaware-handle-large-addresses.md)|通知编译器应用程序支持大于 2 GB 的地址|
|[/LIBPATH](../../build/reference/libpath-additional-libpath.md)|指定要在环境库路径之前搜索的路径。|
|[/LTCG](../../build/reference/ltcg-link-time-code-generation.md)|指定链接时间代码生成。|
|[/MACHINE](../../build/reference/machine-specify-target-platform.md)|指定目标平台。|
|[/MANIFEST](../../build/reference/manifest-create-side-by-side-assembly-manifest.md)|创建并行清单文件，也可以选择将其嵌入二进制文件。|
|[/MANIFESTDEPENDENCY](../../build/reference/manifestdependency-specify-manifest-dependencies.md)|指定\<dependentAssembly > 清单文件中的部分。|
|[/MANIFESTFILE](../../build/reference/manifestfile-name-manifest-file.md)|更改清单文件的默认名称。|
|[/MANIFESTINPUT](../../build/reference/manifestinput-specify-manifest-input.md)|指定链接器要进行处理并嵌入二进制文件的清单输入文件。 可以多次使用此选项以指定多个清单输入文件。|
|[/MANIFESTUAC](../../build/reference/manifestuac-embeds-uac-information-in-manifest.md)|指定是否将用户帐户控制 (UAC) 信息嵌入到程序清单中。|
|[/MAP](../../build/reference/map-generate-mapfile.md)|创建映射文件。|
|[/MAPINFO](../../build/reference/mapinfo-include-information-in-mapfile.md)|包括映射文件中的指定信息。|
|[/MERGE](../../build/reference/merge-combine-sections.md)|合并节。|
|[/MIDL](../../build/reference/midl-specify-midl-command-line-options.md)|指定 MIDL 命令行选项。|
|[/ NATVIS](../../build/reference/natvis-add-natvis-to-pdb.md)|将调试器可视化工具中的 Natvis 文件添加到 PDB。|
|[/NOASSEMBLY](../../build/reference/noassembly-create-a-msil-module.md)|取消创建 .NET Framework 程序集。|
|[/NODEFAULTLIB](../../build/reference/nodefaultlib-ignore-libraries.md)|在解析外部引用时忽略所有（或指定的）默认库。|
|[/NOENTRY](../../build/reference/noentry-no-entry-point.md)|创建纯资源 DLL。|
|[/NOLOGO](../../build/reference/nologo-suppress-startup-banner-linker.md)|取消显示启动版权标志。|
|[/NXCOMPAT](../../build/reference/nxcompat-compatible-with-data-execution-prevention.md)|将可执行文件标记为经验证与 Windows 数据执行保护功能兼容。|
|[/OPT](../../build/reference/opt-optimizations.md)|控制 LINK 优化。|
|[/ORDER](../../build/reference/order-put-functions-in-order.md)|按预先确定的顺序将 COMDAT 放置到映像中。|
|[/OUT](../../build/reference/out-output-file-name.md)|指定输出文件名。|
|[/PDB](../../build/reference/pdb-use-program-database.md)|创建程序数据库 (PDB) 文件。|
|[/PDBALTPATH](../../build/reference/pdbaltpath-use-alternate-pdb-path.md)|使用备用位置来保存 PDB 文件。|
|[/PDBSTRIPPED](../../build/reference/pdbstripped-strip-private-symbols.md)|创建没有私有符号的程序数据库 (PDB) 文件。|
|[/PGD](../../build/reference/pgd-specify-database-for-profile-guided-optimizations.md)|为按配置文件优化指定 .pgd 文件。|
|[/POGOSAFEMODE](../../build/reference/pogosafemode-linker-option.md)|**已过时**创建线程安全 PGO 检测生成。|
|[/PROFILE](../../build/reference/profile-performance-tools-profiler.md)|生成一个可与“性能工具”探查器结合使用的输出文件。|
|[/RELEASE](../../build/reference/release-set-the-checksum.md)|在 .exe 标头中设置校验和。|
|[/SAFESEH](../../build/reference/safeseh-image-has-safe-exception-handlers.md)|指定映像将包含安全异常处理程序表。|
|[/SECTION](../../build/reference/section-specify-section-attributes.md)|重写节的特性。|
|[/ SOURCELINK](../../build/reference/sourcelink.md)|指定要添加到 PDB 的 SourceLink 文件。|
|[/STACK](../../build/reference/stack-stack-allocations.md)|设置堆栈的大小（以字节为单位）。|
|[/STUB](../../build/reference/stub-ms-dos-stub-file-name.md)|将 MS-DOS 存根程序附加到 Win32 程序。|
|[/SUBSYSTEM](../../build/reference/subsystem-specify-subsystem.md)|通知操作系统如何运行 .exe 文件。|
|[/SWAPRUN](../../build/reference/swaprun-load-linker-output-to-swap-file.md)|通知操作系统在运行链接器输出之前将其复制到一个交换文件。|
|[/TLBID](../../build/reference/tlbid-specify-resource-id-for-typelib.md)|指定链接器生成的类型库的资源 ID。|
|[/TLBOUT](../../build/reference/tlbout-name-dot-tlb-file.md)|指定 .tlb 文件和其他 MIDL 输出文件的名称。|
|[/TSAWARE](../../build/reference/tsaware-create-terminal-server-aware-application.md)|创建专为在终端服务器下运行而设计的应用程序。|
|[/USEPROFILE](../../build/reference/useprofile.md)|使用按配置优化训练数据来创建优化的映像。|
|[/VERBOSE](../../build/reference/verbose-print-progress-messages.md)|打印链接器进度消息。|
|[/VERSION](../../build/reference/version-version-information.md)|分配版本号。|
|[/WHOLEARCHIVE](../../build/reference/wholearchive-include-all-library-object-files.md)|包含指定的静态库中的每个对象文件。|
|[/WINMD](../../build/reference/winmd-generate-windows-metadata.md)|允许生成 Windows 运行时元数据文件。|
|[/WINMDFILE](../../build/reference/winmdfile-specify-winmd-file.md)|指定由 [/WINMD](../../build/reference/winmd-generate-windows-metadata.md) 链接器选项生成的 Windows 运行时元数据 (winmd) 输出文件的文件名。|
|[/WINMDKEYFILE](../../build/reference/winmdkeyfile-specify-winmd-key-file.md)|指定用来对 Windows 运行时元数据文件进行签名的密钥或密钥对。|
|[/WINMDKEYCONTAINER](../../build/reference/winmdkeycontainer-specify-key-container.md)|指定用来对 Windows 元数据文件进行签名的密钥容器。|
|[/WINMDDELAYSIGN](../../build/reference/winmddelaysign-partially-sign-a-winmd.md)|通过将公钥放置在 winmd 文件中，对 Windows 运行时元数据 (winmd) 文件进行部分签名。|
|[/WX](../../build/reference/wx-treat-linker-warnings-as-errors.md)|将链接器警告视为错误。|

有关详细信息，请参阅 [Compiler-Controlled LINK Options](../../build/reference/compiler-controlled-link-options.md)。

## <a name="see-also"></a>请参阅

[C/C++ 生成参考](../../build/reference/c-cpp-building-reference.md)<br/>
[设置链接器选项](../../build/reference/setting-linker-options.md)