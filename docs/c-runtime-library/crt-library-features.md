---
title: "CRT 库功能 |Microsoft 文档"
ms.custom: 
ms.date: 03/13/2018
ms.technology:
- cpp-standard-libraries
ms.topic: article
f1_keywords:
- c.runtime
dev_langs:
- C++
helpviewer_keywords:
- MSVCR71.dll
- libraries [C++], multithreaded
- library files, run-time
- LIBCMT.lib
- LIBCP.lib
- LIBCPMT.lib
- run-time libraries, C
- CRT, release versions
- MSVCP71.dll
- LIBC.lib
- libraries [C++]
- libraries [C++], run-time
- linking [C++], libraries
ms.assetid: a889fd39-807d-48f2-807f-81492612463f
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 33e3e5f63aebfd1b169210eaa3748feb761e0422
ms.sourcegitcommit: 9239c52c05e5cd19b6a72005372179587a47a8e4
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/16/2018
---
# <a name="crt-library-features"></a>CRT 库功能

本主题将介绍各种 .lib 文件，包括 C 运行时库及其关联的编译器选项和预处理器指令。

## <a name="c-run-time-libraries-crt"></a>C 运行时库 (CRT)

C 运行时库 (CRT) 是集成了 ISO C99 标准库的 C++ 标准库。 实现 CRT 的 Visual C++ 库支持用于 .NET 开发的本机代码开发以及本机和托管混合代码。 所有版本的 CRT 都支持多线程开发。 大多数的库都支持通过静态链接将库直接链接到代码中，或通过动态链接让代码使用常用 DLL 文件。

从 Visual Studio 2015 开始，CRT 已被重构为新的二进制文件。 通用 CRT (UCRT) 包含通过标准 C99 CRT 库导出的函数和全局函数。 UCRT 现为 Windows 组件，并作为 Windows 10 的一部分提供。 静态库、DLL 导入库和 UCRT 的头文件现在 Windows 10 SDK 中提供。 安装 Visual C++ 时，Visual Studio 安装程序将安装使用 UCRT 所需 Windows 10 SDK 的子集。 可以在 Visual Studio 2015 及更高版本支持的任何 Windows 版本上使用 UCRT。 可以使用 vcredist 重新分发它，以便支持 Windows 10 以外的 Windows 版本。 有关详细信息，请参阅 [Redistributing Visual C++ Files](../ide/redistributing-visual-cpp-files.md)。

下表列出了实现 UCRT 的库。

|库|关联的 DLL|特征|选项|预处理器指令|
|-------------|--------------------|---------------------|------------|-----------------------------|
|libucrt.lib|无|将 UCRT 静态链接到你的代码。|**/MT**|_MT|
|libucrtd.lib|无|用于静态链接的 UCRT 调试版本。 不可再发行。|**/MTd**|_DEBUG, _MT|
|ucrt.lib|ucrtbase.dll|UCRT 的 DLL 导入库。|**/MD**|_MT, _DLL|
|ucrtd.lib|ucrtbased.dll|UCRT 调试版本的 DLL 导入库。 不可再发行。|**/MDd**|_DEBUG, _MT, _DLL|

vcruntime 库包含 Visual C++ CRT 实现特定的代码，例如异常处理和调试支持、运行时检查和类型信息、实现的详细信息和某些扩展的库函数。 此库特定于所用编译器的版本。

此表列出了实现 vcruntime 库的库。

|库|关联的 DLL|特征|选项|预处理器指令|
|-------------|--------------------|---------------------|------------|-----------------------------|
|libvcruntime.lib|无|静态链接到你的代码。|**/MT**|_MT|
|libvcruntimed.lib|无|用于静态链接的调试版本。 不可再发行。|**/MTd**|_MT, _DEBUG|
|vcruntime.lib|vcruntime\<version>.dll|vcruntime 的 DLL 导入库。|**/MD**|_MT, _DLL|
|vcruntimed.lib|vcruntime\<version>d.dll|调试 vcruntime 的 DLL 导入库。 不可再发行。|**/MDd**|_DEBUG, _MT, _DLL|

初始化 CRT 的代码是几个库中的一个，根据 CRT 库是采用静态或动态链接还是本机、托管或混合代码而定。 此代码处理 CRT 启动、内部逐线程数据初始化和终止。 它特定于所用编译器的版本。 此库始终采用动态链接，即使使用动态链接的 UCRT 也是如此。

此表列出了实现 CRT 初始化和终止的库。

|库|特征|选项|预处理器指令|
|-------------|---------------------|------------|-----------------------------|
|LIBCMT.lib|将本机 CRT 启动静态链接到你的代码。|**/MT**|_MT|
|libcmtd.lib|静态链接本机 CRT 启动的调试版本。 不可再发行。|**/MTd**|_DEBUG, _MT|
|msvcrt.lib|与 DLL UCRT 和 vcruntime 一起使用的本机 CRT 启动的静态库。|**/MD**|_MT, _DLL|
|msvcrtd.lib|与 DLL UCRT 和 vcruntime 一起使用的本机 CRT 启动调试版本的静态库。 不可再发行。|**/MDd**|_DEBUG, _MT, _DLL|
|msvcmrt.lib|与 DLL UCRT 和 vcruntime 一起使用的本机和托管混合 CRT 启动的静态库。|**/clr**||
|msvcmrtd.lib|与 DLL UCRT 和 vcruntime 一起使用的本机和托管混合 CRT 启动调试版本的静态库。 不可再发行。|**/clr**||
|msvcurt.lib|纯托管 CRT 的**已弃用**静态库。|**/clr:pure**||
|msvcurtd.lib|纯托管 CRT 调试版本的**已弃用**静态库。 不可再发行。|**/clr:pure**||

