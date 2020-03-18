---
title: CDaoRecordset 类
ms.date: 08/27/2018
f1_keywords:
- CDaoRecordset
- AFXDAO/CDaoRecordset
- AFXDAO/CDaoRecordset::CDaoRecordset
- AFXDAO/CDaoRecordset::AddNew
- AFXDAO/CDaoRecordset::CanAppend
- AFXDAO/CDaoRecordset::CanBookmark
- AFXDAO/CDaoRecordset::CancelUpdate
- AFXDAO/CDaoRecordset::CanRestart
- AFXDAO/CDaoRecordset::CanScroll
- AFXDAO/CDaoRecordset::CanTransact
- AFXDAO/CDaoRecordset::CanUpdate
- AFXDAO/CDaoRecordset::Close
- AFXDAO/CDaoRecordset::Delete
- AFXDAO/CDaoRecordset::DoFieldExchange
- AFXDAO/CDaoRecordset::Edit
- AFXDAO/CDaoRecordset::FillCache
- AFXDAO/CDaoRecordset::Find
- AFXDAO/CDaoRecordset::FindFirst
- AFXDAO/CDaoRecordset::FindLast
- AFXDAO/CDaoRecordset::FindNext
- AFXDAO/CDaoRecordset::FindPrev
- AFXDAO/CDaoRecordset::GetAbsolutePosition
- AFXDAO/CDaoRecordset::GetBookmark
- AFXDAO/CDaoRecordset::GetCacheSize
- AFXDAO/CDaoRecordset::GetCacheStart
- AFXDAO/CDaoRecordset::GetCurrentIndex
- AFXDAO/CDaoRecordset::GetDateCreated
- AFXDAO/CDaoRecordset::GetDateLastUpdated
- AFXDAO/CDaoRecordset::GetDefaultDBName
- AFXDAO/CDaoRecordset::GetDefaultSQL
- AFXDAO/CDaoRecordset::GetEditMode
- AFXDAO/CDaoRecordset::GetFieldCount
- AFXDAO/CDaoRecordset::GetFieldInfo
- AFXDAO/CDaoRecordset::GetFieldValue
- AFXDAO/CDaoRecordset::GetIndexCount
- AFXDAO/CDaoRecordset::GetIndexInfo
- AFXDAO/CDaoRecordset::GetLastModifiedBookmark
- AFXDAO/CDaoRecordset::GetLockingMode
- AFXDAO/CDaoRecordset::GetName
- AFXDAO/CDaoRecordset::GetParamValue
- AFXDAO/CDaoRecordset::GetPercentPosition
- AFXDAO/CDaoRecordset::GetRecordCount
- AFXDAO/CDaoRecordset::GetSQL
- AFXDAO/CDaoRecordset::GetType
- AFXDAO/CDaoRecordset::GetValidationRule
- AFXDAO/CDaoRecordset::GetValidationText
- AFXDAO/CDaoRecordset::IsBOF
- AFXDAO/CDaoRecordset::IsDeleted
- AFXDAO/CDaoRecordset::IsEOF
- AFXDAO/CDaoRecordset::IsFieldDirty
- AFXDAO/CDaoRecordset::IsFieldNull
- AFXDAO/CDaoRecordset::IsFieldNullable
- AFXDAO/CDaoRecordset::IsOpen
- AFXDAO/CDaoRecordset::Move
- AFXDAO/CDaoRecordset::MoveFirst
- AFXDAO/CDaoRecordset::MoveLast
- AFXDAO/CDaoRecordset::MoveNext
- AFXDAO/CDaoRecordset::MovePrev
- AFXDAO/CDaoRecordset::Open
- AFXDAO/CDaoRecordset::Requery
- AFXDAO/CDaoRecordset::Seek
- AFXDAO/CDaoRecordset::SetAbsolutePosition
- AFXDAO/CDaoRecordset::SetBookmark
- AFXDAO/CDaoRecordset::SetCacheSize
- AFXDAO/CDaoRecordset::SetCacheStart
- AFXDAO/CDaoRecordset::SetCurrentIndex
- AFXDAO/CDaoRecordset::SetFieldDirty
- AFXDAO/CDaoRecordset::SetFieldNull
- AFXDAO/CDaoRecordset::SetFieldValue
- AFXDAO/CDaoRecordset::SetFieldValueNull
- AFXDAO/CDaoRecordset::SetLockingMode
- AFXDAO/CDaoRecordset::SetParamValue
- AFXDAO/CDaoRecordset::SetParamValueNull
- AFXDAO/CDaoRecordset::SetPercentPosition
- AFXDAO/CDaoRecordset::Update
- AFXDAO/CDaoRecordset::m_bCheckCacheForDirtyFields
- AFXDAO/CDaoRecordset::m_nFields
- AFXDAO/CDaoRecordset::m_nParams
- AFXDAO/CDaoRecordset::m_pDAORecordset
- AFXDAO/CDaoRecordset::m_pDatabase
- AFXDAO/CDaoRecordset::m_strFilter
- AFXDAO/CDaoRecordset::m_strSort
helpviewer_keywords:
- CDaoRecordset [MFC], CDaoRecordset
- CDaoRecordset [MFC], AddNew
- CDaoRecordset [MFC], CanAppend
- CDaoRecordset [MFC], CanBookmark
- CDaoRecordset [MFC], CancelUpdate
- CDaoRecordset [MFC], CanRestart
- CDaoRecordset [MFC], CanScroll
- CDaoRecordset [MFC], CanTransact
- CDaoRecordset [MFC], CanUpdate
- CDaoRecordset [MFC], Close
- CDaoRecordset [MFC], Delete
- CDaoRecordset [MFC], DoFieldExchange
- CDaoRecordset [MFC], Edit
- CDaoRecordset [MFC], FillCache
- CDaoRecordset [MFC], Find
- CDaoRecordset [MFC], FindFirst
- CDaoRecordset [MFC], FindLast
- CDaoRecordset [MFC], FindNext
- CDaoRecordset [MFC], FindPrev
- CDaoRecordset [MFC], GetAbsolutePosition
- CDaoRecordset [MFC], GetBookmark
- CDaoRecordset [MFC], GetCacheSize
- CDaoRecordset [MFC], GetCacheStart
- CDaoRecordset [MFC], GetCurrentIndex
- CDaoRecordset [MFC], GetDateCreated
- CDaoRecordset [MFC], GetDateLastUpdated
- CDaoRecordset [MFC], GetDefaultDBName
- CDaoRecordset [MFC], GetDefaultSQL
- CDaoRecordset [MFC], GetEditMode
- CDaoRecordset [MFC], GetFieldCount
- CDaoRecordset [MFC], GetFieldInfo
- CDaoRecordset [MFC], GetFieldValue
- CDaoRecordset [MFC], GetIndexCount
- CDaoRecordset [MFC], GetIndexInfo
- CDaoRecordset [MFC], GetLastModifiedBookmark
- CDaoRecordset [MFC], GetLockingMode
- CDaoRecordset [MFC], GetName
- CDaoRecordset [MFC], GetParamValue
- CDaoRecordset [MFC], GetPercentPosition
- CDaoRecordset [MFC], GetRecordCount
- CDaoRecordset [MFC], GetSQL
- CDaoRecordset [MFC], GetType
- CDaoRecordset [MFC], GetValidationRule
- CDaoRecordset [MFC], GetValidationText
- CDaoRecordset [MFC], IsBOF
- CDaoRecordset [MFC], IsDeleted
- CDaoRecordset [MFC], IsEOF
- CDaoRecordset [MFC], IsFieldDirty
- CDaoRecordset [MFC], IsFieldNull
- CDaoRecordset [MFC], IsFieldNullable
- CDaoRecordset [MFC], IsOpen
- CDaoRecordset [MFC], Move
- CDaoRecordset [MFC], MoveFirst
- CDaoRecordset [MFC], MoveLast
- CDaoRecordset [MFC], MoveNext
- CDaoRecordset [MFC], MovePrev
- CDaoRecordset [MFC], Open
- CDaoRecordset [MFC], Requery
- CDaoRecordset [MFC], Seek
- CDaoRecordset [MFC], SetAbsolutePosition
- CDaoRecordset [MFC], SetBookmark
- CDaoRecordset [MFC], SetCacheSize
- CDaoRecordset [MFC], SetCacheStart
- CDaoRecordset [MFC], SetCurrentIndex
- CDaoRecordset [MFC], SetFieldDirty
- CDaoRecordset [MFC], SetFieldNull
- CDaoRecordset [MFC], SetFieldValue
- CDaoRecordset [MFC], SetFieldValueNull
- CDaoRecordset [MFC], SetLockingMode
- CDaoRecordset [MFC], SetParamValue
- CDaoRecordset [MFC], SetParamValueNull
- CDaoRecordset [MFC], SetPercentPosition
- CDaoRecordset [MFC], Update
- CDaoRecordset [MFC], m_bCheckCacheForDirtyFields
- CDaoRecordset [MFC], m_nFields
- CDaoRecordset [MFC], m_nParams
- CDaoRecordset [MFC], m_pDAORecordset
- CDaoRecordset [MFC], m_pDatabase
- CDaoRecordset [MFC], m_strFilter
- CDaoRecordset [MFC], m_strSort
ms.assetid: 2322067f-1027-4662-a5d7-aa2fc7488630
ms.openlocfilehash: 96118645aa656e97fcb93a0fd223045208ab03a3
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/16/2020
ms.locfileid: "79424535"
---
# <a name="cdaorecordset-class"></a>CDaoRecordset 类

表示从数据源选择的一组记录。

## <a name="syntax"></a>语法

