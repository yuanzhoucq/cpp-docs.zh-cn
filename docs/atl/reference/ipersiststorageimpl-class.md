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
ms.openlocfilehash: b235b190f237293932705e4d290ac963088722f3
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81326473"
---
# <a name="ipersiststorageimpl-class"></a>IPersistStorageImpl 类

此类实现[IPersist 存储](/windows/win32/api/objidl/nn-objidl-ipersiststorage)接口。

> [!IMPORTANT]
> 此类及其成员不能在 Windows 运行时中执行的应用程序中使用。

## <a name="syntax"></a>语法

```
template <class T>
class ATL_NO_VTABLE IPersistStorageImpl : public IPersistStorage
```

#### <a name="parameters"></a>参数

*T*<br/>
您的类，派生自`IPersistStorageImpl`。

## <a name="members"></a>成员

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[I 持久存储 impl：获取类 ID](#getclassid)|检索对象的 CLSID。|
|[I 持久存储 Impl：：手关闭存储](#handsoffstorage)|指示对象释放所有存储对象并进入"手关闭"模式。 ATL 实现返回S_OK。|
|[I 持久存储 impl：：ININnew](#initnew)|初始化新存储。|
|[I 持久存储 impl：：是脏的](#isdirty)|检查对象的数据自上次保存以来是否已更改。|
|[I 持久存储 Impl：：加载](#load)|从指定的存储加载对象的属性。|
|[IPersist 存储impl：：保存](#save)|将对象的属性保存到指定的存储。|
|[IPersist 存储impl：：保存完成](#savecompleted)|通知对象它可以返回到"正常"模式以写入其存储对象。 ATL 实现返回S_OK。|

## <a name="remarks"></a>备注

`IPersistStorageImpl`实现[IPersistStorage 接口](/windows/win32/api/objidl/nn-objidl-ipersiststorage)，它允许客户端请求对象加载并使用存储保存其持久数据。

此类的实现要求类`T`通过 使`IPersistStreamInit`接口的实现可用。 `QueryInterface` 通常，`T`这意味着类应派生自[IPersistStreamInitImpl，](../../atl/reference/ipersiststreaminitimpl-class.md)在 COM`IPersistStreamInit`[映射](com-map-macros.md)中提供条目，并使用[属性映射](property-map-macros.md)来描述类的持久数据。

**相关文章** [ATL 教程](../../atl/active-template-library-atl-tutorial.md)， 创建[ATL 项目](../../atl/reference/creating-an-atl-project.md)

## <a name="inheritance-hierarchy"></a>继承层次结构

`IPersistStorage`

`IPersistStorageImpl`

## <a name="requirements"></a>要求

**标题：** atlcom.h

## <a name="ipersiststorageimplgetclassid"></a><a name="getclassid"></a>I 持久存储 impl：获取类 ID

检索对象的 CLSID。

```
STDMETHOD(GetClassID)(CLSID* pClassID);
```

### <a name="remarks"></a>备注

请参阅[IPersist：在](/windows/win32/api/objidl/nf-objidl-ipersist-getclassid)Windows SDK 中获取 ClassID。

## <a name="ipersiststorageimplhandsoffstorage"></a><a name="handsoffstorage"></a>I 持久存储 Impl：：手关闭存储

指示对象释放所有存储对象并进入"手关闭"模式。

```
STDMETHOD(HandsOffStorage)(void);
```

### <a name="return-value"></a>返回值

返回S_OK。

### <a name="remarks"></a>备注

请参阅[IPersist 存储：：Windows SDK 中的"手关闭存储](/windows/win32/api/objidl/nf-objidl-ipersiststorage-handsoffstorage)"。

## <a name="ipersiststorageimplinitnew"></a><a name="initnew"></a>I 持久存储 impl：：ININnew

初始化新存储。

```
STDMETHOD(InitNew)(IStorage*);
```

### <a name="remarks"></a>备注

ATL 实现委托给[IPersistStreamInit](/windows/win32/api/ocidl/nn-ocidl-ipersiststreaminit)接口。

请参阅[IPersist 存储：Windows](/windows/win32/api/objidl/nf-objidl-ipersiststorage-initnew) SDK 中的 Init New。

## <a name="ipersiststorageimplisdirty"></a><a name="isdirty"></a>I 持久存储 impl：：是脏的

检查对象的数据自上次保存以来是否已更改。

```
STDMETHOD(IsDirty)(void);
```

### <a name="remarks"></a>备注

ATL 实现委托给[IPersistStreamInit](/windows/win32/api/ocidl/nn-ocidl-ipersiststreaminit)接口。

请参阅[IPersist 存储：Windows](/windows/win32/api/objidl/nf-objidl-ipersiststorage-isdirty) SDK 中脏污。

## <a name="ipersiststorageimplload"></a><a name="load"></a>I 持久存储 Impl：：加载

从指定的存储加载对象的属性。

```
STDMETHOD(Load)(IStorage* pStorage);
```

### <a name="remarks"></a>备注

ATL 实现委托给[IPersistStreamInit](/windows/win32/api/ocidl/nn-ocidl-ipersiststreaminit)接口。 `Load`使用名为"内容"的流检索对象的数据。 [Save](#save)方法最初创建此流。

请参阅[IPersist 存储：在](/windows/win32/api/objidl/nf-objidl-ipersiststorage-load)Windows SDK 中加载。

## <a name="ipersiststorageimplsave"></a><a name="save"></a>IPersist 存储impl：：保存

将对象的属性保存到指定的存储。

```
STDMETHOD(Save)(IStorage* pStorage, BOOL fSameAsLoad);
```

### <a name="remarks"></a>备注

ATL 实现委托给[IPersistStreamInit](/windows/win32/api/ocidl/nn-ocidl-ipersiststreaminit)接口。 首次`Save`调用时，它会在指定的存储上创建名为"内容"的流。 然后，此流用于以后对`Save` [Load](#load)的调用和调用 。

请参阅[IPersist 存储：保存在](/windows/win32/api/objidl/nf-objidl-ipersiststorage-save)Windows SDK 中。

## <a name="ipersiststorageimplsavecompleted"></a><a name="savecompleted"></a>IPersist 存储impl：：保存完成

通知对象它可以返回到"正常"模式以写入其存储对象。

```
STDMETHOD(SaveCompleted)(IStorage*);
```

### <a name="return-value"></a>返回值

返回S_OK。

### <a name="remarks"></a>备注

请参阅[IPersist 存储：在](/windows/win32/api/objidl/nf-objidl-ipersiststorage-savecompleted)Windows SDK 中保存已完成。

## <a name="see-also"></a>另请参阅

[存储和流](/windows/win32/Stg/storages-and-streams)<br/>
[IPersistStreamInitImpl 类](../../atl/reference/ipersiststreaminitimpl-class.md)<br/>
[IPersistPropertyBagImpl 类](../../atl/reference/ipersistpropertybagimpl-class.md)<br/>
[类概述](../../atl/atl-class-overview.md)
