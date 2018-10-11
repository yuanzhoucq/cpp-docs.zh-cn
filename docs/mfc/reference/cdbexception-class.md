---
title: CDBException 类 |Microsoft Docs
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
ms.openlocfilehash: c34c70f1bca3091ba078846b7b94ad947d5f31cb
ms.sourcegitcommit: 3a141cf07b5411d5f1fdf6cf67c4ce928cf389c3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/11/2018
ms.locfileid: "49083107"
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
|[CDBException::m_nRetCode](#m_nretcode)|包含类型 RETCODE 的开放式数据库连接 (ODBC) 返回代码。|
|[CDBException::m_strError](#m_strerror)|包含在字母数字术语描述错误的字符串。|
|[CDBException::m_strStateNativeOrigin](#m_strstatenativeorigin)|包含描述该错误由 ODBC 返回的错误代码方面的字符串。|

## <a name="remarks"></a>备注

该类包括两个公共数据成员可以使用以确定导致异常或显示一条描述异常的文本消息。 `CDBException` 对象构造，并由数据库类的成员函数引发。

> [!NOTE]
>  此类是一个 MFC 的开放式数据库连接 (ODBC) 类。 如果改为使用较新的数据访问对象 (DAO) 类，使用[CDaoException](../../mfc/reference/cdaoexception-class.md)相反。 所有 DAO 类名称作为前缀都具有"CDao"。 有关详细信息，请参阅文章[概述： 数据库编程](../../data/data-access-programming-mfc-atl.md)。

异常的异常执行涉及外部程序的控制，如数据源的条件的情况下，或网络 I/O 错误。 你可能希望在正常执行程序的过程中看到的错误通常不会考虑异常。

您可以访问这些对象的作用域内**捕获**表达式。 您可以引发`CDBException`对象从你自己的代码与`AfxThrowDBException`全局函数。

有关常规，或有关中的异常处理的详细信息`CDBException`对象，请参阅文章[异常处理 (MFC)](../../mfc/exception-handling-in-mfc.md)并[异常： 数据库异常](../../mfc/exceptions-database-exceptions.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CException](../../mfc/reference/cexception-class.md)

`CDBException`

## <a name="requirements"></a>要求

**标头：** afxdb.h

##  <a name="m_nretcode"></a>  CDBException::m_nRetCode

包含类型 RETCODE 由 ODBC 应用程序编程接口 (API) 函数返回的 ODBC 错误代码。

### <a name="remarks"></a>备注

这种类型包括按 ODBC 定义的 SQL 前缀代码和数据库类定义的 AFX_SQL 前缀代码。 有关`CDBException`，此成员将包含以下值之一：

- AFX_SQL_ERROR_API_CONFORMANCE 驱动程序对于`CDatabase::OpenEx`或`CDatabase::Open`调用不符合所需的 ODBC API 一致性级别 1 (SQL_OAC_LEVEL1)。

- AFX_SQL_ERROR_CONNECT_FAIL 连接到数据源失败。 传递 NULL`CDatabase`指针，指向记录集构造函数和创建的连接的后续尝试基于`GetDefaultConnect`失败。

- AFX_SQL_ERROR_DATA_TRUNCATED 您请求不是提供了适用于存储的更多数据。 有关增加的提供的数据存储的信息`CString`或`CByteArray`数据类型，请参阅`nMaxLength`自变量[RFX_Text](record-field-exchange-functions.md#rfx_text)并[RFX_Binary](record-field-exchange-functions.md#rfx_binary)下"宏和全局变量。"

- AFX_SQL_ERROR_DYNASET_NOT_SUPPORTED 一个调用`CRecordset::Open`请求动态集失败。 驱动程序不支持动态集。

- AFX_SQL_ERROR_EMPTY_COLUMN_LIST 您尝试打开表 (或你为提供无法标识作为过程调用或**选择**语句)，但没有记录字段交换 (RFX) 中的函数调用中标识的列你`DoFieldExchange`重写。

- AFX_SQL_ERROR_FIELD_SCHEMA_MISMATCH RFX 类型函数，在你`DoFieldExchange`重写都不允许在记录集中的列数据类型。

- AFX_SQL_ERROR_ILLEGAL_MODE 你调用`CRecordset::Update`而无需以前请求`CRecordset::AddNew`或`CRecordset::Edit`。

- 因为 ODBC 驱动程序不支持锁定，无法满足 AFX_SQL_ERROR_LOCK_MODE_NOT_SUPPORTED 锁定记录更新到你的请求。

- AFX_SQL_ERROR_MULTIPLE_ROWS_AFFECTED 你调用`CRecordset::Update`或`Delete`没有唯一键的表和已更改的多个记录。

- AFX_SQL_ERROR_NO_CURRENT_RECORD 你尝试编辑或删除以前删除的记录。 您必须删除后滚动到新的当前记录。

- AFX_SQL_ERROR_NO_POSITIONED_UPDATES 无法满足你的动态集请求，因为 ODBC 驱动程序不支持定位更新。

- AFX_SQL_ERROR_NO_ROWS_AFFECTED 你调用`CRecordset::Update`或`Delete`，但操作开始时可能无法再找到该记录。

- AFX_SQL_ERROR_ODBC_LOAD_FAILED 尝试加载 ODBC。DLL 失败;Windows 找不到或无法加载此 DLL。 此错误是致命的。

- AFX_SQL_ERROR_ODBC_V2_REQUIRED 由于级别 2 兼容的 ODBC 驱动程序是必需的无法满足你的动态集请求。

- AFX_SQL_ERROR_RECORDSET_FORWARD_ONLY 滚动的尝试未成功，因为数据源不支持向后滚动。

- AFX_SQL_ERROR_SNAPSHOT_NOT_SUPPORTED 一个调用`CRecordset::Open`请求快照失败。 驱动程序不支持快照。 (应仅发生此情况时 ODBC 游标库 ODBCCURS。DLL 不存在。）

- AFX_SQL_ERROR_SQL_CONFORMANCE 驱动程序对于`CDatabase::OpenEx`或`CDatabase::Open`调用不符合所需的 ODBC SQL 一致性级别的"最小值"(SQL_OSC_MINIMUM)。

- AFX_SQL_ERROR_SQL_NO_TOTAL ODBC 驱动程序无法将指定的总大小`CLongBinary`数据值。 该操作可能失败，因为不会预先分配全局内存块。

- AFX_SQL_ERROR_RECORDSET_READONLY 你尝试更新只读的记录集，或数据源是只读的。 可以使用记录集执行任何更新操作或`CDatabase`与之关联的对象。

- SQL_ERROR 函数失败。 由 ODBC 函数返回的错误消息`SQLError`存储在`m_strError`数据成员。

- SQL_INVALID_HANDLE 函数失败由于无效的环境句柄、 连接句柄或语句句柄。 这指示编程错误。 从 ODBC 函数没有其他信息，则`SQLError`。

由 ODBC 定义的 SQL 前缀代码。 AFX 前缀代码 AFXDB 中定义。H、 在 MFC\INCLUDE 中找到。

##  <a name="m_strerror"></a>  CDBException::m_strError

包含描述导致异常的错误的字符串。

### <a name="remarks"></a>备注

该字符串在字母数字术语中描述的错误。 有关更多详细信息和示例，请参阅`m_strStateNativeOrigin`。

##  <a name="m_strstatenativeorigin"></a>  CDBException::m_strStateNativeOrigin

包含描述导致异常的错误的字符串。

### <a name="remarks"></a>备注

该字符串采用窗体"状态: %s，本机: %ld，源: %s"，其中的格式代码，按顺序，将替换为描述的值：

- 包含五个字符的错误代码的以 null 结尾的字符串返回 SQLSTATE *szSqlState* ODBC 函数的参数`SQLError`。 附录 A 列出了 SQLSTATE 值[ODBC 错误代码](/previous-versions/windows/desktop/ms714687)，在*ODBC 程序员参考*。 示例:"S0022"。

- 在中返回特定于数据源的本机错误代码*pfNativeError*参数的`SQLError`函数。 示例： 207。

- 在返回的错误消息文本*szErrorMsg*参数的`SQLError`函数。 此消息包含几个用括号括起来的名称。 向用户从其源传递错误，因为每个 ODBC 组件 （数据源，驱动程序，驱动程序管理器） 将追加其自己的名称。 此信息可帮助找出错误的源。 示例: [Microsoft] [SQL Server Driver] [SQL Server]

该框架将错误字符串解释，并将放入其组件`m_strStateNativeOrigin`; 如果`m_strStateNativeOrigin`包含信息的多个错误，这些错误由换行符分隔。 该框架将放入的字母数字错误文本`m_strError`。

有关用于构成此字符串的代码的其他信息，请参阅[SQLError](/previous-versions/windows/desktop/ms716312)函数，在*ODBC 程序员参考*。

### <a name="example"></a>示例

  ODBC： 从"状态： S0022，本机： 207，源: [Microsoft] [SQL Server Driver] [SQL Server] 无效的列名称 ColName"

在`m_strStateNativeOrigin`:"状态： S0022，本机： 207，源: [Microsoft] [SQL Server Driver] [SQL Server]"

在`m_strError`:"无效的列 ColName name"

## <a name="see-also"></a>请参阅

[CException 类](../../mfc/reference/cexception-class.md)<br/>
[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[CDatabase 类](../../mfc/reference/cdatabase-class.md)<br/>
[CRecordset 类](../../mfc/reference/crecordset-class.md)<br/>
[CFieldExchange 类](../../mfc/reference/cfieldexchange-class.md)<br/>
[CRecordset::Update](../../mfc/reference/crecordset-class.md#update)<br/>
[CRecordset::Delete](../../mfc/reference/crecordset-class.md#delete)<br/>
[CException 类](../../mfc/reference/cexception-class.md)