```
class CDaoRecordset : public CObject
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[CDaoRecordset：： CDaoRecordset](#cdaorecordset)|构造 `CDaoRecordset` 对象。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CDaoRecordset：： AddNew](#addnew)|准备添加新记录。 调用[Update](#update)来完成添加。|
|[CDaoRecordset：： CanAppend](#canappend)|如果可以通过[AddNew](#addnew)成员函数将新记录添加到记录集中，则返回非零值。|
|[CDaoRecordset：： CanBookmark](#canbookmark)|如果记录集支持书签，则返回非零值。|
|[CDaoRecordset：： CancelUpdate](#cancelupdate)|取消任何挂起的更新，因为[编辑](#edit)或[AddNew](#addnew)操作。|
|[CDaoRecordset：： CanRestart](#canrestart)|如果可以调用[Requery](#requery)再次运行记录集的查询，则返回非零值。|
|[CDaoRecordset：： CanScroll](#canscroll)|如果可以滚动记录，则返回非零值。|
|[CDaoRecordset：： CanTransact](#cantransact)|如果数据源支持事务，则返回非零值。|
|[CDaoRecordset：： CanUpdate](#canupdate)|如果可以更新记录集（您可以添加、更新或删除记录），则返回非零值。|
|[CDaoRecordset：： Close](#close)|关闭记录集。|
|[CDaoRecordset：:D e)](#delete)|从记录集中删除当前记录。 删除后，必须显式滚动到其他记录。|
|[CDaoRecordset：:D oFieldExchange](#dofieldexchange)|调用以在记录集的字段数据成员和数据源的相应记录之间交换数据（双向）。 实现 DAO 记录字段交换（DFX）。|
|[CDaoRecordset：： Edit](#edit)|准备当前记录的更改。 调用 `Update` 以完成编辑。|
|[CDaoRecordset：： FillCache](#fillcache)|填充包含来自 ODBC 数据源的数据的 recordset 对象的全部或部分本地缓存。|
|[CDaoRecordset：： Find](#find)|查找动态集类型记录集中满足指定条件的特定字符串的第一个、下一个、上一个或最后一个位置，并使记录成为当前记录。|
|[CDaoRecordset：： FindFirst](#findfirst)|定位动态集类型或快照类型记录集中满足指定条件的第一条记录，并使该记录成为当前记录。|
|[CDaoRecordset：： FindLast](#findlast)|查找满足指定条件的动态集类型或快照类型记录集中的最后一条记录，并使该记录成为当前记录。|
|[CDaoRecordset：： FindNext](#findnext)|定位满足指定条件的动态集类型或快照类型记录集中的下一条记录，并使该记录成为当前记录。|
|[CDaoRecordset：： FindPrev](#findprev)|在满足指定条件的动态集类型或快照类型记录集中查找上一条记录，并使该记录成为当前记录。|
|[CDaoRecordset：： GetAbsolutePosition](#getabsoluteposition)|返回记录集对象的当前记录的记录号。|
|[CDaoRecordset：： GetBookmark](#getbookmark)|返回一个值，该值表示记录上的书签。|
|[CDaoRecordset：： GetCacheSize](#getcachesize)|返回一个值，该值指定包含要从 ODBC 数据源本地缓存的数据的动态集类型记录集中的记录数。|
|[CDaoRecordset：： GetCacheStart](#getcachestart)|返回一个值，该值指定要缓存的记录集中的第一条记录的书签。|
|[CDaoRecordset：： GetCurrentIndex](#getcurrentindex)|返回一个 `CString`，其中包含最近用于索引表类型 `CDaoRecordset`的索引的名称。|
|[CDaoRecordset：： GetDateCreated](#getdatecreated)|返回创建 `CDaoRecordset` 对象基础的基础表的日期和时间|
|[CDaoRecordset：： GetDateLastUpdated](#getdatelastupdated)|返回对 `CDaoRecordset` 对象基础的基础表的设计进行的最新更改的日期和时间。|
|[CDaoRecordset：： GetDefaultDBName](#getdefaultdbname)|返回默认数据源的名称。|
|[CDaoRecordset：： GetDefaultSQL](#getdefaultsql)|调用以获取要执行的默认 SQL 字符串。|
|[CDaoRecordset：： GetEditMode](#geteditmode)|返回一个值，该值指示当前记录的编辑状态。|
|[CDaoRecordset：： GetFieldCount](#getfieldcount)|返回一个值，该值表示记录集中的字段数。|
|[CDaoRecordset：： Issomapper.getfieldinfo](#getfieldinfo)|返回有关记录集中字段的特定类型的信息。|
|[CDaoRecordset：： GetFieldValue](#getfieldvalue)|返回记录集中某个字段的值。|
|[CDaoRecordset：： GetIndexCount](#getindexcount)|检索记录集的表中的索引数。|
|[CDaoRecordset：： GetIndexInfo](#getindexinfo)|返回有关索引的各种信息。|
|[CDaoRecordset：： GetLastModifiedBookmark](#getlastmodifiedbookmark)|用于确定最近添加或更新的记录。|
|[CDaoRecordset：： GetLockingMode](#getlockingmode)|返回一个值，该值指示在编辑过程中有效的锁定类型。|
|[CDaoRecordset：： GetName](#getname)|返回一个包含记录集名称的 `CString`。|
|[CDaoRecordset：： GetParamValue](#getparamvalue)|检索存储在基础 DAOParameter 对象中的指定参数的当前值。|
|[CDaoRecordset：： GetPercentPosition](#getpercentposition)|以记录总数的百分比形式返回当前记录的位置。|
|[CDaoRecordset：： GetRecordCount](#getrecordcount)|返回 recordset 对象中访问的记录数。|
|[CDaoRecordset：： GetSQL](#getsql)|获取用于为记录集选择记录的 SQL 字符串。|
|[CDaoRecordset：： GetType](#gettype)|调用以确定记录集的类型：表类型、动态集类型或快照类型。|
|[CDaoRecordset：： GetValidationRule](#getvalidationrule)|返回一个 `CString`，其中包含用于在字段中输入数据时对数据进行验证的值。|
|[CDaoRecordset：： GetValidationText](#getvalidationtext)|检索在未满足验证规则时显示的文本。|
|[CDaoRecordset：： IsBOF](#isbof)|如果记录集已定位在第一条记录之前，则返回非零值。 没有当前记录。|
|[CDaoRecordset：： IsDeleted](#isdeleted)|如果记录集位于已删除记录上，则返回非零值。|
|[CDaoRecordset：： IsEOF](#iseof)|如果记录集位于最后一条记录之后，则返回非零值。 没有当前记录。|
|[CDaoRecordset：： IsFieldDirty](#isfielddirty)|如果当前记录中的指定字段已更改，则返回非零值。|
|[CDaoRecordset：： IsFieldNull](#isfieldnull)|如果当前记录中的指定字段为空（没有值），则返回非零值。|
|[CDaoRecordset：： IsFieldNullable](#isfieldnullable)|如果可以将当前记录中的指定字段设置为 Null （没有值），则返回非零值。|
|[CDaoRecordset：： IsOpen](#isopen)|如果先前调用[Open](#open) ，则返回非零值。|
|[CDaoRecordset：： Move](#move)|将记录集定位到任一方向的当前记录中的指定数量的记录。|
|[CDaoRecordset：： MoveFirst](#movefirst)|定位记录集中第一条记录上的当前记录。|
|[CDaoRecordset：： MoveLast](#movelast)|定位记录集中的最后一条记录上的当前记录。|
|[CDaoRecordset：： MoveNext](#movenext)|将当前记录定位到记录集中的下一条记录。|
|[CDaoRecordset：： MovePrev](#moveprev)|将当前记录定位到记录集中的上一条记录。|
|[CDaoRecordset：： Open](#open)|从表、动态集或快照创建新的记录集。|
|[CDaoRecordset：： Requery](#requery)|再次运行记录集的查询以刷新所选记录。|
|[CDaoRecordset：： Seek](#seek)|查找索引表类型记录集中的记录，该对象满足当前索引的指定条件，并使该记录成为当前记录。|
|[CDaoRecordset：： SetAbsolutePosition](#setabsoluteposition)|设置记录集对象的当前记录的记录号。|
|[CDaoRecordset：： SetBookmark](#setbookmark)|将记录集定位在包含指定书签的记录上。|
|[CDaoRecordset：： SetCacheSize](#setcachesize)|设置一个值，该值指定包含要从 ODBC 数据源本地缓存的数据的动态集类型记录集中的记录数。|
|[CDaoRecordset：： SetCacheStart](#setcachestart)|设置一个值，该值指定要缓存的记录集中的第一条记录的书签。|
|[CDaoRecordset：： SetCurrentIndex](#setcurrentindex)|调用以设置表类型记录集的索引。|
|[CDaoRecordset：： SetFieldDirty](#setfielddirty)|将当前记录中的指定字段标记为已更改。|
|[CDaoRecordset：： SetFieldNull](#setfieldnull)|将当前记录中指定字段的值设置为 Null （没有值）。|
|[CDaoRecordset：： SetFieldValue](#setfieldvalue)|设置记录集中某个字段的值。|
|[CDaoRecordset：： SetFieldValueNull](#setfieldvaluenull)|将记录集中某个字段的值设置为 Null。 （没有值）。|
|[CDaoRecordset：： SetLockingMode](#setlockingmode)|设置一个值，该值指示在编辑过程中要生效的锁定类型。|
|[CDaoRecordset：： SetParamValue](#setparamvalue)|设置存储在基础 DAOParameter 对象中的指定参数的当前值|
|[CDaoRecordset：： SetParamValueNull](#setparamvaluenull)|将指定参数的当前值设置为 Null （没有值）。|
|[CDaoRecordset：： SetPercentPosition](#setpercentposition)|将当前记录的位置设置为与记录集中记录总数的百分比相对应的位置。|
|[CDaoRecordset：： Update](#update)|通过保存数据源上的新数据或编辑的数据来完成 `AddNew` 或 `Edit` 操作。|

### <a name="public-data-members"></a>公共数据成员

|名称|说明|
|----------|-----------------|
|[CDaoRecordset：： m_bCheckCacheForDirtyFields](#m_bcheckcachefordirtyfields)|包含一个标志，该标志指示是否将字段自动标记为已更改。|
|[CDaoRecordset：： m_nFields](#m_nfields)|包含记录集类中的字段数据成员数，以及从数据源中记录集选择的列数。|
|[CDaoRecordset：： m_nParams](#m_nparams)|包含记录集类中参数数据成员的数目-与记录集的查询传递的参数的数目|
|[CDaoRecordset：： m_pDAORecordset](#m_pdaorecordset)|指向记录集对象基础的 DAO 接口的指针。|
|[CDaoRecordset：： m_pDatabase](#m_pdatabase)|此结果集的源数据库。 包含指向[CDaoDatabase](../../mfc/reference/cdaodatabase-class.md)对象的指针。|
|[CDaoRecordset：： m_strFilter](#m_strfilter)|包含用于构造 SQL **WHERE**语句的字符串。|
|[CDaoRecordset：： m_strSort](#m_strsort)|包含用于构造 SQL **ORDER BY**语句的字符串。|

## <a name="remarks"></a>备注

称为 "记录集"，`CDaoRecordset` 对象以下列三种形式提供：

- 表类型的记录集表示一个基表，可用于检查、添加、更改或删除单个数据库表中的记录。

- 动态集类型的记录集是可能具有可更新记录的查询结果。 这些记录集是一组记录，可用于检查、添加、更改或删除基础数据库表中的记录。 动态集类型的记录集可以包含数据库中的一个或多个表中的字段。

- 快照类型记录集是一组记录的静态副本，您可以使用这些记录来查找数据或生成报告。 这些记录集可以包含数据库中的一个或多个表中的字段，但不能进行更新。

每种形式的记录集表示在打开记录集时固定的一组记录。 滚动到表类型记录集或动态集类型的记录集中的记录时，它将反映在打开记录集之后，由其他用户或应用程序中的其他记录集对记录所做的更改。 （无法更新快照类型的记录集。）您可以直接使用 `CDaoRecordset` 或从 `CDaoRecordset`派生特定于应用程序的记录集类。 然后，可以：

- 滚动记录。

- 设置索引，并使用[Seek](#seek)快速查找记录（仅限表类型记录集）。

- 基于字符串比较查找记录： "<"、"\<="、"="、"> =" 或 ">" （动态集类型和快照类型记录集）。

- 更新记录并指定锁定模式（快照类型记录集除外）。

- 筛选记录集，以限制从数据源中的可用记录选择的记录。

- 对记录集排序。

- 参数化记录集，以通过在运行时之前不知道的信息自定义其选择。

类 `CDaoRecordset` 提供类似于类 `CRecordset`的接口。 主要区别在于，类 `CDaoRecordset` 通过基于 OLE 的数据访问对象（DAO）来访问数据。 类 `CRecordset` 通过开放式数据库连接（ODBC）和 DBMS 的 ODBC 驱动程序访问 DBMS。

> [!NOTE]
> DAO 数据库类与基于开放式数据库连接（ODBC）的 MFC 数据库类不同。 所有 DAO 数据库类名称都具有 "CDao" 前缀。 你仍可以使用 DAO 类访问 ODBC 数据源;DAO 类通常提供了高级功能，因为它们特定于 Microsoft Jet 数据库引擎。

您可以直接使用 `CDaoRecordset` 或从 `CDaoRecordset`派生类。 若要在这两种情况下使用记录集类，请打开数据库并构造 recordset 对象，并向构造函数传递一个指向 `CDaoDatabase` 对象的指针。 你还可以构造 `CDaoRecordset` 对象，并让 MFC 为你创建一个临时 `CDaoDatabase` 对象。 然后调用记录集的[Open](#open)成员函数，指定该对象是表类型的记录集、动态集类型的记录集还是快照类型的记录集。 调用 `Open` 将从数据库中选择数据，并检索第一条记录。

使用对象的成员函数和数据成员滚动记录并对其进行操作。 可用的操作取决于对象是表类型的记录集、动态集类型的记录集还是快照类型记录集，以及它是可更新还是只读，这取决于数据库的功能或开放式数据库连接（ODBC）数据源。 若要刷新自 `Open` 调用后可能已更改或添加的记录，请调用对象的[Requery](#requery)成员函数。 调用对象的 `Close` 成员函数并在完成后销毁对象。

`CDaoRecordset` 使用 DAO 记录字段交换（DFX）来支持通过 `CDaoRecordset` 或 `CDaoRecordset`派生类的类型安全C++成员读取和更新记录字段。 你还可以在不使用 DFX 机制的情况下，使用[GetFieldValue](#getfieldvalue)和[SetFieldValue](#setfieldvalue)实现列在数据库中的动态绑定。

有关相关信息，请参阅 DAO 帮助中的主题 "Recordset 对象"。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

`CDaoRecordset`

## <a name="requirements"></a>要求

**标头：** afxdao

##  <a name="addnew"></a>CDaoRecordset：： AddNew

调用此成员函数以将新记录添加到表类型或动态集类型的记录集。

```
virtual void AddNew();
```

### <a name="remarks"></a>备注

该记录的字段最初为空。 （在数据库术语中，Null 表示 "无值"，而不是中C++的 null。）若要完成该操作，必须调用[更新](#update)成员函数。 `Update` 保存对数据源所做的更改。

> [!CAUTION]
>  如果编辑一条记录，然后滚动到另一条记录，而不调用 `Update`，则所做的更改不会出现警告。

如果通过调用[AddNew](#addnew)向动态集类型的记录集中添加记录，则该记录将在记录集中可见，并包含在基础表中，该记录将对任何新的 `CDaoRecordset` 对象可见。

新记录的位置取决于记录集的类型：

- 在动态集类型的记录集中，不保证插入新记录的。 此行为随 Microsoft Jet 3.0 更改，原因是性能和并发性的原因。 如果你的目标是使新添加的记录成为当前记录，请获取最后修改的记录的书签，并移到该书签：

[!code-cpp[NVC_MFCDatabase#1](../../mfc/codesnippet/cpp/cdaorecordset-class_1.cpp)]

- 在为其指定了索引的表类型记录集中，记录在排序顺序中的适当位置返回。 如果未指定任何索引，则在记录集的末尾返回新记录。

使用之前的当前记录 `AddNew` 保持最新。 如果要使新记录成为当前记录并且记录集支持书签，请将[SetBookmark](#setbookmark)调用到由基础 DAO 记录集对象的 LastModified 属性设置标识的书签。 这样做可用于确定已添加记录中计数器（自动递增）字段的值。 有关详细信息，请参阅[GetLastModifiedBookmark](#getlastmodifiedbookmark)。

如果数据库支持事务，则可以使 `AddNew` 调用事务的一部分。 有关事务的详细信息，请参阅类[CDaoWorkspace](../../mfc/reference/cdaoworkspace-class.md)。 请注意，在调用 `AddNew`之前应调用[CDaoWorkspace：： BeginTrans](../../mfc/reference/cdaoworkspace-class.md#begintrans) 。

对于尚未调用[Open](#open)成员函数的记录集调用 `AddNew` 是非法的。 如果为无法追加的记录集调用 `AddNew`，则会引发 `CDaoException`。 可以通过调用[CanAppend](#canappend)来确定是否可更新记录集。

框架标记已更改的字段数据成员，以确保 DAO 记录字段交换（DFX）机制将它们写入数据源上的记录。 更改字段的值通常会自动将字段设置为脏字段，因此您很少需要自己调用[SetFieldDirty](#setfielddirty) ，但有时您可能希望确保列将被显式更新或插入，而不考虑字段数据成员中的值。 DFX 机制还采用了**伪 NULL**。 有关详细信息，请参阅[CDaoFieldExchange：： m_nOperation](../../mfc/reference/cdaofieldexchange-class.md#m_noperation)。

如果未使用双缓冲机制，则更改字段的值不会自动将字段设置为 "已更新"。 在这种情况下，需要显式设置现场更新。 [M_bCheckCacheForDirtyFields](#m_bcheckcachefordirtyfields)中包含的标志控制此自动字段检查。

> [!NOTE]
> 如果记录是双缓冲的（即启用了自动字段检查），则调用 `CancelUpdate` 会将成员变量还原到 `AddNew` 或 `Edit` 调用前的值。

有关相关信息，请参阅 DAO 帮助中的 "AddNew 方法"、"CancelUpdate 方法"、"LastModified 属性" 和 "EditMode 属性" 主题。

##  <a name="canappend"></a>CDaoRecordset：： CanAppend

调用此成员函数以确定先前打开的记录集是否允许通过调用[AddNew](#addnew)成员函数来添加新记录。

```
BOOL CanAppend() const;
```

### <a name="return-value"></a>返回值

如果记录集允许添加新记录，则为非零值;否则为0。 如果以只读方式打开了记录集，`CanAppend` 将返回0。

### <a name="remarks"></a>备注

有关相关信息，请参阅 DAO 帮助中的主题 "Append 方法"。

##  <a name="canbookmark"></a>CDaoRecordset：： CanBookmark

调用此成员函数以确定先前打开的记录集是否允许您使用书签单独标记记录。

```
BOOL CanBookmark();
```

### <a name="return-value"></a>返回值

如果记录集支持书签，则为非零; 否则为0。

### <a name="remarks"></a>备注

如果你使用完全基于 Microsoft Jet 数据库引擎表的记录集，则除了标记为只进滚动记录集的快照类型记录集之外，还可以使用书签。 其他数据库产品（外部 ODBC 数据源）可能不支持书签。

有关相关信息，请参阅 DAO 帮助中的主题 "Bookmarkable 属性"。

##  <a name="cancelupdate"></a>CDaoRecordset：： CancelUpdate

`CancelUpdate` 成员函数将取消任何挂起的更新，因为[编辑](#edit)或[AddNew](#addnew)操作。

```
virtual void CancelUpdate();
```

### <a name="remarks"></a>备注

例如，如果应用程序调用 `Edit` 或 `AddNew` 成员函数，但未调用[Update](#update)，`CancelUpdate` 将取消调用 `Edit` 或 `AddNew` 后所做的任何更改。

> [!NOTE]
>  如果记录是双缓冲的（即启用了自动字段检查），则调用 `CancelUpdate` 会将成员变量还原到 `AddNew` 或 `Edit` 调用前的值。

如果没有 `Edit` 或 `AddNew` 操作挂起，`CancelUpdate` 将导致 MFC 引发异常。 调用[GetEditMode](#geteditmode)成员函数，以确定是否有可取消的挂起操作。

有关相关信息，请参阅 DAO 帮助中的 "CancelUpdate 方法" 主题。

##  <a name="canrestart"></a>CDaoRecordset：： CanRestart

调用此成员函数以确定记录集是否允许通过调用 `Requery` 成员函数来重新启动其查询（刷新其记录）。

```
BOOL CanRestart();
```

### <a name="return-value"></a>返回值

如果可以调用 `Requery` 以重新运行记录集的查询，则为非零值; 否则为0。

### <a name="remarks"></a>备注

表类型的记录集不支持 `Requery`。

如果不支持 `Requery`，请调用[Close](#close) ，然后[打开](#open)以刷新数据。 在参数值更改后，可以调用 `Requery` 更新记录集对象的基础参数查询。

相关信息，请参阅 DAO 帮助中的 "重新启动属性" 主题。

##  <a name="canscroll"></a>CDaoRecordset：： CanScroll

调用此成员函数以确定记录集是否允许滚动。

```
BOOL CanScroll() const;
```

### <a name="return-value"></a>返回值

如果可以滚动记录，则为非零; 否则为0。

### <a name="remarks"></a>备注

如果通过 `dbForwardOnly`调用[Open](#open) ，则记录集只能向前滚动。

有关相关信息，请参阅 DAO 帮助中的 "用 DAO 定位当前记录指针" 主题。

##  <a name="cantransact"></a>CDaoRecordset：： CanTransact

调用此成员函数以确定记录集是否允许事务。

```
BOOL CanTransact();
```

### <a name="return-value"></a>返回值

如果基础数据源支持事务，则为非零; 否则为0。

### <a name="remarks"></a>备注

有关相关信息，请参阅 DAO 帮助中的主题 "事务属性"。

##  <a name="canupdate"></a>CDaoRecordset：： CanUpdate

调用此成员函数以确定是否可以更新记录集。

```
BOOL CanUpdate() const;
```

### <a name="return-value"></a>返回值

如果可以更新记录集（添加、更新和删除记录），则为非零; 否则为0。

### <a name="remarks"></a>备注

如果基础数据源为只读，或者如果在为记录集调用[Open](#open)时为*nOptions*指定了 `dbReadOnly`，则记录集可能为只读。

有关相关信息，请参阅 DAO 帮助中的 "AddNew 方法"、"编辑方法"、"删除方法"、"更新方法" 和 "可更新属性" 主题。

##  <a name="cdaorecordset"></a>CDaoRecordset：： CDaoRecordset

构造 `CDaoRecordset` 对象。

```
CDaoRecordset(CDaoDatabase* pDatabase = NULL);
```

### <a name="parameters"></a>parameters

*pDatabase*<br/>
包含指向[CDaoDatabase](../../mfc/reference/cdaodatabase-class.md)对象的指针或值 NULL。 如果不为 NULL，并且尚未调用 `CDaoDatabase` 对象的 `Open` 成员函数以将其连接到数据源，则记录集会在其自己的[open](#open)调用期间尝试打开它。 如果传递 NULL，则将使用指定的数据源信息为你构造并连接 `CDaoDatabase` 对象（如果从 `CDaoRecordset`派生记录集类）。

### <a name="remarks"></a>备注

您可以直接使用 `CDaoRecordset`，也可以从 `CDaoRecordset`派生特定于应用程序的类。 可以使用 ClassWizard 来派生记录集类。

> [!NOTE]
>  如果派生 `CDaoRecordset` 类，则派生类必须提供其自己的构造函数。 在派生类的构造函数中，调用构造函数 `CDaoRecordset::CDaoRecordset`，并将适当的参数传递给它。

将 NULL 传递给记录集构造函数以自动构造和连接 `CDaoDatabase` 对象。 这是一个很有用的快捷方式，在构造记录集之前，不需要构造和连接 `CDaoDatabase` 对象。 如果 `CDaoDatabase` 对象未打开，则还将为你创建使用默认工作区的[CDaoWorkspace](../../mfc/reference/cdaoworkspace-class.md)对象。 有关详细信息，请参阅[CDaoDatabase：： CDaoDatabase](../../mfc/reference/cdaodatabase-class.md#cdaodatabase)。

##  <a name="close"></a>CDaoRecordset：： Close

关闭 `CDaoRecordset` 对象会将其从关联数据库中打开的记录集集合中删除。

```
virtual void Close();
```

### <a name="remarks"></a>备注

由于 `Close` 不会销毁 `CDaoRecordset` 对象，因此可以通过对同一数据源或其他数据源调用 `Open` 来重用该对象。

取消所有挂起的[AddNew](#addnew)或[Edit](#edit)语句，并回滚所有挂起的事务。 如果要保留挂起的添加或编辑，请在为每个记录集调用 `Close` 之前调用[Update](#update) 。

调用 `Close`后，可以再次调用 `Open`。 这使您可以重复使用 recordset 对象。 如果可能，更好的替代方法是调用[Requery](#requery)。

有关相关信息，请参阅 DAO 帮助中的主题 "关闭方法"。

##  <a name="delete"></a>CDaoRecordset：:D e)

调用此成员函数以删除开放动态集类型或表类型 recordset 对象中的当前记录。

```
virtual void Delete();
```

### <a name="remarks"></a>备注

成功删除后，记录集的字段数据成员被设置为 Null 值，并且必须显式调用其中一个记录集导航成员函数（ [move](#move)、 [Seek](#seek)、 [SetBookmark](#setbookmark)等），以便移出已删除的记录。 从记录集中删除记录时，在调用 `Delete`之前，记录集中必须存在当前记录;否则，MFC 会引发异常。

`Delete` 删除当前记录并使其不可访问。 尽管不能编辑或使用已删除的记录，但它仍保持最新。 但是，一旦移动到另一条记录，就不能再次使删除的记录成为最新记录。

> [!CAUTION]
>  记录集必须是可更新的，在调用 `Delete`时，记录集中必须有有效的记录。 例如，如果您删除一个记录，但在再次调用 `Delete` 之前不滚动到新记录，`Delete` 将引发[CDaoException](../../mfc/reference/cdaoexception-class.md)。

如果使用事务，则可以撤消删除记录，并且可以调用[CDaoWorkspace：： Rollback](../../mfc/reference/cdaoworkspace-class.md#rollback)成员函数。 如果基表是级联删除关系中的主表，则删除当前记录也可能会删除外表中的一个或多个记录。 有关详细信息，请参阅 DAO 帮助中的 "级联删除" 定义。

与 `AddNew` 和 `Edit`不同，对 `Delete` 的调用后跟对 `Update`的调用。

有关相关信息，请参阅 DAO 帮助中的 "AddNew 方法"、"编辑方法"、"删除方法"、"更新方法" 和 "可更新属性" 主题。

##  <a name="dofieldexchange"></a>CDaoRecordset：:D oFieldExchange

框架调用此成员函数以自动在记录集对象的字段数据成员与数据源中的当前记录的对应列之间交换数据。

```
virtual void DoFieldExchange(CDaoFieldExchange* pFX);
```

### <a name="parameters"></a>parameters

*pFX*<br/>
包含指向 `CDaoFieldExchange` 对象的指针。 框架将已设置此对象，以指定字段交换操作的上下文。

### <a name="remarks"></a>备注

它还将参数数据成员（如果有）绑定到记录集选定内容的 SQL 语句字符串中的参数占位符。 字段数据的交换（称为 DAO 记录字段交换（DFX））在两个方向上都适用：从记录集对象的字段数据成员到数据源中记录的字段，以及从数据源中的记录到记录集对象。 如果要动态绑定列，则无需实现 `DoFieldExchange`。

通常，为派生的记录集类实现 `DoFieldExchange` 必须执行的唯一操作是创建具有 ClassWizard 的类，并指定字段数据成员的名称和数据类型。 你还可以将代码添加到 ClassWizard 写入内容，以指定参数数据成员。 如果所有字段都要动态绑定，则此函数将处于非活动状态，除非您指定参数数据成员。

使用 ClassWizard 声明派生的记录集类时，向导会为你编写 `DoFieldExchange` 的替代，这类似于以下示例：

[!code-cpp[NVC_MFCDatabase#2](../../mfc/codesnippet/cpp/cdaorecordset-class_2.cpp)]

##  <a name="edit"></a>CDaoRecordset：： Edit

调用此成员函数以允许对当前记录进行更改。

```
virtual void Edit();
```

### <a name="remarks"></a>备注

调用 `Edit` 成员函数后，对当前记录的字段所做的更改将被复制到复制缓冲区。 对记录进行所需的更改后，请调用 `Update` 以保存更改。 `Edit` 保存记录集的数据成员的值。 如果调用 `Edit`，进行更改，然后再次调用 `Edit`，则会将记录的值还原为第一次 `Edit` 调用前的值。

> [!CAUTION]
>  如果编辑一条记录，然后执行任何移动到另一条记录的操作，而无需先调用 `Update`，则所做的更改不会出现警告。 此外，如果关闭记录集或父数据库，则会放弃编辑的记录而不发出警告。

在某些情况下，您可能希望通过将列设为 Null （不包含数据）来更新该列。 为此，请调用参数为 TRUE 的 `SetFieldNull`，以将字段标记为 Null;这也会导致列更新。 如果希望将字段写入数据源（即使其值未更改），请使用参数 TRUE 调用 `SetFieldDirty`。 即使该字段的值为 Null，也是如此。

框架标记已更改的字段数据成员，以确保 DAO 记录字段交换（DFX）机制将它们写入数据源上的记录。 更改字段的值通常会自动将字段设置为脏字段，因此您很少需要自己调用[SetFieldDirty](#setfielddirty) ，但有时您可能希望确保列将被显式更新或插入，而不考虑字段数据成员中的值。 DFX 机制还采用了**伪 NULL**。 有关详细信息，请参阅[CDaoFieldExchange：： m_nOperation](../../mfc/reference/cdaofieldexchange-class.md#m_noperation)。

如果未使用双缓冲机制，则更改字段的值不会自动将字段设置为 "已更新"。 在这种情况下，需要显式设置现场更新。 [M_bCheckCacheForDirtyFields](#m_bcheckcachefordirtyfields)中包含的标志控制此自动字段检查。

如果在多用户环境中 pessimistically 记录集对象，则在更新完成之前，记录将一直保持锁定状态 `Edit`。 如果记录集已乐观地锁定，则该记录将被锁定，并与预编辑的记录进行比较，就像在数据库中更新该记录。 如果记录自调用 `Edit`以来已更改，则 `Update` 操作将失败，MFC 将引发异常。 可以通过 `SetLockingMode`更改锁定模式。

> [!NOTE]
>  始终对外部数据库格式使用开放式锁定，如 ODBC 和可安装的 ISAM。

调用 `Edit`后，当前记录保持最新。 若要调用 `Edit`，必须有当前记录。 如果没有当前记录，或者如果记录集未引用打开的表类型或动态集类型的 recordset 对象，则会发生异常。 调用 `Edit` 会导致 `CDaoException` 在以下条件下引发：

- 没有当前记录。

- 数据库或记录集是只读的。

- 记录中没有可更新的字段。

- 已打开数据库或记录集以供其他用户独占使用。

- 其他用户已锁定包含记录的页面。

如果数据源支持事务，则可以将 `Edit` 调用部分事务。 请注意，在调用 `Edit` 之前以及在打开记录集之后，应调用 `CDaoWorkspace::BeginTrans`。 另请注意，调用 `CDaoWorkspace::CommitTrans` 不能代替调用 `Update` 来完成 `Edit` 操作。 有关事务的详细信息，请参阅类 `CDaoWorkspace`。

有关相关信息，请参阅 DAO 帮助中的 "AddNew 方法"、"编辑方法"、"删除方法"、"更新方法" 和 "可更新属性" 主题。

##  <a name="fillcache"></a>CDaoRecordset：： FillCache

调用此成员函数以从记录集中缓存指定数量的记录。

```
void FillCache(
    long* pSize = NULL,
    COleVariant* pBookmark = NULL);
