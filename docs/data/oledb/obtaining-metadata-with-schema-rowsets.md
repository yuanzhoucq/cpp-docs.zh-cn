---
title: "用架构行集合获取元数据 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "元数据, 获取（OLE DB 模板）"
  - "OLE DB 使用者模板, 获取提供程序元数据"
  - "架构行集合, 获取 OLE DB 提供程序元数据"
ms.assetid: 6b448461-82fb-4acf-816b-3cbb0ca1d186
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 用架构行集合获取元数据
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

有时需要不必打开行集合即可获得有关提供程序、行集合、表、列或其他数据库信息的信息。  有关数据库结构的数据被称为元数据，可以通过多种不同的方法来检索元数据。  一种方法是使用架构行集合。  
  
 OLE DB 模板提供一组类，以检索架构信息；这些类创建预定义的架构行集合，并且列在[架构行集类和 Typedef 类](../../data/oledb/schema-rowset-classes-and-typedef-classes.md)中。  
  
> [!NOTE]
>  如果正在使用 OLAP，而架构行集类不支持某些行集合（例如，具有可变的列数），则应考虑使用 `CManualAccessor` 或 `CDynamicAccessor`。  可以滚动浏览这些列，并使用 case 语句来处理每个列可能的数据类型。  
  
## 目录\/架构模型  
 ANSI SQL 定义数据存储区的目录\/架构模型；OLE DB 使用此模型。  在此模型中，目录（数据库）包含架构而架构包含表。  
  
-   **目录** 目录是数据库的另一个名称。  它是相关架构的集合。  若要列出属于给定数据源的目录（数据库），请使用 [CCatalog](../../data/oledb/ccatalogs-ccataloginfo.md)。  由于很多数据库只有一个目录，元数据有时简称为架构信息。  
  
-   **架构** 架构是特定用户拥有或创建的数据库对象的集合。  若要列出给定用户拥有的架构，请使用 [CSchemata](../../data/oledb/cschemata-cschematainfo.md)。  
  
     在 Microsoft SQL Server 和 ODBC 2.x 术语中，架构是所有者（例如，dbo 是典型的架构名称）。  此外，SQL Server 将元数据存储在一组表中：一个表包含所有表的列表，另一个表中包含所有列的列表。  Microsoft Access 数据库中的架构没有等效项。  
  
-   **表** 表是以特定顺序排列的列的集合。  若要列出给定目录（数据库）中定义的表以及有关这些表的信息，请使用 [CTables](../../data/oledb/ctables-ctableinfo.md)。  
  
## 限制  
 查询架构信息时，可以使用限制来指定感兴趣的信息类型。  可以将限制视为筛选器或查询中的限定符。  例如，在查询中：  
  
```  
SELECT * FROM authors where l_name = 'pivo'  
```  
  
 `l_name` 是一个限制。  这是一个非常简单的示例，它只使用了一个限制；而架构行集类支持多个限制。  
  
 [架构行集 typedef 类](../../data/oledb/schema-rowset-classes-and-typedef-classes.md)封装所有的 OLE DB 架构行集合，以便可以通过实例化并打开它来像任何其他行集合一样访问架构行集合。  例如，typedef 类 [CColumns](../../data/oledb/ccolumns-ccolumnsinfo.md) 的定义为：  
  
```  
CRestrictions<CAccessor<CColumnsInfo>  
```  
  
 [CRestrictions](../../data/oledb/crestrictions-class.md) 类提供了限制支持。  创建架构行集合的实例后，调用 [CRestrictions::Open](../../data/oledb/crestrictions-open.md)。  此方法返回基于所指定限制的结果集。  
  
 若要指定限制，请参阅[附录 B：架构行集合](http://go.microsoft.com/fwlink/?LinkId=64681) 并查找你正在使用的行集合。  例如，**CColumns** 对应 [COLUMNS 行集合](http://go.microsoft.com/fwlink/?LinkId=64682)；该主题列出了 COLUMNS 行集合中的限制列：TABLE\_CATALOG、TABLE\_SCHEMA、TABLE\_NAME、COLUMN\_NAME。  必须遵循此顺序来指定你的限制。  
  
 因此，例如，如果你想要按表名进行限制，注意 TABLE\_NAME 是第三个限制列，然后调用**打开**，将所需的表名指定为第三个限制参数，如下例所示。  
  
#### 若要使用架构行集合  
  
1.  必须包括头文件 Atldbsch.h（当然，Atldbcli.h 还将用于使用者支持）。  
  
2.  实例化使用者的或文档的头文件中的架构行集合对象。  如果需要表信息，则声明 **CTables** 对象；如果需要列信息，则声明 **CColumns** 对象。  此示例演示如何检索作者表中的列：  
  
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
  
3.  若要获取信息，请访问架构行集合对象的相应数据成员，例如 `ColumnSchemaRowset.m_szColumnName`。  它对应 COLUMN\_NAME。  若要查看每个数据成员对应的 OLE DB 列，请参阅 [CColumns](../../data/oledb/ccolumns-ccolumnsinfo.md)。  
  
 有关架构行集合的引用，OLE DB 模板中提供的 typedef 类（请参阅[架构行集类和 Typedef 类](../../data/oledb/schema-rowset-classes-and-typedef-classes.md)）。  
  
 有关 OLE DB 架构行集合，包括限制列的详细信息，请参阅 OLE DB 程序员参考中的[附录 B：架构行集合](http://go.microsoft.com/fwlink/?LinkId=64681)。  
  
 有关如何使用架构行集类的更复杂的示例，请参阅 [CatDB](http://msdn.microsoft.com/zh-cn/003d516b-2bf6-444e-8be5-4ebaa0b66046) 和 [DBViewer](http://msdn.microsoft.com/zh-cn/07620f99-c347-4d09-9ebc-2459e8049832) 示例。  
  
 有关针对架构行集合的提供程序支持的信息，请参阅[支持架构行集合](../../data/oledb/supporting-schema-rowsets.md)。  
  
## 请参阅  
 [使用访问器](../../data/oledb/using-accessors.md)