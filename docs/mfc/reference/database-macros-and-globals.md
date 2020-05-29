---
title: 数据库宏和全局函数
ms.date: 11/04/2016
f1_keywords:
- AFXDB/AFX_ODBC_CALL
- AFXDB/AFX_SQL_ASYNC
- AFXDB/AFX_SQL_SYNC
- AFXDB/AfxGetHENV
helpviewer_keywords:
- global database functions [MFC]
- database macros [MFC]
- database globals [MFC]
- global functions [MFC], database functions
- macros [MFC], MFC database
ms.assetid: 5b9b9e61-1cf9-4345-9f29-3807dd466488
ms.openlocfilehash: 6d8bd56c0bfe4f9b35e34d067dd1042ed11066d5
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/22/2020
ms.locfileid: "81751660"
---
# <a name="database-macros-and-globals"></a>数据库宏和全局函数

下面所列的宏和全局适用于基于 ODBC 的数据库应用程序。 它们不适用于基于 DAO 的应用程序。

在 MFC 4.2 版之前，宏 `AFX_SQL_ASYNC` 和 `AFX_SQL_SYNC` 为异步操作提供了为其他进程让出时间的机会。 从 MFC 4.2 开始，这些宏的实现已改变，因为 MFC ODBC 类仅使用同步操作。 宏 `AFX_ODBC_CALL` 是 MFC 4.2 中新增的。

### <a name="database-macros"></a>数据库宏