```

### <a name="parameters"></a>parameters

*pSize*<br/>
指定要在缓存中填充的行数。 如果省略此参数，则该值由基础 DAO 对象的 CacheSize 属性设置确定。

*pBookmark*<br/>
指定书签的[COleVariant](../../mfc/reference/colevariant-class.md) 。 缓存将从此书签指示的记录开始填充。 如果省略此参数，则缓存将从基础 DAO 对象的 CacheStart 属性所指示的记录开始填充。

### <a name="remarks"></a>备注

缓存提高了从远程服务器检索或提取数据的应用程序的性能。 缓存是本地内存中的空间，保存最近从服务器提取的数据，前提是在运行应用程序时可能会再次请求数据。 请求数据时，Microsoft Jet 数据库引擎首先会检查缓存中的数据，而不是从服务器中提取数据，这需要花费更多时间。 在非 ODBC 数据源上使用数据缓存不会有任何影响，因为数据不会保存到缓存中。

您可以通过调用 `FillCache` 成员函数，在任何时候都可以显式填充缓存，而不是在提取缓存时等待记录。 这是一种更快的缓存方式，因为 `FillCache` 一次提取多条记录，而不是一次提取一个记录。 例如，当显示记录的每个 screenful 时，可以让应用程序调用 `FillCache` 来提取下一 screenful 记录。

使用记录集对象访问的任何 ODBC 数据库都可以有本地缓存。 若要创建缓存，请从远程数据源打开一个记录集对象，然后调用该记录集的 `SetCacheSize` 和 `SetCacheStart` 成员函数。 如果*lSize*和*lBookmark*创建的范围部分或完全超出 `SetCacheSize` 和 `SetCacheStart`指定的范围，则将忽略此范围外的记录集部分，并且不会将其加载到缓存中。 如果 `FillCache` 请求的记录超过远程数据源中保留的数量，则只提取剩余记录，不引发异常。

从缓存中提取的记录不反映其他用户对源数据所做的更改。

`FillCache` 仅提取尚未缓存的记录。 若要强制更新所有缓存的数据，请使用等于0的*lSize*参数调用 `SetCacheSize` 成员函数，再次调用 `SetCacheSize`， *lSize*参数等于最初请求的缓存大小，然后调用 `FillCache`。

有关相关信息，请参阅 DAO 帮助中的 "FillCache 方法" 主题。

##  <a name="find"></a>CDaoRecordset：： Find

使用比较运算符调用此成员函数以定位动态集或快照类型记录集中的特定字符串。

```
virtual BOOL Find(
    long lFindType,
    LPCTSTR lpszFilter);
