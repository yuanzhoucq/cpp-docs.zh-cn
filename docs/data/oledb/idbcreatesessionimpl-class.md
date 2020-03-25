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
ms.openlocfilehash: cff1ca374c9489cb9c5df0dad153c4bf7a4cbc9e
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80210777"
---
# <a name="idbcreatesessionimpl-class"></a>IDBCreateSessionImpl 类

提供[IDBCreateSession](/previous-versions/windows/desktop/ms724076(v=vs.85))接口的实现。

## <a name="syntax"></a>语法

```cpp
template <class T, class SessionClass>
class ATL_NO_VTABLE IDBCreateSessionImpl
   : public IDBCreateSession
```

### <a name="parameters"></a>parameters

*T*<br/>
你的类，派生自

*SessionClass*<br/>
Session 对象。

## <a name="requirements"></a>要求

**标头：** atldb.h

## <a name="members"></a>成员

### <a name="interface-methods"></a>接口方法

|||
|-|-|
|[CreateSession](#createsession)|从数据源对象创建新的会话，并返回新创建的会话上所请求的接口。|

## <a name="remarks"></a>备注

数据源对象上的必需接口。

## <a name="idbcreatesessionimplcreatesession"></a><a name="createsession"></a>IDBCreateSessionImpl：： CreateSession

从数据源对象创建新的会话，并返回新创建的会话上所请求的接口。

### <a name="syntax"></a>语法

```cpp
STDMETHOD(CreateSession)(IUnknown * pUnkOuter,
   REFIID riid,
   IUnknown ** ppDBSession);
```

#### <a name="parameters"></a>parameters

请参阅*OLE DB 程序员参考*中的[IDBCreateSession：： CreateSession](/previous-versions/windows/desktop/ms714942(v=vs.85)) 。

## <a name="see-also"></a>另请参阅

[OLE DB 提供程序模板](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[OLE DB 提供程序模板体系结构](../../data/oledb/ole-db-provider-template-architecture.md)
