---
title: "安装 MFC 数据库支持 | Microsoft Docs"
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
  - "DAO [C++], 安装组件"
  - "数据库 [C++], 安装数据库支持"
  - "数据库 [C++], MFC"
  - "安装 DAO"
  - "安装 ODBC"
  - "ODBC 组件 [C++], 安装"
  - "ODBC 驱动程序 [C++], 安装"
ms.assetid: a6c2fc84-9e0e-4f39-a464-0bcbc415b946
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 安装 MFC 数据库支持
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

##  <a name="_core_odbc_drivers_installed"></a> 已安装的 ODBC 驱动程序  
 安装程序安装以下 ODBC 驱动程序：  
  
-   Microsoft Access 驱动程序  
  
-   Microsoft dBASE 驱动程序  
  
-   Microsoft Excel 驱动程序  
  
-   Microsoft FoxPro VFP 驱动程序  
  
-   Microsoft Visual FoxPro 驱动程序  
  
-   用于 Oracle 的 Microsoft ODBC 驱动程序  
  
-   Microsoft Paradox 驱动程序  
  
-   Microsoft Text 驱动程序  
  
-   Microsoft SQL Server 驱动程序  
  
 有关此版本的 Visual C\+\+ 中包含的 ODBC 驱动程序列表以及如何获取其他驱动程序的信息，请参见 [ODBC 驱动程序列表](../data/odbc/odbc-driver-list.md)。  
  
##  <a name="_core_odbc_sdk_components_installed"></a> 已安装的 ODBC SDK 组件  
 Visual C\+\+ 包含有许多关键 ODBC 组件，包括必需的头文件、库、DLL 以及工具。  这些组件包含用来配置 ODBC 数据源的 ODBC 管理器控制面板以及 ODBC 驱动程序管理器。  此外还包含有适用于[已安装的 ODBC 驱动程序](#_core_odbc_drivers_installed)所列出的多种流行 DBMS 的 ODBC 驱动程序。  
  
 ODBC SDK 为编写和测试 ODBC 驱动程序提供附加信息和工具。  请注意，从 Visual C\+\+ .NET 起，ODBC SDK 不再包括在 Visual C\+\+ .NET 安装介质上，而作为“Visual Studio .NET 系统必备”安装的 [!INCLUDE[winsdkshort](../atl/reference/includes/winsdkshort_md.md)] 的一部分提供。  
  
##  <a name="_core_dao_sdk_components_installed"></a> 已安装的 DAO SDK 组件  
  
> [!NOTE]
>  Microsoft 建议对新项目使用 OLE DB 或 ODBC。  DAO 只应在维护现有应用程序时使用。  
  
 默认情况下安装以下 DAO SDK 组件：  
  
-   Microsoft Jet \(4.0 SP3\)  
  
-   Microsoft Jet \(3.x MDB\)  
  
-   Microsoft Jet（1.x，2.x）  
  
-   [使用 DAO 和 ODBC 可以访问哪些数据库？](../data/what-data-sources-can-i-access-with-dao-and-odbc-q.md)中列出的所有数据库格式  
  
 在 Visual C\+\+ .NET 中，DAO SDK 随“Visual Studio .NET 系统必备”安装。  运行 \\Jet\\Jetsetup.exe。  
  
> [!NOTE]
>  Microsoft 建议使用 Jet 4.0 Service Pack 3（2927.04 版）或更高版本。  Jet 4.0 Service Pack 3 随 Windows 2000 和 Windows ME 一同提供。  使用该版本的 Jet 可以减少必须随应用程序一起测试的 Jet 版本数。  Windows XP 可能随同提供另一版本的 Jet。  请参见[重新发布控件](../data/ado-rdo/redistributing-controls.md)中的“重新分布 DAO 组件说明”。  
  
 如需安装其他 DAO SDK 组件，例如 DAO SDK C\+\+ 类、示例文件或者 DAO 帮助文件的 Windows 帮助版本，请从 Visual C\+\+ 6.0 CD\-ROM 中安装 DAO SDK。  
  
 有关 OLE DB 的更新以及新增功能，请参见 Microsoft 通用数据访问\) 网站 [http:\/\/go.microsoft.com\/fwlink\/?LinkId\=121548](http://go.microsoft.com/fwlink/?LinkId=121548)。  
  
## 请参阅  
 [数据访问编程 \(MFC\/ATL\)](../data/data-access-programming-mfc-atl.md)