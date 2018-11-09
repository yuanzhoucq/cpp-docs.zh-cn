---
title: 将代码升级到通用 CRT
ms.date: 03/31/2017
ms.assetid: eaf34c1b-da98-4058-a059-a10db693a5ce
ms.openlocfilehash: 5e417df380ff2239b7c09ba32cc02b784e9343d2
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50668606"
---
# <a name="upgrade-your-code-to-the-universal-crt"></a>将代码升级到通用 CRT

在 Visual Studio 2015 中，重构了 Microsoft C 运行时库 (CRT)。 将标准 C 库、POSIX 扩展和 Microsoft 特定的函数、宏和全局变量移动到了新库，即通用 C 运行时库（通用 CRT 或 UCRT）。 将 CRT 特定于编译器的组件移动到了新的 vcruntime 库中。

UCRT 现为 Windows 组件，并作为 Windows 10 的一部分提供。 UCRT 支持基于 C 调用约定的稳定 ABI，且谨遵 ISO C99 标准（仅有少数例外）。 它将不再绑定到特定版本的编译器。 可以在 Visual Studio 2015 或 Visual Studio 2017 支持的任何 Windows 版本上使用 UCRT。 其好处是使用者不再需要在每次升级 Visual Studio 时都以新版本的 CRT 为目标来更新自己的版本。

使用此重构时，许多 CRT 头文件、库文件和可再发行组件的名称或位置以及代码所需的部署方法都有所改变。 此外，还在 UCRT 中添加或更改了许多功能和宏以提高对标准的一致性。 若要利用这些更改，必须更新现有代码和项目生成系统。

## <a name="where-to-find-the-universal-crt-files"></a>在哪里可以找到通用 CRT 文件

作为 Windows 组件，UCRT 库文件和标头现在是 Windows 软件开发工具包 (SDK) 的一部分。 安装 Visual Studio 时，会同时安装使用 UCRT 时所需的 Windows SDK 的部件。 Visual Studio 安装程序将 UCRT 头、库和 DLL 文件的位置添加到 Visual Studio 项目生成系统所使用的默认路径。 当更新 Visual C++ 项目时，如果它们使用默认项目设置，IDE 将自动为头文件查找新位置，并且链接器会自动使用新的默认 UCRT 和 vcruntime 库。 同样，如果使用开发人员命令提示执行命令行生成，则包含头和库路径的环境变量也会更新并自动工作。

标准 C 库头文件现可在 Windows SDK 中找到，其位于特定于 SDK 版本的目录的包含文件夹中。 头文件的常规位置在 Windows Kits\\10\\Include\\_sdk-version_\\ucrt 下的 Program Files 或 Program Files (x86) 目录中，其中 _sdk-version_ 对应于 Windows 版本或更新，例如，用于 Windows 10 周年更新的 10.0.14393.0。

UCRT 静态库和动态链接存根库位于 Windows Kits\\10\\Lib\\_sdk-version_\\ucrt\\_architecture_ 下的 Program Files 或 Program Files (x86) 目录下，其中 _architecture_ 是 ARM、x86 或 X64。 零售和调试静态库分别是 libucrt.lib 和 libucrtd.lib，用于 UCRT DLL 的库是 ucrt.lib 和 ucrtd.lib。

零售和调试 UCRT DLL 位于不同的位置。 零售 DLL 可再发行，可以在 Program Files 或 Program Files (x86) 目录的 Windows Kits\\10\\Redist\\ucrt\\DLLs\\architecture\. 中找到 调试 UCRT 库不可再发行，可以在 Program Files 或 Program Files (x86) 目录的 Windows Kits\\10\\bin\\architecture\\ucrt 文件夹中找到。

C 和 C++ 编译器特定的运行时支持库 **vcruntime**，包含支持程序启动所需的代码以及异常处理和内部函数等功能。 库及其头文件仍位于 Program Files 或 Program files (x86) 目录中特定于版本的 Microsoft Visual Studio 文件夹中。 在 Visual Studio 2017 中，标头位于 Microsoft Visual Studio\\2017\\_edition_\\VC\\Tools\\MSVC\\_lib-version_\\include 中，链接库位于 Microsoft Visual Studio\\2017\\_edition_\\VC\\Tools\\MSVC\\_lib-version_\\lib\\_architecture_ 中，其中 _edition_ 是安装的 Visual Studio 版本，_lib-version_ 是库的版本，而 _architecture_ 是处理器体系结构。 OneCore 和 Store 的链接库也位于库文件夹中。 静态库的零售和调试版本分别是 libvcruntime.lib 和 libvcruntimed.lib。 动态链接零售和调试存根库分别是 vcruntime.lib 和 vcruntimed.lib。

