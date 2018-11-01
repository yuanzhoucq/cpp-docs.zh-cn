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
ms.openlocfilehash: 81b1f6d06d909b5b046703b97c4574270efbdd46
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50591719"
---
# <a name="odbc-basics"></a>ODBC 基础

本主题提供的开放式数据库连接 (ODBC) 的基础知识：

- [ODBC 数据库类使用的工作方式](../../data/odbc/odbc-and-the-database-classes.md)

- [ODBC 驱动程序如何使用动态集](../../data/odbc/odbc-driver-requirements-for-dynasets.md)

- [使用你的应用程序需要重新分发的哪些 ODBC 组件](../../data/odbc/redistributing-odbc-components-to-your-customers.md)

您还需要阅读相关的文章[ODBC: ODBC 游标库](../../data/odbc/odbc-the-odbc-cursor-library.md)。

> [!NOTE]
> ODBC 数据源是可通过 MFC ODBC 类，如本主题中所述或 MFC 数据访问对象 (DAO) 类的访问。

> [!NOTE]
> MFC ODBC 类支持 Unicode 和多线程处理。 有关多线程支持的详细信息，请参阅[ODBC 类和线程](../../data/odbc/odbc-classes-and-threads.md)

ODBC 是一个调用级别接口，允许应用程序访问数据的 ODBC 驱动程序任何数据库中。 使用 ODBC，可以使用任何的数据库的最终用户所拥有的 ODBC 驱动程序访问权限创建数据库应用程序。 ODBC 提供了一个 API，使你的应用程序是独立于源数据库管理系统 (DBMS)。

ODBC 是数据库部分的 Microsoft Windows 打开服务体系结构 (WOSA) 中，这是使基于 Windows 的桌面应用程序连接到多个计算环境而无需重写每个平台的应用程序的接口。

ODBC 组件如下：

- ODBC API

   函数的一个库调用时，错误代码和一个标准的一组[SQL](../../data/odbc/sql.md)访问 Dbms 上的数据的语法。

- ODBC 驱动程序管理器

   将 ODBC 数据库驱动程序加载应用程序代表一个动态链接库 (所用的 Odbc32.dll)。 此 DLL 是透明的应用程序。

- ODBC 数据库驱动程序

   处理特定 Dbms 的 ODBC 函数调用的一个或多个 Dll。 提供的驱动程序的列表，请参阅[ODBC 驱动程序列表](../../data/odbc/odbc-driver-list.md)。

- [ODBC 游标库](../../data/odbc/odbc-the-odbc-cursor-library.md)

   一个动态链接库 (Odbccr32.dll) 驻留之间 ODBC 驱动程序管理器和驱动程序并处理滚动浏览数据。

- [ODBC 管理器](../../data/odbc/odbc-administrator.md)

   用于配置 DBMS，以使其可作为应用程序的数据源的工具。

应用程序来实现独立于 Dbms 的通过 ODBC 驱动程序专为 DBMS 编写的工作而不是直接使用 DBMS。 该驱动程序将转换成命令可以使用其 DBMS，从而简化了开发人员的工作并使其可用于各种数据源的调用。

数据库类支持对其具有 ODBC 驱动程序的任何数据源。 这可能，例如，包括关系数据库、 编制索引的顺序访问方法 (ISAM) 数据库、 Microsoft Excel 电子表格或文本文件。 ODBC 驱动程序管理到数据源的连接，SQL 用于从数据库中选择记录。

有关此版本的 Visual c + + 中包含的 ODBC 驱动程序的列表和有关获取其他驱动程序的信息，请参阅[ODBC 驱动程序列表](../../data/odbc/odbc-driver-list.md)。

## <a name="see-also"></a>请参阅

[开放式数据库连接 (ODBC)](../../data/odbc/open-database-connectivity-odbc.md)