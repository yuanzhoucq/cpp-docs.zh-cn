---
title: "ODBC 连接 | Microsoft Docs"
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
  - "ODBC 连接, 配置"
  - "ODBC, 连接"
ms.assetid: c9df2fa6-d9e2-4335-b885-724662968691
caps.latest.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# ODBC 连接
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

ODBC 连接在系统控制面板中配置。  可以对任何已安装 ODBC 驱动程序的数据源建立 ODBC 连接。  Visual C\+\+ 6.0 或更高版本附带了用于文本文件、Access、FoxPro、Paradox、dBASE、Excel、SQL Server 和 Oracle 的驱动程序。  创建 ODBC 连接时，它自动接收数据源名称 \(DSN\)。  DSN 随后用于在数据控件（如 ADO 数据控件和 RDO RemoteData 控件）中标识连接。  
  
 **OLE DB 连接** 配置 OLE DB 连接不需要额外的工作。  例如，如果创建了 ODBC 数据源，用于 ODBC 的 OLE DB 提供程序会自动检测到它。  
  
### 配置 ODBC 数据源  
  
1.  单击**“开始”**，单击**“设置”**，然后单击**“控制面板”**。  
  
2.  在控制面板中，选择“32 位 ODBC”（Windows 95 或 98）或“ODBC”（Windows NT 或 2000）。  
  
3.  选择“用户 DSN”或“系统 DSN”选项卡。  “用户 DSN”使您得以创建用户特定的数据源名称，“系统 DSN”使您得以创建可用于所有用户的数据源。  
  
4.  单击“添加”显示本地安装的 ODBC 驱动程序的列表。  
  
5.  选择与要连接的索引顺序访问方法 \(ISAM\) 或数据库的类型相对应的驱动程序，然后单击“完成”。  
  
6.  遵循特定于该驱动程序的说明。  关闭后，DSN 现在就可供使用了。  
  
 当生成某些 ODBC 驱动程序类型的 DSN 时，需要知道实际文件的位置。  例如，在创建 Access DSN 时，需要知道 .mdb 文件的位置。  同时，应具有有效的用户名和密码。  例如，大多数 Access 系统的系统用户名都是 *admin*。  
  
 在创建 [Oracle](../../data/ado-rdo/oracle-connections.md) DSN 时，应知道 SQL\*Net 连接字符串。  
  
## 请参阅  
 [创建数据库连接](../../data/ado-rdo/creating-database-connections.md)