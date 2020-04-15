---
title: IPersistPropertyBagImpl 类
ms.date: 11/04/2016
f1_keywords:
- IPersistPropertyBagImpl
- ATLCOM/ATL::IPersistPropertyBagImpl
- ATLCOM/ATL::IPersistPropertyBagImpl::GetClassID
- ATLCOM/ATL::IPersistPropertyBagImpl::InitNew
- ATLCOM/ATL::IPersistPropertyBagImpl::Load
- ATLCOM/ATL::IPersistPropertyBagImpl::Save
helpviewer_keywords:
- IPersistPropertyBagImpl class
ms.assetid: 712af24d-99f8-40f2-9811-53b3ff6e5b19
ms.openlocfilehash: f656ecc76b175eae523059c60bb8a3efc6f0b312
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81326485"
---
# <a name="ipersistpropertybagimpl-class"></a>IPersistPropertyBagImpl 类

此类实现`IUnknown`并允许对象将其属性保存到客户端提供的属性包。

> [!IMPORTANT]
> 此类及其成员不能在 Windows 运行时中执行的应用程序中使用。

## <a name="syntax"></a>语法

```
template <class T>
class ATL_NO_VTABLE IPersistPropertyBagImpl : public IPersistPropertyBag
```

#### <a name="parameters"></a>参数

*T*<br/>
您的类，派生自`IPersistPropertyBagImpl`。

## <a name="members"></a>成员

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[I 坚持属性巴格：：获取类 ID](#getclassid)|检索对象的 CLSID。|
|[我坚持财产巴格普：：INIT新](#initnew)|初始化新创建的对象。 ATL 实现返回S_OK。|
|[IPersist 属性袋：：加载](#load)|从客户端提供的属性包加载对象的属性。|
|[IPersist属性袋：：保存](#save)|将对象的属性保存到客户端提供的属性包中。|

## <a name="remarks"></a>备注

[IPersistPropertyBag](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa768205\(v=vs.85\))接口允许对象将其属性保存到客户端提供的属性包。 类`IPersistPropertyBagImpl`通过在调试生成中向转储设备发送`IUnknown`信息来提供此接口的默认实现和实现。

`IPersistPropertyBag`与[IPropertyBag](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa768196\(v=vs.85\))和[IErrorLog](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa768231\(v=vs.85\))一起使用。 后两个接口必须由客户端实现。 通过`IPropertyBag`，客户端保存并加载对象的单个属性。 通过`IErrorLog`，对象和客户端都可以报告遇到的任何错误。

**相关文章** [ATL 教程](../../atl/active-template-library-atl-tutorial.md)， 创建[ATL 项目](../../atl/reference/creating-an-atl-project.md)

## <a name="inheritance-hierarchy"></a>继承层次结构

`IPersistPropertyBag`

`IPersistPropertyBagImpl`

## <a name="requirements"></a>要求

**标题：** atlcom.h

## <a name="ipersistpropertybagimplgetclassid"></a><a name="getclassid"></a>I 坚持属性巴格：：获取类 ID

检索对象的 CLSID。

```
STDMETHOD(GetClassID)(CLSID* pClassID);
```

### <a name="remarks"></a>备注

请参阅[IPersist：在](/windows/win32/api/objidl/nf-objidl-ipersist-getclassid)Windows SDK 中获取 ClassID。

## <a name="ipersistpropertybagimplinitnew"></a><a name="initnew"></a>我坚持财产巴格普：：INIT新

初始化新创建的对象。

```
STDMETHOD(InitNew)();
```

### <a name="return-value"></a>返回值

返回S_OK。

### <a name="remarks"></a>备注

请参阅[IPersist 属性袋：：Windows](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa768204\(v=vs.85\)) SDK 中的"新"。

## <a name="ipersistpropertybagimplload"></a><a name="load"></a>IPersist 属性袋：：加载

从客户端提供的属性包加载对象的属性。

```
STDMETHOD(Load)(LPPROPERTYBAG pPropBag, LPERRORLOG pErrorLog);
```

### <a name="remarks"></a>备注

ATL 使用对象的属性映射来检索此信息。

请参阅[IPersist 属性袋：：](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa768206\(v=vs.85\))在 Windows SDK 中加载。

## <a name="ipersistpropertybagimplsave"></a><a name="save"></a>IPersist属性袋：：保存

将对象的属性保存到客户端提供的属性包中。

```
STDMETHOD(Save)(
    LPPROPERTYBAG pPropBag,
    BOOL fClearDirty,
    BOOL fSaveAllProperties);
```

### <a name="remarks"></a>备注

ATL 使用对象的属性映射来存储此信息。 默认情况下，此方法保存所有属性，而不考虑*fSaveAllProperties*的值。

请参阅[IPersist 属性袋：：保存在](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa768207\(v=vs.85\))Windows SDK 中。

## <a name="see-also"></a>另请参阅

[BEGIN_PROP_MAP](property-map-macros.md#begin_prop_map)<br/>
[类概述](../../atl/atl-class-overview.md)
