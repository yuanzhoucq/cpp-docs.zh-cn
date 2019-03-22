---
title: 用架构行集合获取元数据
ms.date: 10/24/2018
helpviewer_keywords:
- schema rowsets, getting OLE DB provider metadata
- OLE DB consumer templates, getting provider metadata
- metadata, getting (OLE DB Templates)
ms.assetid: 6b448461-82fb-4acf-816b-3cbb0ca1d186
ms.openlocfilehash: 9e61507a187f7625e7e90e2a0e3a1ce404573e29
ms.sourcegitcommit: c1f646c8b72f330fa8cf5ddb0f8f261ba10d16f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/21/2019
ms.locfileid: "58328865"
---
# <a name="obtaining-metadata-with-schema-rowsets"></a>用架构行集合获取元数据

有时需要不必打开行集合即可获得有关提供程序、行集合、表、列或其他数据库信息的信息。 有关数据库结构的数据被称为元数据，可以通过多种不同的方法来检索元数据。 一种方法是使用架构行集合。

OLE DB 模板提供一组类，以检索架构信息;这些类创建预定义的架构行集和中列出[架构行集类和 Typedef 类](../../data/oledb/schema-rowset-classes-and-typedef-classes.md)。

> [!NOTE]
> 如果正在使用 OLAP，而架构行集类不支持某些行集合（例如，具有可变的列数），则应考虑使用 `CManualAccessor` 或 `CDynamicAccessor`。 可以滚动浏览这些列，并使用 case 语句来处理每个列可能的数据类型。

## <a name="catalogschema-model"></a>目录/架构模型

ANSI SQL 定义数据存储区的目录/架构模型；OLE DB 使用此模型。 在此模型中，目录 （数据库） 具有架构和架构必须具有表。

- **目录**目录是数据库的另一个名称。 它是相关架构的集合。 若要列出属于给定的数据源的目录 （数据库），请使用[CCatalog](../../data/oledb/ccatalogs-ccataloginfo.md)。 由于很多数据库只有一个目录，元数据有时称为架构信息。

- **架构**架构是拥有或由特定用户创建的数据库对象的集合。 若要列出给定用户拥有的架构，请使用[CSchemata](../../data/oledb/cschemata-cschematainfo.md)。

   在 Microsoft SQL Server 和 ODBC 2.x 术语中，架构是所有者 （例如，dbo 是典型的架构名称）。 此外，SQL Server 将元数据存储中的一组表： 一个表包含的所有表的列表，另一个表包含的所有列的列表。 到 Microsoft Access 数据库中的架构没有等效项。

- **表**表是以特定顺序排列的列的集合。 若要列出给定的目录 （数据库） 和有关这些表的信息中定义的表，请使用[CTables](../../data/oledb/ctables-ctableinfo.md))。

## <a name="restrictions"></a>限制

当查询架构信息时，可以使用限制来指定感兴趣的信息类型。 可以将限制视为筛选器或查询中的限定符。 例如，在查询中：

```sql
SELECT * FROM authors WHERE l_name = 'pivo'
```

`l_name` 是一个限制。 这是仅有一个限制; 使用一个简单示例架构行集类支持多个限制。

[架构行集 typedef 类](../../data/oledb/schema-rowset-classes-and-typedef-classes.md)封装所有的 OLE DB 架构行集，从而使您可以通过实例化并打开它访问架构行集就像任何其他行集一样。 例如，typedef 类[CColumns](../../data/oledb/ccolumns-ccolumnsinfo.md)定义为：

```cpp
CRestrictions<CAccessor<CColumnsInfo>
```

[CRestrictions](../../data/oledb/crestrictions-class.md)类提供了限制支持。 创建架构行集的实例后，调用[crestrictions:: Open](../../data/oledb/crestrictions-open.md)。 此方法返回基于所指定限制的结果集。

若要指定限制，请参阅[附录 b:架构行集](/previous-versions/windows/desktop/ms712921(v=vs.85))并查找要使用的行集。 例如，`CColumns`对应于[COLUMNS 行集](/previous-versions/windows/desktop/ms723052(v=vs.85)); 该主题列出了 COLUMNS 行集中的限制列：TABLE_CATALOG、 TABLE_SCHEMA、 TABLE_NAME、 COLUMN_NAME。 必须遵循此顺序来指定你的限制。

因此，例如，如果你想要限制的表名，TABLE_NAME 是第三个限制列，，然后调用`Open`，所需的表名指定为第三个限制参数，如以下示例所示。

### <a name="to-use-schema-rowsets"></a>若要使用架构行集合

1. 包括标头文件`Atldbsch.h`(需要`Atldbcli.h`的使用者的支持)。

1. 实例化使用者的或文档的头文件中的架构行集合对象。 如果您需要表信息，请将声明`CTables`对象; 如果您需要列信息，请将声明`CColumns`对象。 此示例演示如何检索作者表中的列：

    ```cpp
    CDataSource ds;
    ds.Open();
    CSession ss;
    ss.Open(ds);
    CColumns columnSchemaRowset;
    // TABLE_NAME is the third restriction column, so
    // specify "authors" as the third restriction parameter:
    HRESULT hr = columnSchemaRowset.Open(ss, NULL, NULL, L"authors");
    hr = columnSchemaRowset.MoveFirst();
    while (hr == S_OK)
    {
       hr = columnSchemaRowset.MoveNext();
    }
    ```

1. 若要提取信息，请访问架构行集合对象的相应数据成员，例如 `ColumnSchemaRowset.m_szColumnName`。 此数据成员对应 COLUMN_NAME。 若要查看每个数据成员对应的 OLE DB 列，请参阅[CColumns](../../data/oledb/ccolumns-ccolumnsinfo.md)。

有关架构行集的引用，typedef 类中提供的 OLE DB 模板 (请参阅[架构行集类和 Typedef 类](../../data/oledb/schema-rowset-classes-and-typedef-classes.md))。

有关 OLE DB 架构行集，包括限制列的详细信息请参阅[附录 b:架构行集](/previous-versions/windows/desktop/ms712921(v=vs.85))中**OLE DB 程序员参考**。

有关如何使用架构行集类的更复杂的示例，请参阅[CatDB](https://github.com/Microsoft/VCSamples)并[DBViewer](https://github.com/Microsoft/VCSamples)示例。

有关架构行集的提供程序支持的信息，请参阅[支持架构行集](../../data/oledb/supporting-schema-rowsets.md)。

## <a name="see-also"></a>请参阅

[使用访问器](../../data/oledb/using-accessors.md)