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
ms.openlocfilehash: 38a625c73a17ecae4d8adc61e8c56bc4bdda67f6
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81320071"
---
# <a name="odbc-and-mfc"></a>ODBC 和 MFC

> [!NOTE]
> 要使用 MFC 数据库类，必须为数据源具有适当的 ODBC 驱动程序。 SQL 服务器的最后一个微软 ODBC 驱动程序是[SQL Server 的 Microsoft ODBC 驱动程序 13。](https://www.microsoft.com/download/details.aspx?id=50420) 大多数数据库供应商为 Windows 提供 ODBC 驱动程序。

本主题介绍 Microsoft 基础类 （MFC） 库基于 ODBC 的数据库类的主要概念，并概述了这些类如何协同工作。 有关 ODBC 和 MFC 的详细信息，请参阅以下主题：

- [连接数据源](connecting-to-a-data-source.md)

- [选择和操作记录](selecting-and-manipulating-records.md)

- [在窗体中显示和操作数据](displaying-and-manipulating-data-in-a-form.md)

- [使用文档和视图](working-with-documents-and-views.md)

- [访问 ODBC 和 SQL](access-to-odbc-and-sql.md)

- [有关 MFC ODBC 类的其他阅读材料](further-reading-about-the-mfc-odbc-classes.md)

基于 ODBC 的 MFC 数据库类旨在提供对可用 ODBC 驱动程序的任何数据库的访问。 由于类使用 ODBC，您的应用程序可以访问许多不同的数据格式和不同的本地/远程配置的数据。 您不必编写特殊情况代码来处理不同的数据库管理系统 （DBMS）。 只要用户具有他们想要访问的数据的适当 ODBC 驱动程序，他们就可以使用您的程序操作存储在其中的表中的数据。

## <a name="see-also"></a>另请参阅

[开放数据库连接 （ODBC）](open-database-connectivity-odbc.md)