```

### <a name="parameters"></a>parameters

*lFindType*<br/>
一个值，该值指示所需的查找操作的类型。 可能的值包括：

- AFX_DAO_NEXT 查找匹配字符串的下一个位置。

- AFX_DAO_PREV 查找匹配字符串的上一个位置。

- AFX_DAO_FIRST 查找匹配字符串的第一个位置。

- AFX_DAO_LAST 查找匹配字符串的最后一个位置。

*lpszFilter*<br/>
用于定位记录的字符串表达式（如 SQL 语句中没有单词**where**的**where**子句）。 例如：

[!code-cpp[NVC_MFCDatabase#3](../../mfc/codesnippet/cpp/cdaorecordset-class_3.cpp)]

### <a name="return-value"></a>返回值

如果找到匹配记录，则为非零; 否则为0。

### <a name="remarks"></a>备注

您可以找到字符串的第一个、下一个、上一个或最后一个实例。 `Find` 是一种虚拟函数，因此可以重写它并添加自己的实现。 `FindFirst`、`FindLast`、`FindNext`和 `FindPrev` 成员函数调用 `Find` 成员函数，因此可以使用 `Find` 来控制所有查找操作的行为。

若要在表类型记录集中查找记录，请调用[Seek](#seek)成员函数。

> [!TIP]
>  您拥有的记录集越小，`Find` 就越有效。 通常情况下，尤其是在使用 ODBC 数据的情况下，最好创建一个仅检索所需记录的新查询。

相关信息，请参阅 DAO 帮助中的 "FindFirst，FindLast，FindNext，FindPrevious 方法" 主题。

##  <a name="findfirst"></a>CDaoRecordset：： FindFirst

调用此成员函数以查找与指定条件匹配的第一条记录。

```
BOOL FindFirst(LPCTSTR lpszFilter);
```

### <a name="parameters"></a>parameters

*lpszFilter*<br/>
用于定位记录的字符串表达式（如 SQL 语句中没有单词**where**的**where**子句）。

### <a name="return-value"></a>返回值

如果找到匹配记录，则为非零; 否则为0。

### <a name="remarks"></a>备注

`FindFirst` 成员函数从记录集的开头开始搜索，并搜索到记录集的末尾。

如果要在搜索中包括所有记录（而不仅仅是满足特定条件的记录），请使用移动操作之一从记录移动到记录。 若要在表类型记录集中查找记录，请调用 `Seek` 成员函数。

如果未找到与条件匹配的记录，则当前记录指针将无法确定，`FindFirst` 将返回零。 如果记录集包含多个满足条件的记录，`FindFirst` 将查找第一个匹配项，`FindNext` 查找下一个匹配项，依此类推。

> [!CAUTION]
>  如果编辑当前记录，请确保先通过调用 `Update` 成员函数来保存更改，然后再移动到另一条记录。 如果移动到另一条记录而不更新，则更改将会丢失，并且不会出现警告。

`Find` 成员函数按照下表中指定的位置进行搜索：

|查找操作|Begin|搜索方向|
|---------------------|-----------|----------------------|
|`FindFirst`|记录集开头|记录集末尾|
|`FindLast`|记录集末尾|记录集开头|
|`FindNext`|当前记录|记录集末尾|
|`FindPrevious`|当前记录|记录集开头|

> [!NOTE]
>  调用 `FindLast`时，如果尚未执行此操作，Microsoft Jet 数据库引擎将在开始搜索之前完全填充记录集。 第一次搜索可能需要比后续搜索更长的时间。

使用其中一个查找操作与调用 `MoveFirst` 或 `MoveNext`不同，但是，这只是在不指定条件的情况下，将第一个或下一个记录作为当前记录。 可以通过移动操作执行查找操作。

使用 "查找" 操作时，请注意以下事项：

- 如果 `Find` 返回非零值，则不定义当前记录。 在这种情况下，您必须将当前记录指针定位回有效记录。

- 不能使用具有只进滚动快照类型记录集的查找操作。

- 当你搜索包含日期的字段时，你应使用美国日期格式（月-日），即使你未使用 Microsoft Jet 数据库引擎的美国版本;否则，可能找不到匹配的记录。

- 使用 ODBC 数据库和大型动态集时，可能会发现使用 "查找" 操作的速度较慢，尤其是在处理大型记录集时。 可以通过使用带有自定义**ORDERBY**或**WHERE**子句、参数查询或 `CDaoQuerydef` 对象的 SQL 查询来检索特定索引记录，从而提高性能。

相关信息，请参阅 DAO 帮助中的 "FindFirst，FindLast，FindNext，FindPrevious 方法" 主题。

##  <a name="findlast"></a>CDaoRecordset：： FindLast

调用此成员函数以查找与指定条件匹配的最后一条记录。

```
BOOL FindLast(LPCTSTR lpszFilter);
```

### <a name="parameters"></a>parameters

*lpszFilter*<br/>
用于定位记录的字符串表达式（如 SQL 语句中没有单词**where**的**where**子句）。

### <a name="return-value"></a>返回值

如果找到匹配记录，则为非零; 否则为0。

### <a name="remarks"></a>备注

`FindLast` 成员函数在记录集末尾开始其搜索，并向后搜索记录集的开头。

如果要在搜索中包括所有记录（而不仅仅是满足特定条件的记录），请使用移动操作之一从记录移动到记录。 若要在表类型记录集中查找记录，请调用 `Seek` 成员函数。

如果未找到与条件匹配的记录，则当前记录指针将无法确定，`FindLast` 将返回零。 如果记录集包含多个满足条件的记录，`FindFirst` 将查找第一个匹配项，`FindNext` 查找第一个匹配项之后的下一个匹配项，依此类推。

> [!CAUTION]
>  如果编辑当前记录，请确保先通过调用 `Update` 成员函数来保存更改，然后再移动到另一条记录。 如果移动到另一条记录而不更新，则更改将会丢失，并且不会出现警告。

使用其中一个查找操作与调用 `MoveFirst` 或 `MoveNext`不同，但是，这只是在不指定条件的情况下，将第一个或下一个记录作为当前记录。 可以通过移动操作执行查找操作。

使用 "查找" 操作时，请注意以下事项：

- 如果 `Find` 返回非零值，则不定义当前记录。 在这种情况下，您必须将当前记录指针定位回有效记录。

- 不能使用具有只进滚动快照类型记录集的查找操作。

- 当你搜索包含日期的字段时，你应使用美国日期格式（月-日），即使你未使用 Microsoft Jet 数据库引擎的美国版本;否则，可能找不到匹配的记录。

- 使用 ODBC 数据库和大型动态集时，可能会发现使用 "查找" 操作的速度较慢，尤其是在处理大型记录集时。 可以通过使用带有自定义**ORDERBY**或**WHERE**子句、参数查询或 `CDaoQuerydef` 对象的 SQL 查询来检索特定索引记录，从而提高性能。

相关信息，请参阅 DAO 帮助中的 "FindFirst，FindLast，FindNext，FindPrevious 方法" 主题。

##  <a name="findnext"></a>CDaoRecordset：： FindNext

调用此成员函数以查找与指定条件匹配的下一条记录。

```
BOOL FindNext(LPCTSTR lpszFilter);
```

### <a name="parameters"></a>parameters

*lpszFilter*<br/>
用于定位记录的字符串表达式（如 SQL 语句中没有单词**where**的**where**子句）。

### <a name="return-value"></a>返回值

如果找到匹配记录，则为非零; 否则为0。

### <a name="remarks"></a>备注

`FindNext` 成员函数在当前记录开始搜索，并搜索到记录集的末尾。

如果要在搜索中包括所有记录（而不仅仅是满足特定条件的记录），请使用移动操作之一从记录移动到记录。 若要在表类型记录集中查找记录，请调用 `Seek` 成员函数。

如果未找到与条件匹配的记录，则当前记录指针将无法确定，`FindNext` 将返回零。 如果记录集包含多个满足条件的记录，`FindFirst` 将查找第一个匹配项，`FindNext` 查找下一个匹配项，依此类推。

> [!CAUTION]
>  如果编辑当前记录，请确保先通过调用 `Update` 成员函数来保存更改，然后再移动到另一条记录。 如果移动到另一条记录而不更新，则更改将会丢失，并且不会出现警告。

使用其中一个查找操作与调用 `MoveFirst` 或 `MoveNext`不同，但是，这只是在不指定条件的情况下，将第一个或下一个记录作为当前记录。 可以通过移动操作执行查找操作。

使用 "查找" 操作时，请注意以下事项：

- 如果 `Find` 返回非零值，则不定义当前记录。 在这种情况下，您必须将当前记录指针定位回有效记录。

- 不能使用具有只进滚动快照类型记录集的查找操作。

- 当你搜索包含日期的字段时，你应使用美国日期格式（月-日），即使你未使用 Microsoft Jet 数据库引擎的美国版本;否则，可能找不到匹配的记录。

- 使用 ODBC 数据库和大型动态集时，可能会发现使用 "查找" 操作的速度较慢，尤其是在处理大型记录集时。 可以通过使用带有自定义**ORDERBY**或**WHERE**子句、参数查询或 `CDaoQuerydef` 对象的 SQL 查询来检索特定索引记录，从而提高性能。

相关信息，请参阅 DAO 帮助中的 "FindFirst，FindLast，FindNext，FindPrevious 方法" 主题。

##  <a name="findprev"></a>CDaoRecordset：： FindPrev

调用此成员函数以查找与指定条件匹配的前一条记录。

```
BOOL FindPrev(LPCTSTR lpszFilter);
```

### <a name="parameters"></a>parameters

*lpszFilter*<br/>
用于定位记录的字符串表达式（如 SQL 语句中没有单词**where**的**where**子句）。

### <a name="return-value"></a>返回值

如果找到匹配记录，则为非零; 否则为0。

### <a name="remarks"></a>备注

`FindPrev` 成员函数在当前记录开始其搜索，并向后搜索记录集的开头。

如果要在搜索中包括所有记录（而不仅仅是满足特定条件的记录），请使用移动操作之一从记录移动到记录。 若要在表类型记录集中查找记录，请调用 `Seek` 成员函数。

如果未找到与条件匹配的记录，则当前记录指针将无法确定，`FindPrev` 将返回零。 如果记录集包含多个满足条件的记录，`FindFirst` 将查找第一个匹配项，`FindNext` 查找下一个匹配项，依此类推。

> [!CAUTION]
>  如果编辑当前记录，请确保先通过调用 `Update` 成员函数来保存更改，然后再移动到另一条记录。 如果移动到另一条记录而不更新，则更改将会丢失，并且不会出现警告。

使用其中一个查找操作与调用 `MoveFirst` 或 `MoveNext`不同，但是，这只是在不指定条件的情况下，将第一个或下一个记录作为当前记录。 可以通过移动操作执行查找操作。

使用 "查找" 操作时，请注意以下事项：

- 如果 `Find` 返回非零值，则不定义当前记录。 在这种情况下，您必须将当前记录指针定位回有效记录。

- 不能使用具有只进滚动快照类型记录集的查找操作。

- 当你搜索包含日期的字段时，你应使用美国日期格式（月-日），即使你未使用 Microsoft Jet 数据库引擎的美国版本;否则，可能找不到匹配的记录。

- 使用 ODBC 数据库和大型动态集时，可能会发现使用 "查找" 操作的速度较慢，尤其是在处理大型记录集时。 可以通过使用带有自定义**ORDERBY**或**WHERE**子句、参数查询或 `CDaoQuerydef` 对象的 SQL 查询来检索特定索引记录，从而提高性能。

相关信息，请参阅 DAO 帮助中的 "FindFirst，FindLast，FindNext，FindPrevious 方法" 主题。

##  <a name="getabsoluteposition"></a>CDaoRecordset：： GetAbsolutePosition

返回记录集对象的当前记录的记录号。

```
long GetAbsolutePosition();
```

### <a name="return-value"></a>返回值

从0到记录集中记录数的整数。 对应于记录集中当前记录的序号位置。

### <a name="remarks"></a>备注

基础 DAO 对象的 AbsolutePosition 属性值从零开始;如果设置为0，则表示记录集中的第一条记录。 可以通过调用[GetRecordCount](#getrecordcount)来确定记录集中填充的记录数。 调用 `GetRecordCount` 可能需要一些时间，因为它必须访问所有记录才能确定计数。

如果没有当前记录（如记录集中没有记录时），则返回-1。 如果删除当前记录，则不会定义 AbsolutePosition 属性值，并且 MFC 会在引用它时引发异常。 对于动态集类型的记录集，新记录将添加到序列的末尾。

> [!NOTE]
>  此属性不应用作代理项记录号。 书签仍是保留并返回到给定位置的建议方法，是将当前记录定位到所有类型的 recordset 对象的唯一方法。 特别是，在删除给定记录之前的记录时，该记录的位置会发生更改。 如果重新创建记录集，则对于给定的记录将具有相同的绝对位置，因为记录集中单个记录的顺序不能保证，除非使用**ORDERBY**子句创建了 SQL 语句。

> [!NOTE]
>  此成员函数仅适用于动态集类型和快照类型记录集。

有关相关信息，请参阅 DAO 帮助中的主题 "AbsolutePosition 属性"。

##  <a name="getbookmark"></a>CDaoRecordset：： GetBookmark

调用此成员函数可获取特定记录中的书签值。

```
COleVariant GetBookmark();
```

### <a name="return-value"></a>返回值

返回表示当前记录上书签的值。

### <a name="remarks"></a>备注

当创建或打开 recordset 对象时，它的每个记录都具有唯一的书签（如果支持）。 调用 `CanBookmark` 以确定记录集是否支持书签。

可以通过将书签的值分配给 `COleVariant` 对象来保存当前记录的书签。 若要在移动到不同记录后随时快速返回到该记录，请使用与该 `COleVariant` 对象的值相对应的参数调用 `SetBookmark`。

> [!NOTE]
>  调用[Requery](#requery)会更改 DAO 书签。

有关相关信息，请参阅 DAO 帮助中的主题 "书签属性"。

##  <a name="getcachesize"></a>CDaoRecordset：： GetCacheSize

调用此成员函数以获取缓存的记录数。

```
long GetCacheSize();
```

### <a name="return-value"></a>返回值

一个值，该值指定包含要从 ODBC 数据源本地缓存的数据的动态集类型记录集中的记录数。

### <a name="remarks"></a>备注

数据缓存提高了从远程服务器检索数据的应用程序的性能。 缓存是本地内存中的一个空间，保存最近从服务器检索到的数据，因为在应用程序运行时将再次请求数据。 请求数据时，Microsoft Jet 数据库引擎首先会检查缓存中是否存在请求的数据，而不是从服务器中检索它，这需要更多时间。 不是来自 ODBC 数据源的数据不会保存在缓存中。

任何 ODBC 数据源（如附加表）都可以具有本地缓存。

相关信息，请参阅 DAO 帮助中的主题 "CacheSize，CacheStart Properties"。

##  <a name="getcachestart"></a>CDaoRecordset：： GetCacheStart

调用此成员函数以获取要缓存的记录集中的第一条记录的书签值。

```
COleVariant GetCacheStart();
```

### <a name="return-value"></a>返回值

一个 `COleVariant`，它指定要缓存的记录集中的第一条记录的书签。

### <a name="remarks"></a>备注

Microsoft Jet 数据库引擎在缓存范围内请求缓存中的记录，并从服务器请求缓存范围之外的记录。

> [!NOTE]
>  从缓存检索的记录不反映其他用户对源数据所做的更改。

相关信息，请参阅 DAO 帮助中的主题 "CacheSize，CacheStart Properties"。

##  <a name="getcurrentindex"></a>CDaoRecordset：： GetCurrentIndex

调用此成员函数来确定索引表类型 `CDaoRecordset` 对象中当前使用的索引。

```
CString GetCurrentIndex();
```

### <a name="return-value"></a>返回值

一个 `CString`，其中包含当前与表类型记录集一起使用的索引的名称。 如果未设置索引，则返回空字符串。

### <a name="remarks"></a>备注

此索引是在表类型记录集中对记录进行排序的基础，由[Seek](#seek)成员函数用来定位记录。

一个 `CDaoRecordset` 对象可以有多个索引，但一次只能使用一个索引（尽管[CDaoTableDef](../../mfc/reference/cdaotabledef-class.md)对象可能在其上定义了多个索引）。

有关相关信息，请参阅 DAO 帮助中的主题 "索引对象" 和定义 "当前索引"。

##  <a name="getdatecreated"></a>CDaoRecordset：： GetDateCreated

调用此成员函数以检索创建基表的日期和时间。

```
COleDateTime GetDateCreated();
```

### <a name="return-value"></a>返回值

一个包含基表创建日期和时间的[COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)对象。

### <a name="remarks"></a>备注

日期和时间设置是从创建基表的计算机派生的。

相关信息，请参阅 DAO 帮助中的主题 "DateCreated，LastUpdated Properties"。

##  <a name="getdatelastupdated"></a>CDaoRecordset：： GetDateLastUpdated

调用此成员函数以检索架构的上次更新日期和时间。

```
COleDateTime GetDateLastUpdated();
```

### <a name="return-value"></a>返回值

一个[COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)对象，其中包含上次更新基表结构（架构）的日期和时间。

### <a name="remarks"></a>备注

日期和时间设置派生自上次更新基本表结构（架构）的计算机。

相关信息，请参阅 DAO 帮助中的主题 "DateCreated，LastUpdated Properties"。

##  <a name="getdefaultdbname"></a>CDaoRecordset：： GetDefaultDBName

调用此成员函数以确定此记录集的数据库名称。

```
virtual CString GetDefaultDBName();
```

### <a name="return-value"></a>返回值

一个 `CString`，它包含从中派生此记录集的数据库的路径和名称。

### <a name="remarks"></a>备注

如果创建的记录集没有指向[CDaoDatabase](../../mfc/reference/cdaodatabase-class.md)的指针，则记录集将使用此路径来打开默认数据库。 默认情况下，此函数返回空字符串。 当 ClassWizard 从 `CDaoRecordset`派生新记录集时，它将为你创建此函数。

下面的示例演示如何在字符串中使用双反斜杠（\\\\），这是字符串正确解释所需的。

[!code-cpp[NVC_MFCDatabase#4](../../mfc/codesnippet/cpp/cdaorecordset-class_4.cpp)]

##  <a name="getdefaultsql"></a>CDaoRecordset：： GetDefaultSQL

框架调用此成员函数以获取记录集所基于的默认 SQL 语句。

```
virtual CString GetDefaultSQL();
```

### <a name="return-value"></a>返回值

包含默认 SQL 语句的 `CString`。

### <a name="remarks"></a>备注

这可能是表名或 SQL **SELECT**语句。

您可以通过使用 ClassWizard 声明记录集类来间接定义默认的 SQL 语句，ClassWizard 为您执行此任务。

如果传递 null SQL 字符串以[打开](#open)，则调用此函数来确定记录集的表名称或 SQL。

##  <a name="geteditmode"></a>CDaoRecordset：： GetEditMode

调用此成员函数以确定编辑状态，这是以下值之一：

```
short GetEditMode();
```

### <a name="return-value"></a>返回值

返回一个值，该值指示当前记录的编辑状态。

### <a name="remarks"></a>备注

|值|说明|
|-----------|-----------------|
|`dbEditNone`|没有正在进行的编辑操作。|
|`dbEditInProgress`|已调用 `Edit`。|
|`dbEditAdd`|已调用 `AddNew`。|

有关相关信息，请参阅 DAO 帮助中的主题 "EditMode 属性"。

##  <a name="getfieldcount"></a>CDaoRecordset：： GetFieldCount

调用此成员函数以检索在记录集中定义的字段（列）的数目。

```
short GetFieldCount();
```

### <a name="return-value"></a>返回值

记录集中的字段数。

### <a name="remarks"></a>备注

相关信息，请参阅 DAO 帮助中的 "计数属性" 主题。

##  <a name="getfieldinfo"></a>CDaoRecordset：： Issomapper.getfieldinfo

调用此成员函数以获取有关记录集中的字段的信息。

```
void GetFieldInfo(
    int nIndex,
    CDaoFieldInfo& fieldinfo,
    DWORD dwInfoOptions = AFX_DAO_PRIMARY_INFO);

void GetFieldInfo(
    LPCTSTR lpszName,
    CDaoFieldInfo& fieldinfo,
    DWORD dwInfoOptions = AFX_DAO_PRIMARY_INFO);
```

### <a name="parameters"></a>parameters

*nIndex*<br/>
记录集的字段集合中预定义字段的从零开始的索引，用于按索引查找。

*fieldinfo*<br/>
对[CDaoFieldInfo](../../mfc/reference/cdaofieldinfo-structure.md)结构的引用。

*dwInfoOptions*<br/>
用于指定要检索的记录集的哪些信息的选项。 此处列出了可用的选项，以及它们导致函数返回的内容。 为了获得最佳性能，请仅检索所需的信息级别：

- `AFX_DAO_PRIMARY_INFO` （默认值）名称、类型、大小、属性

- `AFX_DAO_SECONDARY_INFO` 主要信息，加上：序号位置，必需，允许零长度，排序顺序，外名称，源字段，源表

- `AFX_DAO_ALL_INFO` 主要和辅助信息，加上：默认值，验证规则，验证文本

*lpszName*<br/>
字段的名称。

### <a name="remarks"></a>备注

函数的一个版本允许您按索引查找字段。 其他版本允许您按名称查找字段。

有关所返回信息的说明，请参阅[CDaoFieldInfo](../../mfc/reference/cdaofieldinfo-structure.md)结构。 此结构中有与*dwInfoOptions*中的说明中列出的信息项对应的成员。 当你在一个级别请求信息时，还会获取任何以前的级别的信息。

有关相关信息，请参阅 DAO 帮助中的 "属性属性" 主题。

##  <a name="getfieldvalue"></a>CDaoRecordset：： GetFieldValue

调用此成员函数以检索记录集中的数据。

```
virtual void GetFieldValue(
    LPCTSTR lpszName,
    COleVariant& varValue);

virtual void GetFieldValue(
    int nIndex,
    COleVariant& varValue);

virtual COleVariant GetFieldValue(LPCTSTR lpszName);
virtual COleVariant GetFieldValue(int nIndex);
```

### <a name="parameters"></a>parameters

*lpszName*<br/>
指向包含字段名称的字符串的指针。

*varValue*<br/>
对将存储字段值的 `COleVariant` 对象的引用。

*nIndex*<br/>
记录集的字段集合中的字段的从零开始的索引，用于按索引查找。

### <a name="return-value"></a>返回值

返回值 `GetFieldValue` 的两个版本返回一个[COleVariant](../../mfc/reference/colevariant-class.md)对象，该对象包含字段的值。

### <a name="remarks"></a>备注

可以按名称或序号位置查找字段。

> [!NOTE]
>  调用此成员函数的一个版本作为参数，而不是调用返回 `COleVariant` 对象的版本，则更有效的方法是调用此成员 `COleVariant` 函数的一个版本。 为实现向后兼容性而保留了此函数的后一种版本。

使用 `GetFieldValue` 和[SetFieldValue](#setfieldvalue)在运行时动态绑定字段，而不是使用[DoFieldExchange](#dofieldexchange)机制静态绑定列。

可以结合 `GetFieldValue` 和 `DoFieldExchange` 机制来提高性能。 例如，使用 `GetFieldValue` 按需检索只需要的值，并将调用分配给接口中的 "更多信息" 按钮。

有关相关信息，请参阅 DAO 帮助中的主题 "字段对象" 和 "值属性"。

##  <a name="getindexcount"></a>CDaoRecordset：： GetIndexCount

调用此成员函数可确定表类型记录集中可用的索引数。

```
short GetIndexCount();
```

### <a name="return-value"></a>返回值

表类型记录集中的索引数。

### <a name="remarks"></a>备注

`GetIndexCount` 有助于遍历记录集中的所有索引。 为此，请将 `GetIndexCount` 与[GetIndexInfo](#getindexinfo)结合使用。 如果对动态集类型或快照类型的记录集调用此成员函数，MFC 会引发异常。

有关相关信息，请参阅 DAO 帮助中的 "属性属性" 主题。

##  <a name="getindexinfo"></a>CDaoRecordset：： GetIndexInfo

调用此成员函数可获取有关在基于记录集的基表中定义的索引的各种信息。

```
void GetIndexInfo(
    int nIndex,
    CDaoIndexInfo& indexinfo,
    DWORD dwInfoOptions = AFX_DAO_PRIMARY_INFO);

void GetIndexInfo(
    LPCTSTR lpszName,
    CDaoIndexInfo& indexinfo,
    DWORD dwInfoOptions = AFX_DAO_PRIMARY_INFO);
