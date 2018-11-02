---
title: 数据源：确定数据源的架构 (ODBC)
ms.date: 11/04/2016
helpviewer_keywords:
- ODBC data sources [C++], schema
- schemas [C++], data sources
- data sources [C++], determining schema
ms.assetid: 17284acb-eb10-4f27-9944-ad1d973c0b05
ms.openlocfilehash: ed6500c5718cf90b39600b12659a3090fe9532ce
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50580738"
---
# <a name="data-source-determining-the-schema-of-the-data-source-odbc"></a>数据源：确定数据源的架构 (ODBC)

本主题适用于 MFC ODBC 类。

若要设置数据成员在`CRecordset`对象，您需要知道要连接到数据源的架构。 确定数据源的架构，涉及到获取的数据源中表的列表，每个表中的列，每个列的数据类型的列表，以及存在任何索引。

## <a name="see-also"></a>请参阅

[数据源 (ODBC)](../../data/odbc/data-source-odbc.md)<br/>
[数据源：管理连接 (ODBC)](../../data/odbc/data-source-managing-connections-odbc.md)