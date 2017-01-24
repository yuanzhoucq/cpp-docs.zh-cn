---
title: "安装数据库支持 (MFC/ATL) | Microsoft Docs"
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
  - "ATL [C++], 数据库支持"
  - "数据访问 [C++], 安装数据库支持"
  - "数据库 [C++], 安装数据库支持"
  - "安装数据库支持"
ms.assetid: 3820ba96-4fb8-4405-83dd-bb3bc5998667
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 安装数据库支持 (MFC/ATL)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

当运行 Visual C\+\+ .NET 的安装程序时，将自动安装以下数据库组件：  
  
-   所有必要的 ATL OLE DB 组件。  有关详细信息，请参阅[安装 ATL 数据库支持](../data/installing-atl-database-support.md)。  
  
-   一组带 ODBC 驱动程序管理器和 ODBC 管理员程序的 ODBC 驱动程序。  有关详细信息，请参阅[安装 MFC 数据库支持](../data/installing-mfc-database-support.md)中的“已安装的 ODBC 驱动程序”和“已安装的 ODBC SDK 组件”。  
  
-   DAO 软件开发工具包 \(SDK\) 的所需组件。  包括未与本文集成的“帮助”文件。  但是，如果要使用 DAO，则需要安装与操作系统兼容的 Jet 版本。  有关详细信息，请参阅[安装 MFC 数据库支持](../data/installing-mfc-database-support.md)中的“已安装的 DAO SDK 组件”。  
  
 作为标准安装的一部分，安装程序还会安装 Microsoft 数据访问组件 \(MDAC\)，这是在 Visual C\+\+ .NET 中支持数据访问编程的必备组件。  
  
 Visual C\+\+ .NET 将安装 MDAC 2.7 SDK。  有关 MDAC SDK 的更新和消息，请查看 Microsoft 通用数据访问网站，网址为 [http:\/\/go.microsoft.com\/fwlink\/?LinkId\=121548](http://go.microsoft.com/fwlink/?LinkId=121548)。  
  
 如果你要重新分发数据访问应用程序，你还应安装 MDAC 2.7 重新分发程序。  MDAC 2.7 SDK 仅用于 Visual Studio .NET 系统必备 CD\-ROM 的 MDAC 目录下包含的 MDAC 2.7 重新分发程序。  你还可以从之前列出的 MDAC 2.7 SDK 下载链接下载 Mdac\_typ.exe。  有关重新分发组件的详细信息，请参阅[重新分发控件](../data/ado-rdo/redistributing-controls.md)。  
  
## 请参阅  
 [数据访问](../Topic/Data%20Access%20in%20Visual%20C++.md)