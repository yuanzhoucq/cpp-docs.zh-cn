---
title: 数据源 (ODBC)
ms.date: 11/04/2016
helpviewer_keywords:
- ODBC data sources, configuring
- CDatabase class, data source connections
- ODBC data sources
- configuring ODBC data sources
- ODBC data sources, represented by CDatabase
ms.assetid: b246721f-b9e1-49bd-a6c7-f348b8c3d537
ms.openlocfilehash: df61ca28a1a5c7fb1f2096f2cc22654794f5dbdc
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50469788"
---
# <a name="data-source-odbc"></a>数据源 (ODBC)

本主题适用于 MFC ODBC 类。

在数据库术语中，数据源是一组特定的数据，访问该数据和数据源，可以使用数据源名称所述的位置所需的信息。 若要使用类[CDatabase](../../mfc/reference/cdatabase-class.md)，数据源必须是一个已通过开放式数据库连接 (ODBC) 管理器配置。 数据源的示例包括 Microsoft SQL Server 上运行跨网络或 Microsoft Access 文件的本地目录中的远程数据库。 从应用程序中，可以访问对其具有 ODBC 驱动程序的任何数据源。

你可以一次应用程序中处于活动状态的一个或多个数据源，每个表示`CDatabase`对象。 你还可拥有多个并发连接对任何数据源。 你可以连接到远程，以及连接到本地数据源，具体取决于已安装的驱动程序和 ODBC 驱动程序的功能。 有关数据源和 ODBC 管理器的详细信息，请参阅[ODBC](../../data/odbc/odbc-basics.md)并[ODBC 管理器](../../data/odbc/odbc-administrator.md)。

以下主题介绍更多有关数据源：

- [数据源：管理连接 (ODBC)](../../data/odbc/data-source-managing-connections-odbc.md)

- [数据源：确定数据源的架构 (ODBC)](../../data/odbc/data-source-determining-the-schema-of-the-data-source-odbc.md)

## <a name="see-also"></a>请参阅

[开放式数据库连接 (ODBC)](../../data/odbc/open-database-connectivity-odbc.md)