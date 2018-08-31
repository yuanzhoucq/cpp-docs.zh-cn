---
title: db_column |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.db_column
dev_langs:
- C++
helpviewer_keywords:
- db_column attribute
ms.assetid: 58da4afc-f69c-4ae6-af9a-3f9515f56081
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 10acf2b69eaa6b49145e671d437f18dfaff8e499
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/29/2018
ms.locfileid: "43195785"
---
# <a name="dbcolumn"></a>db_column

将指定的列绑定到行集中的变量。

## <a name="syntax"></a>语法

```cpp
[ db_column(
   ordinal,
   dbtype,
   precision,
   scale,
   status,
   length
) ]
```

#### <a name="parameters"></a>参数

*序号*  
列序号 (`DBCOLUMNINFO`序号) 或列名称 （ANSI 或 Unicode 字符串） 要将数据绑定到行集中的字段相对应。 如果使用数字，则可以跳过连续序号 (例如： 1、 2、 3、 5)。 如果您使用的 OLE DB 访问接口支持的名称包含空格。 例如，可以使用以下格式：

```cpp
[db_column("2")] TCHAR szCity[30];
[db_column(L"city_name")] TCHAR szCity[30];
```

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

**db_column**将指定的表列绑定到行集中的变量。 分隔可以参与在 OLE DB 中的成员数据`IAccessor`-基于绑定。 此属性设置了通常使用 OLE DB 使用者宏定义的列映射[BEGIN_COLUMN_MAP](../data/oledb/begin-column-map.md)， [END_COLUMN_MAP](../data/oledb/end-column-map.md)，并[COLUMN_ENTRY](../data/oledb/column-entry.md)。 这些操作 OLE DB [DBBINDING 结构](/previous-versions/windows/desktop/ms716845\(v=vs.85\))绑定指定的列。 您会使用标记每个成员**db_column**属性将占用列项的窗体中的列映射中的一个条目。 因此，调用此属性，可使列映射，即，命令或表类中。

使用**db_column**结合使用[db_table](../windows/db-table.md)或[db_command](../windows/db-command.md)属性。

编译器时使用者特性提供程序适用于类，此属性，将重命名为类\_ *YourClassName*访问器，其中*名为 YourClassName*是您为指定的名称类和编译器还将创建一个名为类*名为 YourClassName*，它派生\_*名为 YourClassName*访问器。  将在类视图中看到这两个类。

有关应用程序中使用此属性的示例，请参阅示例[AtlAgent](https://github.com/Microsoft/VCSamples)，并[MultiRead](https://github.com/Microsoft/VCSamples)。

## <a name="example"></a>示例

此示例将列绑定到表中**长**数据成员和指定状态和长度的字段。

```cpp
// db_column_1.cpp
// compile with: /LD
#include <atlbase.h>
#include <atlplus.h>
#include <atldbcli.h>

[ db_command(L"Select * from Products") ]
class CProducts {
   DBSTATUS m_dwProductIDStatus;
   DBLENGTH m_dwProductIDLength;

   [ db_column("1", status="m_dwProductIDStatus", length="m_dwProductIDLength") ] LONG m_ProductID;
};
```

## <a name="example"></a>示例

此示例将绑定到四个列**长**，字符字符串、 一个时间戳，和一个`DB_NUMERIC`以该顺序的整数。

```cpp
// db_column_2.cpp
// compile with: /LD
#include <atlbase.h>
#include <atlplus.h>
#include <atldbcli.h>

[ db_command(L"Select * from Products") ]
class CProducts {
   [db_column("1")] LONG m_OrderID;
   [db_column("2")] TCHAR m_CustomerID[6];
   [db_column("4")] DB_NUMERIC m_OrderDate;
   [db_column("7", dbtype="DBTYPE_NUMERIC")] DB_NUMERIC m_ShipVia;
};
```

## <a name="requirements"></a>要求

### <a name="attribute-context"></a>特性上下文

|||
|-|-|
|**适用对象**|**类**，**结构**，成员、 方法|
|**可重复**|否|
|**必需的特性**|无|
|**无效的特性**|无|

有关特性上下文的详细信息，请参见 [特性上下文](../windows/attribute-contexts.md)。

## <a name="see-also"></a>请参阅

[OLE DB 使用者特性](../windows/ole-db-consumer-attributes.md)  
[类特性](../windows/class-attributes.md)  
