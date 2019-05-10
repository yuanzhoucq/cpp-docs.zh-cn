---
title: IRowsetNotifyCP 类
ms.date: 11/04/2016
f1_keywords:
- IRowsetNotifyCP
- Fire_OnFieldChange
- ATL::IRowsetNotifyCP::Fire_OnFieldChange
- ATL.IRowsetNotifyCP.Fire_OnFieldChange
- IRowsetNotifyCP.Fire_OnFieldChange
- IRowsetNotifyCP::Fire_OnFieldChange
- IRowsetNotifyCP.Fire_OnRowChange
- ATL.IRowsetNotifyCP.Fire_OnRowChange
- Fire_OnRowChange
- ATL::IRowsetNotifyCP::Fire_OnRowChange
- IRowsetNotifyCP::Fire_OnRowChange
- Fire_OnRowsetChange
- IRowsetNotifyCP::Fire_OnRowsetChange
- IRowsetNotifyCP.Fire_OnRowsetChange
- ATL::IRowsetNotifyCP::Fire_OnRowsetChange
- ATL.IRowsetNotifyCP.Fire_OnRowsetChange
helpviewer_keywords:
- IRowsetNotifyCP class
- Fire_OnFieldChange method
- Fire_OnRowChange method
- Fire_OnRowsetChange method
ms.assetid: ccef402b-94a0-4c2e-9a13-7e854ef82390
ms.openlocfilehash: a3ab63206ce7ac53ff996ecf1bb64bdaa0b79fcb
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62390732"
---
# <a name="irowsetnotifycp-class"></a>IRowsetNotifyCP 类

实现连接点接口的提供程序站点[IRowsetNotify](/previous-versions/windows/desktop/ms712959(v=vs.85))。

## <a name="syntax"></a>语法

```cpp
template <class T, class ReentrantEventSync = CComSharedMutex>
class IRowsetNotifyCP :
   public IConnectionPointImpl<
      T,
      piid = &__uuidof(IRowsetNotify),
      CComDynamicUnkArray DynamicUnkArray>,
   public ReentrantEventSync
```

### <a name="parameters"></a>参数

*T*<br/>
一个类派生自`IRowsetNotifyCP`。

*ReentrantEventSync*<br/>
支持可重入性 mutex 类 (默认值是`CComSharedMutex`)。 互斥体是一个允许一个线程互斥独占访问资源的同步对象。

*piid*<br/>
接口 ID 指针 (`IID*`) 为`IRowsetNotify`连接点接口。 默认值为 `&__uuidof(IRowsetNotify)`。

*DynamicUnkArray*<br/>
类型的数组[CComDynamicUnkArray](../../atl/reference/ccomdynamicunkarray-class.md)，这是动态分配的数组`IUnknown`指向客户端接收器接口。

## <a name="requirements"></a>要求

**标头：** atldb.h

## <a name="members"></a>成员

### <a name="methods"></a>方法

|||
|-|-|
|[Fire_OnFieldChange](#onfieldchange)|通知对列的值的更改的使用者。|
|[Fire_OnRowChange](#onrowchange)|通知更改影响的行的使用者。|
|[Fire_OnRowsetChange](#onrowsetchange)|通知更改会影响整个行集的使用者。|

## <a name="remarks"></a>备注

`IRowsetNotifyCP` 实现广播函数向侦听器建议的连接点`IID_IRowsetNotify`对行集的内容的更改。

请注意，您还必须实现和注册`IRowsetNotify`上使用使用者 （也称为"接收器"） [IRowsetNotifyImpl](../../data/oledb/irowsetnotifyimpl-class.md) ，以便使用者可以处理通知。 请参阅[接收通知](../../data/oledb/receiving-notifications.md)如何实现上使用者连接点接口。

实现通知的详细信息，请参阅"支持通知"中[创建可更新的提供程序](../../data/oledb/creating-an-updatable-provider.md)。

## <a name="onfieldchange"></a> IRowsetNotifyCP::Fire_OnFieldChange

广播[OnFieldChange](/previous-versions/windows/desktop/ms715961(v=vs.85))事件，以通知使用者对列的值的更改。

### <a name="syntax"></a>语法

```cpp
HRESULT Fire_OnFieldChange(IRowset* pRowset,
   HROW hRow,
   DBORDINAL cColumns,
   DBORDINAL* rgColumns,
   DBREASON eReason,
   DBEVENTPHASE ePhase,
   BOOL fCantDeny);
```

#### <a name="parameters"></a>参数

请参阅[IRowsetNotify::OnFieldChange](/previous-versions/windows/desktop/ms715961(v=vs.85))中*OLE DB 程序员参考*。

## <a name="onrowchange"></a> IRowsetNotifyCP::Fire_OnRowChange

广播[OnRowChange](/previous-versions/windows/desktop/ms722694(v=vs.85))事件与连接点上的所有侦听器`IID_IRowsetNotify`以通知使用者的影响的行的更改。

### <a name="syntax"></a>语法

```cpp
HRESULT Fire_OnRowChange(IRowset* pRowset,
   DBCOUNTITEM cRows,
   const HROW rghRows[],
   DBREASON eReason,
   DBEVENTPHASE ePhase,
   BOOL fCantDeny);
```

#### <a name="parameters"></a>参数

请参阅[irowsetnotify:: Onrowchange](/previous-versions/windows/desktop/ms722694(v=vs.85))中*OLE DB 程序员参考*。

## <a name="onrowsetchange"></a> IRowsetNotifyCP::Fire_OnRowsetChange

广播[OnRowsetChange](/previous-versions/windows/desktop/ms722669(v=vs.85))事件与连接点上的所有侦听器`IID_IRowsetNotify`以通知使用者的更改会影响整个行集。

### <a name="syntax"></a>语法

```cpp
HRESULT Fire_OnRowsetChange(IRowset* pRowset,
   DBREASON eReason,
   DBEVENTPHASE ePhase,
   BOOL fCantDeny);
```

#### <a name="parameters"></a>参数

请参阅[IRowsetNotify::OnRowsetChange](/previous-versions/windows/desktop/ms722669(v=vs.85))中*OLE DB 程序员参考*。

## <a name="see-also"></a>请参阅

[OLE DB 提供程序模板](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[OLE DB 提供程序模板体系结构](../../data/oledb/ole-db-provider-template-architecture.md)<br/>
[通知 (COM)](/windows/desktop/com/notifications)<br/>
[BEGIN_CONNECTION_POINT_MAP](../../atl/reference/connection-point-macros.md#begin_connection_point_map)<br/>
[END_CONNECTION_POINT_MAP](../../atl/reference/connection-point-macros.md#end_connection_point_map)<br/>
[CONNECTION_POINT_ENTRY](../../atl/reference/connection-point-macros.md#connection_point_entry)<br/>
[创建可更新的提供程序](../../data/oledb/creating-an-updatable-provider.md)