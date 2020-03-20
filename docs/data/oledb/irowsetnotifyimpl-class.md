---
title: IRowsetNotifyImpl 类
ms.date: 11/04/2016
f1_keywords:
- ATL.IRowsetNotifyImpl
- ATL::IRowsetNotifyImpl
- IRowsetNotifyImpl
- IRowsetNotifyImpl.OnFieldChange
- IRowsetNotifyImpl::OnFieldChange
- OnFieldChange
- IRowsetNotifyImpl::OnRowChange
- IRowsetNotifyImpl.OnRowChange
- OnRowChange
- OnRowsetChange
- IRowsetNotifyImpl::OnRowsetChange
- IRowsetNotifyImpl.OnRowsetChange
helpviewer_keywords:
- IRowsetNotifyImpl class
- OnFieldChange method
- OnRowChange method
- OnRowsetChange method
ms.assetid: fbfd0cb2-38ff-4b42-899a-8de902f834b8
ms.openlocfilehash: 4e6b4c3298c063038e7365496f26f50d3789be86
ms.sourcegitcommit: 0e3da5cea44437c132b5c2ea522bd229ea000a10
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/12/2019
ms.locfileid: "79544440"
---
# <a name="irowsetnotifyimpl-class"></a>IRowsetNotifyImpl 类

实现并注册使用者（也称为 "sink"）上的[IRowsetNotify](/previous-versions/windows/desktop/ms712959(v=vs.85)) ，以便它可以处理通知。

## <a name="syntax"></a>语法

```cpp
class ATL_NO_VTABLE IRowsetNotifyImpl : public IRowsetNotify
```

## <a name="requirements"></a>要求

**标头:** atldbcli.h

## <a name="members"></a>成员

### <a name="methods"></a>方法

|||
|-|-|
|[OnFieldChange](#onfieldchange)|将对列值所做的任何更改通知给使用方。|
|[OnRowChange](#onrowchange)|将对行的第一个更改或影响整个行的任何更改通知给使用方。|
|[OnRowsetChange](#onrowsetchange)|将影响整个行集合的任何更改通知给使用方。|

## <a name="remarks"></a>备注

请参阅接收有关在使用者上实施连接点接口的[通知](../../data/oledb/receiving-notifications.md)。

`IRowsetNotifyImpl` 提供了 `IRowsetNotify`的虚拟实现，并为 `IRowsetNotify` 方法[OnFieldChange](/previous-versions/windows/desktop/ms715961(v=vs.85))、 [OnRowChange](/previous-versions/windows/desktop/ms722694(v=vs.85))和[OnRowsetChange](/previous-versions/windows/desktop/ms722669(v=vs.85))提供空函数。 如果在实现 `IRowsetNotify` 接口时从该类继承，则只能实现所需的方法。 还需要为其他方法自行提供空实现。

## <a name="irowsetnotifyimplonfieldchange"></a><a name="onfieldchange"></a>IRowsetNotifyImpl：： OnFieldChange

将对列值所做的任何更改通知给使用方。

### <a name="syntax"></a>语法

```cpp
STDMETHOD(OnFieldChange)(
/* [in] */ IRowset* /* pRowset */,
/* [in] */ HROW /* hRow */,
/* [in] */ DBORDINAL /* cColumns */,
/* [size_is][in] */ DBORDINAL /* rgColumns */ [] ,
/* [in] */ DBREASON /* eReason */,
/* [in] */ DBEVENTPHASE /* ePhase */,
/* [in] */ BOOL /* fCantDeny */)
```

#### <a name="parameters"></a>parameters

有关参数说明，请参阅[IRowsetNotify：： OnFieldChange](/previous-versions/windows/desktop/ms715961(v=vs.85)) 。

### <a name="return-value"></a>返回值

有关返回值说明，请参阅[IRowsetNotify：： OnFieldChange](/previous-versions/windows/desktop/ms715961(v=vs.85)) 。

### <a name="remarks"></a>备注

此方法对[IRowsetNotify：： OnFieldChange](/previous-versions/windows/desktop/ms715961(v=vs.85))方法进行包装。 有关详细信息，请参阅“OLE DB 程序员参考”中对该方法的描述。

## <a name="irowsetnotifyimplonrowchange"></a><a name="onrowchange"></a>IRowsetNotifyImpl：： OnRowChange

将对行的第一个更改或影响整个行的任何更改通知给使用方。

### <a name="syntax"></a>语法

```cpp
STDMETHOD(OnRowChange)(
/* [in] */ IRowset* /* pRowset */,
/* [in] */ DBCOUNTITEM /* cRows */,
/* [size_is][in] */ const HROW /* rghRows*/ [] ,
/* [in] */ DBREASON /* eReason */,
/* [in] */ DBEVENTPHASE /* ePhase */,
/* [in] */ BOOL /* fCantDeny */)
```

#### <a name="parameters"></a>parameters

有关参数说明，请参阅[IRowsetNotify：： OnRowChange](/previous-versions/windows/desktop/ms722694(v=vs.85)) 。

### <a name="return-value"></a>返回值

有关返回值说明，请参阅[IRowsetNotify：： OnRowChange](/previous-versions/windows/desktop/ms722694(v=vs.85)) 。

### <a name="remarks"></a>备注

此方法对[IRowsetNotify：： OnRowChange](/previous-versions/windows/desktop/ms722694(v=vs.85))方法进行包装。 有关详细信息，请参阅“OLE DB 程序员参考”中对该方法的描述。

## <a name="irowsetnotifyimplonrowsetchange"></a><a name="onrowsetchange"></a>IRowsetNotifyImpl：： OnRowsetChange

将影响整个行集合的任何更改通知给使用方。

### <a name="syntax"></a>语法

```cpp
STDMETHOD(OnRowsetChange)(
/* [in] */ IRowset* /* pRowset */,
/* [in] */ DBREASON /* eReason */,
/* [in] */ DBEVENTPHASE /* ePhase */,
/* [in] */ BOOL /* fCantDeny */)
```

#### <a name="parameters"></a>parameters

有关参数说明，请参阅[IRowsetNotify：： OnRowsetChange](/previous-versions/windows/desktop/ms722669(v=vs.85)) 。

### <a name="return-value"></a>返回值

有关返回值说明，请参阅[IRowsetNotify：： OnRowsetChange](/previous-versions/windows/desktop/ms722669(v=vs.85)) 。

### <a name="remarks"></a>备注

此方法对[IRowsetNotify：： OnRowsetChange](/previous-versions/windows/desktop/ms722669(v=vs.85))方法进行包装。 有关详细信息，请参阅“OLE DB 程序员参考”中对该方法的描述。

## <a name="see-also"></a>另请参阅

[OLE DB 使用者模板](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[IRowsetNotify](/previous-versions/windows/desktop/ms712959(v=vs.85))
[IRowsetNotifyCP 类](../../data/oledb/irowsetnotifycp-class.md)
