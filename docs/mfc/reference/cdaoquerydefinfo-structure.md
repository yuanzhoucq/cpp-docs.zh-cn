---
title: "CDaoQueryDefInfo 结构 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CDaoQueryDefInfo"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CDaoQueryDefInfo 结构"
  - "DAO（数据访问对象）, QueryDefs 集合"
ms.assetid: e20837dc-e78d-4171-a195-1b4075fb5d2a
caps.latest.revision: 13
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CDaoQueryDefInfo 结构
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

`CDaoQueryDefInfo` 结构包含有关用于数据访问对象定义的 querydef 对象的信息 \(DAO\)。  
  
## 语法  
  
```  
  
      struct CDaoQueryDefInfo  
{  
   CString m_strName;               // Primary  
   short m_nType;                   // Primary  
   COleDateTime m_dateCreated;      // Secondary  
   COleDateTime m_dateLastUpdated;  // Secondary  
   BOOL m_bUpdatable;               // Secondary  
   BOOL m_bReturnsRecords;          // Secondary  
   CString m_strSQL;                // All  
   CString m_strConnect;            // All  
   short m_nODBCTimeout;            // All  
};  
```  
  
#### 参数  
 `m_strName`  
 唯一命名 querydef 对象。  有关更多信息，请参见主题“属性名称”DAO 帮助。  直接调用检索此属性的 [CDaoQueryDef::GetName](../Topic/CDaoQueryDef::GetName.md)。  
  
 `m_nType`  
 指示 querydef 对象的操作类型的值。  其值可以为以下值之一：  
  
-   SELECT 查询**dbQSelect** \- 选择记录。  
  
-   **dbQAction** \- 操作查询移动或更改数据，但不返回记录。  
  
-   **dbQCrosstab** \- Crosstab 查询返回一个类似电子表格格式的数据。  
  
-   删除 \-**dbQDelete** 查询删除一组指定的行。  
  
-   更新 \-**dbQUpdate** 查询更改一组记录。  
  
-   \-**dbQAppend** 追加查询添加新记录到表或查询末尾。  
  
-   **dbQMakeTable** 使表的查询创建从记录集的新表。  
  
-   **dbQDDL** 数据定义的查询影响表或其部件结构。  
  
-   **dbQSQLPassThrough** \- 将 SQL 语句直接传递给数据库后端，中间不处理。  
  
-   **dbQSetOperation** \- 联合查询来创建包含从所有指定记录的快照类型记录集对象与数据在中移除所有重复记录的两个或更多个表。  若要包含复制，在 querydef 的 SQL 语句中 **ALL** 关键字。  
  
-   **dbQSPTBulk** 用于 **dbQSQLPassThrough** 指定不返回记录的查询。  
  