如果从没有编译器选项（可指定 C ++运行时库）的命令行链接程序，则链接器将使用静态链接的 CRT 库：libcmt.lib、libvcruntime.lib 和 libucrt.lib。

使用静态链接的 CRT 意味着由 C 运行时库保存的任何状态信息对于 CRT 的该实例而言是本地的。 例如，如果当使用静态链接的 CRT 时使用 [strtok、_strtok_l、wcstok、_wcstok_l、_mbstok、_mbstok_l](../c-runtime-library/reference/strtok-strtok-l-wcstok-wcstok-l-mbstok-mbstok-l.md)，则 `strtok` 分析器的位置将与链接到另一个静态 CRT 实例的同一进程（但在不同的 DLL 或 EXE 中）的代码中使用的 `strtok` 状态无关。 相反，动态链接的 CRT 可共享动态链接到 CRT 的进程中的所有代码的状态。 如果使用这些函数新的更安全版本，这一问题则不适用；例如， `strtok_s` 就不存在此问题。

由于通过链接到静态 CRT 构建的 DLL 将具有其自己的 CRT 状态，因此不建议以静态方式链接到 DLL 中的 CRT，除非特别需要和需了解这一后果。 例如，如果在加载 DLL（链接到其自己的静态 CRT）的可执行文件中调用 [_set_se_translator](../c-runtime-library/reference/set-se-translator.md) ，则转换器将不会捕获由 DLL 中的代码生成的任何硬件异常，但会捕获由主可执行文件中的代码生成的硬件异常。

如果使用 **/clr** 编译器开关，则将通过静态库 msvcmrt.lib 链接代码。 静态库将提供托管的代码和本机 CRT 之间的代理。 你无法使用静态链接的 CRT（ **/MT** 或 **/MTd** 选项）和 **/clr**。 请改用动态链接的库（**/MD** 或 **/MDd**）。

有关将 CRT 与 **/clr** 配合使用的详细信息，请参阅[混合（本机和托管）程序集](../dotnet/mixed-native-and-managed-assemblies.md)。

若要生成你的应用程序的调试版本，则必须定义 [_DEBUG](../c-runtime-library/debug.md) 标志，并且该应用程序必须与其中一个调试版本的库链接。 有关使用调试版本的库文件的详细信息，请参阅 [CRT 调试技术](/visualstudio/debugger/crt-debugging-techniques)。

此版本的 CRT 不完全符合 C99 标准。 具体而言，不支持 \<tgmath.h> 标头和 CX_LIMITED_RANGE/FP_CONTRACT pragma 宏。 某些元素（如标准 IO 函数中参数说明符的含义）默认采用旧的解释。 可以使用 /Zc 编译器一致性选项并指定链接器选项来控制库一致性的某些方面。

## <a name="c-standard-library"></a>C++ 标准库

|C++ 标准库|特征|选项|预处理器指令|
|----------------------------|---------------------|------------|-----------------------------|
|libcpmt.lib|多线程, 静态链接|**/MT**|_MT|
|msvcprt.lib|多线程动态链接（MSVCPversion.dll 的导入库）|**/MD**|_MT, _DLL|
|libcpmtd.lib|多线程, 静态链接|**/MTd**|_DEBUG, _MT|
|msvcprtd.lib|多线程动态链接（MSVCPversionD.DLL 的导入库）|**/MDd**|_DEBUG, _MT, _DLL|

当构建项目的发行版时，默认情况下，将链接其中一个基本 C 运行时库（libcmt.lib、msvcmrt.lib、msvcrt.lib），具体取决于你选择的编译器选项（多线程、DLL、/clr)。 如果在代码中包含其中一个 [C++ 标准库标头文件](../standard-library/cpp-standard-library-header-files.md)，则将在编译时通过 Visual C++ 自动链接 C++ 标准库。 例如:

```cpp
#include <ios>
```

对于二进制兼容性，可通过单个导入库指定多个 DLL 文件。 版本更新可能会引入点库，点库是引入新的库功能的 单独的 Dll。 例如，Visual Studio 2017 版 15.6 引入了 msvcp140_1.dll 以支持其他标准库功能，而不会破坏由 msvcp140.dll 支持的 ABI。 适用于 Visual Studio 2017 版本 15.6 的工具集中包含的 msvcprt.lib 导入库支持两个 DLL，且此版本的 vcredist 安装两个 DLL。 传送后，点库具有固定 ABI，且不会在以后的点库中包含依赖项。

## <a name="what-problems-exist-if-an-application-uses-more-than-one-crt-version"></a>如果应用程序使用多个 CRT 版本，将存在什么问题？

如果有多个 DLL 或 EXE，则无论是否正在使用不同版本的 Visual C++，你都可以具有多个 CRT。 例如，将 CRT 静态链接到多个 Dll 可能存在相同的问题。 遇到此静态 CRT 问题的开发人员已被告知使用 **/MD** 进行编译，以便使用 CRT DLL。 如果 Dll 跨 DLL 边界传递 CRT 资源，则可能遇到与 CRT 不匹配的问题，需要使用 Visual C++ 重新编译项目。

如果程序使用多个版本的 CRT，则跨 DLL 边界传递某些 CRT 对象（如文件句柄、区域设置和环境变量）时需注意。 有关所涉及问题以及如何解决这些问题的详细信息，请参阅[跨 DLL 边界传递 CRT 对象时可能的错误](../c-runtime-library/potential-errors-passing-crt-objects-across-dll-boundaries.md)。

## <a name="see-also"></a>请参阅

[C 运行时库参考](../c-runtime-library/c-run-time-library-reference.md)
