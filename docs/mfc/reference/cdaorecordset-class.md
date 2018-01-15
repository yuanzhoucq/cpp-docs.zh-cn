---
title: "CDaoRecordset 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
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
dev_langs: C++
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
caps.latest.revision: "26"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: e50e83a2d52567d30901cea33cfccec3e236fe67
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
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
|[CDaoRecordset::CanAppend](#canappend)|返回非零，如果可以将新记录添加到记录集通过[AddNew](#addnew)成员函数。|  
|[CDaoRecordset::CanBookmark](#canbookmark)|返回非零，如果记录集支持书签。|  
|[CDaoRecordset::CancelUpdate](#cancelupdate)|取消任何挂起的更新，由于[编辑](#edit)或[AddNew](#addnew)操作。|  
|[CDaoRecordset::CanRestart](#canrestart)|返回非零如果[Requery](#requery)可以调用以进行重新运行记录集的查询。|  
|[CDaoRecordset::CanScroll](#canscroll)|返回非零，如果可以滚动显示记录。|  
|[CDaoRecordset::CanTransact](#cantransact)|返回非零，如果数据源支持事务。|  
|[CDaoRecordset::CanUpdate](#canupdate)|返回非零，如果可以更新记录集 （你可以添加、 更新或删除记录）。|  
|[CDaoRecordset::Close](#close)|关闭记录集。|  
|[CDaoRecordset::Delete](#delete)|从记录集删除当前记录。 你必须显式滚动到另一条记录后删除。|  
|[CDaoRecordset::DoFieldExchange](#dofieldexchange)|调用以 （在两个方向） 和之间交换数据的记录集的字段数据成员的数据源上相应的记录。 实现 DAO 记录字段交换 (DFX)。|  
|[CDaoRecordset::Edit](#edit)|准备对当前记录的更改。 调用**更新**以完成编辑。|  
|[CDaoRecordset::FillCache](#fillcache)|填充所有或本地缓存中，以便包含从 ODBC 数据源的数据的记录集对象的一部分。|  
|[CDaoRecordset::Find](#find)|查找第一个下, 一步，在满足指定的条件，使该记录的当前记录成为动态集类型记录集特定字符串的上一个或最后一个位置。|  
|[CDaoRecordset::FindFirst](#findfirst)|动态集类型或满足指定的条件，使该记录的当前记录成为的快照类型记录集中查找第一条记录。|  
|[CDaoRecordset::FindLast](#findlast)|动态集类型或满足指定的条件，使该记录的当前记录成为的快照类型记录集中查找最后一条记录。|  
|[CDaoRecordset::FindNext](#findnext)|动态集类型或满足指定的条件，使该记录的当前记录成为的快照类型记录集中查找下一条记录。|  
|[CDaoRecordset::FindPrev](#findprev)|动态集类型或满足指定的条件，使该记录的当前记录成为的快照类型记录集中查找前一条记录。|  
|[CDaoRecordset::GetAbsolutePosition](#getabsoluteposition)|返回一个记录集对象的当前记录的记录号。|  
|[CDaoRecordset::GetBookmark](#getbookmark)|返回一个值，表示记录上的书签。|  
|[CDaoRecordset::GetCacheSize](#getcachesize)|返回一个值，指定动态集类型的记录集包含本地缓存从 ODBC 数据源数据中的记录数。|  
|[CDaoRecordset::GetCacheStart](#getcachestart)|返回一个值，指定在为缓存的记录集的第一条记录的书签。|  
|[CDaoRecordset::GetCurrentIndex](#getcurrentindex)|返回`CString`最近包含索引的名称的索引，表类型上使用`CDaoRecordset`。|  
|[CDaoRecordset::GetDateCreated](#getdatecreated)|返回的日期和时间基表基础`CDaoRecordset`创建对象|  
|[CDaoRecordset::GetDateLastUpdated](#getdatelastupdated)|返回的日期和时间的基表基础的设计所做的最新更改`CDaoRecordset`对象。|  
|[CDaoRecordset::GetDefaultDBName](#getdefaultdbname)|返回默认数据源的名称。|  
|[CDaoRecordset::GetDefaultSQL](#getdefaultsql)|调用以获取要执行的默认 SQL 字符串。|  
|[CDaoRecordset::GetEditMode](#geteditmode)|返回一个值，该值指示当前记录的编辑状态。|  
|[CDaoRecordset::GetFieldCount](#getfieldcount)|返回一个值，表示在记录集中的字段数。|  
|[CDaoRecordset::GetFieldInfo](#getfieldinfo)|在记录集中返回特定类型的字段的信息。|  
|[CDaoRecordset::GetFieldValue](#getfieldvalue)|在记录集中返回的字段的值。|  
|[CDaoRecordset::GetIndexCount](#getindexcount)|检索下一个记录集的表中的索引数。|  
|[CDaoRecordset::GetIndexInfo](#getindexinfo)|返回各种类型的有关索引的信息。|  
|[CDaoRecordset::GetLastModifiedBookmark](#getlastmodifiedbookmark)|用于确定最最近添加或更新记录。|  
|[CDaoRecordset::GetLockingMode](#getlockingmode)|返回一个值，该值指示编辑过程实际上是锁定的类型。|  
|[CDaoRecordset::GetName](#getname)|返回`CString`包含记录集的名称。|  
|[CDaoRecordset::GetParamValue](#getparamvalue)|检索存储在基础 DAOParameter 对象中指定参数的当前值。|  
|[CDaoRecordset::GetPercentPosition](#getpercentposition)|返回的记录总数的百分比当前记录的位置。|  
|[CDaoRecordset::GetRecordCount](#getrecordcount)|返回记录集对象中访问的记录的数。|  
|[CDaoRecordset::GetSQL](#getsql)|获取用于选择记录的记录集的 SQL 字符串。|  
|[CDaoRecordset::GetType](#gettype)|调用以确定记录集的类型： 表类型、 动态集类型或快照的类型。|  
|[CDaoRecordset::GetValidationRule](#getvalidationrule)|返回`CString`包含用于验证数据，因为它字段中输入的值。|  
|[CDaoRecordset::GetValidationText](#getvalidationtext)|检索验证规则不满足时显示的文本。|  
|[CDaoRecordset::IsBOF](#isbof)|返回非零，如果在第一条记录之前定位位置记录集。 没有最新记录。|  
|[CDaoRecordset::IsDeleted](#isdeleted)|返回非零，如果记录集定位在已删除的记录上。|  
|[CDaoRecordset::IsEOF](#iseof)|返回非零，如果在最后一条记录后定位位置记录集。 没有最新记录。|  
|[CDaoRecordset::IsFieldDirty](#isfielddirty)|返回非零，如果已更改的当前记录中的指定的字段。|  
|[CDaoRecordset::IsFieldNull](#isfieldnull)|返回非零，如果当前记录中的指定的字段为 Null （无任何值）。|  
|[CDaoRecordset::IsFieldNullable](#isfieldnullable)|返回非零，如果当前记录中的指定的字段可以设置为 Null （无任何值）。|  
|[CDaoRecordset::IsOpen](#isopen)|返回非零如果[打开](#open)已被调用过。|  
|[CDaoRecordset::Move](#move)|将记录集到指定的记录数置于从中两个方向的当前记录。|  
|[CDaoRecordset::MoveFirst](#movefirst)|在记录集中的第一个记录置于当前记录。|  
|[CDaoRecordset::MoveLast](#movelast)|在记录集中的最后一个记录置于当前记录。|  
|[CDaoRecordset::MoveNext](#movenext)|定位上记录集的下一个记录，当前记录。|  
|[CDaoRecordset::MovePrev](#moveprev)|在上一记录的记录集上定位的当前记录。|  
|[Cdaorecordset:: Open](#open)|从表、 动态集或快照创建新的记录集。|  
|[CDaoRecordset::Requery](#requery)|运行记录集的查询，再次以刷新选定的记录。|  
|[CDaoRecordset::Seek](#seek)|在满足指定的条件的当前索引并使该记录的当前记录成为某个索引的表类型记录集对象中找到的记录。|  
|[CDaoRecordset::SetAbsolutePosition](#setabsoluteposition)|设置记录集对象的当前记录的记录数。|  
|[CDaoRecordset::SetBookmark](#setbookmark)|定位上包含指定的书签的记录，记录集。|  
|[CDaoRecordset::SetCacheSize](#setcachesize)|设置一个值，指定动态集类型的记录集包含本地缓存从 ODBC 数据源数据中的记录数。|  
|[CDaoRecordset::SetCacheStart](#setcachestart)|设置一个值，指定在为缓存的记录集的第一条记录的书签。|  
|[CDaoRecordset::SetCurrentIndex](#setcurrentindex)|调用以在表类型记录集上设置索引。|  
|[CDaoRecordset::SetFieldDirty](#setfielddirty)|将当前记录中的指定的字段标记为已更改。|  
|[CDaoRecordset::SetFieldNull](#setfieldnull)|设置为 Null （无任何值） 的当前记录中的指定字段的值。|  
|[CDaoRecordset::SetFieldValue](#setfieldvalue)|在记录集中设置字段的值。|  
|[CDaoRecordset::SetFieldValueNull](#setfieldvaluenull)|设置在记录集中为 Null 的字段的值。 （具有任何值）。|  
|[CDaoRecordset::SetLockingMode](#setlockingmode)|设置一个值，该值指示锁定，以编辑过程放入效果的类型。|  
|[CDaoRecordset::SetParamValue](#setparamvalue)|设置存储在基础 DAOParameter 对象中指定参数的当前值|  
|[CDaoRecordset::SetParamValueNull](#setparamvaluenull)|将指定的参数的当前值设置为 Null （无任何值）。|  
|[CDaoRecordset::SetPercentPosition](#setpercentposition)|将当前记录的位置设置为对应的在记录集中的记录总数的百分比的位置。|  
|[CDaoRecordset::Update](#update)|完成`AddNew`或**编辑**通过将新的或编辑数据保存在数据源上的操作。|  
  
### <a name="public-data-members"></a>公共数据成员  
  
|名称|描述|  
|----------|-----------------|  
|[Cdaorecordset:: M_bcheckcachefordirtyfields](#m_bcheckcachefordirtyfields)|包含一个标志，指示是否字段自动标记为已更改。|  
|[CDaoRecordset::m_nFields](#m_nfields)|包含记录集类中的字段数据成员的数目和选定数据源的记录集的列数。|  
|[CDaoRecordset::m_nParams](#m_nparams)|包含的记录集类中的参数数据成员数-与记录集的查询一起传递的参数数目|  
|[CDaoRecordset::m_pDAORecordset](#m_pdaorecordset)|指向基础记录集对象的 DAO 接口的指针。|  
|[CDaoRecordset::m_pDatabase](#m_pdatabase)|该结果集的源数据库。 包含指向的[CDaoDatabase](../../mfc/reference/cdaodatabase-class.md)对象。|  
|[CDaoRecordset::m_strFilter](#m_strfilter)|包含用于构造 SQL 字符串**其中**语句。|  
|[CDaoRecordset::m_strSort](#m_strsort)|包含用于构造 SQL 字符串**ORDER BY**语句。|  
  
## <a name="remarks"></a>备注  
 名为"记录集，"`CDaoRecordset`对象可在以下三个窗体中：  
  
-   表类型记录集表示可用于检查、 添加、 更改或删除单个数据库表中的记录的基表。  
  
-   动态集类型记录集是查询的可以具有可更新的记录的结果。 这些记录集是一组可用于检查、 添加、 更改或从基础数据库表或表中删除记录的记录。 动态集类型记录集可包含从数据库中的一个或多个表的字段。  
  
-   快照类型记录集是一组可用于查找数据或生成报表的记录的静态副本。 这些记录集可包含从数据库中的一个或多个表的字段，但无法更新。  
  
 记录集的每个窗体表示一组固定的打开记录集的记录。 时滚动到中的表类型记录集或动态集类型记录的记录时，它会反映其他用户或其他应用程序中的记录集打开记录集之后对记录所做的更改。 （不能更新快照类型记录集）。你可以使用`CDaoRecordset`直接或派生从一个应用程序特定的记录集类`CDaoRecordset`。 然后，你可以：  
  
-   滚动记录。  
  
-   设置索引，然后使用记录快速查找[Seek](#seek) （仅记录的表类型集）。  
  
-   查找记录基于字符串比较:"<"、"\<="，"="、"> ="，或">"（动态集类型和快照类型记录集）。  
  
-   更新的记录并指定锁定模式 （除非快照类型记录集）。  
  
-   筛选为约束从提供的那些数据源选择哪些记录的记录集。  
  
-   对记录集进行排序。  
  
-   参数化记录集使用直到运行时才知道的信息自定义的所选内容。  
  
 类`CDaoRecordset`提供类似于类接口`CRecordset`。 主要区别是该类`CDaoRecordset`访问通过数据访问对象 (DAO) 基于 OLE 的数据。 类`CRecordset`访问 DBMS 通过开放式数据库连接 (ODBC) 和 ODBC 驱动程序为该 DBMS。  
  
> [!NOTE]
>  DAO 数据库类有别于基于开放式数据库连接 (ODBC) 的 MFC 数据库类。 DAO 数据库类的所有名称都具有"CDao"前缀。 你仍可以访问 ODBC 数据源对于 DAO 类;DAO 类通常提供高级功能，因为它们是特定于 Microsoft Jet 数据库引擎。  
  
 你可以使用`CDaoRecordset`直接或从派生类`CDaoRecordset`。 若要在任一情况下使用记录集类，打开数据库，并构造记录集对象，向构造函数传递一个指向你`CDaoDatabase`对象。 此外可以构造`CDaoRecordset`对象，并允许创建一个临时的 MFC`CDaoDatabase`为你的对象。 然后调用记录集的[打开](#open)成员函数，该值指示对象是否为表类型记录集、 动态集类型的记录集或快照类型记录集。 调用**打开**从数据库中选择数据，并检索第一条记录。  
  
 使用对象的成员函数和数据成员滚动显示记录并对它们进行操作。 可执行的操作取决于该对象是表类型记录集、 动态集类型的记录集或快照类型的记录集，以及它是否可更新或只读的这取决于数据库或开放式数据库连接 (ODBC) 的功能数据源。 若要刷新记录可能已更改或添加自**打开**调用，调用对象的[Requery](#requery)成员函数。 调用对象的**关闭**成员函数，并使用它完成后销毁对象。  
  
 `CDaoRecordset`使用 DAO 记录字段交换 (DFX) 来支持读取和更新记录的字段的类型安全的 c + + 成员通过你`CDaoRecordset`或`CDaoRecordset`-派生类。 你还可以实现动态绑定列的数据库中不使用 DFX 机制使用[GetFieldValue](#getfieldvalue)和[SetFieldValue](#setfieldvalue)。  
  
 有关相关信息，请参阅主题 DAO 帮助中的"记录集对象"。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CDaoRecordset`  
  
## <a name="requirements"></a>惠?  
 **标头：** afxdao.h  
  
##  <a name="addnew"></a>CDaoRecordset::AddNew  
 调用此成员函数可将一条新记录添加到表类型或动态集类型的记录集。  
  
```  
virtual void AddNew();
```  
  
### <a name="remarks"></a>备注  
 记录的字段均最初为空。 (在数据库术语中，Null 表示"having 没有值"，并且不能与相同**NULL** c + + 中。)若要完成该操作，必须调用[更新](#update)成员函数。 **更新**将所做的更改保存到数据源。  
  
> [!CAUTION]
>  如果编辑记录的虚拟机和模板，然后向下滚动到另一个记录，而不调用**更新**，所做的更改都将丢失而不发出警告。  
  
 如果你将添加一条记录到动态集类型的记录集通过调用[AddNew](#addnew)，该记录是记录集内可见的且包含在其中它将显示出来到任何新的基础表`CDaoRecordset`对象。  
  
 新的记录的位置取决于的记录集类型：  
  
-   动态集类型中不保证记录集，插入新记录的位置。 使用 Microsoft Jet 3.0 的性能和并发原因更改此行为。 如果你的目标是要使当前记录的新添加的记录，获取最新的已修改记录书签并移动到该书签：  
  
 [!code-cpp[NVC_MFCDatabase#1](../../mfc/codesnippet/cpp/cdaorecordset-class_1.cpp)]  
  
-   在为其指定索引的表类型的记录集的情况下，会在它们在排序顺序的正确位置返回记录。 如果已指定没有索引，则会在记录集的末尾返回新的记录。  
  
 使用之前的当前记录`AddNew`仍然是当前记录。 如果你想要使新的记录当前和记录集支持书签、 调用[SetBookmark](#setbookmark)到由 LastModified 属性设置的基础的 DAO 记录集对象的书签。 这样可用于确定添加记录中的计数器 （自动递增） 字段的值。 有关详细信息，请参阅[GetLastModifiedBookmark](#getlastmodifiedbookmark)。  
  
 如果数据库支持事务，则可以使你`AddNew`调用事务的一部分。 有关事务的详细信息，请参阅类[CDaoWorkspace](../../mfc/reference/cdaoworkspace-class.md)。 请注意，应调用[CDaoWorkspace::BeginTrans](../../mfc/reference/cdaoworkspace-class.md#begintrans)之前调用`AddNew`。  
  
 它是非法调用`AddNew`为记录集其[打开](#open)不调用成员函数。 A`CDaoException`如果调用引发`AddNew`为无法追加的记录集。 你可以确定记录集是否可更新通过调用[CanAppend](#canappend)。  
  
 Framework 标记更改字段数据成员，以确保它们要写入到数据源上的记录由 DAO 记录字段交换 (DFX) 机制。 更改字段的值通常设置为字段脏自动，因此你将很少需要调用[SetFieldDirty](#setfielddirty)你自己，但你有时可能想要确保，列将显式更新或插入无论值是在字段数据成员中。 DFX 机制还使用了使用**伪 NULL**。 有关详细信息，请参阅[CDaoFieldExchange::m_nOperation](../../mfc/reference/cdaofieldexchange-class.md#m_noperation)。  
  
 如果未使用双缓冲机制，然后将更改字段的值不会不自动将字段设置为脏。 在这种情况下，将需要显式将字段设置已更新。 中包含的标志[m_bCheckCacheForDirtyFields](#m_bcheckcachefordirtyfields)控制此自动字段检查。  
  
> [!NOTE]
>  如果记录双缓冲 （即，自动字段启用检查），调用`CancelUpdate`将还原到之前所具有的值的成员变量`AddNew`或**编辑**调用。  
  
 有关相关信息，请参阅主题的"AddNew 方法"、"正在执行方法"、"上次更改时间属性"和 DAO 帮助中的"EditMode 属性"。  
  
##  <a name="canappend"></a>CDaoRecordset::CanAppend  
 调用此成员函数可确定是否以前已打开记录集可用于添加新记录通过调用[AddNew](#addnew)成员函数。  
  
```  
BOOL CanAppend() const;  
```  
  
### <a name="return-value"></a>返回值  
 如果是记录集允许添加新记录; 则为非 0否则为 0。 `CanAppend`如果你打开记录集持久化为只读的则将返回 0。  
  
### <a name="remarks"></a>备注  
 有关相关信息，请参阅主题 DAO 帮助中的"追加方法"。  
  
##  <a name="canbookmark"></a>CDaoRecordset::CanBookmark  
 调用此成员函数可确定是否以前已打开记录集允许你将使用书签的记录逐个标记。  
  
```  
BOOL CanBookmark();
```  
  
### <a name="return-value"></a>返回值  
 如果记录集支持书签，否则为 0，则为非 0。  
  
### <a name="remarks"></a>备注  
 如果你使用的完全基于 Microsoft Jet 数据库引擎表的记录集，书签使用除了在快照类型记录集标记为只进滚动记录集上。 其他数据库产品 （外部 ODBC 数据源） 可能不支持书签。  
  
 有关相关信息，请参阅主题 DAO 帮助中的"Bookmarkable 属性"。  
  
##  <a name="cancelupdate"></a>CDaoRecordset::CancelUpdate  
 `CancelUpdate`成员函数取消任何挂起的更新，由于[编辑](#edit)或[AddNew](#addnew)操作。  
  
```  
virtual void CancelUpdate();
```  
  
### <a name="remarks"></a>备注  
 例如，如果应用程序调用**编辑**或`AddNew`成员函数，并具有不称为[更新](#update)，`CancelUpdate`取消后所做的任何更改**编辑**或`AddNew`调用。  
  
> [!NOTE]
>  如果记录双缓冲 （即，自动字段启用检查），调用`CancelUpdate`将还原到之前所具有的值的成员变量`AddNew`或**编辑**调用。  
  
 如果没有任何**编辑**或`AddNew`操作挂起，`CancelUpdate`导致 MFC 引发异常。 调用[GetEditMode](#geteditmode)成员函数以确定是否可以取消一个挂起操作。  
  
 有关相关信息，请参阅主题 DAO 帮助中的"正在执行方法"。  
  
##  <a name="canrestart"></a>CDaoRecordset::CanRestart  
 调用此成员函数可确定记录集是否允许通过调用重启 （若要刷新其记录） 其查询**Requery**成员函数。  
  
```  
BOOL CanRestart();
```  
  
### <a name="return-value"></a>返回值  
 非零如果**Requery**可以调用以进行运行记录集的一次查询，否则为 0。  
  
### <a name="remarks"></a>备注  
 不支持表类型记录集**Requery**。  
  
 如果**Requery**是不受支持，调用[关闭](#close)然后[打开](#open)刷新数据。 你可以调用**Requery**更新记录集对象的基本参数查询后已更改的参数值。  
  
 有关相关信息，请参阅主题 DAO 帮助中的"可重启属性"。  
  
##  <a name="canscroll"></a>CDaoRecordset::CanScroll  
 调用此成员函数来确定记录集是否允许滚动。  
  
```  
BOOL CanScroll() const;  
```  
  
### <a name="return-value"></a>返回值  
 如果可以滚动浏览记录，否则为 0，则为非 0。  
  
### <a name="remarks"></a>备注  
 如果调用[打开](#open)与**dbForwardOnly**，记录集可以仅向前滚动。  
  
 有关相关信息，请参阅"定位记录用 DAO 当前指针"DAO 帮助中的主题。  
  
##  <a name="cantransact"></a>CDaoRecordset::CanTransact  
 调用此成员函数来确定记录集是否允许事务。  
  
```  
BOOL CanTransact();
```  
  
### <a name="return-value"></a>返回值  
 如果基础数据源支持事务，否则为 0，则为非 0。  
  
### <a name="remarks"></a>备注  
 有关相关信息，请参阅主题 DAO 帮助中的"事务属性"。  
  
##  <a name="canupdate"></a>CDaoRecordset::CanUpdate  
 调用此成员函数可确定是否可以更新记录集。  
  
```  
BOOL CanUpdate() const;  
```  
  
### <a name="return-value"></a>返回值  
 如果可以更新记录集则为非 0 （添加、 更新和删除记录），否则为 0。  
  
### <a name="remarks"></a>备注  
 记录集可能是只读的如果基础数据源是只读的或你指定**dbReadOnly**为`nOptions`当调用[打开](#open)为记录集。  
  
 有关相关信息，请参阅主题的"AddNew 方法"、"编辑方法"、"Delete 方法"、"更新方法"和 DAO 帮助中的"可更新属性"。  
  
##  <a name="cdaorecordset"></a>CDaoRecordset::CDaoRecordset  
 构造 `CDaoRecordset` 对象。  
  
```  
CDaoRecordset(CDaoDatabase* pDatabase = NULL);
```  
  
### <a name="parameters"></a>参数  
 `pDatabase`  
 包含指向的[CDaoDatabase](../../mfc/reference/cdaodatabase-class.md)对象或值**NULL**。 如果不是**NULL**和`CDaoDatabase`对象的**打开**成员函数不调用以将其连接到数据源，记录集尝试自己期间为您打开它[打开](#open)调用。 如果你通过**NULL**、`CDaoDatabase`对象进行构造并为你使用你指定如果派生从记录集类的数据源信息连接`CDaoRecordset`。  
  
### <a name="remarks"></a>备注  
 你可以使用`CDaoRecordset`直接派生从应用程序特定类或`CDaoRecordset`。 可以使用 ClassWizard 派生记录集类。  
  
> [!NOTE]
>  如果你是派生`CDaoRecordset`类，派生类必须提供其自己的构造函数。 在派生类的构造函数调用的构造函数`CDaoRecordset::CDaoRecordset`，将沿适当的参数传递给它。  
  
 传递**NULL**到记录集构造函数，以具有`CDaoDatabase`对象构造并为你自动连接。 这是不需要你构造和连接的有用快捷方式`CDaoDatabase`之前构造记录集对象。 如果`CDaoDatabase`对象未打开， [CDaoWorkspace](../../mfc/reference/cdaoworkspace-class.md)还将为你使用默认工作区创建对象。 有关详细信息，请参阅[CDaoDatabase::CDaoDatabase](../../mfc/reference/cdaodatabase-class.md#cdaodatabase)。  
  
##  <a name="close"></a>CDaoRecordset::Close  
 关闭`CDaoRecordset`对象移除它关联的数据库中的打开记录集的集合中。  
  
```  
virtual void Close();
```  
  
### <a name="remarks"></a>备注  
 因为**关闭**不会销毁`CDaoRecordset`对象，您可以通过调用重新使用该对象**打开**上相同的数据源或其他数据源。  
  
 所有挂起的[AddNew](#addnew)或[编辑](#edit)语句被取消，并且所有挂起的事务将回滚。 如果你想要保留挂起的添加件或编辑，调用[更新](#update)之前调用**关闭**为每个记录集。  
  
 你可以调用**打开**在调用后再次**关闭**。 这样就可以重复使用记录集对象。 一个更好的替代方法是调用[Requery](#requery)如果可能。  
  
 有关相关信息，请参阅主题 DAO 帮助中的"Close 方法"。  
  
##  <a name="delete"></a>CDaoRecordset::Delete  
 调用此成员函数以删除打开的动态集类型或表类型记录集对象中的当前记录。  
  
```  
virtual void Delete();
```  
  
### <a name="remarks"></a>备注  
 在成功删除之后, 记录集的字段数据成员设置为 Null 值，并且你必须显式调用其中一个记录集导航成员函数 ([移动](#move)， [Seek](#seek)， [SetBookmark](#setbookmark)，依次类推) 若要离开已删除的记录。 当从一个记录集删除记录时，必须有当前记录的记录集然后才能调用**删除**; 否则为则 MFC 会引发异常。  
  
 **删除**删除当前记录并使它成为不可访问。 虽然无法编辑或使用已删除的记录，但它仍当前记录。 一旦您移动到另一条记录，但是，你不能设为已删除的记录当前试。  
  
> [!CAUTION]
>  记录集必须是可更新，且必须具有有效记录的记录集当前在调用时**删除**。 例如，如果你删除一条记录，但你在调用之前不将其滚动到一条新记录**删除**再次，**删除**引发[CDaoException](../../mfc/reference/cdaoexception-class.md)。  
  
 如果您使用事务并且你调用，你可以取消删除一条记录[CDaoWorkspace::Rollback](../../mfc/reference/cdaoworkspace-class.md#rollback)成员函数。 如果基表是主表中的级联删除关系，删除当前记录可能也会删除外部表中的一个或多个记录。 有关详细信息，请参阅 DAO 帮助中的定义"级联删除"。  
  
 与不同`AddNew`和**编辑**，调用**删除**对的调用后面不接**更新**。  
  
 有关相关信息，请参阅主题的"AddNew 方法"、"编辑方法"、"Delete 方法"、"更新方法"和 DAO 帮助中的"可更新属性"。  
  
##  <a name="dofieldexchange"></a>CDaoRecordset::DoFieldExchange  
 框架调用此成员函数以自动交换字段数据成员的记录集对象和数据源上的当前记录的相应列之间的数据。  
  
```  
virtual void DoFieldExchange(CDaoFieldExchange* pFX);
```  
  
### <a name="parameters"></a>参数  
 `pFX`  
 包含指向的`CDaoFieldExchange`对象。 框架将已安装了此对象以便字段交换操作为指定上下文。  
  
### <a name="remarks"></a>备注  
 它还会将绑定参数数据成员，如果有的话，到记录集的选择的 SQL 语句字符串中的参数占位符。 字段数据，调用 DAO 记录字段交换 (DFX) 的交换的工作方式在两个方向： 从数据源上的记录的字段的记录集对象的字段数据成员和记录集对象的数据源上的记录。 若要动态绑定列，不需要实现`DoFieldExchange`。  
  
 您通常必须执行以便实现的唯一操作`DoFieldExchange`为派生记录集类是与 ClassWizard 创建类并指定的字段数据成员的名称和数据类型。 此外可能将代码添加到 ClassWizard 写入指定的参数数据成员。 如果所有字段都是要动态绑定，此函数将处于非活动状态，除非你指定的参数数据成员。  
  
 在声明 ClassWizard 你派生的记录集类时，向导会将写入的重写`DoFieldExchange`，类似于下面的示例：  
  
 [!code-cpp[NVC_MFCDatabase#2](../../mfc/codesnippet/cpp/cdaorecordset-class_2.cpp)]  
  
##  <a name="edit"></a>CDaoRecordset::Edit  
 调用此成员函数，以允许对当前记录的更改。  
  
```  
virtual void Edit();
```  
  
### <a name="remarks"></a>备注  
 一旦调用**编辑**成员函数，对当前记录的字段所做的更改复制到复制缓冲区。 对记录进行所需的更改后，调用**更新**以保存所做的更改。 **编辑**将保存记录集的数据成员的值。 如果调用**编辑**，进行更改，然后调用**编辑**再次，记录的值都将还原到它们早于第一个是**编辑**调用。  
  
> [!CAUTION]
>  如果编辑记录，然后执行任何操作都将移到另一条记录，而无需首先调用**更新**，所做的更改都将丢失而不发出警告。 此外，如果你关闭记录集或的父数据库，你已编辑的记录被丢弃而不发出警告。  
  
 在某些情况下，你可能想要通过使 Null （不包含任何数据） 中更新列。 为此，请调用`SetFieldNull`其中参数**TRUE**标记字段为 Null。 这也会导致要更新的列。 如果你想要写入到数据源中，即使其值未更改，请调用的字段`SetFieldDirty`其中参数**TRUE**。 之所以即使字段具有 Null 值。  
  
 Framework 标记更改字段数据成员，以确保它们要写入到数据源上的记录由 DAO 记录字段交换 (DFX) 机制。 更改字段的值通常设置为字段脏自动，因此你将很少需要调用[SetFieldDirty](#setfielddirty)你自己，但你有时可能想要确保，列将显式更新或插入无论值是在字段数据成员中。 DFX 机制还使用了使用**伪 NULL**。 有关详细信息，请参阅[CDaoFieldExchange::m_nOperation](../../mfc/reference/cdaofieldexchange-class.md#m_noperation)。  
  
 如果未使用双缓冲机制，然后将更改字段的值不会不自动将字段设置为脏。 在这种情况下，将需要显式将字段设置已更新。 中包含的标志[m_bCheckCacheForDirtyFields](#m_bcheckcachefordirtyfields)控制此自动字段检查。  
  
 记录当记录集对象保守式锁定在多用户环境中时，保持锁定状态从时间**编辑**完成更新之前使用。 如果乐观锁定记录集，该记录已被锁定，在数据库中更新之前，将与预编辑的记录进行比较。 如果记录已更改，因为你调用**编辑**、**更新**操作失败且 MFC 引发异常。 您可以更改与锁定模式`SetLockingMode`。  
  
> [!NOTE]
>  外部数据库格式，如 ODBC 和可安装 ISAM 上始终使用乐观锁定。  
  
 当前记录后，仍当前调用**编辑**。 若要调用**编辑**，必须有当前记录。 如果没有当前记录或记录集未引用的打开的表类型或动态集类型记录集对象，则会发生异常。 调用**编辑**导致`CDaoException`以下情况下引发：  
  
-   没有最新记录。  
  
-   记录集的数据库是只读的。  
  
-   记录中的任何字段不是可更新的。  
  
-   记录集的数据库由其他用户打开以供独占使用。  
  
-   其他用户锁定了包含您的记录的页面。  
  
 如果数据源支持事务，则你可以**编辑**调用事务的一部分。 请注意，应调用`CDaoWorkspace::BeginTrans`之前调用**编辑**和之后打开记录集。 此外请注意，调用`CDaoWorkspace::CommitTrans`不能用于调用代替**更新**完成**编辑**操作。 有关事务的详细信息，请参阅类`CDaoWorkspace`。  
  
 有关相关信息，请参阅主题的"AddNew 方法"、"编辑方法"、"Delete 方法"、"更新方法"和 DAO 帮助中的"可更新属性"。  
  
##  <a name="fillcache"></a>CDaoRecordset::FillCache  
 调用此成员函数可缓存的指定从记录集中的记录数。  
  
```  
void FillCache(
    long* pSize = NULL,  
    COleVariant* pBookmark = NULL);
```  
  
### <a name="parameters"></a>参数  
 `pSize`  
 指定要在缓存中填充行的数。 如果省略此参数的值是由基础的 DAO 对象 CacheSize 属性设置决定。  
  
 `pBookmark`  
 A [COleVariant](../../mfc/reference/colevariant-class.md)指定书签。 此书签所指定的记录从开始填充缓存。 如果省略此参数时，从基础的 DAO 对象的 CacheStart 属性所指定的记录开始填充缓存。  
  
### <a name="remarks"></a>备注  
 缓存提高的性能的应用程序中检索，或者提取，从远程服务器的数据。 缓存是在本地保存最近从服务器提取假定，数据将可能再次请求对象时运行该应用程序的数据的内存中的空间。 请求数据时，Microsoft Jet 数据库引擎的数据会首先检查缓存而不是提取在服务器上，这需要花费更多的时间。 使用非 ODBC 数据源上的缓存的数据无任何影响，因为不在缓存中保存的数据。  
  
 而不是等待缓存记录它们提取要填充的您可以显式缓存在任何时候调用来填充`FillCache`成员函数。 这是因为填充缓存较快方式`FillCache`提取一次而不是一次一个地的多个记录。 例如，显示每一满屏记录时，你可以让你的应用程序调用`FillCache`提取的下一步满屏记录。  
  
 通过记录集对象访问的任何 ODBC 数据库可以具有本地缓存。 若要创建缓存，请从远程数据源中，打开记录集对象，然后调用`SetCacheSize`和`SetCacheStart`记录集的成员函数。 如果`lSize`和*lBookmark*创建地址范围，则指定的范围之外的部分或完全`SetCacheSize`和`SetCacheStart`，此范围之外的记录集的部分将忽略，并且不会加载到缓存。 如果`FillCache`请求比的更多记录保留在远程数据源中、 仅剩下的记录，提取出来后，且不引发异常。  
  
 从缓存提取的记录不能反映由其他用户对源数据同时进行的更改。  
  
 `FillCache`提取仅尚未缓存的记录。 若要强制所有缓存的数据更新，请调用`SetCacheSize`成员函数时`lSize`参数等于 0，调用`SetCacheSize`试`lSize`最初请求，参数等于缓存的大小，然后调用`FillCache`.  
  
 有关相关信息，请参阅主题 DAO 帮助中的"FillCache 方法"。  
  
##  <a name="find"></a>CDaoRecordset::Find  
 调用此成员函数以在动态集或快照类型记录集中使用比较运算符查找特定字符串。  
  
```  
virtual BOOL Find(
    long lFindType,  
    LPCTSTR lpszFilter);
```  
  
### <a name="parameters"></a>参数  
 *lFindType*  
 一个值，该值指示查找操作所需的类型。 可能的值为：  
  
- **AFX_DAO_NEXT**查找匹配的字符串的下一个位置。  
  
- **AFX_DAO_PREV**查找匹配的字符串的上一位置。  
  
- **AFX_DAO_FIRST**查找匹配的字符串的第一个位置。  
  
- **AFX_DAO_LAST**查找匹配的字符串的最后一个位置。  
  
 `lpszFilter`  
 字符串表达式 (如**其中**不带有单词 SQL 语句中的子句**其中**) 用来定位该记录。 例如:  
  
 [!code-cpp[NVC_MFCDatabase#3](../../mfc/codesnippet/cpp/cdaorecordset-class_3.cpp)]  
  
### <a name="return-value"></a>返回值  
 如果找到匹配的记录，否则为 0，则为非 0。  
  
### <a name="remarks"></a>备注  
 你可以找到第一个下, 一步上, 一个或最后一个的字符串实例。 **查找**是虚函数，因此你可以重写此方法并添加您自己的实现。 `FindFirst`， `FindLast`， `FindNext`，和`FindPrev`成员函数都调用**查找**成员函数，因此你可以使用**查找**来控制的所有查找操作的行为.  
  
 若要查找中的表类型记录集的记录，调用[Seek](#seek)成员函数。  
  
> [!TIP]
>  记录你有多个有效的越小套**查找**将。 通常，和尤其是在具有 ODBC 数据，则最好创建新的查询，以检索所需的记录。  
  
 有关相关信息，请参阅主题"FindFirst，执行 FindLast，FindNext，FindPrevious 方法"DAO 帮助中。  
  
##  <a name="findfirst"></a>CDaoRecordset::FindFirst  
 调用此成员函数以查找与指定的条件匹配的第一个记录。  
  
```  
BOOL FindFirst(LPCTSTR lpszFilter);
```  
  
### <a name="parameters"></a>参数  
 `lpszFilter`  
 字符串表达式 (如**其中**不带有单词 SQL 语句中的子句**其中**) 用来定位该记录。  
  
### <a name="return-value"></a>返回值  
 如果找到匹配的记录，否则为 0，则为非 0。  
  
### <a name="remarks"></a>备注  
 `FindFirst`成员函数开始从记录集的开始其搜索和搜索到记录集的末尾。  
  
 如果你想要包括所有记录 （而不仅仅是满足特定条件的那些） 在搜索中使用移动操作之一来记录之间移动。 若要查找中的表类型记录集的记录，调用`Seek`成员函数。  
  
 如果未找到与条件匹配的记录了，当前记录指针是不确定，和`FindFirst`返回零。 如果记录集包含满足的条件的多个记录`FindFirst`查找第一个匹配项，`FindNext`查找下一个匹配项，依次类推。  
  
> [!CAUTION]
>  如果编辑当前记录，请务必保存所做的更改，通过调用**更新**成员函数之前将移到另一条记录。 如果你不将移至另一条记录更新，所做的更改都将丢失而不发出警告。  
  
 **查找**成员函数搜索的位置和下表中指定的方向：  
  
|查找操作|开始|搜索方向|  
|---------------------|-----------|----------------------|  
|`FindFirst`|记录集的开头|记录集的结尾|  
|`FindLast`|记录集的结尾|记录集的开头|  
|`FindNext`|当前记录|记录集的结尾|  
|**FindPrevious**|当前记录|记录集的开头|  
  
> [!NOTE]
>  当调用`FindLast`，Microsoft Jet 数据库引擎完全填充记录集中在开始搜索之前, 如果这不已完成了。 第一次搜索可能需要超过后续搜索。  
  
 使用一个查找操作不是调用相同**MoveFirst**或`MoveNext`，但是，这只是将第一个或下一步记录当前而无需指定一个条件。 你可以按照与移动操作查找操作。  
  
 使用查找操作时，请记住以下：  
  
-   如果**查找**返回非零值，未定义的当前记录。 在这种情况下，你必须在此位置回有效记录的当前记录指针。  
  
-   不能使用只进滚动快照类型记录集查找操作。  
  
-   应使用美国日期格式 （月-日-年） 时就搜索字段包含日期，即使你不使用 Microsoft Jet 数据库引擎; 的美国版本否则，匹配记录可能找到。  
  
-   在使用 ODBC 数据库和大型动态记录集，你可能发现使用查找操作时，是速度很慢，尤其是处理大型记录集。 你可以通过使用 SQL 查询来提高性能自定义**ORDERBY**或**其中**子句、 参数的查询或**CDaoQuerydef**检索特定的对象索引的记录。  
  
 有关相关信息，请参阅主题"FindFirst，执行 FindLast，FindNext，FindPrevious 方法"DAO 帮助中。  
  
##  <a name="findlast"></a>CDaoRecordset::FindLast  
 调用此成员函数以查找与指定的条件匹配的最后一个记录。  
  
```  
BOOL FindLast(LPCTSTR lpszFilter);
```  
  
### <a name="parameters"></a>参数  
 `lpszFilter`  
 字符串表达式 (如**其中**不带有单词 SQL 语句中的子句**其中**) 用来定位该记录。  
  
### <a name="return-value"></a>返回值  
 如果找到匹配的记录，否则为 0，则为非 0。  
  
### <a name="remarks"></a>备注  
 `FindLast`成员函数开始记录集的末尾其搜索和记录集的开始，从向后搜索。  
  
 如果你想要包括所有记录 （而不仅仅是满足特定条件的那些） 在搜索中使用移动操作之一来记录之间移动。 若要查找中的表类型记录集的记录，调用`Seek`成员函数。  
  
 如果未找到与条件匹配的记录了，当前记录指针是不确定，和`FindLast`返回零。 如果记录集包含满足的条件的多个记录`FindFirst`查找第一个匹配项，`FindNext`查找下一个匹配项后第一个匹配项，依次类推。  
  
> [!CAUTION]
>  如果编辑当前记录，请确保通过调用保存所做的更改**更新**成员函数之前将移到另一条记录。 如果你不将移至另一条记录更新，所做的更改都将丢失而不发出警告。  
  
 使用一个查找操作不是调用相同**MoveFirst**或`MoveNext`，但是，这只是将第一个或下一步记录当前而无需指定一个条件。 你可以按照与移动操作查找操作。  
  
 使用查找操作时，请记住以下：  
  
-   如果**查找**返回非零值，未定义的当前记录。 在这种情况下，你必须在此位置回有效记录的当前记录指针。  
  
-   不能使用只进滚动快照类型记录集查找操作。  
  
-   应使用美国日期格式 （月-日-年） 时就搜索字段包含日期，即使你不使用 Microsoft Jet 数据库引擎; 的美国版本否则，匹配记录可能找到。  
  
-   在使用 ODBC 数据库和大型动态记录集，你可能发现使用查找操作时，是速度很慢，尤其是处理大型记录集。 你可以通过使用 SQL 查询来提高性能自定义**ORDERBY**或**其中**子句、 参数的查询或**CDaoQuerydef**检索特定的对象索引的记录。  
  
 有关相关信息，请参阅主题"FindFirst，执行 FindLast，FindNext，FindPrevious 方法"DAO 帮助中。  
  
##  <a name="findnext"></a>CDaoRecordset::FindNext  
 调用此成员函数以查找与指定的条件匹配的下一个记录。  
  
```  
BOOL FindNext(LPCTSTR lpszFilter);
```  
  
### <a name="parameters"></a>参数  
 `lpszFilter`  
 字符串表达式 (如**其中**不带有单词 SQL 语句中的子句**其中**) 用来定位该记录。  
  
### <a name="return-value"></a>返回值  
 如果找到匹配的记录，否则为 0，则为非 0。  
  
### <a name="remarks"></a>备注  
 `FindNext`成员函数开始处的当前记录其搜索，一直搜索到记录集的末尾。  
  
 如果你想要包括所有记录 （而不仅仅是满足特定条件的那些） 在搜索中使用移动操作之一来记录之间移动。 若要查找中的表类型记录集的记录，调用`Seek`成员函数。  
  
 如果未找到与条件匹配的记录了，当前记录指针是不确定，和`FindNext`返回零。 如果记录集包含满足的条件的多个记录`FindFirst`查找第一个匹配项，`FindNext`查找下一个匹配项，依次类推。  
  
> [!CAUTION]
>  如果编辑当前记录，请确保通过调用保存所做的更改**更新**成员函数之前将移到另一条记录。 如果你不将移至另一条记录更新，所做的更改都将丢失而不发出警告。  
  
 使用一个查找操作不是调用相同**MoveFirst**或`MoveNext`，但是，这只是将第一个或下一步记录当前而无需指定一个条件。 你可以按照与移动操作查找操作。  
  
 使用查找操作时，请记住以下：  
  
-   如果**查找**返回非零值，未定义的当前记录。 在这种情况下，你必须在此位置回有效记录的当前记录指针。  
  
-   不能使用只进滚动快照类型记录集查找操作。  
  
-   应使用美国日期格式 （月-日-年） 时就搜索字段包含日期，即使你不使用 Microsoft Jet 数据库引擎; 的美国版本否则，匹配记录可能找到。  
  
-   在使用 ODBC 数据库和大型动态记录集，你可能发现使用查找操作时，是速度很慢，尤其是处理大型记录集。 你可以通过使用 SQL 查询来提高性能自定义**ORDERBY**或**其中**子句、 参数的查询或**CDaoQuerydef**检索特定的对象索引的记录。  
  
 有关相关信息，请参阅主题"FindFirst，执行 FindLast，FindNext，FindPrevious 方法"DAO 帮助中。  
  
##  <a name="findprev"></a>CDaoRecordset::FindPrev  
 调用此成员函数以查找与指定的条件匹配的上一条记录。  
  
```  
BOOL FindPrev(LPCTSTR lpszFilter);
```  
  
### <a name="parameters"></a>参数  
 `lpszFilter`  
 字符串表达式 (如**其中**不带有单词 SQL 语句中的子句**其中**) 用来定位该记录。  
  
### <a name="return-value"></a>返回值  
 如果找到匹配的记录，否则为 0，则为非 0。  
  
### <a name="remarks"></a>备注  
 `FindPrev`成员函数开始处的当前记录其搜索，并开始，从记录集的向后搜索。  
  
 如果你想要包括所有记录 （而不仅仅是满足特定条件的那些） 在搜索中使用移动操作之一来记录之间移动。 若要查找中的表类型记录集的记录，调用`Seek`成员函数。  
  
 如果未找到与条件匹配的记录了，当前记录指针是不确定，和`FindPrev`返回零。 如果记录集包含满足的条件的多个记录`FindFirst`查找第一个匹配项，`FindNext`查找下一个匹配项，依次类推。  
  
> [!CAUTION]
>  如果编辑当前记录，请确保通过调用保存所做的更改**更新**成员函数之前将移到另一条记录。 如果你不将移至另一条记录更新，所做的更改都将丢失而不发出警告。  
  
 使用一个查找操作不是调用相同**MoveFirst**或`MoveNext`，但是，这只是将第一个或下一步记录当前而无需指定一个条件。 你可以按照与移动操作查找操作。  
  
 使用查找操作时，请记住以下：  
  
-   如果**查找**返回非零值，未定义的当前记录。 在这种情况下，你必须在此位置回有效记录的当前记录指针。  
  
-   不能使用只进滚动快照类型记录集查找操作。  
  
-   应使用美国日期格式 （月-日-年） 时就搜索字段包含日期，即使你不使用 Microsoft Jet 数据库引擎; 的美国版本否则，匹配记录可能找到。  
  
-   在使用 ODBC 数据库和大型动态记录集，你可能发现使用查找操作时，是速度很慢，尤其是处理大型记录集。 你可以通过使用 SQL 查询来提高性能自定义**ORDERBY**或**其中**子句、 参数的查询或**CDaoQuerydef**检索特定的对象索引的记录。  
  
 有关相关信息，请参阅主题"FindFirst，执行 FindLast，FindNext，FindPrevious 方法"DAO 帮助中。  
  
##  <a name="getabsoluteposition"></a>CDaoRecordset::GetAbsolutePosition  
 返回一个记录集对象的当前记录的记录号。  
  
```  
long GetAbsolutePosition();
```  
  
### <a name="return-value"></a>返回值  
 从 0 到记录集内的记录数的整数。 对应于记录集中的当前记录的序号位置。  
  
### <a name="remarks"></a>备注  
 基础的 DAO 对象的 AbsolutePosition 属性值是从零开始;设置为 0 是指在记录集中的第一个记录。 可以通过调用中确定的记录集填充记录数[GetRecordCount](#getrecordcount)。 调用`GetRecordCount`可能需要一些时间，因为它必须访问所有记录，以确定计数。  
  
 如果没有当前记录，作为在记录集中，不记录时-返回 1。 如果删除该当前记录，不定义 AbsolutePosition 属性值，并且如果正在引用则 MFC 会引发异常。 动态集类型的记录集，新的记录会添加到序列的末尾。  
  
> [!NOTE]
>  此属性不应作为代理项记录编号。 仍然建议书签保留并返回到给定位置，而且这是在所有类型的记录集对象之间定位当前记录的唯一方式。 具体而言，当其前面的记录将被删除时，将更改给定的记录的位置。 此外还有，给定的记录将具有相同的绝对位置，如果重新因为不能保证在记录集内的单个记录的顺序，除非它使用 SQL 语句中使用创建再次创建记录集不保证**ORDERBY**子句。  
  
> [!NOTE]
>  此成员函数是仅对动态集类型和快照类型记录集有效。  
  
 有关相关信息，请参阅主题 DAO 帮助中的"AbsolutePosition 属性"。  
  
##  <a name="getbookmark"></a>CDaoRecordset::GetBookmark  
 调用此成员函数可获取特定的记录中的书签值。  
  
```  
COleVariant GetBookmark();
```  
  
### <a name="return-value"></a>返回值  
 返回一个值，表示当前记录上的书签。  
  
### <a name="remarks"></a>备注  
 创建或打开记录集对象后，每个其记录已具有一个唯一的书签它支持它们。 调用`CanBookmark`确定记录集是否支持书签。  
  
 你可以通过将分配到书签的值保存当前记录的书签`COleVariant`对象。 若要快速返回到该记录移到另一条记录之后，任何时候，调用`SetBookmark`带参数的值相对应`COleVariant`对象。  
  
> [!NOTE]
>  调用[Requery](#requery)更改 DAO 书签。  
  
 有关相关信息，请参阅主题 DAO 帮助中的"书签属性"。  
  
##  <a name="getcachesize"></a>CDaoRecordset::GetCacheSize  
 调用此成员函数可获取的缓存的记录数。  
  
```  
long GetCacheSize();
```  
  
### <a name="return-value"></a>返回值  
 一个值，指定动态集类型的记录集包含本地缓存从 ODBC 数据源数据中的记录数。  
  
### <a name="remarks"></a>备注  
 数据缓存提高从通过动态集类型记录集对象的远程服务器中检索数据的应用程序的性能。 缓存在本地保存最近的事件中运行应用程序时将再次请求数据从服务器检索的数据的内存空间。 请求数据时，Microsoft Jet 数据库引擎所请求数据的缓存会首先检查而不是检索在服务器上，这需要花费更多的时间。 不是来自 ODBC 数据源的数据不保存在缓存中。  
  
 任何 ODBC 数据源，例如一个附加的表，可以本地缓存。  
  
 有关相关信息，请参阅 DAO 帮助中的主题"CacheSize，CacheStart 属性"。  
  
##  <a name="getcachestart"></a>CDaoRecordset::GetCacheStart  
 调用此成员函数可获取为缓存的记录集的第一个记录的书签值。  
  
```  
COleVariant GetCacheStart();
```  
  
### <a name="return-value"></a>返回值  
 A `COleVariant` ，它指定的第一条记录书签中为缓存的记录集。  
  
### <a name="remarks"></a>备注  
 Microsoft Jet 数据库引擎从缓存中，请求缓存范围内的记录并从服务器请求到的缓存范围外的记录。  
  
> [!NOTE]
>  从缓存中检索的记录不能反映其他用户对源数据同时进行的更改。  
  
 有关相关信息，请参阅 DAO 帮助中的主题"CacheSize，CacheStart 属性"。  
  
##  <a name="getcurrentindex"></a>CDaoRecordset::GetCurrentIndex  
 调用此成员函数可确定当前正在使用中索引的表类型索引`CDaoRecordset`对象。  
  
```  
CString GetCurrentIndex();
```  
  
### <a name="return-value"></a>返回值  
 A`CString`包含当前正在使用的表类型记录集的索引的名称。 如果已设置没有索引，则返回空字符串。  
  
### <a name="remarks"></a>备注  
 此索引是在表类型记录集中，排序记录的基础，并可用于通过[Seek](#seek)成员函数来查找记录。  
  
 A`CDaoRecordset`对象可以有多个索引，但可以使用一次只有一个索引 (尽管[CDaoTableDef](../../mfc/reference/cdaotabledef-class.md)对象可能具有在其上定义的多个索引)。  
  
 有关相关信息，请参阅主题"索引对象"，并定义 DAO 帮助中的"当前索引"。  
  
##  <a name="getdatecreated"></a>CDaoRecordset::GetDateCreated  
 调用此成员函数可检索的日期和时间创建基表。  
  
```  
COleDateTime GetDateCreated();
```  
  
### <a name="return-value"></a>返回值  
 A [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)对象，其中包含的日期和时间创建基表。  
  
### <a name="remarks"></a>备注  
 日期和时间设置均源自在其创建基础表的计算机。  
  
 有关相关信息，请参阅 DAO 帮助中的主题"时间，上次更新属性"。  
  
##  <a name="getdatelastupdated"></a>CDaoRecordset::GetDateLastUpdated  
 调用此成员函数可检索的日期和时间，上次更新架构。  
  
```  
COleDateTime GetDateLastUpdated();
```  
  
### <a name="return-value"></a>返回值  
 A [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)对象，其中包含的日期和时间，上次更新基表结构 （架构）。  
  
### <a name="remarks"></a>备注  
 日期和时间设置均源自基表结构 （架构） 的上次更新的计算机。  
  
 有关相关信息，请参阅 DAO 帮助中的主题"时间，上次更新属性"。  
  
##  <a name="getdefaultdbname"></a>CDaoRecordset::GetDefaultDBName  
 调用此成员函数可确定该记录集的数据库的名称。  
  
```  
virtual CString GetDefaultDBName();
```  
  
### <a name="return-value"></a>返回值  
 A `CString` ，包含的路径和从中派生该记录集的数据库名称。  
  
### <a name="remarks"></a>备注  
 如果没有指针创建记录集[CDaoDatabase](../../mfc/reference/cdaodatabase-class.md)，然后记录集使用此路径来打开的默认数据库。 默认情况下，此函数返回一个空字符串。 当 ClassWizard 派生新的记录集从`CDaoRecordset`，它将为你创建此函数。  
  
 下面的示例演示如何使用双反斜杠 (\\\\) 在字符串中，按原样需要才能正确解释的字符串。  
  
 [!code-cpp[NVC_MFCDatabase#4](../../mfc/codesnippet/cpp/cdaorecordset-class_4.cpp)]  
  
##  <a name="getdefaultsql"></a>CDaoRecordset::GetDefaultSQL  
 框架调用此成员函数可获取记录集所基于的默认 SQL 语句。  
  
```  
virtual CString GetDefaultSQL();
```  
  
### <a name="return-value"></a>返回值  
 A`CString`包含默认的 SQL 语句。  
  
### <a name="remarks"></a>备注  
 这可能是一个表名或 SQL**选择**语句。  
  
 间接通过声明与 ClassWizard，记录集类定义默认的 SQL 语句，ClassWizard 为你执行此任务。  
  
 如果传递的 null SQL 字符串[打开](#open)，然后调用此函数可确定记录集的表名或 SQL。  
  
##  <a name="geteditmode"></a>CDaoRecordset::GetEditMode  
 调用此成员函数可确定状态的编辑，这是以下值之一：  
  
```  
short GetEditMode();
```  
  
### <a name="return-value"></a>返回值  
 返回一个值，该值指示当前记录的编辑状态。  
  
### <a name="remarks"></a>备注  
  
|“值”|描述|  
|-----------|-----------------|  
|**dbEditNone**|任何编辑操作不正在进行。|  
|**dbEditInProgress**|**编辑**已调用。|  
|**dbEditAdd**|`AddNew`已调用。|  
  
 有关相关信息，请参阅主题 DAO 帮助中的"EditMode 属性"。  
  
##  <a name="getfieldcount"></a>CDaoRecordset::GetFieldCount  
 调用此成员函数可检索的记录集内定义的字段 （列） 数。  
  
```  
short GetFieldCount();
```  
  
### <a name="return-value"></a>返回值  
 在记录集中的字段数。  
  
### <a name="remarks"></a>备注  
 有关相关信息，请参阅主题 DAO 帮助中的"计数属性"。  
  
##  <a name="getfieldinfo"></a>CDaoRecordset::GetFieldInfo  
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
 `nIndex`  
 记录集的字段集合，按索引查找中的预定义字段的从零开始的索引。  
  
 `fieldinfo`  
 对引用[CDaoFieldInfo](../../mfc/reference/cdaofieldinfo-structure.md)结构。  
  
 `dwInfoOptions`  
 指定有关要检索的记录集的信息的选项。 可用选项以及它们会导致函数返回此处列出。 为了获得最佳性能，检索仅您需要的信息的级别：  
  
- `AFX_DAO_PRIMARY_INFO`（默认值）名称、 类型、 大小属性  
  
- `AFX_DAO_SECONDARY_INFO`主要的信息，加上： 序号位置，需要，允许零长度，排序规则顺序外的名称，源字段，源表  
  
- `AFX_DAO_ALL_INFO`主要和辅助信息，加上： 默认值，验证规则验证文本  
  
 `lpszName`  
 字段的名称。  
  
### <a name="remarks"></a>备注  
 一个版本的函数，可按索引查找字段。 另一个版本中，可以按名称查找字段。  
  
 返回的信息的说明，请参阅[CDaoFieldInfo](../../mfc/reference/cdaofieldinfo-structure.md)结构。 此结构具有对应于上面列出的说明中的信息的项的成员`dwInfoOptions`。 当请求在一个级别的信息时，可以为任何以前的级别的信息。  
  
 有关相关信息，请参阅主题 DAO 帮助中的"特性属性"。  
  
##  <a name="getfieldvalue"></a>CDaoRecordset::GetFieldValue  
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
 `lpszName`  
 指向包含的字段名称的字符串的指针。  
  
 `varValue`  
 对引用`COleVariant`将存储的字段值的对象。  
  
 `nIndex`  
 记录集的字段集合，按索引查找中的字段一个从零开始索引。  
  
### <a name="return-value"></a>返回值  
 两个版本`GetFieldValue`的返回值返回[COleVariant](../../mfc/reference/colevariant-class.md)对象，其中包含字段的值。  
  
### <a name="remarks"></a>备注  
 你可以查找字段，按名称或序号位置。  
  
> [!NOTE]
>  调用了采用该成员函数的版本的一个更高效`COleVariant`对象引用为一个参数，而不是调用返回的版本`COleVariant`对象。 为了向后兼容保留此函数后一种版本。  
  
 使用`GetFieldValue`和[SetFieldValue](#setfieldvalue)将字段动态绑定在运行的时而不是静态绑定列使用[DoFieldExchange](#dofieldexchange)机制。  
  
 `GetFieldValue`与`DoFieldExchange`机制可结合使用来提高性能。 例如，使用`GetFieldValue`检索一个值，你需要仅按需，并将分配到接口中的"详细信息"按钮该调用。  
  
 有关相关信息，请参阅"字段对象"和"值属性"DAO 帮助中的主题。  
  
##  <a name="getindexcount"></a>CDaoRecordset::GetIndexCount  
 调用此成员函数可确定对表类型记录集可用的索引数。  
  
```  
short GetIndexCount();
```  
  
### <a name="return-value"></a>返回值  
 中的表类型记录集的索引数。  
  
### <a name="remarks"></a>备注  
 `GetIndexCount`可用于循环访问中的记录集的所有索引。 出于这个目的，使用`GetIndexCount`结合[GetIndexInfo](#getindexinfo)。 如果你对动态集类型或快照类型记录集调用此成员函数，则 MFC 会引发异常。  
  
 有关相关信息，请参阅主题 DAO 帮助中的"特性属性"。  
  
##  <a name="getindexinfo"></a>CDaoRecordset::GetIndexInfo  
 调用此成员函数来获取各种类型的基的基础记录集的表中定义的索引有关的信息。  
  
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
 `nIndex`  
 表的索引集合，按数字位置查找中的从零开始索引。  
  
 `indexinfo`  
 对引用[CDaoIndexInfo](../../mfc/reference/cdaoindexinfo-structure.md)结构。  
  
 `dwInfoOptions`  
 指定要检索的索引有关的信息的选项。 可用选项以及它们会导致函数返回此处列出。 为了获得最佳性能，检索仅您需要的信息的级别：  
  
- `AFX_DAO_PRIMARY_INFO`（默认值）名称，字段信息字段  
  
- `AFX_DAO_SECONDARY_INFO`主要的信息，加上： 主、 唯一、 聚集、 IgnoreNulls，所需，外部  
  
- `AFX_DAO_ALL_INFO`主要和辅助信息，加上： 非重复计数  
  
 `lpszName`  
 指向按名称查找的名称的索引对象的指针。  
  
### <a name="remarks"></a>备注  
 该函数的一个版本，可以通过在集合中的位置的索引查找。 另一个版本中，可以按名称查找索引。  
  
 返回的信息的说明，请参阅[CDaoIndexInfo](../../mfc/reference/cdaoindexinfo-structure.md)结构。 此结构具有对应于上面列出的说明中的信息的项的成员`dwInfoOptions`。 当请求在一个级别的信息时，可以为任何以前的级别的信息。  
  
 有关相关信息，请参阅主题 DAO 帮助中的"特性属性"。  
  
##  <a name="getlastmodifiedbookmark"></a>CDaoRecordset::GetLastModifiedBookmark  
 调用此成员函数可检索最近添加或更新记录的书签。  
  
```  
COleVariant GetLastModifiedBookmark();
```  
  
### <a name="return-value"></a>返回值  
 A`COleVariant`包含该书签用于指示最近添加或更改记录。  
  
### <a name="remarks"></a>备注  
 创建或打开记录集对象后，每个其记录已具有一个唯一的书签它支持它们。 调用[GetBookmark](#getbookmark)来确定记录集是否支持书签。 如果记录集不支持书签，`CDaoException`引发。  
  
 添加一条记录时，它将出现在记录集，末尾，并不是当前记录。 若要使新的记录当前，调用`GetLastModifiedBookmark`，然后调用`SetBookmark`要返回到新添加的记录。  
  
 有关相关信息，请参阅主题 DAO 帮助中的"上次更改时间属性"。  
  
##  <a name="getlockingmode"></a>CDaoRecordset::GetLockingMode  
 调用此成员函数可确定实际上锁定记录集的类型。  
  
```  
BOOL GetLockingMode();
```  
  
### <a name="return-value"></a>返回值  
 如果锁定的类型是保守式的则不为开放式记录锁定否则为 0。  
  
### <a name="remarks"></a>备注  
 只要你调用保守式锁定时实际上，包含正在编辑的记录的数据页锁定[编辑](#edit)成员函数。 在调用时，该页是解锁[更新](#update)或[关闭](#close)成员函数或任何移动或查找操作。  
  
 仅当与正在更新记录时，才时乐观锁定实际上是锁定包含记录的数据页**更新**成员函数。  
  
 当使用 ODBC 数据源，锁定模式始终是开放式的。  
  
 有关相关信息，请参阅"LockEdits 属性"和"锁定行为在多用户应用程序"DAO 帮助中的主题。  
  
##  <a name="getname"></a>CDaoRecordset::GetName  
 调用此成员函数可检索的记录集名称。  
  
```  
CString GetName();
```  
  
### <a name="return-value"></a>返回值  
 A`CString`包含记录集的名称。  
  
### <a name="remarks"></a>备注  
 记录集的名称必须以字母开头，并且可以包含最多 40 个字符。 它可以包含数字和下划线字符，但不能包含标点或空格。  
  
 有关相关信息，请参阅主题 DAO 帮助中的"名称属性"。  
  
##  <a name="getparamvalue"></a>CDaoRecordset::GetParamValue  
 调用此成员函数可检索基础 DAOParameter 对象中存储的指定参数的当前值。  
  
```  
virtual COleVariant GetParamValue(int nIndex);  
virtual COleVariant GetParamValue(LPCTSTR lpszName);
```  
  
### <a name="parameters"></a>参数  
 `nIndex`  
 基础 DAOParameter 对象中的参数的数字位置。  
  
 `lpszName`  
 参数所需其值的名称。  
  
### <a name="return-value"></a>返回值  
 类的对象[COleVariant](../../mfc/reference/colevariant-class.md) ，其中包含参数的值。  
  
### <a name="remarks"></a>备注  
 按名称或集合中其数字位置，你可以访问参数。  
  
 有关相关信息，请参阅主题 DAO 帮助中的"参数对象"。  
  
##  <a name="getpercentposition"></a>CDaoRecordset::GetPercentPosition  
 如果调用处理动态集类型或快照类型记录集时`GetPercentPosition`完全填充记录集之前, 移动的量是相对于访问由调用的记录数[GetRecordCount](#getrecordcount).  
  
```  
float GetPercentPosition();
```  
  
### <a name="return-value"></a>返回值  
 0 到 100 之间的数字指示基于百分比的中记录集的记录的记录集对象中的当前记录的近似位置。  
  
### <a name="remarks"></a>备注  
 你可以通过将移动到最后一个记录调用[MoveLast](#movelast)到完整填充所有记录集，但这可能需要很长的时间。  
  
 你可以调用`GetPercentPosition`上所有三种类型的记录集对象，包括没有索引的表。 但是，不能调用`GetPercentPosition`只进滚动快照，或打开从外部数据库针对的传递查询的记录集。 如果没有当前记录，或其当前记录已被删除，`CDaoException`引发。  
  
 有关相关信息，请参阅主题 DAO 帮助中的"PercentPosition 属性"。  
  
##  <a name="getrecordcount"></a>CDaoRecordset::GetRecordCount  
 调用此成员函数以找出已访问在记录集中的多少条记录。  
  
```  
long GetRecordCount();
```  
  
### <a name="return-value"></a>返回值  
 返回记录集对象中访问的记录的数。  
  
### <a name="remarks"></a>备注  
 `GetRecordCount`不表示多少条记录包含动态集类型或快照类型记录集中，直到已访问的所有记录。 此成员函数调用可能需要占用大量的时间才能完成。  
  
 后的最新记录已被访问，则返回值指示记录集内的未删除记录的总数。 若要强制进行访问的最后一个记录，请调用`MoveLast`或`FindLast`记录集的成员函数。 SQL 计数还可用于确定你的查询将返回的记录的大致数目。  
  
 你的应用程序删除记录集中的动态集类型记录的返回值`GetRecordCount`会降低。 但是，删除其他用户的记录不反映通过`GetRecordCount`直到当前记录位于到已删除的记录。 如果执行影响的记录计数的事务并随后回滚事务，`GetRecordCount`将不会反映剩余的记录的实际数目。  
  
 值`GetRecordCount`从快照类型记录集不受基础表中的更改。  
  
 值`GetRecordCount`从表类型记录集反映表中的记录的大致数目和添加和删除表记录时立即影响。  
  
 具有未记录的记录集返回值为 0。 使用附加的表或 ODBC 数据库时`GetRecordCount`始终返回-1。 调用**Requery**对记录集的成员函数的值重置`GetRecordCount`就像查询已重新执行。  
  
 有关相关信息，请参阅主题 DAO 帮助中的"RecordCount 属性"。  
  
##  <a name="getsql"></a>CDaoRecordset::GetSQL  
 调用此成员函数可获取用于选择记录集的记录已打开状态时的 SQL 语句。  
  
```  
CString GetSQL() const;  
```  
  
### <a name="return-value"></a>返回值  
 A`CString`包含 SQL 语句。  
  
### <a name="remarks"></a>备注  
 通常，这将是 SQL**选择**语句。  
  
 返回的字符串`GetSQL`通常不同于你可能会传递到记录集在任何字符串`lpszSQL`参数[打开](#open)成员函数。 这是因为该记录集构造一个完整的 SQL 语句，基于传递给**打开**ClassWizard，使用指定的内容，你可能具有指定的内容中[m_strFilter](#m_strfilter)和[m_strSort](#m_strsort)数据成员。  
  
> [!NOTE]
>  在调用后才调用此成员函数**打开**。  
  
 有关相关信息，请参阅主题 DAO 帮助中的"SQL 属性"。  
  
##  <a name="gettype"></a>CDaoRecordset::GetType  
 打开要确定记录集对象的类型的记录集后调用此成员函数。  
  
```  
short GetType();
```  
  
### <a name="return-value"></a>返回值  
 指示记录集的类型的以下值之一：  
  
- **dbOpenTable**表类型的记录集  
  
- **dbOpenDynaset**动态集类型的记录集  
  
- **dbOpenSnapshot**快照类型的记录集  
  
### <a name="remarks"></a>备注  
 有关相关信息，请参阅主题 DAO 帮助中的"类型属性"。  
  
##  <a name="getvalidationrule"></a>CDaoRecordset::GetValidationRule  
 调用此成员函数以确定用于验证数据的规则。  
  
```  
CString GetValidationRule();
```  
  
### <a name="return-value"></a>返回值  
 A`CString`对象，其中包含一个值，验证记录中的数据，因为它已更改或添加到表中。  
  
### <a name="remarks"></a>备注  
 此规则是基于文本的并且将应用每次更改基础表。 如果数据不是合法的则 MFC 会引发异常。 返回的错误消息是表达式的基础字段对象，如果指定，有效性文本属性的文本或由基础的字段对象的有效性规则属性指定的文本。 你可以调用[GetValidationText](#getvalidationtext)以获取错误消息的文本。  
  
 例如，需要每月的某一记录中的字段可能具有验证规则例如"天 BETWEEN 1 到 31。"  
  
 有关相关信息，请参阅主题 DAO 帮助中的"有效性规则属性"。  
  
##  <a name="getvalidationtext"></a>CDaoRecordset::GetValidationText  
 调用此成员函数可检索基础的字段对象的有效性文本属性的文本。  
  
```  
CString GetValidationText();
```  
  
### <a name="return-value"></a>返回值  
 A`CString`对象，其中包含的消息如果字段的值不符合验证规则的基础字段对象显示的文本。  
  
### <a name="remarks"></a>备注  
 有关相关信息，请参阅主题 DAO 帮助中的"有效性文本属性"。  
  
##  <a name="isbof"></a>CDaoRecordset::IsBOF  
 从记录滚动到记录以了解是否你进入之前记录集的第一条记录之前，请调用此成员函数。  
  
```  
BOOL IsBOF() const;  
```  
  
### <a name="return-value"></a>返回值  
 非零，如果记录集不包含任何记录，或具有第一个记录; 之前向后滚动否则为 0。  
  
### <a name="remarks"></a>备注  
 你还可以调用`IsBOF`连同`IsEOF`来确定记录集是否包含任何记录，或为空。 立即调用后**打开**，如果记录集不包含任何记录，`IsBOF`返回非零值。 打开一个包含至少一个记录记录集时，第一条记录是当前记录和`IsBOF`返回 0。  
  
 如果第一条记录的当前记录，并且你调用`MovePrev`，`IsBOF`随后将返回非零值。 如果`IsBOF`返回非零，并且你调用`MovePrev`，将引发异常。 如果`IsBOF`返回非零，当前记录是不确定，并且需要当前记录的任何操作会导致引发异常。  
  
 上的特定方法的效果`IsBOF`和`IsEOF`设置：  
  
-   调用**打开**内部通过可使第一条记录中记录集的当前记录调用**MoveFirst**。 因此，调用**打开**上记录的原因的空集`IsBOF`和`IsEOF`若要返回非零值。 (请参阅下表中的失败的行为**MoveFirst**或`MoveLast`调用。)  
  
-   已成功找到一条记录的所有移动操作会都导致同时`IsBOF`和`IsEOF`返回 0。  
  
-   `AddNew`调用跟**更新**成功插入一条新记录的调用将导致`IsBOF`返回 0，但仅当`IsEOF`已为非零值。 状态`IsEOF`将始终保持不变。 定义由 Microsoft Jet 数据库引擎，空的记录集的当前记录指针是在文件末尾，因此任何新记录插入后的当前记录。  
  
-   任何**删除**调用，即使从记录集的唯一的剩余记录中删除不会更改的值`IsBOF`或`IsEOF`。  
  
 下表显示哪些移动操作允许使用的不同组合`IsBOF` /  `IsEOF`。  
  
||MoveFirst MoveLast|MovePrev，<br /><br /> Move < 0|Move 0|MoveNext，<br /><br /> Move > 0|  
|------|-------------------------|-----------------------------|------------|-----------------------------|  
|`IsBOF`= 非零值，<br /><br /> `IsEOF`=0|Allowed|例外|例外|Allowed|  
|`IsBOF`=0,<br /><br /> `IsEOF`= 则为非 0|Allowed|Allowed|例外|例外|  
|同时则为非 0|例外|例外|例外|例外|  
|这两个 0|Allowed|Allowed|Allowed|Allowed|  
  
 允许在移动操作并不意味着该操作将成功找到一条记录。 它只是表示尝试执行指定的移动操作允许，不会生成异常。 值`IsBOF`和`IsEOF`成员函数可能会因所尝试的移动而更改。  
  
 找不到一条记录的值的移动操作的效果`IsBOF`和`IsEOF`下表中显示设置。  
  
||IsBOF|IsEOF|  
|------|-----------|-----------|  
|**MoveFirst**，`MoveLast`|非零|非零|  
|**移动**0|无更改|无更改|  
|`MovePrev`**移动**< 0|非零|无更改|  
|`MoveNext`**移动**> 0|无更改|非零|  
  
 有关相关信息，请参阅主题"BOF，EOF 属性"DAO 帮助中。  
  
##  <a name="isdeleted"></a>CDaoRecordset::IsDeleted  
 调用此成员函数可确定当前记录是否已被删除。  
  
```  
BOOL IsDeleted() const;  
```  
  
### <a name="return-value"></a>返回值  
 记录集放在已删除的记录; 如果非零否则为 0。  
  
### <a name="remarks"></a>备注  
 如果到一条记录滚动和`IsDeleted`返回**TRUE** （非零），然后你必须向下滚动到另一个记录才能执行记录集的任何其他操作。  
  
> [!NOTE]
>  你不需要检查记录集中的快照或表类型记录的已删除的状态。 因为无法从快照中删除记录，所以，并且无需调用`IsDeleted`。 为表类型的记录集，已删除的记录从记录集中实际上已删除。 后一条记录已被删除，由你、 其他用户时，或在另一个记录集，你不能向下滚动到相应的记录。 因此，没有无需调用`IsDeleted`。  
  
 当从动态集删除一条记录时，则会从记录集删除，你不能向下滚动到相应的记录。 但是，如果中的记录动态集删除由另一个用户或在另一个记录集对同一个表，基于`IsDeleted`将返回**TRUE**更高版本滚动时到相应的记录。  
  
 有关相关信息，请参阅"删除方法"、"上次更改时间属性"和 DAO 帮助中的"EditMode 属性"的主题。  
  
##  <a name="iseof"></a>CDaoRecordset::IsEOF  
 调用此成员函数，如从记录滚动到记录以了解是否你已超出最后一个记录集的记录。  
  
```  
BOOL IsEOF() const;  
```  
  
### <a name="return-value"></a>返回值  
 非零，如果记录集不包含任何记录，或已超出最后一条记录; 滚动否则为 0。  
  
### <a name="remarks"></a>备注  
 你还可以调用`IsEOF`来确定记录集是否包含任何记录，或为空。 立即调用后**打开**，如果记录集不包含任何记录，`IsEOF`返回非零值。 打开一个包含至少一个记录记录集时，第一条记录是当前记录和`IsEOF`返回 0。  
  
 在调用时如果最后一条记录是当前记录`MoveNext`，`IsEOF`随后将返回非零值。 如果`IsEOF`返回非零，并且你调用`MoveNext`，将引发异常。 如果`IsEOF`返回非零，当前记录是不确定，并且需要当前记录的任何操作会导致引发异常。  
  
 上的特定方法的效果`IsBOF`和`IsEOF`设置：  
  
-   调用**打开**内部通过可使第一条记录中记录集的当前记录调用**MoveFirst**。 因此，调用**打开**上记录的原因的空集`IsBOF`和`IsEOF`若要返回非零值。 (请参阅下表中的失败的行为**MoveFirst**调用。)  
  
-   已成功找到一条记录的所有移动操作会都导致同时`IsBOF`和`IsEOF`返回 0。  
  
-   `AddNew`调用跟**更新**成功插入一条新记录的调用将导致`IsBOF`返回 0，但仅当`IsEOF`已为非零值。 状态`IsEOF`将始终保持不变。 定义由 Microsoft Jet 数据库引擎，空的记录集的当前记录指针是在文件末尾，因此任何新记录插入后的当前记录。  
  
-   任何**删除**调用，即使从记录集的唯一的剩余记录中删除不会更改的值`IsBOF`或`IsEOF`。  
  
 下表显示哪些移动操作允许使用的不同组合`IsBOF` /  `IsEOF`。  
  
||MoveFirst MoveLast|MovePrev，<br /><br /> Move < 0|Move 0|MoveNext，<br /><br /> Move > 0|  
|------|-------------------------|-----------------------------|------------|-----------------------------|  
|`IsBOF`= 非零值，<br /><br /> `IsEOF`=0|Allowed|例外|例外|Allowed|  
|`IsBOF`=0,<br /><br /> `IsEOF`= 则为非 0|Allowed|Allowed|例外|例外|  
|同时则为非 0|例外|例外|例外|例外|  
|这两个 0|Allowed|Allowed|Allowed|Allowed|  
  
 允许在移动操作并不意味着该操作将成功找到一条记录。 它只是表示尝试执行指定的移动操作允许，不会生成异常。 值`IsBOF`和`IsEOF`成员函数可能会因所尝试的移动而更改。  
  
 找不到一条记录的值的移动操作的效果`IsBOF`和`IsEOF`下表中显示设置。  
  
||IsBOF|IsEOF|  
|------|-----------|-----------|  
|**MoveFirst**，`MoveLast`|非零|非零|  
|**移动**0|无更改|无更改|  
|`MovePrev`**移动**< 0|非零|无更改|  
|`MoveNext`**移动**> 0|无更改|非零|  
  
 有关相关信息，请参阅主题"BOF，EOF 属性"DAO 帮助中。  
  
##  <a name="isfielddirty"></a>CDaoRecordset::IsFieldDirty  
 调用此成员函数，以确定是否尚未标记为"脏"的指定的字段数据成员的动态集 （更改）。  
  
```  
BOOL IsFieldDirty(void* pv);
```  
  
### <a name="parameters"></a>参数  
 `pv`  
 指向字段数据成员你想要检查，其状态的指针或**NULL**以确定其中任何一个字段是否已更新。  
  
### <a name="return-value"></a>返回值  
 如果指定的字段数据成员标记为脏; 则为非 0否则为 0。  
  
### <a name="remarks"></a>备注  
 所有已更新字段数据成员中的数据将传输到记录在数据源上的当前记录更新通过调用时**更新**成员函数`CDaoRecordset`(到调用**编辑**或`AddNew`)。 了解这一点，你可能需要进一步的步骤，如取消标记以将标记列，以便它不会写到数据源的字段数据成员。  
  
 `IsFieldDirty`通过实现`DoFieldExchange`。  
  
##  <a name="isfieldnull"></a>CDaoRecordset::IsFieldNull  
 调用此成员函数来确定记录集的指定的字段数据成员是否已标记为 Null。  
  
```  
BOOL IsFieldNull(void* pv);
```  
  
### <a name="parameters"></a>参数  
 `pv`  
 指向字段数据成员你想要检查，其状态的指针或**NULL**以确定其中任何一个字段是否为 Null。  
  
### <a name="return-value"></a>返回值  
 如果指定的字段数据成员标记为 Null; 则为非 0否则为 0。  
  
### <a name="remarks"></a>备注  
 (在数据库术语中，Null 表示"having 没有值"，并且不能与相同**NULL** c + + 中。)如果字段数据成员标记为 Null，则将它解释为没有值的当前记录的列。  
  
> [!NOTE]
>  在某些情况下，使用`IsFieldNull`可能效率很低，如下面的代码示例所示：  
  
 [!code-cpp[NVC_MFCDatabase#5](../../mfc/codesnippet/cpp/cdaorecordset-class_5.cpp)]  
  
> [!NOTE]
>  如果使用动态记录绑定，但不使用派生自`CDaoRecordset`，请务必使用**VT_NULL**中示例所示。  
  
##  <a name="isfieldnullable"></a>CDaoRecordset::IsFieldNullable  
 调用以确定是否可以指定的字段数据成员为"null"（可以是设置为一个 Null 值; 如果该成员函数C + + **NULL**不同时，则为 Null，这在数据库术语中，意味着"having 没有值")。  
  
```  
BOOL IsFieldNullable(void* pv);
```  
  
### <a name="parameters"></a>参数  
 `pv`  
 指向字段数据成员你想要检查，其状态的指针或**NULL**以确定其中任何一个字段是否为 Null。  
  
### <a name="return-value"></a>返回值  
 非零，如果指定的字段数据成员可设置为 Null。否则为 0。  
  
### <a name="remarks"></a>备注  
 不能为 Null 的字段必须具有一个值。 如果你尝试将此类字段设置为 Null，在添加或更新记录时，数据源拒绝添加或更新，和**更新**将引发异常。 在调用时，则会发生异常**更新**，在调用时不`SetFieldNull`。  
  
##  <a name="isopen"></a>CDaoRecordset::IsOpen  
 调用此成员函数可确定记录集是否打开。  
  
```  
BOOL IsOpen() const;  
```  
  
### <a name="return-value"></a>返回值  
 非零如果记录集对象的**打开**或**Requery**以前调用成员函数和记录集未被关闭; 否则为 0。  
  
### <a name="remarks"></a>备注  
  
##  <a name="m_bcheckcachefordirtyfields"></a>Cdaorecordset:: M_bcheckcachefordirtyfields  
 包含一个标志，指示是否缓存的字段自动标记为脏页 （更改） 和 Null。  
  
### <a name="remarks"></a>备注  
 标志默认为**TRUE**。 此数据成员中的设置控制的整个双缓冲机制。 如果将标志设置为**TRUE**，你可以将关闭使用 DFX 机制的字段的基础上缓存。 如果将标志设置为**FALSE**，必须调用`SetFieldDirty`和`SetFieldNull`自己。  
  
 设置此数据成员之前调用**打开**。 此机制是主要用于易用性。 性能可能会降低由于双缓冲的字段进行更改时。  
  
##  <a name="m_nfields"></a>CDaoRecordset::m_nFields  
 包含记录集类中的字段数据成员的数目和选定数据源的记录集的列数。  
  
### <a name="remarks"></a>备注  
 记录集类的构造函数必须初始化`m_nFields`与正确的静态绑定的字段数。 时用于声明记录集类，ClassWizard 将写入此初始化时。 你还可以编写它手动。  
  
 框架将使用此数字管理字段数据成员与数据源上的当前记录的相应列之间的交互。  
  
> [!NOTE]
>  此数字必须与对应的注册中的输出列数`DoFieldExchange`后调用`SetFieldType`与参数**CDaoFieldExchange::outputColumn**。  
  
 你可以将列绑定动态的方式的`CDaoRecordset::GetFieldValue`和`CDaoRecordset::SetFieldValue`。 如果这样做，你不需要递增中的计数`m_nFields`以反映调用 DFX 函数次数你`DoFieldExchange`成员函数。  
  
##  <a name="m_nparams"></a>CDaoRecordset::m_nParams  
 包含的记录集类中的参数数据成员数-与记录集的查询一起传递的参数数目。  
  
### <a name="remarks"></a>备注  
 如果你记录集的类具有任何参数数据成员，必须初始化类的构造函数`m_nParams`与正确的数目。 值`m_nParams`默认值为 0。 如果添加的参数数据成员-你必须手动执行该操作 — 您必须在类构造函数，以反映参数的数目也手动添加初始化 (它必须是至少一样大的数字的形式 ' 中的占位符你**m_strFilter**或`m_strSort`字符串)。  
  
 它对参数化记录集的查询时，框架将使用此数字。  
  
> [!NOTE]
>  此数字必须与对应"params"中注册的数`DoFieldExchange`后调用`SetFieldType`与参数**CFieldExchange::param**。  
  
 有关相关信息，请参阅主题 DAO 帮助中的"参数对象"。  
  
##  <a name="m_pdaorecordset"></a>CDaoRecordset::m_pDAORecordset  
 包含指向 DAO 记录集对象基础的 OLE 接口的`CDaoRecordset`对象。  
  
### <a name="remarks"></a>备注  
 如果你需要直接访问 DAO 接口，请使用此指针。  
  
 有关相关信息，请参阅主题 DAO 帮助中的"记录集对象"。  
  
##  <a name="m_pdatabase"></a>CDaoRecordset::m_pDatabase  
 包含指向的`CDaoDatabase`通过该记录集连接到数据源的对象。  
  
### <a name="remarks"></a>备注  
 两种方式设置此变量。 通常情况下，将指针传递到已打开`CDaoDatabase`对象构造记录集对象时。 如果你通过**NULL**相反， **CDaoRecordset**创建`CDaoDatabase`为你的对象并将其打开。 在任一情况下，`CDaoRecordset`将指针存储在此变量。  
  
 通常不直接需要使用存储在指针**m_pDatabase**。 如果你编写自己的扩展到`CDaoRecordset`，但是，你可能需要使用该指针。 例如，你可能需要指针如果引发了自己`CDaoException`(s)。  
  
 有关相关信息，请参阅主题 DAO 帮助中的"数据库对象"。  
  
##  <a name="m_strfilter"></a>CDaoRecordset::m_strFilter  
 包含用于构造字符串**其中**SQL 语句子句。  
  
### <a name="remarks"></a>备注  
 它不包括保留的字**其中**来筛选记录集。 使用此数据成员不是适用于表类型记录集。 使用**m_strFilter**打开记录集使用时，不起`CDaoQueryDef`指针。  
  
 使用美国日期格式 （月-日-年） 时您筛选字段包含日期，即使未使用 Microsoft Jet 数据库引擎; 的美国版本否则，不可能按预期筛选数据。  
  
 有关相关信息，请参阅主题 DAO 帮助中的"筛选器属性"。  
  
##  <a name="m_strsort"></a>CDaoRecordset::m_strSort  
 包含一个字符串，包含**ORDERBY**而无需保留字的 SQL 语句子句**ORDERBY**。  
  
### <a name="remarks"></a>备注  
 你可以按动态集和快照类型记录集对象进行排序。  
  
 无法对表类型记录集对象进行排序。 若要确定表类型记录集的排序顺序，请调用[SetCurrentIndex](#setcurrentindex)。  
  
 使用`m_strSort`打开记录集使用时，不起`CDaoQueryDef`指针。  
  
 有关相关信息，请参阅主题 DAO 帮助中的"排序属性"。  
  
##  <a name="move"></a>CDaoRecordset::Move  
 调用此成员函数以定位该记录集`lRows`从当前记录的记录。  
  
```  
virtual void Move(long lRows);
```  
  
### <a name="parameters"></a>参数  
 `lRows`  
 要向前或向后移动的记录数。 正值表示向前，移动记录集的一端。 值为负时，开始向后移动。  
  
### <a name="remarks"></a>备注  
 您可以移动向前或向后。 `Move( 1 )`等效于`MoveNext`，和`Move( -1 )`等效于`MovePrev`。  
  
> [!CAUTION]
>  调用的任何**移动**函数将引发异常，如果记录集不具有任何记录。 一般情况下，请同时调用`IsBOF`和`IsEOF`之前移动操作，以确定是否记录集的任何记录。 调用后**打开**或**Requery**，调用`IsBOF`或`IsEOF`。  
  
> [!NOTE]
>  如果你使用滚动条滚动过去的开头或末尾的记录集 (`IsBOF`或`IsEOF`返回非零)，调用**移动**引发`CDaoException`。  
  
> [!NOTE]
>  如果你调用任意**移动**函数时的当前记录正在更新或添加，更新都将丢失而不发出警告。  
  
 当调用**移动**上只进滚动快照，`lRows`参数必须是一个正整数，书签不允许使用，因此你可以继续仅。  
  
 若要使第一个，最后，接下来，或上一个记录在记录集中的当前记录，调用**MoveFirst**， `MoveLast`， `MoveNext`，或`MovePrev`成员函数。  
  
 有关相关信息，请参阅主题"Move 方法"和"MoveFirst，MoveLast，MoveNext，MovePrevious 方法"DAO 帮助中。  
  
##  <a name="movefirst"></a>CDaoRecordset::MoveFirst  
 调用此成员函数要第一条记录中的记录集 （如果有） 的当前记录。  
  
```  
void MoveFirst();
```  
  
### <a name="remarks"></a>备注  
 无需调用**MoveFirst**后立即打开记录集。 此时，第一条记录 （如果有） 将自动当前记录。  
  
> [!CAUTION]
>  调用的任何**移动**函数将引发异常，如果记录集不具有任何记录。 一般情况下，请同时调用`IsBOF`和`IsEOF`之前移动操作，以确定是否记录集的任何记录。 调用后**打开**或**Requery**，调用`IsBOF`或`IsEOF`。  
  
> [!NOTE]
>  如果你调用任意**移动**函数时的当前记录正在更新或添加，更新都将丢失而不发出警告。  
  
 使用**移动**记录之间移动而不应用条件的函数。 使用查找操作查找记录中的动态集类型或满足特定条件的快照类型的记录集对象。 若要在一个表类型记录集对象中查找一条记录，调用`Seek`。  
  
 如果记录集引用的表类型记录集，则移动遵循表的当前索引。 可以通过使用基础的 DAO 对象的索引属性设置的当前索引。 如果未设置的当前索引，则返回的记录的顺序不确定。  
  
 如果调用`MoveLast`对基于 SQL 查询或 querydef 记录集对象，该查询强制完成并完全填充的记录集对象。  
  
 不能调用**MoveFirst**或`MovePrev`成员函数时只进的滚动快照。  
  
 若要移动特定条记录向前或向后记录集对象中记录当前的位置，调用**移动**。  
  
 有关相关信息，请参阅主题"Move 方法"和"MoveFirst，MoveLast，MoveNext，MovePrevious 方法"DAO 帮助中。  
  
##  <a name="movelast"></a>CDaoRecordset::MoveLast  
 在记录集中的当前记录调用此成员函数，以使最后一条记录 （如果有）。  
  
```  
void MoveLast();
```  
  
### <a name="remarks"></a>备注  
  
> [!CAUTION]
>  调用的任何**移动**函数将引发异常，如果记录集不具有任何记录。 一般情况下，请同时调用`IsBOF`和`IsEOF`之前移动操作，以确定是否记录集的任何记录。 调用后**打开**或**Requery**，调用`IsBOF`或`IsEOF`。  
  
> [!NOTE]
>  如果你调用任意**移动**函数时的当前记录正在更新或添加，更新都将丢失而不发出警告。  
  
 使用**移动**记录之间移动而不应用条件的函数。 使用查找操作查找记录中的动态集类型或满足特定条件的快照类型的记录集对象。 若要在一个表类型记录集对象中查找一条记录，调用`Seek`。  
  
 如果记录集引用的表类型记录集，则移动遵循表的当前索引。 可以通过使用基础的 DAO 对象的索引属性设置的当前索引。 如果未设置的当前索引，则返回的记录的顺序不确定。  
  
 如果调用`MoveLast`对基于 SQL 查询或 querydef 记录集对象，该查询强制完成并完全填充的记录集对象。  
  
 若要移动特定条记录向前或向后记录集对象中记录当前的位置，调用**移动**。  
  
 有关相关信息，请参阅主题"Move 方法"和"MoveFirst，MoveLast，MoveNext，MovePrevious 方法"DAO 帮助中。  
  
##  <a name="movenext"></a>CDaoRecordset::MoveNext  
 调用此成员函数以使记录集的当前记录中的下一步的记录。  
  
```  
void MoveNext();
```  
  
### <a name="remarks"></a>备注  
 建议您调用`IsBOF`尝试将移到上一条记录之前。 调用`MovePrev`将引发`CDaoException`如果`IsBOF`返回非零值，指示，你已使用滚动条滚动在第一条记录之前或没有记录已选择的记录集。  
  
> [!CAUTION]
>  调用的任何**移动**函数将引发异常，如果记录集不具有任何记录。 一般情况下，请同时调用`IsBOF`和`IsEOF`之前移动操作，以确定是否记录集的任何记录。 调用后**打开**或**Requery**，调用`IsBOF`或`IsEOF`。  
  
> [!NOTE]
>  如果你调用任意**移动**函数时的当前记录正在更新或添加，更新都将丢失而不发出警告。  
  
 使用**移动**记录之间移动而不应用条件的函数。 使用查找操作查找记录中的动态集类型或满足特定条件的快照类型的记录集对象。 若要在一个表类型记录集对象中查找一条记录，调用`Seek`。  
  
 如果记录集引用的表类型记录集，则移动遵循表的当前索引。 可以通过使用基础的 DAO 对象的索引属性设置的当前索引。 如果未设置的当前索引，则返回的记录的顺序不确定。  
  
 若要移动特定条记录向前或向后记录集对象中记录当前的位置，调用**移动**。  
  
 有关相关信息，请参阅主题"Move 方法"和"MoveFirst，MoveLast，MoveNext，MovePrevious 方法"DAO 帮助中。  
  
##  <a name="moveprev"></a>CDaoRecordset::MovePrev  
 调用此成员函数，使上一记录中记录集的当前记录。  
  
```  
void MovePrev();
```  
  
### <a name="remarks"></a>备注  
 建议您调用`IsBOF`尝试将移到上一条记录之前。 调用`MovePrev`将引发`CDaoException`如果`IsBOF`返回非零值，指示，你已使用滚动条滚动在第一条记录之前或没有记录已选择的记录集。  
  
> [!CAUTION]
>  调用的任何**移动**函数将引发异常，如果记录集不具有任何记录。 一般情况下，请同时调用`IsBOF`和`IsEOF`之前移动操作，以确定是否记录集的任何记录。 调用后**打开**或**Requery**，调用`IsBOF`或`IsEOF`。  
  
> [!NOTE]
>  如果你调用任意**移动**函数时的当前记录正在更新或添加，更新都将丢失而不发出警告。  
  
 使用**移动**记录之间移动而不应用条件的函数。 使用查找操作查找记录中的动态集类型或满足特定条件的快照类型的记录集对象。 若要在一个表类型记录集对象中查找一条记录，调用`Seek`。  
  
 如果记录集引用的表类型记录集，则移动遵循表的当前索引。 可以通过使用基础的 DAO 对象的索引属性设置的当前索引。 如果未设置的当前索引，则返回的记录的顺序不确定。  
  
 不能调用**MoveFirst**或`MovePrev`成员函数时只进的滚动快照。  
  
 若要移动特定条记录向前或向后记录集对象中记录当前的位置，调用**移动**。  
  
 有关相关信息，请参阅主题"Move 方法"和"MoveFirst，MoveLast，MoveNext，MovePrevious 方法"DAO 帮助中。  
  
##  <a name="open"></a>Cdaorecordset:: Open  
 必须调用该成员函数以检索记录集的记录。  
  
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
 `nOpenType`  
 以下值之一：  
  
- **dbOpenDynaset**具有双向滚动的动态集类型记录集。 这是默认设置。  
  
- **dbOpenTable**具有双向滚动的表类型记录集。  
  
- **dbOpenSnapshot**而双向滚动快照类型的记录集。  
  
 `lpszSQL`  
 字符串指针，包含以下项之一：  
  
-   A **NULL**指针。  
  
-   一个或多个 tabledefs 和/或 querydefs （以逗号分隔） 的名称。  
  
-   SQL**选择**语句 (根据需要使用 SQL**其中**或**ORDERBY**子句)。  
  
-   传递的查询。  
  
 `nOptions`  
 一个或多个下面列出的选项。 默认值为 0。 可能的值如下：  
  
- **dbAppendOnly**可以仅追加新记录 （仅记录动态集类型集）。 此选项的字面意思是，可能仅追加记录。 MFC ODBC 数据库类具有一个允许检索和追加的记录的仅限附加的选项。  
  
- **dbForwardOnly**记录集是只进滚动快照。  
  
- **dbSeeChanges**如果另一个用户正在更改正在编辑的数据生成异常。  
  
- **dbDenyWrite**其他用户不能修改或添加记录。  
  
- **dbDenyRead**其他用户无法查看记录 （仅记录的表类型集）。  
  
- **dbReadOnly**你只可以查看记录; 其他用户可以修改它们。  
  
- **dbInconsistent** （仅记录动态集类型集） 允许不一致的更新。  
  
- **dbConsistent**仅允许一致的更新 （仅记录动态集类型集）。  
  
> [!NOTE]
>  常量**dbConsistent**和**dbInconsistent**是互相排斥。 你可以使用一个或另一个，但不要同时中的给定实例**打开**。  
  
 *pTableDef*  
 指向的指针[CDaoTableDef](../../mfc/reference/cdaotabledef-class.md)对象。 此版本是仅对表类型记录集有效。 使用此选项时`CDaoDatabase`指针用于构造`CDaoRecordset`未使用; 相反，将使用 tabledef 所在的数据库。  
  
 *pQueryDef*  
 指向的指针[CDaoQueryDef](../../mfc/reference/cdaoquerydef-class.md)对象。 此版本是仅对动态集类型和快照类型记录集有效。 使用此选项时`CDaoDatabase`指针用于构造`CDaoRecordset`未使用; 相反，将使用此 querydef 所在的数据库。  
  
### <a name="remarks"></a>备注  
 之前调用**打开**，您必须先构造的记录集对象。 有若干方法可实现此操作：  
  
-   如果你构造的记录集对象，将传递指向的指针`CDaoDatabase`已打开的对象。  
  
-   如果你构造的记录集对象，将传递指向的指针`CDaoDatabase`未打开的对象。 记录集打开`CDaoDatabase`对象，但不是会关闭它，记录集对象关闭时。  
  
-   如果你构造的记录集对象，则将传递**NULL**指针。 记录集对象调用`GetDefaultDBName`若要获取的 Microsoft Access 的名称。要打开的 MDB 文件。 记录集然后打开`CDaoDatabase`对象并使它打开，只要记录集处于打开状态。 当调用**关闭**对记录集，`CDaoDatabase`对象也将关闭。  
  
    > [!NOTE]
    >  记录集打开时`CDaoDatabase`对象，它以非独占方式访问以打开数据源。  
  
 版本的**打开**使用`lpszSQL`参数，记录集处于打开状态后你可以检索几种方式之一中的记录。 第一个选项是在中拥有 DFX 函数你`DoFieldExchange`。 第二个选项是通过调用使用动态绑定`GetFieldValue`成员函数。 单独或组合，可以实现这些选项。 如果合并，你将需要传递的 SQL 语句中自行调用**打开**。  
  
 如果你使用的第二个版本**打开**你传入`CDaoTableDef`对象，生成的列将可供你可通过将绑定`DoFieldExchange`和 DFX 机制，和/或动态通过绑定`GetFieldValue`。  
  
> [!NOTE]
>  你只能调用**打开**使用`CDaoTableDef`表类型记录集的对象。  
  
 如果你使用的第三个版本**打开**你传入`CDaoQueryDef`对象，将执行查询，并生成的列将可供你可通过将绑定`DoFieldExchange`和 DFX 机制，和/或动态绑定通过`GetFieldValue`。  
  
> [!NOTE]
>  你只能调用**打开**使用`CDaoQueryDef`动态集类型和快照类型记录集对象。  
  
 第一个版本的**打开**使用`lpszSQL`参数，记录则下表中所示的所选基于的条件。  
  
|`lpszSQL` 参数的值|由确定所选记录|示例|  
|--------------------------------------|----------------------------------------|-------------|  
|**NULL**|返回的字符串`GetDefaultSQL`。||  
|以逗号分隔的一个或多个 tabledefs 和/或 querydef 名称列表。|在中的所有列都表示`DoFieldExchange`。|`"Customer"`|  
|**选择**列列表**FROM**表列表|从指定的 tabledef(s) 和/或 querydef(s) 指定的列。|`"SELECT CustId, CustName`<br /><br /> `FROM Customer"`|  
  
 常规步骤是将传递**NULL**到**打开**; 在这种情况下，**打开**调用`GetDefaultSQL`，ClassWizard 生成时创建的可重写成员函数`CDaoRecordset`-派生类。 此值使你在 ClassWizard 中指定的 tabledef(s) 和/或 querydef 名称。 您可以指定中的其他信息`lpszSQL`参数。  
  
 你传递的任何**打开**构造查询的最终 SQL 字符串 (字符串可能具有 SQL**其中**和**ORDERBY**子句追加到`lpszSQL`字符串传入） 和执行该查询。 你可以通过调用检查构造的字符串`GetSQL`之后调用**打开**。  
  
 记录集类的字段数据成员将绑定到所选的数据的列。 如果返回任何记录，第一条记录成为当前记录。  
  
 如果你想要设置为记录集，如筛选或排序，选项设置`m_strSort`或**m_strFilter**构造的记录集对象之后但在调用之前**打开**。 如果你想要刷新的记录后记录集中的记录集已打开，请调用**Requery**。  
  
 如果调用**打开**上动态集类型或快照类型的记录集，或者如果数据源引用的 SQL 语句或 tabledef 对象，表示附加的表，不能使用**dbOpenTable**类型自变量;如果这样做，则 MFC 会引发异常。 若要确定 tabledef 对象是否表示附加的表，创建[CDaoTableDef](../../mfc/reference/cdaotabledef-class.md)对象并调用其[GetConnect](../../mfc/reference/cdaotabledef-class.md#getconnect)成员函数。  
  
 使用**dbSeeChanges**标志如果你想要捕获编辑或删除同一记录时，由另一个用户或计算机上的另一个程序所做的更改。 例如，如果两个用户开始编辑同一个记录，若要调用的第一个用户**更新**成员函数成功。 当**更新**由第二个用户，调用`CDaoException`引发。 同样，如果第二个用户尝试调用**删除**删除记录，并已更改第一个用户，通过`CDaoException`时发生。  
  
 通常情况下，如果用户获取此`CDaoException`更新时，你的代码应刷新字段的内容和检索最近修改的值。 如果删除的过程中发生异常，你的代码无法向用户和一条消息指出的数据已最近更改显示新的记录数据。 此时，你的代码可以请求用户仍想要删除的记录一条确认消息。  
  
> [!TIP]
>  使用只进滚动选项 ( **dbForwardOnly**) 以提高性能，当你的应用程序进行单个传递通过记录集打开从 ODBC 数据源。  
  
 有关相关信息，请参阅主题 DAO 帮助中的"OpenRecordset 方法"。  
  
##  <a name="requery"></a>CDaoRecordset::Requery  
 调用此成员函数以重新生成 （刷新） 记录集。  
  
```  
virtual void Requery();
```  
  
### <a name="remarks"></a>备注  
 如果返回任何记录，第一条记录成为当前记录。  
  
 为了使为反映的添加和删除您或其他用户对数据源的记录集，必须重新记录集生成通过调用**Requery**。 如果记录集是动态集，它会自动反映你或其他用户对其现有记录 （但不是添加件） 进行的更新。 如果记录集是快照，则必须调用**Requery**以反映编辑由其他用户，以及添加和删除。  
  
 对于动态集或快照中，调用**Requery**任何你想要重新生成使用参数值的记录集的时间。 通过设置来设置新的筛选器或排序[m_strFilter](#m_strfilter)和[m_strSort](#m_strsort)之前调用**Requery**。 通过将新值分配给之前调用的参数数据成员设置新的参数**Requery**。  
  
 如果重新生成该记录集的尝试失败，已关闭记录集。 在调用之前**Requery**，你可以确定是否可以通过调用重新记录集的查询[CanRestart](#canrestart)成员函数。 `CanRestart`不能保证**Requery**将会成功。  
  
> [!CAUTION]
>  调用**Requery**仅具有调用后**打开**。  
  
> [!NOTE]
>  调用[Requery](#requery)更改 DAO 书签。  
  
 不能调用**Requery**动态集类型或快照类型的记录集如果调用上`CanRestart`返回 0，也无法使用它在表类型记录集上。  
  
 如果这两个`IsBOF`和`IsEOF`后你调用返回非零**Requery**，查询未返回任何记录和记录集将包含任何数据。  
  
 有关相关信息，请参阅主题 DAO 帮助中的"Requery 方法"。  
  
##  <a name="seek"></a>CDaoRecordset::Seek  
 调用此成员函数以满足指定的条件的当前索引，并确保记录当前记录索引的表类型记录集对象中找到的记录。  
  
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
 `lpszComparison`  
 以下字符串表达式之一:"<"、"\<="，"="、"> ="，或">"。  
  
 `pKey1`  
 指向的指针[COleVariant](../../mfc/reference/colevariant-class.md)其值对应于索引中的第一个字段。 必须的。  
  
 *pKey2*  
 指向的指针`COleVariant`其值对应于第二个字段在索引中，如果有的话。 默认为**NULL**。  
  
 *pKey3*  
 指向的指针`COleVariant`其值对应于第三个字段在索引中，如果有的话。 默认为**NULL**。  
  
 *pKeyArray*  
 指向 variant 数组的指针。 数组大小对应于索引中的字段数。  
  
 *nKeys*  
 对应于数组，它是在索引中的字段数的大小的整数。  
  
> [!NOTE]
>  不要在项中指定通配符。 通配符将导致`Seek`返回相匹配的记录。  
  
### <a name="return-value"></a>返回值  
 如果找到匹配的记录，否则为 0，则为非 0。  
  
### <a name="remarks"></a>备注  
 使用第二个 （数组） 版本`Seek`要处理的四个字段的索引或以上。  
  
 `Seek`使搜索表类型记录集上的高性能索引。 必须通过调用设置的当前索引`SetCurrentIndex`之前调用`Seek`。 如果索引标识了非唯一的键字段或字段，`Seek`查找满足的条件的第一个记录。 如果未设置索引，将引发异常。  
  
 请注意，如果你不在创建 UNICODE 记录集，则`COleVariant`对象必须显式声明 ANSI。 这可以通过使用[COleVariant::COleVariant](../../mfc/reference/colevariant-class.md#colevariant)**(** `lpszSrc` **，** `vtSrc` **)**窗体的构造函数与`vtSrc`设置为`VT_BSTRT`(ANSI) 或通过使用**COleVariant**函数[SetString](../../mfc/reference/colevariant-class.md#setstring)**(** `lpszSrc` **，** `vtSrc` **)**与`vtSrc`设置为`VT_BSTRT`。  
  
 当调用`Seek`，你将一个或多个密钥值和比较运算符传递 ("<"、"\<="，"="、"> ="，或">")。 `Seek`搜索指定的键字段，并找到满足指定的条件的第一个记录`lpszComparison`和`pKey1`。 一次找到，`Seek`返回非零值，并将该记录当前。 如果`Seek`无法找到匹配项，`Seek`返回零，而且当前记录是不确定。 当直接使用 DAO，则必须显示检查 NoMatch 属性。  
  
 如果`lpszComparison`"=""> ="，或">"，`Seek`开始的索引开始。 如果`lpszComparison`是"<"或"< ="，`Seek`开始索引末尾、 向后搜索，除非末尾有重复的索引条目。 在这种情况下，`Seek`从索引末尾重复的索引条目中的任意项开始。  
  
 那里没有为当前记录，当你使用`Seek`。  
  
 若要查找动态集类型或满足特定条件的快照类型记录集中的记录，请使用查找操作。 若要包含的所有记录，而不仅仅是那些满足特定条件，用于移动操作记录之间移动。  
  
 不能调用`Seek`上附加任何的表类型，因为必须作为动态集类型或快照类型记录集打开附加的表。 但是，如果调用`CDaoDatabase::Open`若要直接打开可安装的 ISAM 数据库，可以调用`Seek`表在该数据库中，尽管性能可能会降低。  
  
 有关相关信息，请参阅主题 DAO 帮助中的"查找方法"。  
  
##  <a name="setabsoluteposition"></a>CDaoRecordset::SetAbsolutePosition  
 设置记录集对象的当前记录的相对的记录数。  
  
```  
void SetAbsolutePosition(long lPosition);
```  
  
### <a name="parameters"></a>参数  
 *lPosition*  
 对应于记录集中的当前记录的序号位置。  
  
### <a name="remarks"></a>备注  
 调用`SetAbsolutePosition`使您能够将当前记录指针定位到特定记录根据其动态集类型或快照类型记录集中的序号位置。 您还可以通过调用来确定当前记录号[GetAbsolutePosition](#getabsoluteposition)。  
  
> [!NOTE]
>  此成员函数是仅对动态集类型和快照类型记录集有效。  
  
 基础的 DAO 对象的 AbsolutePosition 属性值是从零开始;设置为 0 是指在记录集中的第一个记录。 设置一个值大于填充的记录原因 MFC 引发异常数。 可以通过调用中确定的记录集填充记录数`GetRecordCount`成员函数。  
  
 如果删除该当前记录，不定义 AbsolutePosition 属性值，并且如果正在引用则 MFC 会引发异常。 新记录添加到序列的末尾。  
  
> [!NOTE]
>  此属性不应作为代理项记录编号。 仍然建议书签保留并返回到给定位置，而且这是在所有类型的支持书签的记录集对象之间定位当前记录的唯一方式。 具体而言，当其前面的记录将被删除时，将更改给定的记录的位置。 此外还有，给定的记录将具有相同的绝对位置，如果重新因为不能保证在记录集内的单个记录的顺序，除非它使用 SQL 语句中使用创建再次创建记录集不保证**ORDERBY**子句。  
  
 有关相关信息，请参阅主题 DAO 帮助中的"AbsolutePosition 属性"。  
  
##  <a name="setbookmark"></a>CDaoRecordset::SetBookmark  
 调用此成员函数可置于包含指定的书签记录的记录集。  
  
```  
void SetBookmark(COleVariant varBookmark);
```  
  
### <a name="parameters"></a>参数  
 `varBookmark`  
 A [COleVariant](../../mfc/reference/colevariant-class.md)包含特定记录的书签值对象。  
  
### <a name="remarks"></a>备注  
 创建或打开记录集对象后，每个其记录已有一个唯一的书签。 你可以通过调用来检索当前记录的书签`GetBookmark`和保存到的值`COleVariant`对象。 更高版本可以通过调用返回到该记录`SetBookmark`使用已保存的书签值。  
  
> [!NOTE]
>  调用[Requery](#requery)更改 DAO 书签。  
  
 请注意，如果你不在创建 UNICODE 记录集，则`COleVariant`对象必须显式声明 ANSI。 这可以通过使用[COleVariant::COleVariant](../../mfc/reference/colevariant-class.md#colevariant)**(** `lpszSrc` **，** `vtSrc` **)**窗体的构造函数与`vtSrc`设置为`VT_BSTRT`(ANSI) 或通过使用**COleVariant**函数[SetString](../../mfc/reference/colevariant-class.md#setstring)**(** `lpszSrc` **，** `vtSrc` **)**与`vtSrc`设置为`VT_BSTRT`。  
  
 有关相关信息，请参阅"书签属性"和 Bookmarkable 属性的主题"DAO 帮助中。  
  
##  <a name="setcachesize"></a>CDaoRecordset::SetCacheSize  
 调用此成员函数可设置要缓存的记录数。  
  
```  
void SetCacheSize(long lSize);
```  
  
### <a name="parameters"></a>参数  
 `lSize`  
 指定记录的数。 一个典型值为 100。 设置为 0 表示关闭缓存。 设置必须介于 5 和 1200年记录。 缓存可能会使用相当多的内存。  
  
### <a name="remarks"></a>备注  
 缓存在本地保存最近的事件中运行应用程序时将再次请求数据从服务器检索的数据的内存空间。 数据缓存提高从通过动态集类型记录集对象的远程服务器中检索数据的应用程序的性能。 请求数据时，Microsoft Jet 数据库引擎所请求数据的缓存会首先检查而不是检索在服务器上，这需要花费更多的时间。 不是来自 ODBC 数据源的数据不保存在缓存中。  
  
 任何 ODBC 数据源，例如一个附加的表，可以本地缓存。 若要创建缓存，可从远程数据源，调用打开记录集对象`SetCacheSize`和`SetCacheStart`成员函数，然后调用`FillCache`成员函数或逐句通过移动操作的记录。 `lSize`参数`SetCacheSize`成员函数可以基于你的应用程序可以使用一次的记录数。 例如，如果你使用记录集作为数据源显示在屏幕上，你可以将`SetCacheSize``lSize`参数作为 20 以一次显示 20 的记录。  
  
 有关相关信息，请参阅 DAO 帮助中的主题"CacheSize，CacheStart 属性"。  
  
##  <a name="setcachestart"></a>CDaoRecordset::SetCacheStart  
 调用此成员函数可在记录集缓存中指定的第一条记录的书签。  
  
```  
void SetCacheStart(COleVariant varBookmark);
```  
  
### <a name="parameters"></a>参数  
 `varBookmark`  
 A [COleVariant](../../mfc/reference/colevariant-class.md) ，它指定的第一条记录书签中为缓存的记录集。  
  
### <a name="remarks"></a>备注  
 你可以使用任何记录书签值`varBookmark`参数`SetCacheStart`成员函数。 使你想要与当前记录启动缓存，建立该记录使用的书签的记录[SetBookmark](#setbookmark)，并将书签值作为参数传递`SetCacheStart`成员函数。  
  
 Microsoft Jet 数据库引擎从缓存中，请求缓存范围内的记录并从服务器请求到的缓存范围外的记录。  
  
 从缓存中检索的记录不能反映其他用户对源数据同时进行的更改。  
  
 若要强制所有缓存的数据更新，请将传递`lSize`参数`SetCacheSize`为 0，调用`SetCacheSize`再次缓存的大小与你最初请求，，然后调用`FillCache`成员函数。  
  
 请注意，如果你不在创建 UNICODE 记录集，则`COleVariant`对象必须显式声明 ANSI。 这可以通过使用[COleVariant::COleVariant](../../mfc/reference/colevariant-class.md#colevariant)**(** `lpszSrc` **，** `vtSrc` **)**窗体的构造函数与`vtSrc`设置为`VT_BSTRT`(ANSI) 或通过使用**COleVariant**函数[SetString](../../mfc/reference/colevariant-class.md#setstring)**(** `lpszSrc` **，** `vtSrc` **)**与`vtSrc`设置为`VT_BSTRT`。  
  
 有关相关信息，请参阅主题 CacheSize，CacheStart 属性 DAO 帮助中。  
  
##  <a name="setcurrentindex"></a>CDaoRecordset::SetCurrentIndex  
 调用此成员函数以在表类型记录集上设置索引。  
  
```  
void SetCurrentIndex(LPCTSTR lpszIndex);
```  
  
### <a name="parameters"></a>参数  
 `lpszIndex`  
 一个指针，它包含要设置的索引的名称。  
  
### <a name="remarks"></a>备注  
 基表中的记录不存储在任何特定的顺序。 设置索引更改从数据库中返回的记录的顺序，但它不会影响的记录存储的顺序。 必须已定义指定的索引。 如果你尝试使用索引对象不存在，或如果在调用时，不设置索引[Seek](#seek)，则 MFC 会引发异常。  
  
 你可以通过调用创建新的索引的表[CDaoTableDef::CreateIndex](../../mfc/reference/cdaotabledef-class.md#createindex)并将新的索引追加到基础 tabledef 索引集合中，通过调用[CDaoTableDef::Append](../../mfc/reference/cdaotabledef-class.md#append)，和然后重新打开记录集。  
  
 从表类型记录集返回的记录可仅通过为基础 tabledef 定义的索引进行排序。 若要对其他顺序排序的记录进行排序，可以打开动态集类型或快照类型记录集使用的 SQL **ORDERBY**子句存储在[CDaoRecordset::m_strSort](#m_strsort)。  
  
 有关相关信息，请参阅主题"索引对象"，并定义 DAO 帮助中的"当前索引"。  
  
##  <a name="setfielddirty"></a>CDaoRecordset::SetFieldDirty  
 调用此成员函数来标记的字段数据成员的记录集持久化为已更改或为不变。  
  
```  
void SetFieldDirty(
    void* pv,  
    BOOL bDirty = TRUE);
```  
  
### <a name="parameters"></a>参数  
 `pv`  
 包含在记录集中的字段数据成员的地址或**NULL**。 如果**NULL**，标记在记录集中的所有字段数据成员。 (C + + **NULL**不同时，为 Null，在数据库术语中，这意味着"having 没有值。")  
  
 `bDirty`  
 **TRUE**字段数据成员是否会被标记为"脏"（更改）。 否则为**FALSE**字段数据成员是否会被标记为"清理"（未更改）。  
  
### <a name="remarks"></a>备注  
 将标记为未更改的字段，可确保该字段不会更新。  
  
 Framework 标记更改字段数据成员，以确保它们要写入到数据源上的记录由 DAO 记录字段交换 (DFX) 机制。 更改字段的值通常设置为字段脏自动，因此你将很少需要调用`SetFieldDirty`你自己，但你有时可能想要确保，列将显式更新或插入而不考虑哪些值处于字段数据成员。 DFX 机制还使用了使用**PSEUDONULL**。 有关详细信息，请参阅[CDaoFieldExchange::m_nOperation](../../mfc/reference/cdaofieldexchange-class.md#m_noperation)。  
  
 如果未使用双缓冲机制，然后将更改字段的值不会不自动将字段设置为脏。 在这种情况下，将需要显式将字段设置为脏。 中包含的标志[m_bCheckCacheForDirtyFields](#m_bcheckcachefordirtyfields)控制此自动字段检查。  
  
> [!NOTE]
>  只有具有调用之后才调用此成员函数[编辑](#edit)或[AddNew](#addnew)。  
  
 使用**NULL**函数的第一个参数将函数应用到所有**outputColumn**字段，不**param**中的字段`CDaoFieldExchange`。 例如，调用  
  
 [!code-cpp[NVC_MFCDatabase#6](../../mfc/codesnippet/cpp/cdaorecordset-class_6.cpp)]  
  
 将仅设置**outputColumn**字段设置为**NULL**;**param**字段不会受到影响。  
  
 若要在**param**，你必须提供个人的实际地址**param**你想要使用，如：  
  
 [!code-cpp[NVC_MFCDatabase#7](../../mfc/codesnippet/cpp/cdaorecordset-class_7.cpp)]  
  
 这意味着您不能设置所有**param**字段设置为**NULL**，如可以按照与**outputColumn**字段。  
  
 `SetFieldDirty`通过实现`DoFieldExchange`。  
  
##  <a name="setfieldnull"></a>CDaoRecordset::SetFieldNull  
 调用此成员函数来标记的字段数据成员的记录集为 Null （专门具有任何值） 或为非 Null。  
  
```  
void SetFieldNull(
    void* pv,  
    BOOL bNull = TRUE);
```  
  
### <a name="parameters"></a>参数  
 `pv`  
 包含在记录集中的字段数据成员的地址或**NULL**。 如果**NULL**，标记在记录集中的所有字段数据成员。 (C + + **NULL**不同时，为 Null，在数据库术语中，这意味着"having 没有值。")  
  
 `bNull`  
 如果字段数据成员均被标记为不具有任何值 (Null)，则为非 0。 如果字段数据成员是被标记为非 Null 则否则为 0。  
  
### <a name="remarks"></a>备注  
 `SetFieldNull`用于绑定中的字段，`DoFieldExchange`机制。  
  
 当你将一条新记录添加到记录集时，所有字段数据成员最初设置为 Null 值的并标记为"脏"（更改）。 当从数据源检索一条记录时，其列已具有值，或者为 Null。 如果不合适，若要使字段为 Null， [CDaoException](../../mfc/reference/cdaoexception-class.md)引发。  
  
 如果你使用双缓冲机制，例如，如果你明确想要将当前记录的字段指定为不具有一个值，调用`SetFieldNull`与`bNull`设置为**TRUE**标记为 Null。 如果字段以前已标记为 Null，并且现在想要为其提供一个值，只需将其新值设置。 不需要删除与 Null 标志`SetFieldNull`。 若要确定是否允许该字段为 Null，调用[IsFieldNullable](#isfieldnullable)。  
  
 如果你未使用双缓冲机制，然后将更改字段的值不会自动设置字段作为脏和非 Null。 具体而言，必须设置字段，脏和非 Null。 中包含的标志[m_bCheckCacheForDirtyFields](#m_bcheckcachefordirtyfields)控制此自动字段检查。  
  
 DFX 机制采用使用**PSEUDONULL**。 有关详细信息，请参阅[CDaoFieldExchange::m_nOperation](../../mfc/reference/cdaofieldexchange-class.md#m_noperation)。  
  
> [!NOTE]
>  只有具有调用之后才调用此成员函数[编辑](#edit)或[AddNew](#addnew)。  
  
 使用**NULL**为函数的第一个参数将该函数仅适用于**outputColumn**字段，不**param**中的字段`CDaoFieldExchange`。 例如，调用  
  
 [!code-cpp[NVC_MFCDatabase#8](../../mfc/codesnippet/cpp/cdaorecordset-class_8.cpp)]  
  
 将仅设置**outputColumn**字段设置为**NULL**;**param**字段不会受到影响。  
  
##  <a name="setfieldvalue"></a>CDaoRecordset::SetFieldValue  
 调用此成员函数以设置字段的值，按序号位置或通过更改字符串的值。  
  
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
 `lpszName`  
 指向包含的字段名称的字符串的指针。  
  
 `varValue`  
 对引用[COleVariant](../../mfc/reference/colevariant-class.md)对象包含的值的字段的内容。  
  
 `nIndex`  
 一个整数，表示记录集的字段集合 （从零开始） 中的字段的序号位置。  
  
 `lpszValue`  
 指向包含该字段的内容的值的字符串的指针。  
  
### <a name="remarks"></a>备注  
 使用`SetFieldValue`和[GetFieldValue](#getfieldvalue)将字段动态绑定在运行的时而不是静态绑定列使用[DoFieldExchange](#dofieldexchange)机制。  
  
 请注意，是否你不在创建 UNICODE 记录集，你必须使用一种形式的`SetFieldValue`不包含`COleVariant`参数，或`COleVariant`对象必须显式声明 ANSI。 这可以通过使用[COleVariant::COleVariant](../../mfc/reference/colevariant-class.md#colevariant)**(** `lpszSrc` **，** `vtSrc` **)**窗体的构造函数与`vtSrc`设置为`VT_BSTRT`(ANSI) 或通过使用**COleVariant**函数[SetString](../../mfc/reference/colevariant-class.md#setstring)**(** `lpszSrc` **，** `vtSrc` **)**与`vtSrc`设置为`VT_BSTRT`。  
  
 有关相关信息，请参阅"字段对象"和"值属性"DAO 帮助中的主题。  
  
##  <a name="setfieldvaluenull"></a>CDaoRecordset::SetFieldValueNull  
 调用此成员函数可将字段设置为 Null 值。  
  
```  
void SetFieldValueNull(int nIndex);  
void SetFieldValueNull(LPCTSTR lpszName);
```  
  
### <a name="parameters"></a>参数  
 `nIndex`  
 中的记录集，由从零开始的索引查找的字段的索引。  
  
 `lpszName`  
 按名称查找记录集中的字段名称。  
  
### <a name="remarks"></a>备注  
 C + + **NULL**不同时，则为 Null，这在数据库术语中，意味着"having 没有值。"  
  
 有关相关信息，请参阅"字段对象"和"值属性"DAO 帮助中的主题。  
  
##  <a name="setlockingmode"></a>CDaoRecordset::SetLockingMode  
 调用此成员函数以设置锁定记录集的类型。  
  
```  
void SetLockingMode(BOOL bPessimistic);
```  
  
### <a name="parameters"></a>参数  
 *bPessimistic*  
 一个标志，指示锁定的类型。  
  
### <a name="remarks"></a>备注  
 只要你调用保守式锁定时实际上，包含正在编辑的记录 2k 页锁定**编辑**成员函数。 在调用时，该页是解锁**更新**或**关闭**成员函数或任何移动或查找操作。  
  
 仅当与正在更新记录时，才时乐观锁定实际上是锁定 2k 页面，其中包含记录**更新**成员函数。  
  
 如果页面被锁定，没有其他用户可以编辑的同一页面上的记录。 如果调用`SetLockingMode`和传递一个非零值和其他用户已锁定的页中，在调用时，将引发异常**编辑**。 其他用户可以从锁定的页读取数据。  
  
 如果调用`SetLockingMode`具有零值及更高版本调用**更新**时由另一个用户锁定页，则会发生异常。 若要查看其他用户向您的记录所做的更改 （并放弃所做的更改），调用`SetBookmark`具有当前记录的书签值的成员函数。  
  
 当使用 ODBC 数据源，锁定模式始终是开放式的。  
  
##  <a name="setparamvalue"></a>CDaoRecordset::SetParamValue  
 调用此成员函数以在运行时在记录集设置参数的值。  
  
```  
virtual void SetParamValue(
    int nIndex,  
    const COleVariant& varValue);

 
virtual void SetParamValue(
    LPCTSTR lpszName,  
    const COleVariant& varValue);
```  
  
### <a name="parameters"></a>参数  
 `nIndex`  
 Querydef 的参数集合中的参数的数字位置。  
  
 `var`  
 要设置; 的值请参阅备注。  
  
 `lpszName`  
 参数要设置其值的名称。  
  
### <a name="remarks"></a>备注  
 参数必须已建立作为记录集的 SQL 字符串的一部分。 按名称或在集合中的索引位置，你可以访问参数。  
  
 指定的值将设置为`COleVariant`对象。 有关设置的所需的值和中的类型信息你`COleVariant`对象，请参阅类[COleVariant](../../mfc/reference/colevariant-class.md)。 请注意，如果你不在创建 UNICODE 记录集，则`COleVariant`对象必须显式声明 ANSI。 这可以通过使用[COleVariant::COleVariant](../../mfc/reference/colevariant-class.md#colevariant)**(** `lpszSrc` **，** `vtSrc` **)**窗体的构造函数与`vtSrc`设置为`VT_BSTRT`(ANSI) 或通过使用**COleVariant**函数[SetString](../../mfc/reference/colevariant-class.md#setstring)**(** `lpszSrc` **，** `vtSrc` **)**与`vtSrc`设置为`VT_BSTRT`。  
  
##  <a name="setparamvaluenull"></a>CDaoRecordset::SetParamValueNull  
 调用此成员函数可将参数设置为 Null 值。  
  
```  
void SetParamValueNull(int nIndex);  
void SetParamValueNull(LPCTSTR lpszName);
```  
  
### <a name="parameters"></a>参数  
 `nIndex`  
 中的记录集，由从零开始的索引查找的字段的索引。  
  
 `lpszName`  
 按名称查找记录集中的字段名称。  
  
### <a name="remarks"></a>备注  
 C + + **NULL**不同时，则为 Null，这在数据库术语中，意味着"having 没有值。"  
  
##  <a name="setpercentposition"></a>CDaoRecordset::SetPercentPosition  
 调用此成员函数可设置一个值，更改基于百分比的中记录集的记录的记录集对象中的当前记录的近似位置。  
  
```  
void SetPercentPosition(float fPosition);
```  
  
### <a name="parameters"></a>参数  
 *fPosition*  
 一个介于 0 和 100 之间的数字。  
  
### <a name="remarks"></a>备注  
 在使用动态集类型或快照类型的记录集，首先记录集填充通过移动到最后一个记录，然后才能调用`SetPercentPosition`。 如果调用`SetPercentPosition`完全填充记录集之前, 移动的量是相对于访问的值所述的记录数[GetRecordCount](#getrecordcount)。 你可以通过将移动到最后一个记录调用`MoveLast`。  
  
 一旦调用`SetPercentPosition`，与该值对应的近似位置处的记录将成为当前。  
  
> [!NOTE]
>  调用`SetPercentPosition`移动到特定记录在记录集中的当前记录不建议。 调用[SetBookmark](#setbookmark)成员函数。  
  
 有关相关信息，请参阅主题 DAO 帮助中的"PercentPosition 属性"。  
  
##  <a name="update"></a>CDaoRecordset::Update  
 在调用后调用此成员函数`AddNew`或**编辑**成员函数。  
  
```  
virtual void Update();
```  
  
### <a name="remarks"></a>备注  
 完成所需的此调用`AddNew`或**编辑**操作。  
  
 同时`AddNew`和**编辑**准备保存到数据源在其中放置添加或编辑的数据的编辑缓冲区。 **更新**将数据保存。 更新仅这些字段标记或检测到为已更改。  
  
 如果数据源支持事务，则你可以**更新**调用 (和其对应`AddNew`或**编辑**调用) 事务的一部分。  
  
> [!CAUTION]
>  如果调用**更新**但未事先调用`AddNew`或**编辑**，**更新**引发`CDaoException`。 如果调用`AddNew`或**编辑**，必须调用**更新**之前调用[MoveNext](#movenext)或关闭记录集或数据源连接。 否则，所做的更改都将丢失而不另行通知。  
  
 记录当记录集对象保守式锁定在多用户环境中时，保持锁定状态从时间**编辑**完成更新之前使用。 如果乐观锁定记录集，该记录已被锁定，在数据库中更新之前，将与预编辑的记录进行比较。 如果记录已更改，因为你调用**编辑**、**更新**操作失败且 MFC 引发异常。 您可以更改与锁定模式`SetLockingMode`。  
  
> [!NOTE]
>  外部数据库格式，如 ODBC 和可安装 ISAM 上始终使用乐观锁定。  
  
 有关相关信息，请参阅主题的"AddNew 方法"、"正在执行方法"、"Delete 方法"、"上次更改时间属性"、"更新方法"和 DAO 帮助中的"EditMode 属性"。  
  
## <a name="see-also"></a>请参阅  
 [CObject 类](../../mfc/reference/cobject-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CDaoTableDef 类](../../mfc/reference/cdaotabledef-class.md)   
 [CDaoWorkspace 类](../../mfc/reference/cdaoworkspace-class.md)   
 [CDaoDatabase 类](../../mfc/reference/cdaodatabase-class.md)   
 [CDaoQueryDef 类](../../mfc/reference/cdaoquerydef-class.md)
