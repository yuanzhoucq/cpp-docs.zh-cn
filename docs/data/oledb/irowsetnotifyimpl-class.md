---
title: IRowsetNotifyImpl 类 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- IRowsetNotifyImpl class
- OnFieldChange method
- OnRowChange method
- OnRowsetChange method
ms.assetid: fbfd0cb2-38ff-4b42-899a-8de902f834b8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 8659897e411f703882f398fd7e96c8838b5ddafb
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/25/2018
ms.locfileid: "50056161"
---
# <a name="irowsetnotifyimpl-class"></a>IRowsetNotifyImpl 类

实现和注册[IRowsetNotify](/previous-versions/windows/desktop/ms712959)上使用者 （也称为"接收器"），以便它可以处理通知。

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
|[OnFieldChange](#onfieldchange)|通知对列的值的任何更改的使用者。|
|[OnRowChange](#onrowchange)|通知使用者对行的第一个更改或影响整个行的任何更改。|
|[OnRowsetChange](#onrowsetchange)|通知使用者的任何更改会影响整个行集。|

## <a name="remarks"></a>备注

请参阅[接收通知](../../data/oledb/receiving-notifications.md)如何实现上使用者连接点接口。

`IRowsetNotifyImpl` 提供有关虚拟实现`IRowsetNotify`，具有可实现空功能`IRowsetNotify`方法[OnFieldChange](/previous-versions/windows/desktop/ms715961)， [OnRowChange](/previous-versions/windows/desktop/ms722694)，和[OnRowsetChange](/previous-versions/windows/desktop/ms722669). 如果在实现时，在从此类继承`IRowsetNotify`接口，可以实现仅需要的方法。 此外需要自行提供的其他方法的空实现。

## <a name="onfieldchange"></a> Irowsetnotifyimpl:: Onfieldchange

通知对列的值的任何更改的使用者。

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

#### <a name="parameters"></a>参数

请参阅[IRowsetNotify::OnFieldChange](/previous-versions/windows/desktop/ms715961)有关参数说明。

### <a name="return-value"></a>返回值

请参阅[IRowsetNotify::OnFieldChange](/previous-versions/windows/desktop/ms715961)有关返回值说明。

### <a name="remarks"></a>备注

此方法包装[IRowsetNotify::OnFieldChange](/previous-versions/windows/desktop/ms715961)方法。 有关详细信息，请参阅“OLE DB 程序员参考”中对该方法的描述。

## <a name="onrowchange"></a> Irowsetnotifyimpl:: Onrowchange

通知使用者对行的第一个更改或影响整个行的任何更改。

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

#### <a name="parameters"></a>参数

请参阅[irowsetnotify:: Onrowchange](/previous-versions/windows/desktop/ms722694)有关参数说明。

### <a name="return-value"></a>返回值

请参阅[irowsetnotify:: Onrowchange](/previous-versions/windows/desktop/ms722694)有关返回值说明。

### <a name="remarks"></a>备注

此方法包装[irowsetnotify:: Onrowchange](/previous-versions/windows/desktop/ms722694)方法。 有关详细信息，请参阅“OLE DB 程序员参考”中对该方法的描述。

## <a name="onrowsetchange"></a> Irowsetnotifyimpl:: Onrowsetchange

通知使用者的任何更改会影响整个行集。

### <a name="syntax"></a>语法

```cpp
STDMETHOD(OnRowsetChange)( 
/* [in] */ IRowset* /* pRowset */,
/* [in] */ DBREASON /* eReason */,
/* [in] */ DBEVENTPHASE /* ePhase */,
/* [in] */ BOOL /* fCantDeny */)
```

#### <a name="parameters"></a>参数

请参阅[IRowsetNotify::OnRowsetChange](/previous-versions/windows/desktop/ms722669)有关参数说明。

### <a name="return-value"></a>返回值

请参阅[IRowsetNotify::OnRowsetChange](/previous-versions/windows/desktop/ms722669)有关返回值说明。

### <a name="remarks"></a>备注

此方法包装[IRowsetNotify::OnRowsetChange](/previous-versions/windows/desktop/ms722669)方法。 有关详细信息，请参阅“OLE DB 程序员参考”中对该方法的描述。

## <a name="see-also"></a>请参阅

[OLE DB 使用者模板](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[OLE DB 使用者模板](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[IRowsetNotify](/previous-versions/windows/desktop/ms712959)
[IRowsetNotifyCP 类](../../data/oledb/irowsetnotifycp-class.md)