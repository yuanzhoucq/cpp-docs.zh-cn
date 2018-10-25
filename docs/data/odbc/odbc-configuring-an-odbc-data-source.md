---
title: ODBC： 配置 ODBC 数据源 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- ODBC data sources, configuring
- ODBC connections, configuring
- configuring ODBC data sources
ms.assetid: 1cd03e6a-8d59-4eca-a8c6-1010582d5e67
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: a9a0cd385596f62432f16b7e5abc4259a267dd76
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/25/2018
ms.locfileid: "50080307"
---
# <a name="odbc-configuring-an-odbc-data-source"></a>ODBC：配置 ODBC 数据源

若要使用[数据源](../../data/odbc/data-source-odbc.md)与已开发的应用程序，您必须使用 ODBC 管理器对其进行配置。 跟踪可用的数据源和连接信息在 Windows 注册表中的 ODBC 管理器。 使用 ODBC 管理器来添加、 修改和删除中的数据源**数据源**对话框添加和删除 ODBC 驱动程序。

> [!NOTE]
>  此信息应用于 MFC 数据访问对象 (DAO) 类用于 ODBC 访问和使用 MFC ODBC 类时。

ODBC 管理器会自动安装与 Microsoft 基础类 (MFC) 库数据库支持。 有关 ODBC 管理员程序的详细信息，请参阅[ODBC 管理器](../../data/odbc/odbc-administrator.md)和联机的 ODBC API 参考帮助系统。

有关如何编写 ODBC 安装和管理程序为 MFC 数据库应用程序信息[技术注意 48](../../mfc/tn048-writing-odbc-setup-and-administration-programs.md)。

## <a name="see-also"></a>请参阅

[ODBC 基础](../../data/odbc/odbc-basics.md)<br/>
[ODBC：直接调用 ODBC API 函数](../../data/odbc/odbc-calling-odbc-api-functions-directly.md)