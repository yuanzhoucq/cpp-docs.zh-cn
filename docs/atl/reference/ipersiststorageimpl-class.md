---
title: IPersistStorageImpl 类
ms.date: 11/04/2016
f1_keywords:
- IPersistStorageImpl
- ATLCOM/ATL::IPersistStorageImpl
- ATLCOM/ATL::IPersistStorageImpl::GetClassID
- ATLCOM/ATL::IPersistStorageImpl::HandsOffStorage
- ATLCOM/ATL::IPersistStorageImpl::InitNew
- ATLCOM/ATL::IPersistStorageImpl::IsDirty
- ATLCOM/ATL::IPersistStorageImpl::Load
- ATLCOM/ATL::IPersistStorageImpl::Save
- ATLCOM/ATL::IPersistStorageImpl::SaveCompleted
helpviewer_keywords:
- storage, ATL
- IPersistStorageImpl class
ms.assetid: d652f02c-239c-47c7-9a50-3e9fc3014fff
ms.openlocfilehash: a5b5dd4e5be43d01f00687ed9b96a3f27abcad0f
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69495693"
---
# <a name="ipersiststorageimpl-class"></a>IPersistStorageImpl 类

此类实现[IPersistStorage](/windows/win32/api/objidl/nn-objidl-ipersiststorage)接口。

> [!IMPORTANT]
>  此类及其成员不能用于在 Windows 运行时中执行的应用程序。

## <a name="syntax"></a>语法

```
template <class T>
class ATL_NO_VTABLE IPersistStorageImpl : public IPersistStorage
```

#### <a name="parameters"></a>参数

*T*<br/>
派生自`IPersistStorageImpl`的类。

## <a name="members"></a>成员

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[IPersistStorageImpl::GetClassID](#getclassid)|检索对象的 CLSID。|
|[IPersistStorageImpl::HandsOffStorage](#handsoffstorage)|指示对象释放所有存储对象并进入 HandsOff 模式。 ATL 实现返回 S_OK。|
|[IPersistStorageImpl::InitNew](#initnew)|初始化新的存储。|
|[IPersistStorageImpl::IsDirty](#isdirty)|检查对象的数据自上次保存后是否已更改。|
|[IPersistStorageImpl::Load](#load)|从指定的存储加载对象的属性。|
|[IPersistStorageImpl::Save](#save)|将对象的属性保存到指定的存储。|
|[IPersistStorageImpl::SaveCompleted](#savecompleted)|通知对象它可以返回到正常模式以写入其存储对象。 ATL 实现返回 S_OK。|

## <a name="remarks"></a>备注

`IPersistStorageImpl`实现[IPersistStorage](/windows/win32/api/objidl/nn-objidl-ipersiststorage)接口, 该接口允许客户端使用存储来请求对象加载和保存其持久性数据。

此类的实现需要类`T` , 以便通过`QueryInterface`实现`IPersistStreamInit`接口的实现。 通常, 这意味着类`T`应从[IPersistStreamInitImpl](../../atl/reference/ipersiststreaminitimpl-class.md)派生, `IPersistStreamInit`在[COM 映射](com-map-macros.md)中提供一个条目, 并使用[属性映射](property-map-macros.md)来描述类的持久性数据。

**相关文章**[Atl 教程](../../atl/active-template-library-atl-tutorial.md),[创建 atl 项目](../../atl/reference/creating-an-atl-project.md)

## <a name="inheritance-hierarchy"></a>继承层次结构

`IPersistStorage`

`IPersistStorageImpl`

## <a name="requirements"></a>要求

**标头:** atlcom。h

##  <a name="getclassid"></a>IPersistStorageImpl:: GetClassID

检索对象的 CLSID。

```
STDMETHOD(GetClassID)(CLSID* pClassID);
```

### <a name="remarks"></a>备注

请参阅 Windows SDK 中的[IPersist:: GetClassID](/windows/win32/api/objidl/nf-objidl-ipersist-getclassid) 。

##  <a name="handsoffstorage"></a>IPersistStorageImpl::HandsOffStorage

指示对象释放所有存储对象并进入 HandsOff 模式。

```
STDMETHOD(HandsOffStorage)(void);
```

### <a name="return-value"></a>返回值

返回 S_OK。

### <a name="remarks"></a>备注

请参阅 Windows SDK 中的[IPersistStorage:: HandsOffStorage](/windows/win32/api/objidl/nf-objidl-ipersiststorage-handsoffstorage) 。

##  <a name="initnew"></a>IPersistStorageImpl:: InitNew

初始化新的存储。

```
STDMETHOD(InitNew)(IStorage*);
```

### <a name="remarks"></a>备注

ATL 实现委托给[IPersistStreamInit](/windows/win32/api/ocidl/nn-ocidl-ipersiststreaminit)接口。

请参阅 Windows SDK 中的[IPersistStorage: InitNew](/windows/win32/api/objidl/nf-objidl-ipersiststorage-initnew) 。

##  <a name="isdirty"></a>IPersistStorageImpl:: IsDirty

检查对象的数据自上次保存后是否已更改。

```
STDMETHOD(IsDirty)(void);
```

### <a name="remarks"></a>备注

ATL 实现委托给[IPersistStreamInit](/windows/win32/api/ocidl/nn-ocidl-ipersiststreaminit)接口。

请参阅 Windows SDK 中的[IPersistStorage: IsDirty](/windows/win32/api/objidl/nf-objidl-ipersiststorage-isdirty) 。

##  <a name="load"></a>IPersistStorageImpl:: Load

从指定的存储加载对象的属性。

```
STDMETHOD(Load)(IStorage* pStorage);
```

### <a name="remarks"></a>备注

ATL 实现委托给[IPersistStreamInit](/windows/win32/api/ocidl/nn-ocidl-ipersiststreaminit)接口。 `Load`使用名为 "内容" 的流检索对象的数据。 [Save](#save)方法最初创建该流。

请参阅 Windows SDK 中的[IPersistStorage: Load](/windows/win32/api/objidl/nf-objidl-ipersiststorage-load) 。

##  <a name="save"></a>IPersistStorageImpl:: Save

将对象的属性保存到指定的存储。

```
STDMETHOD(Save)(IStorage* pStorage, BOOL fSameAsLoad);
```

### <a name="remarks"></a>备注

ATL 实现委托给[IPersistStreamInit](/windows/win32/api/ocidl/nn-ocidl-ipersiststreaminit)接口。 第`Save`一次调用时, 它会在指定的存储上创建一个名为 "内容" 的流。 然后, 在以后对和的调用中`Save`使用此流来进行[加载](#load)。

请参阅[IPersistStorage:](/windows/win32/api/objidl/nf-objidl-ipersiststorage-save)在 Windows SDK 中保存。

##  <a name="savecompleted"></a>IPersistStorageImpl::SaveCompleted

通知对象它可以返回到正常模式以写入其存储对象。

```
STDMETHOD(SaveCompleted)(IStorage*);
```

### <a name="return-value"></a>返回值

返回 S_OK。

### <a name="remarks"></a>备注

请参阅 Windows SDK 中的[IPersistStorage: SaveCompleted](/windows/win32/api/objidl/nf-objidl-ipersiststorage-savecompleted) 。

## <a name="see-also"></a>请参阅

[存储和流](/windows/win32/Stg/storages-and-streams)<br/>
[IPersistStreamInitImpl 类](../../atl/reference/ipersiststreaminitimpl-class.md)<br/>
[IPersistPropertyBagImpl 类](../../atl/reference/ipersistpropertybagimpl-class.md)<br/>
[类概述](../../atl/atl-class-overview.md)
