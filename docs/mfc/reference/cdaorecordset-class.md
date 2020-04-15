---
title: CDao记录组类
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
ms.openlocfilehash: 5b4b2919405696c748ce01217ac82afeac316de2
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81377155"
---
# <a name="cdaorecordset-class"></a>CDao记录组类

表示从数据源选择的一组记录。

## <a name="syntax"></a>语法

```
class CDaoRecordset : public CObject
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[CDao 记录集：：CDao 记录集](#cdaorecordset)|构造 `CDaoRecordset` 对象。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CDao 记录集：：添加新](#addnew)|准备添加新记录。 调用[更新](#update)以完成添加。|
|[CDao 记录集：：可应用](#canappend)|如果可以通过[AddNew](#addnew)成员函数将新记录添加到记录集，则返回非零。|
|[CDao 记录集：：CanBookmark](#canbookmark)|如果记录集支持书签，则返回非零。|
|[CDao 记录集：：取消更新](#cancelupdate)|由于[编辑](#edit)或[添加新](#addnew)操作而取消任何挂起的更新。|
|[CDao 记录集：：可以重新启动](#canrestart)|如果可以调用[Requery](#requery)再次运行记录集的查询，则返回非零。|
|[CDao 记录集：：CanScroll](#canscroll)|如果可以滚动浏览记录，则返回非零。|
|[CDao 记录集：：可转换](#cantransact)|如果数据源支持事务，则返回非零。|
|[CDao 记录集：：可以更新](#canupdate)|如果可以更新记录集（可以添加、更新或删除记录），则返回非零。|
|[CDao 记录集：关闭](#close)|关闭记录集。|
|[CDao记录集：:Delete](#delete)|从记录集中删除当前记录。 删除后，必须显式滚动到其他记录。|
|[CDao记录集：:DoFieldExchange](#dofieldexchange)|调用 以在记录集的字段数据成员和数据源上的相应记录之间交换数据（双向）。 实现 DAO 记录字段交换 （DFX）。|
|[CDaoRecordset：编辑](#edit)|准备对当前记录的更改。 调用`Update`以完成编辑。|
|[CDao 记录集：：填充缓存](#fillcache)|填充包含来自 ODBC 数据源数据的记录集对象的全部或部分本地缓存。|
|[CDao 记录集：查找](#find)|在动态集类型记录集中查找特定字符串的第一个、下一个、上一个或最后一个位置，该位置满足指定的条件并使该记录成为当前记录。|
|[CDao 记录集：：查找第一](#findfirst)|在动态集类型或快照类型记录集中查找满足指定条件并使该记录成为当前记录的第一个记录。|
|[CDao 记录集：：查找最后](#findlast)|在动态集类型或快照类型记录集中查找满足指定条件并使该记录成为当前记录的最后一条记录。|
|[CDao 记录集：：查找下一个](#findnext)|在动态集类型或快照类型记录集中查找满足指定条件并使该记录成为当前记录的下一个记录。|
|[CDao记录集：：查找Prev](#findprev)|在满足指定条件并使该记录成为当前记录的动态集类型或快照类型记录集中查找以前的记录。|
|[CDao 记录集：获取绝对位置](#getabsoluteposition)|返回记录集对象的当前记录的记录编号。|
|[CDao 记录集：：获取书签](#getbookmark)|返回表示记录上的书签的值。|
|[CDao 记录集：：获取缓存大小](#getcachesize)|返回指定动态集类型记录集中的记录数的值，其中包含要从 ODBC 数据源本地缓存的数据。|
|[CDao 记录集：：获取缓存开始](#getcachestart)|返回指定要缓存的记录集中第一个记录的书签的值。|
|[CDao 记录集：：获取当前索引](#getcurrentindex)|返回`CString`包含索引表类型`CDaoRecordset`上最近使用的索引的名称 。|
|[CDao 记录集：：获取日期创建](#getdatecreated)|返回创建对象基础的基表的`CDaoRecordset`日期和时间|
|[CDao 记录集：：获取更新日期](#getdatelastupdated)|返回对对象基础表设计进行的最新更改的`CDaoRecordset`日期和时间。|
|[CDao 记录集：获取默认 DB 名称](#getdefaultdbname)|返回默认数据源的名称。|
|[CDao 记录集：：获取默认SQL](#getdefaultsql)|调用以获取要执行的默认 SQL 字符串。|
|[CDao 记录集：：获取编辑模式](#geteditmode)|返回指示当前记录的编辑状态的值。|
|[CDao记录集：：获取菲尔德计数](#getfieldcount)|返回表示记录集中的字段数的值。|
|[CDaoRecordset：获取菲尔德信息](#getfieldinfo)|返回有关记录集中字段的特定类型的信息。|
|[CDao 记录集：获取场值](#getfieldvalue)|返回记录集中的字段的值。|
|[CDao 记录集：获取索引计数](#getindexcount)|检索记录集基础表中的索引数。|
|[CDao 记录集：获取索引信息](#getindexinfo)|返回有关索引的各种信息。|
|[CDao 记录集：：获取上次修改的书签](#getlastmodifiedbookmark)|用于确定最近添加或更新的记录。|
|[CDao 记录集：：获取锁定模式](#getlockingmode)|返回指示编辑期间有效的锁定类型的值。|
|[CDao 记录集：获取名称](#getname)|返回`CString`包含记录集名称的 。|
|[CDao 记录集：：获取帕拉姆价值](#getparamvalue)|检索存储在基础 DAOParameter 对象中的指定参数的当前值。|
|[CDao 记录集：获取百分比位置](#getpercentposition)|将当前记录的位置作为记录总数的百分比返回。|
|[CDao 记录集：：获取记录计数](#getrecordcount)|返回在记录集对象中访问的记录数。|
|[CDao 记录集：：获取SQL](#getsql)|获取用于选择记录集记录的 SQL 字符串。|
|[CDao 记录集：获取类型](#gettype)|调用 以确定记录集的类型：表类型、动态集类型或快照类型。|
|[CDao 记录集：：获取验证规则](#getvalidationrule)|返回`CString`包含在输入字段中的数据时验证数据的值。|
|[CDao 记录集：：获取验证文本](#getvalidationtext)|检索不符合验证规则时显示的文本。|
|[CDao 记录集：IsBOF](#isbof)|如果记录集已定位在第一条记录之前，则返回非零。 没有最新记录。|
|[CDao 记录集：已删除](#isdeleted)|如果记录集位于已删除的记录上，则返回非零。|
|[CDao 记录集：：IsEOF](#iseof)|如果记录集位于最后一条记录之后，则返回非零。 没有最新记录。|
|[CDao 记录集：：IsfieldDirty](#isfielddirty)|如果当前记录中的指定字段已更改，则返回非零。|
|[CDao记录集：：IsfieldNull](#isfieldnull)|如果当前记录中的指定字段为 Null（没有值），则返回非零。|
|[CDao 记录集：：可字段空](#isfieldnullable)|如果当前记录中的指定字段可以设置为 Null（没有值），则返回非零。|
|[CDao 记录集：：是打开的](#isopen)|如果之前已调用[Open，](#open)则返回非零。|
|[CDao 记录集：：移动](#move)|将记录集定位为从当前记录中的指定记录数，以任一方向。|
|[CDao 记录集：：先移动](#movefirst)|将当前记录定位到记录集中的第一条记录上。|
|[CDao 记录集：：移动上次](#movelast)|将当前记录定位到记录集中的最后一条记录上。|
|[CDao 记录集：：移动下一个](#movenext)|将当前记录定位到记录集中的下一条记录上。|
|[CDao记录集：：MovePrev](#moveprev)|在记录集中的上一条记录上定位当前记录。|
|[CDao 记录集：：打开](#open)|从表、动态集或快照创建新的记录集。|
|[CDao 记录集：：重新查询](#requery)|再次运行记录集的查询以刷新所选记录。|
|[CDao 记录集：：查找](#seek)|在索引的表类型记录集对象中查找记录，该对象满足当前索引的指定条件，并使该记录成为当前记录。|
|[CDao 记录集：：设置绝对位置](#setabsoluteposition)|设置记录集对象的当前记录的记录编号。|
|[CDao 记录集：：设置书签](#setbookmark)|将记录集放在包含指定书签的记录上。|
|[CDao 记录集：：设置缓存大小](#setcachesize)|设置一个值，指定动态集类型记录集中的记录数，其中包含要从 ODBC 数据源本地缓存的数据。|
|[CDao 记录集：：设置缓存开始](#setcachestart)|设置指定要缓存的记录集中第一个记录的书签的值。|
|[CDao 记录集：：设置当前索引](#setcurrentindex)|调用 以在表类型记录集上设置索引。|
|[CDao 记录集：：设置字段脏](#setfielddirty)|将当前记录中的指定字段标记为已更改。|
|[CDao 记录集：：SetFieldNull](#setfieldnull)|将当前记录中指定字段的值设置为 Null（没有值）。|
|[CDao 记录集：：设置场值](#setfieldvalue)|在记录集中设置字段的值。|
|[CDao 记录集：：设置场值 Null](#setfieldvaluenull)|将记录集中的字段的值设置为 Null。 （没有值）。|
|[CDao 记录集：：设置锁定模式](#setlockingmode)|设置指示在编辑期间生效的锁定类型的值。|
|[CDao 记录集：：SetParamValue](#setparamvalue)|设置存储在基础 DAO 参数对象中的指定参数的当前值|
|[CDao 记录集：：SetParamValueNull](#setparamvaluenull)|将指定参数的当前值设置为 Null（没有值）。|
|[CDao 记录集：：设置百分比位置](#setpercentposition)|将当前记录的位置设置为对应于记录集中记录总数百分比的位置。|
|[CDao 记录集：：更新](#update)|通过在数据源上`AddNew`保存`Edit`新的或编辑的数据来完成 或 操作。|

### <a name="public-data-members"></a>公共数据成员

|名称|说明|
|----------|-----------------|
|[CDaoRecordset：m_bCheckCacheForDirtyFields](#m_bcheckcachefordirtyfields)|包含一个标志，指示字段是否自动标记为已更改。|
|[CDao 记录集：：m_nFields](#m_nfields)|包含记录集类中的字段数据成员数以及记录组从数据源中选择的列数。|
|[CDao 记录集：：m_nParams](#m_nparams)|包含记录集类中的参数数据成员数 - 使用记录集查询传递的参数数|
|[CDao 记录集：：m_pDAORecordset](#m_pdaorecordset)|指向记录集对象基础的 DAO 接口的指针。|
|[CDao 记录集：：m_pDatabase](#m_pdatabase)|此结果集的源数据库。 包含指向[CDao 数据库](../../mfc/reference/cdaodatabase-class.md)对象的指针。|
|[CDao 记录集：：m_strFilter](#m_strfilter)|包含用于构造 SQL **WHERE**语句的字符串。|
|[CDao 记录集：：m_strSort](#m_strsort)|包含用于构造 SQL **ORDER BY**语句的字符串。|

## <a name="remarks"></a>备注

对象称为"记录集"，`CDaoRecordset`有以下三种形式可供选择：

- 表类型记录集表示一个基本表，可用于检查、添加、更改或删除单个数据库表中的记录。

- 动态集类型的记录集是具有可更新记录的查询的结果。 这些记录集是一组记录，可用于检查、添加、更改或删除基础数据库表或表中的记录。 Dynaset 类型记录集可以包含数据库中一个或多个表中的字段。

- 快照类型记录集是一组记录的静态副本，可用于查找数据或生成报表。 这些记录集可以包含数据库中一个或多个表的字段，但不能更新。

记录集的每种形式表示在打开记录集时修复的一组记录。 当您滚动到表类型记录集中的记录集或动态集类型记录集中的记录时，它反映在打开记录集后对记录所做的更改，由其他用户或应用程序中的其他记录集进行。 （无法更新快照类型的记录集。可以直接使用`CDaoRecordset`或派生应用程序`CDaoRecordset`特定的记录集类。 然后，可以：

- 滚动记录。

- 设置索引并使用[Seek](#seek)快速查找记录（仅限表类型记录集）。

- 根据字符串比较查找记录："<"、"\""""*"、">"\<或">"（动态集类型和快照类型记录集）。

- 更新记录并指定锁定模式（快照类型记录集除外）。

- 筛选记录集以约束它从数据源上可用的记录中选择哪些记录。

- 对记录集进行排序。

- 参数化记录集，以自定义其选择与在运行时之前不知道的信息。

类`CDaoRecordset`提供类似于类`CRecordset`的接口。 主要区别是类`CDaoRecordset`通过基于 OLE 的数据访问对象 （DAO） 访问数据。 类`CRecordset`通过开放数据库连接 （ODBC） 和该 DBMS 的 ODBC 驱动程序访问 DBMS。

> [!NOTE]
> DAO 数据库类不同于基于开放数据库连接 （ODBC） 的 MFC 数据库类。 所有 DAO 数据库类名称都有"CDao"前缀。 您仍可以使用 DAO 类访问 ODBC 数据源;DAO 类通常提供卓越的功能，因为它们特定于 Microsoft Jet 数据库引擎。

可以直接使用`CDaoRecordset`或派生类。 `CDaoRecordset` 要在任一情况下使用记录集类，请打开数据库并构造记录集对象，将构造函数传递给对象的`CDaoDatabase`指针。 您还可以构造对象`CDaoRecordset`，并让 MFC 为您创建临时`CDaoDatabase`对象。 然后调用记录集的[Open](#open)成员函数，指定对象是表类型的记录集、动态集类型的记录集还是快照类型的记录集。 调用`Open`从数据库中选择数据并检索第一条记录。

使用对象的成员函数和数据成员滚动浏览记录并对其进行操作。 可用的操作取决于对象是表类型记录集、动态集类型记录集还是快照类型记录集，以及它是可更新还是只读 - 这取决于数据库或开放数据库连接 （ODBC） 数据源的功能。 要刷新自`Open`调用以来可能已更改或添加的记录，请调用对象的[重新查询](#requery)成员函数。 调用对象的`Close`成员函数，并在对象完成时销毁该函数。

`CDaoRecordset`使用 DAO 记录字段交换 （DFX） 支持通过类型安全C++派生`CDaoRecordset``CDaoRecordset`类的成员读取和更新记录字段。 您还可以使用[GetFieldValue](#getfieldvalue)和[SetFieldValue](#setfieldvalue)在数据库中实现列的动态绑定，而无需使用 DFX 机制。

有关相关信息，请参阅 DAO 帮助中的主题"记录集对象"。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

`CDaoRecordset`

## <a name="requirements"></a>要求

**标题：** afxdao.h

## <a name="cdaorecordsetaddnew"></a><a name="addnew"></a>CDao 记录集：：添加新

调用此成员函数以向表类型或动态集类型记录集添加新记录。

```
virtual void AddNew();
```

### <a name="remarks"></a>备注

记录的字段最初为空。 （在数据库术语中，Null 表示"没有值"，并且与 C++ 中的 NULL 不同。要完成该操作，必须调用[Update](#update)成员函数。 `Update`将更改保存到数据源。

> [!CAUTION]
> 如果编辑记录，然后滚动到另一条记录而不调用`Update`，则更改将丢失，而不会发出警告。

如果通过调用[AddNew](#addnew)将记录添加到动态集类型的记录集中，则该记录在记录集中可见，并包含在基础表中，其中任何新`CDaoRecordset`对象都可以看到该记录。

新记录的位置取决于记录集的类型：

- 在动态集类型的记录集中，不保证插入新记录的位置。 由于性能和并发性的原因，Microsoft Jet 3.0 会更改此行为。 如果目标是使新添加的记录成为当前记录，请获取上次修改记录的书签并移动到该书签：

[!code-cpp[NVC_MFCDatabase#1](../../mfc/codesnippet/cpp/cdaorecordset-class_1.cpp)]

- 在已为其指定索引的表类型记录集中，记录按排序顺序以适当的位置返回。 如果未指定索引，则在记录集的末尾返回新记录。

使用`AddNew`前当前的记录仍为当前记录。 如果要使新记录为当前，并且记录集支持书签，请将[SetBookmark](#setbookmark)调用基础 DAO 记录集对象的"上次修改"属性设置标识的书签。 这样做对于确定添加记录中计数器（自动增量）字段的值非常有用。 有关详细信息，请参阅[获取已修改的书签](#getlastmodifiedbookmark)。

如果数据库支持事务，则可以使`AddNew`调用成为事务的一部分。 有关事务的详细信息，请参阅类[CDao 工作区](../../mfc/reference/cdaoworkspace-class.md)。 请注意，在调用`AddNew`之前，应调用[CDao 工作区：：开始转换](../../mfc/reference/cdaoworkspace-class.md#begintrans)。

调用`AddNew`未调用其[Open](#open)成员函数的记录集是非法的。 如果`CDaoException`调用`AddNew`无法追加的记录集，则引发 。 您可以通过调用[CanAppend](#canappend)来确定记录集是否可以更新。

框架标记已更改的字段数据成员，以确保 DAO 记录字段交换 （DFX） 机制将它们写入数据源上的记录。 更改字段的值通常会自动将字段设置为脏，因此您很少需要自己调用[SetFieldDirty，](#setfielddirty)但有时您可能希望确保无论字段数据成员中的哪个值如何，都会显式更新或插入列。 DFX 机制还使用**PSEUDO NULL**。 有关详细信息，请参阅[CDaoFieldExchange：：m_nOperation](../../mfc/reference/cdaofieldexchange-class.md#m_noperation)。

如果未使用双缓冲机制，则更改字段的值不会自动将字段设置为脏。 在这种情况下，必须显式将字段设置为脏。 [m_bCheckCacheForDirtyFields](#m_bcheckcachefordirtyfields)中包含的标志控制此自动字段检查。

> [!NOTE]
> 如果记录是双缓冲的（即启用了自动字段检查），则调用`CancelUpdate`将成员变量还原到以前`AddNew`或`Edit`已调用的值。

有关相关信息，请参阅 DAO 帮助中的"添加新方法"、"取消更新方法"、"上次修改属性"和"编辑模式属性"的主题。

## <a name="cdaorecordsetcanappend"></a><a name="canappend"></a>CDao 记录集：：可应用

调用此成员函数以确定以前打开的记录集是否允许您通过调用[AddNew](#addnew)成员函数添加新记录。

```
BOOL CanAppend() const;
```

### <a name="return-value"></a>返回值

如果记录集允许添加新记录，则非零;否则 0。 `CanAppend`如果以只读身份打开记录集，则返回 0。

### <a name="remarks"></a>备注

有关相关信息，请参阅 DAO 帮助中的主题"附加方法"。

## <a name="cdaorecordsetcanbookmark"></a><a name="canbookmark"></a>CDao 记录集：：CanBookmark

调用此成员函数以确定以前打开的记录集是否允许您使用书签单独标记记录。

```
BOOL CanBookmark();
```

### <a name="return-value"></a>返回值

如果记录集支持书签，则非零，否则为 0。

### <a name="remarks"></a>备注

如果完全基于 Microsoft Jet 数据库引擎表使用记录集，则可以使用书签，但标记为仅转发滚动记录集的快照类型记录组除外。 其他数据库产品（外部 ODBC 数据源）可能不支持书签。

有关相关信息，请参阅 DAO 帮助中的主题"可书签属性"。

## <a name="cdaorecordsetcancelupdate"></a><a name="cancelupdate"></a>CDao 记录集：：取消更新

成员`CancelUpdate`函数将由于[编辑](#edit)或[AddNew](#addnew)操作而取消任何挂起的更新。

```
virtual void CancelUpdate();
```

### <a name="remarks"></a>备注

例如，如果应用程序调用`Edit`或`AddNew`成员函数，但未调用[Update](#update) `CancelUpdate` ，则取消在调用或`Edit``AddNew`调用后所做的任何更改。

> [!NOTE]
> 如果记录是双缓冲的（即启用了自动字段检查），则调用`CancelUpdate`将成员变量还原到以前`AddNew`或`Edit`已调用的值。

如果没有`Edit`或`AddNew`操作挂起，`CancelUpdate`则会导致 MFC 引发异常。 调用[GetEditMode](#geteditmode)成员函数以确定是否存在可取消的挂起操作。

有关相关信息，请参阅 DAO 帮助中的主题"取消更新方法"。

## <a name="cdaorecordsetcanrestart"></a><a name="canrestart"></a>CDao 记录集：：可以重新启动

调用此成员函数以确定记录集是否允许通过调用`Requery`成员函数重新启动其查询（刷新其记录）。

```
BOOL CanRestart();
```

### <a name="return-value"></a>返回值

如果`Requery`可以调用非零，以便再次运行记录集的查询，否则为 0。

### <a name="remarks"></a>备注

表类型的记录集不支持`Requery`。

如果`Requery`不受支持，则调用["关闭](#close)"然后[打开](#open)以刷新数据。 在参数值`Requery`更改后，可以调用更新记录集对象的基础参数查询。

有关相关信息，请参阅 DAO 帮助中的主题"可重新启动属性"。

## <a name="cdaorecordsetcanscroll"></a><a name="canscroll"></a>CDao 记录集：：CanScroll

调用此成员函数以确定记录集是否允许滚动。

```
BOOL CanScroll() const;
```

### <a name="return-value"></a>返回值

如果可以滚动浏览记录，则为非零，否则为 0。

### <a name="remarks"></a>备注

如果使用 调用["打开](#open)"，`dbForwardOnly`则记录集只能向前滚动。

有关相关信息，请参阅 DAO 帮助中的主题"使用 DAO 定位当前记录指针"。

## <a name="cdaorecordsetcantransact"></a><a name="cantransact"></a>CDao 记录集：：可转换

调用此成员函数以确定记录集是否允许事务。

```
BOOL CanTransact();
```

### <a name="return-value"></a>返回值

如果基础数据源支持事务，则非零，否则为 0。

### <a name="remarks"></a>备注

有关相关信息，请参阅 DAO 帮助中的"交易属性"主题。

## <a name="cdaorecordsetcanupdate"></a><a name="canupdate"></a>CDao 记录集：：可以更新

调用此成员函数以确定是否可以更新记录集。

```
BOOL CanUpdate() const;
```

### <a name="return-value"></a>返回值

如果可以更新记录集（添加、更新和删除记录），则非零，否则为 0。

### <a name="remarks"></a>备注

如果基础数据源是只读的，或者在调用记录集[的 Open](#open)时为*nOptions*指定`dbReadOnly`，则记录集可能是只读的。

有关相关信息，请参阅 DAO 帮助中的"添加新方法"、"编辑方法"、"删除方法"、"更新方法"和"可更新属性"的主题。

## <a name="cdaorecordsetcdaorecordset"></a><a name="cdaorecordset"></a>CDao 记录集：：CDao 记录集

构造 `CDaoRecordset` 对象。

```
CDaoRecordset(CDaoDatabase* pDatabase = NULL);
```

### <a name="parameters"></a>参数

*p数据库*<br/>
包含指向[CDao 数据库](../../mfc/reference/cdaodatabase-class.md)对象的指针或值 NULL。 如果不是 NULL，并且`CDaoDatabase`尚未调用对象`Open`的成员函数将其连接到数据源，则记录集将尝试在它自己的[Open](#open)调用期间为您打开它。 如果传递 NULL，则`CDaoDatabase`使用指定的数据源信息（如果派生自 的`CDaoRecordset`记录集类）为构建和连接对象。

### <a name="remarks"></a>备注

可以直接使用`CDaoRecordset`或派生应用程序`CDaoRecordset`特定的类。 您可以使用 ClassWizard 派生记录集类。

> [!NOTE]
> 如果派生类`CDaoRecordset`，派生类必须提供其自己的构造函数。 在派生类的构造函数中，调用构造函数`CDaoRecordset::CDaoRecordset`，将适当的参数传递给它。

将 NULL 传递给记录集构造函数，以便`CDaoDatabase`自动构造和连接对象。 这是一个有用的快捷方式，不需要在构造记录集之前构造和连接`CDaoDatabase`对象。 如果`CDaoDatabase`对象未打开，也将为您创建一个使用默认工作区的[CDaoWorkspace](../../mfc/reference/cdaoworkspace-class.md)对象。 有关详细信息，请参阅[CDao 数据库：cDao 数据库](../../mfc/reference/cdaodatabase-class.md#cdaodatabase)。

## <a name="cdaorecordsetclose"></a><a name="close"></a>CDao 记录集：关闭

关闭`CDaoRecordset`对象会将其从关联数据库中的打开记录集的集合中删除。

```
virtual void Close();
```

### <a name="remarks"></a>备注

因为`Close`不会破坏`CDaoRecordset`对象，因此可以通过调用`Open`同一数据源或其他数据源来重用该对象。

所有挂起的[AddNew](#addnew)或[Edit](#edit)语句都将取消，并且所有挂起的事务都将回滚。 如果要保留挂起的添加或编辑，请先调用["更新"，](#update)然后再调用`Close`每个记录集。

通话后可以`Open`再次呼叫`Close`。 这允许您重用记录集对象。 如果可能，更好的选择是调用[重新查询](#requery)。

有关相关信息，请参阅 DAO 帮助中的主题"关闭方法"。

## <a name="cdaorecordsetdelete"></a><a name="delete"></a>CDao记录集：:Delete

调用此成员函数以删除打开动态集类型或表类型记录集对象中的当前记录。

```
virtual void Delete();
```

### <a name="remarks"></a>备注

成功删除后，记录集的字段数据成员将设置为 Null 值，您必须显式调用记录集导航成员函数之一（[移动](#move)、[查找](#seek)[、SetBookmark](#setbookmark)等），才能移出已删除的记录。 从记录集中删除记录时，在调用`Delete`和 之前，记录集中必须存在当前记录。否则，MFC 会引发异常。

`Delete`删除当前记录并使其无法访问。 尽管您无法编辑或使用已删除的记录，但它仍然是最新的。 但是，移动到其他记录后，无法使已删除的记录再次成为当前记录。

> [!CAUTION]
> 记录集必须是可向上的，并且在调用`Delete`时记录集中必须有有效的记录电流。 例如，如果删除记录，但在再次调用`Delete`之前不滚动到新记录，则`Delete`引发[CDaoException](../../mfc/reference/cdaoexception-class.md)。

如果使用事务并调用[CDao 工作区：：回滚](../../mfc/reference/cdaoworkspace-class.md#rollback)成员函数，则可以取消删除记录。 如果基表是级联删除关系中的主表，则删除当前记录还可以删除外表中的一个或多个记录。 有关详细信息，请参阅 DAO 帮助中的定义"级联删除"。

与`AddNew``Edit`和 不同`Delete`，调用 后不调用`Update`。

有关相关信息，请参阅 DAO 帮助中的"添加新方法"、"编辑方法"、"删除方法"、"更新方法"和"可更新属性"的主题。

## <a name="cdaorecordsetdofieldexchange"></a><a name="dofieldexchange"></a>CDao记录集：:DoFieldExchange

框架调用此成员函数以在记录集对象的字段数据成员和数据源上的当前记录的相应列之间自动交换数据。

```
virtual void DoFieldExchange(CDaoFieldExchange* pFX);
```

### <a name="parameters"></a>参数

*pFX*<br/>
包含指向`CDaoFieldExchange`对象的指针。 框架已经设置了此对象，以指定字段交换操作的上下文。

### <a name="remarks"></a>备注

它还将参数数据成员（如果有）绑定到 SQL 语句字符串中的参数占位符，以便记录集的选择。 字段数据交换（称为 DAO 记录字段交换 （DFX） 在两个方向上工作：从记录集对象的字段数据成员到数据源上记录的字段，以及从数据源上的记录到记录集对象。 如果动态绑定列，则不需要实现`DoFieldExchange`。

`DoFieldExchange`对于派生的记录集类，通常需要执行的唯一操作是使用 ClassWizard 创建类并指定字段数据成员的名称和数据类型。 您还可以向 ClassWizard 编写的代码添加代码以指定参数数据成员。 如果要动态绑定所有字段，除非指定参数数据成员，否则此函数将处于非活动状态。

当您使用 ClassWizard 声明派生的记录集类时，向导`DoFieldExchange`会为您编写一个重写，类似于以下示例：

[!code-cpp[NVC_MFCDatabase#2](../../mfc/codesnippet/cpp/cdaorecordset-class_2.cpp)]

## <a name="cdaorecordsetedit"></a><a name="edit"></a>CDaoRecordset：编辑

调用此成员函数以允许更改当前记录。

```
virtual void Edit();
```

### <a name="remarks"></a>备注

调用`Edit`成员函数后，对当前记录的字段所做的更改将复制到复制缓冲区。 对记录进行所需的更改后，调用`Update`以保存更改。 `Edit`保存记录集的数据成员的值。 如果调用`Edit`，进行更改，然后再次调用`Edit`，记录的值将还原到第一次`Edit`调用之前的值。

> [!CAUTION]
> 如果编辑记录，然后执行任何移动到另一个记录而不首先调用`Update`的操作，则更改将丢失，而不会发出警告。 此外，如果关闭记录集或父数据库，则已编辑的记录将被丢弃，而不会发出警告。

在某些情况下，您可能希望通过使列为 Null（不包含任何数据）来更新列。 为此，使用 TRUE`SetFieldNull`参数调用以标记字段 Null;这还会导致更新列。 如果希望将字段写入数据源，即使其值未更改，则使用 TRUE 参数调用`SetFieldDirty`。 即使字段的值为 Null，这也能起作用。

框架标记已更改的字段数据成员，以确保 DAO 记录字段交换 （DFX） 机制将它们写入数据源上的记录。 更改字段的值通常会自动将字段设置为脏，因此您很少需要自己调用[SetFieldDirty，](#setfielddirty)但有时您可能希望确保无论字段数据成员中的哪个值如何，都会显式更新或插入列。 DFX 机制还使用**PSEUDO NULL**。 有关详细信息，请参阅[CDaoFieldExchange：：m_nOperation](../../mfc/reference/cdaofieldexchange-class.md#m_noperation)。

如果未使用双缓冲机制，则更改字段的值不会自动将字段设置为脏。 在这种情况下，必须显式将字段设置为脏。 [m_bCheckCacheForDirtyFields](#m_bcheckcachefordirtyfields)中包含的标志控制此自动字段检查。

当记录集对象在多用户环境中被悲观锁定时，记录从使用到`Edit`更新完成时一直锁定。 如果记录集被乐观地锁定，则记录将锁定，并在数据库中更新之前与预编辑的记录进行比较。 如果记录自调用`Edit`后已更改，则`Update`操作将失败，并且 MFC 会引发异常。 您可以使用 更改锁定模式`SetLockingMode`。

> [!NOTE]
> 乐观锁定始终用于外部数据库格式，如 ODBC 和可安装 ISAM。

调用`Edit`后，当前记录保持最新。 要调用`Edit`，必须有当前记录。 如果没有当前记录，或者记录集不引用打开的表类型或动态集类型的记录集对象，则会发生异常。 调用`Edit`会导致在`CDaoException`以下条件下引发 a：

- 没有最新记录。

- 数据库或记录集是只读的。

- 记录中没有字段是可向上的。

- 数据库或记录集已打开，供其他用户独占使用。

- 其他用户已锁定包含您的记录的页面。

如果数据源支持事务，则可以使`Edit`调用成为事务的一部分。 请注意，应在调用`CDaoWorkspace::BeginTrans``Edit`之前和打开记录集之后进行调用。 另请注意，调用`CDaoWorkspace::CommitTrans`不能替代调用`Update`来完成操作`Edit`。 有关事务的详细信息，请参阅类`CDaoWorkspace`。

有关相关信息，请参阅 DAO 帮助中的"添加新方法"、"编辑方法"、"删除方法"、"更新方法"和"可更新属性"的主题。

## <a name="cdaorecordsetfillcache"></a><a name="fillcache"></a>CDao 记录集：：填充缓存

调用此成员函数以缓存记录集中的指定数量的记录。

```
void FillCache(
    long* pSize = NULL,
    COleVariant* pBookmark = NULL);
