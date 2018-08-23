---
title: 重新分发 Visual C++ 文件 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- application deployment [C++], file redistributing
- redistributing applications [C++]
- deploying applications [C++], file redistributing
- file redistribution [C++]
- redistributing applications [C++], about redistributing applications
ms.assetid: d201b2ce-36f1-44e5-a96c-0db81a1ba652
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e67ad87f1dce47f3d02dcbe907285cf0513a8ce9
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33337543"
---
# <a name="redistributing-visual-c-files"></a>重新分发 Visual C++ 文件

> [!NOTE]
> 你转到此处是否因为想下载某个 Visual C++ 运行时文件？ 请转到 [Microsoft](http://www.microsoft.com/) 网站并在搜索框输入“Visual C++ 可再发行组件”。 下载并安装适用于你的计算机体系结构的可再发行组件包（例如，如果运行 64 位 Windows，请使用 x64）以及所需的 Visual C++ 版本（例如 2015 版）。

部署应用程序时，还必须部署支持该应用程序所需的文件。 如果其中有任何文件由 Microsoft 提供，请检查是否允许你重新发布这些文件。 若要查看 Visual Studio 许可条款，请在 IDE 中的“关于 Microsoft Visual Studio”对话框查看许可条款链接，或下载 [Microsoft 软件许可条款](http://go.microsoft.com/fwlink/p/?LinkId=831114)文件。 若要查看某些版本的 Visual Studio 的 Microsoft 软件许可条款中“可分发代码”部分引用的“REDIST 列表”，请参阅 [Microsoft Visual Studio 2017 和 Microsoft Visual Studio 2017 SDK 的可分发代码（包括实用程序和 BuildServer 文件）](http://go.microsoft.com/fwlink/p/?LinkId=823098)，或者如果使用的是 Visual Studio 2015，请参阅 [Microsoft Visual Studio 2015 和 Microsoft Visual Studio 2015 SDK 的可分发代码](http://go.microsoft.com/fwlink/p/?LinkId=523763)。 有关可再发行文件的详细信息，请参阅[确定要重新分发的 Dll](../ide/determining-which-dlls-to-redistribute.md) 和[部署示例](../ide/deployment-examples.md)。

若要部署可再发行 Visual C++ 文件，可以使用包含在 Visual Studio 中的 Visual C++ 可再发行组件包（VCRedist\_x86.exe、VCRedist\_x64.exe 或 VCRedist\_arm.exe）。 在 Visual Studio 2017 中，可在 Program Files[ (x86)]\\Microsoft Visual Studio\\2017\\_edition_\\VC\\Redist\\MSVC\\_lib-version_ 文件夹中找到这些文件，其中 _edition_ 是所安装的 Visual Studio 版本，_lib-version_ 是要重新分发的库的版本。 在 Visual Studio 2015 中，可在 Program Files [(x86)]\Microsoft Visual Studio version\VC\redist\\locale\\ 中的 Visual Studio 安装目录下找到这些文件。 另一个选项是使用可再发行合并模块（.msm 文件），可在 Program Files [(x86)]\\Microsoft Visual Studio\\2017\\_edition_\\VC\\Redist\\MSVC\\_lib-version_\\MergeModules\\ 文件夹中的 Visual Studio 2017 找到该文件。 在 Visual Studio 2015 中，可在 Program Files [(x86)]\Common Files\Merge Modules\\ 找到这些文件。 还可以在应用程序本地文件夹（这是包含可执行应用程序文件的文件夹）中直接安装可再发行 Visual C++ DLL。 出于维护原因，不建议使用此安装位置。

Visual C++ Redistributable Package 将安装并注册所有 Visual C++ 库。 如果你使用其中一个包，则必须将其设置为在目标系统上运行，以此作为安装应用程序的先决条件。 我们建议你在部署中使用这些包，因为它们能够启用 Visual C++ 库的自动更新。 有关如何使用这些包的示例，请参阅[演练：使用 Visual C++ 可再发行组件包部署 Visual C++ 应用程序](../ide/deploying-visual-cpp-application-by-using-the-vcpp-redistributable-package.md)。

每个 Visual C++ 可再发行包都会检查计算机上是否存在较新版本。 如果找到较新版本，则不安装包。 从 Visual Studio 2015 开始，可再发行包会显示一个表明安装失败的错误消息。 如果使用 /quiet 标志运行包，则不会显示错误消息。 在任一情况下，Microsoft 安装程序都会记录错误，并且会将错误结果返回给调用方。 从 Visual Studio 2015 包开始，可以检查注册表是否安装了更新的版本，从而避免出现此错误。 当前所安装的版本存储在 HKEY_LOCAL_MACHINE\SOFTWARE[\Wow6432Node]\Microsoft\VisualStudio\\_vs-version_\VC\Runtimes\\{x86|x64|ARM} 键中，其中 _vs-version_ 是 Visual Studio 的版本号（由于更新的 2017 可再发行组件与 2015 版是二进制兼容的，所以 Visual Studio 2015 和 Visual Studio 2017 的版本号都为 14.0），根据平台所安装的 vcredist 版本，该键可能为 ARM、x86 或 x64。 （不需要在 Wow6432Node 子键下进行检查，除非要使用 RegEdit 查看在 x64 平台上安装的 x86 包的版本。）版本号存储在 REG_SZ 字符串值“Version”和“Major”、“Minor”、“Bld” 和 “Rbld” 等一系列 REG_DWORD 值中。 为了避免在安装时出错，如果当前安装的版本较新，必须跳过可再发行组件包的安装。

如果使用包含 Visual C++ DLL 的合并模块，则必须将该模块包含在用于部署应用程序的 Windows Installer 包（或类似的安装包）中。 有关详细信息，请参阅[使用合并模块重新分发](../ide/redistributing-components-by-using-merge-modules.md)。 有关示例，请参阅[演练：使用安装项目部署 Visual C++ 应用程序](../ide/walkthrough-deploying-a-visual-cpp-application-by-using-a-setup-project.md)，该演练还演示了如何使用 InstallShield Limited Edition 创建安装包。

## <a name="potential-run-time-errors"></a>可能的运行时错误

若 Windows 无法找到应用程序所需的某个可再发行库 DLL，可能会出现类似这样的消息：“因为找不到 library.dll，此应用程序未能启动。 重新安装应用程序可能会修复此问题。”

若要解决这种错误，请确保你的应用程序安装程序正确生成，并且可再发行库正确部署到目标系统中。 有关详细信息，请参阅[了解 Visual C++ 应用程序的依赖项](../ide/understanding-the-dependencies-of-a-visual-cpp-application.md)。

## <a name="related-topics"></a>相关主题

|标题|描述|
|-----------|-----------------|
|[使用合并模块重新分发](../ide/redistributing-components-by-using-merge-modules.md)|描述如何使用 Visual C++ 可再发行合并模块将 Visual C++ 运行库作为共享 DLL 安装到 %windir%\system32\ 文件夹中。|
|[重新分发 Visual C++ ActiveX 控件](../ide/redistributing-visual-cpp-activex-controls.md)|描述如何重新发布使用 ActiveX 控件的应用程序。|
|[重新分发数据库支持文件](../ide/redistributing-database-support-files.md)|讨论如何重新发布用于数据访问对象 (DAO) 以及 Microsoft 数据访问 SDK 中的数据库技术的支持文件。|
|[重新分发 MFC 库](../ide/redistributing-the-mfc-library.md)|描述如何重新发布使用 MFC 的应用程序。|
|[重新分发 ATL 应用程序](../ide/redistributing-an-atl-application.md)|描述如何重新发布使用 ATL 的应用程序。 从 Visual Studio 2012 开始，无需 ATL 的可再发行库。|
|[部署示例](../ide/deployment-examples.md)|指向演示如何部署 Visual C++ 应用程序的示例的链接。|
|[部署桌面应用程序](../ide/deploying-native-desktop-applications-visual-cpp.md)|介绍 Visual C++ 部署概念和技术。|