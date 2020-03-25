---
title: ODBC：配置 ODBC 数据源
ms.date: 11/04/2016
helpviewer_keywords:
- ODBC data sources, configuring
- ODBC connections, configuring
- configuring ODBC data sources
ms.assetid: 1cd03e6a-8d59-4eca-a8c6-1010582d5e67
ms.openlocfilehash: 43d385bea34ba885b9ae0f8efb6109e6959c2383
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80213130"
---
# <a name="odbc-configuring-an-odbc-data-source"></a>ODBC：配置 ODBC 数据源

若要在开发的应用程序中使用[数据源](../../data/odbc/data-source-odbc.md)，必须使用 ODBC 管理器对其进行配置。 ODBC 管理器会在 Windows 注册表中跟踪可用的数据源及其连接信息。 使用 ODBC 管理器可以在 "**数据源**" 对话框中添加、修改和删除数据源，还可以添加和删除 ODBC 驱动程序。

> [!NOTE]
>  当你使用 MFC 数据访问对象（DAO）类进行 ODBC 访问以及使用 MFC ODBC 类时，将应用此信息。

ODBC 管理器随 Microsoft 基础类（MFC）库数据库支持自动安装。 有关 ODBC 管理程序的详细信息，请参阅[Odbc 管理员](../../data/odbc/odbc-administrator.md)和联机 ODBC API 参考帮助系统。

有关如何为 MFC 数据库应用程序编写 ODBC 安装和管理程序的信息，请查阅[技术说明 48](../../mfc/tn048-writing-odbc-setup-and-administration-programs.md)。

## <a name="see-also"></a>另请参阅

[ODBC 基础](../../data/odbc/odbc-basics.md)<br/>
[ODBC：直接调用 ODBC API 函数](../../data/odbc/odbc-calling-odbc-api-functions-directly.md)
