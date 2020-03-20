---
title: IRowsetCreatorImpl 类
ms.date: 11/04/2016
f1_keywords:
- ATL::IRowsetCreatorImpl
- ATL.IRowsetCreatorImpl
- ATL::IRowsetCreatorImpl<T>
- ATL.IRowsetCreatorImpl<T>
- IRowsetCreatorImpl
- IRowsetCreatorImpl.SetSite
- IRowsetCreatorImpl<T>::SetSite
- IRowsetCreatorImpl::SetSite
- SetSite
- ATL.IRowsetCreatorImpl.SetSite
- ATL::IRowsetCreatorImpl<T>::SetSite
- ATL::IRowsetCreatorImpl::SetSite
- ATL.IRowsetCreatorImpl<T>.SetSite
helpviewer_keywords:
- IRowsetCreatorImpl class
- SetSite method
ms.assetid: 92cc950f-7978-4754-8d9a-defa63867d82
ms.openlocfilehash: 8c4253d469c510f5e6eb996ed510ef836844899d
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "79544578"
---
# <a name="irowsetcreatorimpl-class"></a>IRowsetCreatorImpl 类

执行与 `IObjectWithSite` 相同的功能，同时还启用 OLE DB 属性 `DBPROPCANSCROLLBACKWARDS DBPROPCANFETCHBACKWARDS`。

## <a name="syntax"></a>语法

```cpp
template < class T >
class ATL_NO_VTABLE IRowsetCreatorImpl
   : public IObjectWithSiteImpl< T >
```

### <a name="parameters"></a>parameters

*T*<br/>
派生自 `IRowsetCreator`的类。

## <a name="requirements"></a>要求

**标头：** atldb.h

## <a name="members"></a>成员

### <a name="methods"></a>方法

|||
|-|-|
|[SetSite](#setsite)|设置包含行集对象的站点。|

## <a name="remarks"></a>备注

此类继承自[IObjectWithSite](/windows/win32/api/ocidl/nn-ocidl-iobjectwithsite) ，并重写[IObjectWithSite：： SetSite](/windows/win32/api/ocidl/nf-ocidl-iobjectwithsite-setsite)。 当提供程序命令或会话对象创建行集时，它会对查找 `IObjectWithSite` 并调用的行集对象调用 `QueryInterface` `SetSite` 将行集对象的 `IUnkown` 接口作为站点接口传递。

## <a name="irowsetcreatorimplsetsite"></a><a name="setsite"></a>IRowsetCreatorImpl：： SetSite

设置包含行集对象的站点。 有关详细信息，请参阅[IObjectWithSite：： SetSite](/windows/win32/api/ocidl/nf-ocidl-iobjectwithsite-setsite)。

### <a name="syntax"></a>语法

```cpp
STDMETHOD(SetSite )(IUnknown* pCreator);
```

#### <a name="parameters"></a>parameters

*pCreator*<br/>
中指向管理行集对象的站点的 `IUnknown` 接口指针的指针。

### <a name="return-value"></a>返回值

标准的 HRESULT。

### <a name="remarks"></a>备注

此外，`IRowsetCreatorImpl::SetSite` 启用 OLE DB `DBPROPCANSCROLLBACKWARDS DBPROPCANFETCHBACKWARDS` 属性。

## <a name="see-also"></a>另请参阅

[OLE DB 提供程序模板](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[OLE DB 提供程序模板体系结构](../../data/oledb/ole-db-provider-template-architecture.md)