---
title: 为客户重新分发 ODBC 组件
ms.date: 11/04/2016
helpviewer_keywords:
- ODBC components, redistributing
- ODBC, distributing components
- components [C++], distributing
- ODBC Administrator
- components [C++]
- components [C++], redistributing
ms.assetid: 17b065b4-a307-4b89-99ac-d05831cfab87
ms.openlocfilehash: 1a6ec6f5fdd3c32080d357ca58d31ccea271b7a4
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62330071"
---
# <a name="redistributing-odbc-components-to-your-customers"></a>为客户重新分发 ODBC 组件

如果将 ODBC 管理器程序的功能合并到应用程序，您必须还将分发到你的用户运行这些程序的文件。 这些 ODBC 文件位于 \OS\System 目录视觉对象的C++CD-ROM。 Redistrb.wri 文件和许可协议的相同目录中包含你可以重新分发 ODBC 文件的列表。

请查阅你打算发布的任何 ODBC 驱动程序的文档。 您需要确定哪些 Dll 和其他文件交付。 此外应阅读[为客户重新分发 ODBC 组件](../../data/odbc/redistributing-odbc-components-to-your-customers.md)，该文介绍了如何重新分发 ODBC 组件。

此外，您需要在大多数情况下包含一个其他文件。 Odbccr32.dll 是 ODBC 游标库。 此库提供 1 级驱动程序的向前和向后滚动功能。 它还提供了支持快照功能。 有关 ODBC 游标库的详细信息，请参阅[ODBC:ODBC 游标库](../../data/odbc/odbc-the-odbc-cursor-library.md)。

以下主题提供有关使用 ODBC 数据库类使用的详细信息：

- [ODBC：ODBC 游标库](../../data/odbc/odbc-the-odbc-cursor-library.md)

- [ODBC：配置 ODBC 数据源](../../data/odbc/odbc-configuring-an-odbc-data-source.md)

- [ODBC：直接调用 ODBC API 函数](../../data/odbc/odbc-calling-odbc-api-functions-directly.md)

## <a name="see-also"></a>请参阅

[ODBC 基础](../../data/odbc/odbc-basics.md)<br/>
[ODBC 管理器](../../data/odbc/odbc-administrator.md)