```

### <a name="parameters"></a>parameters

*nIndex*<br/>
表的索引集合中从零开始的索引，用于按数字位置查找。

*indexinfo*<br/>
对[CDaoIndexInfo](../../mfc/reference/cdaoindexinfo-structure.md)结构的引用。

*dwInfoOptions*<br/>
用于指定要检索的索引信息的选项。 此处列出了可用的选项，以及它们导致函数返回的内容。 为了获得最佳性能，请仅检索所需的信息级别：

- `AFX_DAO_PRIMARY_INFO` （默认值）名称、字段信息、字段

- `AFX_DAO_SECONDARY_INFO` 主要信息，外加： Primary、Unique、聚集、IgnoreNulls、Required、Foreign

- `AFX_DAO_ALL_INFO` 主要和辅助信息，以及：非重复计数

*lpszName*<br/>
一个指针，指向索引对象的名称，用于按名称进行查找。

### <a name="remarks"></a>备注

函数的一个版本可让你按索引在集合中的位置进行查找。 其他版本允许您按名称查找索引。

有关所返回信息的说明，请参阅[CDaoIndexInfo](../../mfc/reference/cdaoindexinfo-structure.md)结构。 此结构中有与*dwInfoOptions*中的说明中列出的信息项对应的成员。 当你在一个级别请求信息时，还会获取任何以前的级别的信息。

有关相关信息，请参阅 DAO 帮助中的 "属性属性" 主题。

##  <a name="getlastmodifiedbookmark"></a>CDaoRecordset：： GetLastModifiedBookmark

调用此成员函数以检索最近添加或更新的记录的书签。

```
COleVariant GetLastModifiedBookmark();
```

### <a name="return-value"></a>返回值

包含书签的 `COleVariant`，指示最近添加或更改的记录。

### <a name="remarks"></a>备注

当创建或打开 recordset 对象时，它的每个记录都具有唯一的书签（如果支持）。 调用[GetBookmark](#getbookmark)以确定记录集是否支持书签。 如果记录集不支持书签，则会引发 `CDaoException`。

添加记录时，它将显示在记录集的末尾，而不是当前记录。 若要使新记录成为最新记录，请调用 `GetLastModifiedBookmark`，然后调用 `SetBookmark` 以返回到新添加的记录。

有关相关信息，请参阅 DAO 帮助中的主题 "LastModified 属性"。

##  <a name="getlockingmode"></a>CDaoRecordset：： GetLockingMode

调用此成员函数以确定对记录集有效的锁定类型。

```
BOOL GetLockingMode();
```

### <a name="return-value"></a>返回值

如果锁定类型是保守的，则为非零; 否则为0。

### <a name="remarks"></a>备注

当悲观锁定有效时，在调用[Edit](#edit)成员函数时，将立即锁定包含正在编辑的记录的数据页。 在调用[Update](#update)或[Close](#close)成员函数或任何移动或查找操作时，将解除锁定页面。

当乐观锁定有效时，包含记录的数据页仅会锁定，同时将用 `Update` 成员函数更新记录。

使用 ODBC 数据源时，锁定模式始终处于乐观状态。

相关信息，请参阅 DAO 帮助中的主题 "LockEdits 属性" 和 "多用户应用程序中的锁定行为"。

##  <a name="getname"></a>CDaoRecordset：： GetName

调用此成员函数以检索记录集的名称。

```
CString GetName();
```

### <a name="return-value"></a>返回值

包含记录集名称的 `CString`。

### <a name="remarks"></a>备注

记录集的名称必须以字母开头，并且最多可以包含40个字符。 它可以包含数字和下划线字符，但不能包含标点或空格。

有关相关信息，请参阅 DAO 帮助中的主题 "名称属性"。

##  <a name="getparamvalue"></a>CDaoRecordset：： GetParamValue

调用此成员函数以检索存储在基础 DAOParameter 对象中的指定参数的当前值。

```
virtual COleVariant GetParamValue(int nIndex);
virtual COleVariant GetParamValue(LPCTSTR lpszName);
```

### <a name="parameters"></a>parameters

*nIndex*<br/>
基础 DAOParameter 对象中参数的数字位置。

*lpszName*<br/>
需要其值的参数的名称。

### <a name="return-value"></a>返回值

包含参数值的[COleVariant](../../mfc/reference/colevariant-class.md)类的对象。

### <a name="remarks"></a>备注

您可以按名称或其在集合中的数字位置访问参数。

有关相关信息，请参阅 DAO 帮助中的主题 "参数对象"。

##  <a name="getpercentposition"></a>CDaoRecordset：： GetPercentPosition

使用动态集类型或快照类型记录集时，如果在完全填充记录集之前调用 `GetPercentPosition`，则移动量是相对于通过调用[GetRecordCount](#getrecordcount)指定的所访问的记录数。

```
float GetPercentPosition();
```

### <a name="return-value"></a>返回值

介于0到100之间的一个数字，指示记录集中的当前记录相对于记录集中的百分比的近似位置。

### <a name="remarks"></a>备注

您可以通过调用[MoveLast](#movelast)来完成所有记录集的填充，从而移到最后一条记录，但这可能需要很长时间。

您可以对所有这三种类型的记录集对象（包括没有索引的表）调用 `GetPercentPosition`。 但是，不能对只进滚动快照或对外部数据库的传递查询打开的记录集调用 `GetPercentPosition`。 如果没有当前记录，或当前记录已被删除，则会引发 `CDaoException`。

有关相关信息，请参阅 DAO 帮助中的主题 "PercentPosition 属性"。

##  <a name="getrecordcount"></a>CDaoRecordset：： GetRecordCount

调用此成员函数以找出记录集中已访问的记录数。

```
long GetRecordCount();
```

### <a name="return-value"></a>返回值

返回 recordset 对象中访问的记录数。

### <a name="remarks"></a>备注

`GetRecordCount` 不指示动态集类型或快照类型记录集中包含多少记录，直到所有记录都已被访问。 此成员函数调用可能需要很长时间才能完成。

当最后一条记录被访问后，返回值指示记录集中未删除记录的总数。 若要强制访问最后一条记录，请调用该记录集的 `MoveLast` 或 `FindLast` 成员函数。 你还可以使用 SQL 计数来确定查询将返回的记录的大致数目。

当应用程序在动态集类型的记录集中删除记录时，`GetRecordCount` 的返回值将减少。 但是，在当前记录被定位到已删除的记录之前，其他用户删除的记录不会 `GetRecordCount` 反映。 如果执行的事务影响记录计数，随后回滚事务，则 `GetRecordCount` 将不会反映剩余记录的实际数量。

快照类型记录集中 `GetRecordCount` 的值不受基础表中的更改的影响。

表类型记录集中 `GetRecordCount` 的值反映了表中记录的大致数量，并会在添加和删除表记录时立即受到影响。

不包含任何记录的记录集返回值0。 使用附加表或 ODBC 数据库时，`GetRecordCount` 始终返回-1。 对记录集调用 `Requery` 成员函数将重置 `GetRecordCount` 的值，就像重新执行查询一样。

有关相关信息，请参阅 DAO 帮助中的主题 "RecordCount 属性"。

##  <a name="getsql"></a>CDaoRecordset：： GetSQL

调用此成员函数以获取在打开时用于选择记录集的记录的 SQL 语句。

```
CString GetSQL() const;
```

### <a name="return-value"></a>返回值

包含 SQL 语句的 `CString`。

### <a name="remarks"></a>备注

这通常是一个 SQL **SELECT**语句。

`GetSQL` 返回的字符串通常不同于你可能已传递给[开放式](#open)成员函数的*lpszSQL*参数中的记录集的任何字符串。 这是因为记录集基于您传递到 `Open`的内容、您使用 ClassWizard 指定的内容以及您在[m_strFilter](#m_strfilter)和[m_strSort](#m_strsort)数据成员中指定的内容来构造完整的 SQL 语句。

> [!NOTE]
>  仅在调用 `Open`之后调用此成员函数。

有关相关信息，请参阅 DAO 帮助中的 "SQL 属性" 主题。

##  <a name="gettype"></a>CDaoRecordset：： GetType

打开记录集后调用此成员函数以确定 recordset 对象的类型。

```
short GetType();
```

### <a name="return-value"></a>返回值

以下值之一，指示记录集的类型：

- `dbOpenTable` 表类型记录集

- `dbOpenDynaset` 动态集类型的记录集

- `dbOpenSnapshot` 快照类型记录集

### <a name="remarks"></a>备注

有关相关信息，请参阅 DAO 帮助中的 "类型属性" 主题。

##  <a name="getvalidationrule"></a>CDaoRecordset：： GetValidationRule

调用此成员函数以确定用于验证数据的规则。

```
CString GetValidationRule();
```

### <a name="return-value"></a>返回值

一个 `CString` 对象，它包含一个值，用于在记录更改或添加到表中时对记录中的数据进行验证。

### <a name="remarks"></a>备注

此规则基于文本，并在每次更改基础表时应用。 如果数据不是合法的，MFC 会引发异常。 返回的错误消息是基础字段对象的 "有效性文本" 属性的文本，如果已指定，则为; 否则为基础字段对象的 "有效性规则" 属性所指定的表达式文本。 可以调用[GetValidationText](#getvalidationtext)来获取错误消息的文本。

例如，记录中需要月份日期的字段可能有一个验证规则，如 "DAY 介于1和31之间"。

有关相关信息，请参阅 DAO 帮助中的主题 "有效性规则属性"。

##  <a name="getvalidationtext"></a>CDaoRecordset：： GetValidationText

调用此成员函数以检索基础字段对象的 "有效性文本" 属性的文本。

```
CString GetValidationText();
```

### <a name="return-value"></a>返回值

一个 `CString` 对象，该对象包含在字段值不满足基础字段对象的验证规则时显示的消息文本。

### <a name="remarks"></a>备注

有关相关信息，请参阅 DAO 帮助中的主题 "有效性文本属性"。

##  <a name="isbof"></a>CDaoRecordset：： IsBOF

在从记录滚动到记录之前调用此成员函数，以了解您是否已离开记录集的第一条记录。

```
BOOL IsBOF() const;
```

### <a name="return-value"></a>返回值

如果记录集不包含任何记录，或者在第一条记录前向后滚动，则为非零值;否则为0。

### <a name="remarks"></a>备注

还可以调用 `IsBOF` 和 `IsEOF` 来确定记录集是否包含任何记录或为空。 调用 `Open`后，如果记录集不包含任何记录，则 `IsBOF` 返回非零值。 打开至少包含一条记录的记录集时，第一条记录为当前记录并且 `IsBOF` 返回0。

如果第一条记录是当前记录并且您调用 `MovePrev`，`IsBOF` 随后将返回非零值。 如果 `IsBOF` 返回非零值并且您调用 `MovePrev`，则将引发异常。 如果 `IsBOF` 返回非零值，则不定义当前记录，并且任何需要当前记录的操作都将导致异常。

特定方法对 `IsBOF` 和 `IsEOF` 设置的影响：

- 在内部调用 `Open*` 使得记录集中的第一条记录通过调用 `MoveFirst`来记录当前记录。 因此，对一组空记录调用 `Open` 会导致 `IsBOF` 并 `IsEOF` 返回非零值。 （有关失败的 `MoveFirst` 或 `MoveLast` 调用的行为，请参阅下表。）

- 成功定位记录的所有移动操作都将导致 `IsBOF` 和 `IsEOF` 返回0。

- 后跟成功插入新记录的 `Update` 调用的 `AddNew` 调用将导致 `IsBOF` 返回0，但前提是 `IsEOF` 已经为非零值。 `IsEOF` 的状态将始终保持不变。 如 Microsoft Jet 数据库引擎所定义的，空记录集的当前记录指针位于文件的末尾，因此在当前记录的后面插入任何新记录。

- 任何 `Delete` 调用，即使它仅从记录集中删除剩余记录，也不会更改 `IsBOF` 或 `IsEOF`的值。

此表显示了允许 `IsBOF`/ `IsEOF`的不同组合的移动操作。

||MoveFirst、MoveLast|MovePrev<br /><br /> 移动 < 0|移动0|MoveNext<br /><br /> 移动 > 0|
|------|-------------------------|-----------------------------|------------|-----------------------------|
|`IsBOF`= 非零，<br /><br /> `IsEOF`=0|允许|异常|异常|允许|
|`IsBOF`=0,<br /><br /> `IsEOF`= 非零|允许|允许|异常|异常|
|均为非零|异常|异常|异常|异常|
|均为0|允许|允许|允许|允许|

允许移动操作并不意味着操作将成功定位记录。 它仅指示允许执行指定的移动操作，并且不会生成异常。 由于尝试移动，`IsBOF` 和 `IsEOF` 成员函数的值可能会更改。

下表显示了在 `IsBOF` 和 `IsEOF` 设置的值上没有找到记录的移动操作的效果。

||IsBOF|IsEOF|
|------|-----------|-----------|
|`MoveFirst`、`MoveLast`|非零|非零|
|`Move` 0|没有变化|没有变化|
|`MovePrev`，`Move` < 0|非零|没有变化|
|`MoveNext`，`Move` > 0|没有变化|非零|

相关信息，请参阅 DAO 帮助中的主题 "BOF，EOF Properties"。

##  <a name="isdeleted"></a>CDaoRecordset：： IsDeleted

调用此成员函数以确定当前记录是否已被删除。

```
BOOL IsDeleted() const;
```

### <a name="return-value"></a>返回值

如果记录集位于已删除记录上，则为非零值;否则为0。

### <a name="remarks"></a>备注

如果滚动到某一记录并且 `IsDeleted` 返回 TRUE （非零），则必须滚动到其他记录，然后才能执行任何其他记录集操作。

> [!NOTE]
>  不需要检查快照或表类型记录集中记录的已删除状态。 由于不能从快照中删除记录，因此无需调用 `IsDeleted`。 对于表类型记录集，已删除的记录实际上会从记录集中删除。 删除记录后，无论是由您、其他用户或在其他记录集中，都无法向后滚动到该记录。 因此，无需调用 `IsDeleted`。

从动态集中删除记录时，该记录将从记录集中删除，并且无法向后滚动到该记录。 但是，如果动态集中的记录由其他用户或在基于同一个表的另一个记录集中删除，则当你稍后滚动到该记录时，`IsDeleted` 将返回 TRUE。

有关相关信息，请参阅 DAO 帮助中的 "删除方法"、"LastModified 属性" 和 "EditMode 属性" 主题。

##  <a name="iseof"></a>CDaoRecordset：： IsEOF

在从记录滚动到记录时调用此成员函数，以了解您是否超出了记录集的最后一条记录。

```
BOOL IsEOF() const;
```

### <a name="return-value"></a>返回值

如果记录集不包含任何记录，或者滚动到最后一条记录之外，则为非零值;否则为0。

### <a name="remarks"></a>备注

您还可以调用 `IsEOF` 来确定记录集是否包含任何记录或为空。 调用 `Open`后，如果记录集不包含任何记录，则 `IsEOF` 返回非零值。 打开至少包含一条记录的记录集时，第一条记录为当前记录并且 `IsEOF` 返回0。

如果在调用 `MoveNext`时，最后一条记录是当前记录，`IsEOF` 随后将返回非零值。 如果 `IsEOF` 返回非零值并且您调用 `MoveNext`，则将引发异常。 如果 `IsEOF` 返回非零值，则不定义当前记录，并且任何需要当前记录的操作都将导致异常。

特定方法对 `IsBOF` 和 `IsEOF` 设置的影响：

- 在内部调用 `Open` 使得记录集中的第一条记录通过调用 `MoveFirst`来记录当前记录。 因此，对一组空记录调用 `Open` 会导致 `IsBOF` 并 `IsEOF` 返回非零值。 （有关失败的 `MoveFirst` 调用的行为，请参阅下表。）

- 成功定位记录的所有移动操作都将导致 `IsBOF` 和 `IsEOF` 返回0。

- 后跟成功插入新记录的 `Update` 调用的 `AddNew` 调用将导致 `IsBOF` 返回0，但前提是 `IsEOF` 已经为非零值。 `IsEOF` 的状态将始终保持不变。 如 Microsoft Jet 数据库引擎所定义的，空记录集的当前记录指针位于文件的末尾，因此在当前记录的后面插入任何新记录。

- 任何 `Delete` 调用，即使它仅从记录集中删除剩余记录，也不会更改 `IsBOF` 或 `IsEOF`的值。

此表显示了允许 `IsBOF`/ `IsEOF`的不同组合的移动操作。

||MoveFirst、MoveLast|MovePrev<br /><br /> 移动 < 0|移动0|MoveNext<br /><br /> 移动 > 0|
|------|-------------------------|-----------------------------|------------|-----------------------------|
|`IsBOF`= 非零，<br /><br /> `IsEOF`=0|允许|异常|异常|允许|
|`IsBOF`=0,<br /><br /> `IsEOF`= 非零|允许|允许|异常|异常|
|均为非零|异常|异常|异常|异常|
|均为0|允许|允许|允许|允许|

允许移动操作并不意味着操作将成功定位记录。 它仅指示允许执行指定的移动操作，并且不会生成异常。 由于尝试移动，`IsBOF` 和 `IsEOF` 成员函数的值可能会更改。

下表显示了在 `IsBOF` 和 `IsEOF` 设置的值上没有找到记录的移动操作的效果。

||IsBOF|IsEOF|
|------|-----------|-----------|
|`MoveFirst`、`MoveLast`|非零|非零|
|`Move` 0|没有变化|没有变化|
|`MovePrev`，`Move` < 0|非零|没有变化|
|`MoveNext`，`Move` > 0|没有变化|非零|

相关信息，请参阅 DAO 帮助中的主题 "BOF，EOF Properties"。

##  <a name="isfielddirty"></a>CDaoRecordset：： IsFieldDirty

调用此成员函数以确定是否已将动态集的指定字段数据成员标记为 "已更新" （已更改）。

```
BOOL IsFieldDirty(void* pv);
```

### <a name="parameters"></a>parameters

*函数*<br/>
指向要检查其状态的字段数据成员的指针，或为 NULL 以确定是否有任何字段处于脏状态。

### <a name="return-value"></a>返回值

如果将指定字段数据成员标记为已更新，则为非零值;否则为0。

### <a name="remarks"></a>备注

当通过调用 `CDaoRecordset` 的 `Update` 成员函数（在调用了 `Edit` 或 `AddNew`）更新当前记录时，所有更新的字段数据成员中的数据都将传输到数据源中的记录。 了解此知识后，您可以执行更多步骤，如 unflagging 字段数据成员标记列，使其不会写入数据源。

`IsFieldDirty` 是通过 `DoFieldExchange`实现的。

##  <a name="isfieldnull"></a>CDaoRecordset：： IsFieldNull

调用此成员函数以确定是否已将记录集的指定字段数据成员标记为 Null。

```
BOOL IsFieldNull(void* pv);
```

### <a name="parameters"></a>parameters

*函数*<br/>
指向要检查其状态的字段数据成员的指针，或为 NULL 以确定是否有任何字段为 Null。

### <a name="return-value"></a>返回值

如果将指定字段数据成员标记为 Null，则为非零值;否则为0。

### <a name="remarks"></a>备注

（在数据库术语中，Null 表示 "无值"，而不是中C++的 null。）如果将字段数据成员标记为 Null，则将其解释为当前记录中没有值的列。

> [!NOTE]
>  在某些情况下，使用 `IsFieldNull` 可能效率低下，如以下代码示例所示：

[!code-cpp[NVC_MFCDatabase#5](../../mfc/codesnippet/cpp/cdaorecordset-class_5.cpp)]

> [!NOTE]
>  如果使用的是动态记录绑定，而不是从 `CDaoRecordset`派生，请确保使用 VT_NULL，如示例中所示。

##  <a name="isfieldnullable"></a>CDaoRecordset：： IsFieldNullable

调用此成员函数以确定指定的字段数据成员是否为 "nullable" （可以设置为 Null 值;C++ Null 与 null 不同，后者在数据库术语中意味着 "无值"）。

```
BOOL IsFieldNullable(void* pv);
```

### <a name="parameters"></a>parameters

*函数*<br/>
指向要检查其状态的字段数据成员的指针，或为 NULL 以确定是否有任何字段为 Null。

### <a name="return-value"></a>返回值

如果指定的字段数据成员可以为 Null，则为非零值;否则为0。

### <a name="remarks"></a>备注

不能为 Null 的字段必须具有值。 如果在添加或更新记录时尝试将此类字段设置为 Null，则数据源拒绝添加或更新，并且 `Update` 会引发异常。 调用 `Update`时（而不是调用 `SetFieldNull`时），将发生异常。

##  <a name="isopen"></a>CDaoRecordset：： IsOpen

调用此成员函数以确定记录集是否已打开。

```
BOOL IsOpen() const;
```

### <a name="return-value"></a>返回值

如果以前调用了 recordset 对象的 `Open` 或 `Requery` 成员函数但尚未关闭记录集，则为非零值;否则为0。

### <a name="remarks"></a>备注

##  <a name="m_bcheckcachefordirtyfields"></a>CDaoRecordset：： m_bCheckCacheForDirtyFields

包含一个标志，该标志指示是否将缓存字段自动标记为 "已更新" 和 "Null"。

### <a name="remarks"></a>备注

标志默认为 TRUE。 此数据成员中的设置控制整个双缓冲机制。 如果将标志设置为 TRUE，则可以使用 DFX 机制逐个字段地禁用缓存。 如果将标志设置为 FALSE，则必须调用 `SetFieldDirty` 并 `SetFieldNull` 自己。

在调用 `Open`之前设置此数据成员。 此机制主要是为了便于使用。 由于进行了更改，因此性能可能会降低。

##  <a name="m_nfields"></a>CDaoRecordset：： m_nFields

包含记录集类中的字段数据成员数，以及从数据源中记录集选择的列数。

### <a name="remarks"></a>备注

Recordset 类的构造函数必须初始化具有正确的静态绑定字段数的 `m_nFields`。 当你使用它声明记录集类时，ClassWizard 会为你编写此初始化。 你还可以手动编写。

框架使用此数字来管理字段数据成员与数据源中当前记录的对应列之间的交互。

> [!NOTE]
>  此数字必须与在使用参数 `CDaoFieldExchange::outputColumn`调用 `SetFieldType` 后 `DoFieldExchange` 中注册的输出列的数量相对应。

可以通过 `CDaoRecordset::GetFieldValue` 和 `CDaoRecordset::SetFieldValue`以动态方式绑定列。 如果这样做，则不需要增加 `m_nFields` 中的计数，以反映 `DoFieldExchange` 成员函数中的 DFX 函数调用数。

##  <a name="m_nparams"></a>CDaoRecordset：： m_nParams

包含记录集类中参数数据成员的数目-与记录集的查询传递的参数的数目。

### <a name="remarks"></a>备注

如果记录集类有任何参数数据成员，则该类的构造函数必须用正确的数字初始化*m_nParams* 。 *M_nParams*的值默认为0。 如果添加参数数据成员（必须手动执行此操作），则还必须在类构造函数中手动添加初始化，以反映参数的数目（至少必须与*m_strFilter*中的 "" 占位符的数目或*m_strSort*字符串）相同。

参数化记录集的查询时，框架使用此数字。

> [!NOTE]
>  此数字必须与在使用参数 `CFieldExchange::param`调用 `SetFieldType` 后 `DoFieldExchange` 中注册的 "params" 的数量相对应。

有关相关信息，请参阅 DAO 帮助中的主题 "参数对象"。

##  <a name="m_pdaorecordset"></a>CDaoRecordset：： m_pDAORecordset

包含指向 `CDaoRecordset` 对象基础上的 DAO 记录集对象的 OLE 接口的指针。

### <a name="remarks"></a>备注

如果需要直接访问 DAO 界面，请使用此指针。

有关相关信息，请参阅 DAO 帮助中的主题 "Recordset 对象"。

##  <a name="m_pdatabase"></a>CDaoRecordset：： m_pDatabase

包含一个指向 `CDaoDatabase` 对象的指针，该对象通过该对象将记录集连接到数据源。

### <a name="remarks"></a>备注

此变量通过两种方式进行设置。 通常，当构造 recordset 对象时，会将指针传递到已打开的 `CDaoDatabase` 对象。 如果改为传递 NULL，`CDaoRecordset` 将为您创建一个 `CDaoDatabase` 对象并将其打开。 在任一情况下，`CDaoRecordset` 都将指针存储在此变量中。

通常不会直接使用存储在 `m_pDatabase`中的指针。 但是，如果你将自己的扩展写入 `CDaoRecordset`，则可能需要使用指针。 例如，如果你引发自己的 `CDaoException`，则可能需要指针。

有关相关信息，请参阅 DAO 帮助中的主题 "数据库对象"。

##  <a name="m_strfilter"></a>CDaoRecordset：： m_strFilter

包含一个字符串，该字符串用于构造 SQL 语句的**WHERE**子句。

### <a name="remarks"></a>备注

它不**包含用于筛选记录集的保留**字。 使用此数据成员不适用于表类型记录集。 使用 `CDaoQueryDef` 指针打开记录集时，使用 `m_strFilter` 无效。

在筛选包含日期的字段时使用美国日期格式（月-日），即使您未使用美国版本的 Microsoft Jet 数据库引擎，否则，可能无法按预期筛选数据。

有关相关信息，请参阅 DAO 帮助中的 "筛选属性" 主题。

##  <a name="m_strsort"></a>CDaoRecordset：： m_strSort

包含一个字符串，该字符串包含没有保留字词**ORDERBY**的 SQL 语句的**ORDERBY**子句。

### <a name="remarks"></a>备注

可以对动态集和快照类型的记录集对象进行排序。

不能对表类型的 recordset 对象进行排序。 若要确定表类型记录集的排序顺序，请调用[SetCurrentIndex](#setcurrentindex)。

使用 `CDaoQueryDef` 指针打开记录集时，使用*m_strSort*无效。

有关相关信息，请参阅 DAO 帮助中的主题 "Sort 属性"。

##  <a name="move"></a>CDaoRecordset：： Move

调用此成员函数以将记录集从当前记录*lRows*记录。

```
virtual void Move(long lRows);
```

### <a name="parameters"></a>parameters

*lRows*<br/>
向前或向后移动的记录数。 正值表示向前移动，直到记录集的末尾。 负值将向后移动。

### <a name="remarks"></a>备注

您可以向前或向后移动。 `Move( 1 )` 等效于 `MoveNext`，`Move( -1 )` 等效于 `MovePrev`。

> [!CAUTION]
>  如果记录集没有记录，则调用任何 `Move` 函数将引发异常。 通常，在移动操作之前调用 `IsBOF` 和 `IsEOF`，以确定记录集是否有任何记录。 调用 `Open` 或 `Requery`后，调用 `IsBOF` 或 `IsEOF`。

> [!NOTE]
>  如果滚动了记录集的开头或结尾（`IsBOF` 或 `IsEOF` 返回非零值），则对 `Move` 的调用将引发 `CDaoException`。

> [!NOTE]
>  如果在更新或添加当前记录时调用任何 `Move` 函数，则更新将丢失且不发出警告。

当对只进滚动快照调用 `Move` 时， *lRows*参数必须是正整数，并且不允许使用书签，因此只能向前移动。

若要使记录集中的第一条、最后一条、下一条记录或上一条记录成为当前记录，请调用 `MoveFirst`、`MoveLast`、`MoveNext`或 `MovePrev` 成员函数。

有关相关信息，请参阅 DAO 帮助中的主题 "Move Method" 和 "MoveFirst，MoveLast，MoveNext，MovePrevious method"。

##  <a name="movefirst"></a>CDaoRecordset：： MoveFirst

调用此成员函数，使记录集（如果有）中的第一条记录成为当前记录。

```
void MoveFirst();
```

### <a name="remarks"></a>备注

打开记录集之后，无需立即调用 `MoveFirst`。 此时，第一条记录（如果有）将自动成为当前记录。

> [!CAUTION]
>  如果记录集没有记录，则调用任何 `Move` 函数将引发异常。 通常，在移动操作之前调用 `IsBOF` 和 `IsEOF`，以确定记录集是否有任何记录。 调用 `Open` 或 `Requery`后，调用 `IsBOF` 或 `IsEOF`。

> [!NOTE]
>  如果在更新或添加当前记录时调用任何 `Move` 函数，则更新将丢失且不发出警告。

使用 `Move` 函数可在记录之间移动，而无需应用条件。 使用 "查找" 操作在满足特定条件的动态集类型或快照类型 recordset 对象中查找记录。 若要在表类型 recordset 对象中查找记录，请调用 `Seek`。

如果记录集引用表类型的记录集，则移动将遵循该表的当前索引。 您可以使用基础 DAO 对象的 Index 属性设置当前索引。 如果未设置当前索引，则返回的记录的顺序是不确定的。

如果对基于 SQL 查询或 querydef 的记录集对象调用 `MoveLast`，则将强制完成查询，并完全填充记录集对象。

不能使用只进滚动快照调用 `MoveFirst` 或 `MovePrev` 成员函数。

若要将记录集对象中的当前记录的位置向前或向后移动特定数量的记录，请调用 `Move`。

有关相关信息，请参阅 DAO 帮助中的主题 "Move Method" 和 "MoveFirst，MoveLast，MoveNext，MovePrevious method"。

##  <a name="movelast"></a>CDaoRecordset：： MoveLast

调用此成员函数以使记录集中的最后一条记录（如果有）成为当前记录。

```
void MoveLast();
```

### <a name="remarks"></a>备注

> [!CAUTION]
>  如果记录集没有记录，则调用任何 `Move` 函数将引发异常。 通常，在移动操作之前调用 `IsBOF` 和 `IsEOF`，以确定记录集是否有任何记录。 调用 `Open` 或 `Requery`后，调用 `IsBOF` 或 `IsEOF`。

> [!NOTE]
>  如果在更新或添加当前记录时调用任何 `Move` 函数，则更新将丢失且不发出警告。

使用 `Move` 函数可在记录之间移动，而无需应用条件。 使用 "查找" 操作在满足特定条件的动态集类型或快照类型 recordset 对象中查找记录。 若要在表类型 recordset 对象中查找记录，请调用 `Seek`。

如果记录集引用表类型的记录集，则移动将遵循该表的当前索引。 您可以使用基础 DAO 对象的 Index 属性设置当前索引。 如果未设置当前索引，则返回的记录的顺序是不确定的。

如果对基于 SQL 查询或 querydef 的记录集对象调用 `MoveLast`，则将强制完成查询，并完全填充记录集对象。

若要将记录集对象中的当前记录的位置向前或向后移动特定数量的记录，请调用 `Move`。

有关相关信息，请参阅 DAO 帮助中的主题 "Move Method" 和 "MoveFirst，MoveLast，MoveNext，MovePrevious method"。

##  <a name="movenext"></a>CDaoRecordset：： MoveNext

调用此成员函数以使记录集中的下一条记录成为当前记录。

```
void MoveNext();
```

### <a name="remarks"></a>备注

建议在尝试移动到上一条记录之前调用 `IsBOF`。 如果 `IsBOF` 返回非零值，则对 `MovePrev` 的调用将引发 `CDaoException`，这表示你已在第一条记录之前滚动或记录集未选择任何记录。

> [!CAUTION]
>  如果记录集没有记录，则调用任何 `Move` 函数将引发异常。 通常，在移动操作之前调用 `IsBOF` 和 `IsEOF`，以确定记录集是否有任何记录。 调用 `Open` 或 `Requery`后，调用 `IsBOF` 或 `IsEOF`。

> [!NOTE]
>  如果在更新或添加当前记录时调用任何 `Move` 函数，则更新将丢失且不发出警告。

使用 `Move` 函数可在记录之间移动，而无需应用条件。 使用 "查找" 操作在满足特定条件的动态集类型或快照类型 recordset 对象中查找记录。 若要在表类型 recordset 对象中查找记录，请调用 `Seek`。

如果记录集引用表类型的记录集，则移动将遵循该表的当前索引。 您可以使用基础 DAO 对象的 Index 属性设置当前索引。 如果未设置当前索引，则返回的记录的顺序是不确定的。

若要将记录集对象中的当前记录的位置向前或向后移动特定数量的记录，请调用 `Move`。

有关相关信息，请参阅 DAO 帮助中的主题 "Move Method" 和 "MoveFirst，MoveLast，MoveNext，MovePrevious method"。

##  <a name="moveprev"></a>CDaoRecordset：： MovePrev

调用此成员函数以使记录集中的上一记录成为当前记录。

```
void MovePrev();
```

### <a name="remarks"></a>备注

建议在尝试移动到上一条记录之前调用 `IsBOF`。 如果 `IsBOF` 返回非零值，则对 `MovePrev` 的调用将引发 `CDaoException`，这表示你已在第一条记录之前滚动或记录集未选择任何记录。

> [!CAUTION]
>  如果记录集没有记录，则调用任何 `Move` 函数将引发异常。 通常，在移动操作之前调用 `IsBOF` 和 `IsEOF`，以确定记录集是否有任何记录。 调用 `Open` 或 `Requery`后，调用 `IsBOF` 或 `IsEOF`。

> [!NOTE]
>  如果在更新或添加当前记录时调用任何 `Move` 函数，则更新将丢失且不发出警告。

使用 `Move` 函数可在记录之间移动，而无需应用条件。 使用 "查找" 操作在满足特定条件的动态集类型或快照类型 recordset 对象中查找记录。 若要在表类型 recordset 对象中查找记录，请调用 `Seek`。

如果记录集引用表类型的记录集，则移动将遵循该表的当前索引。 您可以使用基础 DAO 对象的 Index 属性设置当前索引。 如果未设置当前索引，则返回的记录的顺序是不确定的。

不能使用只进滚动快照调用 `MoveFirst` 或 `MovePrev` 成员函数。

若要将记录集对象中的当前记录的位置向前或向后移动特定数量的记录，请调用 `Move`。

有关相关信息，请参阅 DAO 帮助中的主题 "Move Method" 和 "MoveFirst，MoveLast，MoveNext，MovePrevious method"。

##  <a name="open"></a>CDaoRecordset：： Open

您必须调用此成员函数以检索记录集的记录。

```
virtual void Open(
    int nOpenType = AFX_DAO_USE_DEFAULT_TYPE,
    LPCTSTR lpszSQL = NULL,
    int nOptions = 0);

