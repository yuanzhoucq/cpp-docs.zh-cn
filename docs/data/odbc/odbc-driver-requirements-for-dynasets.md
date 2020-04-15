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
ms.openlocfilehash: c612e8ea91882a6e744a8f47afe0decbeba85358
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367203"
---
# <a name="odbc-driver-requirements-for-dynasets"></a>动态集的 ODBC 驱动程序需求

在 MFC ODBC 数据库类中，动态集是具有动态属性的记录集;它们在某些方面与数据源保持同步。 MFC 动态集（但不只转发记录集）需要具有 2 级 API 一致性的 ODBC 驱动程序。 如果[数据源](../../data/odbc/data-source-odbc.md)的驱动程序符合 1 级 API 集，您仍可以使用可更新和只读快照和仅转发记录集，但不能使用动态集。 但是，如果级别 1 驱动程序支持扩展提取和键集驱动的游标，则可以支持动态集。

在 ODBC 术语中，动态集和快照称为游标。 游标是用于跟踪其在记录集中的位置的机制。 有关发电机集的驱动程序要求的详细信息，请参阅[动态集](../../data/odbc/dynaset.md)。 有关游标的详细信息，请参阅 MSDN 文档中[的开放数据库连接 （ODBC）](/sql/odbc/microsoft-open-database-connectivity-odbc) SDK。

> [!NOTE]
> 对于可更新的记录集，您的 ODBC 驱动程序必须支持定位更新语句或`::SQLSetPos`ODBC API 功能。 如果两者都支持，MFC`::SQLSetPos`用于提高效率。 或者，对于快照，可以使用游标库，该库为可更新快照（静态游标和定位更新语句）提供所需的支持。

## <a name="see-also"></a>另请参阅

[ODBC 基础](../../data/odbc/odbc-basics.md)
