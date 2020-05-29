---
title: ODBC：配置 ODBC 数据源
ms.date: 11/04/2016
helpviewer_keywords:
- ODBC data sources, configuring
- ODBC connections, configuring
- configuring ODBC data sources
ms.assetid: 1cd03e6a-8d59-4eca-a8c6-1010582d5e67
ms.openlocfilehash: aaa69fd7e0b2b592cd7d5c4eff92f51d0ce5f680
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367196"
---
# <a name="odbc-configuring-an-odbc-data-source"></a>ODBC：配置 ODBC 数据源

要将[数据源](../../data/odbc/data-source-odbc.md)与已开发的应用程序一起使用，必须使用 ODBC 管理员对其进行配置。 ODBC 管理员在 Windows 注册表中跟踪可用数据源及其连接信息。 使用 ODBC 管理员在 **"数据源"** 对话框中添加、修改和删除数据源，并添加和删除 ODBC 驱动程序。

> [!NOTE]
> 当您使用 MFC 数据访问对象 （DAO） 类进行 ODBC 访问时和使用 MFC ODBC 类时，此信息将适用。

ODBC 管理员将自动安装 Microsoft 基础类 （MFC） 库数据库支持。 有关 ODBC 管理员计划的详细信息，请参阅[ODBC 管理员](../../data/odbc/odbc-administrator.md)和在线 ODBC API 参考帮助系统。

有关如何为 MFC 数据库应用程序编写 ODBC 设置和管理程序的信息，[技术说明 48](../../mfc/tn048-writing-odbc-setup-and-administration-programs.md)。

## <a name="see-also"></a>另请参阅

[ODBC 基础](../../data/odbc/odbc-basics.md)<br/>
[ODBC：直接调用 ODBC API 函数](../../data/odbc/odbc-calling-odbc-api-functions-directly.md)