virtual void Open(
    CDaoTableDef* pTableDef,
    int nOpenType = dbOpenTable,
    int nOptions = 0);

virtual void Open(
    CDaoQueryDef* pQueryDef,
    int nOpenType = dbOpenDynaset,
    int nOptions = 0);
```

### <a name="parameters"></a>parameters

*nOpenType*<br/>
以下值之一：

- 使用双向滚动 `dbOpenDynaset` 动态集类型的记录集。 这是默认值。

- 使用双向滚动 `dbOpenTable` 表类型记录集。

- 使用双向滚动 `dbOpenSnapshot` 快照类型记录集。

*lpszSQL*<br/>
包含以下项之一的字符串指针：

- NULL 指针。

- 一个或多个 tabledefs 和/或 querydefs 的名称（以逗号分隔）。

- SQL **SELECT**语句（可以选择使用 sql **WHERE**或**ORDERBY**子句）。

- 传递查询。

*nOptions*<br/>
下面列出的一个或多个选项。 默认值为 0。 可能的值如下所示：

- `dbAppendOnly` 只能追加新记录（仅限动态集类型的记录集）。 此选项意味着仅可以追加记录。 MFC ODBC 数据库类具有仅限追加的选项，该选项允许检索和追加记录。

- `dbForwardOnly` 记录集是只进滚动快照。

- 如果另一个用户正在更改正在编辑的数据，`dbSeeChanges` 会生成异常。

- `dbDenyWrite` 其他用户不能修改或添加记录。

- `dbDenyRead` 其他用户无法查看记录（仅限表类型记录集）。

- `dbReadOnly` 只能查看记录;其他用户可以修改它们。

- 允许 `dbInconsistent` 不一致的更新（仅限动态集类型的记录集）。

- 仅允许 `dbConsistent` 一致性更新（仅限动态集类型的记录集）。

> [!NOTE]
>  常量 `dbConsistent` 和 `dbInconsistent` 互斥。 可以在 `Open`的给定实例中使用一种或其他方法，但不能同时使用这两种方法。

*pTableDef*<br/>
指向[CDaoTableDef](../../mfc/reference/cdaotabledef-class.md)对象的指针。 此版本仅对表类型的记录集有效。 使用此选项时，不使用用于构造 `CDaoRecordset` 的 `CDaoDatabase` 指针;而是使用 tabledef 驻留的数据库。

*pQueryDef*<br/>
指向[CDaoQueryDef](../../mfc/reference/cdaoquerydef-class.md)对象的指针。 此版本仅适用于动态集类型和快照类型记录集。 使用此选项时，不使用用于构造 `CDaoRecordset` 的 `CDaoDatabase` 指针;而是使用 querydef 所在的数据库。

### <a name="remarks"></a>备注

在调用 `Open`之前，必须构造 recordset 对象。 有若干方法可实现此操作：

- 构造 recordset 对象时，传递指向已打开的 `CDaoDatabase` 对象的指针。

- 构造 recordset 对象时，传递指向未打开的 `CDaoDatabase` 对象的指针。 记录集将打开一个 `CDaoDatabase` 对象，但在记录集对象关闭时将不会关闭它。

- 构造 recordset 对象时，传递一个空指针。 Recordset 对象调用 `GetDefaultDBName` 以获取 Microsoft Access 的名称。要打开的 MDB 文件。 然后，该记录集打开 `CDaoDatabase` 对象，只要记录集处于打开状态就会保持打开状态。 对记录集调用 `Close` 时，`CDaoDatabase` 对象也会关闭。

    > [!NOTE]
    >  当记录集打开 `CDaoDatabase` 对象时，它将打开具有非独占访问权限的数据源。

对于使用*lpszSQL*参数的 `Open` 版本，在记录集打开后，可以通过多种方式之一来检索记录。 第一种方法是在 `DoFieldExchange`中包含 DFX 函数。 第二种方法是通过调用 `GetFieldValue` 成员函数来使用动态绑定。 这些选项可单独实现或组合实现。 如果它们合并在一起，则必须在 SQL 语句中自行传入对 `Open`的调用。

当你使用在其中传递 `CDaoTableDef` 对象的 `Open` 的第二个版本时，生成的列将可供你通过 `DoFieldExchange` 和 DFX 机制进行绑定，并/或通过 `GetFieldValue`动态绑定。

> [!NOTE]
>  仅可使用表类型记录集的 `CDaoTableDef` 对象调用 `Open`。

当你使用在其中传递 `CDaoQueryDef` 对象的 `Open` 的第三个版本时，将执行该查询，并且生成的列将可供你通过 `DoFieldExchange` 和 DFX 机制进行绑定，并/或通过 `GetFieldValue`动态绑定。

> [!NOTE]
>  只能使用用于动态集类型和快照类型记录集的 `CDaoQueryDef` 对象调用 `Open`。

对于使用 `lpszSQL` 参数的 `Open` 的第一个版本，将根据下表中所示的条件选择记录。

|`lpszSQL` 参数的值|选择的记录由|示例|
|--------------------------------------|----------------------------------------|-------------|
|Null|`GetDefaultSQL`返回的字符串。||
|一个或多个 tabledefs 和/或 querydef 名称的逗号分隔列表。|`DoFieldExchange`中表示的所有列。|`"Customer"`|
|从表列表**中** **选择**列列表|指定的 tabledef 和/或 querydef 中指定的列。|`"SELECT CustId, CustName`<br /><br /> `FROM Customer"`|

一般的过程是将 NULL 传递到 `Open`;在这种情况下，`Open` 调用 `GetDefaultSQL`，这是在创建 `CDaoRecordset`派生的类时 ClassWizard 生成的可重写成员函数。 此值提供在 ClassWizard 中指定的 tabledef 和/或 querydef 名称。 您可以改为在*lpszSQL*参数中指定其他信息。

无论通过哪种处理，`Open` 都可以为查询构造最终的 SQL 字符串（该字符串可能会将 SQL **WHERE**和**ORDERBY**子句追加到你传递的*lpszSQL*字符串），然后执行查询。 可以通过在调用 `Open`后调用 `GetSQL` 来检查构造的字符串。

记录集类的字段数据成员绑定到所选数据的列。 如果返回任何记录，则第一个记录将成为当前记录。

如果要设置记录集的选项，例如筛选器或排序，请在构造 recordset 对象之后但在调用 `Open`之前设置 `m_strSort` 或 `m_strFilter`。 如果要在记录集已打开后刷新记录集中的记录，请调用 `Requery`。

如果对动态集类型或快照类型的记录集调用 `Open`，或者如果数据源引用的是表示附加表的 SQL 语句或 tabledef，则不能将 `dbOpenTable` 用于类型参数;如果执行此操作，MFC 会引发异常。 若要确定 tabledef 对象是否表示附加表，请创建[CDaoTableDef](../../mfc/reference/cdaotabledef-class.md)对象并调用其[GetConnect](../../mfc/reference/cdaotabledef-class.md#getconnect)成员函数。

如果要在编辑或删除同一记录时捕获其他用户或计算机上的其他程序所做的更改，请使用 `dbSeeChanges` 标志。 例如，如果两个用户开始编辑同一个记录，则第一个调用 `Update` 成员函数的用户将成功。 当第二个用户调用 `Update` 时，将引发 `CDaoException`。 同样，如果第二个用户尝试调用 `Delete` 来删除记录，并且第一个用户已对其进行了更改，则会发生 `CDaoException`。

通常情况下，如果用户在更新时 `CDaoException` 获取此内容，则代码应刷新字段的内容，并检索新修改的值。 如果在删除过程中发生了异常，则您的代码可能会向用户显示新的记录数据，并显示一条消息，指示最近更改了数据。 此时，你的代码可以请求确认，用户仍想要删除该记录。

> [!TIP]
>  当应用程序通过从 ODBC 数据源打开的记录集进行一次传递时，可使用只进滚动选项（`dbForwardOnly`）来提高性能。

有关相关信息，请参阅 DAO 帮助中的 "OpenRecordset 方法" 主题。

##  <a name="requery"></a>CDaoRecordset：： Requery

调用此成员函数以重新生成（刷新）记录集。

```
virtual void Requery();
```

### <a name="remarks"></a>备注

如果返回任何记录，则第一个记录将成为当前记录。

为了使记录集反映您或其他用户对数据源所做的添加和删除操作，您必须通过调用 `Requery`重新生成记录集。 如果记录集是动态集，则它会自动反映您或其他用户对其现有记录所做的更新（但不是添加）。 如果记录集是快照，则必须调用 `Requery` 来反映其他用户的编辑以及添加和删除操作。

对于动态集或快照，请在每次需要使用参数值重新生成记录集时调用 `Requery`。 在调用 `Requery`之前，通过设置[m_strFilter](#m_strfilter)和[m_strSort](#m_strsort)设置新的筛选器或排序。 在调用 `Requery`之前，通过将新值分配给参数数据成员来设置新参数。

如果重新生成记录集的尝试失败，则关闭该记录集。 调用 `Requery`之前，可以通过调用[CanRestart](#canrestart)成员函数来确定是否可以重新查询记录集。 `CanRestart` 不保证 `Requery` 会成功。

> [!CAUTION]
>  只有在调用 `Open`之后，才能调用 `Requery`。

> [!NOTE]
>  调用[Requery](#requery)会更改 DAO 书签。

如果调用 `CanRestart` 返回0，并且不能在表类型的记录集上使用它，则无法对动态集类型或快照类型的记录集调用 `Requery`。

如果在调用 `Requery`后 `IsBOF` 和 `IsEOF` 均返回非零值，则查询不会返回任何记录，并且记录集也不会包含任何数据。

有关相关信息，请参阅 DAO 帮助中的 "Requery 方法" 主题。

##  <a name="seek"></a>CDaoRecordset：： Seek

调用此成员函数以在索引表类型 recordset 对象中查找满足当前索引的指定条件的记录，并使该记录成为当前记录。

```
BOOL Seek(
    LPCTSTR lpszComparison,
    COleVariant* pKey1,
    COleVariant* pKey2 = NULL,
    COleVariant* pKey3 = NULL);

