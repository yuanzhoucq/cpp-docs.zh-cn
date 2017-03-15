---
title: "注册 | Microsoft Docs"
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
  - "初始化服务器"
  - "安装服务器"
  - "OLE 服务器应用程序, 注册服务器"
  - "OLE, 注册"
  - "注册数据库"
  - "注册表, OLE 项数据库"
  - "服务器, 初始化"
  - "服务器, 安装"
ms.assetid: 991d5684-72c1-4f9e-a09a-9184ed12bbb9
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# 注册
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

当用户要插入一个 OLE 项到应用程序时，OLE 存在对象类型列表选择。  OLE 从系统注册数据库获取列表，一个包含所有服务器应用提供的信息。  当服务器注册它放在系统注册数据库中，输入 \(注册表\) 描述对象，它提供对文件扩展名与每个路径类型自身的，以及其他信息中。  
  
 框架和 OLE 系统动态链接库 \(DLL\) \(DLL\) 使用此注册表确定类型的 OLE 项可用系统上。  当链接还是嵌入对象激活时，OLE 系统 DLL 也使用此注册表确定如何启动服务器应用程序。  
  
 本文描述每个服务器应用需要执行，在安装时，将在每次执行。  
  
 有关系统注册数据库和在 .reg 文件格式的详细信息来更新它，请参见 *OLE 程序引用*。  
  
##  <a name="_core_server_installation"></a> SQL Server 2008 安装  
 在首次安装服务器应用程序时，您应对其注册该支持 OLE 项的所有类型。  在执行作为独立应用程序时，还可以使服务器更新系统注册数据库。  如果服务器可执行文件移动，这保证注册数据库最新。  
  
> [!NOTE]
>  当测试运行作为独立应用程序时，应用程序向导生成的 MFC 应用程序自动注册。  
  
 如果在安装时注册应用程序，请使用 RegEdit.exe 程序。\(在 Windows 95、Windows 98 和 Windows ME，RegEdit 在 Windows 目录。  在 Windows NT 和 Windows 2000 上，RegEdit 窗口在 System32 目录中。\)如果包括在应用程序的安装程序，安装程序的 RegEdit“\/S *appname.reg*”。\(\/S 标志指示无操作，也就是说，它不报告显示命令的成功完成的对话框。\)否则，将提示用户手动运行 RegEdit。  
  
> [!NOTE]
>  应用程序向导创建的 .reg 文件中不包含可执行文件的完整路径。  安装程序必须修改 .reg 要包括的文件的完整路径为可执行或修改 PATH 环境变量以包括安装目录。  
  
 RegEdit 将 .reg 文本文件的内容读入注册数据库。  若要验证数据库或修复它，请使用注册表编辑器。  重要注意避免删除 OLE 项。\(在 Windows 95、Windows 98 和 Windows ME，注册表编辑器是 RegEdit.exe。  在 Windows NT 和 Windows 2000，它是 RegEdit32.exe。\)  
  
##  <a name="_core_server_initialization"></a> 服务器初始化  
 在创建与应用程序向导时的服务器应用向导，自动完成您的所有初始化任务。  本节描述您必须执行，如果手动编写服务器应用程序。  
  
 当服务器应用由容器应用程序时启动，OLE 系统 DLL 添加到服务器“\/Embedding”选项的命令行。  服务器应用程序中的行为不同于它是否按容器启动，因此，第一件事应用程序应执行，在开始执行是“\/Embedding”检查或“\-”时嵌入命令行中的选项。  如果此开关存在，请加载显示服务器为就地激活或完全打开不同的资源组。  有关更多信息，请参见 [菜单和资源：服务器添加](../mfc/menus-and-resources-server-additions.md)。  
  
 服务器应用程序还应调用其 `CWinApp::RunEmbedded` 函数分析命令行。  如果返回非零值，应用程序就不应显示其窗口，因为它从容器应用程序运行之后，不用作独立的应用程序。  该函数更新在系统注册数据库的服务器输入并调用 `RegisterAll` 成员函数，会执行实例注册。  
  
 当服务器应用程序启动时，您必须确保该管道执行实例注册。  实例注册通知 OLE 系统 DLL 服务器活动和准备接收从容器的请求。  它不添加 Enter 注册到数据库。  通过调用 `ConnectTemplate` 成员函数执行服务器的实例注册由 `COleTemplateServer`定义的。  这连接到 `COleTemplateServer` 对象的 `CDocTemplate` 对象。  
  
 `ConnectTemplate` 函数采用三个参数：服务器的 **CLSID**、一个指向 `CDocTemplate` 对象的指针以及指示服务器是否为标志都支持多个实例。  miniserver 绑定可以支持多个实例，也就是说，服务器的多个实例同时运行，每个容器中必须是可能的。  因此，此标志中传递 **TRUE**，在启动 miniserver 时。  
  
 如果您编写 miniserver，它将由容器始终基于定义启动。  您仍应分析命令行检查“\/Embedding”选项。  缺少命令行上的该选项意味着用户尝试启动 miniserver 用作独立的应用程序。  如果发生这种情况，请注册向系统注册数据库的服务器然后显示通知用户的消息是从启动容器应用程序的 miniserver。  
  
## 请参阅  
 [OLE](../mfc/ole-in-mfc.md)   
 [服务器](../mfc/servers.md)   
 [CWinApp::RunAutomated](../Topic/CWinApp::RunAutomated.md)   
 [CWinApp::RunEmbedded](../Topic/CWinApp::RunEmbedded.md)   
 [COleTemplateServer Class](../mfc/reference/coletemplateserver-class.md)