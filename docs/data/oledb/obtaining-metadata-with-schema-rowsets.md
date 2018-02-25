---
title: "用架构行集合获取元数据 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- schema rowsets, getting OLE DB provider metadata
- OLE DB consumer templates, getting provider metadata
- metadata, getting (OLE DB Templates)
ms.assetid: 6b448461-82fb-4acf-816b-3cbb0ca1d186
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 1509bb4bd083331c36c3b699b4716945e4573d1d
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/23/2018
---
# <a name="obtaining-metadata-with-schema-rowsets"></a>用架构行集合获取元数据
有时需要不必打开行集合即可获得有关提供程序、行集合、表、列或其他数据库信息的信息。 有关数据库结构的数据被称为元数据，可以通过多种不同的方法来检索元数据。 一种方法是使用架构行集合。  
  
 OLE DB 模板提供一组类，以检索架构信息;这些类创建预定义的架构行集，并且列在[架构行集类和 Typedef 类](../../data/oledb/schema-rowset-classes-and-typedef-classes.md)。  
  
> [!NOTE]
>  如果正在使用 OLAP，而架构行集类不支持某些行集合（例如，具有可变的列数），则应考虑使用 `CManualAccessor` 或 `CDynamicAccessor`。 可以滚动浏览这些列，并使用 case 语句来处理每个列可能的数据类型。  
  
## <a name="catalogschema-model"></a>目录/架构模型  
 ANSI SQL 定义数据存储区的目录/架构模型；OLE DB 使用此模型。 在此模型中，目录（数据库）包含架构而架构包含表。  
  
-   **目录**目录是数据库的另一个名称。 它是相关架构的集合。 若要列出属于给定的数据源的目录 （数据库），使用[CCatalog](../../data/oledb/ccatalogs-ccataloginfo.md)。 由于很多数据库只有一个目录，元数据有时简称为架构信息。  
  
-   **架构**架构是由特定用户已创建或拥有的数据库对象的集合。 若要列出给定用户所拥有的架构，请使用[CSchemata](../../data/oledb/cschemata-cschematainfo.md)。  
  
     在 Microsoft SQL Server 和 ODBC 2.x 术语中，架构是所有者 （例如，dbo 是典型的架构名称）。 此外，SQL Server 将元数据存储在一组表： 一个表包含所有表的列表，另一个表包含的所有列的列表。 Microsoft Access 数据库中的架构没有等效项。  
  
-   **表**表是以特定顺序排列的列的集合。 若要列出给定的目录 （数据库） 和有关这些表的信息中定义的表，请使用[CTables](../../data/oledb/ctables-ctableinfo.md))。  
  
## <a name="restrictions"></a>限制  
 查询架构信息时，可以使用限制来指定感兴趣的信息类型。 可以将限制视为筛选器或查询中的限定符。 例如，在查询中：  
  
```  
SELECT * FROM authors where l_name = 'pivo'  
```  
  
 `l_name` 是一个限制。 这是一个非常简单的示例，它只使用了一个限制；而架构行集类支持多个限制。  
  
 [架构行集 typedef 类](../../data/oledb/schema-rowset-classes-and-typedef-classes.md)封装所有的 OLE DB 架构行集，从而使你可以通过实例化并打开它来访问架构行集就像任何其他行集合一样。 例如，typedef 类[CColumns](../../data/oledb/ccolumns-ccolumnsinfo.md)定义为：  
  
```  
CRestrictions<CAccessor<CColumnsInfo>  
```  
  
 [CRestrictions](../../data/oledb/crestrictions-class.md)类提供了限制支持。 创建架构行集的实例后，调用[crestrictions:: Open](../../data/oledb/crestrictions-open.md)。 此方法返回基于所指定限制的结果集。  
  
 若要指定限制，请参阅[附录 b： 架构行集](http://go.microsoft.com/fwlink/p/?linkid=64681)并查找你使用的行集。 例如， **CColumns**对应于[列行集](http://go.microsoft.com/fwlink/p/?linkid=64682); 该主题列出了 COLUMNS 行集合中的限制列： TABLE_CATALOG、 TABLE_SCHEMA、 TABLE_NAME、 COLUMN_NAME。 必须遵循此顺序来指定你的限制。  
  
 因此，例如，如果你想要限制的表名，注意 TABLE_NAME 是第三个限制列，，然后调用**打开**，所需的表名指定为第三个限制参数，如以下示例所示。  
  
#### <a name="to-use-schema-rowsets"></a>若要使用架构行集合  
  
1.  必须包括头文件 Atldbsch.h（当然，Atldbcli.h 还将用于使用者支持）。  
  
2.  实例化使用者的或文档的头文件中的架构行集合对象。 如果你希望表信息，请将声明**CTables**对象; 如果你希望列信息，请将声明**CColumns**对象。 此示例演示如何检索作者表中的列：  
  
    ```  
    CDataSource ds;  
    ds.Open();  
    CSession ss;  
    ss.Open();  
    CColumns ColumnSchemaRowset;  
    // TABLE_NAME is the third restriction column, so  
    // specify "authors" as the third restriction parameter:  
    hr = ColumnSchemaRowset.Open(ss, NULL, NULL, "authors");  
    hr = ColumnSchemaRowset.MoveFirst();  
    while (hr == S_OK)  
    {  
       hr = ColumnSchemaRowset.MoveNext();  
    }  
    ```  
  
3.  若要获取信息，请访问架构行集合对象的相应数据成员，例如 `ColumnSchemaRowset.m_szColumnName`。 它对应 COLUMN_NAME。 若要查看每个数据成员对应的 OLE DB 列，请参阅[CColumns](../../data/oledb/ccolumns-ccolumnsinfo.md)。  
  
 有关架构行集的引用，typedef 类中提供的 OLE DB 模板 (请参阅[架构行集类和 Typedef 类](../../data/oledb/schema-rowset-classes-and-typedef-classes.md))。  
  
 有关 OLE DB 架构行集合，包括限制列的详细信息请参阅[附录 b： 架构行集](http://go.microsoft.com/fwlink/p/?linkid=64681)OLE DB 程序员参考中。  
  
 有关如何使用架构行集类的更复杂的示例，请参阅[CatDB](http://msdn.microsoft.com/en-us/003d516b-2bf6-444e-8be5-4ebaa0b66046)和[DBViewer](http://msdn.microsoft.com/en-us/07620f99-c347-4d09-9ebc-2459e8049832)示例。  
  
 有关架构行集提供程序支持的信息，请参阅[支持架构行集](../../data/oledb/supporting-schema-rowsets.md)。  
  
## <a name="see-also"></a>请参阅  
 [使用访问器](../../data/oledb/using-accessors.md)