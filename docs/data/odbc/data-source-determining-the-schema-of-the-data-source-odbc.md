---
title: "数据源： 确定数据源 (ODBC) 的架构 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- ODBC data sources [C++], schema
- schemas [C++], data sources
- data sources [C++], determining schema
ms.assetid: 17284acb-eb10-4f27-9944-ad1d973c0b05
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: fc425cf767db6939223288ebe74dcbc7fd4cf5b9
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="data-source-determining-the-schema-of-the-data-source-odbc"></a>数据源：确定数据源的架构 (ODBC)
本主题适用于 MFC ODBC 类。  
  
 若要设置数据成员你`CRecordset`对象，你需要知道你连接到数据源的架构。 确定数据源的架构，包括需要获得的数据源中的表列表、 列表中每个表的列，每个列的数据类型以及存在任何索引。  
  
## <a name="see-also"></a>请参阅  
 [数据源 (ODBC)](../../data/odbc/data-source-odbc.md)   
 [数据源：管理连接 (ODBC)](../../data/odbc/data-source-managing-connections-odbc.md)