---
title: db_source （C++ COM 特性）
ms.date: 10/02/2018
f1_keywords:
- vc-attr.db_source
helpviewer_keywords:
- db_source attribute
ms.assetid: 0ec8bbf7-ade2-4899-bf4c-8608b92779bc
ms.openlocfilehash: 6346a8d6f60313dc17bbcbad062aa888857f0b67
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80167272"
---
# <a name="db_source"></a>db_source

创建与数据源的连接。

## <a name="syntax"></a>语法

```cpp
[ db_source(db_source, name, hresult) ]
```

### <a name="parameters"></a>parameters

*db_source*<br/>
用于连接到数据源的连接字符串。 有关连接字符串的格式，请参阅 Microsoft 数据访问组件（MDAC） SDK 中的[连接字符串和数据链接](/previous-versions/windows/desktop/ms718376(v=vs.85))。

name<br/>
可有可无在类上使用**db_source**时， *name*是应用了**db_source**属性的数据源对象的实例（请参阅示例1）。 在方法实现中使用**db_source**内联时， *name*是可用于访问数据源的变量（方法的本地）（请参阅示例2）。 将此*名称*传递到 `db_command` 的*source_name*参数，以将数据源与命令相关联。

*hresult*<br/>
可有可无标识将接收此数据库命令的 HRESULT 的变量。 如果该变量不存在，属性将自动插入。

## <a name="remarks"></a>备注

**db_source**创建一个[CDataSource](../../data/oledb/cdatasource-class.md)和一个[CSession](../../data/oledb/csession-class.md)对象，该对象共同表示与 OLE DB 使用者数据源的连接。

在类上使用**db_source**时，`CSession` 对象将成为类的成员。

在方法中使用**db_source**时，插入的代码将在方法范围内执行，并将 `CSession` 对象创建为局部变量。

**db_source**向类或方法中添加数据源属性。 它与 `db_command` （采用*db_source* *name*参数作为其*source_name*参数）结合使用。

当使用者特性提供程序将此特性应用于类时，编译器会将类重命名为 \_*YourClassName*访问器，其中*YourClassName*是你为类提供的名称，并且编译器还将创建一个名为*YourClassName*的类，该类派生自 \_*YourClassName*访问器。  将在类视图中看到这两个类。

有关应用程序中使用的此属性的示例，请参阅[MultiRead](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/OLEDB/Consumer)。

## <a name="example"></a>示例

此示例对类调用**db_source** ，以使用 Northwind 数据库创建到数据源的连接 `ds`。 `ds` 是数据源的句柄，可在内部用到 `CMyCommand` 类。

```cpp
// db_source_1.cpp
// compile with: /LD
#include <atlbase.h>
#include <atlplus.h>
#include <atldbcli.h>

[
  db_source(L"my_connection_string", name="ds"),
  db_command(L"select * from Products")
]
class CMyCommand {};
```

## <a name="requirements"></a>要求

### <a name="attribute-context"></a>特性上下文

|||
|-|-|
|**适用对象**|**类**、**结构**、成员、方法、本地|
|**可重复**|否|
|**必需的特性**|无|
|**无效的特性**|无|

有关特性上下文的详细信息，请参见 [特性上下文](cpp-attributes-com-net.md#contexts)。

## <a name="see-also"></a>另请参阅

[OLE DB 使用者特性](ole-db-consumer-attributes.md)
