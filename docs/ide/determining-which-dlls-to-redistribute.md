---
title: "确定哪些 Dll 重新分发的 |Microsoft 文档"
ms.custom: 
ms.date: 09/21/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- redistributing DLLs
- DLLs [C++], redistributing
- dependencies [C++], application deployment and
- application deployment [C++], DLL redistribution
- deploying applications [C++], DLL redistribution
ms.assetid: f7a2cb42-fb48-42ab-abd2-b35e2fd5601a
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: a3cc7b80e16abeecc756e7fa480c7bfe71682382
ms.sourcegitcommit: 54035dce0992ba5dce0323d67f86301f994ff3db
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/03/2018
---
# <a name="determining-which-dlls-to-redistribute"></a>确定要重新分发的 DLL

生成使用由 Visual Studio 提供的库 Dll 的应用程序时，应用程序的用户还必须在应用程序可以运行其计算机上具有这些 Dll。 由于大多数用户可能没有安装 Visual Studio，因此你必须为他们提供这些 DLL。 Visual Studio 提供这些 Dll 作为*可再发行文件*可包括在应用程序安装程序。

若要更加轻松地包括与安装可再发行 Dll，它们都可用作独立*可再发行组件包*。 这些是特定于体系结构的集中部署用于安装用户的计算机上的可再发行文件的可执行文件。 例如，vcredist\_x86.exe 安装 x86 的 32 位库计算机、 vcredist\_x64.exe 安装 x64 的 32 位和 64 位库计算机和 vcredist\_ARM.exe arm 安装库计算机。 我们建议集中部署，因为 Microsoft 可以使用 Windows 更新服务独立更新这些库。 除了 Visual Studio 安装中的副本，当前的可再发行组件包是可供下载上[VisualStudio.com/Downloads](https://www.visualstudio.com/downloads/)其他工具和框架部分中。

你部署的可再发行组件包的主版本号必须与用于创建你的应用程序的 Visual Studio 工具集版本匹配。 Visual Studio 2017 和 Visual Studio 2015 具有兼容的工具集版本数量，这意味着可再发行文件可能会使用通过使用 2015年工具集生成的应用程序的 Visual Studio 2017。 尽管它们可能兼容，我们不支持使用通过使用 2017年工具集生成的应用程序中的 2015年可再发行文件。 我们仅支持使用是相同或比工具集版本新的可再发行组件包。 有关最新支持可再发行组件包的较旧工具集的链接，请参阅[最新支持 Visual c + + 下载](https://support.microsoft.com/en-us/help/2977003/the-latest-supported-visual-c-downloads)。 可能通过搜索找到特定的早期版本的可再发行组件包[Microsoft Download Center](http://go.microsoft.com/fwlink/p/?LinkId=158431) "Visual c + + 可再发行组件包"。

包括与安装可再发行 Dll 另一种方法是使用*的合并模块*。 这些 Microsoft 安装程序模块包含在中并由应用程序安装程序安装。 在 Visual Studio 安装目录中找到可再发行 Dll 的合并模块\\VC\\Redist\MSVC\\*版本*\\MergeModules\\. 在早期版本的 Visual Studio 中，找到这些文件在你\\Program Files 或\\常见文件中的 Program Files (x86) 目录\\合并模块子目录。 有关使用这些文件的详细信息，请参阅[使用合并模块重新发布组件](../ide/redistributing-components-by-using-merge-modules.md)。

单个可再发行 Dll 也包括在你的 Visual Studio 的安装。 默认情况下，他们都安装在 Visual Studio 安装目录\\VC\\Redist\\MSVC\\*版本*文件夹。 *版本*数字可能表示的一组单个通用的可再发行文件不同的次内部版本号。 使用最新任何的版本库 DLL 文件、 可再发行组件包或在这些目录中找到的合并模块。 通过在你的应用程序所在的目录中安装它们，你可以为本地部署中，使用这些库。 我们不建议本地部署，因为它使你负责将更新传递到部署的应用程序。 使用可再发行组件包集中部署是首选方法。

若要确定必须与应用程序一起重新发布的 DLL，请收集应用程序所依赖的 DLL 列表。 这些通常列出为导入到链接器库输入。 某些库，如 vcruntime 和通用 C 运行时库 (UCRT)，包括默认情况下。 如果你的应用程序或其依赖项之一使用 LoadLibrary 动态加载 DLL，该 DLL 可能不会列出到链接器输入中。 收集动态加载的 Dll 的列表的一种方法是在你的应用上运行 Dependency Walker (depends.exe) 中所述[了解 Visual c + + 应用程序的依赖关系](../ide/understanding-the-dependencies-of-a-visual-cpp-application.md)。 遗憾的是，此工具已过时，并可能会报告它找不到某些 Dll。

在必须依赖项列表，请将其进行比较到在 Microsoft Visual Studio 安装目录下找到的 Redist.txt 文件中链接的列表或"REDIST 列表"可再发行 dll 中的"可分发代码文件"部分引用你的 Visual Studio 副本的 Microsoft 软件许可条款。 Visual Studio 2017，请参阅[Microsoft Visual Studio 2017 （包括实用程序、 可扩展性和 BuildServer 文件） 的可分发代码](http://go.microsoft.com/fwlink/p/?linkid=823098)。 Visual Studio 2015，请参阅[Microsoft Visual Studio 2015 和 Microsoft Visual Studio 2015 SDK （包括实用程序和 BuildServer 文件） 的可分发代码](http://go.microsoft.com/fwlink/p/?linkid=799794)。 对于 Visual Studio 2013，列表中未提供联机[Microsoft Visual Studio 2013 和 Microsoft Visual Studio 2013 SDK 的可分发代码](http://go.microsoft.com/fwlink/p/?LinkId=313603)。

在 Visual Studio 2015 之前的 Visual Studio 版本，C 运行库 (CRT) 已作为可再发行 DLL msvc 包含*版本*.dll。 从 Visual Studio 2015 开始，CRT 中的函数已重构为 vcruntime 和 UCRT 中。 UCRT 现在 Windows 10 中，由 Windows 更新的系统组件。 它是在所有 Windows 10 操作系统上可用。 若要部署应用程序与更早的操作系统，你可能需要重新分发的 UCRT 也。 UCRT 的早期版本是包含在 Visual Studio 可再发行文件，它仅安装操作系统早于 Windows 10，并且只，如果尚未安装 UCRT 的任何版本。 作为 Microsoft 系统更新包的下层系统 UCRT 的可安装版本，请参阅[Windows 10 通用 C 运行时](https://www.microsoft.com/en-us/download/details.aspx?id=48234)Microsoft 下载中心中。

无法重新发布 Visual Studio 中包含的所有文件；只允许重新发布 Redist.txt 或在线“REDIST 列表”中指定的文件。 调试版本的应用程序和各种 Visual C++ 调试 DLL 是不可再发行的。 有关详细信息，请参阅[选择部署方法](../ide/choosing-a-deployment-method.md)。

下表描述了应用程序可能依赖的一些 Visual C++ DLL。

|Visual C++ 库|描述|适用对象|
|--------------------------|-----------------|----------------|
|vcruntime*版本*.dll|对于本机代码的运行时库。|使用常规 C 和 c + + 语言启动和终止服务应用程序。|
|vccorlib*版本*.dll|托管代码的运行时库。|使用托管代码的 c + + 语言服务应用程序。|
|msvcp*版本*.dll|对于本机代码的 c + + 标准库。|应用程序使用[c + + 标准库](../standard-library/cpp-standard-library-reference.md)。|
|concrt*版本*.dll|对于本机代码的并发运行时库。|应用程序使用[并发运行时](../parallel/concrt/concurrency-runtime.md)。|
|mfc*版本*.dll|Microsoft 基础类 (MFC) 库。|应用程序使用[MFC 库](../mfc/mfc-desktop-applications.md)。|
|mfc*版本**语言*.dll|Microsoft 基础类 (MFC) 库资源。|对 MFC 使用特定语言资源的应用程序。|
|mfc*版本*u.dll|具有 Unicode 支持的 MFC 库。|应用程序使用[MFC 库](../mfc/mfc-desktop-applications.md)并需要 Unicode 支持。|
|mfcmifc80.dll|MFC 托管接口库。|应用程序使用[MFC 库](../mfc/mfc-desktop-applications.md)与[Windows 窗体控件](/dotnet/framework/winforms/controls/index)。|
|mfcm*版本*.dll|MFC 托管库。|应用程序使用[MFC 库](../mfc/mfc-desktop-applications.md)与[Windows 窗体控件](/dotnet/framework/winforms/controls/index)。|
|mfcm*版本*u.dll|具有 Unicode 支持的 MFC 托管库。|应用程序使用[MFC 库](../mfc/mfc-desktop-applications.md)与[Windows 窗体控件](/dotnet/framework/winforms/controls/index)并需要 Unicode 支持。|
|vcamp*版本*.dll|面向本机代码的 AMP 库。|应用程序使用[c + + AMP 库](../parallel/amp/cpp-amp-cpp-accelerated-massive-parallelism.md)代码。|
|vcomp*版本*.dll|面向本机代码的 OpenMP 库。|应用程序使用[c + + OpenMP 库](../parallel/openmp/openmp-in-visual-cpp.md)代码。|

> [!NOTE]
> 不再需要将活动模板库重新发布为单独的 DLL。 其功能已移至标头和静态库。

有关如何重新发布你的应用程序使用这些 Dll 的详细信息，请参阅[重新分发 Visual c + + 文件](../ide/redistributing-visual-cpp-files.md)。 有关示例，请参阅[部署示例](../ide/deployment-examples.md)。

通常情况下，无需重新发布系统 DLL，因为它们是操作系统的一部分。 但可能存在例外，例如，当应用程序将在几个版本的 Microsoft 操作系统上运行时。 在这种情况下，请务必阅读相应的许可条款。 此外，请尝试通过 Microsoft 提供的 Windows 更新、Service Pack 或使用可再发行组件包来升级系统 DLL。

## <a name="see-also"></a>请参阅

[选择部署方法](../ide/choosing-a-deployment-method.md)

[部署桌面应用程序](../ide/deploying-native-desktop-applications-visual-cpp.md)