BOOL Seek(
    LPCTSTR lpszComparison,
    COleVariant* pKeyArray,
    WORD nKeys);
```

### <a name="parameters"></a>parameters

*lpszComparison*<br/>
以下字符串表达式之一： "<"、"\<="、"="、"> =" 或 ">"。

*pKey1*<br/>
指向其值与索引中第一个字段相对应的[COleVariant](../../mfc/reference/colevariant-class.md)的指针。 必需。

*pKey2*<br/>
指向 `COleVariant` 的指针，其值对应于索引中的第二个字段（如果有）。 默认值为 NULL。

*pKey3*<br/>
指向 `COleVariant` 的指针，其值对应于索引中的第三个字段（如果有）。 默认值为 NULL。

*pKeyArray*<br/>
指向变量的数组的指针。 数组大小对应于索引中的字段数。

*nKeys*<br/>
与数组大小相对应的整数，它是索引中的字段数。

> [!NOTE]
>  不要在密钥中指定通配符。 通配符将导致 `Seek` 不返回匹配的记录。

### <a name="return-value"></a>返回值

如果找到匹配记录，则为非零; 否则为0。

### <a name="remarks"></a>备注

使用 `Seek` 的第二个（数组）版本来处理四个或更多字段的索引。

`Seek` 启用对表类型记录集的高性能索引搜索。 在调用 `Seek`之前，必须通过调用 `SetCurrentIndex` 来设置当前索引。 如果索引标识不唯一的键字段，`Seek` 将查找满足条件的第一条记录。 如果未设置索引，则会引发异常。

请注意，如果不创建 UNICODE 记录集，则 `COleVariant` 对象必须显式声明为 ANSI。 为此，可以使用[COleVariant：： COleVariant](../../mfc/reference/colevariant-class.md#colevariant) **（** *lpszSrc* **，** *vtSrc* **）** 形式的构造函数，将*vtSrc*设置为 `VT_BSTRT` （ANSI），或使用 `COleVariant` 函数[SetString](../../mfc/reference/colevariant-class.md#setstring) **（** *lpszSrc* **，** *vtSrc* **）** ， *vtSrc*设置为 `VT_BSTRT`。

调用 `Seek`时，传递一个或多个键值和比较运算符（"<"、"\<="、"="、"> =" 或 ">"）。 `Seek` 搜索指定的键字段并查找满足*lpszComparison*和*pKey1*指定的条件的第一条记录。 找到后，`Seek` 将返回非零值，并使该记录成为最新记录。 如果 `Seek` 未能找到匹配项，则 `Seek` 返回零，且当前记录未定义。 当直接使用 DAO 时，必须显式检查 NoMatch 属性。

如果 `lpszComparison` 为 "="、"> =" 或 ">"，则 `Seek` 从索引的开头开始。 如果*lpszComparison*是 "<" 或 "< ="，`Seek` 将从索引的末尾开始，直到末尾有重复的索引条目时向后搜索。 在这种情况下，`Seek` 在索引末尾的重复索引项之间的任意项开始。

使用 `Seek`时，不必是当前记录。

若要在满足特定条件的动态集类型或快照类型记录集中查找记录，请使用 "查找" 操作。 若要包括所有记录，而不只是满足特定条件的记录，请使用移动操作从记录移动到记录。

不能对任何类型的附加表调用 `Seek`，因为附加表必须打开为动态集类型或快照类型记录集。 但是，如果调用 `CDaoDatabase::Open` 以直接打开可安装的 ISAM 数据库，则可以对该数据库中的表调用 `Seek`，但性能可能会很慢。

有关相关信息，请参阅 DAO 帮助中的 "查找方法" 主题。

##  <a name="setabsoluteposition"></a>CDaoRecordset：： SetAbsolutePosition

设置记录集对象的当前记录的相对记录号。

```
void SetAbsolutePosition(long lPosition);
```

### <a name="parameters"></a>parameters

*lPosition*<br/>
对应于记录集中当前记录的序号位置。

### <a name="remarks"></a>备注

通过调用 `SetAbsolutePosition`，可以根据当前记录指针在动态集类型或快照类型记录集中的序号位置，将其定位到特定记录。 还可以通过调用[GetAbsolutePosition](#getabsoluteposition)来确定当前记录号。

> [!NOTE]
>  此成员函数仅适用于动态集类型和快照类型记录集。

基础 DAO 对象的 AbsolutePosition 属性值从零开始;如果设置为0，则表示记录集中的第一条记录。 如果将值设置为大于填充记录的数目，将导致 MFC 引发异常。 您可以通过调用 `GetRecordCount` 成员函数来确定记录集中填充的记录数。

如果删除当前记录，则不会定义 AbsolutePosition 属性值，并且 MFC 会在引用它时引发异常。 新记录将添加到序列的末尾。

> [!NOTE]
>  此属性不应用作代理项记录号。 书签仍是保留并返回到给定位置的建议方法，是将当前记录定位在支持书签的所有类型的记录集对象中的唯一方法。 特别是，在删除给定记录之前的记录时，该记录的位置会发生更改。 如果重新创建记录集，则对于给定的记录将具有相同的绝对位置，因为记录集中单个记录的顺序不能保证，除非使用**ORDERBY**子句创建了 SQL 语句。

有关相关信息，请参阅 DAO 帮助中的主题 "AbsolutePosition 属性"。

##  <a name="setbookmark"></a>CDaoRecordset：： SetBookmark

调用此成员函数以将记录集放置在包含指定书签的记录上。

```
void SetBookmark(COleVariant varBookmark);
```

### <a name="parameters"></a>parameters

*varBookmark*<br/>
一个包含特定记录的书签值的[COleVariant](../../mfc/reference/colevariant-class.md)对象。

### <a name="remarks"></a>备注

当创建或打开 recordset 对象时，它的每个记录都具有唯一的书签。 可以通过调用 `GetBookmark` 并将值保存到 `COleVariant` 对象来检索当前记录的书签。 稍后可以通过使用保存的书签值调用 `SetBookmark`，返回到该记录。

> [!NOTE]
>  调用[Requery](#requery)会更改 DAO 书签。

请注意，如果不创建 UNICODE 记录集，则 `COleVariant` 对象必须显式声明为 ANSI。 为此，可以使用[COleVariant：： COleVariant](../../mfc/reference/colevariant-class.md#colevariant) **（** *lpszSrc* **，** *vtSrc* **）** 形式的构造函数，将*vtSrc*设置为 `VT_BSTRT` （ANSI），或使用 `COleVariant` 函数[SetString](../../mfc/reference/colevariant-class.md#setstring) **（** *lpszSrc* **，** *vtSrc* **）** ， *vtSrc*设置为 `VT_BSTRT`。

有关相关信息，请参阅 DAO 帮助中的主题 "Bookmark 属性" 和 Bookmarkable 属性 "。

##  <a name="setcachesize"></a>CDaoRecordset：： SetCacheSize

调用此成员函数可设置要缓存的记录数。

```
void SetCacheSize(long lSize);
```

### <a name="parameters"></a>parameters

*lSize*<br/>
指定记录数。 典型值为100。 设置为0将禁用缓存。 此设置必须介于5到1200条记录之间。 缓存可能会占用大量内存。

### <a name="remarks"></a>备注

缓存是本地内存中的一个空间，保存最近从服务器检索到的数据，因为在应用程序运行时将再次请求数据。 数据缓存提高了从远程服务器检索数据的应用程序的性能。 请求数据时，Microsoft Jet 数据库引擎首先会检查缓存中是否存在请求的数据，而不是从服务器中检索它，这需要更多时间。 不是来自 ODBC 数据源的数据不会保存在缓存中。

任何 ODBC 数据源（如附加表）都可以具有本地缓存。 若要创建缓存，请打开远程数据源中的记录集对象，调用 `SetCacheSize` 并 `SetCacheStart` 成员函数，然后通过使用移动操作之一来调用 `FillCache` 成员函数或单步执行记录。 `SetCacheSize` 成员函数的*lSize*参数可以基于应用程序一次可以处理的记录数。 例如，如果使用记录集作为要在屏幕上显示的数据的源，则可以将 `SetCacheSize` *lSize*参数作为20传递，以便一次显示20条记录。

相关信息，请参阅 DAO 帮助中的主题 "CacheSize，CacheStart Properties"。

##  <a name="setcachestart"></a>CDaoRecordset：： SetCacheStart

调用此成员函数以指定要缓存的记录集中的第一条记录的书签。

```
void SetCacheStart(COleVariant varBookmark);
```

### <a name="parameters"></a>parameters

*varBookmark*<br/>
一个[COleVariant](../../mfc/reference/colevariant-class.md) ，指定要缓存的记录集中的第一条记录的书签。

### <a name="remarks"></a>备注

对于 `SetCacheStart` 成员函数的*varBookmark*参数，您可以使用任何记录的书签值。 使用当前记录创建要启动缓存的记录，使用[SetBookmark](#setbookmark)为该记录建立书签，并将书签值作为 `SetCacheStart` 成员函数的参数进行传递。

Microsoft Jet 数据库引擎在缓存范围内请求缓存中的记录，并从服务器请求缓存范围之外的记录。

从缓存检索的记录不反映其他用户对源数据所做的更改。

若要强制执行所有缓存数据的更新，请将 `SetCacheSize` 的*lSize*参数传递为0，并使用最初请求的缓存大小再次调用 `SetCacheSize`，然后调用 `FillCache` 成员函数。

请注意，如果不创建 UNICODE 记录集，则 `COleVariant` 对象必须显式声明为 ANSI。 为此，可以使用[COleVariant：： COleVariant](../../mfc/reference/colevariant-class.md#colevariant) **（** *lpszSrc* **，** *vtSrc* **）** 形式的构造函数，将*vtSrc*设置为 `VT_BSTRT` （ANSI），或使用 `COleVariant` 函数[SetString](../../mfc/reference/colevariant-class.md#setstring) **（** *lpszSrc* **，** *vtSrc* **）** ， *vtSrc*设置为 `VT_BSTRT`。

相关信息，请参阅 DAO 帮助中的主题 CacheSize，CacheStart Properties。

##  <a name="setcurrentindex"></a>CDaoRecordset：： SetCurrentIndex

调用此成员函数可以设置表类型记录集的索引。

```
void SetCurrentIndex(LPCTSTR lpszIndex);
```

### <a name="parameters"></a>parameters

*lpszIndex*<br/>
一个指针，它包含要设置的索引的名称。

### <a name="remarks"></a>备注

基表中的记录不按任何特定顺序存储。 设置索引会更改从数据库返回的记录的顺序，但不会影响记录的存储顺序。 指定的索引必须已经定义。 如果尝试使用不存在的索引对象，或者在调用[Seek](#seek)时未设置索引，则 MFC 会引发异常。

您可以通过调用[CDaoTableDef：： CreateIndex](../../mfc/reference/cdaotabledef-class.md#createindex)并将新索引追加到基础 Tabledef 的索引[集合，然后](../../mfc/reference/cdaotabledef-class.md#append)重新打开记录集，为该表创建新索引。

从表类型记录集返回的记录只能由为基础 tabledef 定义的索引进行排序。 若要按其他顺序对记录进行排序，可以使用存储在[CDaoRecordset：： m_strSort](#m_strsort)中的 SQL **ORDERBY**子句打开动态集类型或快照类型的记录集。

有关相关信息，请参阅 DAO 帮助中的主题 "索引对象" 和定义 "当前索引"。

##  <a name="setfielddirty"></a>CDaoRecordset：： SetFieldDirty

调用此成员函数可将记录集的字段数据成员标记为已更改或保持不变。

```
void SetFieldDirty(
    void* pv,
    BOOL bDirty = TRUE);
