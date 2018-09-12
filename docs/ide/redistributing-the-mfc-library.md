---
title: 重新分发 MFC 库 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- MFC, redistributing
- redistributing MFC library
ms.assetid: 72714ce1-385e-4c1c-afa5-96b03e873866
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6e23358e17558c436d82a3226f84c35a59bf63a1
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/04/2018
ms.locfileid: "43694040"
---
# <a name="redistributing-the-mfc-library"></a>重新分发 MFC 库
如果将应用程序动态链接到 MFC 库，则必须重新分发匹配的 MFC DLL。 例如，如果 MFC 应用是使用 Visual Studio 2015 附带的 MFC 版本生成的，则必须重新分发 mfc140.dll 或 mfc140u.dll，具体取决于应用是针对窄字符还是 Unicode 支持编译的。  
  
> [!NOTE]
>  Visual Studio 2015 RTM 中的可再发行文件目录中省略了 mfc140.dll 文件。 可改用 Visual Studio 2015 在 Windows\system32 和 Windows\syswow64 目录中安装的版本。  
  
 由于所有 MFC DLL 都使用共享版本的 C 运行库 (CRT)，因此可能还需重新分发 CRT。 Visual Studio 2015 附带的 MFC 版本使用通用 CRT 库，该库作为 Windows 10 的一部分进行分发。 要在早期版本的 Windows 上运行使用 Visual Studio 2015 生成的 MFC 应用程序，必须重新分发通用 CRT。 有关如何将通用 CRT 重新分发为操作系统组件或如何使用本地部署进行重新分发的信息，请参阅[通用 CRT 简介](http://go.microsoft.com/fwlink/p/?linkid=617977)。 要下载通用 CRT 以便在受支持的 Windows 版本 进行集中部署，请参阅 [Windows 10 通用 C 运行时](http://go.microsoft.com/fwlink/p/?LinkId=619489)。 Windows SDK 中提供了用于本地部署的可再发行体系结构特定版本的 ucrtbase.dll。 默认情况下，Visual Studio 将这些文件安装在特定于体系结构的子目录中的 C:\Program Files (x86)\Windows Kits\10\Redist\ucrt\DLLs\ 中。  
  
 如果应用是使用早期版本的 MFC 库生成的，则必须从可再发行文件目录重新分发匹配的 CRT DLL。 例如，如果 MFC 应用程序是使用 Visual Studio 2013 (vc120) 工具集生成的，则必须重新分发 msvcr120.dll。 必须重新分发匹配的 matching mfc`<version>`u.dll 或 mfc`<version>`.dll。  
  
 如果将应用程序静态链接到 MFC（即如果在“属性页”对话框的“常规”选项卡上指定“在静态库中使用 MFC”），则无需重新分发 MFC DLL。 但是，尽管静态链接可能适用于应用程序的测试和内部部署，但不建议使用它来重新分发 MFC。 如需深入了解部署 Visual C++ 库的建议策略，请参阅[选择部署方法](../ide/choosing-a-deployment-method.md)。  
  
 如果应用程序使用实现 WebBrowser 控件的 MFC 类（例如，[CHtmlView 类](../mfc/reference/chtmlview-class.md)或 [CHtmlEditView 类](../mfc/reference/chtmleditview-class.md)），建议同时安装最新版本的 Microsoft Internet Explorer，以便目标计算机具有最新的通用控件文件。 （至少需要 Internet Explorer 4.0。）有关如何安装 Internet Explorer 组件的信息，请参阅 Microsoft 支持部门网站上的“文章 185375：如何创建 Internet Explorer 的单一 EXE 安装”。  
  
 如果应用程序使用 MFC 数据库类（例如 [CRecordset 类](../mfc/reference/crecordset-class.md)和 [CRecordView 类](../mfc/reference/crecordview-class.md)），则必须重新分发 ODBC 和应用程序使用的任何 ODBC 驱动程序。  
  
 如果 MFC 应用程序使用 Windows 窗体控件，则必须使用 应用程序重新分发 mfcmifc80.dll。 此 DLL 是一个强名称签名的 .NET 程序集，可使用应用程序本地文件夹中的应用程序重新分发它，也可通过使用 [Gacutil.exe（全局程序集缓存工具）](/dotnet/framework/tools/gacutil-exe-gac-tool)将其部署到全局程序集缓存 (GAC)。  
  
 如果重新分发 MFC DLL，请确保重新分发零售版本，而不是调试版本。 DLL 的调试版本不可再发行。 MFC DLL 的调试版本的名称以“d”结尾，例如 Mfc140d.dll。  
  
 可通过以下方法来重新分发 MFC：使用随 Visual Studio 一起安装的合并模块 VCRedist_architecture.exe，或者将 MFC DLL 部署到与应用程序相同的文件夹中。 有关如何重新分发 MFC 的详细信息，请参阅[重新分发 Visual C++ 文件](../ide/redistributing-visual-cpp-files.md)。  
  
## <a name="installation-of-localized-mfc-components"></a>安装本地化的 MFC 组件  
 如果决定通过安装 MFC 本地化 DLL 来本地化应用程序，则必须使用可再发行的合并文件 (.msm)。 例如，如果要在 x86 计算机上本地化应用程序，则必须将 Microsoft_VC`<version>`_MFCLOC_x86.msm 合并到 x86 计算机的安装包中。  
  
 可再发行的 .msm 文件包含用于本地化的 DLL。 每种支持的语言都有一个 DLL。 安装进程会将这些 DLL 安装在目标计算机上的 %windir%\system32\ 文件夹中。  
  
 有关如何本地化 MFC 应用程序的详细信息，请参阅 [TN057：MFC 组件的本地化](../mfc/tn057-localization-of-mfc-components.md)。
  
 通过在应用程序本地文件夹中部署 MFC DLL，可重新分发 MFC 本地化 DLL。 有关如何重新分发 Visual C++ 库的详细信息，请参阅[重新分发 Visual C++ 文件](../ide/redistributing-visual-cpp-files.md)。  
  
## <a name="see-also"></a>请参阅  
 [重新分发 Visual C++ 文件](../ide/redistributing-visual-cpp-files.md)
