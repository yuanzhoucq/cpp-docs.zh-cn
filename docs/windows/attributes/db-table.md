---
title: db_table （C++ COM 特性）
ms.date: 10/02/2018
f1_keywords:
- vc-attr.db_table
helpviewer_keywords:
- db_table attribute
ms.assetid: ff9eb957-4e6d-4175-afcc-fd8ea916cec0
ms.openlocfilehash: 2b3be55a4ea118ef3441d3ea93f63e19ebdb3d79
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80167246"
---
# <a name="db_table"></a>db_table

打开 OLE DB 表。

## <a name="syntax"></a>语法

```cpp
[ db_table(db_table, name, source_name, hresult) ]
```

### <a name="parameters"></a>parameters

*db_table*<br/>
一个字符串，该字符串指定数据库表的名称（例如 "产品"）。

name<br/>
可有可无用于处理该表的句柄的名称。 如果希望返回多行结果，则必须指定此参数。 **db_table**生成一个具有指定*名称*的变量，该变量可用于遍历行集或执行多个操作查询。

*source_name*<br/>
可有可无类的 `CSession` 变量或实例，该类具有应用于该命令的 `db_source` 属性。 请参阅 [db_source](db-source.md)。

*hresult*<br/>
可有可无标识将接收此数据库命令的 HRESULT 的变量。 如果该变量不存在，属性将自动插入。

## <a name="remarks"></a>备注

**db_table**创建一个[CTable](../../data/oledb/ctable-class.md)对象，该对象由 OLE DB 使用者用来打开表。 只能在类级别使用此特性;不能以内联方式使用它。 使用 `db_column` 将表列绑定到变量;使用 `db_param` 分隔参数的（设置参数类型等）。

当使用者特性提供程序将此特性应用于类时，编译器会将类重命名为 \_*YourClassName*访问器，其中*YourClassName*是你为类提供的名称，并且编译器还将创建一个名为*YourClassName*的类，该类派生自 \_*YourClassName*访问器。  将在类视图中看到这两个类。

## <a name="example"></a>示例

下面的示例将打开 Products 表以供 `CProducts`使用。

```cpp
// db_table.cpp
// compile with: /LD
#include <atlbase.h>
#include <atlplus.h>
#include <atldbcli.h>

[ db_table(L"dbo.Products") ]
class CProducts {
   [ db_column("1") ] LONG m_ProductID;
};
```

有关应用程序中使用的此属性的示例，请参阅[MultiRead](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/OLEDB/Consumer)。

## <a name="requirements"></a>要求

### <a name="attribute-context"></a>特性上下文

|||
|-|-|
|**适用对象**|**class**、 **struct**|
|**可重复**|否|
|**必需的特性**|无|
|**无效的特性**|无|

有关特性上下文的详细信息，请参见 [特性上下文](cpp-attributes-com-net.md#contexts)。

## <a name="see-also"></a>另请参阅

[OLE DB 使用者特性](ole-db-consumer-attributes.md)
