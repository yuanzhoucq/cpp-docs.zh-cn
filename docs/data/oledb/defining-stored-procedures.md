---
title: 定义存储过程
ms.date: 10/24/2018
helpviewer_keywords:
- stored procedures, syntax
- OLE DB, stored procedures
- stored procedures, defining
- stored procedures, OLE DB
ms.assetid: 54949b81-3275-4dd9-96e4-3eda1ed755f2
ms.openlocfilehash: 9bab086bf6982eae5779d3199cfd2ac2c8efe77f
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80210999"
---
# <a name="defining-stored-procedures"></a>定义存储过程

在调用存储过程之前，必须先使用[DEFINE_COMMAND](../../data/oledb/define-command.md)宏对其进行定义。 定义该命令时，请使用问号（？）作为参数标记来表示参数：

```cpp
DEFINE_COMMAND_EX(CMySProcAccessor, _T("{INSERT {name, phone} INTO shippers (?,?)}"))
```

本主题的代码示例中使用的语法（使用大括号等）特定于 SQL Server。 在存储过程中使用的语法可能因使用的提供程序而异。

接下来，在参数映射中，指定在命令中使用的参数，并按命令中出现的顺序列出参数：

```cpp
BEGIN_PARAM_MAP(CMySProcAccessor)
   SET_PARAM_TYPE(DBPARAMIO_INPUT)
   COLUMN_ENTRY(1, m_Name)   // name corresponds to first '?' param
   SET_PARAM_TYPE(DBPARAMIO_INPUT)
   COLUMN_ENTRY(2, m_Phone)  // phone corresponds to second '?' param
END_PARAM_MAP()
```

前面的示例定义了一个存储过程。 通常，为了有效地重复使用代码，数据库包含一组名称为的预定义存储过程，例如 `Sales by Year` 或 `dt_adduserobject`。 您可以使用 SQL Server Enterprise Manager 查看其定义。 按如下所示调用它们（的*位置：* 参数依赖于存储过程的接口）：

```cpp
DEFINE_COMMAND_EX(CMySProcAccessor, _T("{CALL \"Sales by Year\" (?,?) }"))
DEFINE_COMMAND_EX(CMySProcAccessor, _T("{CALL dbo.dt_adduserobject (?,?) }"))
```

接下来，声明命令类：

```cpp
class CMySProc : public CCommand<CAccessor<CMySProcAccessor>>
```

最后，在 `OpenRowset` 中调用存储过程，如下所示：

```cpp
CSession m_session;

HRESULT OpenRowset()
{
   return CCommand<CAccessor<CMySProcAccessor>>::Open(m_session);
}
```

另请注意，你可以使用数据库属性定义存储过程[db_command](../../windows/db-command.md)如下所示：

```cpp
db_command("{ ? = CALL dbo.dt_adduserobject }")
```

## <a name="see-also"></a>另请参阅

[使用存储过程](../../data/oledb/using-stored-procedures.md)
