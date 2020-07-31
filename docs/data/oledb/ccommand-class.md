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
ms.openlocfilehash: 73b02f0ffb9d9b98a17933cc3b17c8627121e3ac
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87228916"
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
若要使用可以返回多个结果的 OLE DB 命令，请指定[CMultipleResults](../../data/oledb/cmultipleresults-class.md)。 否则，请使用[CNoMultipleResults](../../data/oledb/cnomultipleresults-class.md)。 有关详细信息，请参阅[IMultipleResults](/previous-versions/windows/desktop/ms721289(v=vs.85))。

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

需要执行基于参数的操作或执行命令时，请使用此类。 如果只需打开简单行集，请改用[CTable](../../data/oledb/ctable-class.md) 。

使用的访问器类可确定绑定参数和数据的方法。

请注意，不能将存储过程与 Jet 的 OLE DB 提供程序一起使用，因为该提供程序不支持存储过程（查询字符串中只允许使用常数）。

## <a name="ccommandclose"></a><a name="close"></a>CCommand：： Close

发布与命令关联的访问器行集。

### <a name="syntax"></a>语法

```cpp
void Close();
```

### <a name="remarks"></a>备注

命令使用行集、结果集访问器和（可选的）参数访问器（与不支持参数并且不需要参数访问器的表不同）。

执行命令时，应在命令后同时调用 `Close` 和[ReleaseCommand](../../data/oledb/ccommand-releasecommand.md) 。

当你要重复执行同一命令时，你应通过在调用 `Close` 之前调用 `Execute` 来发布每个结果集访问器。 在序列末尾，应通过调用 `ReleaseCommand` 发布参数访问器。 另一种常见情形是调用具有输出参数的存储过程。 在很多提供程序（如 SQL Server 的 OLE DB 提供程序）上，输出参数值在您关闭结果集访问器前不可访问。 调用 `Close` 以关闭返回的行集和结果集访问器而不返回参数访问器，从而让你检索输出参数值。

### <a name="example"></a>示例

以下示例演示在重复执行同一命令时如何调用 `Close` 和 `ReleaseCommand`。

