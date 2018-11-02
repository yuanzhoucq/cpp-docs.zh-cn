---
title: CCommand 类
ms.date: 11/04/2016
f1_keywords:
- ATL::CCommand
- CCommand
- ATL.CCommand
- CCommand.Close
- CCommand::Close
- CCommand.Create
- CCommand::Create
- CCommand.CreateCommand
- CreateCommand
- CCommand::CreateCommand
- ATL::CCommand::GetNextResult
- CCommand::GetNextResult
- GetNextResult
- CCommand.GetNextResult
- ATL.CCommand.GetNextResult
- GetParameterInfo
- CCommand.GetParameterInfo
- CCommand::GetParameterInfo
- ATL.CCommand.Open
- ATL::CCommand::Open
- CCommand.Open
- CCommand::Open
- CCommand.Prepare
- CCommand::Prepare
- Prepare
- CCommand.ReleaseCommand
- ReleaseCommand
- CCommand::ReleaseCommand
- SetParameterInfo
- CCommand.SetParameterInfo
- CCommand::SetParameterInfo
- Unprepare
- CCommand.Unprepare
- CCommand::Unprepare
helpviewer_keywords:
- CCommand class
- Close method
- Create method [C++]
- CreateCommand method
- GetNextResult method
- GetParameterInfo method
- Open method
- Prepare method
- ReleaseCommand method
- SetParameterInfo method
- Unprepare method
ms.assetid: 0760bfc5-b9ee-4aee-8e54-31bd78714d3a
ms.openlocfilehash: 64774f5a8a81d7c4b3432800376c00f7d1e96d62
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50596841"
---
# <a name="ccommand-class"></a>CCommand 类

提供设置和执行命令的方法。

## <a name="syntax"></a>语法

```cpp
template <class TAccessor = CNoAccessor,
   template <typename T> class TRowset = CRowset,
   class TMultiple = CNoMultipleResults>
class CCommand :
   public CAccessorRowset <TAccessor, TRowset>,
   public CCommandBase,
   public TMultiple
```

### <a name="parameters"></a>参数

*TAccessor*<br/>
你希望命令使用的访问器类的类型（如 `CDynamicParameterAccessor`、`CDynamicStringAccessor` 或 `CEnumeratorAccessor`）。 默认值为 `CNoAccessor`，它指定该类不支持参数或输出列。

*TRowset*<br/>
您希望命令使用的行集类的类型（如 `CArrayRowset` 或 `CNoRowset`）。 默认值为 `CRowset`。

*TMultiple*<br/>
若要使用 OLE DB 命令可以返回多个结果，指定[CMultipleResults](../../data/oledb/cmultipleresults-class.md)。 否则，请使用[CNoMultipleResults](../../data/oledb/cnomultipleresults-class.md)。 有关详细信息，请参阅[IMultipleResults](/previous-versions/windows/desktop/ms721289)。

## <a name="requirements"></a>要求

**标头:** atldbcli.h

## <a name="members"></a>成员

### <a name="methods"></a>方法

