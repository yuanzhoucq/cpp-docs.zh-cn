---
title: 动态集的 ODBC 驱动程序要求 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- ODBC recordsets, dynasets
- drivers, for dynasets
- drivers, ODBC
- recordsets, dynasets
- dynasets
- ODBC drivers, dynasets
ms.assetid: 585cc67b-4d92-404b-9903-d769cd17badc
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: d9fad26440cea2c8ec2efd7d07dacb83547252e3
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="odbc-driver-requirements-for-dynasets"></a>动态集的 ODBC 驱动程序需求
在 MFC ODBC 数据库类中，动态记录集是记录集具有动态属性：它们保持同步与数据源以某些方式。 MFC 动态记录集 （但不是仅向前的记录集） 需要与级别 2 API 一致性 ODBC 驱动程序。 如果驱动程序你[数据源](../../data/odbc/data-source-odbc.md)符合级别 1 API 设置，你仍然可以使用可更新和只读快照以及只进的记录集，但不是能使用动态集。 但是，如果它支持扩展的提取和键集驱动游标级别 1 驱动程序，就可以支持动态记录集。  
  
 在 ODBC 术语中，动态记录集和快照统称为游标。 一种用于跟踪其位置在记录集中使用的机制。 有关动态集的驱动程序要求的详细信息，请参阅[动态集](../../data/odbc/dynaset.md)。 有关游标的详细信息，请参阅[开放式数据库连接 (ODBC)](https://msdn.microsoft.com/en-us/library/ms710252.aspx) MSDN 文档中的 SDK。  
  
> [!NOTE]
>  可更新记录集，ODBC 驱动程序必须支持任一定位的更新语句或 **:: SQLSetPos** ODBC API 函数。 如果支持这两，MFC 使用 **:: SQLSetPos**为提高效率。 或者，生成的快照，你可以使用的是光标库，它为可更新快照 （静态游标和定位的 update 语句） 提供所需的支持。  
  
## <a name="see-also"></a>请参阅  
 [ODBC 基础](../../data/odbc/odbc-basics.md)