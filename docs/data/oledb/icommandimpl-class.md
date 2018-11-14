---
title: ICommandImpl 类
ms.date: 11/04/2016
f1_keywords:
- ICommandImpl
- ICommandImpl::Cancel
- Cancel
- ICommandImpl.Cancel
- ICommandImpl::CancelExecution
- ATL::ICommandImpl::CancelExecution
- ATL.ICommandImpl.CancelExecution
- CancelExecution
- ICommandImpl.CancelExecution
- ICommandImpl::CreateRowset
- ICommandImpl.CreateRowset
- CreateRowset
- ICommandImpl::Execute
- ICommandImpl.Execute
- ICommandImpl::GetDBSession
- GetDBSession
- ICommandImpl.GetDBSession
- ATL.ICommandImpl.ICommandImpl
- ATL::ICommandImpl::ICommandImpl
- ICommandImpl
- ICommandImpl::ICommandImpl
- ICommandImpl.ICommandImpl
- ICommandImpl::m_bCancel
- ICommandImpl.m_bCancel
- m_bCancel
- ATL::ICommandImpl::m_bCancel
- ATL.ICommandImpl.m_bCancel
- ICommandImpl::m_bCancelWhenExecuting
- ICommandImpl.m_bCancelWhenExecuting
- ATL::ICommandImpl::m_bCancelWhenExecuting
- m_bCancelWhenExecuting
- ATL.ICommandImpl.m_bCancelWhenExecuting
- ICommandImpl.m_bIsExecuting
- ATL::ICommandImpl::m_bIsExecuting
- m_bIsExecuting
- ATL.ICommandImpl.m_bIsExecuting
- ICommandImpl::m_bIsExecuting
helpviewer_keywords:
- ICommandImpl class
- Cancel method
- CancelExecution method
- CreateRowset method
- Execute method
- GetDBSession method
- ICommandImpl constructor
- ICommandImpl class, constructor
- m_bCancel
- m_bCancelWhenExecuting
- m_bIsExecuting
ms.assetid: ef285fef-0d66-45e6-a762-b03357098e3b
ms.openlocfilehash: c5e599b437f7660801a1eb40618eb49bee84a918
ms.sourcegitcommit: c40469825b6101baac87d43e5f4aed6df6b078f5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/12/2018
ms.locfileid: "51556811"
---
# <a name="icommandimpl-class"></a>ICommandImpl 类

