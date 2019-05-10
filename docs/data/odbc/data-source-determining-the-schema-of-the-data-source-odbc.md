---
title: 数据源：确定数据源 (ODBC) 的架构
ms.date: 11/04/2016
helpviewer_keywords:
- ODBC data sources [C++], schema
- schemas [C++], data sources
- data sources [C++], determining schema
ms.assetid: 17284acb-eb10-4f27-9944-ad1d973c0b05
ms.openlocfilehash: c419a3ac2d870e6a85675492ee6c9b726427a0e9
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62395971"
---
# <a name="data-source-determining-the-schema-of-the-data-source-odbc"></a>数据源：确定数据源 (ODBC) 的架构

本主题适用于 MFC ODBC 类。

若要设置数据成员在`CRecordset`对象，您需要知道要连接到数据源的架构。 确定数据源的架构，涉及到获取的数据源中表的列表，每个表中的列，每个列的数据类型的列表，以及存在任何索引。

## <a name="see-also"></a>请参阅

[数据源 (ODBC)](../../data/odbc/data-source-odbc.md)<br/>
[数据源：管理连接 (ODBC)](../../data/odbc/data-source-managing-connections-odbc.md)