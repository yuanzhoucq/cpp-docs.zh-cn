---
title: db_table （c + + COM 属性） |Microsoft Docs
ms.custom: ''
ms.date: 10/02/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.db_table
dev_langs:
- C++
helpviewer_keywords:
- db_table attribute
ms.assetid: ff9eb957-4e6d-4175-afcc-fd8ea916cec0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 07910693b3236e3a90d7ad420392552d90abd747
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/25/2018
ms.locfileid: "50052143"
---
# <a name="dbtable"></a>db_table

将打开一个 OLE DB 表。

## <a name="syntax"></a>语法

```cpp
[ db_table(db_table, name, source_name, hresult) ]
```

#### <a name="parameters"></a>参数

*db_table*<br/>
指定 （例如"产品"） 的数据库表的名称的字符串。

*name*<br/>
（可选）句柄用于处理表的名称。 如果你想要返回多个行的结果，必须指定此参数。 **db_table**生成具有指定的变量*名称*可用来遍历行集或执行多个操作查询。

*source_name*<br/>
（可选）`CSession`变量或具有的类的实例`db_source`特性应用于它执行命令。 请参阅 [db_source](db-source.md)。

*hresult*<br/>
（可选）标识将接收此数据库命令的 HRESULT 的变量。 如果该变量不存在，属性将自动插入。

## <a name="remarks"></a>备注

**db_table**创建[CTable](../../data/oledb/ctable-class.md)对象，OLE DB 使用者用于打开表。 只能在类级别，则使用此属性它不能使用内联。 使用`db_column`若要将表中的列绑定到变量; 使用`db_param`来分隔 （该参数的类型，因此在上设置） 的参数。

编译器时使用者特性提供程序适用于类，此属性，将重命名为类\_ *YourClassName*访问器，其中*名为 YourClassName*是您为指定的名称类和编译器还将创建一个名为类*名为 YourClassName*，它派生\_*名为 YourClassName*访问器。  将在类视图中看到这两个类。

## <a name="example"></a>示例

下面的示例打开 Products 表以供`CProducts`。

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

有关在应用程序中使用此属性的一个示例，请参阅示例[AtlAgent](https://github.com/Microsoft/VCSamples)并[MultiRead](https://github.com/Microsoft/VCSamples)。

## <a name="requirements"></a>要求

### <a name="attribute-context"></a>特性上下文

|||
|-|-|
|**适用对象**|**类**，**结构**|
|**可重复**|否|
|**必需的特性**|无|
|**无效的特性**|无|

有关特性上下文的详细信息，请参见 [特性上下文](cpp-attributes-com-net.md#contexts)。

## <a name="see-also"></a>请参阅

[OLE DB 使用者特性](ole-db-consumer-attributes.md)
