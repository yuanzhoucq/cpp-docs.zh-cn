---
title: 国开行例外类
ms.date: 11/04/2016
f1_keywords:
- CDBException
- AFXDB/CDBException
- AFXDB/CDBException::m_nRetCode
- AFXDB/CDBException::m_strError
- AFXDB/CDBException::m_strStateNativeOrigin
helpviewer_keywords:
- CDBException [MFC], m_nRetCode
- CDBException [MFC], m_strError
- CDBException [MFC], m_strStateNativeOrigin
ms.assetid: eb9e1119-89f5-49a7-b9d4-b91cee1ccc82
ms.openlocfilehash: 1ab7daeb3af55c92985c951c632b1d4050681474
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81321897"
---
# <a name="cdbexception-class"></a>国开行例外类

表示由数据库类引起的异常条件。

## <a name="syntax"></a>语法

```
class CDBException : public CException
```

## <a name="members"></a>成员

### <a name="public-data-members"></a>公共数据成员

|名称|说明|
|----------|-----------------|
|[国开行例外：m_nRetCode](#m_nretcode)|包含 OPEN 数据库连接 （ODBC） 返回代码，类型为 RETCODE。|
|[国开行例外：m_strError](#m_strerror)|包含用字母数字描述错误的字符串。|
|[国开行例外：：m_strStateNativeOrigin](#m_strstatenativeorigin)|包含一个字符串，描述 ODBC 返回的错误代码方面的错误。|

## <a name="remarks"></a>备注

该类包括两个公共数据成员，可用于确定异常的原因或显示描述异常的文本消息。 `CDBException`对象由数据库类的成员函数构造和引发。

> [!NOTE]
> 此类是 MFC 的开放数据库连接 （ODBC） 类之一。 如果您改用较新的数据访问对象 （DAO） 类，请使用[CDaoException。](../../mfc/reference/cdaoexception-class.md) 所有 DAO 类名称都以"CDao"为前缀。 有关详细信息，请参阅文章[概述：数据库编程](../../data/data-access-programming-mfc-atl.md)。

例外情况是涉及程序控制之外的条件（如数据源或网络 I/O 错误）的异常执行情况。 在程序执行的正常过程中，您可能期望看到的错误通常不被视为例外。

您可以在**CATCH**表达式的范围内访问这些对象。 还可以使用`AfxThrowDBException`全局函数`CDBException`从您自己的代码中引发对象。

有关常规异常处理或`CDBException`对象的详细信息，请参阅[文章"异常处理 "（MFC）](../../mfc/exception-handling-in-mfc.md)和["例外：数据库例外](../../mfc/exceptions-database-exceptions.md)"。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[C 例外](../../mfc/reference/cexception-class.md)

`CDBException`

## <a name="requirements"></a>要求

**标题：** afxdb.h

## <a name="cdbexceptionm_nretcode"></a><a name="m_nretcode"></a>国开行例外：m_nRetCode

包含由 ODBC 应用程序编程接口 （API） 函数返回的 RETCODE 类型的 ODBC 错误代码。

### <a name="remarks"></a>备注

此类型包括由 ODBC 定义的 SQL 前缀代码和数据库类定义的AFX_SQL预缀代码。 对于`CDBException`，此成员将包含以下值之一：

- AFX_SQL_ERROR_API_CONFORMANCE 或`CDatabase::OpenEx``CDatabase::Open`呼叫的驱动程序不符合所需的 ODBC API 符合性级别 1（SQL_OAC_LEVEL1）。

- AFX_SQL_ERROR_CONNECT_FAIL连接到数据源失败。 您将 NULL`CDatabase`指针传递给记录集构造函数，并随后尝试基于`GetDefaultConnect`失败创建连接。

- AFX_SQL_ERROR_DATA_TRUNCATED您请求的数据多于您提供的存储。 有关`CString`增加为 或 类型`CByteArray`提供的数据存储的信息，请参阅"宏和`nMaxLength`全局"下[RFX_Text](record-field-exchange-functions.md#rfx_text)和[RFX_Binary](record-field-exchange-functions.md#rfx_binary)的参数。

- AFX_SQL_ERROR_DYNASET_NOT_SUPPORTED请求`CRecordset::Open`发电机的呼叫失败。 驱动程序不支持动态集。

- AFX_SQL_ERROR_EMPTY_COLUMN_LIST您尝试打开表（或您提供的内容无法标识为过程调用或**SELECT**语句），但在`DoFieldExchange`重写中记录字段交换 （RFX） 函数调用中未标识列。

- AFX_SQL_ERROR_FIELD_SCHEMA_MISMATCH`DoFieldExchange`重写中的 RFX 函数的类型与记录集中的列数据类型不兼容。

- AFX_SQL_ERROR_ILLEGAL_MODE您之前`CRecordset::Update`没有打电话`CRecordset::AddNew`或`CRecordset::Edit`。

- AFX_SQL_ERROR_LOCK_MODE_NOT_SUPPORTED无法满足锁定更新记录的请求，因为 ODBC 驱动程序不支持锁定。

- AFX_SQL_ERROR_MULTIPLE_ROWS_AFFECTED您调用`CRecordset::Update`的`Delete`表或没有唯一键并更改了多个记录的表。

- AFX_SQL_ERROR_NO_CURRENT_RECORD您尝试编辑或删除以前删除的记录。 删除后，必须滚动到新的当前记录。

- AFX_SQL_ERROR_NO_POSITIONED_UPDATES无法满足您对动态集的请求，因为 ODBC 驱动程序不支持定位更新。

- AFX_SQL_ERROR_NO_ROWS_AFFECTED您调用`CRecordset::Update``Delete`或 ，但操作开始时，找不到记录。

- AFX_SQL_ERROR_ODBC_LOAD_FAILED尝试加载 ODBC。DLL 失败;Windows 找不到或无法加载此 DLL。 此错误是致命的。

- AFX_SQL_ERROR_ODBC_V2_REQUIRED由于需要符合 2 级的 ODBC 驱动程序，因此无法满足对动态集的请求。

- AFX_SQL_ERROR_RECORDSET_FORWARD_ONLY 尝试滚动失败，因为数据源不支持向后滚动。

- AFX_SQL_ERROR_SNAPSHOT_NOT_SUPPORTED请求`CRecordset::Open`快照的调用失败。 驱动程序不支持快照。 （仅当 ODBC 游标库 ODBCCURS 时，才应发生这种情况。DLL 不存在。

- AFX_SQL_ERROR_SQL_CONFORMANCE 或`CDatabase::OpenEx``CDatabase::Open`调用的驱动程序不符合所需的 ODBC SQL 符合性级别"最小值"（SQL_OSC_MINIMUM）。

- AFX_SQL_ERROR_SQL_NO_TOTAL ODBC 驱动程序无法指定`CLongBinary`数据值的总大小。 操作可能失败，因为无法预分配全局内存块。

- AFX_SQL_ERROR_RECORDSET_READONLY您尝试更新只读记录集，或者数据源是只读的。 不能对记录集或其关联的`CDatabase`对象执行更新操作。

- SQL_ERROR 功能失败。 ODBC 函数`SQLError`返回的错误消息存储在数据成员中`m_strError`。

- SQL_INVALID_HANDLE功能由于环境句柄、连接句柄或语句句柄无效而失败。 这表示编程错误。 ODBC 函数`SQLError`没有其他信息。

SQL 预缀代码由 ODBC 定义。 AFX 前缀代码在 AFXDB 中定义。H，在 MFC_INCLUDE 中找到。

## <a name="cdbexceptionm_strerror"></a><a name="m_strerror"></a>国开行例外：m_strError

包含描述导致异常的错误的字符串。

### <a name="remarks"></a>备注

字符串用字母数字术语描述错误。 有关详细信息和示例，请参阅`m_strStateNativeOrigin`。

## <a name="cdbexceptionm_strstatenativeorigin"></a><a name="m_strstatenativeorigin"></a>国开行例外：：m_strStateNativeOrigin

包含描述导致异常的错误的字符串。

### <a name="remarks"></a>备注

字符串的形式是"状态：%s，本机：%ld，原点：%s"，其中格式代码按顺序替换为描述：

- SQLSTATE，一个空端端字符串，其中包含在 ODBC 函数`SQLError`的*szSqlState*参数中返回的五个字符错误代码。 SQLSTATE 值列在附录[A，ODBC 错误代码](/sql/odbc/reference/appendixes/appendix-a-odbc-error-codes)，在*ODBC 程序员的参考*中。 示例："S0022"。

- 特定于数据源的本机错误代码在`SQLError`函数的*pfNativeError*参数中返回。 例如：207。

- 在`SQLError`函数的*szErrorMsg*参数中返回的错误消息文本。 此消息由多个括号内的名称组成。 当错误从源传递给用户时，每个 ODBC 组件（数据源、驱动程序、驱动程序管理器）都会追加其自己的名字。 此信息有助于确定错误的来源。 示例： [微软][ODBC SQL 服务器驱动程序][SQL 服务器]

框架解释错误字符串并将其组件放入`m_strStateNativeOrigin`中。如果`m_strStateNativeOrigin`包含多个错误的信息，则错误由换行分隔。 框架将字母数字错误文本放入`m_strError`。

有关用于组成此字符串的代码的其他信息，请参阅*ODBC 程序员参考*中的[SQLError](/sql/odbc/reference/syntax/sqlerror-function)函数。

### <a name="example"></a>示例

从 ODBC："状态：S0022，本机：207，原点\[：微软\[] ODBC SQL\[服务器驱动程序* SQL 服务器* 无效列名称"ColName"

在`m_strStateNativeOrigin`： "状态：S0022，本机：207，\[原点\[：微软] ODBC\[SQL 服务器驱动程序* SQL 服务器*"

在`m_strError`： "无效列名称 'ColName'"

## <a name="see-also"></a>另请参阅

[CException 类](../../mfc/reference/cexception-class.md)<br/>
[层次结构图表](../../mfc/hierarchy-chart.md)<br/>
[CDatabase 类](../../mfc/reference/cdatabase-class.md)<br/>
[CRecordset 类](../../mfc/reference/crecordset-class.md)<br/>
[CFieldExchange 课程](../../mfc/reference/cfieldexchange-class.md)<br/>
[CRecordset：：更新](../../mfc/reference/crecordset-class.md#update)<br/>
[C记录集：:Delete](../../mfc/reference/crecordset-class.md#delete)<br/>
[CException 类](../../mfc/reference/cexception-class.md)
