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
ms.openlocfilehash: ed9eeb8f5ef0d53846761062cf2c6575d2eaf9e6
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80213290"
---
# <a name="data-source-odbc"></a>数据源 (ODBC)

本主题适用于 MFC ODBC 类。

在数据库术语中，数据源是一组特定的数据、访问该数据所需的信息和数据源的位置，可以使用数据源名称进行描述。 若要使用类[CDatabase](../../mfc/reference/cdatabase-class.md)，数据源必须是通过开放式数据库连接（ODBC）管理员配置的数据源。 数据源的示例包括 Microsoft SQL Server 跨网络运行的远程数据库或本地目录中的 Microsoft Access 文件。 在应用程序中，可以访问具有 ODBC 驱动程序的任何数据源。

你可以在应用程序中一次激活一个或多个数据源，每个数据源都由一个 `CDatabase` 对象表示。 还可以同时连接到任何数据源。 可以连接到远程和本地数据源，具体取决于已安装的驱动程序和 ODBC 驱动程序的功能。 有关数据源和 ODBC 管理器的详细信息，请参阅[odbc](../../data/odbc/odbc-basics.md)和[odbc 管理员](../../data/odbc/odbc-administrator.md)。

以下主题详细介绍了数据源：

- [数据源：管理连接 (ODBC)](../../data/odbc/data-source-managing-connections-odbc.md)

- [数据源：确定数据源的架构 (ODBC)](../../data/odbc/data-source-determining-the-schema-of-the-data-source-odbc.md)

## <a name="see-also"></a>另请参阅

[开放式数据库连接 (ODBC)](../../data/odbc/open-database-connectivity-odbc.md)
