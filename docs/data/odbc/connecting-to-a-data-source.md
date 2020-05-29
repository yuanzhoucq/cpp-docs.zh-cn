---
title: 连接数据源
ms.date: 11/04/2016
helpviewer_keywords:
- database connections [C++], ODBC
- ODBC connections [C++], using
- connections [C++], data source
- databases [C++], connecting to
- data sources [C++], connecting to
- ODBC data sources [C++], connections
- database connections [C++], MFC ODBC classes
ms.assetid: ef6c8c98-5979-43a8-9fb5-5bb06fc59f36
ms.openlocfilehash: 712910aca2622f2678b8b9d06b18a2fdbf9157e4
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80213338"
---
# <a name="connecting-to-a-data-source"></a>连接数据源

ODBC 数据源是一组特定的数据、访问该数据所需的信息和数据源的位置，可以使用数据源名称进行描述。 从程序的角度来看，数据源包括数据、DBMS、网络（如果有）和 ODBC。

若要访问数据源所提供的数据，您的程序必须首先建立与数据源的连接。 所有数据访问都通过该连接进行管理。

数据源连接由类[CDatabase](../../mfc/reference/cdatabase-class.md)封装。 将 `CDatabase` 对象连接到数据源时，可以执行以下操作：

- 构造[记录集](../../mfc/reference/crecordset-class.md)，它从表或查询中选择记录。

- 管理[事务](../../data/odbc/transaction-odbc.md)，对更新进行批处理，以便一次提交到数据源（或者整个事务都将回滚以便数据源不变）（如果数据源支持所需的事务级别）。

- 直接执行[SQL](../../data/odbc/sql.md)语句。

完成数据源连接的处理后，关闭 `CDatabase` 的对象，并将其销毁或重复用于新连接。 有关数据源连接的详细信息，请参阅[数据源（ODBC）](../../data/odbc/data-source-odbc.md)。

## <a name="see-also"></a>另请参阅

[ODBC 和 MFC](../../data/odbc/odbc-and-mfc.md)