```

### <a name="parameters"></a>参数

*pSize*<br/>
指定要填充缓存的行数。 如果省略此参数，该值由基础 DAO 对象的 CacheSize 属性设置确定。

*pBookmark*<br/>
指定书签的[COleVariant。](../../mfc/reference/colevariant-class.md) 缓存从此书签指示的记录开始填充。 如果省略此参数，则缓存将从基础 DAO 对象的 CacheStart 属性指示的记录开始填充。

### <a name="remarks"></a>备注

缓存提高了从远程服务器检索或获取数据的应用程序的性能。 缓存是本地内存中的空间，它保存最近从服务器获取的数据，前提是在应用程序运行时可能会再次请求数据。 请求数据时，Microsoft Jet 数据库引擎会首先检查缓存的数据，而不是从服务器获取数据，这需要更多的时间。 在非 ODBC 数据源上使用数据缓存不起作用，因为数据不会保存在缓存中。

您可以随时通过调用`FillCache`成员函数来显式填充缓存，而不是等待缓存在获取记录时填充这些记录。 这是一种加快填充缓存的方法，因为`FillCache`一次获取多个记录，而不是一次获取一条记录。 例如，在显示每个记录屏幕时，您可以让应用程序调用`FillCache`来获取下一个记录屏幕。

使用记录集对象访问的任何 ODBC 数据库都可以具有本地缓存。 要创建缓存，请从远程数据源打开记录集对象，然后调用记录集 的`SetCacheSize`和`SetCacheStart`成员函数。 如果*lSize*和*lBookmark*创建的范围部分或全部超出 和 指定的`SetCacheSize`范围`SetCacheStart`，则忽略此范围之外的记录集部分，并且不会加载到缓存中。 如果`FillCache`请求的记录多于保留在远程数据源中的记录，则仅提取其余记录，并且不会引发异常。

从缓存获取的记录不会反映其他用户同时对源数据所做的更改。

`FillCache`仅获取尚未缓存的记录。 要强制更新所有缓存的数据，请调用具有等于 0 `SetCacheSize` *的 lSize*参数的成员函数，再次调用`SetCacheSize` *lSize*参数等于您最初请求的缓存的大小，然后调用`FillCache`。

有关相关信息，请参阅 DAO 帮助中的主题"FillCache 方法"。

## <a name="cdaorecordsetfind"></a><a name="find"></a>CDao 记录集：查找

调用此成员函数，使用比较运算符在动态集或快照类型记录集中查找特定字符串。

```
virtual BOOL Find(
    long lFindType,
    LPCTSTR lpszFilter);
