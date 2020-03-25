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
ms.openlocfilehash: 3507a5ee7dcfb8bf4f4eee12ef9264c16ad904c2
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80213104"
---
# <a name="odbc-driver-requirements-for-dynasets"></a>动态集的 ODBC 驱动程序需求

在 MFC ODBC 数据库类中，动态集是包含动态属性的记录集;它们在某些方面与数据源保持同步。 MFC 动态集（但非只进记录集）需要具有2级 API 一致性的 ODBC 驱动程序。 如果[数据源](../../data/odbc/data-source-odbc.md)的驱动程序符合第1级 API 集，则仍可使用可更新和只读快照以及只进记录集，但不能使用动态集。 但是，如果第1级驱动程序支持扩展提取和由键集驱动的游标，则它可以支持动态集。

在 ODBC 术语中，动态集和快照称为游标。 游标是一种用于在记录集中跟踪其位置的机制。 有关动态集的驱动程序要求的详细信息，请参阅[动态集](../../data/odbc/dynaset.md)。 有关游标的详细信息，请参阅 MSDN 文档中的[开放式数据库连接（ODBC）](/sql/odbc/microsoft-open-database-connectivity-odbc) SDK。

> [!NOTE]
>  对于可更新的记录集，ODBC 驱动程序必须支持定位的 update 语句或 `::SQLSetPos` ODBC API 函数。 如果两者都受支持，MFC 将使用 `::SQLSetPos` 提高效率。 或者，对于快照，你可以使用游标库，该库为可更新的快照（静态游标和定位的 update 语句）提供所需的支持。

## <a name="see-also"></a>另请参阅

[ODBC 基础](../../data/odbc/odbc-basics.md)
