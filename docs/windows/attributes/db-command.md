---
title: db_command （c + + COM 属性） |Microsoft Docs
ms.custom: ''
ms.date: 07/10/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.db_command
dev_langs:
- C++
helpviewer_keywords:
- db_command attribute
ms.assetid: 714c3e15-85d7-408b-9a7c-88505c3e5d24
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 0111dfc424a99d413a217149b3c5e579a3999f13
ms.sourcegitcommit: 955ef0f9d966e7c9c65e040f1e28fa83abe102a5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/04/2018
ms.locfileid: "48790399"
---
# <a name="dbcommand"></a>db_command

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

 命令语法如下：

> 绑定参数块 1 &nbsp; &nbsp;OLE DB 命令绑定参数块 2 &nbsp;&nbsp;的 OLE DB 命令绑定参数块 3 延续...

 绑定参数块的定义如下：

> **(\[**  *bindtype* **]** *szVar1* \[， *szVar2* \[， *nVar3* \[，...]]]**)**

其中：

- **(** 标记数据绑定块的开始位置。

- **\[** *bindtype* **]** 是以下不区分大小写的字符串之一：

  - **\[db_column]** 将每个成员变量绑定到行集中的列。

  - **\[bindto]** (与相同 **\[db_column]**)。

  - **\[在]** 将作为输入参数的成员变量绑定。

  - **\[out] 一个**将作为输出参数的成员变量绑定。

  - **\[in，out]** 成员将变量绑定为输入/输出参数。

- *szVarX*， *nVarX*解析为当前作用域内的成员变量。

- **)** 标记数据绑定块的结束位置。

如果命令字符串包含一个或多个说明符，如\[在]， \[out]，或\[in/out]， **db_command**生成参数映射。

如果命令字符串包含一个或多个参数，如\[db_column] 或\[bindto]， **db_command**生成行集和取值函数映射以服务这些绑定的变量。 请参阅[db_accessor](db-accessor.md)有关详细信息。

> [!NOTE]
> \[*bindtype*] 语法和*绑定*使用时，可能不是有效参数**db_command**在类级别。

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
（可选）用于处理行集的句柄的名称。 如果指定名称 ， **db_command** 会生成具有指定名称 的类，可以用它来遍历行集或执行多个操作查询。 如果未指定名称 ，则无法向用户返回多个行的结果。

*source_name*<br/>
（可选）`CSession`变量或具有的类的实例`db_source`特性应用于它执行命令。 请参阅[db_source](db-source.md)。

执行**db_command** 检查，确认用于 *source_name* 的变量有效，使指定的变量位于函数或全局范围内。

*hresult*<br/>
（可选）标识将接收此数据库命令的 HRESULT 的变量。 如果该变量不存在，属性将自动插入。

*绑定*<br/>
（可选）可以从 OLE DB 命令分离绑定参数。

如果指定的值*绑定*， **db_command**将分析相关联的值，但不会分析\[ *bindtype*] 参数。 这种用法允许使用 OLE DB 提供程序语法。 若要禁用分析，但不绑定参数，请指定`Bindings=""`。

如果未指定的值*绑定*， **db_command**将分析绑定参数块，查找 **(** 后, 跟 **\[** _bindtype_**]** 在方括号内后, 跟一个或多个以前声明 c + + 成员变量后, 接 **)**。 将从生成的命令中去除括号间的所有文本，并且这些参数将用于为此命令构造列和参数绑定。

*bulk_fetch*<br/>
（可选）一个整数值，指定要提取的行数。

默认值为 1，指定单行提取 (行集将为类型[CRowset](../../data/oledb/crowset-class.md))。

大于 1 的值指定批量取行。 批量取行指提取多个行句柄的大容量行集的能力 (行集将为类型[CBulkRowset](../../data/oledb/cbulkrowset-class.md) ，并将调用`SetRows`与指定的行数)。

如果 *bulk_fetch* 小于 1， `SetRows` 将返回零。

## <a name="remarks"></a>备注

**db_command**创建[CCommand](../../data/oledb/ccommand-class.md)对象，OLE DB 使用者用于执行命令。

可以将 **db_command** 与类或函数范围一起使用，主要差异在于 `CCommand` 对象的范围。 使用函数范围，绑定等数据终止于函数末端。 类和函数范围的用法涉及到 OLE DB 使用者模板类`CCommand<>`，但函数和类的情况下，模板参数不同。 在函数事例中，将对进行绑定`Accessor`包含本地变量，而类用法将推断`CAccessor`-派生的类作为参数。 用作类属性时， **db_command** 和 **db_column**配合使用。

**db_command** 可用于执行不返回结果集的命令。

编译器时使用者特性提供程序适用于类，此属性，将重命名为类\_ *YourClassName*访问器，其中*名为 YourClassName*是您为指定的名称类和编译器还将创建一个名为类*名为 YourClassName*，它派生\_*名为 YourClassName*访问器。  将在类视图中看到这两个类。

## <a name="example"></a>示例

本示例定义一个命令，该命令从状态列与“CA”匹配的表格中选择第一个和最后一个名称。 **db_command**创建并读取行集可以调用向导生成的函数如[OpenAll 和 CloseAll](../../data/oledb/consumer-wizard-generated-methods.md)，以及`CRowset`之类的函数成员[MoveNext](../../data/oledb/crowset-movenext.md)。

请注意，此代码要求提供自己连接到 pubs 数据库的连接字符串。 有关如何执行此操作在开发环境中的信息，请参阅[如何： 连接到数据库并浏览现有对象](/sql/ssdt/how-to-connect-to-a-database-and-browse-existing-objects)并[添加新连接](/visualstudio/data-tools/add-new-connections)。

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
|**适用对象**|**类**，**结构**，成员、 方法、 本地|
|**可重复**|否|
|**必需的特性**|无|
|**无效的特性**|无|

有关特性上下文的详细信息，请参阅[特性上下文](cpp-attributes-com-net.md#contexts)。

## <a name="see-also"></a>请参阅

[OLE DB 使用者特性](ole-db-consumer-attributes.md)<br/>
[独立特性](stand-alone-attributes.md)  
