---
title: db_command （c + + COM 特性）
ms.date: 07/10/2018
f1_keywords:
- vc-attr.db_command
helpviewer_keywords:
- db_command attribute
ms.assetid: 714c3e15-85d7-408b-9a7c-88505c3e5d24
ms.openlocfilehash: 87043315def59bcd7cff706710d988cc0ed37876
ms.sourcegitcommit: 6b749db14b4cf3a2b8d581fda6fdd8cb98bc3207
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/05/2020
ms.locfileid: "82825425"
---
# <a name="db_command"></a>db_command

创建 OLE DB 命令。

## <a name="syntax"></a>语法

```cpp
[ db_command(command, name, source_name, hresult, bindings, bulk_fetch)
]
```

### <a name="parameters"></a>参数

*command*<br/>
包含 OLE DB 命令文本的命令字符串。 一个简单的例子是：

```cpp
[ db_command ( command = "Select * from Products" ) ]
```

** 命令语法如下：

> 绑定参数块 1 \
> &nbsp;&nbsp;OLE DB 命令 \
> 绑定参数块 2 \
> &nbsp;&nbsp;OLE DB 命令的继续
> 绑定参数块 3 \
> ...

** 绑定参数块的定义如下：

> **（\[ ** *bindtype* **]** *szVar1* szVar1 \[， *szVar2* szVar2 \[， *nVar3* nVar3 \[，...]]]**)**

其中：

- **(** 标记数据绑定块的开始位置。

- **\[***bindtype* **]** 是以下不区分大小写的字符串之一：

  - ** \[db_column]** 将每个成员变量绑定到行集中的列。

  - ** \[bindto]**（与** \[db_column]** 相同。

  - ** \[in]** 将成员变量绑定为输入参数。

  - ** \[out]** 将成员变量绑定为输出参数。

  - in、out] ** \[** 将成员变量绑定为输入/输出参数。

- *szVarX*， *nVarX*解析为当前范围内的成员变量。

- **)** 标记数据绑定块的结束位置。

如果命令字符串包含一个或多个说明符（例如\[in]、 \[out] 或\[in/out]）， **db_command**会生成参数映射。

如果命令字符串包含一个或多个参数（如\[db_column] 或\[bindto]）， **db_command**会生成一个行集和一个访问器映射以服务这些绑定变量。 有关详细信息，请参阅 [db_accessor](db-accessor.md) 。

> [!NOTE]
> \[*bindtype*]在类级别使用**db_command**时，句法和*bindings*参数无效。

下面是一些绑定参数块的示例。 下面的示例分别将 `m_au_fname` 和 `m_au_lname` 数据成员绑定到 pubs 数据库中作者表的 `au_fname` 和 `au_lname` 列：

```cpp
TCHAR m_au_fname[21];
TCHAR m_au_lname[41];
TCHAR m_state[3] = 'CA';

[db_command (command = "SELECT au_fname([bindto]m_au_fname), au_lname([bindto]m_au_lname) " \
   "FROM dbo.authors " \
   "WHERE state = ?([in]m_state)")
]
```

*name*<br/>
可有可无用于处理行集的句柄名称。 如果指定名称 **， **db_command** 会生成具有指定名称 ** 的类，可以用它来遍历行集或执行多个操作查询。 如果未指定名称 **，则无法向用户返回多个行的结果。

*source_name*<br/>
可有可无对`CSession`其应用了`db_source`属性的类的变量或实例。 请参阅 [db_source](db-source.md)。

执行**db_command** 检查，确认用于 *source_name* 的变量有效，使指定的变量位于函数或全局范围内。

*hresult*<br/>
可有可无标识将接收此数据库命令的 HRESULT 的变量。 如果该变量不存在，属性将自动插入。

*绑定*<br/>
可有可无允许你将绑定参数与 OLE DB 命令分离。

如果为*绑定*指定一个值， **db_command**将分析关联的值，而不会分析\[ *bindtype*] 参数。 这种用法允许使用 OLE DB 提供程序语法。 若要禁用分析，但不绑定参数`Bindings=""`，请指定。

如果未指定*绑定*的值， **db_command**将分析绑定参数块，查找 "**（**"，后面跟**\[** 有一个或多个前面_声明的 c_**]** + + 成员变量，后跟一个或多个以前声明的 c + + 成员变量，后跟 "**）**"。 将从生成的命令中去除括号间的所有文本，并且这些参数将用于为此命令构造列和参数绑定。

*bulk_fetch*<br/>
可有可无一个整数值，该值指定要提取的行数。

默认值为 1，指定单行提取（行集将为 [CRowset](../../data/oledb/crowset-class.md)类型）。

大于 1 的值指定批量取行。 批量取行指提取多个行句柄的批量行集功能（行集将为 [CBulkRowset](../../data/oledb/cbulkrowset-class.md) 类型，并将采用指定的行数调用 `SetRows` ）。

如果 *bulk_fetch* 小于 1， `SetRows` 将返回零。

## <a name="remarks"></a>备注

**db_command** 创建 [CCommand](../../data/oledb/ccommand-class.md) 对象，OLE DB 使用者使用该对象来执行命令。

