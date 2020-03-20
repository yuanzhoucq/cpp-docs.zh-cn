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
ms.openlocfilehash: 481c2c0ec28972e9cef8d1103e49afa2037c2393
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "79544566"
---
# <a name="irowsetnotifycp-class"></a>IRowsetNotifyCP 类

实现连接点接口[IRowsetNotify](/previous-versions/windows/desktop/ms712959(v=vs.85))的提供程序站点。

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

### <a name="parameters"></a>parameters

*T*<br/>
派生自 `IRowsetNotifyCP`的类。

*ReentrantEventSync*<br/>
支持重入的 mutex 类（默认值为 `CComSharedMutex`）。 Mutex 是一个同步对象，允许一个线程互相排斥地访问资源。

*piid*<br/>
`IRowsetNotify` 连接点接口的接口 ID 指针（`IID*`）。 默认值是 `&__uuidof(IRowsetNotify)`。

*DynamicUnkArray*<br/>
[CComDynamicUnkArray](../../atl/reference/ccomdynamicunkarray-class.md)类型的数组，它是一个动态分配的数组，该数组是指向客户端接收器接口的 `IUnknown` 指针。

## <a name="requirements"></a>要求

**标头：** atldb.h

## <a name="members"></a>成员

### <a name="methods"></a>方法

|||
|-|-|
|[Fire_OnFieldChange](#onfieldchange)|通知使用者对列的值进行了更改。|
|[Fire_OnRowChange](#onrowchange)|通知使用者影响行的更改。|
|[Fire_OnRowsetChange](#onrowsetchange)|通知使用者影响整个行集的更改。|

## <a name="remarks"></a>备注

`IRowsetNotifyCP` 实现广播函数，以便在连接点上通知侦听器 `IID_IRowsetNotify` 行集内容的更改。

请注意，还必须使用[IRowsetNotifyImpl](../../data/oledb/irowsetnotifyimpl-class.md)实现使用者（也称为 "接收器"）上的 `IRowsetNotify`，以便使用者可以处理通知。 请参阅接收有关在使用者上实施连接点接口的[通知](../../data/oledb/receiving-notifications.md)。

有关实现通知的详细信息，请参阅[创建可更新的提供程序](../../data/oledb/creating-an-updatable-provider.md)中的 "支持通知"。

## <a name="irowsetnotifycpfire_onfieldchange"></a><a name="onfieldchange"></a>IRowsetNotifyCP：： Fire_OnFieldChange

广播[OnFieldChange](/previous-versions/windows/desktop/ms715961(v=vs.85))事件，通知使用者对列的值进行了更改。

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

#### <a name="parameters"></a>parameters

请参阅*OLE DB 程序员参考*中的[IRowsetNotify：： OnFieldChange](/previous-versions/windows/desktop/ms715961(v=vs.85)) 。

## <a name="irowsetnotifycpfire_onrowchange"></a><a name="onrowchange"></a>IRowsetNotifyCP：： Fire_OnRowChange

将[OnRowChange](/previous-versions/windows/desktop/ms722694(v=vs.85))事件广播到连接点上的所有侦听器 `IID_IRowsetNotify` 以通知使用者影响行的更改。

### <a name="syntax"></a>语法

```cpp
HRESULT Fire_OnRowChange(IRowset* pRowset,
   DBCOUNTITEM cRows,
   const HROW rghRows[],
   DBREASON eReason,
   DBEVENTPHASE ePhase,
   BOOL fCantDeny);
```

#### <a name="parameters"></a>parameters

请参阅*OLE DB 程序员参考*中的[IRowsetNotify：： OnRowChange](/previous-versions/windows/desktop/ms722694(v=vs.85)) 。

## <a name="irowsetnotifycpfire_onrowsetchange"></a><a name="onrowsetchange"></a>IRowsetNotifyCP：： Fire_OnRowsetChange

将[OnRowsetChange](/previous-versions/windows/desktop/ms722669(v=vs.85))事件广播到连接点上的所有侦听器 `IID_IRowsetNotify` 以通知使用者影响整个行集的更改。

### <a name="syntax"></a>语法

```cpp
HRESULT Fire_OnRowsetChange(IRowset* pRowset,
   DBREASON eReason,
   DBEVENTPHASE ePhase,
   BOOL fCantDeny);
```

#### <a name="parameters"></a>parameters

请参阅*OLE DB 程序员参考*中的[IRowsetNotify：： OnRowsetChange](/previous-versions/windows/desktop/ms722669(v=vs.85)) 。

## <a name="see-also"></a>另请参阅

[OLE DB 提供程序模板](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[OLE DB 提供程序模板体系结构](../../data/oledb/ole-db-provider-template-architecture.md)<br/>
[通知（COM）](/windows/win32/com/notifications)<br/>
[BEGIN_CONNECTION_POINT_MAP](../../atl/reference/connection-point-macros.md#begin_connection_point_map)<br/>
[END_CONNECTION_POINT_MAP](../../atl/reference/connection-point-macros.md#end_connection_point_map)<br/>
[CONNECTION_POINT_ENTRY](../../atl/reference/connection-point-macros.md#connection_point_entry)<br/>
[创建可更新的提供程序](../../data/oledb/creating-an-updatable-provider.md)