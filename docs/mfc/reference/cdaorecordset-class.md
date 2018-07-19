---
title: CDaoRecordset 类 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a7ac9328a6f0f63d3f5d9ee622dabad9f171650c
ms.sourcegitcommit: 6408139d5f5ff8928f056bde93d20eecb3520361
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2018
ms.locfileid: "37339652"
---
# <a name="cdaorecordset-class"></a>CDaoRecordset 类
表示从数据源选择的一组记录。  
  
## <a name="syntax"></a>语法  
  
```  
class CDaoRecordset : public CObject  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[CDaoRecordset::CDaoRecordset](#cdaorecordset)|构造 `CDaoRecordset` 对象。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CDaoRecordset::AddNew](#addnew)|准备用于添加新记录。 调用[更新](#update)完成添加。|  
|[CDaoRecordset::CanAppend](#canappend)|返回非零，如果可以将新记录添加到通过记录集[AddNew](#addnew)成员函数。|  
|[CDaoRecordset::CanBookmark](#canbookmark)|返回非零，如果记录集支持书签。|  
|[CDaoRecordset::CancelUpdate](#cancelupdate)|取消所有挂起的更新，由于[编辑](#edit)或[AddNew](#addnew)操作。|  
|[CDaoRecordset::CanRestart](#canrestart)|返回非零 if[再次查询](#requery)可以调用以再次运行记录集的查询。|  
|[CDaoRecordset::CanScroll](#canscroll)|返回非零，如果可以滚动浏览记录。|  
|[CDaoRecordset::CanTransact](#cantransact)|返回非零，如果数据源支持事务。|  
|[CDaoRecordset::CanUpdate](#canupdate)|返回非零，如果可以更新该记录集 （你可以添加、 更新或删除记录）。|  
|[CDaoRecordset::Close](#close)|关闭记录集。|  
|[CDaoRecordset::Delete](#delete)|从记录集中删除当前记录。 您必须显式滚动到另一条记录后删除。|  
|[CDaoRecordset::DoFieldExchange](#dofieldexchange)|调用以交换 （在这两个方向上） 之间的记录集的字段数据成员和数据源上的相应记录的数据。 实现 DAO 记录字段交换 (DFX)。|  
|[CDaoRecordset::Edit](#edit)|准备对当前记录的更改。 调用`Update`以完成编辑。|  
|[CDaoRecordset::FillCache](#fillcache)|填充所有或一部分记录集对象，其中包含来自 ODBC 数据源的数据的本地缓存。|  
|[CDaoRecordset::Find](#find)|查找第一个下, 一步，在满足指定的条件并将该记录的当前记录的动态集类型记录集的特定字符串的上一个，或最后一个位置。|  
|[CDaoRecordset::FindFirst](#findfirst)|动态集类型或满足指定的条件并将该记录的当前记录的快照类型记录集中定位第一条记录。|  
|[CDaoRecordset::FindLast](#findlast)|动态集类型或满足指定的条件并将该记录的当前记录的快照类型记录集中查找最后一条记录。|  
|[CDaoRecordset::FindNext](#findnext)|动态集类型或满足指定的条件并将该记录的当前记录的快照类型记录集中查找下一条记录。|  
|[CDaoRecordset::FindPrev](#findprev)|动态集类型或满足指定的条件并将该记录的当前记录的快照类型记录集中定位前一条记录。|  
|[CDaoRecordset::GetAbsolutePosition](#getabsoluteposition)|返回记录集对象的当前记录的记录数。|  
|[CDaoRecordset::GetBookmark](#getbookmark)|返回一个值，表示一条记录上的书签。|  
|[CDaoRecordset::GetCacheSize](#getcachesize)|返回一个值，指定动态集类型的记录集包含本地缓存从 ODBC 数据源数据中的记录数。|  
|[CDaoRecordset::GetCacheStart](#getcachestart)|返回一个值，指定在记录集缓存中的第一条记录的书签。|  
|[CDaoRecordset::GetCurrentIndex](#getcurrentindex)|返回`CString`最近包含索引的名称索引的表类型上使用`CDaoRecordset`。|  
|[CDaoRecordset::GetDateCreated](#getdatecreated)|返回的日期和时间基表基础`CDaoRecordset`创建对象|  
|[CDaoRecordset::GetDateLastUpdated](#getdatelastupdated)|返回的日期和时间的基表基础设计所做的最新更改`CDaoRecordset`对象。|  
|[CDaoRecordset::GetDefaultDBName](#getdefaultdbname)|返回默认数据源的名称。|  
|[CDaoRecordset::GetDefaultSQL](#getdefaultsql)|调用以获取要执行的默认 SQL 字符串。|  
|[CDaoRecordset::GetEditMode](#geteditmode)|返回一个值，该值指示当前记录的编辑状态。|  
|[CDaoRecordset::GetFieldCount](#getfieldcount)|返回一个值，表示在记录集中的字段数。|  
|[CDaoRecordset::GetFieldInfo](#getfieldinfo)|在记录集中返回特定类型的字段的信息。|  
|[CDaoRecordset::GetFieldValue](#getfieldvalue)|在记录集中返回的字段值。|  
|[CDaoRecordset::GetIndexCount](#getindexcount)|检索下一个记录集的表中的索引数。|  
|[CDaoRecordset::GetIndexInfo](#getindexinfo)|返回各种类型的有关索引的信息。|  
|[CDaoRecordset::GetLastModifiedBookmark](#getlastmodifiedbookmark)|用于确定最最近添加或更新记录。|  
|[CDaoRecordset::GetLockingMode](#getlockingmode)|返回一个值，指示在编辑过程实际上是锁定的类型。|  
|[CDaoRecordset::GetName](#getname)|返回`CString`包含记录集的名称。|  
|[CDaoRecordset::GetParamValue](#getparamvalue)|检索基础 DAOParameter 对象中存储的指定参数的当前值。|  
|[CDaoRecordset::GetPercentPosition](#getpercentposition)|返回的记录总数的百分比当前记录的位置。|  
|[CDaoRecordset::GetRecordCount](#getrecordcount)|返回记录集对象中访问的记录的数。|  
|[CDaoRecordset::GetSQL](#getsql)|获取用于选择记录集的记录的 SQL 字符串。|  
|[CDaoRecordset::GetType](#gettype)|调用以确定记录集的类型： 表类型、 动态集的类型或快照类型。|  
|[CDaoRecordset::GetValidationRule](#getvalidationrule)|返回`CString`包含用于验证数据，如在字段中输入的值。|  
|[CDaoRecordset::GetValidationText](#getvalidationtext)|检索不满足有效性规则时显示的文本。|  
|[CDaoRecordset::IsBOF](#isbof)|返回非零，如果在第一条记录之前定位完记录集。 没有当前记录。|  
|[CDaoRecordset::IsDeleted](#isdeleted)|返回非零，如果记录集定位在已删除的记录上。|  
|[CDaoRecordset::IsEOF](#iseof)|返回非零，如果在最后一条记录后定位完记录集。 没有当前记录。|  
|[CDaoRecordset::IsFieldDirty](#isfielddirty)|返回非零，如果已更改的当前记录中的指定的字段。|  
|[CDaoRecordset::IsFieldNull](#isfieldnull)|返回非零，如果当前记录中的指定的字段为 Null （具有任何值）。|  
|[CDaoRecordset::IsFieldNullable](#isfieldnullable)|返回非零，如果当前记录中指定的字段可以设置为 Null （具有任何值）。|  
|[CDaoRecordset::IsOpen](#isopen)|返回非零 if[打开](#open)已被调用过。|  
|[CDaoRecordset::Move](#move)|从两个方向中的当前记录到指定数目的记录定位记录集。|  
|[CDaoRecordset::MoveFirst](#movefirst)|定位在记录集中的第一个记录的当前记录。|  
|[CDaoRecordset::MoveLast](#movelast)|定位在记录集中的最后一个记录的当前记录。|  
|[CDaoRecordset::MoveNext](#movenext)|定位在记录集中的下一个记录的当前记录。|  
|[CDaoRecordset::MovePrev](#moveprev)|定位记录集的上一个记录的当前记录。|  
|[Cdaorecordset:: Open](#open)|从表、 动态集或快照创建新的记录集。|  
|[CDaoRecordset::Requery](#requery)|运行以刷新所选的记录的记录集的查询。|  
|[CDaoRecordset::Seek](#seek)|查找满足指定的条件的当前索引并将该记录的当前记录的索引的表类型记录集对象中的记录。|  
|[CDaoRecordset::SetAbsolutePosition](#setabsoluteposition)|设置记录集对象的当前记录的记录数。|  
|[CDaoRecordset::SetBookmark](#setbookmark)|定位记录集包含指定的书签的记录。|  
|[CDaoRecordset::SetCacheSize](#setcachesize)|设置一个值，指定动态集类型的记录集包含本地缓存从 ODBC 数据源数据中的记录数。|  
|[CDaoRecordset::SetCacheStart](#setcachestart)|设置一个值，指定在记录集缓存中的第一条记录的书签。|  
|[CDaoRecordset::SetCurrentIndex](#setcurrentindex)|调用以设置索引类型一个表的记录集。|  
|[CDaoRecordset::SetFieldDirty](#setfielddirty)|将当前记录中指定的字段标记为已更改。|  
|[CDaoRecordset::SetFieldNull](#setfieldnull)|为 Null （具有任何值） 的当前记录中设置指定字段的值。|  
|[CDaoRecordset::SetFieldValue](#setfieldvalue)|在记录集中设置字段的值。|  
|[CDaoRecordset::SetFieldValueNull](#setfieldvaluenull)|设置字段的值中的记录集为 Null。 （具有任何值）。|  
|[CDaoRecordset::SetLockingMode](#setlockingmode)|设置一个值，指示锁定使编辑期间生效的类型。|  
|[CDaoRecordset::SetParamValue](#setparamvalue)|设置基础 DAOParameter 对象中存储的指定参数的当前值|  
|[CDaoRecordset::SetParamValueNull](#setparamvaluenull)|将指定的参数的当前值设置为 Null （具有任何值）。|  
|[CDaoRecordset::SetPercentPosition](#setpercentposition)|将当前记录的位置设置为相应的记录集中的记录总数的百分比形式的位置。|  
|[CDaoRecordset::Update](#update)|完成`AddNew`或`Edit`通过将新的或编辑数据保存在数据源上的操作。|  
  
### <a name="public-data-members"></a>公共数据成员  
  
|名称|描述|  
|----------|-----------------|  
|[Cdaorecordset:: M_bcheckcachefordirtyfields](#m_bcheckcachefordirtyfields)|包含一个标志，指示是否字段将自动标记为已更改。|  
|[CDaoRecordset::m_nFields](#m_nfields)|包含记录集类中的字段数据成员的数目和选定数据源的记录集的列数。|  
|[CDaoRecordset::m_nParams](#m_nparams)|包含记录集类中的参数数据成员的数目，使用记录集的查询传递的参数的数目|  
|[CDaoRecordset::m_pDAORecordset](#m_pdaorecordset)|指向基础的记录集对象的 DAO 接口的指针。|  
|[CDaoRecordset::m_pDatabase](#m_pdatabase)|此结果集的源数据库。 包含一个指向[CDaoDatabase](../../mfc/reference/cdaodatabase-class.md)对象。|  
|[CDaoRecordset::m_strFilter](#m_strfilter)|包含一个字符串，用来构造 SQL**其中**语句。|  
|[CDaoRecordset::m_strSort](#m_strsort)|包含一个字符串，用来构造 SQL **ORDER BY**语句。|  
  
## <a name="remarks"></a>备注  
 名为"记录集，"`CDaoRecordset`对象可在以下三个窗体中：  
  
-   表类型的记录集表示可用于检查、 添加、 更改或删除单个数据库表中的记录的基本表。  
  
-   动态集类型的记录集是查询的可以具有可更新的记录的结果。 这些记录集是一组可用于检查、 添加、 更改或删除基础数据库表或表中的记录的记录。 动态集类型的记录集可以包含在数据库中的一个或多个表中的字段。  
  
-   快照类型的记录集是一组可用于查找数据或生成报告的记录的静态副本。 这些记录集可以包含在数据库中的一个或多个表中的字段，但不能更新。  
  
 记录集的每个窗体表示一组固定的打开记录集的记录。 当您滚动到类型一个表的记录集或动态集类型记录集中的记录时，它反映了打开记录集，其他用户或应用程序中的其他记录集后，对记录所做的更改。 （快照类型记录集不能更新。）可以使用`CDaoRecordset`直接或派生应用程序特定的记录集类从`CDaoRecordset`。 然后，可以：  
  
-   滚动浏览记录。  
  
-   设置索引，并使用记录快速查找[Seek](#seek) （仅类型一个表的记录集）。  
  
-   查找基于字符串比较的记录:"<"、"\<="，"="、"> ="，或">"（动态集类型和快照类型的记录集）。  
  
-   更新的记录，并指定 （除快照类型的记录集） 的锁定模式。  
  
-   要将限制从提供的那些数据源选择的记录的记录集的筛选器。  
  
-   对记录集进行排序。  
  
-   参数化记录集进行自定义信息直到运行时才知道其所选内容。  
  
 类`CDaoRecordset`提供类似于类的接口`CRecordset`。 主要区别是该类`CDaoRecordset`访问的数据通过数据访问对象 (DAO) 基于 OLE。 类`CRecordset`该 dbms 通过开放式数据库连接 (ODBC) 和 ODBC 驱动程序访问 DBMS。  
  
> [!NOTE]
>  DAO 数据库类是不同于基于开放式数据库连接 (ODBC) 的 MFC 数据库类。 所有 DAO 数据库类名称都具有"CDao"前缀。 您仍然可以访问 ODBC 数据源对于 DAO 类中;DAO 类通常提供高级功能，因为它们是特定于 Microsoft Jet 数据库引擎。  
  
 您可以使用`CDaoRecordset`直接或从派生类`CDaoRecordset`。 若要使用的记录集类在任一情况下，打开数据库，然后构造一个记录集对象，将构造函数传递一个指向你`CDaoDatabase`对象。 您还可以构造`CDaoRecordset`对象，并允许创建一个临时的 MFC`CDaoDatabase`为您的对象。 然后，调用记录集的[打开](#open)成员函数，该值指示对象是否为类型一个表的记录集、 动态集类型的记录集或快照类型记录集。 调用`Open`从数据库选择数据，然后检索第一条记录。  
  
 使用对象的成员函数和数据成员来滚动浏览记录并进行这些操作。 可使用的操作取决于该对象是类型一个表的记录集、 动态集类型的记录集或快照类型的记录集，以及它是否可更新或只读的这取决于数据库或开放式数据库连接 (ODBC) 的功能数据源。 若要刷新记录可能已更改或添加以来`Open`调用，调用对象的[再次查询](#requery)成员函数。 调用对象的`Close`成员函数，并使用它完成后销毁对象。  
  
 `CDaoRecordset` 使用 DAO 记录字段交换 (DFX) 来支持读取和更新记录的字段类型安全的 c + + 成员通过你`CDaoRecordset`或`CDaoRecordset`-派生的类。 您还可以实现动态绑定列的数据库中而无需使用 DFX 机制使用[GetFieldValue](#getfieldvalue)并[SetFieldValue](#setfieldvalue)。  
  
 有关相关信息，请参阅主题 DAO 帮助中的"记录集对象"。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CDaoRecordset`  
  
## <a name="requirements"></a>要求  
 **标头：** afxdao.h  
  
##  <a name="addnew"></a>  CDaoRecordset::AddNew  
 调用此成员函数以将新记录添加到表类型或动态集类型的记录集。  
  
```  
virtual void AddNew();
```  
  
