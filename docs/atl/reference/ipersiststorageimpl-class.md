---
title: IPersistStorageImpl 类 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- storage, ATL
- IPersistStorageImpl class
ms.assetid: d652f02c-239c-47c7-9a50-3e9fc3014fff
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 93a1c08e8e50e8ef1236b253d471c2332c4e6e03
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/05/2018
ms.locfileid: "43763765"
---
# <a name="ipersiststorageimpl-class"></a>IPersistStorageImpl 类

此类实现[IPersistStorage](/windows/desktop/api/objidl/nn-objidl-ipersiststorage)接口。

> [!IMPORTANT]
>  不能在 Windows 运行时中执行的应用程序中使用此类和其成员。

## <a name="syntax"></a>语法

```
template <class T>  
class ATL_NO_VTABLE IPersistStorageImpl : public IPersistStorage
```

#### <a name="parameters"></a>参数

*T*  
您的类，派生自`IPersistStorageImpl`。

## <a name="members"></a>成员

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[IPersistStorageImpl::GetClassID](#getclassid)|检索对象的 CLSID。|
|[IPersistStorageImpl::HandsOffStorage](#handsoffstorage)|指示要释放所有存储对象并进入 HandsOff 模式的对象。 ATL 实现返回 S_OK。|
|[IPersistStorageImpl::InitNew](#initnew)|初始化新的存储。|
|[IPersistStorageImpl::IsDirty](#isdirty)|检查对象的数据是否自上次保存以来已更改。|
|[IPersistStorageImpl::Load](#load)|从指定的存储中加载对象的属性。|
|[IPersistStorageImpl::Save](#save)|将对象的属性保存到指定的存储。|
|[IPersistStorageImpl::SaveCompleted](#savecompleted)|通知它可以返回到正常模式下要写入到它的存储对象的对象。 ATL 实现返回 S_OK。|

## <a name="remarks"></a>备注

`IPersistStorageImpl` 实现[IPersistStorage](/windows/desktop/api/objidl/nn-objidl-ipersiststorage)接口，它允许客户端请求的对象加载和保存使用存储其持久性数据。

此类的实现需要类`T`进行的实现`IPersistStreamInit`接口可通过`QueryInterface`。 通常这意味着该类`T`应派生自[IPersistStreamInitImpl](../../atl/reference/ipersiststreaminitimpl-class.md)，提供的条目`IPersistStreamInit`中[COM 映射](com-map-macros.md)，并使用[属性映射](property-map-macros.md)来描述类的持久性数据。

**相关文章** [ATL 教程](../../atl/active-template-library-atl-tutorial.md)，[创建 ATL 项目](../../atl/reference/creating-an-atl-project.md)

## <a name="inheritance-hierarchy"></a>继承层次结构

`IPersistStorage`

`IPersistStorageImpl`

## <a name="requirements"></a>要求

**标头：** atlcom.h

##  <a name="getclassid"></a>  IPersistStorageImpl::GetClassID

检索对象的 CLSID。

```
STDMETHOD(GetClassID)(CLSID* pClassID);
```

### <a name="remarks"></a>备注

请参阅[IPersist::GetClassID](/windows/desktop/api/objidl/nf-objidl-ipersist-getclassid) Windows SDK 中。

##  <a name="handsoffstorage"></a>  IPersistStorageImpl::HandsOffStorage

指示要释放所有存储对象并进入 HandsOff 模式的对象。

```
STDMETHOD(HandsOffStorage)(void);
```

### <a name="return-value"></a>返回值

返回 S_OK。

### <a name="remarks"></a>备注

请参阅[IPersistStorage::HandsOffStorage](/windows/desktop/api/objidl/nf-objidl-ipersiststorage-handsoffstorage) Windows SDK 中。

##  <a name="initnew"></a>  IPersistStorageImpl::InitNew

初始化新的存储。

```
STDMETHOD(InitNew)(IStorage*);
```

### <a name="remarks"></a>备注

ATL 实现委托给[IPersistStreamInit](/windows/desktop/api/ocidl/nn-ocidl-ipersiststreaminit)接口。

请参阅[IPersistStorage:InitNew](/windows/desktop/api/objidl/nf-objidl-ipersiststorage-initnew) Windows SDK 中。

##  <a name="isdirty"></a>  IPersistStorageImpl::IsDirty

检查对象的数据是否自上次保存以来已更改。

```
STDMETHOD(IsDirty)(void);
```

### <a name="remarks"></a>备注

ATL 实现委托给[IPersistStreamInit](/windows/desktop/api/ocidl/nn-ocidl-ipersiststreaminit)接口。

请参阅[IPersistStorage:IsDirty](/windows/desktop/api/objidl/nf-objidl-ipersiststorage-isdirty) Windows SDK 中。

##  <a name="load"></a>  IPersistStorageImpl::Load

从指定的存储中加载对象的属性。

```
STDMETHOD(Load)(IStorage* pStorage);
```

### <a name="remarks"></a>备注

ATL 实现委托给[IPersistStreamInit](/windows/desktop/api/ocidl/nn-ocidl-ipersiststreaminit)接口。 `Load` 使用名为"内容"的流中检索对象的数据。 [保存](#save)方法最初创建此流。

请参阅[IPersistStorage:Load](/windows/desktop/api/objidl/nf-objidl-ipersiststorage-load) Windows SDK 中。

##  <a name="save"></a>  IPersistStorageImpl::Save

将对象的属性保存到指定的存储。

```
STDMETHOD(Save)(IStorage* pStorage, BOOL fSameAsLoad);
```

### <a name="remarks"></a>备注

ATL 实现委托给[IPersistStreamInit](/windows/desktop/api/ocidl/nn-ocidl-ipersiststreaminit)接口。 当`Save`第一次调用，它将创建指定的存储上名为"内容"的流。 在更高版本调用然后使用此流`Save`并在调用[负载](#load)。

请参阅[IPersistStorage:Save](/windows/desktop/api/objidl/nf-objidl-ipersiststorage-save) Windows SDK 中。

##  <a name="savecompleted"></a>  IPersistStorageImpl::SaveCompleted

通知它可以返回到正常模式下要写入到它的存储对象的对象。

```
STDMETHOD(SaveCompleted)(IStorage*);
```

### <a name="return-value"></a>返回值

返回 S_OK。

### <a name="remarks"></a>备注

请参阅[IPersistStorage:SaveCompleted](/windows/desktop/api/objidl/nf-objidl-ipersiststorage-savecompleted) Windows SDK 中。

## <a name="see-also"></a>请参阅

[存储和流](/windows/desktop/Stg/storages-and-streams)   
[IPersistStreamInitImpl 类](../../atl/reference/ipersiststreaminitimpl-class.md)   
[IPersistPropertyBagImpl 类](../../atl/reference/ipersistpropertybagimpl-class.md)   
[类概述](../../atl/atl-class-overview.md)