更新 Visual C++ 项目时，如果将项目的链接器属性“忽略所有默认库”设置为“是”，或在命令行上使用 `/NODEFAULTLIB` 链接器选项，则必须更新库的列表，使其包含新的重构库。 将旧的 CRT 库（例如 libcmt.lib、libcmtd.lib、msvcrt.lib 或 msvcrtd.lib）替换为等效的重构库。 有关要使用的特定库的信息，请参阅 [CRT 库的功能](../c-runtime-library/crt-library-features.md)。

## <a name="deployment-and-redistribution-of-the-universal-crt"></a>通用 CRT 的部署和重新分发

因为 UCRT 现在是Microsoft Windows 操作系统组件，它作为操作系统的一部分包含在 Windows 10 中，可通过较旧操作系统（Windows Vista 到 Windows 8.1）的 Windows 更新获得。 有一个可重新分发的版本适用于 Windows XP。 作为操作系统组件，UCRT 更新和服务由 Windows 更新进行管理（独立于 Visual Studio 和 Microsoft C++ 编译器版本）。 由于 UCRT 是 Windows 组件，出于安全性、易于更新以及更小的映像大小的考虑，强烈建议为应用集中部署 UCRT。

可以在 Visual Studio 2015 或 Visual Studio 2017 支持的任何 Windows 版本上使用 UCRT。 可以使用 vcredist 包重新分发它，以便支持 Windows 10 以外的 Windows 版本。 Vcredist 包包含 UCRT 组件，并自动将这些组件安装在默认情况下不安装它们的 Windows 操作系统上。 有关详细信息，请参阅[重新分发 Visual C++ 文件](../ide/redistributing-visual-cpp-files.md)。

支持 UCRT 的本地应用部署（尽管由于性能和安全原因不推荐）。 用于本地应用部署的 DLL 作为 Windows SDK 的一部分包含在 **redist** 子目录下。 所需的 DLL 包括 ucrtbase.dll 和名为 api-ms-win-_subset_.dll. 的一组 **APISet forwarder** DLL。 每个操作系统所需的 DLL 集各不相同，因此建议在使用应用本地部署时包括所有 DLL。 有关应用本地部署的其他详细信息和注意事项，请参阅 [Visual C++ 中的部署](../ide/deployment-in-visual-cpp.md)。

## <a name="changes-to-the-universal-crt-functions-and-macros"></a>对通用 CRT 函数和宏的更改

已在 UCRT 中添加或更新许多功能，以提高 ISO C99 一致性和解决代码质量和安全问题。 在某些情况下，这需要中断对库的更改。 如果在使用较旧版本的 CRT 时代码编译顺畅，但在使用 UCRT 时编译中断，则必须更改代码以利用这些更新和功能。 有关通用 CRT 中出现的 CRT 更改和更新中断情况的详细列表，请参阅 Visual C++ 更改历史记录的 [C 运行时库 (CRT)](visual-cpp-change-history-2003-2015.md#BK_CRT) 部分。 它包括受影响的标头和函数的列表，可以使用它们来标识代码中需要的更改。

## <a name="see-also"></a>请参阅

[Visual C++ 移植和升级指南](visual-cpp-porting-and-upgrading-guide.md)<br/>
[潜在的升级问题概述 (Visual C++)](overview-of-potential-upgrade-issues-visual-cpp.md)<br/>
[从 Visual C++ 早期版本升级项目](upgrading-projects-from-earlier-versions-of-visual-cpp.md)<br/>
[Visual C++ 更改历史记录（2003 - 2015）](visual-cpp-change-history-2003-2015.md)<br/>
[Visual Studio 2017 中 C++ 的符合性改进](../cpp-conformance-improvements-2017.md)