---
title: "重新分发控件 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ActiveX 控件 [C++], 重新发布"
  - "可重新发布的控件"
ms.assetid: 32d03b95-d328-4f10-ad9b-f3ebbe03339d
caps.latest.revision: 14
caps.handback.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 重新分发控件
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Visual C\+\+.NET 提供可以在应用程序中使用的 ActiveX 控件。 然后可以与应用程序一起重新发布控件。 在“插入 ActiveX 控件”对话框中，突出显示控件将显示其 .ocx 或 .dll 文件。  
  
 有关 Visual C\+\+ 提供的可再发行 ActiveX 控件的列表，请参阅 Visual C\+\+.NET 产品 CD\-ROM 第 2 张光盘上的 Program Files\\Microsoft Visual Studio.NET 2003\\redist.txt；Win\\System 文件夹中的任何 .ocx 文件都可以再发行。  
  
 [MFC ActiveX 控件：发行 ActiveX 控件](../../mfc/mfc-activex-controls-distributing-activex-controls.md)说明如何安装和注册可再发行的 ActiveX 控件。  
  
 [合并模块项目](http://msdn.microsoft.com/zh-cn/e92e4f85-fba5-45ee-a432-892a956daeb9)说明 Visual Studio .NET 部署如何通过合并模块处理文件的再发行。  
  
 [重新发布数据库支持文件](../../ide/redistributing-database-support-files.md)讨论如何为 Microsoft 数据访问 SDK 中的数据库技术重新发布支持文件。  
  
 如果应用程序使用连接到数据库的 ActiveX 控件，则需要安装或执行以下各项：  
  
-   **用于 Windows 的 DCOM。**在运行 Windows 2000 之前的 Windows 版本的任何计算机上，需要运行 Dcom98.exe 或 Dcom95.exe。 （Dcom98.exe 专用于 Windows 98；而 Dcom95.exe 专用于 Windows 95。）  
  
-   **MDAC 2.8 SDK。**应在目标计算机上安装 Microsoft 数据访问 2.8 SDK。 可从 [http:\/\/go.microsoft.com\/fwlink\/?LinkId\=205525](http://go.microsoft.com/fwlink/?LinkId=205525) 下载此文件。  
  
-   **MDAC 2.8 重新发布程序。**MDAC 2.8 SDK 专用于与 MDAC 2.8 重新发布程序 \(MDAC\_TYP.EXE\) 一起使用。 可从 [http:\/\/go.microsoft.com\/fwlink\/?LinkId\=164412](http://go.microsoft.com/fwlink/?LinkId=164412) 下载 MDAC\_TYP.EXE。  
  
-   **复制 DSN。**还需要在目标计算机上复制数据源名称。 可以用函数（如 [ConfigDSN](https://msdn.microsoft.com/en-us/library/ms709275.aspx)）以编程方式来完成此操作。  
  
## 有关组件重新发布的重要说明  
  
-   **重新发布 DAO 组件。** Microsoft 建议使用 Jet 4.0 SP3（版本 2927.04）或更高版本。 Jet 4.0 SP3 随 Windows 2000 和 Windows Me 一起提供。 使用此版本的 Jet 可以减少必须随应用程序一起测试的 Jet 版本数。  
  
     Windows XP 附带有以前的 Windows 版本中未包括的 Jet 升级 Service Pack 版本。 在 Windows XP 上测试你的应用程序将自动测试 Windows XP 附带的 Jet 版本。 在发布 DAO 应用程序前，需要在 Jet 4.0 的两个版本上测试它们。  
  
     Windows XP 版本中的唯一差别是用于修复自 Windows 2000 发布后发现的问题的修复程序。 如果你的应用程序用户没有遇到问题，就不需要升级到 Jet 4.0 SP3 以上的版本。  
  
-   **ActiveX 控件的已知问题。** 在未安装 Visual C\+\+ 的计算机上动态创建可再发行 ActiveX 控件的实例时，存在一个已知的问题，如知识库文章“PRB：动态创建可再发行控件失败”\(Q151804\) 中所述。 可在 MSDN Library CD\-ROM 中或 [http:\/\/support.microsoft.com](http://support.microsoft.com) 上找到知识库文章。 在将某些 ActiveX 控件放在对话框上时，也存在一个已知问题；你将收到一个指出控件要求设计时许可证的消息框，如知识库文章“PRB：需要 Microsoft ActiveX 控件的设计时许可证”\(Q155059\) 中所述。 可在 MSDN Library CD\-ROM 中或 [http:\/\/support.microsoft.com](http://support.microsoft.com) 上找到知识库文章。  
  
-   **Visual Studio 许可控件。** 获得 Visual Studio 许可接受方可以重新发布特定于其他 Visual Studio 开发工具的附加 ActiveX 控件。 例如，Chart 控件与 Visual Basic 一起发布，而 Visual Basic 同样随 Visual Studio 一起提供。 因此，如果将 Visual C\+\+ 用作 Visual Studio 许可证的一部分，则可以重新发布 Chart 控件。 但是，如果只购买了 Visual C\+\+，将不具有重新发布 Chart 控件的许可证。  
  
## 请参阅  
 [使用 ActiveX 控件](../../data/ado-rdo/using-activex-controls.md)   
 [MFC ActiveX 控件：发行 ActiveX 控件](../../mfc/mfc-activex-controls-distributing-activex-controls.md)