```

### <a name="parameters"></a>参数

*l 查找类型*<br/>
指示所需查找操作类型的值。 可能的值包括：

- AFX_DAO_NEXT查找匹配字符串的下一个位置。

- AFX_DAO_PREV查找匹配字符串的上一个位置。

- AFX_DAO_FIRST 查找匹配字符串的第一个位置。

- AFX_DAO_LAST 查找匹配字符串的最后一个位置。

*lpszFilter*<br/>
用于查找记录的字符串表达式（如 SQL 语句中的**WHERE**子句，没有单词**WHERE）。** 例如：

[!code-cpp[NVC_MFCDatabase#3](../../mfc/codesnippet/cpp/cdaorecordset-class_3.cpp)]

### <a name="return-value"></a>返回值

如果找到匹配的记录，则非零，否则为 0。

### <a name="remarks"></a>备注

您可以找到字符串的第一个、下一个、上一个或最后一个实例。 `Find`是一个虚拟函数，因此您可以重写它并添加您自己的实现。 `FindFirst` `FindPrev` `Find` 、和 成员函数调用成员函数，因此可以使用 来控制`Find`所有 Find 操作的行为。 `FindLast` `FindNext`

要在表类型记录集中查找记录，请调用[Seek](#seek)成员函数。

> [!TIP]
> 记录集越小，效果就越大`Find`。 通常，尤其是使用 ODBC 数据时，最好创建一个新查询，仅检索所需的记录。

有关相关信息，请参阅 DAO 帮助中的主题"查找第一、查找最后、查找下一个、查找以前的方法"。

## <a name="cdaorecordsetfindfirst"></a><a name="findfirst"></a>CDao 记录集：：查找第一

调用此成员函数以查找与指定条件匹配的第一个记录。

```
BOOL FindFirst(LPCTSTR lpszFilter);
```

### <a name="parameters"></a>参数

*lpszFilter*<br/>
用于查找记录的字符串表达式（如 SQL 语句中的**WHERE**子句，没有单词**WHERE）。**

### <a name="return-value"></a>返回值

如果找到匹配的记录，则非零，否则为 0。

### <a name="remarks"></a>备注

`FindFirst`成员函数从记录集的开头开始搜索，然后搜索到记录集的末尾。

如果要在搜索中包括所有记录（而不仅仅是满足特定条件的记录），请使用 Move 操作之一从记录移动到记录。 要在表类型记录集中查找记录，请调用`Seek`成员函数。

如果未找到与条件匹配的记录，则当前记录指针未确定，并`FindFirst`返回零。 如果记录集包含满足条件的多个记录，则`FindFirst`查找第一个匹配项，`FindNext`找到下一个匹配项，等等。

> [!CAUTION]
> 如果编辑当前记录，请确保在移动到其他记录之前通过调用`Update`成员函数来保存更改。 如果不更新而移动到其他记录，则更改将丢失，而不会发出警告。

成员`Find`函数从下表中指定的位置和方向进行搜索：

|查找操作|Begin|搜索方向|
|---------------------|-----------|----------------------|
|`FindFirst`|记录集的开始|记录集结束|
|`FindLast`|记录集结束|记录集的开始|
|`FindNext`|当前记录|记录集结束|
|`FindPrevious`|当前记录|记录集的开始|

> [!NOTE]
> 调用`FindLast`时，如果尚未完成搜索，则 Microsoft Jet 数据库引擎在开始搜索之前将完全填充记录集。 第一次搜索可能需要比后续搜索更长的时间。

使用 Find 操作之一与 调用`MoveFirst`或`MoveNext`不同，它只是使第一个或下一个记录保持最新而不指定条件。 您可以使用"移动"操作执行"查找"操作。

使用 Find 操作时，请记住以下事项：

- 如果`Find`返回非零，则不定义当前记录。 在这种情况下，必须将当前记录指针定位回有效记录。

- 不能将"查找"操作与仅转发滚动快照类型记录集一起使用。

- 搜索包含日期的字段时，即使您未使用 Microsoft Jet 数据库引擎的美国版本，也应使用美国日期格式（月日年）。否则，可能无法找到匹配的记录。

- 使用 ODBC 数据库和大型动态集时，您可能会发现使用 Find 操作很慢，尤其是在使用大型记录集时。 通过将 SQL 查询与自定义**ORDERBY**或**WHERE**子句、参数查询或`CDaoQuerydef`检索特定索引记录的对象使用 SQL 查询来提高性能。

有关相关信息，请参阅 DAO 帮助中的主题"查找第一、查找最后、查找下一个、查找以前的方法"。

## <a name="cdaorecordsetfindlast"></a><a name="findlast"></a>CDao 记录集：：查找最后

调用此成员函数以查找与指定条件匹配的最后一条记录。

```
BOOL FindLast(LPCTSTR lpszFilter);
```

### <a name="parameters"></a>参数

*lpszFilter*<br/>
用于查找记录的字符串表达式（如 SQL 语句中的**WHERE**子句，没有单词**WHERE）。**

### <a name="return-value"></a>返回值

如果找到匹配的记录，则非零，否则为 0。

### <a name="remarks"></a>备注

`FindLast`成员函数在记录集的末尾开始搜索，然后向后搜索到记录集的开头。

如果要在搜索中包括所有记录（而不仅仅是满足特定条件的记录），请使用 Move 操作之一从记录移动到记录。 要在表类型记录集中查找记录，请调用`Seek`成员函数。

如果未找到与条件匹配的记录，则当前记录指针未确定，并`FindLast`返回零。 如果记录集包含满足条件的多个记录，则`FindFirst`查找第一个匹配项，`FindNext`查找第一次匹配项之后的下一个匹配项，等等。

> [!CAUTION]
> 如果编辑当前记录，请确保在移动到其他记录之前通过调用`Update`成员函数来保存更改。 如果不更新而移动到其他记录，则更改将丢失，而不会发出警告。

使用 Find 操作之一与 调用`MoveFirst`或`MoveNext`不同，它只是使第一个或下一个记录保持最新而不指定条件。 您可以使用"移动"操作执行"查找"操作。

使用 Find 操作时，请记住以下事项：

- 如果`Find`返回非零，则不定义当前记录。 在这种情况下，必须将当前记录指针定位回有效记录。

- 不能将"查找"操作与仅转发滚动快照类型记录集一起使用。

- 搜索包含日期的字段时，即使您未使用 Microsoft Jet 数据库引擎的美国版本，也应使用美国日期格式（月日年）。否则，可能无法找到匹配的记录。

- 使用 ODBC 数据库和大型动态集时，您可能会发现使用 Find 操作很慢，尤其是在使用大型记录集时。 通过将 SQL 查询与自定义**ORDERBY**或**WHERE**子句、参数查询或`CDaoQuerydef`检索特定索引记录的对象使用 SQL 查询来提高性能。

有关相关信息，请参阅 DAO 帮助中的主题"查找第一、查找最后、查找下一个、查找以前的方法"。

## <a name="cdaorecordsetfindnext"></a><a name="findnext"></a>CDao 记录集：：查找下一个

调用此成员函数以查找与指定条件匹配的下一个记录。

```
BOOL FindNext(LPCTSTR lpszFilter);
```

### <a name="parameters"></a>参数

*lpszFilter*<br/>
用于查找记录的字符串表达式（如 SQL 语句中的**WHERE**子句，没有单词**WHERE）。**

### <a name="return-value"></a>返回值

如果找到匹配的记录，则非零，否则为 0。

### <a name="remarks"></a>备注

成员`FindNext`函数在当前记录处开始搜索，然后搜索到记录集的末尾。

如果要在搜索中包括所有记录（而不仅仅是满足特定条件的记录），请使用 Move 操作之一从记录移动到记录。 要在表类型记录集中查找记录，请调用`Seek`成员函数。

如果未找到与条件匹配的记录，则当前记录指针未确定，并`FindNext`返回零。 如果记录集包含满足条件的多个记录，则`FindFirst`查找第一个匹配项，`FindNext`找到下一个匹配项，等等。

> [!CAUTION]
> 如果编辑当前记录，请确保在移动到其他记录之前通过调用`Update`成员函数来保存更改。 如果不更新而移动到其他记录，则更改将丢失，而不会发出警告。

使用 Find 操作之一与 调用`MoveFirst`或`MoveNext`不同，它只是使第一个或下一个记录保持最新而不指定条件。 您可以使用"移动"操作执行"查找"操作。

使用 Find 操作时，请记住以下事项：

- 如果`Find`返回非零，则不定义当前记录。 在这种情况下，必须将当前记录指针定位回有效记录。

- 不能将"查找"操作与仅转发滚动快照类型记录集一起使用。

- 搜索包含日期的字段时，即使您未使用 Microsoft Jet 数据库引擎的美国版本，也应使用美国日期格式（月日年）。否则，可能无法找到匹配的记录。

- 使用 ODBC 数据库和大型动态集时，您可能会发现使用 Find 操作很慢，尤其是在使用大型记录集时。 通过将 SQL 查询与自定义**ORDERBY**或**WHERE**子句、参数查询或`CDaoQuerydef`检索特定索引记录的对象使用 SQL 查询来提高性能。

有关相关信息，请参阅 DAO 帮助中的主题"查找第一、查找最后、查找下一个、查找以前的方法"。

## <a name="cdaorecordsetfindprev"></a><a name="findprev"></a>CDao记录集：：查找Prev

调用此成员函数以查找与指定条件匹配的上一条记录。

```
BOOL FindPrev(LPCTSTR lpszFilter);
```

### <a name="parameters"></a>参数

*lpszFilter*<br/>
用于查找记录的字符串表达式（如 SQL 语句中的**WHERE**子句，没有单词**WHERE）。**

### <a name="return-value"></a>返回值

如果找到匹配的记录，则非零，否则为 0。

### <a name="remarks"></a>备注

`FindPrev`成员函数在当前记录处开始搜索，然后向后搜索到记录集的开头。

如果要在搜索中包括所有记录（而不仅仅是满足特定条件的记录），请使用 Move 操作之一从记录移动到记录。 要在表类型记录集中查找记录，请调用`Seek`成员函数。

如果未找到与条件匹配的记录，则当前记录指针未确定，并`FindPrev`返回零。 如果记录集包含满足条件的多个记录，则`FindFirst`查找第一个匹配项，`FindNext`找到下一个匹配项，等等。

> [!CAUTION]
> 如果编辑当前记录，请确保在移动到其他记录之前通过调用`Update`成员函数来保存更改。 如果不更新而移动到其他记录，则更改将丢失，而不会发出警告。

使用 Find 操作之一与 调用`MoveFirst`或`MoveNext`不同，它只是使第一个或下一个记录保持最新而不指定条件。 您可以使用"移动"操作执行"查找"操作。

使用 Find 操作时，请记住以下事项：

- 如果`Find`返回非零，则不定义当前记录。 在这种情况下，必须将当前记录指针定位回有效记录。

- 不能将"查找"操作与仅转发滚动快照类型记录集一起使用。

- 搜索包含日期的字段时，即使您未使用 Microsoft Jet 数据库引擎的美国版本，也应使用美国日期格式（月日年）。否则，可能无法找到匹配的记录。

- 使用 ODBC 数据库和大型动态集时，您可能会发现使用 Find 操作很慢，尤其是在使用大型记录集时。 通过将 SQL 查询与自定义**ORDERBY**或**WHERE**子句、参数查询或`CDaoQuerydef`检索特定索引记录的对象使用 SQL 查询来提高性能。

有关相关信息，请参阅 DAO 帮助中的主题"查找第一、查找最后、查找下一个、查找以前的方法"。

## <a name="cdaorecordsetgetabsoluteposition"></a><a name="getabsoluteposition"></a>CDao 记录集：获取绝对位置

返回记录集对象的当前记录的记录编号。

```
long GetAbsolutePosition();
```

### <a name="return-value"></a>返回值

从 0 到记录集中记录数的整数。 对应于记录集中当前记录的盘位位置。

### <a name="remarks"></a>备注

基础 DAO 对象的绝对位置属性值是零基的;设置为 0 是指记录集中的第一个记录。 您可以通过调用[GetRecordCount](#getrecordcount)来确定记录集中填充的记录数。 调用`GetRecordCount`可能需要一些时间，因为它必须访问所有记录以确定计数。

如果没有当前记录，如记录集中没有记录时，则返回 - 1。 如果删除当前记录，则不定义绝对位置属性值，如果引用，MFC 将引发异常。 对于动态集类型的记录集，新记录将添加到序列的末尾。

> [!NOTE]
> 此属性不用作代理记录编号。 书签仍然是保留和返回到给定位置的推荐方式，是跨所有类型的记录集对象定位当前记录的唯一方法。 特别是，当删除给定记录之前的记录时，给定记录的位置会发生变化。 如果再次重新创建记录集，也不能保证给定记录集具有相同的绝对位置，因为除非使用**ORDERBY**子句使用 SQL 语句创建记录集中的单个记录的顺序不保证。

> [!NOTE]
> 此成员函数仅适用于动态集类型和快照类型记录集。

有关相关信息，请参阅 DAO 帮助中的"绝对位置属性"主题。

## <a name="cdaorecordsetgetbookmark"></a><a name="getbookmark"></a>CDao 记录集：：获取书签

调用此成员函数以获取特定记录中的书签值。

```
COleVariant GetBookmark();
```

### <a name="return-value"></a>返回值

返回表示当前记录上的书签的值。

### <a name="remarks"></a>备注

创建或打开记录集对象时，如果每个记录支持它们，则其每个记录已具有唯一的书签。 调用`CanBookmark`以确定记录集是否支持书签。

通过将书签的值分配给`COleVariant`对象，可以保存当前记录的书签。 要在移动到其他记录后随时快速返回到该记录，请调用`SetBookmark`与该`COleVariant`对象的值对应的参数。

> [!NOTE]
> 调用[重新查询](#requery)会更改 DAO 书签。

有关相关信息，请参阅 DAO 帮助中的主题"书签属性"。

## <a name="cdaorecordsetgetcachesize"></a><a name="getcachesize"></a>CDao 记录集：：获取缓存大小

调用此成员函数以获取缓存的记录数。

```
long GetCacheSize();
```

### <a name="return-value"></a>返回值

指定动态集类型记录集中的记录数的值，其中包含要从 ODBC 数据源本地缓存的数据。

### <a name="remarks"></a>备注

数据缓存提高了应用程序通过动态集类型记录集对象从远程服务器检索数据的性能。 缓存是本地内存中的一个空间，用于保存最近从服务器检索的数据，如果应用程序运行时将再次请求数据。 请求数据时，Microsoft Jet 数据库引擎首先检查缓存中请求的数据，而不是从服务器检索数据，这需要更多的时间。 不来自 ODBC 数据源的数据不会保存在缓存中。

任何 ODBC 数据源（如附加的表）都可以具有本地缓存。

有关相关信息，请参阅 DAO 帮助中的主题"缓存大小、缓存启动属性"。

## <a name="cdaorecordsetgetcachestart"></a><a name="getcachestart"></a>CDao 记录集：：获取缓存开始

调用此成员函数以获取要缓存的记录集中第一个记录的书签值。

```
COleVariant GetCacheStart();
```

### <a name="return-value"></a>返回值

指定`COleVariant`要缓存的记录集中第一个记录的书签。

### <a name="remarks"></a>备注

Microsoft Jet 数据库引擎从缓存请求缓存范围内的记录，并且请求服务器在缓存范围之外的记录。

> [!NOTE]
> 从缓存中检索的记录不会反映其他用户同时对源数据所做的更改。

有关相关信息，请参阅 DAO 帮助中的主题"缓存大小、缓存启动属性"。

## <a name="cdaorecordsetgetcurrentindex"></a><a name="getcurrentindex"></a>CDao 记录集：：获取当前索引

调用此成员函数以确定索引表类型`CDaoRecordset`对象中当前使用的索引。

```
CString GetCurrentIndex();
```

### <a name="return-value"></a>返回值

包含`CString`当前与表类型记录集一起使用的索引的名称。 如果未设置索引，则返回空字符串。

### <a name="remarks"></a>备注

此索引是对表类型记录集中的记录排序的基础，并且[由 Seek](#seek)成员函数用于查找记录。

对象`CDaoRecordset`可以有多个索引，但一次只能使用一个索引（尽管[CDaoTableDef](../../mfc/reference/cdaotabledef-class.md)对象可能有多个索引定义）。

有关相关信息，请参阅 DAO 帮助中的主题"索引对象"和定义"当前索引"。

## <a name="cdaorecordsetgetdatecreated"></a><a name="getdatecreated"></a>CDao 记录集：：获取日期创建

调用此成员函数以检索创建基表的日期和时间。

```
COleDateTime GetDateCreated();
```

### <a name="return-value"></a>返回值

包含创建基表的日期和时间的[COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)对象。

### <a name="remarks"></a>备注

日期和时间设置派生自创建基表的计算机。

有关相关信息，请参阅 DAO 帮助中的主题"创建日期，上次更新的属性"。

## <a name="cdaorecordsetgetdatelastupdated"></a><a name="getdatelastupdated"></a>CDao 记录集：：获取更新日期

调用此成员函数以检索架构上次更新的日期和时间。

```
COleDateTime GetDateLastUpdated();
```

### <a name="return-value"></a>返回值

包含上次更新基表结构（架构）的日期和时间的[COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)对象。

### <a name="remarks"></a>备注

日期和时间设置派生自上次更新基表结构（架构）的计算机。

有关相关信息，请参阅 DAO 帮助中的主题"创建日期，上次更新的属性"。

## <a name="cdaorecordsetgetdefaultdbname"></a><a name="getdefaultdbname"></a>CDao 记录集：获取默认 DB 名称

调用此成员函数以确定此记录集的数据库名称。

```
virtual CString GetDefaultDBName();
```

### <a name="return-value"></a>返回值

包含`CString`派生此记录集的数据库的路径和名称的 。

### <a name="remarks"></a>备注

如果创建记录集时没有指向[CDao 数据库](../../mfc/reference/cdaodatabase-class.md)的指针，则记录集使用此路径来打开默认数据库。 默认情况下，此函数返回一个空字符串。 当 ClassWizard 从`CDaoRecordset`派生新的记录集时，它将为您创建此函数。

下面的示例说明了在字符串中使用双反斜杠 （\\\\），这是正确解释字符串所需的。

[!code-cpp[NVC_MFCDatabase#4](../../mfc/codesnippet/cpp/cdaorecordset-class_4.cpp)]

## <a name="cdaorecordsetgetdefaultsql"></a><a name="getdefaultsql"></a>CDao 记录集：：获取默认SQL

框架调用此成员函数以获取记录集所基于的默认 SQL 语句。

```
virtual CString GetDefaultSQL();
```

### <a name="return-value"></a>返回值

包含`CString`默认 SQL 语句的 。

### <a name="remarks"></a>备注

这可能是表名称或 SQL **SELECT**语句。

通过使用 ClassWizard 声明记录集类来间接定义默认 SQL 语句，ClassWizard 会为您执行此任务。

如果将空 SQL 字符串传递给[Open](#open)，则调用此函数以确定记录集的表名或 SQL。

## <a name="cdaorecordsetgeteditmode"></a><a name="geteditmode"></a>CDao 记录集：：获取编辑模式

调用此成员函数以确定编辑状态，这是以下值之一：

```
short GetEditMode();
```

### <a name="return-value"></a>返回值

返回指示当前记录的编辑状态的值。

### <a name="remarks"></a>备注

|“值”|说明|
|-----------|-----------------|
|`dbEditNone`|未正在进行编辑操作。|
|`dbEditInProgress`|已调用 `Edit`。|
|`dbEditAdd`|已调用 `AddNew`。|

有关相关信息，请参阅 DAO 帮助中的主题"编辑模式属性"。

## <a name="cdaorecordsetgetfieldcount"></a><a name="getfieldcount"></a>CDao记录集：：获取菲尔德计数

调用此成员函数以检索记录集中定义的字段（列）数。

```
short GetFieldCount();
```

### <a name="return-value"></a>返回值

记录集中的字段数。

### <a name="remarks"></a>备注

有关相关信息，请参阅 DAO 帮助中的主题"计数属性"。

## <a name="cdaorecordsetgetfieldinfo"></a><a name="getfieldinfo"></a>CDaoRecordset：获取菲尔德信息

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

### <a name="parameters"></a>参数

*nIndex*<br/>
记录集的"字段"集合中预定义字段的零基索引，用于按索引进行查找。

*菲尔德信息*<br/>
对[CDaoFieldInfo](../../mfc/reference/cdaofieldinfo-structure.md)结构的引用。

*dwInfoOptions*<br/>
指定有关要检索的记录集的信息的选项。 此处列出了可用选项以及它们导致函数返回的内容。 为了获得最佳性能，仅检索所需的信息级别：

- `AFX_DAO_PRIMARY_INFO`（默认）名称、类型、大小、属性

- `AFX_DAO_SECONDARY_INFO`主要信息，加上：序号位置、必需位置、允许零长度、分词顺序、外名、源字段、源表

- `AFX_DAO_ALL_INFO`主要和辅助信息，以及：默认值、验证规则、验证文本

*lpsz名称*<br/>
字段的名称。

### <a name="remarks"></a>备注

函数的一个版本允许您按索引查找字段。 另一个版本允许您按名称查找字段。

有关返回的信息的说明，请参阅[CDaoFieldInfo](../../mfc/reference/cdaofieldinfo-structure.md)结构。 此结构的成员对应于*dwInfoOptions*描述中列出的信息项。 当您在一个级别请求信息时，您也获取任何先前级别的信息。

有关相关信息，请参阅 DAO 帮助中的主题"属性属性"。

## <a name="cdaorecordsetgetfieldvalue"></a><a name="getfieldvalue"></a>CDao 记录集：获取场值

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

### <a name="parameters"></a>参数

*lpsz名称*<br/>
指向包含字段名称的字符串的指针。

*varValue*<br/>
对将存储字段`COleVariant`值的对象的引用。

*nIndex*<br/>
记录集的"字段"集合中字段的零基索引，用于按索引查找。

### <a name="return-value"></a>返回值

该值的`GetFieldValue`两个版本返回包含字段值的[COleVariant](../../mfc/reference/colevariant-class.md)对象。

### <a name="remarks"></a>备注

您可以按名称或位形位置查找字段。

> [!NOTE]
> 调用此成员函数之一`COleVariant`以对象引用为参数，而不是调用返回`COleVariant`对象的版本，效率更高。 为了向后兼容性，将保留此函数的后一个版本。

使用`GetFieldValue`和[SetFieldValue](#setfieldvalue)在运行时动态绑定字段，而不是使用[DoFieldExchange](#dofieldexchange)机制对列进行静态绑定。

`GetFieldValue`和`DoFieldExchange`机制可以结合，以提高性能。 例如，用于`GetFieldValue`检索仅按需需要的值，并将该调用分配给界面中的"更多信息"按钮。

有关相关信息，请参阅 DAO 帮助中的"字段对象"和"值属性"主题。

## <a name="cdaorecordsetgetindexcount"></a><a name="getindexcount"></a>CDao 记录集：获取索引计数

调用此成员函数以确定表类型记录集中可用的索引数。

```
short GetIndexCount();
```

### <a name="return-value"></a>返回值

表类型记录集中的索引数。

### <a name="remarks"></a>备注

`GetIndexCount`可用于循环遍历记录集中的所有索引。 为此，请与`GetIndexCount`[GetIndexInfo](#getindexinfo)结合使用。 如果在动态集类型或快照类型记录集上调用此成员函数，MFC 将引发异常。

有关相关信息，请参阅 DAO 帮助中的主题"属性属性"。

## <a name="cdaorecordsetgetindexinfo"></a><a name="getindexinfo"></a>CDao 记录集：获取索引信息

调用此成员函数以获取有关在记录集基础基表中定义的索引的各种信息。

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

### <a name="parameters"></a>参数

*nIndex*<br/>
表的 Index 集合中的零基索引，用于按数字位置查找。

*索引信息*<br/>
对[CDaoIndexInfo](../../mfc/reference/cdaoindexinfo-structure.md)结构的引用。

*dwInfoOptions*<br/>
指定要检索的索引的信息的选项。 此处列出了可用选项以及它们导致函数返回的内容。 为了获得最佳性能，仅检索所需的信息级别：

- `AFX_DAO_PRIMARY_INFO`（默认）名称、字段信息、字段

- `AFX_DAO_SECONDARY_INFO`主要信息，加上：主信息、唯一信息、群集、忽略 Null、必需、外国

- `AFX_DAO_ALL_INFO`主要和次要信息，加上：不同的计数

*lpsz名称*<br/>
指向索引对象名称的指针，用于按名称查找。

### <a name="remarks"></a>备注

函数的一个版本允许您按索引在集合中的位置查找索引。 另一个版本允许您按名称查找索引。

有关返回的信息的说明，请参阅[CDaoIndexInfo](../../mfc/reference/cdaoindexinfo-structure.md)结构。 此结构的成员对应于*dwInfoOptions*描述中列出的信息项。 当您在一个级别请求信息时，您也获取任何先前级别的信息。

有关相关信息，请参阅 DAO 帮助中的主题"属性属性"。

## <a name="cdaorecordsetgetlastmodifiedbookmark"></a><a name="getlastmodifiedbookmark"></a>CDao 记录集：：获取上次修改的书签

调用此成员函数以检索最近添加或更新的记录的书签。

```
COleVariant GetLastModifiedBookmark();
```

### <a name="return-value"></a>返回值

包含`COleVariant`指示最近添加或更改的记录的书签。

### <a name="remarks"></a>备注

创建或打开记录集对象时，如果每个记录支持它们，则其每个记录已具有唯一的书签。 调用[GetBookmark](#getbookmark)以确定记录集是否支持书签。 如果记录集不支持书签，则引发 。 `CDaoException`

添加记录时，它将显示在记录集的末尾，而不是当前记录。 要使新记录成为当前记录，请`GetLastModifiedBookmark`调用，然后`SetBookmark`调用以返回到新添加的记录。

有关相关信息，请参阅 DAO 帮助中的主题"上次修改属性"。

## <a name="cdaorecordsetgetlockingmode"></a><a name="getlockingmode"></a>CDao 记录集：：获取锁定模式

调用此成员函数以确定记录集有效的锁定类型。

```
BOOL GetLockingMode();
```

### <a name="return-value"></a>返回值

如果锁定类型为悲观，则非零，否则为 0 表示乐观记录锁定。

### <a name="remarks"></a>备注

当悲观锁定生效时，包含您正在编辑的记录的数据页在调用[Edit](#edit)成员函数后立即锁定。 当您调用["更新](#update)"或"[关闭](#close)"成员功能或任何"移动"或"查找"操作时，页面将解锁。

当乐观锁定生效时，包含记录的数据页仅在使用`Update`成员函数更新记录时锁定。

使用 ODBC 数据源时，锁定模式始终乐观。

有关相关信息，请参阅 DAO 帮助中的"锁定属性"和"多用户应用程序中的锁定行为"主题。

## <a name="cdaorecordsetgetname"></a><a name="getname"></a>CDao 记录集：获取名称

调用此成员函数以检索记录集的名称。

```
CString GetName();
```

### <a name="return-value"></a>返回值

包含`CString`记录集的名称。

### <a name="remarks"></a>备注

记录集的名称必须以字母开头，最多只能包含 40 个字符。 它可以包括数字和下划线字符，但不能包括标点符号或空格。

有关相关信息，请参阅 DAO 帮助中的主题"名称属性"。

## <a name="cdaorecordsetgetparamvalue"></a><a name="getparamvalue"></a>CDao 记录集：：获取帕拉姆价值

调用此成员函数以检索存储在基础 DAOParameter 对象中的指定参数的当前值。

```
virtual COleVariant GetParamValue(int nIndex);
virtual COleVariant GetParamValue(LPCTSTR lpszName);
```

### <a name="parameters"></a>参数

*nIndex*<br/>
参数在基础 DAO 参数对象中的数值位置。

*lpsz名称*<br/>
所需的值的参数的名称。

### <a name="return-value"></a>返回值

包含参数值的类[COleVariant](../../mfc/reference/colevariant-class.md)的对象。

### <a name="remarks"></a>备注

您可以按名称或参数在集合中的数值位置访问参数。

有关相关信息，请参阅 DAO 帮助中的主题"参数对象"。

## <a name="cdaorecordsetgetpercentposition"></a><a name="getpercentposition"></a>CDao 记录集：获取百分比位置

使用动态集类型或快照类型记录集时，如果在完全填充记录集之前调用`GetPercentPosition`，则移动量与调用[GetRecordCount](#getrecordcount)指示的访问记录数相关。

```
float GetPercentPosition();
```

### <a name="return-value"></a>返回值

介于 0 和 100 之间的数字，该数字根据记录集中记录中记录的百分比指示记录集对象中当前记录的大致位置。

### <a name="remarks"></a>备注

您可以通过调用[MoveLast](#movelast)来移动到最后一个记录以完成所有记录集的填充，但这可能需要大量时间。

您可以调用`GetPercentPosition`所有三种类型的记录集对象，包括没有索引的表。 但是，您不能调用仅`GetPercentPosition`转发滚动快照，也不能调用从针对外部数据库的传递查询打开的记录集上。 如果没有当前记录，或者他当前记录已被删除，则引发 a。 `CDaoException`

有关相关信息，请参阅 DAO 帮助中的主题"百分比位置属性"。

## <a name="cdaorecordsetgetrecordcount"></a><a name="getrecordcount"></a>CDao 记录集：：获取记录计数

调用此成员函数，了解已访问的记录集中的记录数。

```
long GetRecordCount();
```

### <a name="return-value"></a>返回值

返回在记录集对象中访问的记录数。

### <a name="remarks"></a>备注

`GetRecordCount`不指示在已访问所有记录之前，动态集类型或快照类型记录集中包含多少条记录。 此成员函数调用可能需要大量时间才能完成。

访问最后一条记录后，返回值指示记录集中未删除记录的总数。 要强制访问最后一个记录，请调用 记录`MoveLast`集`FindLast`的 或 成员函数。 您还可以使用 SQL 计数来确定查询将返回的记录的大致数量。

当应用程序删除动态集类型记录集中的记录时，返回`GetRecordCount`值将减小。 但是，在将当前记录定位到已删除的记录之前`GetRecordCount`，其他用户删除的记录不会反映在该记录上。 如果执行影响记录计数的事务，然后回滚事务，`GetRecordCount`则不会反映剩余记录的实际数量。

`GetRecordCount`快照类型记录集的值不受基础表中的更改的影响。

表类型记录`GetRecordCount`集的值反映表中记录的近似数量，并且随着表记录的添加和删除而立即受到影响。

没有记录的记录集返回值 0。 使用附加的表或 ODBC 数据库`GetRecordCount`时，始终返回 - 1。 在`Requery`记录集中调用成员函数将重置的值，`GetRecordCount`就像重新执行查询一样。

有关相关信息，请参阅 DAO 帮助中的主题"记录计数属性"。

## <a name="cdaorecordsetgetsql"></a><a name="getsql"></a>CDao 记录集：：获取SQL

调用此成员函数获取用于在打开记录集时用于选择记录集记录的 SQL 语句。

```
CString GetSQL() const;
```

### <a name="return-value"></a>返回值

包含`CString`SQL 语句的 。

### <a name="remarks"></a>备注

这通常是 SQL **SELECT**语句。

返回`GetSQL`的字符串通常不同于您可能传递给*lpszSQL*参数中的记录集到[Open](#open)成员函数的任何字符串。 这是因为记录集基于您传递给`Open`的内容构建完整的 SQL 语句，以及您在m_strFilter中指定的内容以及[数据](#m_strfilter)成员[m_strSort。](#m_strsort)

> [!NOTE]
> 仅在调用`Open`后调用此成员函数。

有关相关信息，请参阅 DAO 帮助中的主题"SQL 属性"。

## <a name="cdaorecordsetgettype"></a><a name="gettype"></a>CDao 记录集：获取类型

打开记录集后调用此成员函数以确定记录集对象的类型。

```
short GetType();
```

### <a name="return-value"></a>返回值

指示记录集类型的以下值之一：

- `dbOpenTable`表类型记录集

- `dbOpenDynaset`动态集类型记录集

- `dbOpenSnapshot`快照类型记录集

### <a name="remarks"></a>备注

有关相关信息，请参阅 DAO 帮助中的主题"类型属性"。

## <a name="cdaorecordsetgetvalidationrule"></a><a name="getvalidationrule"></a>CDao 记录集：：获取验证规则

调用此成员函数以确定用于验证数据的规则。

```
CString GetValidationRule();
```

### <a name="return-value"></a>返回值

包含`CString`值的对象，用于在更改数据或添加到表中时验证记录中的数据。

### <a name="remarks"></a>备注

此规则基于文本，并在每次更改基础表时应用。 如果数据不合法，MFC 将引发异常。 返回的错误消息是基础字段对象的验证文本属性的文本（如果指定）或基础字段对象的验证规则属性指定的表达式的文本。 您可以调用[Get验证文本](#getvalidationtext)以获取错误消息的文本。

例如，记录中需要月份当天的字段可能具有验证规则，如"天与 1 和 31"。

有关相关信息，请参阅 DAO 帮助中的主题"验证规则属性"。

## <a name="cdaorecordsetgetvalidationtext"></a><a name="getvalidationtext"></a>CDao 记录集：：获取验证文本

调用此成员函数以检索基础字段对象的验证文本属性的文本。

```
CString GetValidationText();
```

### <a name="return-value"></a>返回值

包含`CString`消息文本的对象，如果字段的值不符合基础字段对象的验证规则，则显示该消息的文本。

### <a name="remarks"></a>备注

有关相关信息，请参阅 DAO 帮助中的主题"验证文本属性"。

## <a name="cdaorecordsetisbof"></a><a name="isbof"></a>CDao 记录集：IsBOF

在从记录滚动到记录之前，请调用此成员函数，以了解您是否在记录集的第一个记录之前。

```
BOOL IsBOF() const;
```

### <a name="return-value"></a>返回值

如果记录集不包含任何记录，或者在第一个记录之前向后滚动，则非零;否则 0。

### <a name="remarks"></a>备注

还可以一起`IsEOF`调用`IsBOF`以确定记录集是否包含任何记录或为空。 调用 后立即`Open`调用，如果记录集不包含任何记录，`IsBOF`则返回非零。 当您打开至少具有一条记录的记录集时，第一个记录是当前记录，并`IsBOF`返回 0。

如果第一条记录是当前记录，而您调用`MovePrev``IsBOF`时，将随后返回非零。 如果`IsBOF`返回非零，并且调用`MovePrev`，将引发异常。 如果`IsBOF`返回非零，则当前记录未定义，任何需要当前记录的操作都将导致异常。

特定方法对`IsBOF`和`IsEOF`设置的影响：

- 内部`Open*`调用通过调用`MoveFirst`使记录中的第一个记录成为当前记录。 因此，调用`Open`一组空的记录会导致`IsBOF`并`IsEOF`返回非零。 （有关失败`MoveFirst`或`MoveLast`调用的行为，请参阅下表。

- 成功查找记录的所有移动操作都会导致两者`IsBOF`并`IsEOF`返回 0。

- `AddNew`成功插入新记录的`Update`调用后跟调用将导致`IsBOF`返回 0，但仅当已为非零时`IsEOF`才会返回 0。 的状态`IsEOF`将保持不变。 根据 Microsoft Jet 数据库引擎的定义，空记录集的当前记录指针位于文件的末尾，因此在当前记录之后插入任何新记录。

- 任何`Delete`调用（即使它从记录集中中删除唯一的剩余记录）也不会更改 或`IsBOF``IsEOF`的值。

此表显示允许使用 的不同组合的`IsBOF`/ `IsEOF`Move 操作。

||首先移动，移动最后|MovePrev，<br /><br /> 移动< 0|移动 0|移动下一个，<br /><br /> 移动> 0|
|------|-------------------------|-----------------------------|------------|-----------------------------|
|`IsBOF`*非零，<br /><br /> `IsEOF`=0|允许|异常|异常|允许|
|`IsBOF`=0,<br /><br /> `IsEOF`*非零|允许|允许|异常|异常|
|两者均无零|异常|异常|异常|异常|
|两者均为 0|允许|允许|允许|允许|

允许 Move 操作并不意味着操作将成功找到记录。 它只是指示尝试执行指定的 Move 操作是允许的，不会生成异常。 `IsBOF`和`IsEOF`成员函数的值可能会因尝试移动而更改。

下表中显示了未找到记录对`IsBOF`和 和`IsEOF`设置 值的 Move 操作的效果。

||ISBOF|伊塞OF|
|------|-----------|-----------|
|`MoveFirst`, `MoveLast`|零|零|
|`Move` 0|没有变化|没有变化|
|`MovePrev`， `Move` < 0|零|没有变化|
|`MoveNext`， `Move` > 0|没有变化|零|

有关相关信息，请参阅 DAO 帮助中的"BOF，EOF 属性"主题。

## <a name="cdaorecordsetisdeleted"></a><a name="isdeleted"></a>CDao 记录集：已删除

调用此成员函数以确定当前记录是否已被删除。

```
BOOL IsDeleted() const;
```

### <a name="return-value"></a>返回值

如果记录集位于已删除的记录上，则非零;否则 0。

### <a name="remarks"></a>备注

如果滚动到记录并`IsDeleted`返回 TRUE（非零），则必须滚动到其他记录，然后才能执行任何其他记录集操作。

> [!NOTE]
> 您无需检查快照或表类型记录集中的记录的已删除状态。 由于无法从快照中删除记录，因此无需调用`IsDeleted`。 对于表类型的记录集，删除的记录实际上将从记录集中删除。 一旦您、其他用户或其他记录集中删除了记录，您就无法回滚到该记录。 因此，无需调用`IsDeleted`。

从动态集中删除记录时，该记录将从记录集中删除，并且无法回滚到该记录。 但是，如果动态集中的记录被其他用户删除，或者基于同一表的另一个记录集中删除，则当您以后滚动到该`IsDeleted`记录时，将返回 TRUE。

有关相关信息，请参阅 DAO 帮助中的"删除方法"、"上次修改属性"和"编辑模式属性"的主题。

## <a name="cdaorecordsetiseof"></a><a name="iseof"></a>CDao 记录集：：IsEOF

在从记录滚动到记录时调用此成员函数，以了解您是否超出了记录集的最后一条记录。

```
BOOL IsEOF() const;
```

### <a name="return-value"></a>返回值

如果记录集不包含任何记录，或者您滚动超过最后一条记录，则为非零;否则 0。

### <a name="remarks"></a>备注

还可以调用`IsEOF`以确定记录集是否包含任何记录或为空。 调用 后立即`Open`调用，如果记录集不包含任何记录，`IsEOF`则返回非零。 当您打开至少具有一条记录的记录集时，第一个记录是当前记录，并`IsEOF`返回 0。

如果最后一条记录是您调用`MoveNext`时的当前记录，`IsEOF`则随后将返回非零。 如果`IsEOF`返回非零，并且调用`MoveNext`，将引发异常。 如果`IsEOF`返回非零，则当前记录未定义，任何需要当前记录的操作都将导致异常。

特定方法对`IsBOF`和`IsEOF`设置的影响：

- 内部`Open`调用通过调用`MoveFirst`使记录中的第一个记录成为当前记录。 因此，调用`Open`一组空的记录会导致`IsBOF`并`IsEOF`返回非零。 （有关失败`MoveFirst`呼叫的行为，请参阅下表。

- 成功查找记录的所有移动操作都会导致两者`IsBOF`并`IsEOF`返回 0。

- `AddNew`成功插入新记录的`Update`调用后跟调用将导致`IsBOF`返回 0，但仅当已为非零时`IsEOF`才会返回 0。 的状态`IsEOF`将保持不变。 根据 Microsoft Jet 数据库引擎的定义，空记录集的当前记录指针位于文件的末尾，因此在当前记录之后插入任何新记录。

- 任何`Delete`调用（即使它从记录集中中删除唯一的剩余记录）也不会更改 或`IsBOF``IsEOF`的值。

此表显示允许使用 的不同组合的`IsBOF`/ `IsEOF`Move 操作。

||首先移动，移动最后|MovePrev，<br /><br /> 移动< 0|移动 0|移动下一个，<br /><br /> 移动> 0|
|------|-------------------------|-----------------------------|------------|-----------------------------|
|`IsBOF`*非零，<br /><br /> `IsEOF`=0|允许|异常|异常|允许|
|`IsBOF`=0,<br /><br /> `IsEOF`*非零|允许|允许|异常|异常|
|两者均无零|异常|异常|异常|异常|
|两者均为 0|允许|允许|允许|允许|

允许 Move 操作并不意味着操作将成功找到记录。 它只是指示尝试执行指定的 Move 操作是允许的，不会生成异常。 `IsBOF`和`IsEOF`成员函数的值可能会由于尝试的 Move 而改变。

下表中显示了未找到记录对`IsBOF`和 和`IsEOF`设置 值的 Move 操作的效果。

||ISBOF|伊塞OF|
|------|-----------|-----------|
|`MoveFirst`, `MoveLast`|零|零|
|`Move` 0|没有变化|没有变化|
|`MovePrev`， `Move` < 0|零|没有变化|
|`MoveNext`， `Move` > 0|没有变化|零|

有关相关信息，请参阅 DAO 帮助中的"BOF，EOF 属性"主题。

## <a name="cdaorecordsetisfielddirty"></a><a name="isfielddirty"></a>CDao 记录集：：IsfieldDirty

调用此成员函数以确定动态集的指定字段数据成员是否已标记为"脏"（已更改）。

```
BOOL IsFieldDirty(void* pv);
```

### <a name="parameters"></a>参数

*光伏*<br/>
指向要检查其状态的字段数据成员的指针，或 NULL 以确定任何字段是否脏。

### <a name="return-value"></a>返回值

如果指定的字段数据成员标记为脏，则非零;否则 0。

### <a name="remarks"></a>备注

`Update`当对 成员`CDaoRecordset`函数的调用（在对`Edit`或`AddNew`调用 后）更新当前记录时，所有脏字段数据成员中的数据都将传输到数据源上的记录。 有了这些知识，您可以执行进一步步骤，例如取消标记字段数据成员以标记列，以便不会将其写入数据源。

`IsFieldDirty`通过`DoFieldExchange`实现 。

## <a name="cdaorecordsetisfieldnull"></a><a name="isfieldnull"></a>CDao记录集：：IsfieldNull

调用此成员函数以确定记录集的指定字段数据成员是否已标记为 Null。

```
BOOL IsFieldNull(void* pv);
```

### <a name="parameters"></a>参数

*光伏*<br/>
指向要检查其状态的字段数据成员的指针，或 NULL 以确定是否有任何字段为 Null。

### <a name="return-value"></a>返回值

如果指定的字段数据成员标记为 Null，则非零;否则 0。

### <a name="remarks"></a>备注

（在数据库术语中，Null 表示"没有值"，并且与 C++ 中的 NULL 不同。如果字段数据成员标记为 Null，则将其解释为当前记录的列，该列没有值。

> [!NOTE]
> 在某些情况下，使用`IsFieldNull`效率可能很低，如下代码示例所示：

[!code-cpp[NVC_MFCDatabase#5](../../mfc/codesnippet/cpp/cdaorecordset-class_5.cpp)]

> [!NOTE]
> 如果使用动态记录绑定，而不派生于`CDaoRecordset`，请确保使用VT_NULL如示例中所示。

## <a name="cdaorecordsetisfieldnullable"></a><a name="isfieldnullable"></a>CDao 记录集：：可字段空

调用此成员函数以确定指定的字段数据成员是否为"空"（可以设置为 Null 值;是否可以设置为 Null 值。"C++ NULL 与 Null 不同，在数据库术语中，Null 表示"没有值"）。

```
BOOL IsFieldNullable(void* pv);
```

### <a name="parameters"></a>参数

*光伏*<br/>
指向要检查其状态的字段数据成员的指针，或 NULL 以确定是否有任何字段为 Null。

### <a name="return-value"></a>返回值

如果指定的字段数据成员可以为 Null，则非零;否则 0。

### <a name="remarks"></a>备注

不能为空的字段必须具有值。 如果在添加或更新记录时尝试将此类字段设置为 Null，数据源将拒绝添加或更新，并将`Update`引发异常。 当您调用`Update`时，则出现异常，而不是调用`SetFieldNull`时出现。

## <a name="cdaorecordsetisopen"></a><a name="isopen"></a>CDao 记录集：：是打开的

调用此成员函数以确定记录集是否打开。

```
BOOL IsOpen() const;
```

### <a name="return-value"></a>返回值

以前已调用记录集对象的`Open`或`Requery`成员函数，并且记录集尚未关闭，则非零;否则 0。

### <a name="remarks"></a>备注

## <a name="cdaorecordsetm_bcheckcachefordirtyfields"></a><a name="m_bcheckcachefordirtyfields"></a>CDaoRecordset：m_bCheckCacheForDirtyFields

包含一个标志，指示缓存的字段是否自动标记为脏（更改）和 Null。

### <a name="remarks"></a>备注

标志默认为 TRUE。 此数据成员中的设置控制整个双缓冲机制。 如果将标志设置为 TRUE，则可以使用 DFX 机制逐字段关闭缓存。 如果将标志设置为 FALSE，则必须调用`SetFieldDirty`自己。 `SetFieldNull`

在调用`Open`之前设置此数据成员。 此机制主要是为了方便使用。 性能可能较慢，因为在进行更改时对字段进行了双重缓冲。

## <a name="cdaorecordsetm_nfields"></a><a name="m_nfields"></a>CDao 记录集：：m_nFields

包含记录集类中的字段数据成员数以及记录组从数据源中选择的列数。

### <a name="remarks"></a>备注

记录集类的构造函数必须用正确数量的静态`m_nFields`绑定字段进行初始化。 当您使用它声明记录集类时，ClassWizard 会为您编写此初始化。 您也可以手动编写。

框架使用此数字来管理字段数据成员与数据源上当前记录的相应列之间的交互。

> [!NOTE]
> 此编号必须对应于`DoFieldExchange``SetFieldType`使用 参数`CDaoFieldExchange::outputColumn`调用 后注册的输出列数。

可以通过`CDaoRecordset::GetFieldValue`和`CDaoRecordset::SetFieldValue`动态绑定列。 如果这样做，则不需要增加计数`m_nFields`以反映`DoFieldExchange`成员函数中的 DFX 函数调用数。

## <a name="cdaorecordsetm_nparams"></a><a name="m_nparams"></a>CDao 记录集：：m_nParams

包含记录集类中的参数数据成员数 - 记录集查询传递的参数数。

### <a name="remarks"></a>备注

如果记录集类具有任何参数数据成员，则类的构造函数必须用正确的数字初始化*m_nParams。* *值m_nParams*默认值为 0。 如果添加参数数据成员（您必须手动执行），还必须在类构造函数中手动添加初始化，以反映参数数（参数数量必须至少与*m_strFilter*或*m_strSort*字符串中的''占位符数相同）。

框架在参数化记录集的查询时使用此数字。

> [!NOTE]
> 此号码必须对应于`DoFieldExchange``SetFieldType`使用 参数`CFieldExchange::param`调用 后注册的"参数"数。

有关相关信息，请参阅 DAO 帮助中的主题"参数对象"。

## <a name="cdaorecordsetm_pdaorecordset"></a><a name="m_pdaorecordset"></a>CDao 记录集：：m_pDAORecordset

包含指向对象基础的 DAO 记录集对象的 OLE 接口的`CDaoRecordset`指针。

### <a name="remarks"></a>备注

如果需要直接访问 DAO 接口，请使用此指针。

有关相关信息，请参阅 DAO 帮助中的主题"记录集对象"。

## <a name="cdaorecordsetm_pdatabase"></a><a name="m_pdatabase"></a>CDao 记录集：：m_pDatabase

包含指向记录集连接到数据源`CDaoDatabase`的对象的指针。

### <a name="remarks"></a>备注

此变量以两种方式设置。 通常，在构造记录集对象时，将`CDaoDatabase`指针传递给已打开的对象。 如果改为传递 NULL，`CDaoRecordset`则为您`CDaoDatabase`创建一个对象并打开它。 在这两种情况下，`CDaoRecordset`都在此变量中存储指针。

通常，您不需要直接使用存储在 中的`m_pDatabase`指针。 但是，如果将自己的扩展写入`CDaoRecordset`，则可能需要使用指针。 例如，如果抛出自己的`CDaoException`（s），则可能需要指针。

有关相关信息，请参阅 DAO 帮助中的主题"数据库对象"。

## <a name="cdaorecordsetm_strfilter"></a><a name="m_strfilter"></a>CDao 记录集：：m_strFilter

包含用于构造 SQL 语句的**WHERE**子句的字符串。

### <a name="remarks"></a>备注

它不包括用于筛选记录集的保留字**WHERE。** 此数据成员的使用不适用于表类型的记录集。 使用`CDaoQueryDef`指针`m_strFilter`打开记录集时，使用 没有任何效果。

筛选包含日期的字段时，使用美国日期格式（月日年），即使您没有使用 Microsoft Jet 数据库引擎的美国版本;否则，数据可能无法按预期进行筛选。

有关相关信息，请参阅 DAO 帮助中的主题"筛选属性"。

## <a name="cdaorecordsetm_strsort"></a><a name="m_strsort"></a>CDao 记录集：：m_strSort

包含包含 SQL 语句的**ORDERBY**子句的字符串，而不保留单词**ORDERBY**。

### <a name="remarks"></a>备注

您可以对动态集和快照类型的记录集对象进行排序。

不能对表类型记录集对象进行排序。 要确定表类型记录集的排序顺序，请调用[SetCurrentIndex](#setcurrentindex)。

使用`CDaoQueryDef`指针打开记录集时，使用*m_strSort*不起作用。

有关相关信息，请参阅 DAO 帮助中的主题"排序属性"。

## <a name="cdaorecordsetmove"></a><a name="move"></a>CDao 记录集：：移动

调用此成员函数以定位当前记录中的记录集*lRows*记录。

```
virtual void Move(long lRows);
```

### <a name="parameters"></a>参数

*lRows*<br/>
要向前或向后移动的记录数。 正值向前移动，接近记录集的末尾。 负值向后移动，向起点移动。

### <a name="remarks"></a>备注

您可以向前或向后移动。 `Move( 1 )`等效于`MoveNext`和`Move( -1 )`等效于`MovePrev`。

> [!CAUTION]
> 如果记录集没有`Move`记录，则调用任何函数都会引发异常。 通常，调用 Move `IsBOF` `IsEOF`操作之前，以确定记录集是否有任何记录。 呼叫`Open`或`Requery`后，请呼叫`IsBOF`或`IsEOF`。

> [!NOTE]
> 如果滚动过记录集的开头或结尾`IsBOF`（或`IsEOF`返回非零），则调用`Move`引发 。 `CDaoException`

> [!NOTE]
> 如果在更新或添加当前记录`Move`时调用任何函数，则更新将丢失，而不会发出警告。

当您调用`Move`仅转发滚动快照时 *，lRows*参数必须是正整数，不允许使用书签，因此您只能向前移动。

要在记录中创建第一条、最后记录、上一条或上一条记录，请`MoveFirst`调用`MoveLast` `MoveNext`、、`MovePrev`或成员函数。

有关相关信息，请参阅 DAO 帮助中的"移动方法"和"移动第一、移动最后一个、移动下一个、移动上一个方法"的主题。

## <a name="cdaorecordsetmovefirst"></a><a name="movefirst"></a>CDao 记录集：：先移动

调用此成员函数以使记录集中的第一个记录（如果有）成为当前记录。

```
void MoveFirst();
```

### <a name="remarks"></a>备注

打开记录集后，不必`MoveFirst`立即调用。 此时，第一条记录（如果有）自动是当前记录。

> [!CAUTION]
> 如果记录集没有`Move`记录，则调用任何函数都会引发异常。 通常，调用 Move `IsBOF` `IsEOF`操作之前，以确定记录集是否有任何记录。 呼叫`Open`或`Requery`后，请呼叫`IsBOF`或`IsEOF`。

> [!NOTE]
> 如果在更新或添加当前记录`Move`时调用任何函数，则更新将丢失，而不会发出警告。

使用`Move`函数在不应用条件的情况下从记录移动到记录。 使用 Find 操作查找满足特定条件的动态集类型或快照类型记录集对象中的记录。 要在表类型记录集对象中查找记录，请调用`Seek`。

如果记录集引用表类型的记录集，则移动遵循表的当前索引。 可以使用基础 DAO 对象的 Index 属性设置当前索引。 如果未设置当前索引，则未定义返回的记录的顺序。

如果基于`MoveLast`SQL 查询或查询def对记录集对象进行调用，则强制完成查询，并且记录集对象已完全填充。

不能使用仅转发`MoveFirst`滚动`MovePrev`快照调用 或 成员函数。

要向前或向后移动记录集对象中当前记录的位置特定数量的记录，请调用`Move`。

有关相关信息，请参阅 DAO 帮助中的"移动方法"和"移动第一、移动最后一个、移动下一个、移动上一个方法"的主题。

## <a name="cdaorecordsetmovelast"></a><a name="movelast"></a>CDao 记录集：：移动上次

调用此成员函数，使记录中的最后一条记录（如果有）成为当前记录。

```
void MoveLast();
```

### <a name="remarks"></a>备注

> [!CAUTION]
> 如果记录集没有`Move`记录，则调用任何函数都会引发异常。 通常，调用 Move `IsBOF` `IsEOF`操作之前，以确定记录集是否有任何记录。 呼叫`Open`或`Requery`后，请呼叫`IsBOF`或`IsEOF`。

> [!NOTE]
> 如果在更新或添加当前记录`Move`时调用任何函数，则更新将丢失，而不会发出警告。

使用`Move`函数在不应用条件的情况下从记录移动到记录。 使用 Find 操作查找满足特定条件的动态集类型或快照类型记录集对象中的记录。 要在表类型记录集对象中查找记录，请调用`Seek`。

如果记录集引用表类型的记录集，则移动遵循表的当前索引。 可以使用基础 DAO 对象的 Index 属性设置当前索引。 如果未设置当前索引，则未定义返回的记录的顺序。

如果基于`MoveLast`SQL 查询或查询def对记录集对象进行调用，则强制完成查询，并且记录集对象已完全填充。

要向前或向后移动记录集对象中当前记录的位置特定数量的记录，请调用`Move`。

有关相关信息，请参阅 DAO 帮助中的"移动方法"和"移动第一、移动最后一个、移动下一个、移动上一个方法"的主题。

## <a name="cdaorecordsetmovenext"></a><a name="movenext"></a>CDao 记录集：：移动下一个

调用此成员函数以使记录集中的下一条记录成为当前记录。

```
void MoveNext();
```

### <a name="remarks"></a>备注

建议您在尝试移动到上一`IsBOF`条记录之前调用。 调用 将`MovePrev`引发`CDaoException`if`IsBOF`返回非零，指示您已在第一个记录之前滚动，或者记录集未选择任何记录。

> [!CAUTION]
> 如果记录集没有`Move`记录，则调用任何函数都会引发异常。 通常，调用 Move `IsBOF` `IsEOF`操作之前，以确定记录集是否有任何记录。 呼叫`Open`或`Requery`后，请呼叫`IsBOF`或`IsEOF`。

> [!NOTE]
> 如果在更新或添加当前记录`Move`时调用任何函数，则更新将丢失，而不会发出警告。

使用`Move`函数在不应用条件的情况下从记录移动到记录。 使用 Find 操作查找满足特定条件的动态集类型或快照类型记录集对象中的记录。 要在表类型记录集对象中查找记录，请调用`Seek`。

如果记录集引用表类型的记录集，则移动遵循表的当前索引。 可以使用基础 DAO 对象的 Index 属性设置当前索引。 如果未设置当前索引，则未定义返回的记录的顺序。

要向前或向后移动记录集对象中当前记录的位置特定数量的记录，请调用`Move`。

有关相关信息，请参阅 DAO 帮助中的"移动方法"和"移动第一、移动最后一个、移动下一个、移动上一个方法"的主题。

## <a name="cdaorecordsetmoveprev"></a><a name="moveprev"></a>CDao记录集：：MovePrev

调用此成员函数以使记录中以前的记录成为当前记录。

```
void MovePrev();
```

### <a name="remarks"></a>备注

建议您在尝试移动到上一`IsBOF`条记录之前调用。 调用 将`MovePrev`引发`CDaoException`if`IsBOF`返回非零，指示您已在第一个记录之前滚动，或者记录集未选择任何记录。

> [!CAUTION]
> 如果记录集没有`Move`记录，则调用任何函数都会引发异常。 通常，调用 Move `IsBOF` `IsEOF`操作之前，以确定记录集是否有任何记录。 呼叫`Open`或`Requery`后，请呼叫`IsBOF`或`IsEOF`。

> [!NOTE]
> 如果在更新或添加当前记录`Move`时调用任何函数，则更新将丢失，而不会发出警告。

使用`Move`函数在不应用条件的情况下从记录移动到记录。 使用 Find 操作查找满足特定条件的动态集类型或快照类型记录集对象中的记录。 要在表类型记录集对象中查找记录，请调用`Seek`。

如果记录集引用表类型的记录集，则移动遵循表的当前索引。 可以使用基础 DAO 对象的 Index 属性设置当前索引。 如果未设置当前索引，则未定义返回的记录的顺序。

不能使用仅转发`MoveFirst`滚动`MovePrev`快照调用 或 成员函数。

要向前或向后移动记录集对象中当前记录的位置特定数量的记录，请调用`Move`。

有关相关信息，请参阅 DAO 帮助中的"移动方法"和"移动第一、移动最后一个、移动下一个、移动上一个方法"的主题。

## <a name="cdaorecordsetopen"></a><a name="open"></a>CDao 记录集：：打开

必须调用此成员函数才能检索记录集的记录。

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

### <a name="parameters"></a>参数

*n 开放类型*<br/>
以下值之一：

- `dbOpenDynaset`具有双向滚动的动态集类型记录集。 这是默认值。

- `dbOpenTable`具有双向滚动的表类型记录集。

- `dbOpenSnapshot`具有双向滚动的快照类型记录集。

*lpszSQL*<br/>
包含以下之一的字符串指针：

- NULL 指针。

- 一个或多个表def和/或查询defs的名称（逗号分隔）。

- SQL **SELECT**语句（可选使用 SQL **WHERE**或**ORDERBY**子句）。

- 传递查询。

*n选项*<br/>
下面列出的一个或多个选项。 默认值为 0。 可能的值如下所示：

- `dbAppendOnly`您只能追加新记录（仅限动态设置类型记录集）。 此选项表示实际上只能追加记录。 MFC ODBC 数据库类具有仅追加选项，允许检索和追加记录。

- `dbForwardOnly`记录集是仅转发滚动快照。

- `dbSeeChanges`如果其他用户正在更改您正在编辑的数据，则生成异常。

- `dbDenyWrite`其他用户无法修改或添加记录。

- `dbDenyRead`其他用户无法查看记录（仅限表类型记录集）。

- `dbReadOnly`您只能查看记录;其他用户可以修改它们。

- `dbInconsistent`允许不一致的更新（仅限动态集类型记录集）。

- `dbConsistent`仅允许一致的更新（仅限动态集类型记录集）。

> [!NOTE]
> 常量是`dbConsistent``dbInconsistent`互斥的。 您可以使用其中一个或另一个，但不能同时在 给定实例中使用`Open`。

*pTableDef*<br/>
指向[CDaoTableDef](../../mfc/reference/cdaotabledef-class.md)对象的指针。 此版本仅适用于表类型的记录集。 使用此选项时，`CDaoDatabase`不使用用于构造 的`CDaoRecordset`指针;而是使用表def所在的数据库。

*pQueryDef*<br/>
指向[CDaoQueryDef](../../mfc/reference/cdaoquerydef-class.md)对象的指针。 此版本仅适用于动态集类型和快照类型记录集。 使用此选项时，`CDaoDatabase`不使用用于构造 的`CDaoRecordset`指针;而是使用查询def所在的数据库。

### <a name="remarks"></a>备注

在调用`Open`之前，必须构造记录集对象。 有若干方法可实现此操作：

- 构造记录集对象时，将指针传递给已打开`CDaoDatabase`的对象。

- 构造记录集对象时，将指针传递给未打开`CDaoDatabase`的对象。 记录集将打开对象`CDaoDatabase`，但不会在记录集对象关闭时关闭该对象。

- 构造记录集对象时，传递 NULL 指针。 记录集对象调用`GetDefaultDBName`以获取 Microsoft Access 的名称。要打开的 MDB 文件。 然后，记录集打开对象`CDaoDatabase`，只要记录集处于打开状态，它就会保持打开状态。 当您调用`Close`记录集时，`CDaoDatabase`对象也会关闭。

    > [!NOTE]
    >  当记录集打开对象时`CDaoDatabase`，它将打开具有非独占访问权限的数据源。

对于使用`Open`*lpszSQL*参数的版本，一旦记录集打开，您可以通过多种方式之一检索记录。 第一个选项是在 您的`DoFieldExchange`中具有 DFX 函数。 第二个选项是通过调用`GetFieldValue`成员函数使用动态绑定。 这些选项可以单独实现或组合实现。 如果它们合并在一起，您必须在调用 时自己传递 SQL 语句`Open`。

当您使用对象中`Open`传递位置的第二个版本`CDaoTableDef`时，生成的列将可供您通过`DoFieldExchange`DFX 机制绑定，和/或通过 动态绑定。 `GetFieldValue`

> [!NOTE]
> 只能使用对象`CDaoTableDef`对`Open`表类型的记录集进行调用。

当您`Open`使用在`CDaoQueryDef`对象中传递的位置的第三个版本时，将执行该查询，并且生成的列将可供您通过`DoFieldExchange`DFX 机制绑定，和/或通过 动态绑定。 `GetFieldValue`

> [!NOTE]
> 只能使用`CDaoQueryDef`对象调用`Open`动态集类型和快照类型记录集。

对于使用`lpszSQL`参数的第`Open`一个版本，将根据下表中显示的条件选择记录。

|`lpszSQL` 参数的值|所选记录由|示例|
|--------------------------------------|----------------------------------------|-------------|
|Null|返回`GetDefaultSQL`的字符串。||
|一个或多个表def和/或查询def名称的逗号分隔列表。|中表示的所有列`DoFieldExchange`。|`"Customer"`|
|**从**表列表中**选择**列列表|指定表def 和/或查询def 的指定列。|`"SELECT CustId, CustName`<br /><br /> `FROM Customer"`|

通常的程序是将 NULL 传递给`Open`。在这种情况下，`Open`调用`GetDefaultSQL`，ClassWizard 在创建`CDaoRecordset`派生类时生成的可重写成员函数。 此值提供在 ClassWizard 中指定的表def 和/或查询def 名称。 您可以改为在*lpszSQL*参数中指定其他信息。

无论您通过什么，`Open`都会构造查询的最终 SQL 字符串（该字符串可能将 SQL **WHERE**和**ORDERBY**子句追加到您传递的*lpszSQL*字符串上），然后执行查询。 您可以通过调用`GetSQL``Open`后调用 来检查构造的字符串。

记录集类的字段数据成员绑定到所选数据的列。 如果返回任何记录，则第一条记录将成为当前记录。

如果要为记录集设置选项（如筛选器或排序）设置`m_strSort`或`m_strFilter`构造记录集对象之后，但在调用`Open`之前设置 。 如果要在记录集打开后刷新记录集中的记录，请调用`Requery`。

如果调用`Open`动态集类型或快照类型记录集，或者数据源引用表示附加表的 SQL 语句或表def，则无法用于类型参数;如果数据源引用的 SQL 语句或`dbOpenTable`表def 表示附加表，则无法用于类型参数;如果数据源引用的 SQL 语句或表def 表示附加表，则无法用于类型参数。如果这样做，MFC 会引发异常。 要确定 tabledef 对象是否表示附加的表，请创建[CDaoTableDef](../../mfc/reference/cdaotabledef-class.md)对象并调用其[GetConnect](../../mfc/reference/cdaotabledef-class.md#getconnect)成员函数。

如果要在`dbSeeChanges`编辑或删除同一记录时捕获其他用户或其他程序在计算机上所做的更改，请使用该标志。 例如，如果两个用户开始编辑同一记录，则调用`Update`成员函数的第一个用户将成功。 当`Update`第二个用户调用时，将`CDaoException`引发 。 同样，如果第二个用户尝试调用`Delete`以删除记录，并且第一个用户已更改该记录，则会发生`CDaoException`。

通常，如果用户在更新时收到`CDaoException`此内容，则代码应刷新字段的内容并检索新修改的值。 如果在删除过程中出现异常，则代码可能会向用户显示新的记录数据，并显示指示数据最近已更改的消息。 此时，您的代码可以请求确认用户仍希望删除记录。

> [!TIP]
> 当应用程序通过从 ODBC 数据源`dbForwardOnly`打开的记录集进行单次传递时，使用仅转发滚动选项 （ ） 来提高性能。

有关相关信息，请参阅 DAO 帮助中的主题"打开记录集方法"。

## <a name="cdaorecordsetrequery"></a><a name="requery"></a>CDao 记录集：：重新查询

调用此成员函数以重建（刷新）记录集。

```
virtual void Requery();
```

### <a name="remarks"></a>备注

如果返回任何记录，则第一条记录将成为当前记录。

为了使记录集反映您或其他用户对数据源进行的添加和删除，必须通过调用`Requery`来重新生成记录集。 如果记录集是动态集，它会自动反映您或其他用户对其现有记录（但不是添加）进行的更新。 如果记录集是快照，则必须调用`Requery`以反映其他用户的编辑以及添加和删除。

对于动态集或快照，`Requery`请随时调用要使用参数值重建记录集。 在调用`Requery`[之前设置新的](#m_strfilter)筛选器或排序，m_strFilter和[m_strSort。](#m_strsort) 通过在调用`Requery`之前将新值分配给参数数据成员来设置新参数。

如果重建记录集的尝试失败，记录集将关闭。 在调用`Requery`之前，可以通过调用[CanRestart](#canrestart)成员函数来确定是否可以重新查询记录集。 `CanRestart`不能保证会`Requery`成功。

> [!CAUTION]
> 仅在`Requery`您致电 后才能`Open`致电。

> [!NOTE]
> 调用[重新查询](#requery)会更改 DAO 书签。

如果调用`Requery``CanRestart`返回 0，则不能调用动态集类型或快照类型记录集，也不能在表类型记录集中使用它。

如果两`IsBOF`者`IsEOF`都和调用`Requery`后返回非零，则查询未返回任何记录，并且记录集将不包含任何数据。

有关相关信息，请参阅 DAO 帮助中的"重新查询方法"主题。

## <a name="cdaorecordsetseek"></a><a name="seek"></a>CDao 记录集：：查找

调用此成员函数以查找索引表类型记录集对象中的记录，该对象满足当前索引的指定条件，并使该记录成为当前记录。

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

### <a name="parameters"></a>参数

*lpsz比较*<br/>
以下字符串表达式之一\<："<"、"\""""\"""""">"或">"。

*pKey1*<br/>
指向[COleVariant 的](../../mfc/reference/colevariant-class.md)指针，其值对应于索引中的第一个字段。 必需。

*pKey2*<br/>
指向`COleVariant`其值对应于索引中的第二个字段（如果有）的指针。 默认值为 NULL。

*pKey3*<br/>
指向`COleVariant`其值对应于索引中的第三个字段（如果有）的指针。 默认值为 NULL。

*pKeyarray*<br/>
指向变体数组的指针。 数组大小对应于索引中的字段数。

*n键*<br/>
与数组大小对应的整数，即索引中的字段数。

> [!NOTE]
> 请勿在键中指定通配符。 通配符将导致`Seek`返回没有匹配的记录。

### <a name="return-value"></a>返回值

如果找到匹配的记录，则非零，否则为 0。

### <a name="remarks"></a>备注

使用 第`Seek`二个（数组）版本来处理四个或更多字段的索引。

`Seek`支持在表类型的记录集上搜索高性能索引。 在调用`SetCurrentIndex``Seek`之前，必须通过调用 来设置当前索引。 如果索引标识非唯一键字段或字段，`Seek`则查找满足条件的第一个记录。 如果不设置索引，将引发异常。

请注意，如果不创建 UNICODE 记录集，则必须显式声明`COleVariant`对象为 ANSI。 这可以通过使用[COleVariant：COlevariant（lpszSrc，](../../mfc/reference/colevariant-class.md#colevariant)**(** *lpszSrc* **,** *vtSrc）***)** 形式的构造函数与*vtSrc*设置为`VT_BSTRT`（ANSI） 或使用`COleVariant`函数[SetString](../../mfc/reference/colevariant-class.md#setstring) *（lpszSrc，* **,** *vtSrc）***)** 与*vtSrc*设置为`VT_BSTRT`。**(**

调用 时`Seek`，传递一个或多个键值和比较运算符\<（"<"、"\""""""""""">"或">"）。 `Seek`搜索指定的键字段，并找到满足*lpsz比较*和*pKey1*指定的条件的第一个记录。 找到后，`Seek`返回非零，并使该记录成为当前记录。 如果`Seek`找不到匹配项，`Seek`则返回零，并且当前记录未定义。 直接使用 DAO 时，必须显式检查 NoMatch 属性。

如果`lpszComparison`为"*"、">"或">"，则`Seek`从索引的开头开始。 如果*lpsz比较*是"<"或"<+"，`Seek`则从索引的末尾开始，然后向后搜索，除非末尾有重复的索引条目。 在这种情况下，`Seek`从索引末尾的重复索引条目之间的任意条目开始。

使用`Seek`时不必有当前记录。

要查找满足特定条件的动态集类型或快照类型记录集中的记录，请使用 Find 操作。 要包括所有记录，而不仅仅是满足特定条件的记录，请使用 Move 操作从记录移动到记录。

不能调用`Seek`任何类型的附加表，因为附加的表必须作为动态集类型或快照类型记录集打开。 但是，如果您调用`CDaoDatabase::Open`直接打开可安装的 ISAM 数据库，则可以调用`Seek`该数据库中的表，尽管性能可能很慢。

有关相关信息，请参阅 DAO 帮助中的主题"查找方法"。

## <a name="cdaorecordsetsetabsoluteposition"></a><a name="setabsoluteposition"></a>CDao 记录集：：设置绝对位置

设置记录集对象当前记录的相对记录编号。

```
void SetAbsolutePosition(long lPosition);
```

### <a name="parameters"></a>参数

*l定位*<br/>
对应于记录集中当前记录的盘位位置。

### <a name="remarks"></a>备注

通过`SetAbsolutePosition`调用，您可以根据当前记录指针在动态集类型或快照类型记录集中的位级位置定位到特定记录。 您还可以通过调用[Get 绝对位置](#getabsoluteposition)来确定当前记录编号。

> [!NOTE]
> 此成员函数仅适用于动态集类型和快照类型记录集。

基础 DAO 对象的绝对位置属性值是零基的;设置为 0 是指记录集中的第一个记录。 设置大于填充记录数的值会导致 MFC 引发异常。 您可以通过调用`GetRecordCount`成员函数来确定记录集中填充的记录数。

如果删除当前记录，则不定义绝对位置属性值，如果引用，MFC 将引发异常。 新记录将添加到序列的末尾。

> [!NOTE]
> 此属性不用作代理记录编号。 书签仍然是保留和返回到给定位置的推荐方式，是跨支持书签的所有类型的记录集对象定位当前记录的唯一方法。 特别是，当删除给定记录之前的记录时，给定记录的位置会发生变化。 如果再次重新创建记录集，也不能保证给定记录集具有相同的绝对位置，因为除非使用**ORDERBY**子句使用 SQL 语句创建记录集中的单个记录的顺序不保证。

有关相关信息，请参阅 DAO 帮助中的"绝对位置属性"主题。

## <a name="cdaorecordsetsetbookmark"></a><a name="setbookmark"></a>CDao 记录集：：设置书签

调用此成员函数将记录集放置在包含指定书签的记录上。

```
void SetBookmark(COleVariant varBookmark);
```

### <a name="parameters"></a>参数

*瓦尔布克马克*<br/>
包含特定记录的书签值的[COleVariant](../../mfc/reference/colevariant-class.md)对象。

### <a name="remarks"></a>备注

创建或打开记录集对象时，其每个记录都已具有唯一的书签。 可以通过调用`GetBookmark`该值并将值保存到`COleVariant`对象来检索当前记录的书签。 稍后，可以使用保存的书签值调用`SetBookmark`该记录。

> [!NOTE]
> 调用[重新查询](#requery)会更改 DAO 书签。

请注意，如果不创建 UNICODE 记录集，`COleVariant`则必须显式声明该对象为 ANSI。 这可以通过使用[COleVariant：COlevariant（lpszSrc，](../../mfc/reference/colevariant-class.md#colevariant)**(** *lpszSrc* **,** *vtSrc）***)** 形式的构造函数与*vtSrc*设置为`VT_BSTRT`（ANSI） 或使用`COleVariant`函数[SetString](../../mfc/reference/colevariant-class.md#setstring) *（lpszSrc，* **,** *vtSrc）***)** 与*vtSrc*设置为`VT_BSTRT`。**(**

有关相关信息，请参阅 DAO 帮助中的"书签属性"和"可书签属性"主题。

## <a name="cdaorecordsetsetcachesize"></a><a name="setcachesize"></a>CDao 记录集：：设置缓存大小

调用此成员函数以设置要缓存的记录数。

```
void SetCacheSize(long lSize);
```

### <a name="parameters"></a>参数

*lSize*<br/>
指定记录数。 典型值为 100。 设置为 0 将关闭缓存。 设置必须介于 5 和 1200 条记录之间。 缓存可能使用大量内存。

### <a name="remarks"></a>备注

缓存是本地内存中的一个空间，用于保存最近从服务器检索的数据，如果应用程序运行时将再次请求数据。 数据缓存提高了应用程序通过动态集类型记录集对象从远程服务器检索数据的性能。 请求数据时，Microsoft Jet 数据库引擎首先检查缓存中请求的数据，而不是从服务器检索数据，这需要更多的时间。 不来自 ODBC 数据源的数据不会保存在缓存中。

任何 ODBC 数据源（如附加的表）都可以具有本地缓存。 要创建缓存，请从远程数据源打开记录集对象，调用`SetCacheSize`和`SetCacheStart`成员函数，然后调用`FillCache`成员函数或使用 Move 操作之一单步执行记录。 成员函数的`SetCacheSize` *lSize*参数可以基于应用程序一次可以使用的记录数。 例如，如果使用记录集作为要显示在屏幕上的数据的来源，则可以将`SetCacheSize`*lSize*参数传递为 20，以一次显示 20 条记录。

有关相关信息，请参阅 DAO 帮助中的主题"缓存大小、缓存启动属性"。

## <a name="cdaorecordsetsetcachestart"></a><a name="setcachestart"></a>CDao 记录集：：设置缓存开始

调用此成员函数以指定要缓存的记录集中第一个记录的书签。

```
void SetCacheStart(COleVariant varBookmark);
```

### <a name="parameters"></a>参数

*瓦尔布克马克*<br/>
指定要缓存的记录集中第一个记录的书签的[COleVariant。](../../mfc/reference/colevariant-class.md)

### <a name="remarks"></a>备注

您可以使用`SetCacheStart`成员函数的*varBookmark*参数的任何记录的书签值。 使用当前记录创建要启动缓存的记录，使用[SetBookmark](#setbookmark)为该记录建立书签，并将书签值作为成员函数的`SetCacheStart`参数传递。

Microsoft Jet 数据库引擎从缓存请求缓存范围内的记录，并且请求服务器在缓存范围之外的记录。

从缓存中检索的记录不会反映其他用户同时对源数据所做的更改。

要强制更新所有缓存的数据，请传递`SetCacheSize`*lSize*参数为 0，使用最初请求`SetCacheSize`的缓存大小再次调用，然后调用`FillCache`成员函数。

请注意，如果不创建 UNICODE 记录集，`COleVariant`则必须显式声明该对象为 ANSI。 这可以通过使用[COleVariant：COlevariant（lpszSrc，](../../mfc/reference/colevariant-class.md#colevariant)**(** *lpszSrc* **,** *vtSrc）***)** 形式的构造函数与*vtSrc*设置为`VT_BSTRT`（ANSI） 或使用`COleVariant`函数[SetString](../../mfc/reference/colevariant-class.md#setstring) *（lpszSrc，* **,** *vtSrc）***)** 与*vtSrc*设置为`VT_BSTRT`。**(**

有关相关信息，请参阅 DAO 帮助中的主题"缓存大小、缓存启动属性"。

## <a name="cdaorecordsetsetcurrentindex"></a><a name="setcurrentindex"></a>CDao 记录集：：设置当前索引

调用此成员函数以在表类型记录集上设置索引。

```
void SetCurrentIndex(LPCTSTR lpszIndex);
```

### <a name="parameters"></a>参数

*lpszIndex*<br/>
包含要设置的索引名称的指针。

### <a name="remarks"></a>备注

基表中的记录不会按任何特定顺序存储。 设置索引会更改从数据库返回的记录的顺序，但不会影响记录的存储顺序。 必须已定义指定的索引。 如果尝试使用不存在的索引对象，或者在调用[Seek](#seek)时未设置索引，则 MFC 将引发异常。

您可以通过调用[CDaoTableDef：：createIndex](../../mfc/reference/cdaotabledef-class.md#createindex)并将新索引追加到基础表def的索引集合，通过调用[CDaoTableDef：：：append，](../../mfc/reference/cdaotabledef-class.md#append)然后重新打开记录集，为表创建新索引。

从表类型记录集返回的记录只能由为基础表def定义的索引排序。 要按其他排序对记录进行排序，可以使用存储在[CDaoRecordset：：m_strSort](#m_strsort)中的 SQL **ORDERBY**子句打开动态集类型或快照类型记录集。

有关相关信息，请参阅 DAO 帮助中的主题"索引对象"和定义"当前索引"。

## <a name="cdaorecordsetsetfielddirty"></a><a name="setfielddirty"></a>CDao 记录集：：设置字段脏

调用此成员函数将记录集的字段数据成员标记为已更改或未更改。

```
void SetFieldDirty(
    void* pv,
    BOOL bDirty = TRUE);
