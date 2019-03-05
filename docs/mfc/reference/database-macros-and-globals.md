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
ms.openlocfilehash: 47a1bb434801c24ab8eee048d9ef8f93793101cc
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/04/2019
ms.locfileid: "57268715"
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
|[AfxDbInitModule](#afxdbinitmodule)|添加了对动态链接到 MFC 的规则 MFC DLL 的数据库支持。|
|[AfxGetHENV](#afxgethenv)|检索 MFC 当前正在使用的 ODBC 环境的句柄。 您可以在直接 ODBC 调用中使用此句柄。|

## <a name="afxdbinitmodule"></a> AfxDbInitModule

有关 MFC 数据库 （或 DAO） 支持从动态链接到 MFC 的规则 MFC DLL，添加对此函数的调用在规则 MFC DLL 的`CWinApp::InitInstance`函数以初始化 MFC 数据库 DLL。

### <a name="syntax"></a>语法

```
void AFXAPI AfxDbInitModule( );
```

### <a name="remarks"></a>备注

请确保此调用之前的任何基类调用或任何添加的代码访问 MFC 数据库 DLL。 MFC 数据库 DLL 是 MFC 扩展 DLL;MFC 扩展 DLL 才能连接到`CDynLinkLibrary`链，它必须创建`CDynLinkLibrary`将使用它的每个模块的上下文中的对象。 `AfxDbInitModule` 创建`CDynLinkLibrary`对象在规则 MFC DLL 的上下文中，以便它连接到`CDynLinkLibrary`对象的规则 MFC DLL 链。

### <a name="requirements"></a>要求

**标头：** \<afxdll_.h >

##  <a name="afx_odbc_call"></a>  AFX_ODBC_CALL

使用此宏调用可能会返回任何 ODBC API 函数`SQL_STILL_EXECUTING`。

```
AFX_ODBC_CALL(SQLFunc)
```

### <a name="parameters"></a>参数

*SQLFunc*<br/>
ODBC API 函数。 有关 ODBC API 函数的详细信息，请参阅 Windows SDK。

### <a name="remarks"></a>备注

`AFX_ODBC_CALL` 将重复调用该函数之前不能再返回`SQL_STILL_EXECUTING`。

然后再调用`AFX_ODBC_CALL`，必须声明一个变量， `nRetCode`，类型 RETCODE。

请注意，MFC ODBC 类现在使用仅同步处理。 若要执行异步操作，必须调用 ODBC API 函数`SQLSetConnectOption`。 有关详细信息，请参阅"异步执行函数"Windows SDK 中的主题。

### <a name="example"></a>示例

此示例使用`AFX_ODBC_CALL`来调用`SQLColumns`ODBC API 函数时，它会在通过名为的表中返回的列的列表`strTableName`。 请注意声明`nRetCode`和记录集数据成员，将参数传递给函数的使用。 该示例还演示了如何检查与调用的结果`Check`，类的成员函数`CRecordset`。 在变量`prs`是一个指向`CRecordset`声明其他位置的对象。

[!code-cpp[NVC_MFCDatabase#39](../../mfc/codesnippet/cpp/database-macros-and-globals_1.cpp)]

### <a name="requirements"></a>要求

**标头：** afxdb.h

##  <a name="afx_sql_async"></a>  AFX_SQL_ASYNC

此宏的实现在 MFC 4.2 中发生更改。

```
AFX_SQL_ASYNC(prs, SQLFunc)
```

### <a name="parameters"></a>参数

*prs*<br/>
指向 `CRecordset` 对象或 `CDatabase` 对象的指针。 从 MFC 4.2 开始，将忽略此参数值。

*SQLFunc*<br/>
ODBC API 函数。 有关 ODBC API 函数的详细信息，请参阅 Windows SDK。

### <a name="remarks"></a>备注

`AFX_SQL_ASYNC` 简单调用宏[AFX_ODBC_CALL](#afx_odbc_call) ，并忽略*pr*参数。 在 4.2 之前的 MFC 版本中，`AFX_SQL_ASYNC` 用于调用可能返回 `SQL_STILL_EXECUTING` 的 ODBC API 函数。 如果 ODBC API 函数返回 `SQL_STILL_EXECUTING`，则 `AFX_SQL_ASYNC` 将调用 `prs->OnWaitForDataSource`。

> [!NOTE]
>  MFC ODBC 类现在只能使用同步处理。 若要执行异步操作，必须调用 ODBC API 函数`SQLSetConnectOption`。 有关详细信息，请参阅"异步执行函数"Windows SDK 中的主题。

### <a name="requirements"></a>要求

  **标头**afxdb.h

##  <a name="afx_sql_sync"></a>  AFX_SQL_SYNC

`AFX_SQL_SYNC`宏将只需调用该函数`SQLFunc`。

```
AFX_SQL_SYNC(SQLFunc)
```

### <a name="parameters"></a>参数

*SQLFunc*<br/>
ODBC API 函数。 有关这些函数的详细信息，请参阅 Windows SDK。

### <a name="remarks"></a>备注

使用此宏调用不会返回的 ODBC API 函数`SQL_STILL_EXECUTING`。

然后再调用`AFX_SQL_SYNC`，必须声明一个变量， `nRetCode`，类型 RETCODE。 你可以检查的值`nRetCode`宏调用之后。

请注意，实现`AFX_SQL_SYNC`在 MFC 4.2 中发生更改。 正在检查服务器状态不再是必需的因为`AFX_SQL_SYNC`只需将一个值赋给`nRetCode`。 例如，而不是进行调用

[!code-cpp[NVC_MFCDatabase#40](../../mfc/codesnippet/cpp/database-macros-and-globals_2.cpp)]

您可以只需进行分配

[!code-cpp[NVC_MFCDatabase#41](../../mfc/codesnippet/cpp/database-macros-and-globals_3.cpp)]

### <a name="requirements"></a>要求

  **标头**afxdb.h

##  <a name="afxgethenv"></a>  AfxGetHENV

可以在直接 ODBC 调用中，使用返回的句柄，但您不能关闭句柄或假定该句柄仍有效且可用后存在的任何`CDatabase`-或`CRecordset`-在销毁派生的对象。

```
HENV AFXAPI AfxGetHENV();
```

### <a name="return-value"></a>返回值

当前正在使用 MFC ODBC 环境句柄。 可以是`SQL_HENV_NULL`是否存在任何[CDatabase](../../mfc/reference/cdatabase-class.md)对象但没有[CRecordset](../../mfc/reference/crecordset-class.md)中使用的对象。

### <a name="requirements"></a>要求

  **标头**afxdb.h

## <a name="see-also"></a>请参阅

[宏和全局函数](../../mfc/reference/mfc-macros-and-globals.md)
