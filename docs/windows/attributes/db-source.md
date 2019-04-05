---
title: db_source （c + + COM 属性）
ms.date: 10/02/2018
f1_keywords:
- vc-attr.db_source
helpviewer_keywords:
- db_source attribute
ms.assetid: 0ec8bbf7-ade2-4899-bf4c-8608b92779bc
ms.openlocfilehash: 884cab78d64c20bef00958f0cc0319281fd69921
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/05/2019
ms.locfileid: "59026326"
---
# <a name="dbsource"></a>db_source

创建与数据源的连接。

## <a name="syntax"></a>语法

```cpp
[ db_source(db_source, name, hresult) ]
```

### <a name="parameters"></a>参数

*db_source*<br/>
用于连接到数据源的连接字符串。 有关连接字符串的格式，请参阅[连接字符串和数据链接](/previous-versions/windows/desktop/ms718376(v=vs.85))在 Microsoft 数据访问组件 (MDAC) SDK。

*name*<br/>
（可选）当你使用**db_source**的类上*名称*是具有的数据源对象的实例**db_source**特性应用于它 （请参阅示例 1）。 当你使用**db_source**中的方法实现，以内联方式*名称*是一个变量 （本地到方法），可用于访问数据源 （请参见示例 2）。 将此传递*名称*到*source_name*参数的`db_command`若要将数据源与命令相关联。

*hresult*<br/>
（可选）标识将接收此数据库命令的 HRESULT 的变量。 如果该变量不存在，属性将自动插入。

## <a name="remarks"></a>备注

**db_source**创建[CDataSource](../../data/oledb/cdatasource-class.md)和一个[CSession](../../data/oledb/csession-class.md)对象，一起表示与 OLE DB 使用者数据源的连接。

当你使用**db_source**的类上`CSession`对象将成为类的成员。

当你使用**db_source**在方法范围内，将在方法中，执行插入的代码和`CSession`对象创建为本地变量。

**db_source**将数据源属性添加到类或方法中。 结合使用`db_command`(此方法采用*db_source* *名称*参数作为其*source_name*参数)。

编译器时使用者特性提供程序适用于类，此属性，将重命名为类\_ *YourClassName*访问器，其中*名为 YourClassName*是您为指定的名称类和编译器还将创建一个名为类*名为 YourClassName*，它派生\_*名为 YourClassName*访问器。  将在类视图中看到这两个类。

有关在应用程序中使用此属性的一个示例，请参阅示例[AtlAgent](https://github.com/Microsoft/VCSamples)并[MultiRead](https://github.com/Microsoft/VCSamples)。

## <a name="example"></a>示例

此示例会调用**db_source**类创建与数据源的连接上`ds`使用 Northwind 数据库。 `ds` 数据源，可以在内部为使用的句柄`CMyCommand`类。

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
|**适用对象**|**类**，**结构**，成员、 方法、 本地|
|**可重复**|否|
|**必需的特性**|None|
|**无效的特性**|None|

有关特性上下文的详细信息，请参见 [特性上下文](cpp-attributes-com-net.md#contexts)。

## <a name="see-also"></a>请参阅

[OLE DB 使用者特性](ole-db-consumer-attributes.md)