```

### <a name="parameters"></a>参数

*光伏*<br/>
在记录集或 NULL 中包含字段数据成员的地址。 如果为 NULL，则记录集中的所有字段数据成员将被标记。 （C++ NULL 与数据库术语中的 Null 不同，这意味着"没有值"。

*bDirty*<br/>
如果字段数据成员被标记为"脏"（已更改），则为 TRUE。 否则，如果字段数据成员被标记为"干净"（未更改），则 FALSE。

### <a name="remarks"></a>备注

将字段标记为未更改可确保不更新该字段。

框架标记已更改的字段数据成员，以确保 DAO 记录字段交换 （DFX） 机制将它们写入数据源上的记录。 更改字段的值通常会自动将字段设置脏，因此您很少需要调用`SetFieldDirty`自己，但有时您可能希望确保无论字段数据成员中的哪个值如何，都会显式更新或插入列。 DFX 机制还使用 PSEUDONULL。 有关详细信息，请参阅[CDaoFieldExchange：：m_nOperation](../../mfc/reference/cdaofieldexchange-class.md#m_noperation)。

如果未使用双缓冲机制，则更改字段的值不会自动将字段设置为脏。 在这种情况下，必须显式将字段设置为脏。 [m_bCheckCacheForDirtyFields](#m_bcheckcachefordirtyfields)中包含的标志控制此自动字段检查。

> [!NOTE]
> 仅在调用["编辑"](#edit)或["添加 New"](#addnew)后才能调用此成员函数。

将 NULL 用于函数的第一个参数将函数应用于所有`outputColumn`字段，而不是 将**中的**`CDaoFieldExchange`参数字段应用于 。 例如，呼叫

[!code-cpp[NVC_MFCDatabase#6](../../mfc/codesnippet/cpp/cdaorecordset-class_6.cpp)]

将仅`outputColumn`将字段设置为 NULL;**参数**字段将不受影响。

要处理**参数**，您必须提供要处理的单个**参数**的实际地址，例如：

[!code-cpp[NVC_MFCDatabase#7](../../mfc/codesnippet/cpp/cdaorecordset-class_7.cpp)]

这意味着您不能将所有**参数**字段设置为 NULL，就像对字段一样`outputColumn`。

`SetFieldDirty`通过`DoFieldExchange`实现 。

## <a name="cdaorecordsetsetfieldnull"></a><a name="setfieldnull"></a>CDao 记录集：：SetFieldNull

调用此成员函数将记录集的字段数据成员标记为 Null（具体没有值）或非 Null。

```
void SetFieldNull(
    void* pv,
    BOOL bNull = TRUE);