### <a name="remarks"></a>备注  
 记录的字段是最初为 Null。 （在数据库术语中，Null 意味着"无值"，并且不为 NULL，c + + 中相同。）若要完成该操作，必须调用[更新](#update)成员函数。 `Update` 将所做的更改保存到数据源。  
  
> [!CAUTION]
>  如果编辑记录，然后滚动到另一条记录，而无需调用`Update`，所做的更改都将丢失而不发出警告。  
  
 如果您将添加一条记录到动态集类型的记录集通过调用[AddNew](#addnew)，该记录是记录集内可见并包含在其中它将显示出来到任何新的基础表`CDaoRecordset`对象。  
  
 新记录的位置取决于记录集的类型：  
  
-   动态集类型中不保证在记录集，其中插入新记录。 使用 Microsoft Jet 3.0 出于性能和并发更改此行为。 如果你的目标是使当前记录的新添加的记录，获取最后一个修改后记录的书签并将移动到该书签：  
  
 [!code-cpp[NVC_MFCDatabase#1](../../mfc/codesnippet/cpp/cdaorecordset-class_1.cpp)]  
  
-   在为其指定索引的表类型的记录集中，在它们的排序顺序中的正确位置中返回的记录。 如果已指定没有索引，记录集的末尾返回新的记录。  
  
 使用之前的当前记录`AddNew`保持最新。 如果你想要将当前版本的新记录和记录集支持书签，调用[SetBookmark](#setbookmark)到书签标识的基础的 DAO 记录集对象的上次更改时间属性设置。 执行此操作可用于确定在添加的记录中的计数器 （自动递增） 字段的值。 有关详细信息，请参阅[GetLastModifiedBookmark](#getlastmodifiedbookmark)。  
  
 如果数据库支持事务，可以使您`AddNew`调用事务的一部分。 有关事务的详细信息，请参阅类[CDaoWorkspace](../../mfc/reference/cdaoworkspace-class.md)。 请注意，应调用[CDaoWorkspace::BeginTrans](../../mfc/reference/cdaoworkspace-class.md#begintrans)然后才能调用`AddNew`。  
  
 您不能调用`AddNew`记录集其[打开](#open)尚未调用成员函数。 一个`CDaoException`如果您调用，将引发`AddNew`无法追加的记录集。 您可以确定记录集是否可更新通过调用[CanAppend](#canappend)。  
  
 Framework 标记更改字段数据成员，以确保它们将写入到数据源上的记录的 DAO 记录字段交换 (DFX) 机制。 将更改字段的值通常字段已更新会自动设置，因此很少需要调用[SetFieldDirty](#setfielddirty)自己，但您有时可能想要确保，列将显式更新或插入而不考虑值是字段数据成员中。 DFX 机制还使用了利用**伪 NULL**。 有关详细信息，请参阅[CDaoFieldExchange::m_nOperation](../../mfc/reference/cdaofieldexchange-class.md#m_noperation)。  
  
 如果未使用双缓冲机制，然后更改字段的值不会不会自动将字段设置为脏。 在这种情况下，将需要显式设置该字段已更新。 中包含的标志[m_bCheckCacheForDirtyFields](#m_bcheckcachefordirtyfields)控制此自动字段检查。  
  
> [!NOTE]
>  如果记录都是双缓冲 （即自动字段检查已启用），调用`CancelUpdate`将还原到之前所具有的值的成员变量`AddNew`或`Edit`调用。  
  
 有关相关信息，请参阅"AddNew 方法"、"CancelUpdate 方法"、"上次更改时间属性"和"EditMode 属性"DAO 帮助中的主题。  
  
##  <a name="canappend"></a>  CDaoRecordset::CanAppend  
 调用此成员函数以确定是否以前打开的记录集，可通过调用添加新记录[AddNew](#addnew)成员函数。  
  
```  
BOOL CanAppend() const;  
```  
  
### <a name="return-value"></a>返回值  
 非零，如果记录集允许添加新记录;否则为 0。 `CanAppend` 如果打开记录集持久化为只读的则将返回 0。  
  
### <a name="remarks"></a>备注  
 有关相关信息，请参阅主题 DAO 帮助中的"追加方法"。  
  
##  <a name="canbookmark"></a>  CDaoRecordset::CanBookmark  
 调用此成员函数以确定是否以前打开的记录集，可单独将记录使用书签标记。  
  
```  
BOOL CanBookmark();
```  
  
### <a name="return-value"></a>返回值  
 如果记录集支持的书签，否则为 0，非零值。  
  
### <a name="remarks"></a>备注  
 如果使用的完全基于 Microsoft Jet 数据库引擎表的记录集，书签可以使用除上快照类型记录集标记为只进滚动记录集。 其他数据库产品 （外部 ODBC 数据源） 可能不支持书签。  
  
 有关相关信息，请参阅主题 DAO 帮助中的"可存为书签属性"。  
  
##  <a name="cancelupdate"></a>  CDaoRecordset::CancelUpdate  
 `CancelUpdate`成员函数将取消所有挂起的更新，由于[编辑](#edit)或[AddNew](#addnew)操作。  
  
```  
virtual void CancelUpdate();
```  
  
### <a name="remarks"></a>备注  
 例如，如果应用程序调用`Edit`或`AddNew`成员函数和具有不调用[更新](#update)，`CancelUpdate`取消后所做的任何更改`Edit`或`AddNew`调用。  
  
> [!NOTE]
>  如果记录都是双缓冲 （即自动字段检查已启用），调用`CancelUpdate`将还原到之前所具有的值的成员变量`AddNew`或`Edit`调用。  
  
 如果没有任何`Edit`或`AddNew`操作挂起，`CancelUpdate`导致 MFC 引发异常。 调用[GetEditMode](#geteditmode)成员函数以确定是否可以取消的挂起操作。  
  
 有关相关信息，请参阅主题 DAO 帮助中的"CancelUpdate 方法"。  
  
##  <a name="canrestart"></a>  CDaoRecordset::CanRestart  
 调用此成员函数可确定记录集是否允许通过调用重启 （若要刷新其记录） 其查询`Requery`成员函数。  
  
```  
BOOL CanRestart();
```  
  
### <a name="return-value"></a>返回值  
 如果非零`Requery`可以调用来运行记录集的一次查询，否则为 0。  
  
### <a name="remarks"></a>备注  
 不支持类型一个表的记录集`Requery`。  
  
 如果`Requery`是不受支持，调用[关闭](#close)然后[打开](#open)刷新的数据。 您可以调用`Requery`来更新记录集对象的基本参数查询后已更改的参数值。  
  
 有关相关信息，请参阅主题 DAO 帮助中的"可重新启动属性"。  
  
##  <a name="canscroll"></a>  CDaoRecordset::CanScroll  
 调用此成员函数可确定记录集是否允许滚动。  
  
```  
BOOL CanScroll() const;  
```  
  
### <a name="return-value"></a>返回值  
 如果可以滚动浏览记录，否则为 0，非零值。  
  
### <a name="remarks"></a>备注  
 如果您调用[开放](#open)与`dbForwardOnly`，可以仅向前滚动记录集。  
  
 有关相关信息，请参阅"当前记录指针与 DAO 定位"DAO 帮助中的主题。  
  
##  <a name="cantransact"></a>  CDaoRecordset::CanTransact  
 调用此成员函数可确定记录集是否允许事务。  
  
```  
BOOL CanTransact();
```  
  
### <a name="return-value"></a>返回值  
 如果基础数据源支持事务，否则为 0，非零值。  
  
### <a name="remarks"></a>备注  
 有关相关信息，请参阅主题 DAO 帮助中的"事务属性"。  
  
##  <a name="canupdate"></a>  CDaoRecordset::CanUpdate  
 调用此成员函数以确定是否可以更新该记录集。  
  
```  
BOOL CanUpdate() const;  
```  
  
### <a name="return-value"></a>返回值  
 如果可以更新该记录集，非零值 （添加、 更新和删除记录），否则为 0。  
  
### <a name="remarks"></a>备注  
 记录集可能是只读的如果基础数据源是只读的或者指定`dbReadOnly`有关*nOptions*何时调用[打开](#open)记录集。  
  
 有关相关信息，请参阅主题的"AddNew 方法"、"编辑方法"、"Delete 方法"、"更新方法"和 DAO 帮助中的"可更新属性"。  
  
##  <a name="cdaorecordset"></a>  CDaoRecordset::CDaoRecordset  
 构造 `CDaoRecordset` 对象。  
  
```  
CDaoRecordset(CDaoDatabase* pDatabase = NULL);
```  
  
### <a name="parameters"></a>参数  
 *pDatabase*  
 包含一个指向[CDaoDatabase](../../mfc/reference/cdaodatabase-class.md)对象或值为 NULL。 如果不为 NULL，`CDaoDatabase`对象的`Open`成员函数不调用以将其连接到数据源，该记录集尝试打开为你自己期间[打开](#open)调用。 如果传递 NULL，`CDaoDatabase`对象构造和使用您指定如果派生从记录集类的数据源信息为你连接`CDaoRecordset`。  
  
### <a name="remarks"></a>备注  
 您可以使用`CDaoRecordset`直接或派生特定于应用程序的类从`CDaoRecordset`。 类向导用于派生您的记录集类。  
  
> [!NOTE]
>  如果派生`CDaoRecordset`类，在派生类必须提供自己的构造函数。 在派生类的构造函数中调用构造函数`CDaoRecordset::CDaoRecordset`，将沿适当的参数传递给它。  
  
 将 NULL 传递给您的记录集构造函数具有`CDaoDatabase`对象构造，并自动为您进行连接。 这是有用的快捷方式不需要可构造并连接`CDaoDatabase`之前构造记录集对象。 如果`CDaoDatabase`对象未打开，请[CDaoWorkspace](../../mfc/reference/cdaoworkspace-class.md)还将为你使用默认工作区创建对象。 有关详细信息，请参阅[CDaoDatabase::CDaoDatabase](../../mfc/reference/cdaodatabase-class.md#cdaodatabase)。  
  
##  <a name="close"></a>  CDaoRecordset::Close  
 关闭`CDaoRecordset`对象从打开的记录集相关联的数据库中的集合中移除。  
  
```  
virtual void Close();
```  
  
### <a name="remarks"></a>备注  
 因为`Close`不会销毁`CDaoRecordset`对象，您可以重用该对象通过调用`Open`对同一数据源或不同的数据源。  
  
 所有挂起[AddNew](#addnew)或[编辑](#edit)语句被取消，并且所有挂起的事务将回滚。 如果你想要保留挂起的添加或编辑操作，调用[更新](#update)在调用之前`Close`为每个记录集。  
  
 您可以调用`Open`后调用`Close`。 这样可以重复使用记录集对象。 更好的选择是调用[再次查询](#requery)如有可能。  
  
 有关相关信息，请参阅主题 DAO 帮助中的"关闭方法"。  
  
##  <a name="delete"></a>  CDaoRecordset::Delete  
 调用此成员函数可删除打开的动态集类型或类型一个表的记录集对象中的当前记录。  
  
```  
virtual void Delete();
```  
  
### <a name="remarks"></a>备注  
 成功删除操作之后, 记录集的字段数据成员设置为 Null 值，并且必须显式调用其中一个记录集导航成员函数 ([移动](#move)， [Seek](#seek)， [SetBookmark](#setbookmark)，依次类推) 若要离开已删除的记录。 从记录集删除记录时，必须有当前记录中记录集在调用之前`Delete`; 否则为 MFC 将引发异常。  
  
 `Delete` 删除当前记录并使其不可访问。 尽管您不能编辑或使用已删除的记录，但保持最新。 一旦您移动到另一条记录，但是，您不能已删除的记录当前再次进行。  
  
> [!CAUTION]
>  记录集必须可更新，并且必须有有效记录当前记录集内调用时`Delete`。 例如，如果您删除的记录，但在调用之前不将其滚动到新的记录`Delete`再次`Delete`将引发[CDaoException](../../mfc/reference/cdaoexception-class.md)。  
  
 可以撤消删除一条记录，如果您使用的事务，并且调用[CDaoWorkspace::Rollback](../../mfc/reference/cdaoworkspace-class.md#rollback)成员函数。 如果基础表是主表中的级联删除关系，删除当前记录也可能会删除外部表中的一个或多个记录。 有关详细信息，请参阅 DAO 帮助中的定义"级联删除"。  
  
 与不同`AddNew`并`Edit`，调用`Delete`对的调用后面不接`Update`。  
  
 有关相关信息，请参阅主题的"AddNew 方法"、"编辑方法"、"Delete 方法"、"更新方法"和 DAO 帮助中的"可更新属性"。  
  
##  <a name="dofieldexchange"></a>  CDaoRecordset::DoFieldExchange  
 框架调用此成员函数以自动和之间交换数据的记录集对象的字段数据成员的对应列的数据源上的当前记录。  
  
```  
virtual void DoFieldExchange(CDaoFieldExchange* pFX);
```  
  
### <a name="parameters"></a>参数  
 *pFX*  
 包含一个指向`CDaoFieldExchange`对象。 框架已具有将设置此对象指定为字段 exchange 操作上下文。  
  
### <a name="remarks"></a>备注  
 它还会将绑定参数数据成员，如果有，到记录集的所选内容的 SQL 语句字符串中的参数占位符。 交换字段数据，调用 DAO 记录字段交换 (DFX)，在这两个方向上的工作： 从数据源上的记录的字段的记录集对象的字段数据成员并从上至记录集对象的数据源的记录。 如果要动态绑定列，不需要实现`DoFieldExchange`。  
  
 唯一的操作时通常必须执行实现`DoFieldExchange`派生记录集的类是使用类向导创建类并指定字段数据成员的名称和数据类型。 您还可能会将代码添加到 ClassWizard 写入指定的参数数据成员。 如果所有字段都是要动态绑定，此函数将处于非活动状态，除非您指定的参数数据成员。  
  
 声明类向导在派生的记录集类时，向导会将写入的重写`DoFieldExchange`，类似于下面的示例：  
  
 [!code-cpp[NVC_MFCDatabase#2](../../mfc/codesnippet/cpp/cdaorecordset-class_2.cpp)]  
  
##  <a name="edit"></a>  CDaoRecordset::Edit  
 调用此成员函数以允许对当前记录进行更改。  
  
```  
virtual void Edit();
```  
  
### <a name="remarks"></a>备注  
 一旦调用`Edit`成员函数，对当前记录的字段所做的更改复制到复制缓冲区。 对记录进行所需的更改后，调用`Update`以保存所做的更改。 `Edit` 保存记录集的数据成员的值。 如果您调用`Edit`，进行更改，然后调用`Edit`同样，记录的值会还原到之前第一个`Edit`调用。  
  
> [!CAUTION]
>  如果编辑记录，然后执行任何操作都将移到另一条记录，而无需第一个调用`Update`，所做的更改都将丢失而不发出警告。 此外，如果关闭记录集或对父数据库，你已编辑的记录被丢弃而不发出警告。  
  
 在某些情况下，你可能想要更新的 （不包含任何数据），则为 Null 的列。 若要执行此操作，调用`SetFieldNull`其中参数为 true，则标记字段为 Null; 这也会导致要更新的列。 如果你想要写入的数据源，即使其值已更改，请调用的字段`SetFieldDirty`参数为 TRUE。 这样即使字段具有值为 Null。  
  
 Framework 标记更改字段数据成员，以确保它们将写入到数据源上的记录的 DAO 记录字段交换 (DFX) 机制。 将更改字段的值通常字段已更新会自动设置，因此很少需要调用[SetFieldDirty](#setfielddirty)自己，但您有时可能想要确保，列将显式更新或插入而不考虑值是字段数据成员中。 DFX 机制还使用了利用**伪 NULL**。 有关详细信息，请参阅[CDaoFieldExchange::m_nOperation](../../mfc/reference/cdaofieldexchange-class.md#m_noperation)。  
  
 如果未使用双缓冲机制，然后更改字段的值不会不会自动将字段设置为脏。 在这种情况下，将需要显式设置该字段已更新。 中包含的标志[m_bCheckCacheForDirtyFields](#m_bcheckcachefordirtyfields)控制此自动字段检查。  
  
 记录集对象悲观锁定时在多用户环境中，则记录将保留锁定的时间`Edit`使用，直到更新已完成。 如果乐观地锁定记录集，该记录已被锁定，在数据库中更新之前，将与预编辑记录进行比较。 如果记录已更改，因为你调用`Edit`，则`Update`操作将失败和 MFC 会引发异常。 你可以用在锁定模式下`SetLockingMode`。  
  
> [!NOTE]
>  在外部数据库格式，如 ODBC 和可安装 ISAM 始终使用乐观锁定。  
  
 当前记录保持最新调用后`Edit`。 若要调用`Edit`，必须有当前记录。 如果没有当前记录或记录集不引用打开的表类型或动态集类型记录集对象，则会发生异常。 调用`Edit`导致`CDaoException`在以下情况下引发：  
  
-   没有当前记录。  
  
-   记录集的数据库是只读的。  
  
-   记录中的任何字段不是可更新。  
  
-   记录集的数据库已打开可供独占使用由另一个用户。  
  
-   其他用户锁定了包含您的记录的页。  
  
 如果数据源支持事务，则可以进行`Edit`调用事务的一部分。 请注意，应调用`CDaoWorkspace::BeginTrans`之前调用`Edit`和之后打开记录集。 此外请注意，调用`CDaoWorkspace::CommitTrans`不是调用的替代`Update`若要完成`Edit`操作。 有关事务的详细信息，请参阅类`CDaoWorkspace`。  
  
 有关相关信息，请参阅主题的"AddNew 方法"、"编辑方法"、"Delete 方法"、"更新方法"和 DAO 帮助中的"可更新属性"。  
  
##  <a name="fillcache"></a>  CDaoRecordset::FillCache  
 调用此成员函数以缓存指定的数目的从记录集中的记录。  
  
```  
void FillCache(
    long* pSize = NULL,  
    COleVariant* pBookmark = NULL);
```  
  
### <a name="parameters"></a>参数  
 *pSize*  
 指定要在缓存中填充行的数。 如果省略此参数，值是由基础的 DAO 对象的 CacheSize 属性设置确定。  
  
 *pBookmark*  
 一个[COleVariant](../../mfc/reference/colevariant-class.md)指定书签。 此书签所指定的记录从开始填充缓存。 如果省略此参数，从基础的 DAO 对象的 CacheStart 属性所指定的记录开始填充缓存。  
  
### <a name="remarks"></a>备注  
 缓存可提高性能的应用程序的检索，或提取远程服务器中的数据。 缓存是在本地保存最近从服务器提取的数据将可能再次请求应用程序运行时假定的数据的内存中的空间。 请求数据，Microsoft Jet 数据库引擎的数据会首先检查缓存而不是提取在服务器上，这需要更多的时间。 使用数据缓存在非 ODBC 数据源上没有任何影响，因为数据不保存在缓存中。  
  
 而不是等待它们提取要用记录填充缓存，您可以显式缓存在任何时候调用来填充`FillCache`成员函数。 这是更快地填满缓存，因为`FillCache`提取，而不是一次一个地几条记录。 例如，显示每一满屏记录时，您可以让应用程序调用`FillCache`要提取的下一步满屏记录。  
  
 使用记录集对象访问任何 ODBC 数据库可以具有的本地缓存。 若要创建缓存，请从远程数据源中，打开记录集对象，然后调用`SetCacheSize`和`SetCacheStart`记录集的成员函数。 如果*lSize*并*lBookmark*创建范围，则指定的范围之外的部分或全部`SetCacheSize`和`SetCacheStart`，超出此范围的记录集的部分将被忽略并不是加载到缓存。 如果`FillCache`请求比多个记录将保留在远程数据源、 提取仅剩下的记录，并不会引发异常。  
  
 从缓存中提取的记录不反映对源数据同时进行的其他用户的更改。  
  
 `FillCache` 提取只尚不存在缓存的记录。 若要强制更新所有缓存数据，请调用`SetCacheSize`成员函数*lSize*参数等于 0，调用`SetCacheSize`再次*lSize*参数等于缓存的大小最初请求，，然后调用`FillCache`。  
  
 有关相关信息，请参阅主题 DAO 帮助中的"FillCache 方法"。  
  
##  <a name="find"></a>  CDaoRecordset::Find  
 调用此成员函数来查找特定字符串中使用比较运算符的动态集或快照类型记录集。  
  
```  
virtual BOOL Find(
    long lFindType,  
    LPCTSTR lpszFilter);
```  
  
### <a name="parameters"></a>参数  
 *lFindType*  
 指示查找操作所需的类型的值。 可能的值为：  
  
- AFX_DAO_NEXT 查找匹配的字符串的下一个位置。  
  
- AFX_DAO_PREV 查找匹配的字符串的上一位置。  
  
- AFX_DAO_FIRST 查找匹配的字符串的第一个位置。  
  
- AFX_DAO_LAST 查找匹配的字符串的最后一个位置。  
  
 *lpszFilter*  
 字符串表达式 (如**其中**SQL 语句，而无需单词中的子句**其中**) 用于查找的记录。 例如：  
  
 [!code-cpp[NVC_MFCDatabase#3](../../mfc/codesnippet/cpp/cdaorecordset-class_3.cpp)]  
  
### <a name="return-value"></a>返回值  
 如果找到匹配的记录，否则为 0，非零值。  
  
### <a name="remarks"></a>备注  
 您可以找到第一个下, 一步，该字符串的上一个，或最后一个实例。 `Find` 是虚拟函数，因此可以重写它并添加您自己的实现。 `FindFirst`， `FindLast`， `FindNext`，和`FindPrev`成员函数会调用`Find`成员函数，因此，可以使用`Find`来控制所有查找操作的行为。  
  
 若要找到一条记录中类型一个表的记录集，请调用[Seek](#seek)成员函数。  
  
> [!TIP]
>  较小的组记录，更有效`Find`将为。 在常规和尤其是在使用 ODBC 数据，最好创建一个新查询，以检索所需的记录。  
  
 有关相关信息，请参阅主题"FindFirst，FindLast FindNext，FindPrevious 方法"DAO 帮助中。  
  
##  <a name="findfirst"></a>  CDaoRecordset::FindFirst  
 调用此成员函数以查找与指定的条件匹配的第一个记录。  
  
```  
BOOL FindFirst(LPCTSTR lpszFilter);
```  
  
### <a name="parameters"></a>参数  
 *lpszFilter*  
 字符串表达式 (如**其中**SQL 语句，而无需单词中的子句**其中**) 用于查找的记录。  
  
### <a name="return-value"></a>返回值  
 如果找到匹配的记录，否则为 0，非零值。  
  
### <a name="remarks"></a>备注  
 `FindFirst`成员函数开始记录集开始从其搜索并搜索到记录集的结尾。  
  
 如果你想要包括所有记录 （而不仅仅是满足特定条件的那些） 在搜索中使用的移动操作之一来记录之间移动。 若要找到一条记录中类型一个表的记录集，请调用`Seek`成员函数。  
  
 如果未找到与条件匹配的记录了，是不确定，当前记录指针和`FindFirst`返回零。 如果记录集包含多个记录满足的条件`FindFirst`查找第一个匹配项，`FindNext`查找下一个匹配项，依次类推。  
  
> [!CAUTION]
>  如果编辑当前记录，请务必保存所做的更改通过调用`Update`成员函数之前将移到另一条记录。 如果将移到另一条记录而不更新，所做的更改将丢失而不发出警告。  
  
 `Find`成员函数搜索的位置和下表中指定的方向：  
  
|查找操作|开始|搜索方向|  
|---------------------|-----------|----------------------|  
|`FindFirst`|记录集的开头|记录集的结尾|  
|`FindLast`|记录集的结尾|记录集的开头|  
|`FindNext`|当前记录|记录集的结尾|  
|`FindPrevious`|当前记录|记录集的开头|  
  
> [!NOTE]
>  当您调用`FindLast`，Microsoft Jet 数据库引擎完全填充记录集之前开始搜索，如果这不已完成。 第一次搜索可能超过后续搜索。  
  
 使用查找操作的其中一个不是调用相同`MoveFirst`或`MoveNext`，但是，这只是将第一个或下一个记录当前无需指定一个条件。 可以按照与移动操作查找操作。  
  
 使用查找操作时，请记住以下：  
  
-   如果`Find`返回非零值，未定义的当前记录。 在这种情况下，您必须定位当前记录指针返回到有效的记录。  
  
-   查找操作不能使用只进滚动快照类型记录集。  
  
-   应使用美国英语日期格式 （月-日-年） 时您搜索的字段包含日期，即使不使用 Microsoft Jet 数据库引擎; 美国版本否则，匹配记录可能会找到。  
  
-   当使用 ODBC 数据库和大型的动态集，可能会发现的使用的查找操作速度变慢，尤其在使用大型记录集时。 可以通过使用 SQL 查询来提高性能与自定义**ORDERBY**或**其中**子句，参数查询或`CDaoQuerydef`检索特定索引的记录的对象。  
  
 有关相关信息，请参阅主题"FindFirst，FindLast FindNext，FindPrevious 方法"DAO 帮助中。  
  
##  <a name="findlast"></a>  CDaoRecordset::FindLast  
 调用此成员函数以查找与指定的条件匹配的最后一个记录。  
  
```  
BOOL FindLast(LPCTSTR lpszFilter);
```  
  
### <a name="parameters"></a>参数  
 *lpszFilter*  
 字符串表达式 (如**其中**SQL 语句，而无需单词中的子句**其中**) 用于查找的记录。  
  
### <a name="return-value"></a>返回值  
 如果找到匹配的记录，否则为 0，非零值。  
  
### <a name="remarks"></a>备注  
 `FindLast`成员函数开始其搜索末尾的记录集和记录集开始向后搜索。  
  
 如果你想要包括所有记录 （而不仅仅是满足特定条件的那些） 在搜索中使用的移动操作之一来记录之间移动。 若要找到一条记录中类型一个表的记录集，请调用`Seek`成员函数。  
  
 如果未找到与条件匹配的记录了，是不确定，当前记录指针和`FindLast`返回零。 如果记录集包含多个记录满足的条件`FindFirst`查找第一个匹配项，`FindNext`查找下一个匹配项后的第一个匹配项，依此类推。  
  
> [!CAUTION]
>  如果编辑当前记录，请确保通过调用保存所做的更改`Update`成员函数之前将移到另一条记录。 如果将移到另一条记录而不更新，所做的更改将丢失而不发出警告。  
  
 使用查找操作的其中一个不是调用相同`MoveFirst`或`MoveNext`，但是，这只是将第一个或下一个记录当前无需指定一个条件。 可以按照与移动操作查找操作。  
  
 使用查找操作时，请记住以下：  
  
-   如果`Find`返回非零值，未定义的当前记录。 在这种情况下，您必须定位当前记录指针返回到有效的记录。  
  
-   查找操作不能使用只进滚动快照类型记录集。  
  
-   应使用美国英语日期格式 （月-日-年） 时您搜索的字段包含日期，即使不使用 Microsoft Jet 数据库引擎; 美国版本否则，匹配记录可能会找到。  
  
-   当使用 ODBC 数据库和大型的动态集，可能会发现的使用的查找操作速度变慢，尤其在使用大型记录集时。 可以通过使用 SQL 查询来提高性能与自定义**ORDERBY**或**其中**子句，参数查询或`CDaoQuerydef`检索特定索引的记录的对象。  
  
 有关相关信息，请参阅主题"FindFirst，FindLast FindNext，FindPrevious 方法"DAO 帮助中。  
  
##  <a name="findnext"></a>  CDaoRecordset::FindNext  
 调用此成员函数以查找与指定的条件匹配的下一个记录。  
  
```  
BOOL FindNext(LPCTSTR lpszFilter);
```  
  
### <a name="parameters"></a>参数  
 *lpszFilter*  
 字符串表达式 (如**其中**SQL 语句，而无需单词中的子句**其中**) 用于查找的记录。  
  
### <a name="return-value"></a>返回值  
 如果找到匹配的记录，否则为 0，非零值。  
  
### <a name="remarks"></a>备注  
 `FindNext`成员函数开始处的当前记录其搜索，一直搜索到记录集的结尾。  
  
 如果你想要包括所有记录 （而不仅仅是满足特定条件的那些） 在搜索中使用的移动操作之一来记录之间移动。 若要找到一条记录中类型一个表的记录集，请调用`Seek`成员函数。  
  
 如果未找到与条件匹配的记录了，是不确定，当前记录指针和`FindNext`返回零。 如果记录集包含多个记录满足的条件`FindFirst`查找第一个匹配项，`FindNext`查找下一个匹配项，依次类推。  
  
> [!CAUTION]
>  如果编辑当前记录，请确保通过调用保存所做的更改`Update`成员函数之前将移到另一条记录。 如果将移到另一条记录而不更新，所做的更改将丢失而不发出警告。  
  
 使用查找操作的其中一个不是调用相同`MoveFirst`或`MoveNext`，但是，这只是将第一个或下一个记录当前无需指定一个条件。 可以按照与移动操作查找操作。  
  
 使用查找操作时，请记住以下：  
  
-   如果`Find`返回非零值，未定义的当前记录。 在这种情况下，您必须定位当前记录指针返回到有效的记录。  
  
-   查找操作不能使用只进滚动快照类型记录集。  
  
-   应使用美国英语日期格式 （月-日-年） 时您搜索的字段包含日期，即使不使用 Microsoft Jet 数据库引擎; 美国版本否则，匹配记录可能会找到。  
  
-   当使用 ODBC 数据库和大型的动态集，可能会发现的使用的查找操作速度变慢，尤其在使用大型记录集时。 可以通过使用 SQL 查询来提高性能与自定义**ORDERBY**或**其中**子句，参数查询或`CDaoQuerydef`检索特定索引的记录的对象。  
  
 有关相关信息，请参阅主题"FindFirst，FindLast FindNext，FindPrevious 方法"DAO 帮助中。  
  
##  <a name="findprev"></a>  CDaoRecordset::FindPrev  
 调用此成员函数以查找与指定的条件匹配的前一条记录。  
  
```  
BOOL FindPrev(LPCTSTR lpszFilter);
```  
  
### <a name="parameters"></a>参数  
 *lpszFilter*  
 字符串表达式 (如**其中**SQL 语句，而无需单词中的子句**其中**) 用于查找的记录。  
  
### <a name="return-value"></a>返回值  
 如果找到匹配的记录，否则为 0，非零值。  
  
### <a name="remarks"></a>备注  
 `FindPrev`成员函数开始其搜索的时间的当前记录和记录集开始向后搜索。  
  
 如果你想要包括所有记录 （而不仅仅是满足特定条件的那些） 在搜索中使用的移动操作之一来记录之间移动。 若要找到一条记录中类型一个表的记录集，请调用`Seek`成员函数。  
  
 如果未找到与条件匹配的记录了，是不确定，当前记录指针和`FindPrev`返回零。 如果记录集包含多个记录满足的条件`FindFirst`查找第一个匹配项，`FindNext`查找下一个匹配项，依次类推。  
  
> [!CAUTION]
>  如果编辑当前记录，请确保通过调用保存所做的更改`Update`成员函数之前将移到另一条记录。 如果将移到另一条记录而不更新，所做的更改将丢失而不发出警告。  
  
 使用查找操作的其中一个不是调用相同`MoveFirst`或`MoveNext`，但是，这只是将第一个或下一个记录当前无需指定一个条件。 可以按照与移动操作查找操作。  
  
 使用查找操作时，请记住以下：  
  
-   如果`Find`返回非零值，未定义的当前记录。 在这种情况下，您必须定位当前记录指针返回到有效的记录。  
  
-   查找操作不能使用只进滚动快照类型记录集。  
  
-   应使用美国英语日期格式 （月-日-年） 时您搜索的字段包含日期，即使不使用 Microsoft Jet 数据库引擎; 美国版本否则，匹配记录可能会找到。  
  
-   当使用 ODBC 数据库和大型的动态集，可能会发现的使用的查找操作速度变慢，尤其在使用大型记录集时。 可以通过使用 SQL 查询来提高性能与自定义**ORDERBY**或**其中**子句，参数查询或`CDaoQuerydef`检索特定索引的记录的对象。  
  
 有关相关信息，请参阅主题"FindFirst，FindLast FindNext，FindPrevious 方法"DAO 帮助中。  
  
##  <a name="getabsoluteposition"></a>  CDaoRecordset::GetAbsolutePosition  
 返回记录集对象的当前记录的记录数。  
  
```  
long GetAbsolutePosition();
```  
  
### <a name="return-value"></a>返回值  
 从 0 到记录集中的记录数的整数。 对应于当前记录的记录集中的序号位置。  
  
### <a name="remarks"></a>备注  
 AbsolutePosition 属性值的基础的 DAO 对象是从零开始;设置为 0 是指在记录集中的第一个记录。 可以通过调用确定记录集填充记录数[GetRecordCount](#getrecordcount)。 调用`GetRecordCount`可能需要一些时间，因为它必须访问所有记录，以确定计数。  
  
 如果没有当前记录，为时没有记录集中的记录，则返回 1。 如果删除当前记录，则不定义 AbsolutePosition 属性值，并且 MFC 会引发异常，如果它引用。 动态集类型的记录集，为新记录添加到序列的末尾。  
  
> [!NOTE]
>  此属性不是要用作代理记录编号。 仍建议采用书签保留和返回到给定位置，而且这是在所有类型的记录集对象之间定位当前记录的唯一方法。 具体而言，给定的记录的位置发生更改时将删除其前面的记录。 此外，还有，如果重新因为除非创建与 SQL 语句中使用，否则不能保证在记录集内的单个记录的顺序重新创建记录集，给定的记录将具有相同的绝对位置不能保证**ORDERBY**子句。  
  
> [!NOTE]
>  此成员函数仅适用于动态集类型和快照类型的记录集无效。  
  
 有关相关信息，请参阅主题 DAO 帮助中的"AbsolutePosition 属性"。  
  
##  <a name="getbookmark"></a>  CDaoRecordset::GetBookmark  
 调用此成员函数可获取特定记录中的书签值。  
  
```  
COleVariant GetBookmark();
```  
  
### <a name="return-value"></a>返回值  
 返回一个值，表示当前记录上的书签。  
  
### <a name="remarks"></a>备注  
 当创建或打开记录集对象时，其记录的每个已具有一个唯一的书签支持它们。 调用`CanBookmark`确定记录集是否支持书签。  
  
 可以将当前记录的书签保存到书签的值指定`COleVariant`对象。 若要快速返回到该记录随时移动到另一个记录后，调用`SetBookmark`带参数的值对应`COleVariant`对象。  
  
> [!NOTE]
>  调用[再次查询](#requery)更改 DAO 书签。  
  
 有关相关信息，请参阅主题 DAO 帮助中的"书签属性"。  
  
##  <a name="getcachesize"></a>  CDaoRecordset::GetCacheSize  
 调用此成员函数以获取缓存的记录数。  
  
```  
long GetCacheSize();
```  
  
### <a name="return-value"></a>返回值  
 一个值，指定动态集类型的记录集包含本地缓存从 ODBC 数据源数据中的记录数。  
  
### <a name="remarks"></a>备注  
 数据缓存提高了从远程服务器通过动态集类型的记录集对象中检索数据的应用程序的性能。 缓存是在包含最新的事件中运行应用程序时将再次请求数据从服务器检索的数据的本地内存中的空间。 请求数据，Microsoft Jet 数据库引擎为所请求的数据会首先检查缓存而不是从花费的时间的服务器中检索它。 不是来自 ODBC 数据源的数据不保存在缓存中。  
  
 任何 ODBC 数据源，如附加表，可以本地缓存。  
  
 相关信息，请参阅 DAO 帮助中的主题"CacheSize，CacheStart 属性"。  
  
##  <a name="getcachestart"></a>  CDaoRecordset::GetCacheStart  
 调用此成员函数来获取书签值的记录集缓存中的第一个记录。  
  
```  
COleVariant GetCacheStart();
```  
  
### <a name="return-value"></a>返回值  
 一个`COleVariant`，它指定记录集缓存中的第一条记录的书签。  
  
### <a name="remarks"></a>备注  
 Microsoft Jet 数据库引擎从缓存中请求缓存范围内的记录并从服务器请求到缓存范围外的记录。  
  
> [!NOTE]
>  从缓存中检索的记录不反映对源数据同时进行的其他用户的更改。  
  
 相关信息，请参阅 DAO 帮助中的主题"CacheSize，CacheStart 属性"。  
  
##  <a name="getcurrentindex"></a>  CDaoRecordset::GetCurrentIndex  
 调用此成员函数可确定当前正在使用中索引的表类型索引`CDaoRecordset`对象。  
  
```  
CString GetCurrentIndex();
```  
  
### <a name="return-value"></a>返回值  
 一个`CString`包含索引当前正在使用与类型一个表的记录集的名称。 如果已设置没有索引，则返回空字符串。  
  
### <a name="remarks"></a>备注  
 此索引是对记录中的表类型的记录集中，排序的基础，并由[Seek](#seek)成员函数来查找记录。  
  
 一个`CDaoRecordset`对象可以有多个索引，但可以使用一次只有一个索引 (尽管[CDaoTableDef](../../mfc/reference/cdaotabledef-class.md)对象可能具有针对它定义的多个索引)。  
  
 有关相关信息，请参阅主题"索引对象"和"当前索引"DAO 帮助中的定义。  
  
##  <a name="getdatecreated"></a>  CDaoRecordset::GetDateCreated  
 调用此成员函数可检索的日期和时间创建基本表。  
  
```  
COleDateTime GetDateCreated();
```  
  
### <a name="return-value"></a>返回值  
 一个[COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)对象，其中包含的日期和时间创建基本表。  
  
### <a name="remarks"></a>备注  
 日期和时间设置派生自创建基本表的计算机。  
  
 相关信息，请参阅 DAO 帮助中的主题"DateCreated，上次更新属性"。  
  
##  <a name="getdatelastupdated"></a>  CDaoRecordset::GetDateLastUpdated  
 调用此成员函数可检索的日期和时间上次更新架构。  
  
```  
COleDateTime GetDateLastUpdated();
```  
  
### <a name="return-value"></a>返回值  
 一个[COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)对象，其中包含的日期和时间上次更新基表结构 （架构）。  
  
### <a name="remarks"></a>备注  
 日期和时间设置派生自基本表结构 （架构） 的上次更新的计算机。  
  
 相关信息，请参阅 DAO 帮助中的主题"DateCreated，上次更新属性"。  
  
##  <a name="getdefaultdbname"></a>  CDaoRecordset::GetDefaultDBName  
 调用此成员函数来确定此记录集的数据库的名称。  
  
```  
virtual CString GetDefaultDBName();
```  
  
### <a name="return-value"></a>返回值  
 一个`CString`，其中包含的路径和从其派生此记录集的数据库的名称。  
  
### <a name="remarks"></a>备注  
 如果未一个指针创建一个记录集[CDaoDatabase](../../mfc/reference/cdaodatabase-class.md)，则该记录集使用此路径来打开默认数据库。 默认情况下，此函数返回空字符串。 当 ClassWizard 派生新的记录集从`CDaoRecordset`，它将为你创建此函数。  
  
 下面的示例演示如何使用双反斜杠 (\\\\) 在字符串中，按原样需要正确地解释的字符串。  
  
 [!code-cpp[NVC_MFCDatabase#4](../../mfc/codesnippet/cpp/cdaorecordset-class_4.cpp)]  
  
##  <a name="getdefaultsql"></a>  CDaoRecordset::GetDefaultSQL  
 框架调用此成员函数可获取记录集所基于的默认 SQL 语句。  
  
```  
virtual CString GetDefaultSQL();
```  
  
### <a name="return-value"></a>返回值  
 一个`CString`，其中包含默认的 SQL 语句。  
  
### <a name="remarks"></a>备注  
 这可能是表名称或 SQL**选择**语句。  
  
 间接通过声明类向导，在记录集类定义默认的 SQL 语句和类向导会为您执行此任务。  
  
 如果传递到空的 SQL 字符串[打开](#open)，则调用此函数来确定记录集的表名称或 SQL。  
  
##  <a name="geteditmode"></a>  CDaoRecordset::GetEditMode  
 调用此成员函数来确定状态的编辑，这是以下值之一：  
  
```  
short GetEditMode();
```  
  
### <a name="return-value"></a>返回值  
 返回一个值，该值指示当前记录的编辑状态。  
  
### <a name="remarks"></a>备注  
  
|“值”|描述|  
|-----------|-----------------|  
|`dbEditNone`|不正在编辑的任何操作。|  
|`dbEditInProgress`|`Edit` 已调用。|  
|`dbEditAdd`|`AddNew` 已调用。|  
  
 有关相关信息，请参阅主题 DAO 帮助中的"EditMode 属性"。  
  
##  <a name="getfieldcount"></a>  CDaoRecordset::GetFieldCount  
 调用此成员函数可检索的记录集中定义的字段 （列）。  
  
```  
short GetFieldCount();
```  
  
### <a name="return-value"></a>返回值  
 在记录集中的字段数。  
  
### <a name="remarks"></a>备注  
 有关相关信息，请参阅主题 DAO 帮助中的"计数属性"。  
  
##  <a name="getfieldinfo"></a>  CDaoRecordset::GetFieldInfo  
 调用此成员函数以获取有关在记录集中的字段的信息。  
  
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
 *nIndex*  
 记录集的字段集合，用于查找索引中的预定义字段的从零开始的索引。  
  
 *fieldinfo*  
 对引用[CDaoFieldInfo](../../mfc/reference/cdaofieldinfo-structure.md)结构。  
  
 *dwInfoOptions*  
 指定要检索的记录集有关的信息的选项。 可用选项以及它们会导致函数返回此处列出。 为了获得最佳性能，检索仅的所需的信息的级别：  
  
- `AFX_DAO_PRIMARY_INFO` （默认值）名称、 类型、 大小、 属性  
  
- `AFX_DAO_SECONDARY_INFO` 主要信息加上： 序号位置，必需的允许为零长度，排序规则顺序外名称、 源字段中，源表  
  
- `AFX_DAO_ALL_INFO` 主要和次要信息加上： 默认值，验证规则验证文本  
  
 *lpszName*  
 字段的名称。  
  
### <a name="remarks"></a>备注  
 函数的一个版本，可按索引查找字段。 另一个版本，可以按名称查找字段。  
  
 返回的信息的说明，请参阅[CDaoFieldInfo](../../mfc/reference/cdaofieldinfo-structure.md)结构。 此结构具有对应于上面列出的说明中的信息的项目的成员*dwInfoOptions*。 当请求在某一级别的信息时，可以获取任何以前的级别的信息。  
  
 有关相关信息，请参阅主题 DAO 帮助中的"特性属性"。  
  
##  <a name="getfieldvalue"></a>  CDaoRecordset::GetFieldValue  
 调用此成员函数以检索在记录集中的数据。  
  
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
 *lpszName*  
 指向包含的字段名称的字符串的指针。  
  
 *varValue*  
 对引用`COleVariant`将存储字段的值的对象。  
  
 *nIndex*  
 在记录集的字段集合中，按索引查找的字段的一个从零开始的索引。  
  
### <a name="return-value"></a>返回值  
 两个版本的`GetFieldValue`的返回值返回[COleVariant](../../mfc/reference/colevariant-class.md)对象，其中包含字段的值。  
  
### <a name="remarks"></a>备注  
 您可以查看字段按名称或序号位置。  
  
> [!NOTE]
>  调用此成员函数的版本之一的效率更高`COleVariant`对象引用作为参数，而不是调用返回的版本`COleVariant`对象。 此函数后一种版本保持向后兼容性。  
  
 使用`GetFieldValue`并[SetFieldValue](#setfieldvalue)若要动态绑定在运行的时而不是以静态方式使用绑定列的字段[DoFieldExchange](#dofieldexchange)机制。  
  
 `GetFieldValue` 和`DoFieldExchange`机制可以组合起来，以提高性能。 例如，使用`GetFieldValue`检索一个值，你需要仅按需、 并将分配到界面中的"更多信息"按钮该调用。  
  
 有关相关信息，请参阅主题"字段对象"和 DAO 帮助中的"值属性"。  
  
##  <a name="getindexcount"></a>  CDaoRecordset::GetIndexCount  
 调用此成员函数可确定类型一个表的记录集上可用的索引号。  
  
```  
short GetIndexCount();
```  
  
### <a name="return-value"></a>返回值  
 中的表类型的记录集的索引数。  
  
### <a name="remarks"></a>备注  
 `GetIndexCount` 可用于循环遍历记录集中的所有索引。 为此，使用`GetIndexCount`结合[GetIndexInfo](#getindexinfo)。 如果动态集类型或快照类型的记录集上调用此成员函数，MFC 会引发异常。  
  
 有关相关信息，请参阅主题 DAO 帮助中的"特性属性"。  
  
##  <a name="getindexinfo"></a>  CDaoRecordset::GetIndexInfo  
 调用此成员函数以获取各种类型的记录集的基础基表中定义的索引信息。  
  
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
 *nIndex*  
 在表的索引集合中，按数字位置查找的从零开始的索引。  
  
 *indexinfo*  
 对引用[CDaoIndexInfo](../../mfc/reference/cdaoindexinfo-structure.md)结构。  
  
 *dwInfoOptions*  
 指定要检索的索引有关的信息的选项。 可用选项以及它们会导致函数返回此处列出。 为了获得最佳性能，检索仅的所需的信息的级别：  
  
- `AFX_DAO_PRIMARY_INFO` （默认值）名称字段信息字段  
  
- `AFX_DAO_SECONDARY_INFO` 主要信息加上： 主、 Unique、 聚集、 IgnoreNulls，必需的外部  
  
- `AFX_DAO_ALL_INFO` 主要和次要信息加上： 非重复计数  
  
 *lpszName*  
 一个指向按名称查找索引对象的名称。  
  
### <a name="remarks"></a>备注  
 函数的一个版本能够让您通过在集合中的位置的索引查找。 另一个版本，可以按名称查找索引。  
  
 返回的信息的说明，请参阅[CDaoIndexInfo](../../mfc/reference/cdaoindexinfo-structure.md)结构。 此结构具有对应于上面列出的说明中的信息的项目的成员*dwInfoOptions*。 当请求在某一级别的信息时，可以获取任何以前的级别的信息。  
  
 有关相关信息，请参阅主题 DAO 帮助中的"特性属性"。  
  
##  <a name="getlastmodifiedbookmark"></a>  CDaoRecordset::GetLastModifiedBookmark  
 调用此成员函数以检索最近添加或更新记录的书签。  
  
```  
COleVariant GetLastModifiedBookmark();
```  
  
### <a name="return-value"></a>返回值  
 一个`COleVariant`包含一个书签，用于指示最近添加或更改记录。  
  
### <a name="remarks"></a>备注  
 当创建或打开记录集对象时，其记录的每个已具有一个唯一的书签支持它们。 调用[GetBookmark](#getbookmark)来确定记录集是否支持书签。 如果记录集不支持书签，`CDaoException`引发。  
  
 当添加一条记录时，它出现在该记录集的末尾并不是当前记录。 若要激活新的记录，请调用`GetLastModifiedBookmark`，然后调用`SetBookmark`以返回到新添加的记录。  
  
 有关相关信息，请参阅主题 DAO 帮助中的"上次更改时间属性"。  
  
##  <a name="getlockingmode"></a>  CDaoRecordset::GetLockingMode  
 调用此成员函数可确定记录集实际上锁定的类型。  
  
```  
BOOL GetLockingMode();
```  
  
### <a name="return-value"></a>返回值  
 非零的锁定类型是否为悲观，否则为 0 表示开放式记录锁定。  
  
### <a name="remarks"></a>备注  
 只要您调用保守式锁定时有效时，包含要编辑的记录的数据页锁定[编辑](#edit)成员函数。 在调用时，页处于未锁定[更新](#update)或[关闭](#close)成员函数或任何移动或查找操作。  
  
 乐观锁定实际上是包含记录的数据页被锁定，仅在使用更新记录时`Update`成员函数。  
  
 在使用 ODBC 数据源，始终是乐观锁定模式。  
  
 有关相关信息，请参阅"LockEdits 属性"和"锁定行为中多个用户应用程序"DAO 帮助中的主题。  
  
##  <a name="getname"></a>  CDaoRecordset::GetName  
 调用此成员函数可检索的记录集名称。  
  
```  
CString GetName();
```  
  
### <a name="return-value"></a>返回值  
 一个`CString`包含记录集的名称。  
  
### <a name="remarks"></a>备注  
 记录集名称必须以字母开头，并且可以包含最多 40 个字符。 它可以包括数字和下划线字符，但不能包含标点或空格。  
  
 有关相关信息，请参阅主题 DAO 帮助中的"名称属性"。  
  
##  <a name="getparamvalue"></a>  CDaoRecordset::GetParamValue  
 调用此成员函数以检索基础 DAOParameter 对象中存储的指定参数的当前值。  
  
```  
virtual COleVariant GetParamValue(int nIndex);  
virtual COleVariant GetParamValue(LPCTSTR lpszName);
```  
  
### <a name="parameters"></a>参数  
 *nIndex*  
 参数的基础 DAOParameter 对象中的数字位置。  
  
 *lpszName*  
 参数所需的值的名称。  
  
### <a name="return-value"></a>返回值  
 类的对象[COleVariant](../../mfc/reference/colevariant-class.md) ，其中包含参数的值。  
  
### <a name="remarks"></a>备注  
 按名称或集合中其数字位置，可以访问该参数。  
  
 有关相关信息，请参阅主题 DAO 帮助中的"参数对象"。  
  
##  <a name="getpercentposition"></a>  CDaoRecordset::GetPercentPosition  
 使用动态集类型或快照类型的记录集中，如果调用时`GetPercentPosition`完全填充记录集时之前, 的移动量是相对于访问由调用的记录数目[GetRecordCount](#getrecordcount).  
  
```  
float GetPercentPosition();
```  
  
### <a name="return-value"></a>返回值  
 指示基于百分比的记录集中记录的记录集对象中的当前记录的近似位置数介于 0 和 100 之间。  
  
### <a name="remarks"></a>备注  
 您可以移动到最后一个记录通过调用[MoveLast](#movelast)到完整的填充行为的所有记录集，但这可能需要很长的时间。  
  
 您可以调用`GetPercentPosition`对所有三种类型的记录集对象，其中包括没有索引的表。 但是，不能调用`GetPercentPosition`仅向前滚动快照，或从外部数据库对的传递查询打开的记录集。 如果没有当前记录，或者他当前记录已被删除，`CDaoException`引发。  
  
 有关相关信息，请参阅主题 DAO 帮助中的"PercentPosition 属性"。  
  
##  <a name="getrecordcount"></a>  CDaoRecordset::GetRecordCount  
 调用此成员函数来找出在记录集中的多少条记录已被访问。  
  
```  
long GetRecordCount();
```  
  
### <a name="return-value"></a>返回值  
 返回记录集对象中访问的记录的数。  
  
### <a name="remarks"></a>备注  
 `GetRecordCount` 并不表示直到已经被访问过的所有记录中的动态集类型或快照类型的记录集包含多少条记录。 此成员函数调用可能需要很长时间才能完成。  
  
 一旦被访问的最后一个记录，则返回值指示撤消删除记录集中记录的总数。 若要强制执行要访问的最后一个记录，请调用`MoveLast`或`FindLast`记录集的成员函数。 此外可以使用 SQL 计数以确定你的查询将返回的记录的大致数目。  
  
 你的应用程序删除动态集类型的记录集，返回值中的记录`GetRecordCount`会降低。 但是，删除其他用户的记录不反映通过`GetRecordCount`直到当前的记录放到已删除记录。 如果执行的事务的影响的记录计数并随后回滚事务，`GetRecordCount`将不会反映实际的剩余的记录数。  
  
 值`GetRecordCount`从快照类型记录集不受基础表中的更改。  
  
 值`GetRecordCount`表类型从记录集反映了的表中的记录的大致数目和添加和删除表记录时，会立即影响。  
  
 具有未记录的记录集返回的值为 0。 使用附加的表或 ODBC 数据库时`GetRecordCount`始终返回-1。 调用`Requery`上记录集的成员函数的值重置`GetRecordCount`就好像是重新执行查询。  
  
 有关相关信息，请参阅主题 DAO 帮助中的"RecordCount 属性"。  
  
##  <a name="getsql"></a>  CDaoRecordset::GetSQL  
 调用此成员函数可获取用于选择记录集的记录时已打开的 SQL 语句。  
  
```  
CString GetSQL() const;  
```  
  
### <a name="return-value"></a>返回值  
 一个`CString`，其中包含 SQL 语句。  
  
### <a name="remarks"></a>备注  
 这通常是 SQL**选择**语句。  
  
 返回的字符串`GetSQL`通常不同于你可能会传递到记录集在任何字符串*lpszSQL*参数[打开](#open)成员函数。 这是因为该记录集构造基于传递给一个完整的 SQL 语句`Open`、 使用类向导，指定的内容和可能具有中指定的内容[m_strFilter](#m_strfilter)和[m_strSort](#m_strsort)数据成员。  
  
> [!NOTE]
>  仅在调用后调用此成员函数`Open`。  
  
 有关相关信息，请参阅主题 DAO 帮助中的"SQL 属性"。  
  
##  <a name="gettype"></a>  CDaoRecordset::GetType  
 打开要确定记录集对象的类型的记录集后调用此成员函数。  
  
```  
short GetType();
```  
  
### <a name="return-value"></a>返回值  
 以下值，该值指示记录集的类型之一：  
  
- `dbOpenTable` 表类型的记录集  
  
- `dbOpenDynaset` 动态集类型的记录集  
  
- `dbOpenSnapshot` 快照类型的记录集  
  
### <a name="remarks"></a>备注  
 有关相关信息，请参阅主题 DAO 帮助中的"类型属性"。  
  
##  <a name="getvalidationrule"></a>  CDaoRecordset::GetValidationRule  
 调用此成员函数可确定用于验证数据的规则。  
  
```  
CString GetValidationRule();
```  
  
### <a name="return-value"></a>返回值  
 一个`CString`对象，其中包含一个值，因为它已更改或添加到表验证记录中的数据。  
  
### <a name="remarks"></a>备注  
 此规则是基于文本的并应用每次更改基础表。 如果数据不是合法的 MFC 会引发异常。 如果指定，基础字段对象的有效性的文本或由基础的字段对象的 ValidationRule 属性所指定的表达式的文本，返回的错误消息。 您可以调用[GetValidationText](#getvalidationtext)来获取错误消息的文本。  
  
 例如，需要每月天数的记录中的字段可能具有的验证规则例如"天 BETWEEN 1 到 31。"  
  
 有关相关信息，请参阅主题 DAO 帮助中的"ValidationRule 属性"。  
  
##  <a name="getvalidationtext"></a>  CDaoRecordset::GetValidationText  
 调用此成员函数以检索基础字段对象的有效性的文本。  
  
```  
CString GetValidationText();
```  
  
### <a name="return-value"></a>返回值  
 一个`CString`对象，其中包含的消息，如果字段的值不符合验证规则的基础字段对象的显示的文本。  
  
### <a name="remarks"></a>备注  
 有关相关信息，请参阅主题 DAO 帮助中的"有效性文本属性"。  
  
##  <a name="isbof"></a>  CDaoRecordset::IsBOF  
 之前从记录滚动到记录以了解是否已在第一个记录的记录集之前调用此成员函数。  
  
```  
BOOL IsBOF() const;  
```  
  
### <a name="return-value"></a>返回值  
 如果记录集不包含任何记录，或如果已在第一条记录; 之前向后滚动，则非零值否则为 0。  
  
### <a name="remarks"></a>备注  
 您还可以调用`IsBOF`连同`IsEOF`来确定记录集是否包含任何记录，或为空。 立即调用后`Open`，如果记录集不包含任何记录，`IsBOF`返回非零值。 打开具有至少一个记录的记录集，第一条记录时的当前记录和`IsBOF`返回 0。  
  
 如果第一条记录的当前记录，并且你调用`MovePrev`，`IsBOF`随后将返回非零值。 如果`IsBOF`返回非零值，并且您调用`MovePrev`，将引发异常。 如果`IsBOF`返回非零值时，当前记录是不确定，并需要当前记录任何操作将导致异常。  
  
 对特定方法的效果`IsBOF`和`IsEOF`设置：  
  
-   调用`Open*`在内部使第一条记录中记录集的当前记录通过调用`MoveFirst`。 因此，调用`Open`上的记录会导致空集`IsBOF`和`IsEOF`若要返回非零值。 (请参阅下表中的失败行为`MoveFirst`或`MoveLast`调用。)  
  
-   已成功找到一条记录的所有移动操作会都导致两者`IsBOF`和`IsEOF`返回 0。  
  
-   `AddNew`调用后面`Update`成功插入新记录的调用将导致`IsBOF`返回 0，但是只有当`IsEOF`已为非零值。 状态`IsEOF`将始终保持不变。 根据 Microsoft Jet 数据库引擎的定义，空记录集的当前记录指针是一个文件的末尾，因此当前记录后插入任何新的记录。  
  
-   任何`Delete`调用，即使它可以删除记录集，其余的唯一记录不会更改的值`IsBOF`或`IsEOF`。  
  
 此表显示了使用不同的组合允许哪些移动操作`IsBOF` /  `IsEOF`。  
  
||MoveFirst、 MoveLast|MovePrev，<br /><br /> 移动 < 0|移动 0|MoveNext，<br /><br /> 移动 > 0|  
|------|-------------------------|-----------------------------|------------|-----------------------------|  
|`IsBOF`= 非零值，<br /><br /> `IsEOF`=0|Allowed|例外|例外|Allowed|  
|`IsBOF`=0,<br /><br /> `IsEOF`= 非零值|Allowed|Allowed|例外|例外|  
|非零值都|例外|例外|例外|例外|  
|这两个 0|Allowed|Allowed|Allowed|Allowed|  
  
 允许移动操作并不意味着该操作将成功找到一条记录。 它只是表示尝试执行指定的移动操作允许的不会生成异常。 值`IsBOF`和`IsEOF`成员函数可能会因所尝试的移动而更改。  
  
 找不到一条记录的值的移动操作的效果`IsBOF`和`IsEOF`下表中显示设置。  
  
||IsBOF|IsEOF|  
|------|-----------|-----------|  
|`MoveFirst`, `MoveLast`|非零值|非零值|  
|`Move` 0|无更改|无更改|  
|`MovePrev``Move` < 0|非零值|无更改|  
|`MoveNext``Move` > 0|无更改|非零值|  
  
 有关相关信息，请参阅主题"BOF、 EOF 属性"DAO 帮助中。  
  
##  <a name="isdeleted"></a>  CDaoRecordset::IsDeleted  
 调用此成员函数可确定当前记录是否已被删除。  
  
```  
BOOL IsDeleted() const;  
```  
  
### <a name="return-value"></a>返回值  
 如果记录集定位在已删除的记录; 上的非零否则为 0。  
  
### <a name="remarks"></a>备注  
 如果滚动到一条记录和`IsDeleted`返回 TRUE （非零），则您必须向下滚动到另一个记录之前可以执行任何其他记录集操作。  
  
> [!NOTE]
>  不需要检查快照或表类型的记录集中记录的已删除的状态。 因为不能从快照中删除记录，则无需调用`IsDeleted`。 为表类型的记录集，已删除的记录实际上会从记录集。 后一条记录已被删除，由你，另一个用户，或在另一个记录集，您不能向下滚动到相应的记录。 因此，没有无需调用`IsDeleted`。  
  
 从动态集删除记录时，将会删除从记录集并且您不能向下滚动到相应的记录。 但是，如果记录中动态集并删除由另一个用户或基于同一个表，另一个记录集中`IsDeleted`更高版本滚动到相应的记录时，将返回 TRUE。  
  
 有关相关信息，请参阅"Delete 方法"、"上次更改时间属性"和"EditMode 属性"DAO 帮助中的主题。  
  
##  <a name="iseof"></a>  CDaoRecordset::IsEOF  
 调用此成员函数，如从记录滚动到记录以了解是否已超出最后一个记录的记录集。  
  
```  
BOOL IsEOF() const;  
```  
  
### <a name="return-value"></a>返回值  
 如果记录集不包含任何记录，或如果已超出最后一条记录; 滚动，则非零值否则为 0。  
  
### <a name="remarks"></a>备注  
 您还可以调用`IsEOF`来确定记录集是否包含任何记录，或为空。 立即调用后`Open`，如果记录集不包含任何记录，`IsEOF`返回非零值。 打开具有至少一个记录的记录集，第一条记录时的当前记录和`IsEOF`返回 0。  
  
 最后一条记录的当前记录时是否调用`MoveNext`，`IsEOF`随后将返回非零值。 如果`IsEOF`返回非零值，并且您调用`MoveNext`，将引发异常。 如果`IsEOF`返回非零值时，当前记录是不确定，并需要当前记录任何操作将导致异常。  
  
 对特定方法的效果`IsBOF`和`IsEOF`设置：  
  
-   调用`Open`在内部使第一条记录中记录集的当前记录通过调用`MoveFirst`。 因此，调用`Open`上的记录会导致空集`IsBOF`和`IsEOF`若要返回非零值。 (请参阅下表中的失败行为`MoveFirst`调用。)  
  
-   已成功找到一条记录的所有移动操作会都导致两者`IsBOF`和`IsEOF`返回 0。  
  
-   `AddNew`调用后面`Update`成功插入新记录的调用将导致`IsBOF`返回 0，但是只有当`IsEOF`已为非零值。 状态`IsEOF`将始终保持不变。 根据 Microsoft Jet 数据库引擎的定义，空记录集的当前记录指针是一个文件的末尾，因此当前记录后插入任何新的记录。  
  
-   任何`Delete`调用，即使它可以删除记录集，其余的唯一记录不会更改的值`IsBOF`或`IsEOF`。  
  
 此表显示了使用不同的组合允许哪些移动操作`IsBOF` /  `IsEOF`。  
  
||MoveFirst、 MoveLast|MovePrev，<br /><br /> 移动 < 0|移动 0|MoveNext，<br /><br /> 移动 > 0|  
|------|-------------------------|-----------------------------|------------|-----------------------------|  
|`IsBOF`= 非零值，<br /><br /> `IsEOF`=0|Allowed|例外|例外|Allowed|  
|`IsBOF`=0,<br /><br /> `IsEOF`= 非零值|Allowed|Allowed|例外|例外|  
|非零值都|例外|例外|例外|例外|  
|这两个 0|Allowed|Allowed|Allowed|Allowed|  
  
 允许移动操作并不意味着该操作将成功找到一条记录。 它只是表示尝试执行指定的移动操作允许的不会生成异常。 值`IsBOF`和`IsEOF`成员函数可能会因所尝试的移动而更改。  
  
 找不到一条记录的值的移动操作的效果`IsBOF`和`IsEOF`下表中显示设置。  
  
||IsBOF|IsEOF|  
|------|-----------|-----------|  
|`MoveFirst`, `MoveLast`|非零值|非零值|  
|`Move` 0|无更改|无更改|  
|`MovePrev``Move` < 0|非零值|无更改|  
|`MoveNext``Move` > 0|无更改|非零值|  
  
 有关相关信息，请参阅主题"BOF、 EOF 属性"DAO 帮助中。  
  
##  <a name="isfielddirty"></a>  CDaoRecordset::IsFieldDirty  
 调用此成员函数，以确定是否已动态集的指定的字段数据成员标记为"已更新"（更改）。  
  
```  
BOOL IsFieldDirty(void* pv);
```  
  
### <a name="parameters"></a>参数  
 *pv*  
 指向字段数据成员你想要检查，则为 NULL 以确定的任何字段是否已更新其状态的指针。  
  
### <a name="return-value"></a>返回值  
 如果指定的字段数据成员标记为已更新; 非零值否则为 0。  
  
### <a name="remarks"></a>备注  
 所有已更新字段数据成员中的数据将传输到记录上的数据源时的当前记录更新通过调用`Update`成员函数`CDaoRecordset`(在调用`Edit`或`AddNew`)。 了解这一点，您可以采取进一步的步骤，如取消标记要将列标记，因此它不会写入到数据源的字段数据成员。  
  
 `IsFieldDirty` 通过实现`DoFieldExchange`。  
  
##  <a name="isfieldnull"></a>  CDaoRecordset::IsFieldNull  
 调用此成员函数可确定记录集的指定的字段数据成员是否已标记为 Null。  
  
```  
BOOL IsFieldNull(void* pv);
```  
  
### <a name="parameters"></a>参数  
 *pv*  
 指向字段数据成员的状态，你想要进行检查，或者以确定的任何字段是否为 Null，则为 NULL 指针。  
  
### <a name="return-value"></a>返回值  
 如果指定的字段数据成员标记为 Null; 非零值否则为 0。  
  
### <a name="remarks"></a>备注  
 （在数据库术语中，Null 意味着"无值"，并且不为 NULL，c + + 中相同。）如果字段数据成员标记为 Null，它被解释为当前记录没有值的列。  
  
> [!NOTE]
>  在某些情况下，使用`IsFieldNull`可能效率很低，如下面的代码示例所示：  
  
 [!code-cpp[NVC_MFCDatabase#5](../../mfc/codesnippet/cpp/cdaorecordset-class_5.cpp)]  
  
> [!NOTE]
>  如果使用动态记录绑定，而无需派生自`CDaoRecordset`，请务必使用 VT_NULL，如示例所示。  
  
##  <a name="isfieldnullable"></a>  CDaoRecordset::IsFieldNullable  
 调用以确定是否可为"null"指定的字段数据成员 （可以是设置为一个 Null 值; 如果此成员函数C + + NULL 不是 Null，这意味着，在数据库术语中，相同"having 没有值")。  
  
```  
BOOL IsFieldNullable(void* pv);
```  
  
### <a name="parameters"></a>参数  
 *pv*  
 指向字段数据成员的状态，你想要进行检查，或者以确定的任何字段是否为 Null，则为 NULL 指针。  
  
### <a name="return-value"></a>返回值  
 如果指定的字段数据成员可为 Null; 非零值否则为 0。  
  
### <a name="remarks"></a>备注  
 不能为 Null 的字段必须具有值。 如果您尝试将此类字段设置为 Null 添加或更新记录时，会拒绝添加或更新，数据源和`Update`将引发异常。 在调用时，会发生异常`Update`，在调用时不`SetFieldNull`。  
  
##  <a name="isopen"></a>  CDaoRecordset::IsOpen  
 调用此成员函数可确定记录集处于打开状态。  
  
```  
BOOL IsOpen() const;  
```  
  
### <a name="return-value"></a>返回值  
 如果非零的记录集对象`Open`或`Requery`以前调用成员函数和未关闭记录集; 否则为 0。  
  
### <a name="remarks"></a>备注  
  
##  <a name="m_bcheckcachefordirtyfields"></a>  Cdaorecordset:: M_bcheckcachefordirtyfields  
 包含一个标志，指示是否缓存的字段自动标记为脏 （已更改） 和 Null。  
  
### <a name="remarks"></a>备注  
 该标志默认为 TRUE。 此数据成员中的设置控制整个双缓冲机制。 如果将标志设置为 TRUE 时，可以关闭使用 DFX 机制的逐个字段基础上缓存。 如果标志设置为 FALSE，则必须调用`SetFieldDirty`和`SetFieldNull`自己。  
  
 将之前调用此数据成员设置`Open`。 此机制主要是为了便于使用。 性能可能会由于双缓冲的字段慢随着所做的更改。  
  
##  <a name="m_nfields"></a>  CDaoRecordset::m_nFields  
 包含记录集类中的字段数据成员的数目和选定数据源的记录集的列数。  
  
### <a name="remarks"></a>备注  
 记录集类的构造函数必须初始化`m_nFields`与正确的静态绑定的字段数。 用于声明您记录集的类时，ClassWizard 将写入此初始化时。 您还可以编写它手动。  
  
 该框架使用此数字来管理的对应列的数据源上的当前记录的字段数据成员之间的交互。  
  
> [!NOTE]
>  此数字必须与对应的注册中的输出列数`DoFieldExchange`后调用`SetFieldType`与参数`CDaoFieldExchange::outputColumn`。  
  
 您可以将动态的方式的列绑定`CDaoRecordset::GetFieldValue`和`CDaoRecordset::SetFieldValue`。 如果这样做，不需要在计数增加`m_nFields`以反映的 DFX 函数调用数你`DoFieldExchange`成员函数。  
  
##  <a name="m_nparams"></a>  CDaoRecordset::m_nParams  
 包含记录集类中的参数数据成员的数目，使用记录集的查询传递的参数的数目。  
  
### <a name="remarks"></a>备注  
 如果记录集类具有任何参数的数据成员，类的构造函数必须初始化*m_nParams*与正确的数字。 值*m_nParams*默认值为 0。 如果添加的参数数据成员-必须手动执行该操作，必须手动添加一个初始化类构造函数，以反映参数的数目 (必须至少为数一样大 ' 中的占位符你*m_strFilter*或*m_strSort*字符串)。  
  
 参数化记录集的查询时，框架将使用此数字。  
  
> [!NOTE]
>  此数字必须与对应的"参数"中注册`DoFieldExchange`后调用`SetFieldType`与参数`CFieldExchange::param`。  
  
 有关相关信息，请参阅主题 DAO 帮助中的"参数对象"。  
  
##  <a name="m_pdaorecordset"></a>  CDaoRecordset::m_pDAORecordset  
 包含的 DAO 记录集对象基础的 OLE 接口的指针`CDaoRecordset`对象。  
  
### <a name="remarks"></a>备注  
 如果你需要直接访问 DAO 接口，请使用此指针。  
  
 有关相关信息，请参阅主题 DAO 帮助中的"记录集对象"。  
  
##  <a name="m_pdatabase"></a>  CDaoRecordset::m_pDatabase  
 包含一个指向`CDaoDatabase`对象通过该记录集与连接到数据源。  
  
### <a name="remarks"></a>备注  
 两种方式设置此变量。 通常情况下，将指针传递到已打开`CDaoDatabase`对象构造的记录集对象时。 如果传递 NULL 而`CDaoRecordset`创建`CDaoDatabase`为您的对象并将其打开。 在任一情况下，`CDaoRecordset`将指针存储在此变量。  
  
 通常情况下不直接需要使用存储在指针`m_pDatabase`。 如果您编写自己的扩展到`CDaoRecordset`，但是，您可能需要使用该指针。 例如，您可能需要将指针如果引发自己`CDaoException`(s)。  
  
 有关相关信息，请参阅主题 DAO 帮助中的"数据库对象"。  
  
##  <a name="m_strfilter"></a>  CDaoRecordset::m_strFilter  
 包含一个字符串，用于构造**其中**SQL 语句的子句。  
  
### <a name="remarks"></a>备注  
 它不包括保留的字**其中**来筛选记录集。 使用此数据成员不是适用于表类型的记录集。 利用`m_strFilter`打开记录集使用时，不起`CDaoQueryDef`指针。  
  
 使用美国英语日期格式 （月-日-年） 筛选字段包含日期，即使不使用 Microsoft Jet 数据库引擎; 美国版本时否则，不可能按预期筛选的数据。  
  
 有关相关信息，请参阅主题 DAO 帮助中的"筛选器属性"。  
  
##  <a name="m_strsort"></a>  CDaoRecordset::m_strSort  
 包含一个字符串，包含**ORDERBY** SQL 语句，而无需保留字的子句**ORDERBY**。  
  
### <a name="remarks"></a>备注  
 您可以对动态集和快照类型的记录集对象进行排序。  
  
 不能对类型一个表的记录集对象进行排序。 若要确定类型一个表的记录集的排序顺序，请调用[SetCurrentIndex](#setcurrentindex)。  
  
 利用*m_strSort*不起作用时打开记录集使用`CDaoQueryDef`指针。  
  
 有关相关信息，请参阅主题 DAO 帮助中的"排序属性"。  
  
##  <a name="move"></a>  CDaoRecordset::Move  
 调用此成员函数以定位该记录集*lRows*中当前记录的记录。  
  
```  
virtual void Move(long lRows);
```  
  
### <a name="parameters"></a>参数  
 *lRows*  
 要向前或向后移动的记录数。 值为正，移动到记录集结束。 值为负向后移动的开头。  
  
### <a name="remarks"></a>备注  
 您可以向前或向后移动。 `Move( 1 )` 等效于`MoveNext`，并`Move( -1 )`等效于`MovePrev`。  
  
> [!CAUTION]
>  调用的任何`Move`函数将引发异常，如果记录集不具有任何记录。 一般情况下，请同时调用`IsBOF`和`IsEOF`移动操作，以确定是否记录集的任何记录之前。 调用后`Open`或`Requery`，调用`IsBOF`或`IsEOF`。  
  
> [!NOTE]
>  如果您使用滚动条滚动过去的开头或结尾，记录集的 (`IsBOF`或`IsEOF`返回非零值)，调用`Move`引发`CDaoException`。  
  
> [!NOTE]
>  如果你调用任意`Move`函数时当前记录更新或添加，更新都将丢失而不发出警告。  
  
 当您调用`Move`对只进滚动快照， *lRows*参数必须是一个正整数，并且不允许书签，因此你才能向前移动仅。  
  
 若要使第一个，最后下, 一步，或上一个记录集中的记录当前的记录，调用`MoveFirst`， `MoveLast`， `MoveNext`，或`MovePrev`成员函数。  
  
 有关相关信息，请参阅主题的"移动方法"和"MoveFirst、 MoveLast、 MoveNext、 MovePrevious 方法"DAO 帮助中。  
  
##  <a name="movefirst"></a>  CDaoRecordset::MoveFirst  
 调用此成员函数要第一条记录中的记录集 （如果有） 的当前记录。  
  
```  
void MoveFirst();
```  
  
### <a name="remarks"></a>备注  
 无需调用`MoveFirst`立即打开记录集后。 此时，第一条记录 （如果有） 将自动当前记录。  
  
> [!CAUTION]
>  调用的任何`Move`函数将引发异常，如果记录集不具有任何记录。 一般情况下，请同时调用`IsBOF`和`IsEOF`移动操作，以确定是否记录集的任何记录之前。 调用后`Open`或`Requery`，调用`IsBOF`或`IsEOF`。  
  
> [!NOTE]
>  如果你调用任意`Move`函数时当前记录更新或添加，更新都将丢失而不发出警告。  
  
 使用`Move`函数移动而无需应用条件的记录。 使用查找操作的动态集类型或满足特定条件的快照类型的记录集对象中查找记录。 若要找到类型一个表的记录集对象中的一条记录，请调用`Seek`。  
  
 如果记录集所引用的表类型的记录集，则移动遵循表的当前索引。 可以通过使用基础的 DAO 对象的索引属性设置的当前索引。 如果未设置当前索引，返回的记录的顺序未定义。  
  
 如果调用`MoveLast`上基于 SQL 查询或 querydef 的记录集对象，该查询强制完成和记录集对象已完全填充。  
  
 不能调用`MoveFirst`或`MovePrev`成员函数和只进的滚动快照。  
  
 若要移动条记录向前或向后的特定记录集对象中记录当前的位置，请调用`Move`。  
  
 有关相关信息，请参阅主题的"移动方法"和"MoveFirst、 MoveLast、 MoveNext、 MovePrevious 方法"DAO 帮助中。  
  
##  <a name="movelast"></a>  CDaoRecordset::MoveLast  
 在记录集的当前记录中调用此成员函数以进行最后一条记录 （如果有）。  
  
```  
void MoveLast();
```  
  
### <a name="remarks"></a>备注  
  
> [!CAUTION]
>  调用的任何`Move`函数将引发异常，如果记录集不具有任何记录。 一般情况下，请同时调用`IsBOF`和`IsEOF`移动操作，以确定是否记录集的任何记录之前。 调用后`Open`或`Requery`，调用`IsBOF`或`IsEOF`。  
  
> [!NOTE]
>  如果你调用任意`Move`函数时当前记录更新或添加，更新都将丢失而不发出警告。  
  
 使用`Move`函数移动而无需应用条件的记录。 使用查找操作的动态集类型或满足特定条件的快照类型的记录集对象中查找记录。 若要找到类型一个表的记录集对象中的一条记录，请调用`Seek`。  
  
 如果记录集所引用的表类型的记录集，则移动遵循表的当前索引。 可以通过使用基础的 DAO 对象的索引属性设置的当前索引。 如果未设置当前索引，返回的记录的顺序未定义。  
  
 如果调用`MoveLast`上基于 SQL 查询或 querydef 的记录集对象，该查询强制完成和记录集对象已完全填充。  
  
 若要移动条记录向前或向后的特定记录集对象中记录当前的位置，请调用`Move`。  
  
 有关相关信息，请参阅主题的"移动方法"和"MoveFirst、 MoveLast、 MoveNext、 MovePrevious 方法"DAO 帮助中。  
  
##  <a name="movenext"></a>  CDaoRecordset::MoveNext  
 调用此成员函数要记录集的当前记录中的下一条记录。  
  
```  
void MoveNext();
```  
  
### <a name="remarks"></a>备注  
 建议您调用`IsBOF`尝试移动到上一条记录之前。 调用`MovePrev`将引发`CDaoException`如果`IsBOF`返回非零值，指示已滚动过之前的第一个记录或任何记录了所选的记录集。  
  
> [!CAUTION]
>  调用的任何`Move`函数将引发异常，如果记录集不具有任何记录。 一般情况下，请同时调用`IsBOF`和`IsEOF`移动操作，以确定是否记录集的任何记录之前。 调用后`Open`或`Requery`，调用`IsBOF`或`IsEOF`。  
  
> [!NOTE]
>  如果你调用任意`Move`函数时当前记录更新或添加，更新都将丢失而不发出警告。  
  
 使用`Move`函数移动而无需应用条件的记录。 使用查找操作的动态集类型或满足特定条件的快照类型的记录集对象中查找记录。 若要找到类型一个表的记录集对象中的一条记录，请调用`Seek`。  
  
 如果记录集所引用的表类型的记录集，则移动遵循表的当前索引。 可以通过使用基础的 DAO 对象的索引属性设置的当前索引。 如果未设置当前索引，返回的记录的顺序未定义。  
  
 若要移动条记录向前或向后的特定记录集对象中记录当前的位置，请调用`Move`。  
  
 有关相关信息，请参阅主题的"移动方法"和"MoveFirst、 MoveLast、 MoveNext、 MovePrevious 方法"DAO 帮助中。  
  
##  <a name="moveprev"></a>  CDaoRecordset::MovePrev  
 调用此成员函数以使前一条记录中记录集的当前记录。  
  
```  
void MovePrev();
```  
  
### <a name="remarks"></a>备注  
 建议您调用`IsBOF`尝试移动到上一条记录之前。 调用`MovePrev`将引发`CDaoException`如果`IsBOF`返回非零值，指示已滚动过之前的第一个记录或任何记录了所选的记录集。  
  
> [!CAUTION]
>  调用的任何`Move`函数将引发异常，如果记录集不具有任何记录。 一般情况下，请同时调用`IsBOF`和`IsEOF`移动操作，以确定是否记录集的任何记录之前。 调用后`Open`或`Requery`，调用`IsBOF`或`IsEOF`。  
  
> [!NOTE]
>  如果你调用任意`Move`函数时当前记录更新或添加，更新都将丢失而不发出警告。  
  
 使用`Move`函数移动而无需应用条件的记录。 使用查找操作的动态集类型或满足特定条件的快照类型的记录集对象中查找记录。 若要找到类型一个表的记录集对象中的一条记录，请调用`Seek`。  
  
 如果记录集所引用的表类型的记录集，则移动遵循表的当前索引。 可以通过使用基础的 DAO 对象的索引属性设置的当前索引。 如果未设置当前索引，返回的记录的顺序未定义。  
  
 不能调用`MoveFirst`或`MovePrev`成员函数和只进的滚动快照。  
  
 若要移动条记录向前或向后的特定记录集对象中记录当前的位置，请调用`Move`。  
  
 有关相关信息，请参阅主题的"移动方法"和"MoveFirst、 MoveLast、 MoveNext、 MovePrevious 方法"DAO 帮助中。  
  
##  <a name="open"></a>  Cdaorecordset:: Open  
 必须调用此成员函数以检索记录集的记录。  
  
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
 *nOpenType*  
 以下值之一：  
  
- `dbOpenDynaset` 具有双向滚动的动态集类型记录集。 这是默认设置。  
  
- `dbOpenTable` 与双向滚动表类型的记录集。  
  
- `dbOpenSnapshot` 与双向滚动快照类型的记录集。  
  
 *lpszSQL*  
 字符串指针，其中包含以下项之一：  
  
-   NULL 指针。  
  
-   一个或多个 tabledefs 和/或 querydefs （逗号分隔） 的名称。  
  
-   SQL**选择**语句 (根据需要使用 SQL**其中**或**ORDERBY**子句)。  
  
-   传递查询。  
  
 *nOptions*  
 一个或多个下面列出的选项。 默认值为 0。 可能的值如下：  
  
- `dbAppendOnly` 您只能追加新记录 （仅记录于动态集类型集）。 此选项的字面意思，可能仅追加记录。 MFC ODBC 数据库类具有一个允许检索和追加的记录的仅限追加的选项。  
  
- `dbForwardOnly` 记录集是只进的滚动快照。  
  
- `dbSeeChanges` 如果另一个用户正在更改正在编辑的数据，生成一个异常。  
  
- `dbDenyWrite` 其他用户不能修改或添加记录。  
  
- `dbDenyRead` 其他用户无法查看记录 （仅类型一个表的记录集）。  
  
- `dbReadOnly` 你可以仅查看记录;其他用户可以修改它们。  
  
- `dbInconsistent` 允许不一致的更新 （仅记录于动态集类型集）。  
  
- `dbConsistent` 允许仅一致的更新 （仅记录于动态集类型集）。  
  
> [!NOTE]
>  常量`dbConsistent`和`dbInconsistent`互相排斥。 可以使用一个或另一个，但不是能同时中的给定实例`Open`。  
  
 *pTableDef*  
 一个指向[CDaoTableDef](../../mfc/reference/cdaotabledef-class.md)对象。 此版本是仅对类型一个表的记录集有效。 使用此选项时`CDaoDatabase`指针，用于构造`CDaoRecordset`未使用; 而是使用 tabledef 所驻留的数据库。  
  
 *pQueryDef*  
 一个指向[CDaoQueryDef](../../mfc/reference/cdaoquerydef-class.md)对象。 此版本仅适用于动态集类型和快照类型的记录集无效。 使用此选项时`CDaoDatabase`指针，用于构造`CDaoRecordset`未使用; 而是使用 querydef 所驻留的数据库。  
  
### <a name="remarks"></a>备注  
 然后再调用`Open`，必须构造记录集对象。 有若干方法可实现此操作：  
  
-   在构造记录集对象时，传递一个指向`CDaoDatabase`已打开的对象。  
  
-   在构造记录集对象时，传递一个指向`CDaoDatabase`未打开的对象。 记录集打开`CDaoDatabase`对象，但不是会关闭它，记录集对象关闭时。  
  
-   在构造记录集对象时，传递一个 NULL 指针。 记录集对象调用`GetDefaultDBName`获取 Microsoft Access 的名称。要打开的 MDB 文件。 记录集然后打开`CDaoDatabase`对象并保留其打开，只要该记录集处于打开状态。 当您调用`Close`记录集，`CDaoDatabase`对象也将关闭。  
  
    > [!NOTE]
    >  记录集打开时`CDaoDatabase`对象，它打开数据源具有非独占访问权限。  
  
 新版`Open`，它使用*lpszSQL*参数，该记录集处于打开状态后可以检索以下几种方式中的记录。 第一个选项是具有 DFX 函数在`DoFieldExchange`。 第二个选项是使用动态绑定通过调用`GetFieldValue`成员函数。 可以单独或组合中实现这些选项。 如果结合使用，必须将传递在 SQL 语句中自行调用`Open`。  
  
 当你使用的第二个版本`Open`您传入`CDaoTableDef`对象，生成的列将可供您通过将绑定`DoFieldExchange`和 DFX 机制，和/或通过动态绑定`GetFieldValue`。  
  
> [!NOTE]
>  您只能调用`Open`使用`CDaoTableDef`类型一个表的记录集的对象。  
  
 当你使用的第三个版本`Open`您传入`CDaoQueryDef`对象，将执行查询，并将可供你通过将绑定生成的列`DoFieldExchange`和 DFX 机制，和/或通过动态绑定`GetFieldValue`。  
  
> [!NOTE]
>  您只能调用`Open`使用`CDaoQueryDef`动态集类型和快照类型的记录集对象。  
  
 第一个版本的`Open`，它使用`lpszSQL`参数，记录的所选基于的条件下表中所示。  
  
|`lpszSQL` 参数的值|取决于选择的记录|示例|  
|--------------------------------------|----------------------------------------|-------------|  
|NULL|返回的字符串`GetDefaultSQL`。||  
|以逗号分隔的一个或多个 tabledefs 和/或 querydef 名称列表。|所有列中都表示`DoFieldExchange`。|`"Customer"`|  
|**选择**列列表**FROM**表列表|从指定的 tabledef(s) 和/或 querydef(s) 指定的列。|`"SELECT CustId, CustName`<br /><br /> `FROM Customer"`|  
  
 常规步骤是将传递到 NULL `Open`; 在这种情况下，`Open`调用`GetDefaultSQL`，ClassWizard 生成时创建的可重写成员函数`CDaoRecordset`-派生的类。 此值使类向导中指定 tabledef(s) 和/或 querydef 名称。 您可以指定中的其他信息*lpszSQL*参数。  
  
 您传递的任何`Open`构造查询的最终 SQL 字符串 (字符串可能具有 SQL**其中**并**ORDERBY**子句追加到*lpszSQL*字符串您传递），然后执行查询。 可以通过调用检查构造的字符串`GetSQL`后调用`Open`。  
  
 记录集类的字段数据成员绑定到所选的数据的列。 如果未返回任何记录，第一条记录将成为当前记录。  
  
 如果想要设置的记录集，如筛选或排序，选项设置`m_strSort`或`m_strFilter`构造的记录集对象之后但在调用之前`Open`。 如果你想要刷新后记录集中记录的记录集已打开，请调用`Requery`。  
  
 如果您调用`Open`上的动态集类型或快照类型的记录集中，或者如果数据源引用的 SQL 语句或 tabledef 对象，表示附加的表，则不能使用`dbOpenTable`类型参数; 如果这样做，则 MFC 会引发异常。 若要确定 tabledef 对象是否表示一个附加的表，创建[CDaoTableDef](../../mfc/reference/cdaotabledef-class.md)对象，并调用其[GetConnect](../../mfc/reference/cdaotabledef-class.md#getconnect)成员函数。  
  
 使用`dbSeeChanges`标志，如果你想要捕获编辑或删除同一记录时，由另一个用户或计算机上的另一个程序所做的更改。 例如，如果两个用户开始编辑同一个记录，若要调用的第一个用户`Update`成员函数运行成功。 当`Update`由第二个用户，调用`CDaoException`引发。 同样，如果第二个用户尝试调用`Delete`若要删除的记录，以及它已改变的第一个用户，通过`CDaoException`时发生。  
  
 通常情况下，如果用户获取此`CDaoException`更新时，你的代码应刷新字段的内容并检索新修改的值。 如果删除的过程中发生异常，你的代码无法对用户和一条消息指出数据最近更改了显示新的记录数据。 此时，你的代码可以请求用户仍想要删除的记录一条确认消息。  
  
> [!TIP]
>  使用只进滚动选项 (`dbForwardOnly`) 以提高性能，当你的应用程序发出一个记录集一次传递时打开从 ODBC 数据源。  
  
 有关相关信息，请参阅主题 DAO 帮助中的"OpenRecordset 方法"。  
  
##  <a name="requery"></a>  CDaoRecordset::Requery  
 调用此成员函数以重新生成 （刷新） 记录集。  
  
```  
virtual void Requery();
```  
  
### <a name="remarks"></a>备注  
 如果未返回任何记录，第一条记录将成为当前记录。  
  
 为了使该记录集，以反映添加和删除操作，您或其他用户对数据源，必须重新记录集生成通过调用`Requery`。 如果记录集是动态集，它会自动反映您或其他用户对其现有的记录 （但不是添加件） 进行的更新。 如果记录集是快照，则必须调用`Requery`以反映由其他用户，以及添加和删除操作的编辑。  
  
 对于动态集或快照中，调用`Requery`任何时候你想要重新生成使用的参数值的记录集。 通过设置来设置新的筛选器或排序[m_strFilter](#m_strfilter)并[m_strSort](#m_strsort)之前调用`Requery`。 通过将新值分配给之前调用的参数数据成员设置新的参数`Requery`。  
  
 如果重新生成该记录集的尝试失败，则关闭记录集。 在调用之前`Requery`，可以确定记录集是否可以通过调用重新查询[CanRestart](#canrestart)成员函数。 `CanRestart` 并不保证`Requery`将会成功。  
  
> [!CAUTION]
>  调用`Requery`之后调用仅`Open`。  
  
> [!NOTE]
>  调用[再次查询](#requery)更改 DAO 书签。  
  
 不能调用`Requery`上的动态集类型或快照类型记录集，如果调用`CanRestart`返回 0，也不可以使用它在类型一个表的记录集上。  
  
 如果这两个`IsBOF`并`IsEOF`调用后返回非零值`Requery`，查询未返回任何记录和记录集将包含任何数据。  
  
 有关相关信息，请参阅主题 DAO 帮助中的"再次查询方法"。  
  
##  <a name="seek"></a>  CDaoRecordset::Seek  
 调用此成员函数以满足指定的条件的当前索引，并确保记录当前记录的索引的表类型记录集对象中找到的记录。  
  
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
 *lpszComparison*  
 以下字符串表达式之一:"<"、"\<="，"="、"> ="，或">"。  
  
 *pKey1*  
 一个指向[COleVariant](../../mfc/reference/colevariant-class.md)其值对应于在索引中的第一个字段。 必须的。  
  
 *pKey2*  
 一个指向`COleVariant`其值对应于第二个字段在索引中，如果有的话。 默认值为 NULL。  
  
 *pKey3*  
 一个指向`COleVariant`其值对应于第三个字段在索引中，如果有的话。 默认值为 NULL。  
  
 *pKeyArray*  
 指向 variant 数组的指针。 数组大小对应于索引中的字段数。  
  
 *nKeys*  
 对应于数组，它是在索引中的字段数的大小的整数。  
  
> [!NOTE]
>  不要在键中指定通配符。 通配符将导致`Seek`返回没有匹配的记录。  
  
### <a name="return-value"></a>返回值  
 如果找到匹配的记录，否则为 0，非零值。  
  
### <a name="remarks"></a>备注  
 使用第二个 （数组） 版本的`Seek`来处理或更多的四个字段的索引。  
  
 `Seek` 启用搜索的表类型的记录集上的高性能索引。 必须通过调用设置的当前索引`SetCurrentIndex`之前调用`Seek`。 如果索引标识的非唯一的键字段或字段，`Seek`找到满足条件的第一个记录。 如果未设置索引，将引发异常。  
  
 请注意，如果不创建 UNICODE 记录集，则`COleVariant`对象必须显式声明为 ANSI。 这可以通过使用[COleVariant::COleVariant](../../mfc/reference/colevariant-class.md#colevariant)**(** *lpszSrc *** *vtSrc* **)** 构造函数使用的窗体*vtSrc*设置为`VT_BSTRT`(ANSI) 或通过使用`COleVariant`函数[SetString](../../mfc/reference/colevariant-class.md#setstring)**(** *lpszSrc * * *，** *vtSrc* **)** 与*vtSrc*设置为`VT_BSTRT`。  
  
 当您调用`Seek`，则传递一个或多个密钥值和比较运算符 ("<"、"\<="，"="、"> ="，或">")。 `Seek` 搜索指定的键字段，并查找满足指定条件的第一个记录*lpszComparison*并*pKey1*。 找到后，`Seek`返回非零值，并将该记录当前。 如果`Seek`无法找到匹配项，`Seek`返回零，并且当前记录是未定义。 当直接使用 DAO，则必须显示检查 NoMatch 属性。  
  
 如果`lpszComparison`为"=""> ="，或">"，`Seek`开头开始的索引。 如果*lpszComparison*是"<"或"< ="，`Seek`索引的结尾处开始，并向后搜索，除非结尾处有重复的索引条目。 在这种情况下，`Seek`从索引结束时重复的索引条目中的任意项开始。  
  
 那里没有使用时为当前记录`Seek`。  
  
 若要找到一条记录中的动态集类型或快照类型满足特定条件的记录集，请使用查找操作。 若要包含的所有记录，而不仅仅是那些满足特定条件，用于移动操作记录之间移动。  
  
 不能调用`Seek`上的任何附加表类型，因为必须作为动态集类型或快照类型的记录集打开附加的表。 但是，如果您调用`CDaoDatabase::Open`若要直接打开可安装 ISAM 数据库，可以调用`Seek`表在该数据库中，尽管性能可能会降低。  
  
 有关相关信息，请参阅主题 DAO 帮助中的"查找方法"。  
  
##  <a name="setabsoluteposition"></a>  CDaoRecordset::SetAbsolutePosition  
 设置记录集对象的当前记录的相对记录数。  
  
```  
void SetAbsolutePosition(long lPosition);
```  
  
### <a name="parameters"></a>参数  
 *lPosition*  
 对应于当前记录的记录集中的序号位置。  
  
### <a name="remarks"></a>备注  
 调用`SetAbsolutePosition`，可将当前记录指针定位到特定的记录根据其序号位置中的动态集类型或快照类型的记录集。 您还可以通过调用来确定当前记录数[GetAbsolutePosition](#getabsoluteposition)。  
  
> [!NOTE]
>  此成员函数仅适用于动态集类型和快照类型的记录集无效。  
  
 AbsolutePosition 属性值的基础的 DAO 对象是从零开始;设置为 0 是指在记录集中的第一个记录。 设置一个值大于填充的记录原因 MFC 引发异常数。 可以通过调用确定记录集填充记录数`GetRecordCount`成员函数。  
  
 如果删除当前记录，则不定义 AbsolutePosition 属性值，并且 MFC 会引发异常，如果它引用。 新记录添加到序列的末尾。  
  
> [!NOTE]
>  此属性不是要用作代理记录编号。 仍建议采用书签保留和返回到给定位置，而且这是在所有类型的记录集对象支持书签定位当前记录的唯一方法。 具体而言，给定的记录的位置发生更改时将删除其前面的记录。 此外，还有，如果重新因为除非创建与 SQL 语句中使用，否则不能保证在记录集内的单个记录的顺序重新创建记录集，给定的记录将具有相同的绝对位置不能保证**ORDERBY**子句。  
  
 有关相关信息，请参阅主题 DAO 帮助中的"AbsolutePosition 属性"。  
  
##  <a name="setbookmark"></a>  CDaoRecordset::SetBookmark  
 调用此成员函数来定位上包含指定的书签记录的记录集。  
  
```  
void SetBookmark(COleVariant varBookmark);
```  
  
### <a name="parameters"></a>参数  
 *varBookmark*  
 一个[COleVariant](../../mfc/reference/colevariant-class.md)对象，其中包含特定记录的书签值。  
  
### <a name="remarks"></a>备注  
 当创建或打开记录集对象时，它的记录的每个已具有一个唯一的书签。 可以通过调用来检索当前记录的书签将变为`GetBookmark`并保存到值`COleVariant`对象。 你可以稍后返回到该记录通过调用`SetBookmark`使用已保存的书签值。  
  
> [!NOTE]
>  调用[再次查询](#requery)更改 DAO 书签。  
  
 请注意，如果不创建 UNICODE 记录集，则`COleVariant`对象必须显式声明为 ANSI。 这可以通过使用[COleVariant::COleVariant](../../mfc/reference/colevariant-class.md#colevariant)**(** *lpszSrc *** *vtSrc* **)** 构造函数使用的窗体*vtSrc*设置为`VT_BSTRT`(ANSI) 或通过使用`COleVariant`函数[SetString](../../mfc/reference/colevariant-class.md#setstring)**(** *lpszSrc * * *，** *vtSrc* **)** 与*vtSrc*设置为`VT_BSTRT`。  
  
 有关相关信息，请参阅"书签属性"和可存为书签属性的主题"DAO 帮助中。  
  
##  <a name="setcachesize"></a>  CDaoRecordset::SetCacheSize  
 调用此成员函数可设置要缓存的记录数。  
  
```  
void SetCacheSize(long lSize);
```  
  
### <a name="parameters"></a>参数  
 *lSize*  
 指定记录的数。 典型值为 100。 设置为 0 会关闭缓存。 该设置必须介于 5 和 1200年记录之间。 缓存可能会使用相当多的内存。  
  
### <a name="remarks"></a>备注  
 缓存是在包含最新的事件中运行应用程序时将再次请求数据从服务器检索的数据的本地内存中的空间。 数据缓存提高了从远程服务器通过动态集类型的记录集对象中检索数据的应用程序的性能。 请求数据，Microsoft Jet 数据库引擎为所请求的数据会首先检查缓存而不是从花费的时间的服务器中检索它。 不是来自 ODBC 数据源的数据不保存在缓存中。  
  
 任何 ODBC 数据源，如附加表，可以本地缓存。 若要创建缓存，请打开记录集对象从远程数据源，调用`SetCacheSize`并`SetCacheStart`成员函数，然后调用`FillCache`成员函数或逐步执行记录通过使用其中一个移动操作。 *LSize*参数的`SetCacheSize`成员函数可以基于你的应用程序可以使用一次的记录数。 例如，如果您使用记录集作为数据源要显示在屏幕上，您可以传递`SetCacheSize` *lSize*参数作为 20 来一次显示 20 条记录。  
  
 相关信息，请参阅 DAO 帮助中的主题"CacheSize，CacheStart 属性"。  
  
##  <a name="setcachestart"></a>  CDaoRecordset::SetCacheStart  
 调用此成员函数以在记录集缓存中指定的第一条记录的书签。  
  
```  
void SetCacheStart(COleVariant varBookmark);
```  
  
### <a name="parameters"></a>参数  
 *varBookmark*  
 一个[COleVariant](../../mfc/reference/colevariant-class.md) ，它指定记录集缓存中的第一条记录的书签。  
  
### <a name="remarks"></a>备注  
 可以使用任何记录的书签值*varBookmark*参数的`SetCacheStart`成员函数。 请的记录你想要与当前记录开始缓存，建立使用该记录的书签[SetBookmark](#setbookmark)，并将书签值作为参数传递`SetCacheStart`成员函数。  
  
 Microsoft Jet 数据库引擎从缓存中请求缓存范围内的记录并从服务器请求到缓存范围外的记录。  
  
 从缓存中检索的记录不反映对源数据同时进行的其他用户的更改。  
  
 若要强制更新所有缓存数据，请将传递*lSize*的参数`SetCacheSize`为 0 时，调用`SetCacheSize`再次缓存的大小与你最初请求，，然后调用`FillCache`成员函数。  
  
 请注意，如果不创建 UNICODE 记录集，则`COleVariant`对象必须显式声明为 ANSI。 这可以通过使用[COleVariant::COleVariant](../../mfc/reference/colevariant-class.md#colevariant)**(** *lpszSrc *** *vtSrc* **)** 构造函数使用的窗体*vtSrc*设置为`VT_BSTRT`(ANSI) 或通过使用`COleVariant`函数[SetString](../../mfc/reference/colevariant-class.md#setstring)**(** *lpszSrc * * *，** *vtSrc* **)** 与*vtSrc*设置为`VT_BSTRT`。  
  
 有关相关信息，请参阅主题 CacheSize，CacheStart 属性 DAO 帮助中。  
  
##  <a name="setcurrentindex"></a>  CDaoRecordset::SetCurrentIndex  
 调用此成员函数以类型一个表的记录集上设置索引。  
  
```  
void SetCurrentIndex(LPCTSTR lpszIndex);
```  
  
### <a name="parameters"></a>参数  
 *lpszIndex*  
 一个指针，其中包含要设置的索引的名称。  
  
### <a name="remarks"></a>备注  
 基表中的记录不按任何特定顺序存储。 设置索引会更改为从数据库中返回的记录的顺序，但它不会影响的记录存储的顺序。 必须已定义的指定的索引。 如果你尝试使用不存在的索引对象，或在调用时未设置索引[Seek](#seek)，MFC 将引发异常。  
  
 可以通过调用创建新表的索引[CDaoTableDef::CreateIndex](../../mfc/reference/cdaotabledef-class.md#createindex)并通过调用追加到基础 tabledef 的索引集合的新索引[CDaoTableDef::Append](../../mfc/reference/cdaotabledef-class.md#append)，和然后重新打开记录集。  
  
 可以仅按索引为基础 tabledef 定义排序类型一个表的记录集从返回的记录。 若要对其他顺序中的记录进行排序，可以打开的动态集类型或使用 SQL 快照类型记录集**ORDERBY**子句存储在[CDaoRecordset::m_strSort](#m_strsort)。  
  
 有关相关信息，请参阅主题"索引对象"和"当前索引"DAO 帮助中的定义。  
  
##  <a name="setfielddirty"></a>  CDaoRecordset::SetFieldDirty  
 调用此成员函数可标记为已更改或为不变的记录集的字段数据成员。  
  
```  
void SetFieldDirty(
    void* pv,  
    BOOL bDirty = TRUE);
```  
  
### <a name="parameters"></a>参数  
 *pv*  
 包含中的记录集或为 NULL 的字段数据成员的地址。 如果为 NULL，将标记为记录集中的所有字段数据成员。 (C + + NULL 不是 Null 相同数据库术语中，这意味着"无任何值。")  
  
 *bDirty*  
 如果字段数据成员是被标记为"更新"（更改），则为 TRUE。 如果字段数据成员将会被标记为"清理"（未更改）; 否则为 FALSE。  
  
### <a name="remarks"></a>备注  
 将标记为未更改的字段可确保该字段不会更新。  
  
 Framework 标记更改字段数据成员，以确保它们将写入到数据源上的记录的 DAO 记录字段交换 (DFX) 机制。 将更改字段的值通常字段已更新会自动设置，因此很少需要调用`SetFieldDirty`自己，但您有时可能想要确保，列将显式更新或插入而不考虑哪些值是字段数据成员。 DFX 机制还采用 PSEUDONULL 使用。 有关详细信息，请参阅[CDaoFieldExchange::m_nOperation](../../mfc/reference/cdaofieldexchange-class.md#m_noperation)。  
  
 如果未使用双缓冲机制，然后更改字段的值不会不会自动将字段设置为脏。 在这种情况下，将需要显式将字段设置为脏。 中包含的标志[m_bCheckCacheForDirtyFields](#m_bcheckcachefordirtyfields)控制此自动字段检查。  
  
> [!NOTE]
>  调用此成员函数才具有名为[编辑](#edit)或[AddNew](#addnew)。  
  
 该函数的第一个参数将该函数应用于所有使用 NULL`outputColumn`字段，不**param**中的字段`CDaoFieldExchange`。 例如，调用  
  
 [!code-cpp[NVC_MFCDatabase#6](../../mfc/codesnippet/cpp/cdaorecordset-class_6.cpp)]  
  
 将仅设置`outputColumn`字段为 NULL;**param**字段不会受影响。  
  
 若要在运行**param**，必须提供个人的实际地址**param**你想要如：  
  
 [!code-cpp[NVC_MFCDatabase#7](../../mfc/codesnippet/cpp/cdaorecordset-class_7.cpp)]  
  
 这意味着您不能设置所有**param**字段为 NULL，如处理`outputColumn`字段。  
  
 `SetFieldDirty` 通过实现`DoFieldExchange`。  
  
##  <a name="setfieldnull"></a>  CDaoRecordset::SetFieldNull  
 调用此成员函数可标记为 Null （特别具有任何值） 或非 null 值的记录集的字段数据成员。  
  
```  
void SetFieldNull(
    void* pv,  
    BOOL bNull = TRUE);
```  
  
### <a name="parameters"></a>参数  
 *pv*  
 包含中的记录集或为 NULL 的字段数据成员的地址。 如果为 NULL，将标记为记录集中的所有字段数据成员。 (C + + NULL 不是 Null 相同数据库术语中，这意味着"无任何值。")  
  
 *bNull*  
 如果字段数据成员是被标记为不具有任何值 (Null)，非零值。 否则为 0 的字段数据成员是否被标记为非 Null。  
  
### <a name="remarks"></a>备注  
 `SetFieldNull` 用于绑定中的字段`DoFieldExchange`机制。  
  
 当你将一条新记录添加到记录集时，所有字段数据成员是最初设置为 Null 值和标记为"更新"（更改）。 当从数据源检索一条记录时，其列已具有的值或均为 Null。 如果不是适当的时候字段为 Null， [CDaoException](../../mfc/reference/cdaoexception-class.md)引发。  
  
 如果使用的双缓冲机制，例如，如果您特别希望将当前记录的字段指定为不具有一个值，调用`SetFieldNull`与*bNull*设置为 TRUE 以标记为 Null。 如果以前标记的字段为 Null，并且现在想要为其提供一个值，只需设置它的新值。 无需删除具有 Null 标志`SetFieldNull`。 若要确定是否允许该字段为 Null，请调用[IsFieldNullable](#isfieldnullable)。  
  
 如果不使用双缓冲机制，然后更改字段的值不会不会自动将字段设置为脏和非 Null。 已更新和非 Null，必须专门设置字段。 中包含的标志[m_bCheckCacheForDirtyFields](#m_bcheckcachefordirtyfields)控制此自动字段检查。  
  
 DFX 机制采用 PSEUDONULL 使用。 有关详细信息，请参阅[CDaoFieldExchange::m_nOperation](../../mfc/reference/cdaofieldexchange-class.md#m_noperation)。  
  
> [!NOTE]
>  调用此成员函数才具有名为[编辑](#edit)或[AddNew](#addnew)。  
  
 该函数的第一个参数将该函数仅适用于使用 NULL`outputColumn`字段，不**param**中的字段`CDaoFieldExchange`。 例如，调用  
  
 [!code-cpp[NVC_MFCDatabase#8](../../mfc/codesnippet/cpp/cdaorecordset-class_8.cpp)]  
  
 将仅设置`outputColumn`字段为 NULL;**param**字段不会受影响。  
  
##  <a name="setfieldvalue"></a>  CDaoRecordset::SetFieldValue  
 调用此成员函数按序号位置或更改字符串的值设置字段的值。  
  
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
 *lpszName*  
 指向包含的字段名称的字符串的指针。  
  
 *varValue*  
 对引用[COleVariant](../../mfc/reference/colevariant-class.md)对象，其中包含字段的内容的值。  
  
 *nIndex*  
 一个整数，表示字段的记录集的字段集合 （从零开始） 中的序号位置。  
  
 *lpszValue*  
 指向包含该字段的内容的值的字符串的指针。  
  
### <a name="remarks"></a>备注  
 使用`SetFieldValue`并[GetFieldValue](#getfieldvalue)若要动态绑定在运行的时而不是以静态方式使用绑定列的字段[DoFieldExchange](#dofieldexchange)机制。  
  
 请注意，是否不创建 UNICODE 记录集，你必须使用的窗体`SetFieldValue`不包含`COleVariant`参数，或`COleVariant`对象必须显式声明为 ANSI。 这可以通过使用[COleVariant::COleVariant](../../mfc/reference/colevariant-class.md#colevariant)**(** *lpszSrc *** *vtSrc* **)** 构造函数使用的窗体*vtSrc*设置为`VT_BSTRT`(ANSI) 或通过使用`COleVariant`函数[SetString](../../mfc/reference/colevariant-class.md#setstring)**(** *lpszSrc * * *，** *vtSrc* **)** 与*vtSrc*设置为`VT_BSTRT`。  
  
 有关相关信息，请参阅主题"字段对象"和 DAO 帮助中的"值属性"。  
  
##  <a name="setfieldvaluenull"></a>  CDaoRecordset::SetFieldValueNull  
 调用此成员函数可将字段设置为 Null 值。  
  
```  
void SetFieldValueNull(int nIndex);  
void SetFieldValueNull(LPCTSTR lpszName);
```  
  
### <a name="parameters"></a>参数  
 *nIndex*  
 集中的记录，以便按从零开始的索引的查找字段的索引。  
  
 *lpszName*  
 按名称查找该记录集中的字段名称。  
  
### <a name="remarks"></a>备注  
 C + + NULL 不是 Null，这意味着，在数据库术语中，相同"具有任何值。"  
  
 有关相关信息，请参阅主题"字段对象"和 DAO 帮助中的"值属性"。  
  
##  <a name="setlockingmode"></a>  CDaoRecordset::SetLockingMode  
 调用此成员函数可设置的锁定记录集的类型。  
  
```  
void SetLockingMode(BOOL bPessimistic);
```  
  
### <a name="parameters"></a>参数  
 *bPessimistic*  
 一个标志，指示锁定的类型。  
  
### <a name="remarks"></a>备注  
 只要您调用保守式锁定时有效时，包含要编辑的记录的 2 千页锁定`Edit`成员函数。 在调用时，页处于未锁定`Update`或`Close`成员函数或任何移动或查找操作。  
  
 乐观锁定实际上是包含记录的 2 千页被锁定，仅在使用更新记录时`Update`成员函数。  
  
 如果页处于锁定状态，没有其他用户可以编辑同一页面上的记录。 如果您调用`SetLockingMode`并传递一个非零值和另一个用户已锁定的页，在调用时引发异常`Edit`。 其他用户可以从锁定的页读取数据。  
  
 如果您调用`SetLockingMode`具有零值及更高版本调用`Update`而另一个用户被锁定的页，则会发生异常。 若要查看其他用户到你的记录所做的更改 （并放弃所做的更改），调用`SetBookmark`书签值为当前记录的成员函数。  
  
 在使用 ODBC 数据源，始终是乐观锁定模式。  
  
##  <a name="setparamvalue"></a>  CDaoRecordset::SetParamValue  
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
 *nIndex*  
 Querydef 的参数集合中参数的数字位置。  
  
 *var*  
 要设置; 的值请参阅备注。  
  
 *lpszName*  
 参数要设置其值的名称。  
  
### <a name="remarks"></a>备注  
 该参数必须已建立作为记录集的 SQL 字符串的一部分。 按名称或在集合中的索引位置，可以访问该参数。  
  
 指定要设置为值`COleVariant`对象。 了解如何设置所需的值并键入你`COleVariant`对象，请参阅类[COleVariant](../../mfc/reference/colevariant-class.md)。 请注意，如果不创建 UNICODE 记录集，则`COleVariant`对象必须显式声明为 ANSI。 这可以通过使用[COleVariant::COleVariant](../../mfc/reference/colevariant-class.md#colevariant)**(** *lpszSrc *** *vtSrc* **)** 构造函数使用的窗体*vtSrc*设置为`VT_BSTRT`(ANSI) 或通过使用`COleVariant`函数[SetString](../../mfc/reference/colevariant-class.md#setstring)**(** *lpszSrc * * *，** *vtSrc* **)** 与*vtSrc*设置为`VT_BSTRT`。  
  
##  <a name="setparamvaluenull"></a>  CDaoRecordset::SetParamValueNull  
 调用此成员函数以将参数设置为 Null 值。  
  
```  
void SetParamValueNull(int nIndex);  
void SetParamValueNull(LPCTSTR lpszName);
```  
  
### <a name="parameters"></a>参数  
 *nIndex*  
 集中的记录，以便按从零开始的索引的查找字段的索引。  
  
 *lpszName*  
 按名称查找该记录集中的字段名称。  
  
### <a name="remarks"></a>备注  
 C + + NULL 不是 Null，这意味着，在数据库术语中，相同"具有任何值。"  
  
##  <a name="setpercentposition"></a>  CDaoRecordset::SetPercentPosition  
 调用此成员函数可设置一个值，更改基于百分比的记录集中记录的记录集对象中的当前记录的近似位置。  
  
```  
void SetPercentPosition(float fPosition);
```  
  
### <a name="parameters"></a>参数  
 *fPosition*  
 一个介于 0 和 100 之间的数字。  
  
### <a name="remarks"></a>备注  
 通过移动到最后一个记录，然后再调用时使用的动态集类型或快照类型的记录集，首先填充记录集`SetPercentPosition`。 如果您调用`SetPercentPosition`完全填充记录集时之前, 的移动量是相对于访问的值所示的记录数目[GetRecordCount](#getrecordcount)。 您可以移动到最后一个记录通过调用`MoveLast`。  
  
 一旦调用`SetPercentPosition`，对应的值相对应的近似位置处的记录将成为当前。  
  
> [!NOTE]
>  调用`SetPercentPosition`移动不建议对在记录集中的特定记录的当前记录。 调用[SetBookmark](#setbookmark)成员函数。  
  
 有关相关信息，请参阅主题 DAO 帮助中的"PercentPosition 属性"。  
  
##  <a name="update"></a>  CDaoRecordset::Update  
 在调用后调用此成员函数`AddNew`或`Edit`成员函数。  
  
```  
virtual void Update();
```  
  
### <a name="remarks"></a>备注  
 完成所需的此调用`AddNew`或`Edit`操作。  
  
 这两`AddNew`和`Edit`准备对保存到数据源添加或编辑过的数据放置在该域中的编辑缓冲区。 `Update` 保存数据。 只有这些字段标记为或检测到因为更改会更新。  
  
 如果数据源支持事务，则可以进行`Update`调用 (和其对应`AddNew`或`Edit`调用) 事务的一部分。  
  
> [!CAUTION]
>  如果您调用`Update`而不必首先调用`AddNew`或`Edit`，`Update`引发`CDaoException`。 如果您调用`AddNew`或`Edit`，则必须调用`Update`在调用之前[MoveNext](#movenext)或关闭记录集或数据源连接。 否则，所做的更改都将丢失而不另行通知。  
  
 记录集对象悲观锁定时在多用户环境中，则记录将保留锁定的时间`Edit`使用，直到更新已完成。 如果乐观地锁定记录集，该记录已被锁定，在数据库中更新之前，将与预编辑记录进行比较。 如果记录已更改，因为你调用`Edit`，则`Update`操作将失败和 MFC 会引发异常。 你可以用在锁定模式下`SetLockingMode`。  
  
> [!NOTE]
>  在外部数据库格式，如 ODBC 和可安装 ISAM 始终使用乐观锁定。  
  
 有关相关信息，请参阅主题的"AddNew 方法"、"CancelUpdate 方法"、"Delete 方法"、"上次更改时间属性"、"更新方法"和 DAO 帮助中的"EditMode 属性"。  
  
## <a name="see-also"></a>请参阅  
 [CObject 类](../../mfc/reference/cobject-class.md)   
 [层次结构图表](../../mfc/hierarchy-chart.md)   
 [CDaoTableDef 类](../../mfc/reference/cdaotabledef-class.md)   
 [CDaoWorkspace 类](../../mfc/reference/cdaoworkspace-class.md)   
 [CDaoDatabase 类](../../mfc/reference/cdaodatabase-class.md)   
 [CDaoQueryDef 类](../../mfc/reference/cdaoquerydef-class.md)
