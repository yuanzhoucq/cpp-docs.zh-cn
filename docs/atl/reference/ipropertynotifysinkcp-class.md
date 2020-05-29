---
title: IPropertyNotifySinkCP 类
ms.date: 11/04/2016
f1_keywords:
- IPropertyNotifySinkCP
- atlctl/ATL::IPropertyNotifySinkCP
helpviewer_keywords:
- connection points [C++], managing
- sinks, notifying of changes
- IPropertyNotifySinkCP class
ms.assetid: 1b41445e-bc88-4fa6-bb62-d68aacec2bd5
ms.openlocfilehash: c6d98bf5a6dfe5566839eb22bcd2bab2a9c28e4d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81329600"
---
# <a name="ipropertynotifysinkcp-class"></a>IPropertyNotifySinkCP 类

此类将[IPropertyNotifySink](/windows/win32/api/ocidl/nn-ocidl-ipropertynotifysink)接口公开为可连接对象上的传出接口。

> [!IMPORTANT]
> 此类及其成员不能在 Windows 运行时中执行的应用程序中使用。

## <a name="syntax"></a>语法

```
template<class T, class CDV = CComDynamicUnkArray>
class IPropertyNotifySinkCP
   : public IConnectionPointImpl<T, &IID_IPropertyNotifySink, CDV>
```

#### <a name="parameters"></a>参数

*T*<br/>
您的类，派生自`IPropertyNotifySinkCP`。

*CDV*<br/>
管理连接点与其接收器之间的连接的类。 默认值为[CComDynamicUnkarray，](../../atl/reference/ccomdynamicunkarray-class.md)它允许无限制的连接。 您还可以使用[CComUnkArray](../../atl/reference/ccomunkarray-class.md)，它指定固定数量的连接。

## <a name="remarks"></a>备注

`IPropertyNotifySinkCP`通过其基类[IConnectionPointImpl 继承](../../atl/reference/iconnectionpointimpl-class.md)所有方法。

[IPropertyNotifySink](/windows/win32/api/ocidl/nn-ocidl-ipropertynotifysink)接口允许接收器对象接收有关属性更改的通知。 类`IPropertyNotifySinkCP`公开此接口作为可连接对象上的传出接口。 客户端必须在接收器上实现`IPropertyNotifySink`方法。

从`IPropertyNotifySinkCP`要创建表示`IPropertyNotifySink`接口的连接点时派生类。

有关在 ATL 中使用连接点的详细信息，请参阅文章[连接点](../../atl/atl-connection-points.md)。

## <a name="requirements"></a>要求

**标题：** atlctl.h

## <a name="see-also"></a>另请参阅

[IConnectionPointImpl 类](../../atl/reference/iconnectionpointimpl-class.md)<br/>
[IConnectionPointContainerImpl 类](../../atl/reference/iconnectionpointcontainerimpl-class.md)<br/>
[类概述](../../atl/atl-class-overview.md)
