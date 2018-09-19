---
title: 数据源： 确定数据源 (ODBC) 的架构 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- ODBC data sources [C++], schema
- schemas [C++], data sources
- data sources [C++], determining schema
ms.assetid: 17284acb-eb10-4f27-9944-ad1d973c0b05
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: d9db21b7531f71ba40be64018b71c4e2e3e555e2
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46064966"
---
# <a name="data-source-determining-the-schema-of-the-data-source-odbc"></a>数据源：确定数据源的架构 (ODBC)

本主题适用于 MFC ODBC 类。  
  
若要设置数据成员在`CRecordset`对象，您需要知道要连接到数据源的架构。 确定数据源的架构，涉及到获取的数据源中表的列表，每个表中的列，每个列的数据类型的列表，以及存在任何索引。  
  
## <a name="see-also"></a>请参阅  

[数据源 (ODBC)](../../data/odbc/data-source-odbc.md)<br/>
[数据源：管理连接 (ODBC)](../../data/odbc/data-source-managing-connections-odbc.md)