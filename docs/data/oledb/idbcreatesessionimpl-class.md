---
title: IDBCreateSessionImpl 类
ms.date: 11/04/2016
f1_keywords:
- IDBCreateSessionImpl
- ATL.IDBCreateSessionImpl
- ATL::IDBCreateSessionImpl
- IDBCreateSessionImpl::CreateSession
- IDBCreateSessionImpl.CreateSession
- CreateSession
helpviewer_keywords:
- IDBCreateSessionImpl class
- CreateSession method
ms.assetid: 48c02c5c-8362-45ac-af8e-bb119cf8c5c7
ms.openlocfilehash: ae59abc542a4599d289c099801fc34d56b2b13d4
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62409156"
---
# <a name="idbcreatesessionimpl-class"></a>IDBCreateSessionImpl 类

提供一个实现[IDBCreateSession](/previous-versions/windows/desktop/ms724076(v=vs.85))接口。

## <a name="syntax"></a>语法

```cpp
template <class T, class SessionClass>
class ATL_NO_VTABLE IDBCreateSessionImpl
   : public IDBCreateSession
```

### <a name="parameters"></a>参数

*T*<br/>
您的类，派生自

*SessionClass*<br/>
会话对象中。

## <a name="requirements"></a>要求

**标头：** atldb.h

## <a name="members"></a>成员

### <a name="interface-methods"></a>接口方法

|||
|-|-|
|[CreateSession](#createsession)|从数据源对象创建一个新的会话并返回所请求的接口上新创建的会话。|

## <a name="remarks"></a>备注

数据源对象上的必需接口。

## <a name="createsession"></a> IDBCreateSessionImpl::CreateSession

从数据源对象创建一个新的会话并返回所请求的接口上新创建的会话。

### <a name="syntax"></a>语法

```cpp
STDMETHOD(CreateSession)(IUnknown * pUnkOuter,
   REFIID riid,
   IUnknown ** ppDBSession);
```

#### <a name="parameters"></a>参数

请参阅[idbcreatesession:: Createsession](/previous-versions/windows/desktop/ms714942(v=vs.85))中*OLE DB 程序员参考*。

## <a name="see-also"></a>请参阅

[OLE DB 提供程序模板](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[OLE DB 提供程序模板体系结构](../../data/oledb/ole-db-provider-template-architecture.md)