```

### <a name="parameters"></a>参数

*光伏*<br/>
在记录集或 NULL 中包含字段数据成员的地址。 如果为 NULL，则记录集中的所有字段数据成员将被标记。 （C++ NULL 与数据库术语中的 Null 不同，这意味着"没有值"。

*bNull*<br/>
如果要将字段数据成员标记为无值（空），则非零。 否则 0 如果字段数据成员被标记为非 Null。

### <a name="remarks"></a>备注

`SetFieldNull`用于在机制中绑定的`DoFieldExchange`字段。

将新记录添加到记录集时，所有字段数据成员最初都设置为 Null 值，并标记为"脏"（已更改）。 从数据源检索记录时，其列要么已有值，要么为 Null。 如果不适合使字段为 Null，则引发["CDaoException"。](../../mfc/reference/cdaoexception-class.md)

例如，如果您正在使用双缓冲机制，如果您特别希望将当前记录的字段指定为没有值，则使用*bNull*设置为 TRUE 的调用`SetFieldNull`将其标记为 Null。 如果字段以前标记为 Null，现在您希望为其提供值，只需设置其新值即可。 不必删除带有`SetFieldNull`的 Null 标志。 要确定该字段是否允许为空，请调用[IsFieldable 。](#isfieldnullable)

如果不使用双缓冲机制，则更改字段的值不会自动将字段设置为脏和非 Null。 您必须专门设置字段脏和非 Null。 [m_bCheckCacheForDirtyFields](#m_bcheckcachefordirtyfields)中包含的标志控制此自动字段检查。

DFX 机制使用 PSEUDONULL。 有关详细信息，请参阅[CDaoFieldExchange：：m_nOperation](../../mfc/reference/cdaofieldexchange-class.md#m_noperation)。

> [!NOTE]
> 仅在调用["编辑"](#edit)或["添加 New"](#addnew)后才能调用此成员函数。

将 NULL 用于函数的第一个参数将仅将函数应用于`outputColumn`字段，而不是将**参数**字段`CDaoFieldExchange`应用于 。 例如，呼叫

[!code-cpp[NVC_MFCDatabase#8](../../mfc/codesnippet/cpp/cdaorecordset-class_8.cpp)]

将仅`outputColumn`将字段设置为 NULL;**参数**字段将不受影响。

## <a name="cdaorecordsetsetfieldvalue"></a><a name="setfieldvalue"></a>CDao 记录集：：设置场值

调用此成员函数以按任位或更改字符串的值设置字段的值。

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

### <a name="parameters"></a>参数

*lpsz名称*<br/>
指向包含字段名称的字符串的指针。

*varValue*<br/>
对包含字段内容值的[COleVariant](../../mfc/reference/colevariant-class.md)对象的引用。

*nIndex*<br/>
表示记录集"字段"集合中字段的整数（从零开始）。

*lpszValue*<br/>
指向包含字段内容值的字符串的指针。

### <a name="remarks"></a>备注

使用`SetFieldValue`和[GetFieldValue](#getfieldvalue)在运行时动态绑定字段，而不是使用[DoFieldExchange](#dofieldexchange)机制对列进行静态绑定。

请注意，如果不创建 UNICODE 记录集，则必须使用不包含`SetFieldValue``COleVariant`参数的 窗体，或者必须显式声明`COleVariant`该对象 ANSI。 这可以通过使用[COleVariant：COlevariant（lpszSrc，](../../mfc/reference/colevariant-class.md#colevariant)**(** *lpszSrc* **,** *vtSrc）***)** 形式的构造函数与*vtSrc*设置为`VT_BSTRT`（ANSI） 或使用`COleVariant`函数[SetString](../../mfc/reference/colevariant-class.md#setstring) *（lpszSrc，* **,** *vtSrc）***)** 与*vtSrc*设置为`VT_BSTRT`。**(**

有关相关信息，请参阅 DAO 帮助中的"字段对象"和"值属性"主题。

## <a name="cdaorecordsetsetfieldvaluenull"></a><a name="setfieldvaluenull"></a>CDao 记录集：：设置场值 Null

调用此成员函数将字段设置为 Null 值。

```
void SetFieldValueNull(int nIndex);
void SetFieldValueNull(LPCTSTR lpszName);
```

### <a name="parameters"></a>参数

*nIndex*<br/>
记录集中的字段的索引，用于按零基索引查找。

*lpsz名称*<br/>
记录集中的字段的名称，用于按名称查找。

### <a name="remarks"></a>备注

C++ NULL 与 Null 不同，在数据库术语中，Null 表示"没有值"。

有关相关信息，请参阅 DAO 帮助中的"字段对象"和"值属性"主题。

## <a name="cdaorecordsetsetlockingmode"></a><a name="setlockingmode"></a>CDao 记录集：：设置锁定模式

调用此成员函数以设置记录集的锁定类型。

```
void SetLockingMode(BOOL bPessimistic);
```

### <a name="parameters"></a>参数

*b：00*<br/>
指示锁定类型的标志。

### <a name="remarks"></a>备注

当悲观锁定生效时，包含您编辑的记录的 2K 页面在调用`Edit`成员函数后立即锁定。 当您调用 或`Update``Close`成员函数或任何"移动"或"查找"操作时，页面将解锁。

当乐观锁定生效时，包含记录的 2K 页面仅在使用`Update`成员函数更新记录时锁定。

如果页面被锁定，则其他用户无法编辑同一页上的记录。 如果调用`SetLockingMode`并传递非零值，而另一个用户已锁定页面，则调用`Edit`时将引发异常。 其他用户可以从锁定的页面读取数据。

如果使用零`SetLockingMode`值进行调用，并在页面被`Update`其他用户锁定时稍后调用，则会发生异常。 要查看其他用户对记录所做的更改（并丢失更改），请使用当前记录的书签值调用`SetBookmark`成员函数。

使用 ODBC 数据源时，锁定模式始终乐观。

## <a name="cdaorecordsetsetparamvalue"></a><a name="setparamvalue"></a>CDao 记录集：：SetParamValue

调用此成员函数以在运行时在记录集中设置参数的值。

```
virtual void SetParamValue(
    int nIndex,
    const COleVariant& varValue);