|||
|-|-|
|[AFX_ODBC_CALL](#afx_odbc_call)|调用返回 `SQL_STILL_EXECUTING` 的 ODBC API 函数。 `AFX_ODBC_CALL` 将反复调用该函数，直到不再返回 `SQL_STILL_EXECUTING`。|
|[AFX_SQL_ASYNC](#afx_sql_async)|调用 `AFX_ODBC_CALL`。|
|[AFX_SQL_SYNC](#afx_sql_sync)|调用不返回 `SQL_STILL_EXECUTING` 的 ODBC API 函数。|

### <a name="database-globals"></a>数据库全局

|||
|-|-|
|[AfxDbInitModule](#afxdbinitmodule)|添加对动态链接到 MFC 的常规 MFC DLL 的数据库支持。|
|[AfxGetHENV](#afxgethenv)|检索 MFC 当前正在使用的 ODBC 环境的句柄。 您可以在直接 ODBC 调用中使用此句柄。|

## <a name="afxdbinitmodule"></a><a name="afxdbinitmodule"></a>AfxDbinit 模块

对于动态链接到 MFC 的常规 MFC DLL 的 MFC 数据库（或 DAO）支持，在常规 MFC DLL 函数中添加`CWinApp::InitInstance`对此函数的调用，以初始化 MFC 数据库 DLL。

### <a name="syntax"></a>语法

```cpp
void AFXAPI AfxDbInitModule( );
```

### <a name="remarks"></a>备注

请确保此调用发生在任何基类调用或访问 MFC 数据库 DLL 的任何添加代码之前。 MFC 数据库 DLL 是 MFC 扩展 DLL;为了使 MFC 扩展 DLL 连接到`CDynLinkLibrary`链中，它必须在将使用它的每个模块`CDynLinkLibrary`的上下文中创建一个对象。 `AfxDbInitModule`在`CDynLinkLibrary`常规 MFC DLL 的上下文中创建对象，以便将其连接到常规 MFC DLL`CDynLinkLibrary`的对象链中。

### <a name="requirements"></a>要求

**标题：** \<afxdll_.h>

## <a name="afx_odbc_call"></a><a name="afx_odbc_call"></a>AFX_ODBC_CALL

使用此宏可以调用任何可能返回`SQL_STILL_EXECUTING`的 ODBC API 函数。

```
AFX_ODBC_CALL(SQLFunc)
```

### <a name="parameters"></a>参数

*SQLFunc*<br/>
ODBC API 函数。 有关 ODBC API 功能的详细信息，请参阅 Windows SDK。

### <a name="remarks"></a>备注

`AFX_ODBC_CALL`重复调用函数，直到它不再返回`SQL_STILL_EXECUTING`。

在调用`AFX_ODBC_CALL`之前，必须声明类型 RETCODE 的变量`nRetCode`，

请注意，MFC ODBC 类现在仅使用同步处理。 为了执行异步操作，必须调用 ODBC API 函数`SQLSetConnectOption`。 有关详细信息，请参阅 Windows SDK 中的主题"异步执行函数"。

### <a name="example"></a>示例

此示例用于`AFX_ODBC_CALL`调用`SQLColumns`ODBC API 函数，该函数返回由`strTableName`命名的表中的列的列表。 请注意记录集数据`nRetCode`成员的声明和使用，以将参数传递给函数。 该示例还演示了使用`Check`检查调用的结果，该函数是类`CRecordset`的成员函数。 变量`prs`是指向`CRecordset`对象的指针，声明在其他地方。

[!code-cpp[NVC_MFCDatabase#39](../../mfc/codesnippet/cpp/database-macros-and-globals_1.cpp)]

### <a name="requirements"></a>要求

**标题：** afxdb.h

## <a name="afx_sql_async"></a><a name="afx_sql_async"></a>AFX_SQL_ASYNC

此宏的实现在 MFC 4.2 中发生更改。

```
AFX_SQL_ASYNC(prs, SQLFunc)
```

### <a name="parameters"></a>参数

*prs*<br/>
指向 `CRecordset` 对象或 `CDatabase` 对象的指针。 从 MFC 4.2 开始，将忽略此参数值。

*SQLFunc*<br/>
ODBC API 函数。 有关 ODBC API 功能的详细信息，请参阅 Windows SDK。

### <a name="remarks"></a>备注

`AFX_SQL_ASYNC`只需调用宏[AFX_ODBC_CALL](#afx_odbc_call)并忽略*prs*参数。 在 4.2 之前的 MFC 版本中，`AFX_SQL_ASYNC` 用于调用可能返回 `SQL_STILL_EXECUTING` 的 ODBC API 函数。 如果 ODBC API 函数返回 `SQL_STILL_EXECUTING`，则 `AFX_SQL_ASYNC` 将调用 `prs->OnWaitForDataSource`。

> [!NOTE]
> MFC ODBC 类现在只能使用同步处理。 为了执行异步操作，必须调用 ODBC API 函数`SQLSetConnectOption`。 有关详细信息，请参阅 Windows SDK 中的主题"异步执行函数"。

### <a name="requirements"></a>要求

  **头**afxdb.h

## <a name="afx_sql_sync"></a><a name="afx_sql_sync"></a>AFX_SQL_SYNC

宏`AFX_SQL_SYNC`只是调用 函数`SQLFunc`。

```
AFX_SQL_SYNC(SQLFunc)
```

### <a name="parameters"></a>参数

*SQLFunc*<br/>
ODBC API 函数。 有关这些功能的详细信息，请参阅 Windows SDK。

### <a name="remarks"></a>备注

使用此宏可以调用不会返回`SQL_STILL_EXECUTING`的 ODBC API 函数。

在调用`AFX_SQL_SYNC`之前，必须声明 RETCODE 类型的变量`nRetCode`， 您可以在宏调用后检查`nRetCode`的值。

请注意，MFC `AFX_SQL_SYNC` 4.2 中的实现已更改。 由于不再需要检查服务器状态，`AFX_SQL_SYNC`因此只需将值分配给 。 `nRetCode` 例如，而不是进行调用

[!code-cpp[NVC_MFCDatabase#40](../../mfc/codesnippet/cpp/database-macros-and-globals_2.cpp)]

你可以简单地做分配

[!code-cpp[NVC_MFCDatabase#41](../../mfc/codesnippet/cpp/database-macros-and-globals_3.cpp)]

### <a name="requirements"></a>要求

  **头**afxdb.h

## <a name="afxgethenv"></a><a name="afxgethenv"></a>阿夫达赫内夫

您可以在直接 ODBC 调用中使用返回的句柄，但不得关闭句柄或假定该句柄在任何现有`CDatabase`或`CRecordset`派生对象被销毁后仍然有效且可用。

```
HENV AFXAPI AfxGetHENV();
```

### <a name="return-value"></a>返回值

对 MFC 当前正在使用的 ODBC 环境的句柄。 `SQL_HENV_NULL`如果没有[CDatabase](../../mfc/reference/cdatabase-class.md)对象，并且没有[CRecordset](../../mfc/reference/crecordset-class.md)对象正在使用，则可以。

### <a name="requirements"></a>要求

  **头**afxdb.h

## <a name="see-also"></a>请参阅

[MFC 宏和全局函数](../../mfc/reference/mfc-macros-and-globals.md)
