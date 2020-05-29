---
title: CDaoQueryDefInfo 结构
ms.date: 11/04/2016
f1_keywords:
- CDaoQueryDefInfo
helpviewer_keywords:
- DAO (Data Access Objects), QueryDefs collection
- CDaoQueryDefInfo structure [MFC]
ms.assetid: e20837dc-e78d-4171-a195-1b4075fb5d2a
ms.openlocfilehash: e2f0325237a30989637821464c63a4d8b8000b1e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368937"
---
# <a name="cdaoquerydefinfo-structure"></a>CDaoQueryDefInfo 结构

该`CDaoQueryDefInfo`结构包含有关为数据访问对象 （DAO） 定义的查询def对象的信息。

## <a name="syntax"></a>语法

```
struct CDaoQueryDefInfo
{
    CString m_strName;               // Primary
    short m_nType;   // Primary
    COleDateTime m_dateCreated;      // Secondary
    COleDateTime m_dateLastUpdated;  // Secondary
    BOOL m_bUpdatable;               // Secondary
    BOOL m_bReturnsRecords;          // Secondary
    CString m_strSQL;                // All
    CString m_strConnect;            // All
    short m_nODBCTimeout;            // All
};
```

#### <a name="parameters"></a>参数

*m_strName*<br/>
唯一地命名查询def对象。 有关详细信息，请参阅 DAO 帮助中的主题"名称属性"。 调用[CDaoQueryDef：获取名称](../../mfc/reference/cdaoquerydef-class.md#getname)以直接检索此属性。

*m_nType*<br/>
指示查询def对象的操作类型的值。 值可以是下列任一值：

- `dbQSelect`选择 = 查询选择记录。

- `dbQAction`操作 — 查询移动或更改数据，但不返回记录。

- `dbQCrosstab`交叉选项卡 – 查询以类似电子表格的格式返回数据。

- `dbQDelete`删除 = 查询删除一组指定的行。

- `dbQUpdate`更新 = 查询更改一组记录。

- `dbQAppend`追加 - 查询将新记录添加到表或查询的末尾。

- `dbQMakeTable`制作表 – 查询从记录集创建新表。

- `dbQDDL`数据定义 – 查询影响表或其部件的结构。

- `dbQSQLPassThrough`传递 – SQL 语句直接传递到数据库后端，无需中间处理。

- `dbQSetOperation`联合 = 查询创建一个快照类型记录集对象，其中包含来自两个或多个表中所有指定记录的数据，并删除了任何重复的记录。 要包括重复项，请在查询def的 SQL 语句中添加关键字**ALL。**

- `dbQSPTBulk``dbQSQLPassThrough`用于指定不返回记录的查询。

> [!NOTE]
> 要创建 SQL 传递查询，请不要设置常`dbQSQLPassThrough`量。 当您创建查询def对象并设置 Connect 属性时，Microsoft Jet 数据库引擎会自动设置此设置。

有关详细信息，请参阅 DAO 帮助中的主题"类型属性"。

*m_dateCreated*<br/>
创建查询def的日期和时间。 要直接检索创建查询def的日期，请调用与表关联的`CDaoTableDef`对象的[GetDateCreated](../../mfc/reference/cdaotabledef-class.md#getdatecreated)成员函数。 有关详细信息，请参阅下面的注释。 另请参阅 DAO 帮助中的主题"创建日期，上次更新的属性"。

*m_dateLastUpdated*<br/>
对查询 def 进行的最新更改的日期和时间。 要直接检索表上次更新的日期，请调用查询def的[GetDateLast 更新](../../mfc/reference/cdaoquerydef-class.md#getdatelastupdated)成员函数。 有关详细信息，请参阅下面的注释。 并查看 DAO 帮助中的主题"创建日期，上次更新的属性"。

*m_bUpdatable*<br/>
指示是否可以对查询def对象进行更改。 如果此属性为 TRUE，则查询def 是可升的;如果此属性为 TRUE，则查询 def 是可向上的。否则，它不是。 可上可意味着可以更改查询def对象的查询定义。 如果查询定义可以更新，即使生成的记录集不可更新，查询def对象的 Upda 可属性也设置为 TRUE。 要直接检索此属性，请调用查询def 的[CanUpdate](../../mfc/reference/cdaoquerydef-class.md#canupdate)成员函数。 有关详细信息，请参阅 DAO 帮助中的主题"可增加属性"。

*m_bReturnsRecords*<br/>
指示对外部数据库的 SQL 传递查询是否返回记录。 如果此属性为 TRUE，则查询将返回记录。 要直接检索此属性，请致电[CdaoQueryDef：：获取返回记录](../../mfc/reference/cdaoquerydef-class.md#getreturnsrecords)。 并非所有 SQL 传递到外部数据库的查询都返回记录。 例如，SQL **UPDATE**语句在不返回记录的情况下更新记录，而 SQL **SELECT**语句会返回记录。 有关详细信息，请参阅 DAO 帮助中的主题"返回记录属性"。

*m_strSQL*<br/>
定义由查询def对象执行的查询的 SQL 语句。 SQL 属性包含 SQL 语句，用于确定在执行查询时记录的选择、分组和排序方式。 可以使用查询选择要包含在动态集或快照类型记录集对象中的记录。 您还可以定义批量查询以修改数据，而无需返回记录。 您可以通过调用查询def的[GetSQL](../../mfc/reference/cdaoquerydef-class.md#getsql)成员函数直接检索此属性的值。

*m_strConnect*<br/>
提供有关传递查询中使用的数据库源的信息。 此信息采用连接字符串的形式。 有关连接字符串的详细信息，以及有关直接检索此属性值的信息，请参阅[CDao 数据库：：GetConnect](../../mfc/reference/cdaodatabase-class.md#getconnect)成员函数。

*m_nODBCTimeout*<br/>
在 ODBC 数据库上运行查询之前，Microsoft Jet 数据库引擎等待的秒数。 当您使用 ODBC 数据库（如 Microsoft SQL Server）时，可能会由于网络流量或大量使用 ODBC 服务器而出现延迟。 您可以指定 Microsoft Jet 引擎在产生错误之前等待多长时间，而不是无限期地等待。 默认超时值为 60 秒。 您可以通过调用查询def的[GetODBCTimeout](../../mfc/reference/cdaoquerydef-class.md#getodbctimeout)成员函数直接检索此属性的值。 有关详细信息，请参阅 DAO 帮助中的主题"ODBCTimeout 属性"。

## <a name="remarks"></a>备注

查询def是类[CDaoQueryDef 的对象](../../mfc/reference/cdaoquerydef-class.md)。 对上述主要、次要和全部的引用指示类 中的[GetQueryDefInfo](../../mfc/reference/cdaodatabase-class.md#getquerydefinfo)成员函数如何返回信息`CDaoDatabase`。

[CDao 数据库检索的信息：：getQueryDefInfo](../../mfc/reference/cdaodatabase-class.md#getquerydefinfo)成员函数存储在结构`CDaoQueryDefInfo`中。 调用`GetQueryDefInfo`其 QueryDefs 集合中的数据库对象，其中存储查询def对象。 `CDaoQueryDefInfo`还在调试生成中`Dump`定义成员函数。 可以使用`Dump`转储`CDaoQueryDefInfo`对象的内容。 类`CDaoDatabase`还提供成员函数，用于直接访问`CDaoQueryDefInfo`对象中返回的所有属性，因此您可能很少需要调用`GetQueryDefInfo`。

将新字段或参数对象追加到查询def对象的字段或参数集合时，如果基础数据库不支持为新对象指定的数据类型，则将引发异常。

日期和时间设置派生自创建或上次更新查询def 的计算机。 在多用户环境中，用户应使用**网络时间**命令直接从文件服务器获取这些设置，以避免在 Date"创建"和"上次更新"属性设置中出现差异。

## <a name="requirements"></a>要求

**标题：** afxdao.h

## <a name="see-also"></a>另请参阅

[结构、样式、回调和消息映射](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)<br/>
[CDaoQueryDef 类](../../mfc/reference/cdaoquerydef-class.md)<br/>
[CDaoDatabase 类](../../mfc/reference/cdaodatabase-class.md)
