---
title: "CDatabase 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CDatabase
- AFXDB/CDatabase
- AFXDB/CDatabase::CDatabase
- AFXDB/CDatabase::BeginTrans
- AFXDB/CDatabase::BindParameters
- AFXDB/CDatabase::Cancel
- AFXDB/CDatabase::CanTransact
- AFXDB/CDatabase::CanUpdate
- AFXDB/CDatabase::Close
- AFXDB/CDatabase::CommitTrans
- AFXDB/CDatabase::ExecuteSQL
- AFXDB/CDatabase::GetBookmarkPersistence
- AFXDB/CDatabase::GetConnect
- AFXDB/CDatabase::GetCursorCommitBehavior
- AFXDB/CDatabase::GetCursorRollbackBehavior
- AFXDB/CDatabase::GetDatabaseName
- AFXDB/CDatabase::IsOpen
- AFXDB/CDatabase::OnSetOptions
- AFXDB/CDatabase::Open
- AFXDB/CDatabase::OpenEx
- AFXDB/CDatabase::Rollback
- AFXDB/CDatabase::SetLoginTimeout
- AFXDB/CDatabase::SetQueryTimeout
- AFXDB/CDatabase::m_hdbc
dev_langs: C++
helpviewer_keywords:
- CDatabase [MFC], CDatabase
- CDatabase [MFC], BeginTrans
- CDatabase [MFC], BindParameters
- CDatabase [MFC], Cancel
- CDatabase [MFC], CanTransact
- CDatabase [MFC], CanUpdate
- CDatabase [MFC], Close
- CDatabase [MFC], CommitTrans
- CDatabase [MFC], ExecuteSQL
- CDatabase [MFC], GetBookmarkPersistence
- CDatabase [MFC], GetConnect
- CDatabase [MFC], GetCursorCommitBehavior
- CDatabase [MFC], GetCursorRollbackBehavior
- CDatabase [MFC], GetDatabaseName
- CDatabase [MFC], IsOpen
- CDatabase [MFC], OnSetOptions
- CDatabase [MFC], Open
- CDatabase [MFC], OpenEx
- CDatabase [MFC], Rollback
- CDatabase [MFC], SetLoginTimeout
- CDatabase [MFC], SetQueryTimeout
- CDatabase [MFC], m_hdbc
ms.assetid: bd0de70a-e3c3-4441-bcaa-bbf434426ca8
caps.latest.revision: "24"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: c6aeaa64b0b665449ee9216070cdebbc2632948b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="cdatabase-class"></a>CDatabase 类
表示与数据源的连接，通过此连接可操作数据源。  
  
## <a name="syntax"></a>语法  
  
