---
title: "重新分发 MFC 库 | Microsoft Docs"
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
  - "MFC, 重新分发"
  - "重新分发 MFC 库"
ms.assetid: 72714ce1-385e-4c1c-afa5-96b03e873866
caps.latest.revision: 32
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 29
---
# 重新分发 MFC 库
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

如果您将应用程序动态链接到 MFC 库，则必须重新发布 Msvcr100.dll，因为所有 MFC DLL 都使用 C 运行库 \(CRT\) 的共享版本。  您还必须重新发布 Mfc100u.dll 或 Mfc100.dll。  
  
 如果将应用程序静态链接到 MFC（即，如果在**“属性页”**对话框中的**“常规”**选项卡上指定**“在静态库中使用 MFC”**），则不必重新发布 Mfc100u.dll 或 Mfc100.dll。  但是，虽然静态链接可能对应用程序的测试以及内部部署都有效，但是不建议使用静态链接来重新发布 MFC。  有关用于部署 Visual C\+\+ 库的建议策略的更多信息，请参见[选择部署方法](../ide/choosing-a-deployment-method.md)。  
  
 如果应用程序使用实现 WebBrowser 控件的 MFC 类（例如，[CHtmlView 类](../mfc/reference/chtmlview-class.md) 或 [CHtmlEditView Class](../mfc/reference/chtmleditview-class.md)），则建议还安装最新版本的 Microsoft Internet Explorer，以便目标计算机具有最新的公共控制文件。（至少需要 Internet Explorer 4.0。）有关如何安装 Internet Explorer 组件的信息可以在 Microsoft 支持网站上的“Article 185375: How To Create a Single EXE Install of Internet Explorer”（文章 185375：如何：创建 Internet Explorer 的单个 EXE 安装）中找到。  
  
 如果应用程序使用 MFC 数据库类（例如 [CRecordset Class](../mfc/reference/crecordset-class.md) 和 [CRecordView Class](../mfc/reference/crecordview-class.md)），则必须重新发布应用程序所使用的 ODBC 和任何 ODBC 驱动程序。  有关详细信息，请参阅[重新分发数据库支持文件](../ide/redistributing-database-support-files.md)。  
  
 如果 MFC 应用程序使用 Windows 窗体控件，则必须随应用程序一起重新发布 mfcmifc80.dll。  此 DLL 是一个强名称签名的 .NET 程序集，可以通过其应用程序本地文件夹中的应用程序或通过使用[Gacutil.exe（全局程序集缓存工具）](../Topic/Gacutil.exe%20\(Global%20Assembly%20Cache%20Tool\).md) 部署到全局程序集缓存 \(GAC\) 进行重新发布。  
  
 如果重新发布 MFC DLL，请确保重新发布零售版本，而不是调试版本。  DLL 的调试版本是不可重新发布的。  MFC DLL 的调试版本的名称以“d”结尾，例如 Mfc100d.dll。  
  
 如果修改 MFC 源代码，然后重新生成 MFC DLL，则必须重命名修改的 MFC DLL，以便其不会与 Visual Studio 中包含的 MFC DLL 冲突。  建议不要重新生成或重命名 MFC DLL。  有关更多信息，请参见 MFC 技术说明 33。  
  
 您可以通过以下方法来重新发布 MFC：使用与 Visual Studio 一起安装的合并模块 VCRedist\_*architecture*.exe，或者将 MFC DLL 部署到应用程序所在文件夹中。  有关如何重新发布 MFC 的更多信息，请参见[重新分发 Visual C\+\+ 文件](../ide/redistributing-visual-cpp-files.md)。  
  
## 安装本地化的 MFC 组件  
 如果您决定通过安装 MFC 本地化 DLL 来本地化应用程序，则必须使用可再发行合并文件 \(.msm\)。  例如，如果希望本地化 x86 计算机上的应用程序，则必须将 Microsoft\_VC100\_MFCLOC\_x86.msm 合并到 x86 计算机的安装软件包中。  
  
 可再发行 .msm 文件包含用于本地化的 DLL。  每种支持的语言都有一个 DLL。  安装过程会将这些 DLL 安装到目标计算机上的 %windir%\\system32\\ 文件夹中。  
  
 获取有关如何本地化 MFC 应用程序的更多信息，请参见 [TN057：MFC 组件的本地化](../mfc/tn057-localization-of-mfc-components.md)，也可参见微软提供支持的网站上的 [Article 208983: How to Using MFC LOC DLLs](http://go.microsoft.com/fwlink/?LinkId=198025)。  
  
 可以通过在应用程序本地文件夹中部署 MFC DLL 来重新发布 MFC 本地化 DLL。  有关如何重新发布 Visual C\+\+ 库的更多信息，请参见[重新分发 Visual C\+\+ 文件](../ide/redistributing-visual-cpp-files.md)。  
  
## 请参阅  
 [重新分发 Visual C\+\+ 文件](../ide/redistributing-visual-cpp-files.md)