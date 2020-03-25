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
ms.openlocfilehash: 0d4d3948add665c54be3d3b0596a7a6fc0e414f5
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80212727"
---
# <a name="redistributing-odbc-components-to-your-customers"></a>为客户重新分发 ODBC 组件

如果将 ODBC 管理程序的功能合并到应用程序中，还必须将运行这些程序的文件分发给用户。 这些 ODBC 文件位于 Visual C++ Cd-rom 的 \OS\System 目录中。 Redistrb. wri 文件和相同目录中的许可协议包含可重新分发的 ODBC 文件的列表。

请参阅文档，了解你计划交付的任何 ODBC 驱动程序。 需要确定要交付哪些 Dll 和其他文件。 还应阅读将[Odbc 组件重新分发给客户](../../data/odbc/redistributing-odbc-components-to-your-customers.md)，这说明了如何再分发 odbc 组件。

此外，在大多数情况下，您还需要包含一个文件。 Odbccr32 是 ODBC 游标库。 此库为第1级驱动程序提供向前和向后滚动功能。 它还提供了支持快照的功能。 有关 ODBC 游标库的详细信息，请参阅 odbc [： Odbc 游标库](../../data/odbc/odbc-the-odbc-cursor-library.md)。

以下主题提供有关将 ODBC 与数据库类结合使用的详细信息：

- [ODBC：ODBC 游标库](../../data/odbc/odbc-the-odbc-cursor-library.md)

- [ODBC：配置 ODBC 数据源](../../data/odbc/odbc-configuring-an-odbc-data-source.md)

- [ODBC：直接调用 ODBC API 函数](../../data/odbc/odbc-calling-odbc-api-functions-directly.md)

## <a name="see-also"></a>另请参阅

[ODBC 基础](../../data/odbc/odbc-basics.md)<br/>
[ODBC 管理器](../../data/odbc/odbc-administrator.md)
