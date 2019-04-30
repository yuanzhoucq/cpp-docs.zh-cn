---
title: 动态集的 ODBC 驱动程序需求
ms.date: 11/04/2016
helpviewer_keywords:
- ODBC recordsets, dynasets
- drivers, for dynasets
- drivers, ODBC
- recordsets, dynasets
- dynasets
- ODBC drivers, dynasets
ms.assetid: 585cc67b-4d92-404b-9903-d769cd17badc
ms.openlocfilehash: c44e34023ecdeb994ea3a60ea3b699cd5b1488a3
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62395750"
---
# <a name="odbc-driver-requirements-for-dynasets"></a>动态集的 ODBC 驱动程序需求

在 MFC ODBC 数据库类中，动态集是记录集具有动态属性：它们保持与以下几个方面中的数据源同步。 MFC 动态集 （但不是仅向前的记录集） 需要使用符合性级别 2 API 的 ODBC 驱动程序。 如果驱动程序为你[数据源](../../data/odbc/data-source-odbc.md)符合级别 1 API 设置，您仍然可以使用可更新和只读快照和只进的记录集，但不是能使用动态集。 但是，第 1 级驱动程序可以支持动态集，如果它支持扩展的获取和由键集驱动的游标。

在 ODBC 术语中，动态集和快照都称为游标。 游标是一种机制，用于跟踪中记录集的位置使用。 有关程序需求的驱动程序要求的详细信息，请参阅[动态集](../../data/odbc/dynaset.md)。 有关游标的详细信息，请参阅[开放式数据库连接 (ODBC)](/sql/odbc/microsoft-open-database-connectivity-odbc) MSDN 文档中的 SDK。

> [!NOTE]
>  可更新的记录集，ODBC 驱动程序必须支持任一定位的 update 语句或`::SQLSetPos`ODBC API 函数。 如果两者都受支持，MFC 使用`::SQLSetPos`以提高效率。 或者，生成的快照，可以使用游标库，它为可更新的快照 （静态游标和定位的 update 语句） 提供所需的支持。

## <a name="see-also"></a>请参阅

[ODBC 基础](../../data/odbc/odbc-basics.md)