可以将 **db_command** 与类或函数范围一起使用，主要差异在于 `CCommand` 对象的范围。 使用函数范围，绑定等数据终止于函数末端。 类和函数范围用法都涉及到 OLE DB 使用者模板`CCommand<>`类，但对于函数和类事例，模板参数有所不同。 在函数情况下，将对包含局部变量`Accessor`的进行绑定，而类用法将推断派生的`CAccessor`类作为参数。 用作类属性时， **db_command** 和 **db_column**配合使用。

**db_command** 可用于执行不返回结果集的命令。

当使用者特性提供程序将此特性应用于类时，编译器会将类重\_命名为*YourClassName*访问器，其中*YourClassName*是您赋予类的名称，并且编译器还将创建一个名为*YourClassName*的类， \_该类派生自*YourClassName*访问器。  将在类视图中看到这两个类。

## <a name="example"></a>示例

本示例定义一个命令，该命令从状态列与“CA”匹配的表格中选择第一个和最后一个名称。 **db_command** 创建并读取行集，在行集上可以调用向导生成的函数（例如 [OpenAll 和 CloseAll](../../data/oledb/consumer-wizard-generated-methods.md)）和 `CRowset` 成员函数（例如 [MoveNext](../../data/oledb/crowset-movenext.md)）。

请注意，此代码要求提供自己连接到 pubs 数据库的连接字符串。 有关如何在开发环境中执行此操作的信息，请参阅[如何：连接到数据库和浏览现有对象](/sql/ssdt/how-to-connect-to-a-database-and-browse-existing-objects)和[添加新连接](/visualstudio/data-tools/add-new-connections)。

```cpp
// db_command.h
#include <atlbase.h>
#include <atlplus.h>
#include <atldbcli.h>

#pragma once

[  db_source(L"your connection string"), db_command(L" \
      SELECT au_lname, au_fname \
      FROM dbo.authors \
      WHERE state = 'CA'")  ]

struct CAuthors {
   // In order to fix several issues with some providers, the code below may bind
   // columns in a different order than reported by the provider

   DBSTATUS m_dwau_lnameStatus;
   DBSTATUS m_dwau_fnameStatus;
   DBLENGTH m_dwau_lnameLength;
   DBLENGTH m_dwau_fnameLength;

   [ db_column("au_lname", status="m_dwau_lnameStatus", length="m_dwau_lnameLength") ] TCHAR m_au_lname[41];
   [ db_column("au_fname", status="m_dwau_fnameStatus", length="m_dwau_fnameLength") ] TCHAR m_au_fname[21];

   [ db_param("7", paramtype="DBPARAMIO_INPUT") ] TCHAR m_state[3];

   void GetRowsetProperties(CDBPropSet* pPropSet) {
      pPropSet->AddProperty(DBPROP_CANFETCHBACKWARDS, true, DBPROPOPTIONS_OPTIONAL);
      pPropSet->AddProperty(DBPROP_CANSCROLLBACKWARDS, true, DBPROPOPTIONS_OPTIONAL);
   }
};
```

## <a name="example"></a>示例

```cpp
// db_command.cpp
// compile with: /c
#include "db_command.h"

int main(int argc, _TCHAR* argv[]) {
   HRESULT hr = CoInitialize(NULL);

   // Instantiate rowset
   CAuthors rs;

   // Open rowset and move to first row
   strcpy_s(rs.m_state, sizeof(rs.m_state), _T("CA"));
   hr = rs.OpenAll();
   hr = rs.MoveFirst();

   // Iterate through the rowset
   while( SUCCEEDED(hr) && hr != DB_S_ENDOFROWSET ) {
      // Print out the column information for each row
      printf("First Name: %s, Last Name: %s\n", rs.m_au_fname, rs.m_au_lname);
      hr = rs.MoveNext();
   }

   rs.CloseAll();
   CoUninitialize();
}
```

## <a name="example"></a>示例

此示例使用数据源类 `db_source` 上的 `CMySource`以及命令类 `db_command` 和 `CCommand1` 上的 `CCommand2`。

```cpp
// db_command_2.cpp
// compile with: /c
#include <atlbase.h>
#include <atlplus.h>
#include <atldbcli.h>
// class usage for both db_source and db_command

[  db_source(L"your connection string"), db_command(L" \
      SELECT au_lname, au_fname \
      FROM dbo.authors \
      WHERE state = 'CA'")  ]
struct CMySource {
   HRESULT OpenDataSource() {
      return S_OK;
   }
};

[db_command(command = "SELECT * FROM Products")]
class CCommand1 {};

[db_command(command = "SELECT FNAME, LNAME FROM Customers")]
class CCommand2 {};

int main() {
   CMySource s;
   HRESULT hr = s.OpenDataSource();
   if (SUCCEEDED(hr)) {
      CCommand1 c1;
      hr = c1.Open(s);

      CCommand2 c2;
      hr = c2.Open(s);
   }

   s.CloseDataSource();
}
```

## <a name="requirements"></a>要求

### <a name="attribute-context"></a>特性上下文

|||
|-|-|
|**适用于**|**类**、**结构**、成员、方法、本地|
|**且**|否|
|**必需属性**|无|
|**无效的特性**|无|

有关特性上下文的详细信息，请参见 [特性上下文](cpp-attributes-com-net.md#contexts)。

## <a name="see-also"></a>另请参阅

[OLE DB 使用者属性](ole-db-consumer-attributes.md)<br/>
[独立特性](stand-alone-attributes.md)
