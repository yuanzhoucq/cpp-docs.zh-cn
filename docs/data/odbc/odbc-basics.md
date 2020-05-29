---
title: ODBC 基础
ms.date: 11/04/2016
helpviewer_keywords:
- ODBC cursor library [ODBC], ODBC components
- ODBC components
- ODBC components, required components
- ODBC, about ODBC
- ODBC, components
ms.assetid: ec529702-0fb2-4754-b8de-d1efa8eca18f
ms.openlocfilehash: 042b1ce6d12e4f4a2be57c0e2e8e01d9750f5357
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80213182"
---
# <a name="odbc-basics"></a>ODBC 基础

本主题提供开放式数据库连接（ODBC）的基础知识：

- [ODBC 如何处理数据库类](../../data/odbc/odbc-and-the-database-classes.md)

- [ODBC 驱动程序如何使用动态集](../../data/odbc/odbc-driver-requirements-for-dynasets.md)

- [需要与应用程序一起重新发布的 ODBC 组件](../../data/odbc/redistributing-odbc-components-to-your-customers.md)

还需要阅读相关主题[odbc： Odbc 游标库](../../data/odbc/odbc-the-odbc-cursor-library.md)。

> [!NOTE]
> ODBC 数据源可通过 MFC ODBC 类访问，如本主题中所述，或通过 MFC 数据访问对象（DAO）类访问。

> [!NOTE]
> MFC ODBC 类支持 Unicode 和多线程处理。 有关多线程支持的详细信息，请参阅[ODBC 类和线程](../../data/odbc/odbc-classes-and-threads.md)

ODBC 是一个调用级接口，它允许应用程序访问存在 ODBC 驱动程序的任何数据库中的数据。 使用 ODBC，可以创建数据库应用程序，以便访问您的最终用户具有其 ODBC 驱动程序的任何数据库。 ODBC 提供了一个 API，使您的应用程序可以独立于源数据库管理系统（DBMS）。

ODBC 是 Microsoft Windows Open Services 体系结构（WOSA）的数据库部分，它是一个接口，它允许基于 Windows 的桌面应用程序连接到多个计算环境，而无需为每个平台重写应用程序。

下面是 ODBC 的组件：

- ODBC API

   函数调用库、一组错误代码和用于访问 Dbms 上数据的标准[SQL](../../data/odbc/sql.md)语法。

- ODBC 驱动程序管理器

   动态链接库（Odbc32.lib），用于代表应用程序加载 ODBC 数据库驱动程序。 此 DLL 对应用程序是透明的。

- ODBC 数据库驱动程序

   处理特定 Dbms 的 ODBC 函数调用的一个或多个 Dll。 有关提供的驱动程序的列表，请参阅[ODBC Driver list](../../data/odbc/odbc-driver-list.md)。

- [ODBC 游标库](../../data/odbc/odbc-the-odbc-cursor-library.md)

   驻留在 ODBC 驱动程序管理器和驱动程序之间并处理数据滚动的动态链接库（Odbccr32）。

- [ODBC 管理器](../../data/odbc/odbc-administrator.md)

   一种用于配置 DBMS 以使其可用作应用程序的数据源的工具。

应用程序通过专门为 DBMS 编写的 ODBC 驱动程序而不是直接处理 DBMS，实现了 Dbms 的独立性。 驱动程序将调用转换为其 DBMS 可以使用的命令，从而简化了开发人员的工作，使其可用于各种数据源。

数据库类支持具有 ODBC 驱动程序的任何数据源。 例如，这可能包括关系数据库、索引顺序访问方法（ISAM）数据库、Microsoft Excel 电子表格或文本文件。 ODBC 驱动程序管理与数据源的连接，SQL 用于从数据库中选择记录。

有关此版本的 Visual C++ 中包含的 ODBC 驱动程序列表以及有关获取其他驱动程序的信息，请参阅 [ODBC 驱动程序列表](../../data/odbc/odbc-driver-list.md)。

## <a name="see-also"></a>另请参阅

[开放式数据库连接 (ODBC)](../../data/odbc/open-database-connectivity-odbc.md)
