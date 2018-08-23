---
title: db_param |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.db_param
dev_langs:
- C++
helpviewer_keywords:
- db_param attribute
ms.assetid: a28315f5-4722-459e-92ef-32e83c0b205a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: c3bfa286e253ef634a42fea5a5c926981174c400
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/22/2018
ms.locfileid: "42612996"
---
# <a name="dbparam"></a>db_param

指定的成员变量相关联的输入或输出参数和分隔变量。

## <a name="syntax"></a>语法

```cpp
[ db_param(
   ordinal,
   paramtype="DBPARAMIO_INPUT",
   dbtype,
   precision,
   scale,
   status,
   length
) ]
```

### <a name="parameters"></a>参数

*序号*  
列对应的编号 （DBCOLUMNINFO 序号） 到要将数据绑定到行集中的字段。

*paramtype* （可选）  
要为参数设置的类型。 提供程序仅支持参数 I/O 类型所支持的基础数据源。 类型为一个或多个 DBPARAMIOENUM 值的组合：

- DBPARAMIO_INPUT 输入参数。

- DBPARAMIO_OUTPUT 输出参数。

- DBPARAMIO_NOTPARAM 访问器没有任何参数。 设置`eParamIO`为行中此值的访问器提醒用户参数将被忽略。

*dbtype* （可选）  
OLE DB[类型指示符](/previous-versions/windows/desktop/ms711251\(v=vs.85\))列条目。

*精度*（可选）  
要用于列条目精度。 有关详细信息，请参阅的说明`bPrecision`元素的[DBBINDING 结构](/previous-versions/windows/desktop/ms716845\(v=vs.85\))

*缩放*（可选）  
要用于列项目的比例。 有关详细信息，请参阅的说明`bScale`元素的[DBBINDING 结构](/previous-versions/windows/desktop/ms716845\(v=vs.85\))

*状态*（可选）  
成员变量，用来保存此列的状态。 状态指示该列的值是数据值或其他某个值，如空值。 有关可能的值，请参阅[状态](/previous-versions/windows/desktop/ms722617\(v=vs.85\))中*OLE DB 程序员参考*。

*长度*（可选）  
成员变量，用来保存的列的大小以字节为单位。

## <a name="remarks"></a>备注

**db_param**定义的参数，在命令中使用; 因此可以将它与`db_command`。 例如，可以使用**db_param**绑定中的 SQL 查询或存储的过程的参数。 由问号 （？），表示存储过程中的参数，并应将数据成员绑定参数的显示顺序。

**db_param**分隔可以参与在 OLE DB 中的成员数据`ICommandWithParameters`-基于绑定。 它设置参数类型 （输入或输出）、 OLE DB 类型、 精度、 小数位数、 状态和为指定的参数的长度。 此属性将插入的 OLE DB 使用者宏 BEGIN_PARAM_MAP...END_PARAM_MAP。 您会使用标记每个成员**db_param**属性将占用 COLUMN_ENTRY 窗体中的映射中的一个条目。

**db_param**与可以结合使用[db_table](../windows/db-table.md)或[db_command](../windows/db-command.md)属性。

编译器时使用者特性提供程序适用于类，此属性，将重命名为类\_ *YourClassName*访问器，其中*名为 YourClassName*是您为指定的名称类和编译器还将创建一个名为类*名为 YourClassName*，它派生\_*名为 YourClassName*访问器。  将在类视图中看到这两个类。

## <a name="example"></a>示例

以下示例创建基于 Northwind 数据库中的 SalesbyYear 存储过程的命令类。 它将关联的存储过程的第一个参数`m_RETURN_VALUE`变量，并将其定义为 output 参数。 它将使用最后两个 （输入） 参数相关联`m_Beginning_Date`和`m_Ending_Date`。

下面的示例关联`nOutput`使用输出参数变量。

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
|**适用对象**|**类**，**结构**，成员、 方法、 本地|
|**可重复**|否|
|**必需的特性**|无|
|**无效的特性**|无|

有关特性上下文的详细信息，请参见 [特性上下文](../windows/attribute-contexts.md)。

## <a name="see-also"></a>请参阅

[OLE DB 使用者特性](../windows/ole-db-consumer-attributes.md)  
