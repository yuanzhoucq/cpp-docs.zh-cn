---
title: CDBException 类 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CDBException
- AFXDB/CDBException
- AFXDB/CDBException::m_nRetCode
- AFXDB/CDBException::m_strError
- AFXDB/CDBException::m_strStateNativeOrigin
dev_langs:
- C++
helpviewer_keywords:
- CDBException [MFC], m_nRetCode
- CDBException [MFC], m_strError
- CDBException [MFC], m_strStateNativeOrigin
ms.assetid: eb9e1119-89f5-49a7-b9d4-b91cee1ccc82
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 824ac88326042eb55ecb9667c39331d1ab5464e7
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33368330"
---
# <a name="cdbexception-class"></a>CDBException 类
表示由数据库类引起的异常条件。  
  
## <a name="syntax"></a>语法  
  
```  
class CDBException : public CException  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-data-members"></a>公共数据成员  
  
|名称|描述|  
|----------|-----------------|  
|[CDBException::m_nRetCode](#m_nretcode)|包含类型的开放式数据库连接 (ODBC) 返回代码**某一 RETCODE**。|  
|[CDBException::m_strError](#m_strerror)|包含在字母数字术语描述错误的字符串。|  
|[CDBException::m_strStateNativeOrigin](#m_strstatenativeorigin)|包含在由 ODBC 返回的错误代码方面对错误进行描述的字符串。|  
  
## <a name="remarks"></a>备注  
 该类包括两个公共数据成员可以使用来确定导致异常或显示一条描述异常的文本消息。 `CDBException` 对象为构造，并且由数据库类的成员函数引发。  
  
> [!NOTE]
>  此类是 MFC 的开放式数据库连接 (ODBC) 类。 如果改为使用较新的数据访问对象 (DAO) 类，使用[CDaoException](../../mfc/reference/cdaoexception-class.md)相反。 所有的 DAO 类名称作为前缀都具有"CDao"。 有关详细信息，请参阅文章[概述： 数据库编程](../../data/data-access-programming-mfc-atl.md)。  
  
 异常的异常执行涉及外部程序的控制，如数据源的条件的情况下，或网络 I/O 错误。 您可能希望在正常运行的执行程序中看到的错误通常不会视为异常。  
  
 你可以访问这些对象的作用域内**捕获**表达式。 你可以引发`CDBException`对象从你自己的代码与`AfxThrowDBException`全局函数。  
  
 有关常规，或有关中的异常处理的详细信息`CDBException`对象，请参阅文章[异常处理 (MFC)](../../mfc/exception-handling-in-mfc.md)和[异常： 数据库异常](../../mfc/exceptions-database-exceptions.md)。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CException](../../mfc/reference/cexception-class.md)  
  
 `CDBException`  
  
## <a name="requirements"></a>要求  
 **标头：** afxdb.h  
  
##  <a name="m_nretcode"></a>  CDBException::m_nRetCode  
 包含 ODBC 错误代码的类型**某一 RETCODE**返回的 ODBC 应用程序编程接口 (API) 函数。  
  
### <a name="remarks"></a>备注  
 此类型包括定义的 ODBC 的 SQL 前缀代码和数据库类定义的 AFX_SQL 前缀代码。 有关`CDBException`，此成员将包含以下值之一：  
  
- **AFX_SQL_ERROR_API_CONFORMANCE**的驱动程序`CDatabase::OpenEx`或`CDatabase::Open`调用不符合所需的 ODBC API 一致性级别 1 ( **SQL_OAC_LEVEL1**)。  
  
- **AFX_SQL_ERROR_CONNECT_FAIL**与数据源连接失败。 你传递**NULL** `CDatabase`指向记录集构造函数和创建的连接的后续尝试基于`GetDefaultConnect`失败。  
  
- **AFX_SQL_ERROR_DATA_TRUNCATED**请求更多的数据不是你提供的存储。 有关提高的提供的数据存储信息`CString`或`CByteArray`数据类型，请参阅`nMaxLength`参数[RFX_Text](record-field-exchange-functions.md#rfx_text)和[RFX_Binary](record-field-exchange-functions.md#rfx_binary)下"宏和全局函数。"  
  
- **AFX_SQL_ERROR_DYNASET_NOT_SUPPORTED**调用`CRecordset::Open`请求动态集失败。 由驱动程序不支持动态记录集。  
  
- **AFX_SQL_ERROR_EMPTY_COLUMN_LIST**尝试打开一个表 (或你为提供可能不会标识为过程调用或**选择**语句) 但没有在记录字段交换 (RFX) 中标识列函数调用中你`DoFieldExchange`重写。  
  
- **AFX_SQL_ERROR_FIELD_SCHEMA_MISMATCH**中 RFX 函数类型你`DoFieldExchange`替代与不兼容的记录集的列数据类型。  
  
- **AFX_SQL_ERROR_ILLEGAL_MODE**你调用`CRecordset::Update`而无需以前调用`CRecordset::AddNew`或`CRecordset::Edit`。  
  
- **AFX_SQL_ERROR_LOCK_MODE_NOT_SUPPORTED**无法满足你的更新锁定记录的请求，因为 ODBC 驱动程序不支持锁定。  
  
- **AFX_SQL_ERROR_MULTIPLE_ROWS_AFFECTED**你调用`CRecordset::Update`或**删除**具有没有唯一键的表和已更改的多个记录。  
  
- **AFX_SQL_ERROR_NO_CURRENT_RECORD**您尝试编辑或删除以前已删除的记录。 你必须在删除之后滚动到新的当前记录。  
  
- **AFX_SQL_ERROR_NO_POSITIONED_UPDATES**您的请求的不会完成动态集，因为 ODBC 驱动程序不支持定位更新。  
  
- **AFX_SQL_ERROR_NO_ROWS_AFFECTED**你调用`CRecordset::Update`或**删除**，但该操作开始时记录不再找不到。  
  
- **AFX_SQL_ERROR_ODBC_LOAD_FAILED**尝试加载 ODBC。DLL 失败;Windows 找不到或无法加载此 DLL。 此错误是致命的。  
  
- **AFX_SQL_ERROR_ODBC_V2_REQUIRED**无法满足你动态集的请求，因为级别 2 符合的 ODBC 驱动程序是必需的。  
  
- **AFX_SQL_ERROR_RECORDSET_FORWARD_ONLY**尝试向下滚动未成功，因为数据源不支持向后滚动。  
  
- **AFX_SQL_ERROR_SNAPSHOT_NOT_SUPPORTED**调用`CRecordset::Open`请求快照失败。 由驱动程序不支持快照。 (应仅发生此情况时 ODBC 游标库 ODBCCURS。DLL 不存在。）  
  
- **AFX_SQL_ERROR_SQL_CONFORMANCE**的驱动程序`CDatabase::OpenEx`或`CDatabase::Open`调用不符合所需的"最小值"的 ODBC SQL 一致性级别 ( **SQL_OSC_MINIMUM**)。  
  
- **AFX_SQL_ERROR_SQL_NO_TOTAL** ODBC 驱动程序无法将指定的总大小`CLongBinary`数据值。 该操作可能失败，因为不预分配全局内存块。  
  
- **AFX_SQL_ERROR_RECORDSET_READONLY**试图更新只读的记录集，或数据源是只读的。 可以使用该记录执行任何更新操作或`CDatabase`与之关联的对象。  
  
- **SQL_ERROR**失败的函数。 ODBC 函数返回的错误消息**SQLError**存储在**m_strError**数据成员。  
  
- **SQL_INVALID_HANDLE**函数失败，由于无效的环境句柄、 连接句柄或语句句柄。 这指示编程错误。 无更多信息可从 ODBC 函数**SQLError**。  
  
 由 ODBC 定义 SQL 前缀代码。 AFX 前缀代码 AFXDB 中定义。H、 在 MFC\INCLUDE 中找到。  
  
##  <a name="m_strerror"></a>  CDBException::m_strError  
 包含描述导致异常的错误的字符串。  
  
### <a name="remarks"></a>备注  
 字符串在字母数字术语中描述的错误。 有关详细信息及示例，请参阅**m_strStateNativeOrigin**。  
  
##  <a name="m_strstatenativeorigin"></a>  CDBException::m_strStateNativeOrigin  
 包含描述导致异常的错误的字符串。  
  
### <a name="remarks"></a>备注  
 该字符串采用的窗体"状态: %s，本机: %ld，源: %s"，其中的格式代码，按顺序，将替换为描述的值：  
  
-   **SQLSTATE**、 以 null 结尾的字符串，包含在中返回的五个字符的错误代码*szSqlState* ODBC 函数的参数**SQLError**。 **SQLSTATE**附录 A 列出了值[ODBC 错误代码](https://msdn.microsoft.com/library/ms714687.aspx)中*ODBC 程序员参考*。 示例:"S0022"。  
  
-   中的特定于数据源的本机错误代码返回*pfNativeError*参数**SQLError**函数。 示例： 207。  
  
-   在返回的错误消息文本*szErrorMsg*参数**SQLError**函数。 此消息由多个括在括号中的名称组成。 向用户从其源传递错误，如每个 ODBC 组件 （驱动程序，驱动程序管理器中的数据源） 将追加其自己的名称。 此信息可帮助找出错误的源。 示例: [Microsoft] [ODBC SQL Server 驱动程序] [SQL Server]  
  
 框架解释的错误字符串，并将其组件都进入**m_strStateNativeOrigin**; 如果**m_strStateNativeOrigin**包含信息用分隔多个错误，错误换行符。 框架将放到的字母数字的错误文本**m_strError**。  
  
 有关用于构成此字符串的代码的其他信息，请参阅[SQLError](https://msdn.microsoft.com/library/ms716312.aspx)函数中*ODBC 程序员参考*。  
  
### <a name="example"></a>示例  
  ODBC： 从"状态： S0022、 本机： 207、 源: [Microsoft] [ODBC SQL Server 驱动程序] [SQL Server] 无效的列名称 ColName"  
  
 在**m_strStateNativeOrigin**:"状态： S0022、 本机： 207、 源: [Microsoft] [ODBC SQL Server 驱动程序] [SQL Server]"  
  
 在**m_strError**:"无效的列 ColName 名称"  
  
## <a name="see-also"></a>请参阅  
 [CException 类](../../mfc/reference/cexception-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CDatabase 类](../../mfc/reference/cdatabase-class.md)   
 [CRecordset 类](../../mfc/reference/crecordset-class.md)   
 [CFieldExchange 类](../../mfc/reference/cfieldexchange-class.md)   
 [CRecordset::Update](../../mfc/reference/crecordset-class.md#update)   
 [CRecordset::Delete](../../mfc/reference/crecordset-class.md#delete)   
 [CException 类](../../mfc/reference/cexception-class.md)