> [!NOTE]
>  若要创建 SQL 查询传递，不设置 **dbQSQLPassThrough** 常数。  当创建 querydef 对象并设置附加属性时，这是 Microsoft Jet 数据库引擎自动设置。  
  
 有关更多信息，请参见主题“类型属性”DAO 帮助。  
  
 `m_dateCreated`  
 querydef 创建日期和时间。  直接检索 querydef 创建日期，调用 `CDaoTableDef` 对象的函数 [GetDateCreated](../Topic/CDaoTableDef::GetDateCreated.md) 成员与表。  请参见下面的说明。更多信息。  请参见主题“DateCreated，LastUpdated 属性”DAO 帮助。  
  
 `m_dateLastUpdated`  
 进行的最近更改的日期和时间。querydef。  直接检索表是最新更新的日期，请调用 querydef 的 [GetDateLastUpdated](../Topic/CDaoQueryDef::GetDateLastUpdated.md) 成员函数。  请参见下面的说明。更多信息。  请参见主题“DateCreated，LastUpdated 属性”DAO 帮助。  
  
 `m_bUpdatable`  
 指示是否可更改对 querydef 对象。  如果此属性 **TRUE**，querydef;是可更新的否则，它也不是。  可更新方式 querydef 对象查询的定义可以更改。  querydef 对象的可枚举集更新的属性设置为 **TRUE**，则可以更新查询定义，因此，即使一结果记录集不可更新。  若要直接检索此属性，调用 querydef 的 [CanUpdate](../Topic/CDaoQueryDef::CanUpdate.md) 成员函数。  有关更多信息，请参见主题“可更新的属性”DAO 帮助。  
  
 *m\_bReturnsRecords*  
 指示对外部数据库的 SQL 传递查询是否返回记录。  如果此属性 **TRUE**，查询返回记录。  直接检索此属性，调用 [CDaoQueryDef::GetReturnsRecords](../Topic/CDaoQueryDef::GetReturnsRecords.md)。  不是对外部数据库返回记录的所有 SQL 的查询。  例如，SQL **UPDATE** 语句更新记录，而无需返回记录，而 SQL **SELECT** 语句返回记录。  有关更多信息，请参见主题“ReturnsRecords 属性”DAO 帮助。  
  
 *m\_strSQL*  
 定义 querydef 对象执行的查询 SQL 语句。  确定属性的 SQL 包含 SQL 语句如何选择记录，组合，并排序何时执行查询。  可以使用查询选择记录到包含在动态集还是快照类型记录集对象。  您还可以定义有关批量查询修改数据，而无需返回记录。  可以直接通过调用 querydef 的 [GetSQL](../Topic/CDaoQueryDef::GetSQL.md) 成员函数检索此属性的值。  
  
 `m_strConnect`  
 提供有关在传递查询数据库的数据源的信息。  此信息包含连接字符串的窗体。  有关的更多信息请连接字符串，和有关直接检索值的信息，请参见 [CDaoDatabase::GetConnect](../Topic/CDaoDatabase::GetConnect.md) 此属性成员函数。  
  
 *m\_nODBCTimeout*  
 Microsoft Jet 数据库引擎等待的秒数，在超时错误之前，在查询上 ODBC 数据库运行。  如果使用 ODBC 数据库，例如 Microsoft SQL Server 时，由于网络流量使用 ODBC 或服务器的大量使用，可能出现延迟。  而不是无限期等待，则可以指定 Microsoft Jet 引擎所等待，则会产生错误。  默认超时值为 60 秒。  可以直接通过调用 querydef 的 [GetODBCTimeout](../Topic/CDaoQueryDef::GetODBCTimeout.md) 成员函数检索此属性的值。  有关更多信息，请参见主题“ODBCTimeout 属性”DAO 帮助。  
  
## 备注  
 querydef 是 [CDaoQueryDef](../../mfc/reference/cdaoquerydef-class.md)类对象。  为 Main，附属的引用和所有的指示信息如何通过类 `CDaoDatabase`中的 [GetQueryDefInfo](../Topic/CDaoDatabase::GetQueryDefInfo.md) 成员函数返回。  
  
 [CDaoDatabase::GetQueryDefInfo](../Topic/CDaoDatabase::GetQueryDefInfo.md) 成员函数检索的信息在 `CDaoQueryDefInfo` 结构存储。  调用 QueryDefs 集合 querydef 对象中存储的数据库对象的 `GetQueryDefInfo` 中。  `CDaoQueryDefInfo` 还定义了函数调试版本的 `Dump` 成员。  可以使用 `Dump` 转储 `CDaoQueryDefInfo` 对象的内容。  `CDaoDatabase` 类也提供直接访问的 `CDaoQueryDefInfo` 对象中返回的所有成员函数属性，因此，可能少需要调用 `GetQueryDefInfo`。  
  
 当您追加到 querydef 对象的字段或参数集合中的新字段或参数对象，则会引发异常，如果基础数据库不支持新对象指定数据类型。  
  
 日期和时间设置从 querydef 创建或之前更新计算机的派生。  在多用户环境中，用户应直接从文件的服务器获得这些设置使用 **net time** 命令来避免在 DateCreated 和属性设置 LastUpdated 的变体。  
  
## 要求  
 **页眉：** afxdao.h  
  
## 请参阅  
 [结构、样式、回调和消息映射](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CDaoQueryDef Class](../../mfc/reference/cdaoquerydef-class.md)   
 [CDaoDatabase Class](../../mfc/reference/cdaodatabase-class.md)