[!code-cpp[NVC_OLEDB_Consumer#2](../../data/oledb/codesnippet/cpp/ccommand-close_1.cpp)]

## <a name="ccommandgetnextresult"></a><a name="getnextresult"></a>CCommand：： GetNextResult

提取下一个结果集（如果有）。

### <a name="syntax"></a>语法

```cpp
HRESULT GetNextResult(DBROWCOUNT* pulRowsAffected,
   bool bBind = true) throw();
```

#### <a name="parameters"></a>参数

*pulRowsAffected*<br/>
[in/out]一个指向内存的指针，它将返回受命令影响的行计数。

*bBind*<br/>
中指定是否在执行后自动绑定命令。 默认值为 **`true`** ，这将导致自动绑定命令。 将*bBind*设置为可 **`false`** 阻止自动绑定命令，以便可以手动绑定。 （手动绑定对 OLAP 用户特别感兴趣。）

### <a name="return-value"></a>返回值

标准的 HRESULT。

### <a name="remarks"></a>备注

如果以前已获取结果集，则此函数将释放以前的结果集并取消绑定列。 如果*bBind*为 **`true`** ，则绑定新列。

仅当通过设置 `CCommand` 模板参数*TMultiple*指定了多个结果时，才应调用此函数 = `CMultipleResults` 。

## <a name="ccommandopen"></a><a name="open"></a>CCommand：： Open

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

*会议*<br/>
中要在其中执行命令的会话。

*wszCommand*<br/>
中作为 Unicode 字符串传递的要执行的命令。 使用时可以为 NULL `CAccessor` ，在这种情况下，将从传递给[DEFINE_COMMAND](../../data/oledb/define-command.md)宏的值中检索命令。 有关详细信息，请参阅*OLE DB 程序员参考*中的[ICommand：： Execute](/previous-versions/windows/desktop/ms718095(v=vs.85)) 。

*szCommand*<br/>
中与*wszCommand*相同，只不过此参数使用 ANSI 命令字符串。 此方法的第四种形式可以采用 NULL 值。 有关详细信息，请参阅本主题后面的 "备注"。

*pPropSet*<br/>
中指向包含要设置的属性和值的[DBPROPSET](/previous-versions/windows/desktop/ms714367(v=vs.85))结构的数组的指针。 请参阅 Windows SDK 中*OLE DB 程序员参考*中的[属性集和属性组](/previous-versions/windows/desktop/ms713696(v=vs.85))。

*pRowsAffected*<br/>
[in/out]一个指向内存的指针，它将返回受命令影响的行计数。 如果* \* PROWSAFFECTED*为 NULL，则不返回行计数。 否则， `Open` 根据以下条件设置* \* pRowsAffected* ：

|如果|Then|
|--------|----------|
|的 `cParamSets` 元素 `pParams` 大于1|* \* pRowsAffected*表示在执行中指定的所有参数集所影响的总行数。|
|受影响的行数不可用|* \* pRowsAffected*设置为-1。|
|此命令不会更新、删除或插入行|* \* pRowsAffected*未定义。|

*guidCommand*<br/>
中一个 GUID，指定提供程序在分析命令文本时使用的语法和一般规则。 有关详细信息，请参阅*OLE DB 程序员参考*中的[ICommandText：： GetCommandText](/previous-versions/windows/desktop/ms709825(v=vs.85))和[ICommandText：： SetCommandText](/previous-versions/windows/desktop/ms709757(v=vs.85)) 。

*bBind*<br/>
中指定是否在执行后自动绑定命令。 默认值为 **`true`** ，这将导致自动绑定命令。 将*bBind*设置为可 **`false`** 阻止自动绑定命令，以便可以手动绑定。 （手动绑定对 OLAP 用户特别感兴趣。）

*ulPropSets*<br/>
中在*传入 ppropset*参数中传递的[DBPROPSET](/previous-versions/windows/desktop/ms714367(v=vs.85))结构的数目。

### <a name="return-value"></a>返回值

标准的 HRESULT。

### <a name="remarks"></a>备注

的前三种形式 `Open` 会创建一个会话，创建一个命令，然后执行该命令，并根据需要绑定任何参数。

的第一种形式 `Open` 采用 Unicode 命令字符串并且没有默认值。

的第二种形式 `Open` 采用 ANSI 命令字符串并且没有默认值（提供它是为了与现有 ANSI 应用程序向后兼容）。

的第三种形式 `Open` 允许命令字符串为 null，因为类型的 **`int`** 默认值为 null。 提供此方法是为了调用 `Open(session, NULL);` 或， `Open(session);` 因为 NULL 的类型为 **`int`** 。 此版本需要并断言 **`int`** 参数为 NULL。

`Open`如果已创建了一个命令并且想要执行单个[准备](../../data/oledb/ccommand-prepare.md)和多个执行，请使用第四种形式的。

> [!NOTE]
> `Open`调用 `Execute` ，后者又调用 `GetNextResult` 。

## <a name="ccommandcreate"></a><a name="create"></a>CCommand：： Create

调用[CCommand：： CreateCommand](../../data/oledb/ccommand-createcommand.md)来为指定的会话创建命令，然后调用[ICommandText：： SetCommandText](/previous-versions/windows/desktop/ms709825(v=vs.85))来指定命令文本。

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

*会议*<br/>
中要在其上创建命令的会话。

*wszCommand*<br/>
中指向命令字符串的 Unicode 文本的指针。

*szCommand*<br/>
中指向命令字符串的 ANSI 文本的指针。

*guidCommand*<br/>
中一个 GUID，指定提供程序在分析命令文本时使用的语法和一般规则。 有关方言的说明，请参阅*OLE DB 程序员参考*中的[ICommandText：： GetCommandText](/previous-versions/windows/desktop/ms709825(v=vs.85)) 。

### <a name="return-value"></a>返回值

标准的 HRESULT。

### <a name="remarks"></a>备注

的第一种形式 `Create` 采用 Unicode 命令字符串。 的第二种形式 `Create` 采用 ANSI 命令字符串（提供以便与现有 ANSI 应用程序向后兼容）。

## <a name="ccommandcreatecommand"></a><a name="createcommand"></a>CCommand：： CreateCommand

创建新的命令。

### <a name="syntax"></a>语法

```cpp
HRESULT CCommandBase::CreateCommand(const CSession& session) throw ();
```

#### <a name="parameters"></a>参数

*会议*<br/>
中`CSession`要与新命令关联的对象。

### <a name="return-value"></a>返回值

标准的 HRESULT。

### <a name="remarks"></a>备注

此方法使用指定的会话对象创建一个命令。

## <a name="ccommandgetparameterinfo"></a><a name="getparameterinfo"></a>CCommand：： GetParameterInfo

获取命令的参数、参数名称和参数类型的列表。

### <a name="syntax"></a>语法

```cpp
HRESULT CCommandBase::GetParameterInfo(DB_UPARAMS* pParams,
   DBPARAMINFO** ppParamInfo,
   OLECHAR** ppNamesBuffer) throw ();
```

#### <a name="parameters"></a>参数

请参阅*OLE DB 程序员参考*中的[ICommandWithParameters：： GetParameterInfo](/previous-versions/windows/desktop/ms714917(v=vs.85)) 。

### <a name="return-value"></a>返回值

标准的 HRESULT。

## <a name="ccommandprepare"></a><a name="prepare"></a>CCommand：:P 准备

验证并优化当前命令。

### <a name="syntax"></a>语法

```cpp
HRESULT CCommandBase::Prepare(ULONG cExpectedRuns = 0) throw();
```

#### <a name="parameters"></a>参数

*cExpectedRuns*<br/>
中希望执行命令的次数。

### <a name="return-value"></a>返回值

标准的 HRESULT。

### <a name="remarks"></a>备注

此方法包装 OLE DB 方法[ICommandPrepare：:P 准备](/previous-versions/windows/desktop/ms718370(v=vs.85))。

## <a name="ccommandreleasecommand"></a><a name="releasecommand"></a>CCommand：： ReleaseCommand

释放参数访问器，然后释放命令本身。

### <a name="syntax"></a>语法

```cpp
void CCommandBase::ReleaseCommand() throw();
```

### <a name="remarks"></a>备注

`ReleaseCommand`与结合使用 `Close` 。 有关使用情况详细信息，请参阅[Close](../../data/oledb/ccommand-close.md) 。

## <a name="ccommandsetparameterinfo"></a><a name="setparameterinfo"></a>CCommand：： SetParameterInfo

指定每个命令参数的本机类型。

### <a name="syntax"></a>语法

```cpp
HRESULT CCommandBase::SetParameterInfo(DB_UPARAMS ulParams,
   const DBORDINAL* pOrdinals,
   const DBPARAMBINDINFO* pParamInfo) throw();
```

#### <a name="parameters"></a>参数

请参阅*OLE DB 程序员参考*中的[ICommandWithParameters：： SetParameterInfo](/previous-versions/windows/desktop/ms725393(v=vs.85)) 。

### <a name="return-value"></a>返回值

标准的 HRESULT。

## <a name="ccommandunprepare"></a><a name="unprepare"></a>CCommand：： Unprepare

放弃当前命令执行计划。

### <a name="syntax"></a>语法

```cpp
HRESULT CCommandBase::Unprepare() throw();
```

### <a name="return-value"></a>返回值

标准的 HRESULT。

### <a name="remarks"></a>备注

此方法包装 OLE DB 方法[ICommandPrepare：： Unprepare](/previous-versions/windows/desktop/ms719635(v=vs.85))。

## <a name="see-also"></a>另请参阅

[OLE DB 使用者模板](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[OLE DB 使用者模板参考](../../data/oledb/ole-db-consumer-templates-reference.md)
