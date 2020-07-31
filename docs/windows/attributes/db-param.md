---
title: db_param （c + + COM 特性）
ms.date: 10/02/2018
f1_keywords:
- vc-attr.db_param
helpviewer_keywords:
- db_param attribute
ms.assetid: a28315f5-4722-459e-92ef-32e83c0b205a
ms.openlocfilehash: 1a32dcceae1e4e4fbc730101381eda84b5350ffd
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87215304"
---
# <a name="db_param"></a>db_param

将指定的成员变量与输入或输出参数关联，并将变量分隔。

## <a name="syntax"></a>语法

```cpp
[ db_param(ordinal, paramtype="DBPARAMIO_INPUT", dbtype, precision, scale, status, length) ]
```

### <a name="parameters"></a>参数

*序号*<br/>
与行集中要将数据绑定到的字段相对应的列号（DBCOLUMNINFO 序数）。

*paramtype*<br/>
可有可无要为参数设置的类型。 提供程序仅支持基础数据源支持的参数 i/o 类型。 该类型是一个或多个 DBPARAMIOENUM 值的组合：

- DBPARAMIO_INPUT 输入参数。

- DBPARAMIO_OUTPUT 输出参数。

- DBPARAMIO_NOTPARAM 访问器没有参数。 如果 `eParamIO` 在行访问器中将此值设置为此值，则将提醒用户忽略参数。

*dbtype*<br/>
可有可无列项的 OLE DB[类型指示符](/previous-versions/windows/desktop/ms711251(v=vs.85))。

*精度*<br/>
可有可无要用于列项的精度。 有关详细信息，请参阅 `bPrecision` [DBBINDING 结构](/previous-versions/windows/desktop/ms716845(v=vs.85))的元素说明

*scale*<br/>
可有可无要用于列项的刻度。 有关详细信息，请参阅 `bScale` [DBBINDING 结构](/previous-versions/windows/desktop/ms716845(v=vs.85))的元素说明

*status*<br/>
可有可无用于保存此列的状态的成员变量。 状态指示列值是否为数据值或其他值（如 NULL）。 有关可能的值，请参阅*OLE DB 程序员参考*中的[状态](/previous-versions/windows/desktop/ms722617(v=vs.85))。

*length*<br/>
可有可无一个成员变量，用于保存列的大小（以字节为单位）。

## <a name="remarks"></a>备注

**db_param**定义在命令中使用的参数;因此，可将它用于 `db_command` 。 例如，可以使用**db_param**来绑定 SQL 查询或存储过程中的参数。 存储过程中的参数由问号（？）表示，您应按照参数出现的顺序来绑定数据成员。

**db_param**分隔可参与基于 OLE DB 的绑定的成员数据 `ICommandWithParameters` 。 它设置指定参数的参数类型（输入或输出）、OLE DB 类型、精度、小数位数、状态和长度。 此属性将 OLE DB 使用者宏插入 BEGIN_PARAM_MAP .。。END_PARAM_MAP。 使用**db_param**特性标记的每个成员都将在映射中以 COLUMN_ENTRY 的形式占用一个条目。

**db_param**与[db_table](db-table.md)或[db_command](db-command.md)特性结合使用。

当使用者特性提供程序将此特性应用于类时，编译器会将类重命名为 \_ *YourClassName*访问器，其中*YourClassName*是您赋予类的名称，并且编译器还将创建一个名为*YourClassName*的类，该类派生自 \_ *YourClassName*访问器。  将在类视图中看到这两个类。

## <a name="example"></a>示例

下面的示例基于 Northwind 数据库中的 SalesbyYear 存储过程创建一个 command 类。 它将存储过程中的第一个参数与变量相关联 `m_RETURN_VALUE` ，并将其定义为输出参数。 它将最后两个（输入）参数与 `m_Beginning_Date` 和相关联 `m_Ending_Date` 。

下面的示例将 `nOutput` 变量与 output 参数相关联。

```cpp
// db_param.cpp
// compile with: /LD
#include <atlbase.h>
#include <atlplus.h>
#include <atldbcli.h>

[ db_source(L"my_connection_string"),
  db_command(L"{ ? = CALL dbo.\"Sales by Year\"(?,?) }")
]
struct CSalesbyYear {
   DBSTATUS m_dwShippedDateStatus;
   DBSTATUS m_dwOrderIDStatus;
   DBSTATUS m_dwSubtotalStatus;
   DBSTATUS m_dwYearStatus;

   DBLENGTH m_dwShippedDateLength;
   DBLENGTH m_dwOrderIDLength;
   DBLENGTH m_dwSubtotalLength;
   DBLENGTH m_dwYearLength;

   // Bind columns
   [ db_column("1", status="m_dwShippedDateStatus", length="m_dwShippedDateLength") ] DBTIMESTAMP m_ShippedDate;
   [ db_column("2", status="m_dwOrderIDStatus", length="m_dwOrderIDLength") ] LONG m_OrderID;
   [ db_column("3", status="m_dwSubtotalStatus", length="m_dwSubtotalLength") ] CURRENCY m_Subtotal;
   [ db_column("4", status="m_dwYearStatus", length="m_dwYearLength") ] TCHAR m_Year[31];

   // Bind parameters
   [ db_param("1", paramtype="DBPARAMIO_OUTPUT") ] LONG m_RETURN_VALUE;
   [ db_param("2", paramtype="DBPARAMIO_INPUT") ] DBTIMESTAMP m_Beginning_Date;
   [ db_param("3", paramtype="DBPARAMIO_INPUT") ] DBTIMESTAMP m_Ending_Date;
};
```

## <a name="requirements"></a>要求

### <a name="attribute-context"></a>特性上下文

|||
|-|-|
|**适用于**|**`class`**、 **`struct`** 、成员、方法、本地|
|**且**|否|
|**必需属性**|无|
|**无效的特性**|无|

有关特性上下文的详细信息，请参见 [特性上下文](cpp-attributes-com-net.md#contexts)。

## <a name="see-also"></a>另请参阅

[OLE DB 使用者属性](ole-db-consumer-attributes.md)