|||
|-|-|
|[关闭](#close)|关闭当前命令。|
|[GetNextResult](#getnextresult)|在使用多个结果集时提取下一个结果。|
|[打开](#open)|执行并选择性地绑定命令。|

### <a name="inherited-methods"></a>继承的方法

|||
|-|-|
|[创建](#create)|为指定会话创建新命令，然后设置命令文本。|
|[CreateCommand](#createcommand)|创建新的命令。|
|[GetParameterInfo](#getparameterinfo)|获取命令的参数、参数名称和参数类型的列表。|
|[准备](#prepare)|验证并优化当前命令。|
|[ReleaseCommand](#releasecommand)|在必要时释放参数访问器，然后释放命令。|
|[SetParameterInfo](#setparameterinfo)|指定每个命令参数的本机类型。|
|[Unprepare](#unprepare)|放弃当前命令执行计划。|

## <a name="remarks"></a>备注

当您需要执行基于参数的操作或执行命令时，请使用此类。 如果你只需打开一个简单的行集，使用[CTable](../../data/oledb/ctable-class.md)相反。

使用的访问器类可确定绑定参数和数据的方法。

请注意，不能将存储过程与 Jet 的 OLE DB 提供程序一起使用，因为该提供程序不支持存储过程（查询字符串中只允许使用常数）。

## <a name="close"></a> Ccommand:: Close

发布与命令关联的访问器行集。

### <a name="syntax"></a>语法

```cpp
void Close();
```

### <a name="remarks"></a>备注

命令使用行集、结果集访问器和（可选的）参数访问器（与不支持参数并且不需要参数访问器的表不同）。

在执行命令时，应将同时调用`Close`并[ReleaseCommand](../../data/oledb/ccommand-releasecommand.md)的命令。

当你要重复执行同一命令时，你应通过在调用 `Close` 之前调用 `Execute` 来发布每个结果集访问器。 在序列末尾，应通过调用 `ReleaseCommand` 发布参数访问器。 另一种常见情形是调用具有输出参数的存储过程。 在很多提供程序（如 SQL Server 的 OLE DB 提供程序）上，输出参数值在你关闭结果集访问器前不可访问。 调用 `Close` 以关闭返回的行集和结果集访问器而不返回参数访问器，从而让你检索输出参数值。

### <a name="example"></a>示例

以下示例演示在重复执行同一命令时如何调用 `Close` 和 `ReleaseCommand`。

[!code-cpp[NVC_OLEDB_Consumer#2](../../data/oledb/codesnippet/cpp/ccommand-close_1.cpp)]

## <a name="getnextresult"></a> Ccommand:: Getnextresult

提取下一个结果集之一是否可用。

### <a name="syntax"></a>语法

```cpp
HRESULT GetNextResult(DBROWCOUNT* pulRowsAffected,
   bool bBind = true) throw();
```

#### <a name="parameters"></a>参数

*pulRowsAffected*<br/>
[输入/输出]指向内存位置返回受命令影响的行数的指针。

*bBind*<br/>
[in]指定是否正在执行后自动绑定命令。 默认值是 **，则返回 true**，这将导致自动绑定的命令。 设置*bBind*到**false**可防止自动绑定命令，以便您可以手动绑定。 （手动绑定是 OLAP 用户特别关注。）

### <a name="return-value"></a>返回值

标准的 HRESULT。

### <a name="remarks"></a>备注

如果先前已读取结果集，此函数释放以前的结果集，并取消绑定列。 如果*bBind*是**true**，它将新列绑定。

仅当你通过设置指定多个结果，应调用此函数`CCommand`模板参数*TMultiple*=`CMultipleResults`。

## <a name="open"></a> Ccommand:: Open

执行并选择性地绑定命令。

### <a name="syntax"></a>语法

```cpp
HRESULT Open(const CSession& session,
   LPCWSTR wszCommand,
   DBPROPSET *pPropSet = NULL,
   DBROWCOUNT* pRowsAffected = NULL,
   REFGUID guidCommand = DBGUID_DEFAULT,
   bool bBind = true,
   ULONG ulPropSets = 0) throw();

HRESULT Open(const CSession& session,
   LPCSTR szCommand,
   DBPROPSET *pPropSet = NULL,
   DBROWCOUNT* pRowsAffected = NULL,
   REFGUID guidCommand = DBGUID_DEFAULT,
   bool bBind = true,
   ULONG ulPropSets = 0) throw();

HRESULT Open(const CSession& session,
   INT szCommand = NULL,
   DBPROPSET *pPropSet = NULL,
   DBROWCOUNT* pRowsAffected = NULL,
   REFGUID guidCommand = DBGUID_DEFAULT,
   bool bBind = true,
   ULONG ulPropSets = 0) throw();

HRESULT Open(DBPROPSET *pPropSet = NULL,
   DBROWCOUNT* pRowsAffected = NULL,
   bool bBind = true,
   ULONG ulPropSets = 0) throw();
```

#### <a name="parameters"></a>参数

*会话*<br/>
[in]在其中执行命令会话。

*wszCommand*<br/>
[in]若要执行，该命令传递为 Unicode 字符串。 使用时，可以为 NULL `CAccessor`，在这种情况下该命令将检索传递给的值从[DEFINE_COMMAND](../../data/oledb/define-command.md)宏。 请参阅[icommand:: Execute](/previous-versions/windows/desktop/ms718095)中*OLE DB 程序员参考*有关详细信息。

*szCommand*<br/>
[in]与相同*wszCommand*只不过此参数采用 ANSI 命令字符串。 此方法的第四个窗体可以采用 NULL 值。 有关详细信息的本主题中的更高版本，请参阅"备注"。

*pPropSet*<br/>
[in]指向数组的指针[DBPROPSET](/previous-versions/windows/desktop/ms714367)结构包含要设置属性和值。 请参阅[属性设置和属性组](/previous-versions/windows/desktop/ms713696)中*OLE DB 程序员参考*Windows SDK 中。

*pRowsAffected*<br/>
[输入/输出]指向内存位置返回受命令影响的行数的指针。 如果 *\*pRowsAffected*为 NULL，会返回任何行。 否则为`Open`设置 *\*pRowsAffected*根据以下条件：

|如果|Then|
|--------|----------|
|`cParamSets`元素的`pParams`大于 1|*\*pRowsAffected*表示受影响的执行过程中指定的参数集的所有行的总数。|
|受影响的行数不可用|*\*pRowsAffected*设置为-1。|
|该命令不会更新、 删除或插入行|*\*pRowsAffected*是不确定的。|

*guidCommand*<br/>
[in]分析命令文本中指定的语法和一般规则要使用的提供程序的 GUID。 请参阅[ICommandText::GetCommandText](/previous-versions/windows/desktop/ms709825)并[icommandtext:: Setcommandtext](/previous-versions/windows/desktop/ms709757)中*OLE DB 程序员参考*有关详细信息。

*bBind*<br/>
[in]指定是否正在执行后自动绑定命令。 默认值是 **，则返回 true**，这将导致自动绑定的命令。 设置*bBind*到**false**可防止自动绑定命令，以便您可以手动绑定。 （手动绑定是 OLAP 用户特别关注。）

*ulPropSets*<br/>
[in]数[DBPROPSET](/previous-versions/windows/desktop/ms714367)结构传入*pPropSet*参数。

### <a name="return-value"></a>返回值

标准的 HRESULT。

### <a name="remarks"></a>备注

前三个形式的`Open`需要会话，创建一个命令，并执行命令，根据需要绑定任何参数。

第一种形式`Open`Unicode 命令字符串，并没有默认值。

第二种形式的`Open`采用 ANSI 命令字符串，并且没有默认值 （为了向后兼容现有的 ANSI 应用程序提供）。

第三种形式`Open`允许命令字符串为 NULL，因为类型**int**默认值为 NULL。 提供用于调用`Open(session, NULL);`或`Open(session);`因为 NULL 的类型**int**。此版本要求，断言**int**参数为 NULL。

使用的第四个形式`Open`当你已创建命令并且想要执行单个[准备](../../data/oledb/ccommand-prepare.md)和多个执行。

> [!NOTE]
>  `Open` 调用`Execute`，从而又会调用`GetNextResult`。

## <a name="create"></a> Ccommand:: Create

调用[ccommand:: Createcommand](../../data/oledb/ccommand-createcommand.md)命令创建为指定的会话，然后调用[icommandtext:: Setcommandtext](/previous-versions/windows/desktop/ms709825)指定的命令文本。

### <a name="syntax"></a>语法

```cpp
HRESULT CCommandBase::Create(const CSession& session,
   LPCWSTR wszCommand,
   REFGUID guidCommand = DBGUID_DEFAULT) throw ();

HRESULT CCommandBase::Create(const CSession& session,
   LPCSTR szCommand,
   REFGUID guidCommand = DBGUID_DEFAULT) throw ();
```

#### <a name="parameters"></a>参数

*会话*<br/>
[in]在其上创建命令会话。

*wszCommand*<br/>
[in]指向 Unicode 文本的命令字符串的指针。

*szCommand*<br/>
[in]ANSI 的文本命令字符串的指针。

*guidCommand*<br/>
[in]分析命令文本中指定的语法和一般规则要使用的提供程序的 GUID。 本地语言的说明，请参阅[ICommandText::GetCommandText](/previous-versions/windows/desktop/ms709825)中*OLE DB 程序员参考*。

### <a name="return-value"></a>返回值

标准的 HRESULT。

### <a name="remarks"></a>备注

第一种形式`Create`采用 Unicode 命令字符串。 第二种形式的`Create`采用 ANSI 命令字符串 （为了向后兼容现有的 ANSI 应用程序提供）。

## <a name="createcommand"></a> Ccommand:: Createcommand

创建新的命令。

### <a name="syntax"></a>语法

```cpp
HRESULT CCommandBase::CreateCommand(const CSession& session) throw ();
```

#### <a name="parameters"></a>参数

*会话*<br/>
[in]一个`CSession`对象要与新的命令相关联。

### <a name="return-value"></a>返回值

标准的 HRESULT。

### <a name="remarks"></a>备注

此方法创建使用指定的会话对象的命令。

## <a name="getparameterinfo"></a> Ccommand:: Getparameterinfo

获取命令的参数、参数名称和参数类型的列表。

### <a name="syntax"></a>语法

```cpp
HRESULT CCommandBase::GetParameterInfo(DB_UPARAMS* pParams,
   DBPARAMINFO** ppParamInfo,
   OLECHAR** ppNamesBuffer) throw ();
```

#### <a name="parameters"></a>参数

请参阅[icommandwithparameters:: Getparameterinfo](/previous-versions/windows/desktop/ms714917)中*OLE DB 程序员参考*。

### <a name="return-value"></a>返回值

标准的 HRESULT。

## <a name="prepare"></a> Ccommand:: Prepare

验证并优化当前命令。

### <a name="syntax"></a>语法

```cpp
HRESULT CCommandBase::Prepare(ULONG cExpectedRuns = 0) throw();
```

#### <a name="parameters"></a>参数

*cExpectedRuns*<br/>
[in]您希望执行命令次数。

### <a name="return-value"></a>返回值

标准的 HRESULT。

### <a name="remarks"></a>备注

此方法将 OLE DB 方法包装[icommandprepare:: Prepare](/previous-versions/windows/desktop/ms718370)。

## <a name="releasecommand"></a> Ccommand:: Releasecommand

释放参数访问器，然后释放命令本身。

### <a name="syntax"></a>语法

```cpp
void CCommandBase::ReleaseCommand() throw();
```

### <a name="remarks"></a>备注

`ReleaseCommand` 结合使用`Close`。 请参阅[关闭](../../data/oledb/ccommand-close.md)使用情况详细信息。

## <a name="setparameterinfo"></a> Ccommand:: Setparameterinfo

指定每个命令参数的本机类型。

### <a name="syntax"></a>语法

```cpp
HRESULT CCommandBase::SetParameterInfo(DB_UPARAMS ulParams,
   const DBORDINAL* pOrdinals,
   const DBPARAMBINDINFO* pParamInfo) throw();
```

#### <a name="parameters"></a>参数

请参阅[icommandwithparameters:: Setparameterinfo](/previous-versions/windows/desktop/ms725393)中*OLE DB 程序员参考*。

### <a name="return-value"></a>返回值

标准的 HRESULT。

## <a name="unprepare"></a> Ccommand:: Unprepare

放弃当前命令执行计划。

### <a name="syntax"></a>语法

```cpp
HRESULT CCommandBase::Unprepare() throw();
```

### <a name="return-value"></a>返回值

标准的 HRESULT。

### <a name="remarks"></a>备注

此方法将 OLE DB 方法包装[icommandprepare:: Unprepare](/previous-versions/windows/desktop/ms719635)。

## <a name="see-also"></a>请参阅

[OLE DB 使用者模板](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[OLE DB 使用者模板参考](../../data/oledb/ole-db-consumer-templates-reference.md)