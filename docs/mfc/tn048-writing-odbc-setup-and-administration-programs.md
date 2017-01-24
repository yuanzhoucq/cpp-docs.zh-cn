---
title: "TN048：为 MFC 数据库应用程序编写 ODBC 安装和管理程序 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.mfc.odbc"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "安装 ODBC"
  - "MFC, 数据库应用程序"
  - "ODBC, 和 MFC"
  - "ODBC, 安装"
  - "安装, ODBC 安装程序"
  - "TN048"
ms.assetid: d456cdd4-0513-4a51-80c0-9132b66115ce
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# TN048：为 MFC 数据库应用程序编写 ODBC 安装和管理程序
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

> [!NOTE]
>  以下技术说明在首次包括在联机文档中后未更新。  因此，某些过程和主题可能已过时或不正确。  要获得最新信息，建议你在联机文档索引中搜索热点话题。  
  
 使用 MFC 数据库类的应用程序将需要安装 ODBC 组件的安装程序。  它们可能还需要将检索有关使用驱动程序的信息，指定默认驱动程序和配置数据源的 ODBC 管理程序。  此注释说明使用 ODBC 安装程序 API 编写这些程序。  
  
##  <a name="_mfcnotes_writing_an_odbc_setup_program"></a> 编写 ODBC 安装程序  
 MFC 数据库应用程序需要 ODBC 驱动程序管理器 \(ODBC.DLL\) 和 ODBC 驱动程序可以让数据源。  许多 ODBC 驱动程序还需要其他网络和通信 DLL。  大多数 ODBC 驱动程序附带的 ODBC 将安装所需组件的安装程序。  使用 MFC 数据库类的应用程序开发人员可以：  
  
-   取决于安装的 ODBC 驱动特定组件程序安装程序。  这不需要对部分的开发人员进一步工作可以重新发布用于驱动程序的安装程序。  
  
-   或者，您可以编写自己安装程序，用于安装驱动程序管理器和驱动程序。  
  
 ODBC 安装程序 API 可用于编写应用程序特定的安装程序。  在安装程序中安装 DLL。ODBC API 函数。程序在 16 位 Windows 上的 ODBCINST.DLL 和 Win32 上的 ODB CCP32 .DLL 实现。  应用程序可以在调用安装程序 DLL 的 **SQLInstallODBC**，会安装 ODBC 驱动程序管理器、ODBC 驱动程序和任何必需的转换器。  然后记录安装的驱动程序和 ODBCINST.INI 转换器 \(文件或注册表中，在 NT\)。  **SQLInstallODBC** 要求的完整路径 ODBC.INF 文件，包含的安装驱动程序的列表并描述文件包含每驱动程序。  它还包含有关驱动程序管理器和该转换器的类似的信息。  驱动程序开发人员通常提供 ODBC.INF 文件。  
  
 安装程序还可以针对各个 ODBC 组件。  安装驱动程序管理器，在安装程序 DLL 的程序第一次调用 **SQLInstallDriverManager** 来获取驱动程序管理器的目标目录。  这通常属于 Windows DLL 所在的目录。  程序在 ODBC.INF 文件的 \[ODBC 驱动程序管理器\] 节然后使用信息复制驱动程序管理器和相关文件从磁盘安装到此目录。  安装单独驱动程序，在安装程序 DLL 的程序第一次调用 **SQLInstallDriver** 将驱动程序指定为 ODBCINST.INI 文件 \(或注册表中，在 NT\)。  **SQLInstallDriver** 返回驱动程序的目标目录 \- Windows DLL 通常驻留的目录。  程序在 ODBC.INF 文件的驱动程序中节然后使用信息复制驱动程序 DLL 和相关文件从磁盘安装到此目录。  
  
 有关 ODBC.INF 的更多信息，ODBCINST.INI 安装和使用程序 API，请参见 ODBC SDK *程序员参考，* 第 19 章，安装 ODBC 软件。  
  
##  <a name="_mfcnotes_writing_an_odbc_administrator"></a> 编写的 ODBC 管理器  
 MFC 数据库应用程序中两种方法之一来设置和配置 ODBC 数据源，方法如下：  
  
-   使用 ODBC 管理器 \(可为程序或控制面板项\)。  
  
-   创建自己的应用程序配置数据源。  
  
 配置数据源的程序进行函数调用安装程序 DLL。  安装程序 DLL 称为"安装 DLL 配置数据源。  将每个推动的安装 DLL;可驱动程序 DLL 或者单独的 DLL。  设置 DLL 提示用户。驱动程序所需连接到数据源以及默认转换器，因此，如果支持的信息。  然后调用安装程序 DLL 和 Windows API 记录在 ODBC.INI 文件 \(或注册表\) 的此信息。  
  
 显示的对话框，用户可以添加、修改和删除数据源，在安装程序 DLL 的程序调用 **SQLManageDataSources**。  当安装程序 DLL 从控制面板时，调用此函数调用。  若要添加修改，或删除数据源时，**SQLManageDataSources** 调用中安装 DLL 的 **ConfigDSN** 驱动程序的与该数据源。  直接添加或删除数据源，修改安装程序，程序中调用 DLL 的 **SQLConfigDataSource**。  程序将操作指定数据源和选项的名称。  **SQLConfigDataSource** 调用中安装 DLL 并将它从 **SQLConfigDataSource**中的 **ConfigDSN** 参数。  
  
 有关更多信息，请参见 ODBC SDK *Programmer's Reference、* 或 23，则安装 DLL 函数引用和章节 24，则安装程序 DLL 函数引用。  
  
## 请参阅  
 [按编号列出的技术说明](../mfc/technical-notes-by-number.md)   
 [按类别列出的技术说明](../mfc/technical-notes-by-category.md)