```  
class CDatabase : public CObject  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[CDatabase::CDatabase](#cdatabase)|构造 `CDatabase` 对象。 必须通过调用初始化对象`OpenEx`或**打开**。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CDatabase::BeginTrans](#begintrans)|启动"事务"-可逆调用一系列`AddNew`，**编辑**，**删除**，和**更新**类的成员函数`CRecordset`-上已连接的数据源。 数据源必须支持事务**BeginTrans**以产生任何影响。|  
|[CDatabase::BindParameters](#bindparameters)|允许你将绑定之前调用的参数`CDatabase::ExecuteSQL`。|  
|[CDatabase::Cancel](#cancel)|取消一个异步操作或从第二个线程的进程。|  
|[CDatabase::CanTransact](#cantransact)|返回非零，如果数据源支持事务。|  
|[CDatabase::CanUpdate](#canupdate)|返回非零如果`CDatabase`是可更新的对象 （不只读的）。|  
|[CDatabase::Close](#close)|关闭数据源连接。|  
|[CDatabase::CommitTrans](#committrans)|完成开始的事务**BeginTrans**。 在事务中更改数据源的命令都将执行。|  
|[CDatabase::ExecuteSQL](#executesql)|执行 SQL 语句。 会不返回任何数据记录。|  
|[CDatabase::GetBookmarkPersistence](#getbookmarkpersistence)|标识通过该书签将保留在记录集对象的操作。|  
|[CDatabase::GetConnect](#getconnect)|返回用于连接的 ODBC 连接字符串`CDatabase`到数据源的对象。|  
|[CDatabase::GetCursorCommitBehavior](#getcursorcommitbehavior)|标识提交打开记录集对象上的事务的效果。|  
|[CDatabase::GetCursorRollbackBehavior](#getcursorrollbackbehavior)|标识在打开记录集对象上回滚事务的效果。|  
|[CDatabase::GetDatabaseName](#getdatabasename)|返回当前所用的数据库名称。|  
|[CDatabase::IsOpen](#isopen)|返回非零如果`CDatabase`对象当前连接到数据源。|  
|[CDatabase::OnSetOptions](#onsetoptions)|由框架调用以设置标准连接选项。 默认实现设置的查询超时值。 您可以通过调用建立提前这些选项`SetQueryTimeout`。|  
|[CDatabase::Open](#open)|建立到数据源 （通过 ODBC 驱动程序） 的连接。|  
|[CDatabase::OpenEx](#openex)|建立到数据源 （通过 ODBC 驱动程序） 的连接。|  
|[CDatabase::Rollback](#rollback)|反转当前事务过程中做出的更改。 数据源返回到以前的状态，如中所定义**BeginTrans**调用，不变。|  
|[CDatabase::SetLoginTimeout](#setlogintimeout)|设置后，该数据源连接尝试将超时时间的秒数。|  
|[CDatabase::SetQueryTimeout](#setquerytimeout)|之后的数据库的秒数查询操作的设置将会超时。影响所有后续的记录集**打开**， `AddNew`，**编辑**，和**删除**调用。|  
  
### <a name="public-data-members"></a>公共数据成员  
  
|名称|描述|  
|----------|-----------------|  
|[CDatabase::m_hdbc](#m_hdbc)|打开数据库连接 (ODBC) 连接到数据源的句柄。 类型**HDBC**。|  
  
## <a name="remarks"></a>备注  
 数据源是由某些数据库管理系统 (DBMS) 承载的数据的特定实例。 示例包括 Microsoft SQL Server、 Microsoft Access、 高 dBASE 和 xBASE。 可以包含一个或多个`CDatabase`active 一次应用程序中的对象。  
  
> [!NOTE]
>  如果你正在使用的数据访问对象 (DAO) 类，而不是开放式数据库连接 (ODBC) 类，可以使用类[CDaoDatabase](../../mfc/reference/cdaodatabase-class.md)相反。 有关详细信息，请参阅文章[概述： 数据库编程](../../data/data-access-programming-mfc-atl.md)。  
  
 若要使用`CDatabase`，构造`CDatabase`对象并调用其`OpenEx`成员函数。 这将打开一个连接。 然后构造时`CRecordset`在连接的数据源上的对象传递给记录集构造函数的指针你`CDatabase`对象。 当你完成使用连接时，调用**关闭**成员函数，并且销毁`CDatabase`对象。 **关闭**关闭你以前没有关闭任何记录集。  
  
 有关详细信息`CDatabase`，请参阅文章[数据源 (ODBC)](../../data/odbc/data-source-odbc.md)和[概述： 数据库编程](../../data/data-access-programming-mfc-atl.md)。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CDatabase`  
  
## <a name="requirements"></a>惠?  
 **标头：** afxdb.h  
  
##  <a name="begintrans"></a>CDatabase::BeginTrans  
 调用此成员函数以开始连接的数据源的事务。  
  
```  
BOOL BeginTrans();
```  
  
### <a name="return-value"></a>返回值  
 如果调用已成功完成，在提交更改仅手动; 则为非 0否则为 0。  
  
