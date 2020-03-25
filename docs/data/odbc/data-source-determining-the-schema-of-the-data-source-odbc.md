---
title: 数据源：确定数据源的架构 (ODBC)
ms.date: 11/04/2016
helpviewer_keywords:
- ODBC data sources [C++], schema
- schemas [C++], data sources
- data sources [C++], determining schema
ms.assetid: 17284acb-eb10-4f27-9944-ad1d973c0b05
ms.openlocfilehash: 60ed77ec8870ba80832d4f8c73a8362062dc9c2a
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80213312"
---
# <a name="data-source-determining-the-schema-of-the-data-source-odbc"></a>数据源：确定数据源的架构 (ODBC)

本主题适用于 MFC ODBC 类。

若要在 `CRecordset` 对象中设置数据成员，需要知道要连接到的数据源的架构。 确定数据源的架构涉及获取数据源中的表的列表、每个表中的列列表、每个列的数据类型以及是否存在任何索引。

## <a name="see-also"></a>另请参阅

[数据源 (ODBC)](../../data/odbc/data-source-odbc.md)<br/>
[数据源：管理连接 (ODBC)](../../data/odbc/data-source-managing-connections-odbc.md)
