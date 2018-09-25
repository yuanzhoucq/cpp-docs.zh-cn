---
title: CDaoQueryDefInfo 结构 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CDaoQueryDefInfo
dev_langs:
- C++
helpviewer_keywords:
- DAO (Data Access Objects), QueryDefs collection
- CDaoQueryDefInfo structure [MFC]
ms.assetid: e20837dc-e78d-4171-a195-1b4075fb5d2a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 930626a2c28009f8f0174069a88a59a12c9059af
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46418536"
---
# <a name="cdaoquerydefinfo-structure"></a>CDaoQueryDefInfo 结构

`CDaoQueryDefInfo`结构包含有关 querydef 对象定义为数据访问对象 (DAO) 的信息。

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
唯一地命名 querydef 对象。 有关详细信息，请参阅主题 DAO 帮助中的"名称属性"。 调用[CDaoQueryDef::GetName](../../mfc/reference/cdaoquerydef-class.md#getname)直接检索此属性。

*m_nType*<br/>
一个值，指示 querydef 对象的操作类型。 值可以是下列任一值：

- `dbQSelect` 选择 — 查询用于选择记录。

- `dbQAction` 操作-查询将移动或更改数据但不返回记录。

- `dbQCrosstab` 交叉表 — 查询类似于电子表格的格式返回数据。

- `dbQDelete` 删除 — 查询删除一组指定的行。

- `dbQUpdate` 更新 — 查询更改记录的集。

- `dbQAppend` 查询追加-将新记录添加到表或查询的末尾。

- `dbQMakeTable` 生成表，查询从记录集中创建新表。

- `dbQDDL` 数据定义-查询影响的表或其部分内容的结构。

- `dbQSQLPassThrough` 直通-SQL 语句将直接传递到数据库后端，而无需中间处理。

- `dbQSetOperation` 并集，查询将创建一个包含所有指定在两个记录中的数据的快照类型的记录集对象或任何重复记录的多个表中删除。 若要包含重复项，添加关键字**所有**querydef 的 SQL 语句中。

- `dbQSPTBulk` 用于`dbQSQLPassThrough`若要指定不返回记录的查询。

> [!NOTE]
>  若要创建 SQL 传递查询，未设置`dbQSQLPassThrough`常量。 这是由自动设置 Microsoft Jet 数据库引擎时创建 querydef 对象并设置连接属性。

有关详细信息，请参阅主题 DAO 帮助中的"类型属性"。

*m_dateCreated*<br/>
日期和 querydef 的创建的时间。 若要直接检索 querydef 的创建的日期，请调用[GetDateCreated](../../mfc/reference/cdaotabledef-class.md#getdatecreated)成员函数的`CDaoTableDef`与表关联的对象。 有关详细信息，请参阅下面的注释。 此外请参阅 DAO 帮助中的主题"DateCreated，上次更新属性"。

*m_dateLastUpdated*<br/>
日期和时间对 querydef 所做的最新更改。 若要直接检索上次更新表的日期，请调用[GetDateLastUpdated](../../mfc/reference/cdaoquerydef-class.md#getdatelastupdated) querydef 成员函数。 有关详细信息，请参阅下面的注释。 请参阅中 DAO 帮助主题"DateCreated，上次更新属性"。

*m_bUpdatable*<br/>
指示是否可以对 querydef 对象进行更改。 如果此属性为 TRUE，querydef 是可更新;否则，它不是。 可更新意味着可以更改 querydef 对象的查询定义。 Querydef 对象的可更新属性设置为 TRUE 可更新查询定义，如果即使生成的记录集是不可更新。 若要直接检索此属性，请调用 querydef [CanUpdate](../../mfc/reference/cdaoquerydef-class.md#canupdate)成员函数。 有关详细信息，请参阅主题 DAO 帮助中的"可更新属性"。

*m_bReturnsRecords*<br/>
指示是否向外部数据库的 SQL 传递查询返回的记录。 如果此属性为 TRUE，查询将返回的记录。 若要直接检索此属性，请调用[CDaoQueryDef::GetReturnsRecords](../../mfc/reference/cdaoquerydef-class.md#getreturnsrecords)。 到外部数据库不是所有 SQL 传递查询都返回的记录。 例如，SQL**更新**语句更新记录，并且不返回记录，而 SQL**选择**语句返回的记录。 有关详细信息，请参阅"属性"DAO 帮助中的主题。

*m_strSQL*<br/>
定义由 querydef 对象执行的查询的 SQL 语句。 SQL 属性包含确定如何选择记录，分组和排序时执行查询的 SQL 语句。 可以使用查询来选择要包括在动态集或快照类型的记录集对象中的记录。 此外可以定义大容量查询不返回记录的情况下修改数据。 您可以直接通过调用 querydef 检索此属性的值[GetSQL](../../mfc/reference/cdaoquerydef-class.md#getsql)成员函数。

*m_strConnect*<br/>
提供了有关使用传递查询中的数据库的源的信息。 此信息的连接字符串的形式。 有关详细信息大约连接字符串，并直接检索此属性的值的信息，请参阅[CDaoDatabase::GetConnect](../../mfc/reference/cdaodatabase-class.md#getconnect)成员函数。

*m_nODBCTimeout*<br/>
ODBC 数据库上运行一次查询时发生超时错误之前的 Microsoft Jet 数据库引擎等待的秒数。 在使用 ODBC 数据库，例如 Microsoft SQL Server 时由于网络流量或频繁使用的 ODBC 服务器可能存在延迟。 而不是无限期地等待，可以指定 Microsoft Jet 引擎等待多长时间才能生成错误。 默认超时值为 60 秒。 您可以直接通过调用 querydef 检索此属性的值[GetODBCTimeout](../../mfc/reference/cdaoquerydef-class.md#getodbctimeout)成员函数。 有关详细信息，请参阅主题 DAO 帮助中的"odbc 超时属性"。

## <a name="remarks"></a>备注

Querydef 是类的对象[CDaoQueryDef](../../mfc/reference/cdaoquerydef-class.md)。 对主要、 次要和上面所有的引用指示如何通过返回的信息[GetQueryDefInfo](../../mfc/reference/cdaodatabase-class.md#getquerydefinfo)类中的成员函数`CDaoDatabase`。

检索的信息[CDaoDatabase::GetQueryDefInfo](../../mfc/reference/cdaodatabase-class.md#getquerydefinfo)成员函数存储在`CDaoQueryDefInfo`结构。 调用`GetQueryDefInfo`querydef 对象存储在其 QueryDefs 集合中的数据库对象。 `CDaoQueryDefInfo` 此外定义了`Dump`成员函数在调试生成。 可以使用`Dump`转储的内容`CDaoQueryDefInfo`对象。 类`CDaoDatabase`还提供了用于直接访问的所有属性中返回的成员函数`CDaoQueryDefInfo`对象，因此您可能很少需要调用`GetQueryDefInfo`。

当你将新字段或参数对象追加到 querydef 对象的字段或参数的集合时，如果基础数据库不支持指定为新的对象的数据类型是引发异常。

从计算机在其创建或上次更新时间 querydef 派生的日期和时间设置。 在多用户环境中，用户应直接从文件服务器使用获取这些设置**net 时间**命令，以避免 DateCreated 和上次更新属性设置中的差异。

## <a name="requirements"></a>要求

**标头：** afxdao.h

## <a name="see-also"></a>请参阅

[结构、样式、回调和消息映射](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)<br/>
[CDaoQueryDef 类](../../mfc/reference/cdaoquerydef-class.md)<br/>
[CDaoDatabase 类](../../mfc/reference/cdaodatabase-class.md)