### <a name="remarks"></a>备注  
 事务由一个或多个对的调用`AddNew`，**编辑**，**删除**，和**更新**的成员函数`CRecordset`对象。 开始一个事务之前,`CDatabase`对象必须已具有已连接到数据源通过调用其`OpenEx`或**打开**成员函数。 若要结束该事务，调用[CommitTrans](#committrans)以接受对数据源的所有更改 （并执行其） 或调用[回滚](#rollback)中止整个事务。 调用**BeginTrans**后，你可以打开任何事务中涉及的记录集并作为接近实际更新尽可能操作。  
  
> [!CAUTION]
>  具体取决于 ODBC 驱动程序，打开之前调用的记录集**BeginTrans**调用时可能会导致问题**回滚**。 你应检查你使用的特定驱动程序。 例如，在使用 Microsoft ODBC Desktop Driver Pack 3.0 中包括 Microsoft Access 驱动程序时，你必须考虑不应以上的所有数据库都已打开的游标的事务的 Jet 数据库引擎的要求。 在 MFC 数据库类中，打开的游标意味着打开`CRecordset`对象。 有关详细信息，请参阅[技术注意 68](../../mfc/tn068-performing-transactions-with-the-microsoft-access-7-odbc-driver.md)。  
  
 **BeginTrans**还可能会锁定数据记录在服务器上，具体取决于请求的并发和数据源的功能。 锁定的数据有关的信息，请参阅文章[记录集： 锁定记录 (ODBC)](../../data/odbc/recordset-locking-records-odbc.md)。  
  
 用户定义的事务文章中所述[事务 (ODBC)](../../data/odbc/transaction-odbc.md)。  
  
 **BeginTrans**建立到的事务序列都可以回滚的状态 （已反转）。 若要建立回滚的新状态，提交任何当前的事务，然后调用**BeginTrans**试。  
  
> [!CAUTION]
>  调用**BeginTrans**试情况下调用**CommitTrans**或**回滚**时出错。  
  
 调用[CanTransact](#cantransact)成员函数来确定您的驱动程序是否支持给定的数据库的事务。 此外应调用[GetCursorCommitBehavior](#getcursorcommitbehavior)和[GetCursorRollbackBehavior](#getcursorrollbackbehavior)确定光标实现保留的支持。  
  
 有关事务的详细信息，请参阅文章[事务 (ODBC)](../../data/odbc/transaction-odbc.md)。  
  
### <a name="example"></a>示例  
  请参阅文章[事务： 在记录集 (ODBC) 执行事务](../../data/odbc/transaction-performing-a-transaction-in-a-recordset-odbc.md)。  
  
##  <a name="bindparameters"></a>CDatabase::BindParameters  
 重写`BindParameters`何时需要将之前调用的参数绑定[CDatabase::ExecuteSQL](#executesql)。  
  
```  
virtual void BindParameters(HSTMT hstmt);
```  
  
### <a name="parameters"></a>参数  
 `hstmt`  
 你想要将参数绑定 ODBC 语句句柄。  
  
### <a name="remarks"></a>备注  
 当你不需要结果时，此方法非常有用设置从存储过程。  
  
 在替代中，调用**SQLBindParameters**和相关 ODBC 函数将参数绑定。 MFC 调用之前调用重写`ExecuteSQL`。 不需要调用**SQLPrepare**;`ExecuteSQL`调用**SQLExecDirect**和销毁**hstmt**，用于一次。  
  
##  <a name="cancel"></a>CDatabase::Cancel  
 调用此成员函数以请求的数据源取消正在进行的异步操作或从第二个线程的进程。  
  
```  
void Cancel();
```  
  
### <a name="remarks"></a>备注  
 请注意，MFC ODBC 类不再使用异步处理;若要执行异步操作，必须直接调用 ODBC API 函数[SQLSetConnectOption](https://msdn.microsoft.com/library/ms713564.aspx)。 有关详细信息，请参阅[异步执行](https://msdn.microsoft.com/library/ms713563.aspx)Windows SDK 中。  
  
##  <a name="cantransact"></a>CDatabase::CanTransact  
 调用此成员函数来确定数据库是否允许事务。  
  
```  
BOOL CanTransact() const;  
```  
  
### <a name="return-value"></a>返回值  
 非零如果使用此记录集`CDatabase`对象允许事务; 否则为 0。  
  
### <a name="remarks"></a>备注  
 有关事务的信息，请参阅文章[事务 (ODBC)](../../data/odbc/transaction-odbc.md)。  
  
##  <a name="canupdate"></a>CDatabase::CanUpdate  
 调用此成员函数可确定是否`CDatabase`对象允许更新。  
  
```  
BOOL CanUpdate() const;  
```  
  
### <a name="return-value"></a>返回值  
 非零如果`CDatabase`对象允许更新; 否则为 0，指示该你传递**TRUE**中`bReadOnly`打开时`CDatabase`对象或数据源本身是只读的。 数据源是只读的如果对 ODBC API 函数的调用**SQLGetInfo**为**SQL_DATASOURCE_READ_ONLY**返回"y"。  
  
### <a name="remarks"></a>备注  
 并非所有驱动程序支持更新。  
  
##  <a name="cdatabase"></a>CDatabase::CDatabase  
 构造 `CDatabase` 对象。  
  
```  
CDatabase();
```  
  
### <a name="remarks"></a>备注  
 在构造对象之后, 必须调用其`OpenEx`或**打开**成员函数以建立与指定的数据源的连接。  
  
 您可能发现方便嵌入`CDatabase`中您的文档类对象。  
  
### <a name="example"></a>示例  
 此示例演示如何使用`CDatabase`中`CDocument`-派生类。  
  
 [!code-cpp[NVC_MFCDatabase#9](../../mfc/codesnippet/cpp/cdatabase-class_1.h)]  
  
 [!code-cpp[NVC_MFCDatabase#10](../../mfc/codesnippet/cpp/cdatabase-class_2.cpp)]  
  
##  <a name="close"></a>CDatabase::Close  
 如果你想要从数据源断开连接，请调用此成员函数。  
  
```  
virtual void Close();
```  
  
### <a name="remarks"></a>备注  
 您必须关闭任何与关联的记录集`CDatabase`对象之前调用此成员函数。 因为**关闭**不会销毁`CDatabase`对象，您可以通过打开新连接到同一数据源或其他数据源重新使用该对象。  
  
 所有挂起的`AddNew`或**编辑**取消时使用的数据库的记录集的语句，并且所有挂起的事务将回滚。 依赖于任何记录集`CDatabase`对象处于未定义的状态。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCDatabase#12](../../mfc/codesnippet/cpp/cdatabase-class_3.cpp)]  
  
##  <a name="committrans"></a>CDatabase::CommitTrans  
 调用此成员函数在完成事务时。  
  
```  
BOOL CommitTrans();
```  
  
### <a name="return-value"></a>返回值  
 如果更新已成功提交; 则为非 0否则为 0。 如果**CommitTrans**失败，数据源的状态是不确定。 必须检查以确定其状态的数据。  
  
### <a name="remarks"></a>备注  
 事务由一系列到调用的`AddNew`，**编辑**，**删除**，和**更新**的成员函数`CRecordset`以开头的对象调用[BeginTrans](#begintrans)成员函数。 **CommitTrans**提交事务。 默认情况下，将提交更新立即;调用**BeginTrans**导致承诺的更新会延迟，直至**CommitTrans**调用。  
  
 直到你调用**CommitTrans**若要结束事务，可以调用[回滚](#rollback)成员函数以中止事务，并将数据源保留在其原始状态。 若要开始新事务，调用**BeginTrans**试。  
  
 有关事务的详细信息，请参阅文章[事务 (ODBC)](../../data/odbc/transaction-odbc.md)。  
  
### <a name="example"></a>示例  
  请参阅文章[事务： 在记录集 (ODBC) 执行事务](../../data/odbc/transaction-performing-a-transaction-in-a-recordset-odbc.md)。  
  
##  <a name="executesql"></a>CDatabase::ExecuteSQL  
 当你需要直接执行 SQL 命令时，请调用此成员函数。  
  
```  
void ExecuteSQL(LPCTSTR lpszSQL);
```  
  
### <a name="parameters"></a>参数  
 `lpszSQL`  
 指向以 null 结尾的字符串，包含要执行的有效 SQL 命令。 你可以将传递[CString](../../atl-mfc-shared/reference/cstringt-class.md)。  
  
### <a name="remarks"></a>备注  
 以 null 结尾的字符串创建的命令。 `ExecuteSQL`不返回数据记录。 如果你想要对记录进行操作，请改为使用记录集对象。  
  
 通过选择数据、 将新记录插入、 删除记录，和编辑记录支持命令的记录集对象颁发大部分你的数据源的命令。 但是，并非所有 ODBC 直接支持功能由数据库类中，因此您有时可能需要进行直接 SQL 调用具有`ExecuteSQL`。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCDatabase#13](../../mfc/codesnippet/cpp/cdatabase-class_4.cpp)]  
  
##  <a name="getbookmarkpersistence"></a>CDatabase::GetBookmarkPersistence  
 在某些操作之后，通过调用此成员函数确定记录集对象上的书签的持久性。  
  
```  
DWORD GetBookmarkPersistence() const;  
```  
  
### <a name="return-value"></a>返回值  
 用于标识操作的位掩码，书签通过它来保存在记录集对象上。 有关详细信息，请参阅“备注”。  
  
### <a name="remarks"></a>备注  
 例如，如果调用 `CRecordset::GetBookmark`，然后调用 `CRecordset::Requery`，则从 `GetBookmark` 获取的书签可能不再有效。 在调用 `GetBookmarkPersistence` 之前应当先调用 `CRecordset::SetBookmark`。  
  
 下表列出了位掩码值，这些值可组合成 `GetBookmarkPersistence` 的返回值。  
  
|位掩码值|书签的持久性|  
|-------------------|--------------------------|  
|`SQL_BP_CLOSE`|书签将变为有效之后**Requery**操作。|  
|`SQL_BP_DELETE`|行的书签将变为有效之后**删除**该行上的操作。|  
|`SQL_BP_DROP`|书签将变为有效之后**关闭**操作。|  
|`SQL_BP_SCROLL`|书签后任何将变为有效**移动**操作。 这只标识记录集上是否支持书签，正如 `CRecordset::CanBookmark` 返回的值一样。|  
|`SQL_BP_TRANSACTION`|在提交或回滚事务后，书签将变为有效。|  
|`SQL_BP_UPDATE`|行的书签将变为有效之后**更新**该行上的操作。|  
|`SQL_BP_OTHER_HSTMT`|与某个记录集对象关联的书签在另一个记录集上有效。|  
  
 有关此返回值的详细信息，请参阅 ODBC API 函数**SQLGetInfo** Windows SDK 中。 有关书签的详细信息，请参阅文章[记录集： 书签和绝对位置 (ODBC)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md)。  
  
##  <a name="getconnect"></a>CDatabase::GetConnect  
 调用此成员函数可检索到调用过程中使用的连接字符串`OpenEx`或`Open`连接`CDatabase`到数据源的对象。  
  
```  
const CString GetConnect() const;  
```  
  
### <a name="return-value"></a>返回值  
 A `const` [CString](../../atl-mfc-shared/reference/cstringt-class.md)包含连接字符串，如果`OpenEx`或`Open`调用; 否则为空字符串。  
  
### <a name="remarks"></a>备注  
 请参阅[CDatabase::Open](#open)有关如何创建连接字符串的说明。  
  
##  <a name="getcursorcommitbehavior"></a>CDatabase::GetCursorCommitBehavior  
 调用此成员函数可确定如何[CommitTrans](#committrans)操作影响打开记录集对象上的游标。  
  
```  
int GetCursorCommitBehavior() const;  
```  
  
### <a name="return-value"></a>返回值  
 一个值，该值指示在打开记录集对象上的事务的效果。 有关详细信息，请参阅“备注”。  
  
### <a name="remarks"></a>备注  
 下表列出可能的返回值`GetCursorCommitBehavior`以及对打开的记录集的相应影响。  
  
|返回值|CRecordset 对象上的效果|  
|------------------|----------------------------------|  
|`SQL_CB_CLOSE`|调用`CRecordset::Requery`紧跟在事务提交。|  
|`SQL_CB_DELETE`|调用`CRecordset::Close`紧跟在事务提交。|  
|`SQL_CB_PRESERVE`|通常情况下继续`CRecordset`操作。|  
  
 有关此返回值的详细信息，请参阅 ODBC API 函数**SQLGetInfo** Windows SDK 中。 有关事务的详细信息，请参阅文章[事务 (ODBC)](../../data/odbc/transaction-odbc.md)。  
  
##  <a name="getcursorrollbackbehavior"></a>CDatabase::GetCursorRollbackBehavior  
 调用此成员函数可确定如何[回滚](#rollback)操作影响打开记录集对象上的游标。  
  
```  
int GetCursorRollbackBehavior() const;  
```  
  
### <a name="return-value"></a>返回值  
 一个值，该值指示在打开记录集对象上的事务的效果。 有关详细信息，请参阅“备注”。  
  
### <a name="remarks"></a>备注  
 下表列出可能的返回值`GetCursorRollbackBehavior`以及对打开的记录集的相应影响。  
  
|返回值|CRecordset 对象上的效果|  
|------------------|----------------------------------|  
|`SQL_CB_CLOSE`|调用`CRecordset::Requery`紧跟在事务回滚。|  
|`SQL_CB_DELETE`|调用`CRecordset::Close`紧跟在事务回滚。|  
|`SQL_CB_PRESERVE`|通常情况下继续`CRecordset`操作。|  
  
 有关此返回值的详细信息，请参阅 ODBC API 函数**SQLGetInfo** Windows SDK 中。 有关事务的详细信息，请参阅文章[事务 (ODBC)](../../data/odbc/transaction-odbc.md)。  
  
##  <a name="getdatabasename"></a>CDatabase::GetDatabaseName  
 调用此成员函数以检索当前连接的数据库的名称 （前提是数据源定义一个命名的对象称为"数据库"）。  
  
```  
CString GetDatabaseName() const;  
```  
  
### <a name="return-value"></a>返回值  
 A [CString](../../atl-mfc-shared/reference/cstringt-class.md)包含数据库名称，如果成功; 否则为一个空`CString`。  
  
### <a name="remarks"></a>备注  
 这是不与数据源名称 (DSN) 中指定相同`OpenEx`或**打开**调用。 什么`GetDatabaseName`返回依赖于 ODBC。 通常情况下，数据库是一系列表。 如果此实体具有一个名称，`GetDatabaseName`返回它。  
  
 例如，你可能会想要在标题中显示此名称。 如果从 ODBC，检索的名称时出错`GetDatabaseName`返回一个空**Cstring**。  
  
##  <a name="isopen"></a>CDatabase::IsOpen  
 调用此成员函数可确定是否`CDatabase`对象当前连接到数据源。  
  
```  
BOOL IsOpen() const;  
```  
  
### <a name="return-value"></a>返回值  
 非零如果`CDatabase`当前连接对象; 否则为 0。  
  
##  <a name="m_hdbc"></a>CDatabase::m_hdbc  
 包含 ODBC 数据源连接的公共句柄-的"连接句柄。"  
  
### <a name="remarks"></a>备注  
 通常情况下，你将具有无需直接访问此成员变量。 框架在调用时相反，分配的句柄`OpenEx`或**打开**。 在调用时，框架将释放句柄**删除**运算符`CDatabase`对象。 请注意，**关闭**成员函数不释放句柄。  
  
 但是，某些情况下，可能需要直接使用该句柄。 例如，如果你需要直接而不是类通过调用 ODBC API 函数`CDatabase`，你可能需要连接句柄将作为参数传递。 请参阅下面的代码示例。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCDatabase#15](../../mfc/codesnippet/cpp/cdatabase-class_5.cpp)]  
  
##  <a name="onsetoptions"></a>CDatabase::OnSetOptions  
 框架调用此成员函数，直接执行 SQL 语句时`ExecuteSQL`成员函数。  
  
```  
virtual void OnSetOptions(HSTMT hstmt);
```  
  
### <a name="parameters"></a>参数  
 `hstmt`  
 ODBC 语句句柄为其设置选项。  
  
### <a name="remarks"></a>备注  
 `CRecordset::OnSetOptions`此外会调用此成员函数。  
  
 `OnSetOptions`设置登录超时值。 如果进行了以前调用`SetQueryTimeout`和成员函数，`OnSetOptions`反映当前的值; 否则，它将设置默认值。  
  
> [!NOTE]
>  在 MFC 4.2 版之前`OnSetOptions`到任一 snychronous 或异步还设置的处理模式。 从 MFC 4.2 开始，所有操作都是同步的。 若要执行异步操作，必须进行直接调用 ODBC API 函数**SQLSetPos**。  
  
 不需要重写`OnSetOptions`更改超时值。 相反，若要自定义的查询超时值，请调用`SetQueryTimeout`之前创建记录集;`OnSetOptions`将使用新值。 设置的值将应用于的所有记录集或直接 SQL 调用上的后续操作。  
  
 重写`OnSetOptions`如果你想要设置其他选项。 重写应调用基类`OnSetOptions`之前或之后调用 ODBC API 函数**SQLSetStmtOption**。 请按照框架的默认实现中所示的方法`OnSetOptions`。  
  
##  <a name="open"></a>CDatabase::Open  
 调用此成员函数以初始化新构造`CDatabase`对象。  
  
```  
virtual BOOL Open(
    LPCTSTR lpszDSN,  
    BOOL bExclusive = FALSE,  
    BOOL bReadOnly = FALSE,  
    LPCTSTR lpszConnect = _T("ODBC;"),  
    BOOL bUseCursorLib = TRUE);
```  
  
### <a name="parameters"></a>参数  
 `lpszDSN`  
 指定数据源名称 — 通过 ODBC 注册通过 ODBC 管理员程序的名称。 如果在指定 DSN 值`lpszConnect`(窗体中"DSN =\<数据源 >")，它必须未中再次指定`lpszDSN`。 在这种情况下，`lpszDSN`应**NULL**。 否则，你可以将传递**NULL**如果你想要向用户显示数据源对话框中，用户可以在其中选择数据源。 有关详细信息，请参阅备注。  
  
 `bExclusive`  
 不支持在此版本的类库。 目前，断言失败时如果此参数为**TRUE**。 数据源是始终打开是因为共享 （非独占）。  
  
 `bReadOnly`  
 **TRUE**如果你想要为只读的并禁止对数据源的更新的连接。 所有依赖的记录集继承此属性。 默认值是**FALSE**。  
  
 `lpszConnect`  
 指定的连接字符串。 连接字符串连接信息，还可能包括数据源名称，在数据源、 用户身份验证字符串 （密码，如果数据源需要一个） 和其他信息有效的用户 ID。 整个连接字符串必须为前缀字符串"ODBC;"（大写或小写）。 "ODBC;"字符串用于表示网络连接到 ODBC 数据源;这样是类库的为了向上兼容性时的未来版本可能支持非 ODBC 数据源的不同而不同。  
  
 `bUseCursorLib`  
 **TRUE**如果你想要加载的 ODBC 游标库 DLL。 游标库屏蔽的基础的 ODBC 驱动程序，有效地阻止动态记录集 （如果该驱动程序支持它们） 的一些功能。 如果加载的是光标库支持的唯一光标是静态的快照和只进游标。 默认值是**TRUE**。 如果你计划创建记录集对象直接从`CRecordset`而无需从其派生，不应加载的是光标库。  
  
### <a name="return-value"></a>返回值  
 如果成功建立连接; 则为非 0否则如果用户选择的 0 取消时显示一个对话框，要求你连接的详细信息。 所有其他情况下，框架会引发异常。  
  
### <a name="remarks"></a>备注  
 可以使用它来构造一个记录集对象之前，必须初始化数据库对象。  
  
> [!NOTE]
>  调用[OpenEx](#openex)成员函数是首选的方法，以连接到数据源并初始化你的数据库对象。  
  
 如果中的参数你**打开**调用不包含足够的信息来建立连接时，ODBC 驱动程序将打开一个对话框，从用户获取所需的信息。 当调用**打开**，连接字符串， `lpszConnect`，存储私下在`CDatabase`对象，可通过调用[GetConnect](#getconnect)成员函数。  
  
 如果您愿意，你可以打开对话框中，然后才能调用**打开**获取信息从用户，如密码，然后该将信息添加到连接字符串传递给**打开**。 或者你可能想要通过使你可以重复使用它的下一步的连接字符串保存时间应用程序调用**打开**上`CDatabase`对象。  
  
 此外可以针对多个级别的登录名授权使用的连接字符串 (每个不同`CDatabase`对象)，或者传递其他数据源特定的信息。 有关连接字符串的详细信息，请参阅 Windows SDK 中第 5 章:。  
  
 如果，例如，DBMS 主机不可用，它有可能连接尝试超时。 如果连接尝试失败，**打开**引发`CDBException`。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCDatabase#14](../../mfc/codesnippet/cpp/cdatabase-class_6.cpp)]  
  
##  <a name="openex"></a>CDatabase::OpenEx  
 调用此成员函数以初始化新构造`CDatabase`对象。  
  
```  
virtual BOOL OpenEx(
    LPCTSTR lpszConnectString,  
    DWORD dwOptions = 0);
```  
  
### <a name="parameters"></a>参数  
 `lpszConnectString`  
 指定一个 ODBC 连接字符串。 这包括数据源名称，以及其他可选信息，例如用户 ID 和密码。 例如，"DSN = SQLServer_Source;UID = SA;PWD = abc123"是一个可能的连接字符串。 请注意，如果你通过**NULL**为`lpszConnectString`，数据源对话框将提示用户选择数据源。  
  
 `dwOptions`  
 一个位屏蔽，它指定以下值的组合。 默认值为 0，这意味着将为打开该数据库共享具有写访问权限，将不加载 ODBC 游标库 DLL，并且将显示 ODBC 连接对话框中，仅当没有足够的信息来建立连接。  
  
- **CDatabase::openExclusive**的类库的此版本不支持。 数据源是始终打开是因为共享 （非独占）。 目前，断言失败时，如果指定此选项。  
  
- **CDatabase::openReadOnly**打开该数据源作为只读的。  
  
- **CDatabase::useCursorLib**加载 ODBC 游标库 DLL。 游标库屏蔽的基础的 ODBC 驱动程序，有效地阻止动态记录集 （如果该驱动程序支持它们） 的一些功能。 如果加载的是光标库支持的唯一光标是静态的快照和只进游标。 如果你计划创建记录集对象直接从`CRecordset`而无需从其派生，不应加载的是光标库。  
  
- **CDatabase::noOdbcDialog**不显示 ODBC 的连接对话框中，而不考虑是否提供足够的连接信息。  
  
- **CDatabase::forceOdbcDialog**始终显示 ODBC 连接对话框。  
  
### <a name="return-value"></a>返回值  
 如果成功建立连接; 则为非 0否则如果用户选择的 0 取消时显示一个对话框，要求你连接的详细信息。 所有其他情况下，框架会引发异常。  
  
### <a name="remarks"></a>备注  
 可以使用它来构造一个记录集对象之前，必须初始化数据库对象。  
  
 如果`lpszConnectString`中的参数你`OpenEx`调用不包含足够的信息来建立连接，ODBC 驱动程序将打开一个对话框，以从用户获取所需的信息，提供你尚未设置**CDatabase::noOdbcDialog**或**CDatabase::forceOdbcDialog**中`dwOptions`参数。 当调用`OpenEx`，连接字符串， `lpszConnectString`，存储私下在`CDatabase`对象，可通过调用[GetConnect](#getconnect)成员函数。  
  
 如果您愿意，你可以打开对话框中，然后才能调用`OpenEx`用户，如密码，从获取信息，然后将该信息添加到连接字符串传递给`OpenEx`。 或者你可能想要通过使你可以重复使用它的下一步的连接字符串保存时间应用程序调用`OpenEx`上`CDatabase`对象。  
  
 此外可以针对多个级别的登录名授权使用的连接字符串 (每个不同`CDatabase`对象)，或者传递其他数据源特定的信息。 有关连接字符串的详细信息，请参阅第 6 章中*ODBC 程序员参考*。  
  
 如果，例如，DBMS 主机不可用，它有可能连接尝试超时。 如果连接尝试失败，`OpenEx`引发`CDBException`。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCDatabase#11](../../mfc/codesnippet/cpp/cdatabase-class_7.cpp)]  
  
##  <a name="rollback"></a>CDatabase::Rollback  
 调用此成员函数以反向在事务期间所做的更改。  
  
```  
BOOL Rollback();
```  
  
### <a name="return-value"></a>返回值  
 如果成功撤消事务; 则为非 0否则为 0。 如果**回滚**调用失败，数据源和事务状态为未定义。 如果**回滚**返回 0，必须检查数据源，以确定其状态。  
  
### <a name="remarks"></a>备注  
 所有`CRecordset` `AddNew`，**编辑**，**删除**，和**更新**调用执行，因为最后一个[BeginTrans](#begintrans)将累加返回到该调用时存在于的状态。  
  
 调用了**回滚**、 事务已结束，并且必须调用**BeginTrans**再次为另一个事务。 是你在调用之前的最新的记录**BeginTrans**将成为当前记录再次后的**回滚**。  
  
 在回滚时后, 回滚之前的当前记录仍然是当前记录。 有关状态的记录集和回滚后的数据源的详细信息，请参阅文章[事务 (ODBC)](../../data/odbc/transaction-odbc.md)。  
  
### <a name="example"></a>示例  
  请参阅文章[事务： 在记录集 (ODBC) 执行事务](../../data/odbc/transaction-performing-a-transaction-in-a-recordset-odbc.md)。  
  
##  <a name="setlogintimeout"></a>CDatabase::SetLoginTimeout  
 调用此成员函数 — 之前调用`OpenEx`或**打开**-若要重写默认允许尝试数据前的秒数源连接超时。  
  
```  
void SetLoginTimeout(DWORD dwSeconds);
```  
  
### <a name="parameters"></a>参数  
 `dwSeconds`  
 超时允许在连接尝试之前的秒数。  
  
### <a name="remarks"></a>备注  
 如果，例如，DBMS 不可用，则连接尝试可能会超时。 调用**SetLoginTimeout**构造未经初始化即之后`CDatabase`对象，但之前调用`OpenEx`或**打开**。  
  
 登录超时的默认值为 15 秒。 并非所有数据源都支持的功能来指定登录超时值。 如果数据源不支持超时，将获得跟踪输出，但不是异常。 值为 0 表示"无限"。  
  
##  <a name="setquerytimeout"></a>CDatabase::SetQueryTimeout  
 调用此成员函数可重写默认以允许在后续操作上连接的数据源超时之前的秒数。  
  
```  
void SetQueryTimeout(DWORD dwSeconds);
```  
  
### <a name="parameters"></a>参数  
 `dwSeconds`  
 超时允许在查询尝试之前的秒数。  
  
### <a name="remarks"></a>备注  
 由于网络访问权限问题、 过多的查询处理时间等的操作可能会超时。 调用`SetQueryTimeout`打开记录集之前或在调用记录集的之前`AddNew`，**更新**或**删除**成员函数，如果你想要更改的查询超时值。 该设置将影响所有后续**打开**， `AddNew`，**更新**，和**删除**到任何与此相关的记录集的调用`CDatabase`对象。 在打开后更改记录集的查询超时值不会更改记录集的值。 例如，后续**移动**操作不使用新值。  
  
 查询超时的默认值为 15 秒。 并非所有数据源都支持的功能，以设置查询超时值。 如果你设置查询超时值为 0，则会发生无超时;与数据源的通信可能会停止响应。 在开发过程中，此行为可能会有用。 如果数据源不支持超时，将获得跟踪输出，但不是异常。  
  
## <a name="see-also"></a>请参阅  
 [CObject 类](../../mfc/reference/cobject-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CRecordset 类](../../mfc/reference/crecordset-class.md)
