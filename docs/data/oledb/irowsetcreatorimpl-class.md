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
ms.openlocfilehash: 3dc5cb06b3eb7f01667e4e1ec09dd60f9befae77
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/18/2019
ms.locfileid: "59026599"
---
# <a name="irowsetcreatorimpl-class"></a>IRowsetCreatorImpl 类

执行相同的功能`IObjectWithSite`但也可以启用 OLE DB 属性`DBPROPCANSCROLLBACKWARDS DBPROPCANFETCHBACKWARDS`。

## <a name="syntax"></a>语法

```cpp
template < class T >
class ATL_NO_VTABLE IRowsetCreatorImpl
   : public IObjectWithSiteImpl< T >
```

### <a name="parameters"></a>参数

*T*<br/>
一个类派生自`IRowsetCreator`。

## <a name="requirements"></a>要求

**标头：** atldb.h

## <a name="members"></a>成员

### <a name="methods"></a>方法

|||
|-|-|
|[SetSite](#setsite)|设置包含行集对象的站点。|

## <a name="remarks"></a>备注

此类继承自[IObjectWithSite](/windows/desktop/api/ocidl/nn-ocidl-iobjectwithsite)并重写[IObjectWithSite::SetSite](/windows/desktop/api/ocidl/nf-ocidl-iobjectwithsite-setsite)。 当提供程序命令或会话对象创建行集时，它将调用`QueryInterface`寻找对行集对象`IObjectWithSite`并调用`SetSite`将行集对象传递`IUnkown`作为站点接口的接口。

## <a name="setsite"></a> IRowsetCreatorImpl::SetSite

设置包含行集对象的站点。 有关详细信息，请参阅[IObjectWithSite::SetSite](/windows/desktop/api/ocidl/nf-ocidl-iobjectwithsite-setsite)。

### <a name="syntax"></a>语法

```cpp
STDMETHOD(SetSite )(IUnknown* pCreator);
```

#### <a name="parameters"></a>参数

*pCreator*<br/>
[in]指向`IUnknown`管理行集对象的站点的接口指针。

### <a name="return-value"></a>返回值

标准的 HRESULT。

### <a name="remarks"></a>备注

此外，`IRowsetCreatorImpl::SetSite`能使 OLE DB`DBPROPCANSCROLLBACKWARDS DBPROPCANFETCHBACKWARDS`属性。

## <a name="see-also"></a>请参阅

[OLE DB 提供程序模板](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[OLE DB 提供程序模板体系结构](../../data/oledb/ole-db-provider-template-architecture.md)