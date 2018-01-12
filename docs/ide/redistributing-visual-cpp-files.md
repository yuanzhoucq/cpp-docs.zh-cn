---
title: "重新分发 Visual c + + 文件 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- application deployment [C++], file redistributing
- redistributing applications [C++]
- deploying applications [C++], file redistributing
- file redistribution [C++]
- redistributing applications [C++], about redistributing applications
ms.assetid: d201b2ce-36f1-44e5-a96c-0db81a1ba652
caps.latest.revision: "50"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 106123557c4efab5ccddf9f1292570d36b0f8313
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="redistributing-visual-c-files"></a>重新分发 Visual C++ 文件
部署应用程序时，还必须部署支持该应用程序所需的文件。 如果其中有任何文件由 Microsoft 提供，请检查是否允许你重新发布这些文件。 若要查看 Visual Studio 许可条款，请参阅有关 Microsoft Visual Studio 对话框中，在 IDE 中，在许可条款链接，或下载[Microsoft 软件许可条款](http://go.microsoft.com/fwlink/p/?LinkId=831114)文件。 若要查看 Microsoft 软件许可条款，某些版本的 Visual Studio 的"可分发代码"部分中引用的"REDIST 列表"，请参阅[Microsoft Visual Studio 2017 和 Microsoft Visual Studio 2017 可分发代码SDK （包括实用程序和 BuildServer 文件）](http://go.microsoft.com/fwlink/p/?LinkId=823098)，或 Visual Studio 2015，请参阅[Microsoft Visual Studio 2015 和 Microsoft Visual Studio 2015 SDK 的可分发代码](http://go.microsoft.com/fwlink/p/?LinkId=523763)。 有关可再发行文件的详细信息，请参阅[确定要重新分发的 Dll](../ide/determining-which-dlls-to-redistribute.md)和[部署示例](../ide/deployment-examples.md)。  
  
 若要部署可再发行 Visual c + + 文件，你可以使用 Visual c + + 可再发行组件包 (VCRedist\_x86.exe，VCRedist\_x64.exe 或 VCRedist\_arm.exe)，而且包含在 Visual Studio。 可以在 Visual Studio 2017，在程序文件 [(x86)] 中找到这些文件\\Microsoft Visual Studio\\2017年\\_版本_\\VC\\Redist\\MSVC\\_lib 版本_文件夹，其中_版本_是安装，Visual Studio 版本和_lib 版本_的版本若要重新分发的库。 在 Visual Studio 2015 中，找到这些文件可以在你的 Visual Studio 安装目录下位于 Program Files [(x86)] \Microsoft Visual Studio*版本*\VC\redist\\*区域设置*\\. 另一个选项是使用可再发行合并模块 （.msm 文件），这会在 Visual Studio 2017 可以在 Program Files [(x86)] 中找到\\Microsoft Visual Studio\\2017年\\_版本_\\VC\\Redist\\MSVC\\_lib 版本_\\MergeModules\\文件夹。 Visual Studio 2015 中这些可以找到的 Program Files [(x86)] \common 模块\\。 还有可能直接安装可再发行组件中的 Visual c + + Dll*应用程序本地文件夹*，它是包含可执行应用程序文件的文件夹。 出于维护原因，不建议使用此安装位置。  
  
 Visual C++ Redistributable Package 将安装并注册所有 Visual C++ 库。 如果你使用其中一个包，则必须将其设置为在目标系统上运行，以此作为安装应用程序的先决条件。 我们建议你在部署中使用这些包，因为它们能够启用 Visual C++ 库的自动更新。 有关如何使用这些包的示例，请参阅[演练： 部署 Visual c + + 应用程序通过使用 Visual c + + 可再发行组件包](../ide/deploying-visual-cpp-application-by-using-the-vcpp-redistributable-package.md)。  
  
 每个 Visual C++ 可再发行包都会检查计算机上是否存在较新版本。 如果找到较新版本，则不安装包。 从 Visual Studio 2015 开始，可再发行包会显示一个表明安装失败的错误消息。 如果通过使用运行包**/quiet/**标志，任何错误消息显示为。 在任一情况下，Microsoft 安装程序都会记录错误，并且会将错误结果返回给调用方。 从 Visual Studio 2015 包开始，你可以通过检查注册表以确定是否安装了较新版本来避免此错误。 当前安装的版本存储在 HKEY_LOCAL_MACHINE\SOFTWARE [\Wow6432Node] \Microsoft\VisualStudio\\_vs 版本_\VC\Runtimes\\{x86 | x64 |ARM} 键，其中_vs 版本_的版本号为 Visual Studio (14.0 Visual Studio 2015 和 Visual Studio 自 2017 年 1，因为更新自 2017 年 1 可再发行组件是 2015年版本与二进制兼容)，和其中的键是ARM、 x86 或 x64 具体取决于平台的已安装了 vcredist 版本。 (你不需要检查 Wow6432Node 子项下，除非你使用注册表编辑器查看已安装 x86 版本在 x64 上的包平台。)版本号存储在 REG_SZ 字符串值**版本**，也可以在的一套**主要**，**次要**， **Bld**，和**Rbld** REG_DWORD 值。 若要避免在安装时出错，则必须跳过的可再发行组件包的安装当前安装的版本是最新。  
  
 如果使用包含 Visual C++ DLL 的合并模块，则必须将该模块包含在用于部署应用程序的 Windows Installer 包（或类似的安装包）中。 有关详细信息，请参阅[通过使用合并模块重新发布](../ide/redistributing-components-by-using-merge-modules.md)。 有关示例，请参阅[演练： 部署 Visual c + + 应用程序通过使用安装项目](../ide/walkthrough-deploying-a-visual-cpp-application-by-using-a-setup-project.md)，其中还说明了如何使用 InstallShield Limited Edition 创建安装包。  
  
## <a name="potential-run-time-errors"></a>可能的运行时错误  
 如果 Visual c + + 库 DLL 不可访问，并且 Windows 无法加载此应用程序，可能会显示此消息：**此应用程序未能启动，因为 MSVCR\<版本号 > 找不到.dll。重新安装应用程序可能会修复此问题。”**  
  
 若要解决这种错误，请确保你的应用程序正确生成，并且 Visual C++ 库正确部署到目标系统中。 有关详细信息，请参阅[了解 Visual c + + 应用程序的依赖关系](../ide/understanding-the-dependencies-of-a-visual-cpp-application.md)。  
  
## <a name="related-topics"></a>相关主题  
  
|标题|描述|  
|-----------|-----------------|  
|[使用合并模块重新发布](../ide/redistributing-components-by-using-merge-modules.md)|描述如何使用 Visual c + + 可再发行合并模块将安装 Visual c + + 运行库作为共享 Dll %windir%\system32\ 文件夹中。|  
|[重新分发 Visual C++ ActiveX 控件](../ide/redistributing-visual-cpp-activex-controls.md)|描述如何重新发布使用 ActiveX 控件的应用程序。|  
|[重新分发数据库支持文件](../ide/redistributing-database-support-files.md)|讨论如何重新发布用于数据访问对象 (DAO) 以及 Microsoft 数据访问 SDK 中的数据库技术的支持文件。|  
|[重新分发 MFC 库](../ide/redistributing-the-mfc-library.md)|描述如何重新发布使用 MFC 的应用程序。|  
|[重新分发 ATL 应用程序](../ide/redistributing-an-atl-application.md)|描述如何重新发布使用 ATL 的应用程序。 从 Visual Studio 2012 开始，无需 ATL 的可再发行库。|  
|[部署示例](../ide/deployment-examples.md)|指向演示如何部署 Visual C++ 应用程序的示例的链接。|  
|[部署桌面应用程序](../ide/deploying-native-desktop-applications-visual-cpp.md)|介绍 Visual C++ 部署概念和技术。|