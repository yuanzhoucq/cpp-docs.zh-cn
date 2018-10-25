---
title: ODBC 和 MFC |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- ODBC [C++], MFC
- connections [C++], databases
- connections [C++], data source
- databases [C++], connecting to
- data sources [C++], connecting to
- MFC [C++], ODBC and
- database connections [C++], MFC ODBC classes
ms.assetid: 98f02fd7-1235-437b-89a9-edfd0fc797f7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: b6a712b28fba569bfb46124f828e85dfa5dbb229
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/25/2018
ms.locfileid: "50079501"
---
# <a name="odbc-and-mfc"></a>ODBC 和 MFC

> [!NOTE]
>  若要使用 MFC 数据库类，必须具有相应的 ODBC 驱动程序的数据源。 SQL Server 的最新 Microsoft ODBC 驱动程序[适用于 SQL Server 的 Microsoft ODBC Driver 13](https://www.microsoft.com/download/details.aspx?id=50420)。 大多数数据库供应商为 Windows 提供的 ODBC 驱动程序。

本主题介绍 Microsoft 基础类 (MFC) 库的基于 ODBC 的数据库类的主要概念，并概述了类如何协同工作。 有关 ODBC 和 MFC 的详细信息，请参阅以下主题：

- [连接到数据源](connecting-to-a-data-source.md)

- [选择和操作记录](selecting-and-manipulating-records.md)

- [在窗体中显示和操作数据](displaying-and-manipulating-data-in-a-form.md)

- [使用文档和视图](working-with-documents-and-views.md)

- [访问 ODBC 和 SQL](access-to-odbc-and-sql.md)

- [有关 MFC ODBC 类的其他阅读材料](further-reading-about-the-mfc-odbc-classes.md)

基于 ODBC 的 MFC 数据库类旨在提供对任何其数据库的 ODBC 驱动程序可用的访问。 因为这些类使用 ODBC，你的应用程序可以访问许多不同的数据格式和不同的本地/远程配置中的数据。 您不必编写特殊处理代码来处理不同的数据库管理系统 (Dbms)。 只要用户具有相应的 ODBC 驱动程序为他们想要访问的数据，它们可以使用您的程序来处理存储在其中的表中的数据。

## <a name="see-also"></a>请参阅

[开放式数据库连接 (ODBC)](open-database-connectivity-odbc.md)