```

### <a name="parameters"></a>parameters

*函数*<br/>
包含记录集的字段数据成员的地址，或为 NULL。 如果为 NULL，则对记录集中的所有字段数据成员进行标记。 （C++ Null 与数据库术语中的 null 不相同，这意味着 "无值"。）

*bDirty*<br/>
如果要将字段数据成员标记为 "已更新" （已更改），则为 TRUE。 否则，如果将字段数据成员标记为 "清理" （未更改），则为 FALSE。

### <a name="remarks"></a>备注

将字段标记为 "未更改" 可确保字段不会更新。

框架标记已更改的字段数据成员，以确保 DAO 记录字段交换（DFX）机制将它们写入数据源上的记录。 更改字段的值通常会自动将字段设置为脏字段，因此您很少需要自行调用 `SetFieldDirty`，但有时您可能需要确保列将被显式更新或插入，而不考虑字段数据成员中的值。 DFX 机制还使用 PSEUDONULL。 有关详细信息，请参阅[CDaoFieldExchange：： m_nOperation](../../mfc/reference/cdaofieldexchange-class.md#m_noperation)。

如果未使用双缓冲机制，则更改字段的值不会自动将字段设置为 "已更新"。 在这种情况下，必须将字段显式设置为 "已更新"。 [M_bCheckCacheForDirtyFields](#m_bcheckcachefordirtyfields)中包含的标志控制此自动字段检查。

> [!NOTE]
>  只有在调用 "[编辑](#edit)" 或 " [AddNew](#addnew)" 后才调用此成员函数。

使用 NULL 作为函数的第一个参数会将函数应用于所有 `outputColumn` 字段，而不是 `CDaoFieldExchange`中的**参数**字段。 例如，调用

[!code-cpp[NVC_MFCDatabase#6](../../mfc/codesnippet/cpp/cdaorecordset-class_6.cpp)]

仅将 `outputColumn` 字段设置为 NULL;**参数**字段将不受影响。

若要处理某个**参数**，必须提供要使用的各个**参数**的实际地址，例如：

[!code-cpp[NVC_MFCDatabase#7](../../mfc/codesnippet/cpp/cdaorecordset-class_7.cpp)]

这意味着，不能将所有的**参数**字段设置为 NULL，这与 `outputColumn` 字段一样。

`SetFieldDirty` 是通过 `DoFieldExchange`实现的。

##  <a name="setfieldnull"></a>CDaoRecordset：： SetFieldNull

调用此成员函数可将记录集的字段数据成员标记为 Null （具体没有值）或非 Null。

```
void SetFieldNull(
    void* pv,
    BOOL bNull = TRUE);
```

### <a name="parameters"></a>parameters

*函数*<br/>
包含记录集的字段数据成员的地址，或为 NULL。 如果为 NULL，则对记录集中的所有字段数据成员进行标记。 （C++ Null 与数据库术语中的 null 不相同，这意味着 "无值"。）

*bNull*<br/>
如果要将字段数据成员标记为没有值（Null），则为非零值。 否则，如果将字段数据成员标记为非 Null，则为0。

### <a name="remarks"></a>备注

`SetFieldNull` 用于 `DoFieldExchange` 机制中绑定的字段。

向记录集添加新记录时，所有字段数据成员最初均设置为 Null 值并标记为 "已更新" （已更改）。 在从数据源中检索记录时，其列要么已包含值，要么是 Null。 如果不适合使字段为空，则会引发[CDaoException](../../mfc/reference/cdaoexception-class.md) 。

例如，如果您要使用双缓冲机制（例如，如果您特别希望将当前记录的字段指定为不具有值），请调用 `SetFieldNull` 将*bNull*设置为 TRUE，以将其标记为 Null。 如果字段以前标记为 Null，并且你现在要为其指定值，只需设置其新值。 无需删除 `SetFieldNull`的 Null 标志。 若要确定是否允许字段为空，请调用[IsFieldNullable](#isfieldnullable)。

如果未使用双缓冲机制，则更改字段的值不会自动将字段设置为 "已更新" 和 "非 Null"。 必须专门设置脏字段和非 Null 字段。 [M_bCheckCacheForDirtyFields](#m_bcheckcachefordirtyfields)中包含的标志控制此自动字段检查。

DFX 机制采用了 PSEUDONULL 的用法。 有关详细信息，请参阅[CDaoFieldExchange：： m_nOperation](../../mfc/reference/cdaofieldexchange-class.md#m_noperation)。

> [!NOTE]
>  只有在调用 "[编辑](#edit)" 或 " [AddNew](#addnew)" 后才调用此成员函数。

如果对函数的第一个参数使用 NULL，则仅将函数应用于 `CDaoFieldExchange`中 `outputColumn` 字段，而不是**参数**字段。 例如，调用

[!code-cpp[NVC_MFCDatabase#8](../../mfc/codesnippet/cpp/cdaorecordset-class_8.cpp)]

仅将 `outputColumn` 字段设置为 NULL;**参数**字段将不受影响。

##  <a name="setfieldvalue"></a>CDaoRecordset：： SetFieldValue

调用此成员函数可以通过序号位置或通过更改字符串的值来设置字段的值。

```
virtual void SetFieldValue(
    LPCTSTR lpszName,
    const COleVariant& varValue);

virtual void SetFieldValue(
    int nIndex,
    const COleVariant& varValue);

void SetFieldValue(
    LPCTSTR lpszName,
    LPCTSTR lpszValue);

void SetFieldValue(
    int nIndex,
    LPCTSTR lpszValue);
```

### <a name="parameters"></a>parameters

*lpszName*<br/>
指向包含字段名称的字符串的指针。

*varValue*<br/>
对包含字段内容值的[COleVariant](../../mfc/reference/colevariant-class.md)对象的引用。

*nIndex*<br/>
一个整数，表示字段在记录集的字段集合中的序号位置（从零开始）。

*lpszValue*<br/>
指向包含字段内容值的字符串的指针。

### <a name="remarks"></a>备注

使用 `SetFieldValue` 和[GetFieldValue](#getfieldvalue)在运行时动态绑定字段，而不是使用[DoFieldExchange](#dofieldexchange)机制静态绑定列。

请注意，如果不创建 UNICODE 记录集，则必须使用不包含 `COleVariant` 参数的 `SetFieldValue` 形式，或者必须将 `COleVariant` 对象显式声明为 ANSI。 为此，可以使用[COleVariant：： COleVariant](../../mfc/reference/colevariant-class.md#colevariant) **（** *lpszSrc* **，** *vtSrc* **）** 形式的构造函数，将*vtSrc*设置为 `VT_BSTRT` （ANSI），或使用 `COleVariant` 函数[SetString](../../mfc/reference/colevariant-class.md#setstring) **（** *lpszSrc* **，** *vtSrc* **）** ， *vtSrc*设置为 `VT_BSTRT`。

有关相关信息，请参阅 DAO 帮助中的主题 "字段对象" 和 "值属性"。

##  <a name="setfieldvaluenull"></a>CDaoRecordset：： SetFieldValueNull

调用此成员函数可将字段设置为 Null 值。

```
void SetFieldValueNull(int nIndex);
void SetFieldValueNull(LPCTSTR lpszName);
```

### <a name="parameters"></a>parameters

*nIndex*<br/>
记录集中的字段索引，用于按从零开始的索引查找。

*lpszName*<br/>
记录集中字段的名称，用于按名称查找。

### <a name="remarks"></a>备注

C++NULL 与 Null 不同，后者在数据库术语中意味着 "无值"。

有关相关信息，请参阅 DAO 帮助中的主题 "字段对象" 和 "值属性"。

##  <a name="setlockingmode"></a>CDaoRecordset：： SetLockingMode

调用此成员函数可设置记录集的锁定类型。

```
void SetLockingMode(BOOL bPessimistic);
```

### <a name="parameters"></a>parameters

*bPessimistic*<br/>
指示锁定类型的标志。

### <a name="remarks"></a>备注

当悲观锁定有效时，只要调用 `Edit` 成员函数，就会锁定包含正在编辑的记录的2K 页面。 调用 `Update` 或 `Close` 成员函数或任何移动或查找操作时，将取消锁定此页。

当乐观锁定生效时，只有在用 `Update` 成员函数更新记录时，才会锁定包含记录的2K 页面。

如果页面被锁定，则任何其他用户都不能在同一页面上编辑记录。 如果调用 `SetLockingMode` 并传递一个非零值，而另一个用户已锁定页面，则在调用 `Edit`时会引发异常。 其他用户可以从锁定的页面读取数据。

如果使用零值调用 `SetLockingMode`，并在页面被其他用户锁定时调用 `Update`，则会出现异常。 若要查看其他用户对记录所做的更改（并放弃更改），请使用当前记录的书签值调用 `SetBookmark` 成员函数。

使用 ODBC 数据源时，锁定模式始终处于乐观状态。

##  <a name="setparamvalue"></a>CDaoRecordset：： SetParamValue

调用此成员函数可在运行时设置记录集中的参数的值。

```
virtual void SetParamValue(
    int nIndex,
    const COleVariant& varValue);

virtual void SetParamValue(
    LPCTSTR lpszName,
    const COleVariant& varValue);
```

### <a name="parameters"></a>parameters

*nIndex*<br/>
Querydef 的参数集合中的参数的数字位置。

*var*<br/>
要设置的值;请参阅 "备注"。

*lpszName*<br/>
要设置其值的参数的名称。

### <a name="remarks"></a>备注

该参数必须已作为记录集的 SQL 字符串的一部分已建立。 可以通过名称或其在集合中的索引位置访问参数。

指定要设置为 `COleVariant` 对象的值。 有关在 `COleVariant` 对象中设置所需值和类型的信息，请参阅[COleVariant](../../mfc/reference/colevariant-class.md)类。 请注意，如果不创建 UNICODE 记录集，则 `COleVariant` 对象必须显式声明为 ANSI。 为此，可以使用[COleVariant：： COleVariant](../../mfc/reference/colevariant-class.md#colevariant) **（** *lpszSrc* **，** *vtSrc* **）** 形式的构造函数，将*vtSrc*设置为 `VT_BSTRT` （ANSI），或使用 `COleVariant` 函数[SetString](../../mfc/reference/colevariant-class.md#setstring) **（** *lpszSrc* **，** *vtSrc* **）** ， *vtSrc*设置为 `VT_BSTRT`。

##  <a name="setparamvaluenull"></a>CDaoRecordset：： SetParamValueNull

调用此成员函数可将参数设置为 Null 值。

```
void SetParamValueNull(int nIndex);
void SetParamValueNull(LPCTSTR lpszName);
```

### <a name="parameters"></a>parameters

*nIndex*<br/>
记录集中的字段索引，用于按从零开始的索引查找。

*lpszName*<br/>
记录集中字段的名称，用于按名称查找。

### <a name="remarks"></a>备注

C++NULL 与 Null 不同，后者在数据库术语中意味着 "无值"。

##  <a name="setpercentposition"></a>CDaoRecordset：： SetPercentPosition

调用此成员函数可以设置一个值，该值根据记录集中的记录的百分比更改 recordset 对象中当前记录的近似位置。

```
void SetPercentPosition(float fPosition);
```

### <a name="parameters"></a>parameters

*fPosition*<br/>
一个介于 0 和 100 之间的数字。

### <a name="remarks"></a>备注

使用动态集类型或快照类型记录集时，首先在调用 `SetPercentPosition`之前，通过移动到最后一条记录来填充记录集。 如果在完全填充记录集之前调用 `SetPercentPosition`，则移动量相对于按[GetRecordCount](#getrecordcount)值指示的被访问的记录数。 您可以通过调用 `MoveLast`移动到最后一条记录。

调用 `SetPercentPosition`后，与该值相对应的近似位置的记录将变为当前值。

> [!NOTE]
>  不建议调用 `SetPercentPosition` 将当前记录移动到记录集中的特定记录。 改为调用[SetBookmark](#setbookmark)成员函数。

有关相关信息，请参阅 DAO 帮助中的主题 "PercentPosition 属性"。

##  <a name="update"></a>CDaoRecordset：： Update

调用 `AddNew` 或 `Edit` 成员函数后，调用此成员函数。

```
virtual void Update();
```

### <a name="remarks"></a>备注

完成 `AddNew` 或 `Edit` 操作需要执行此调用。

`AddNew` 和 `Edit` 准备一个编辑缓冲区，在此缓冲区中添加或编辑的数据用于保存到数据源。 `Update` 保存数据。 仅更新标记或检测为已更改的字段。

如果数据源支持事务，则可以对事务进行 `Update` 调用（及其相应的 `AddNew` 或 `Edit` 调用）部分。

> [!CAUTION]
> 如果在调用 `Update` 时未首先调用 `AddNew` 或 `Edit`，则 `Update` 将引发 `CDaoException`。 如果调用 `AddNew` 或 `Edit`，则必须在调用[MoveNext](#movenext)之前调用 `Update`，或关闭记录集或数据源连接。 否则，你所做的更改将丢失，但不通知。

如果在多用户环境中 pessimistically 记录集对象，则在更新完成之前，记录将一直保持锁定状态 `Edit`。 如果记录集已乐观地锁定，则该记录将被锁定，并与预编辑的记录进行比较，就像在数据库中更新该记录。 如果记录自调用 `Edit`以来已更改，则 `Update` 操作将失败，MFC 将引发异常。 可以通过 `SetLockingMode`更改锁定模式。

> [!NOTE]
> 始终对外部数据库格式使用开放式锁定，如 ODBC 和可安装的 ISAM。

有关相关信息，请参阅 DAO 帮助中的 "AddNew 方法"、"CancelUpdate 方法"、"删除方法"、"LastModified 属性"、"更新方法" 和 "EditMode 属性" 主题。

## <a name="see-also"></a>另请参阅

[CObject 类](../../mfc/reference/cobject-class.md)<br/>
[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[CDaoTableDef 类](../../mfc/reference/cdaotabledef-class.md)<br/>
[CDaoWorkspace 类](../../mfc/reference/cdaoworkspace-class.md)<br/>
[CDaoDatabase 类](../../mfc/reference/cdaodatabase-class.md)<br/>
[CDaoQueryDef 类](../../mfc/reference/cdaoquerydef-class.md)<br/>
