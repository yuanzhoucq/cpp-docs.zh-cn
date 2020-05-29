---
title: 用架构行集合获取元数据
ms.date: 10/24/2018
helpviewer_keywords:
- schema rowsets, getting OLE DB provider metadata
- OLE DB consumer templates, getting provider metadata
- metadata, getting (OLE DB Templates)
ms.assetid: 6b448461-82fb-4acf-816b-3cbb0ca1d186
ms.openlocfilehash: e04b9a335c60cefdc28be2347ef1f0762c424d8e
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80210127"
---
# <a name="obtaining-metadata-with-schema-rowsets"></a>用架构行集合获取元数据

有时需要不必打开行集合即可获得有关提供程序、行集合、表、列或其他数据库信息的信息。 有关数据库结构的数据被称为元数据，可以通过多种不同的方法来检索元数据。 一种方法是使用架构行集合。

OLE DB 模板提供一组用于检索架构信息的类;这些类创建预定义的架构行集，并列在[架构行集类和 Typedef 类](../../data/oledb/schema-rowset-classes-and-typedef-classes.md)中。

> [!NOTE]
> 如果正在使用 OLAP，而架构行集类不支持某些行集合（例如，具有可变的列数），则应考虑使用 `CManualAccessor` 或 `CDynamicAccessor`。 可以滚动浏览这些列，并使用 case 语句来处理每个列可能的数据类型。

## <a name="catalogschema-model"></a>目录/架构模型

ANSI SQL 定义数据存储区的目录/架构模型；OLE DB 使用此模型。 在此模型中，目录（数据库）的架构和架构都具有表。

- **目录**目录是数据库的另一个名称。 它是相关架构的集合。 若要列出属于给定数据源的目录（数据库），请使用[CCatalog](../../data/oledb/ccatalogs-ccataloginfo.md)。 由于许多数据库只有一个目录，因此元数据有时称为架构信息。

- **架构**架构是由特定用户拥有或创建的数据库对象的集合。 若要列出给定用户拥有的架构，请使用[CSchemata](../../data/oledb/cschemata-cschematainfo.md)。

   在 Microsoft SQL Server 和 ODBC 2.x 术语中，架构是所有者（例如，dbo 是典型的架构名称）。 此外，SQL Server 会将元数据存储在一组表中：一个表包含所有表的列表，另一个表包含所有列的列表。 没有等效于 Microsoft Access 数据库中的架构。

- **表**表是按特定顺序排列的列的集合。 若要列出在给定目录（数据库）中定义的表以及这些表的相关信息，请使用[CTables](../../data/oledb/ctables-ctableinfo.md)）。

## <a name="restrictions"></a>限制

查询架构信息时，您可以使用限制来指定您感兴趣的信息的类型。 可以将限制视为筛选器或查询中的限定符。 例如，在查询中：

```sql
SELECT * FROM authors WHERE l_name = 'pivo'
```

`l_name` 是一个限制。 这是一个只包含一个限制的简单示例;架构行集类支持多种限制。

[架构行集 typedef 类](../../data/oledb/schema-rowset-classes-and-typedef-classes.md)封装所有 OLE DB 架构行集，以便可以通过实例化并打开架构行集，就像访问任何其他行集一样。 例如，typedef 类[CColumns](../../data/oledb/ccolumns-ccolumnsinfo.md)定义为：

```cpp
CRestrictions<CAccessor<CColumnsInfo>
```

[CRestrictions](../../data/oledb/crestrictions-class.md)类提供限制支持。 创建架构行集的实例后，调用[CRestrictions：： Open](../../data/oledb/crestrictions-open.md)。 此方法返回基于所指定限制的结果集。

若要指定限制，请参阅[附录 B：架构行集](/previous-versions/windows/desktop/ms712921(v=vs.85))，并查找正在使用的行集。 例如，`CColumns` 对应于[列行集](/previous-versions/windows/desktop/ms723052(v=vs.85));该主题列出了列行集中的限制列： TABLE_CATALOG、TABLE_SCHEMA、TABLE_NAME COLUMN_NAME。 必须遵循此顺序来指定你的限制。

例如，如果想要按表名进行限制，TABLE_NAME 是第三个限制列，然后调用 `Open`，并将所需的表名称指定为第三个限制参数，如以下示例中所示。

### <a name="to-use-schema-rowsets"></a>若要使用架构行集合

1. `Atldbsch.h` 中包含头文件（还需要 `Atldbcli.h` 使用者支持）。

1. 实例化使用者的或文档的头文件中的架构行集合对象。 如果需要表信息，请声明一个 `CTables` 对象;如果需要列信息，请声明一个 `CColumns` 对象。 此示例演示如何检索作者表中的列：

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

1. 若要提取信息，请访问架构行集合对象的相应数据成员，例如 `ColumnSchemaRowset.m_szColumnName`。 此数据成员对应于 COLUMN_NAME。 若要查看每个数据成员所对应 OLE DB 列，请参阅[CColumns](../../data/oledb/ccolumns-ccolumnsinfo.md)。

对于架构行集的引用，OLE DB 模板中提供的 typedef 类（请参阅[架构行集类和 Typedef 类](../../data/oledb/schema-rowset-classes-and-typedef-classes.md)）。

有关 OLE DB 架构行集（包括限制列）的详细信息，请参阅**OLE DB 程序员参考**中的[附录 B：架构行集](/previous-versions/windows/desktop/ms712921(v=vs.85))。

有关如何使用架构行集类的更复杂示例，请参阅[CatDB](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/OLEDB/Consumer)和[DBViewer](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/OLEDB/Consumer)示例。

有关架构行集的提供程序支持的信息，请参阅[支持架构行集](../../data/oledb/supporting-schema-rowsets.md)。

## <a name="see-also"></a>另请参阅

[使用访问器](../../data/oledb/using-accessors.md)
