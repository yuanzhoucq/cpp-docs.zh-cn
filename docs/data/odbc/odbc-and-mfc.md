---
title: ODBC 和 MFC
ms.date: 11/04/2016
helpviewer_keywords:
- ODBC [C++], MFC
- connections [C++], databases
- connections [C++], data source
- databases [C++], connecting to
- data sources [C++], connecting to
- MFC [C++], ODBC and
- database connections [C++], MFC ODBC classes
ms.assetid: 98f02fd7-1235-437b-89a9-edfd0fc797f7
ms.openlocfilehash: 94a3455324a52b789bcfcf192b698a3c42b37c00
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80213151"
---
# <a name="odbc-and-mfc"></a>ODBC 和 MFC

> [!NOTE]
>  若要使用 MFC 数据库类，必须具有相应的数据源 ODBC 驱动程序。 用于 SQL Server 的 microsoft ODBC 驱动程序最新是[MICROSOFT Odbc driver 13 for SQL Server](https://www.microsoft.com/download/details.aspx?id=50420)。 大多数数据库供应商提供适用于 Windows 的 ODBC 驱动程序。

本主题介绍了 Microsoft 基础类（MFC）库的基于 ODBC 的数据库类的主要概念，并概述了这些类如何协同工作。 有关 ODBC 和 MFC 的详细信息，请参阅以下主题：

- [连接到数据源](connecting-to-a-data-source.md)

- [选择和操作记录](selecting-and-manipulating-records.md)

- [在窗体中显示和操作数据](displaying-and-manipulating-data-in-a-form.md)

- [使用文档和视图](working-with-documents-and-views.md)

- [访问 ODBC 和 SQL](access-to-odbc-and-sql.md)

- [有关 MFC ODBC 类的其他阅读材料](further-reading-about-the-mfc-odbc-classes.md)

基于 ODBC 的 MFC 数据库类旨在提供对可使用 ODBC 驱动程序的任何数据库的访问。 由于类使用 ODBC，因此你的应用程序可以访问多种不同数据格式和不同本地/远程配置的数据。 无需编写特殊的代码来处理不同的数据库管理系统（Dbms）。 只要用户为要访问的数据提供适当的 ODBC 驱动程序，他们就可以使用您的程序操作存储在那里的表中的数据。

## <a name="see-also"></a>另请参阅

[开放式数据库连接 (ODBC)](open-database-connectivity-odbc.md)
