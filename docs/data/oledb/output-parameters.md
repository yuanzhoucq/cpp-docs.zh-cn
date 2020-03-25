---
title: 输出参数
ms.date: 10/24/2018
helpviewer_keywords:
- OLE DB, stored procedures
- stored procedures, calling
- stored procedures, parameters
- procedure calls
- procedure calls, stored procedures
ms.assetid: 4f7c2700-1c2d-42f3-8c9f-7e83962b2442
ms.openlocfilehash: ece626eb7fbecae9b90321ccc2569607897cf520
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80209854"
---
# <a name="output-parameters"></a>输出参数

调用存储过程类似于运行 SQL 命令。 主要区别在于，存储过程使用输出参数（或 "outparameters"）并返回值。

在下面的存储过程中，第一个 "？" 是返回值（phone），第二个 "？" 是输入参数（name）：

```cpp
DEFINE_COMMAND_EX(CMySProcAccessor, _T("{ ? = SELECT phone FROM shippers WHERE name = ? }"))
```

在参数映射中指定 in 和 out 参数：

```cpp
BEGIN_PARAM_MAP(CMySProcAccessor)
   SET_PARAM_TYPE(DBPARAMIO_OUTPUT)
   COLUMN_ENTRY(1, m_Phone)   // Phone is the return value
   SET_PARAM_TYPE(DBPARAMIO_INPUT)
   COLUMN_ENTRY(2, m_Name)   // Name is the input parameter
END_PARAM_MAP()
```

应用程序必须处理从存储过程返回的输出。 在结果处理期间，不同的 OLE DB 访问接口返回输出参数和返回值的时间不同。 例如，在使用者检索或取消了存储过程返回的结果集之前，适用于 SQL Server 的 Microsoft OLE DB 提供程序（SQLOLEDB）不会提供输出参数和返回代码。 输出将从服务器的最后一个 TDS 数据包中返回。

## <a name="row-count"></a>行计数

如果使用 OLE DB 使用者模板执行具有 outparameters 的存储过程，则在关闭行集之前，不会设置行计数。

例如，假设有一个包含行集和 outparameter 的存储过程：

```sql
create procedure sp_test
   @_rowcount integer output
as
   select top 50 * from test
   @_rowcount = @@rowcount
return 0
```

`@_rowcount` outparameter 报告从测试表中返回的行数。 但是，此存储过程将行数限制为50。 例如，如果测试中有100行，则行计数将为50（因为此代码仅检索最上面的50行）。 如果表中只有30行，则行计数将为30。 在提取 outparameter 值之前，请务必调用 `Close` 或 `CloseAll` 来填充。

## <a name="see-also"></a>另请参阅

[使用存储过程](../../data/oledb/using-stored-procedures.md)
