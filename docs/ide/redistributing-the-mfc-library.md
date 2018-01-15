---
title: "重新分发 MFC 库 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- MFC, redistributing
- redistributing MFC library
ms.assetid: 72714ce1-385e-4c1c-afa5-96b03e873866
caps.latest.revision: "32"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 9ca153ec9ca079bf13b1c1c1dcedd6e41497307f
ms.sourcegitcommit: 54035dce0992ba5dce0323d67f86301f994ff3db
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/03/2018
---
# <a name="redistributing-the-mfc-library"></a>重新分发 MFC 库
如果动态链接到 MFC 库的应用程序，你必须重新分发匹配的 MFC DLL。 例如，如果使用 Visual Studio 2015 中使用 MFC 附带的版本生成 MFC 应用程序，你必须重新分发 mfc140.dll 或 mfc140u.dll，具体取决于是否将您的应用程序编译窄字符或 Unicode 支持。  
  
> [!NOTE]
>  在 Visual Studio 2015 RTM 中的可再发行文件目录中省略 mfc140.dll 文件。 你可以使用由 Visual Studio 2015 中安装的 Windows\system32 和 Windows\syswow64 目录相反的版本。  
  
 由于所有 MFC Dll 都使用 C 运行库 (CRT) 的共享的版本，因此你可能还需要重新分发 CRT。 使用 Visual Studio 2015 附带的 MFC 的版本使用通用的 CRT 库作为 Windows 10 的一部分分发。 若要运行早期版本的 Windows 上使用 Visual Studio 2015 生成 MFC 应用程序，必须重新分发通用 CRT。 有关如何重新发布通用的 CRT，作为操作系统组件或通过使用本地部署的信息，请参阅[简介通用 CRT](http://go.microsoft.com/fwlink/p/?linkid=617977)。 若要下载通用 CRT 支持的 Windows 版本上的中央部署，请参阅[Windows 10 通用 C 运行时](http://go.microsoft.com/fwlink/p/?LinkId=619489)。 在 Windows SDK 中找到可再发行组件体系结构的特定版本的本地部署的是 ucrtbase.dll。 默认情况下，Visual Studio 安装在 C:\Program Files (x86) \Windows Kits\10\Redist\ucrt\DLLs\ 这些特定于体系结构的子目录中。  
  
 如果使用早期版本的 MFC 库生成你的应用程序，你必须重新分发可再发行文件目录从匹配的 CRT DLL。 例如，如果使用 Visual Studio 2013 (vc120) 工具集生成 MFC 应用程序，你必须重新分发 msvcr120.dll。 你还必须重新分发匹配 mfc`<version>`u.dll 或 mfc`<version>`.dll。  
  
 如果静态链接到 MFC 应用程序 (即，如果你指定**在静态库中使用 MFC**上**常规**选项卡中**属性页**对话框中)，你还没有若要重新分发 MFC DLL。 但是，虽然静态链接可能适用于测试和内部部署的应用程序中，我们建议，你并不使用它重新分发 MFC。 有关建议的策略用于部署 Visual c + + 库的详细信息，请参阅[选择部署方法](../ide/choosing-a-deployment-method.md)。  
  
 如果你的应用程序将使用实现 WebBrowser 控件的 MFC 类 (例如， [CHtmlView 类](../mfc/reference/chtmlview-class.md)或[CHtmlEditView 类](../mfc/reference/chtmleditview-class.md))，我们建议您同时安装的最新版本Microsoft Internet Explorer，以便目标计算机都具有最新的公共控件文件。 （最低限度上，在 Internet Explorer 4.0 是必需的。有关如何安装 Internet 资源管理器组件的信息会出现在"文章 185375:: 如何为创建单个 EXE 安装 Internet Explorer 中的"Microsoft 支持网站。  
  
 如果你的应用程序使用的 MFC 数据库类 (例如， [CRecordset 类](../mfc/reference/crecordset-class.md)和[CRecordView 类](../mfc/reference/crecordview-class.md))，你必须重新分发 ODBC 和应用程序使用任何 ODBC 驱动程序。 有关详细信息，请参阅[重新分发数据库支持文件](../ide/redistributing-database-support-files.md)。  
  
 如果你的 MFC 应用程序使用 Windows 窗体控件，必须重新 mfcmifc80.dll 分发与你的应用程序。 此 DLL 是的强名称签名.NET 程序集可以与在其应用程序本地文件夹中或通过将其部署到全局程序集缓存 (GAC) 中使用的应用程序一起重新发布[Gacutil.exe （全局程序集缓存工具）](/dotnet/framework/tools/gacutil-exe-gac-tool)。  
  
 如果你重新分发 MFC DLL，请确保重新发布的零售版本，而不是调试版。 Dll 的调试版本是不可再发行。 MFC Dll 的调试版本的名称结尾"d"，例如，Mfc140d.dll。  
  
 可以通过使用任一 VCRedist_ 重新发布 MFC*体系结构*.exe、 与 Visual Studio 中，通过将 MFC DLL 部署到你的应用程序所在的文件夹或安装的合并模块。 有关如何重新发布 MFC 的详细信息，请参阅[重新分发 Visual c + + 文件](../ide/redistributing-visual-cpp-files.md)。  
  
## <a name="installation-of-localized-mfc-components"></a>安装本地化的 MFC 组件  
 如果你决定通过安装 MFC 本地化 DLL 本地化你的应用程序，则必须使用可再发行合并文件 (.msm)。 例如，如果你想要本地化 x86 上的应用程序的计算机，必须合并 Microsoft_VC`<version>`_MFCLOC_x86.msm x86 安装包到计算机。  
  
 可再发行组件.msm 文件包含用于本地化的 Dll。 没有为每个受支持的语言的一个 DLL。 安装过程在目标计算机上的 %windir%\system32\ 文件夹中安装这些 Dll。  
  
 有关如何本地化 MFC 应用程序的详细信息，请参阅[TN057: MFC 组件的本地化](../mfc/tn057-localization-of-mfc-components.md)，以及[文章 208983： 如何使用 MFC LOC Dll](http://go.microsoft.com/fwlink/p/?linkid=198025) Microsoft 支持网站上。  
  
 你可以通过部署应用程序本地文件夹中的 MFC DLL 重新分发 MFC 本地化 Dll。 有关如何重新分发 Visual c + + 库的详细信息，请参阅[重新分发 Visual c + + 文件](../ide/redistributing-visual-cpp-files.md)。  
  
## <a name="see-also"></a>请参阅  
 [重新分发 Visual C++ 文件](../ide/redistributing-visual-cpp-files.md)