提供用于实现[ICommand](https://docs.microsoft.com/previous-versions/windows/desktop/ms709737(v=vs.85))接口。

## <a name="syntax"></a>语法

```cpp
template <class T, class CommandBase = ICommand>
class ATL_NO_VTABLE ICommandImpl : public CommandBase
```

### <a name="parameters"></a>参数

*T*<br/>
您的类，派生自`ICommandImpl`。

*CommandBase*<br/>
一个命令接口。 默认值为 `ICommand`。

## <a name="requirements"></a>要求

**标头：** atldb.h

## <a name="members"></a>成员

### <a name="methods"></a>方法

|||
|-|-|
|[取消](#cancel)|取消当前命令执行。|
|[CancelExecution](#cancelexecution)|取消当前命令执行。|
|[CreateRowset](#createrowset)|创建一个行集对象。|
|[Execute](#execute)|执行的命令。|
|[GetDBSession](#getdbsession)|返回到创建该命令的会话的接口指针。|
|[ICommandImpl](#icommandimpl)|构造函数。|

### <a name="data-members"></a>数据成员

|||
|-|-|
|[m_bCancel](#bcancel)|指示是否要取消该命令。|
|[m_bCancelWhenExecuting](#bcancelwhenexecuting)|指示是否要取消时执行该命令。|
|[m_bIsExecuting](#bisexecuting)|指示是否当前正在执行该命令。|

## <a name="remarks"></a>备注

命令对象上的必需接口。

## <a name="cancel"></a> Icommandimpl:: Cancel

取消当前命令执行。

### <a name="syntax"></a>语法

```cpp
STDMETHOD(Cancel)();
```

### <a name="remarks"></a>备注

请参阅[ICommand::Cancel](https://docs.microsoft.com/previous-versions/windows/desktop/ms714402(v=vs.85))中*OLE DB 程序员参考*。

## <a name="cancelexecution"></a> Icommandimpl:: Cancelexecution

取消当前命令执行。

### <a name="syntax"></a>语法

```cpp
HRESULT CancelExecution();
```

## <a name="createrowset"></a> Icommandimpl:: Createrowset

调用[Execute](../../data/oledb/icommandimpl-execute.md)创建单个行集。

### <a name="syntax"></a>语法

```cpp
template template <class RowsetClass>
HRESULT CreateRowset(IUnknown* pUnkOuter,
   REFIID riid,
   DBPARAMS* pParams,
   DBROWCOUNT* pcRowsAffected,
   IUnknown** ppRowset,
   RowsetClass*& pRowsetObj);
```

#### <a name="parameters"></a>参数

*RowsetClass*<br/>
模板类成员表示用户的行集类。 通常由向导生成。

*pUnkOuter*<br/>
[in]一个指向控制`IUnknown`接口如果行集创建聚合的一部分; 否则为 null。

*riid*<br/>
[in]对应于*riid*中`ICommand::Execute`。

*pParams*<br/>
[输入/输出]对应于*pParams*中`ICommand::Execute`。

*pcRowsAffected*<br/>
对应于*pcRowsAffected*中`ICommand::Execute`。

*ppRowset*<br/>
[输入/输出]对应于*ppRowset*中`ICommand::Execute`。

*pRowsetObj*<br/>
[out]指向行集对象的指针。 通常不使用此参数，但如果必须传递给 COM 对象之前在行集上执行更多的工作，可以使用它。 生存期*pRowsetObj*受*ppRowset*。

### <a name="return-value"></a>返回值

标准的 HRESULT 值。 请参阅`ICommand::Execute`有关的典型值列表。

### <a name="remarks"></a>备注

若要创建多个行集，或提供你自己创建不同的行集的条件，将放到不同的调用`CreateRowset`从`Execute`。

请参阅[icommand:: Execute](https://docs.microsoft.com/previous-versions/windows/desktop/ms718095(v=vs.85))中*OLE DB 程序员参考。*

## <a name="execute"></a> Icommandimpl:: Execute

执行的命令。

### <a name="syntax"></a>语法

```cpp
HRESULT Execute(IUnknown* pUnkOuter,
   REFIID riid,
   DBPARAMS* pParams,
   DBROWCOUNT* pcRowsAffected,
   IUnknown** ppRowset);
```

#### <a name="parameters"></a>参数

请参阅[icommand:: Execute](https://docs.microsoft.com/previous-versions/windows/desktop/ms718095(v=vs.85))中*OLE DB 程序员参考*。

### <a name="remarks"></a>备注

所请求的传出接口将从该函数创建的行集对象中获取的接口。

`Execute` 调用[CreateRowset](../../data/oledb/icommandimpl-createrowset.md)。 重写以创建多个行集或提供你自己的条件创建不同的行集的默认实现。

## <a name="getdbsession"></a> Icommandimpl:: Getdbsession

返回到创建该命令的会话的接口指针。

### <a name="syntax"></a>语法

```cpp
STDMETHOD (GetDBSession) (REFIID riid,
   IUnknown** ppSession);
```

#### <a name="parameters"></a>参数

请参阅[ICommand::GetDBSession](https://docs.microsoft.com/previous-versions/windows/desktop/ms719622(v=vs.85))中*OLE DB 程序员参考*。

### <a name="remarks"></a>备注

对于从会话中检索属性很有用。

## <a name="icommandimpl"></a> Icommandimpl:: Icommandimpl

构造函数。

### <a name="syntax"></a>语法

```cpp
ICommandImpl();
```

## <a name="bcancel"></a> Icommandimpl:: M_bcancel

指示是否取消该命令。

### <a name="syntax"></a>语法

```cpp
unsigned m_bCancel:1;
```

### <a name="remarks"></a>备注

您可以检索在此变量`Execute`命令类和根据需要取消的方法。

## <a name="bcancelwhenexecuting"></a> Icommandimpl:: M_bcancelwhenexecuting

指示执行时是否可以取消该命令。

### <a name="syntax"></a>语法

```cpp
unsigned m_bCancelWhenExecuting:1;
```

### <a name="remarks"></a>备注

默认情况下 **，则返回 true** （可以取消）。

## <a name="bisexecuting"></a> Icommandimpl:: M_bisexecuting

指示是否当前正在执行该命令。

### <a name="syntax"></a>语法

```cpp
unsigned m_bIsExecuting:1;
```

### <a name="remarks"></a>备注

`Execute`命令类的方法可以将此变量设置为**true**。

## <a name="see-also"></a>请参阅

[OLE DB 提供程序模板](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[OLE DB 提供程序模板体系结构](../../data/oledb/ole-db-provider-template-architecture.md)