virtual void SetParamValue(
    LPCTSTR lpszName,
    const COleVariant& varValue);
```

### <a name="parameters"></a>参数

*nIndex*<br/>
参数在查询def的参数集合中的数值位置。

*var*<br/>
要设置的值;请参阅备注。

*lpsz名称*<br/>
要设置其值的参数的名称。

### <a name="remarks"></a>备注

参数必须已作为记录集的 SQL 字符串的一部分建立。 您可以按名称或其集合中的索引位置访问参数。

指定要设置为`COleVariant`对象的值。 有关在`COleVariant`对象中设置所需值和类型的信息，请参阅类[COleVariant](../../mfc/reference/colevariant-class.md)。 请注意，如果不创建 UNICODE 记录集，`COleVariant`则必须显式声明该对象为 ANSI。 这可以通过使用[COleVariant：COlevariant（lpszSrc，](../../mfc/reference/colevariant-class.md#colevariant)**(** *lpszSrc* **,** *vtSrc）***)** 形式的构造函数与*vtSrc*设置为`VT_BSTRT`（ANSI） 或使用`COleVariant`函数[SetString](../../mfc/reference/colevariant-class.md#setstring) *（lpszSrc，* **,** *vtSrc）***)** 与*vtSrc*设置为`VT_BSTRT`。**(**

## <a name="cdaorecordsetsetparamvaluenull"></a><a name="setparamvaluenull"></a>CDao 记录集：：SetParamValueNull

调用此成员函数将参数设置为 Null 值。

```
void SetParamValueNull(int nIndex);
void SetParamValueNull(LPCTSTR lpszName);
```

### <a name="parameters"></a>参数

*nIndex*<br/>
记录集中的字段的索引，用于按零基索引查找。

*lpsz名称*<br/>
记录集中的字段的名称，用于按名称查找。

### <a name="remarks"></a>备注

C++ NULL 与 Null 不同，在数据库术语中，Null 表示"没有值"。

## <a name="cdaorecordsetsetpercentposition"></a><a name="setpercentposition"></a>CDao 记录集：：设置百分比位置

调用此成员函数可设置一个值，该值根据记录集中记录中的记录的百分比更改记录集对象中当前记录的大致位置。

```
void SetPercentPosition(float fPosition);
```

### <a name="parameters"></a>参数

*f定位*<br/>
一个介于 0 和 100 之间的数字。

### <a name="remarks"></a>备注

使用动态集类型或快照类型记录集时，首先通过在调用`SetPercentPosition`之前移动到最后一个记录来填充记录集。 如果在完全填充`SetPercentPosition`记录集之前调用，则移动量与[GetRecordCount](#getrecordcount)的值指示的访问记录数相关。 您可以通过调用`MoveLast`移动到最后一个记录。

调用`SetPercentPosition`后，与该值对应的近似位置的记录将成为当前记录。

> [!NOTE]
> 不`SetPercentPosition`建议调用将当前记录移动到记录集中的特定记录。 请改为调用[SetBookmark](#setbookmark)成员函数。

有关相关信息，请参阅 DAO 帮助中的主题"百分比位置属性"。

## <a name="cdaorecordsetupdate"></a><a name="update"></a>CDao 记录集：：更新

调用`AddNew`或`Edit`成员函数后调用此成员函数。

```
virtual void Update();
```

### <a name="remarks"></a>备注

完成`AddNew`或`Edit`操作需要此调用。

`AddNew`并`Edit`准备一个编辑缓冲区，其中添加或编辑的数据被放置到数据源中。 `Update`保存数据。 只会更新标记为或检测到已更改的字段。

如果数据源支持事务，则可以将`Update`调用（及其相应的`AddNew`或`Edit`调用）作为事务的一部分。

> [!CAUTION]
> 如果在未首先`Update`调用 或`AddNew``Edit`的情况下调用`Update`，`CDaoException`则引发 。 如果调用`AddNew`或`Edit`，则必须在`Update`调用[MoveNext](#movenext)之前调用或关闭记录集或数据源连接。 否则，您的更改将丢失，恕不另行通知。

当记录集对象在多用户环境中被悲观锁定时，记录从使用到`Edit`更新完成时一直锁定。 如果记录集被乐观地锁定，则记录将锁定，并在数据库中更新之前与预编辑的记录进行比较。 如果记录自调用`Edit`后已更改，则`Update`操作将失败，并且 MFC 会引发异常。 您可以使用 更改锁定模式`SetLockingMode`。

> [!NOTE]
> 乐观锁定始终用于外部数据库格式，如 ODBC 和可安装 ISAM。

有关相关信息，请参阅 DAO 帮助中的"添加新方法"、"取消更新方法"、"删除方法"、"上次修改属性"、"更新方法"和"编辑模式属性"的主题。

## <a name="see-also"></a>另请参阅

[CObject 类](../../mfc/reference/cobject-class.md)<br/>
[层次结构图表](../../mfc/hierarchy-chart.md)<br/>
[CDaoTableDef 类](../../mfc/reference/cdaotabledef-class.md)<br/>
[CDaoWorkspace 类](../../mfc/reference/cdaoworkspace-class.md)<br/>
[CDaoDatabase 类](../../mfc/reference/cdaodatabase-class.md)<br/>
[CDaoQueryDef 类](../../mfc/reference/cdaoquerydef-class.md)<br/>
