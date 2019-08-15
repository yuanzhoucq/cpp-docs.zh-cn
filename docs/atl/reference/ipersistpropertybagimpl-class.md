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
ms.openlocfilehash: 15b9c9738d921c4c6f7837f9280c6dd6b09392d6
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69495766"
---
# <a name="ipersistpropertybagimpl-class"></a>IPersistPropertyBagImpl 类

此类实现`IUnknown`并允许对象将其属性保存到客户端提供的属性包。

> [!IMPORTANT]
>  此类及其成员不能用于在 Windows 运行时中执行的应用程序。

## <a name="syntax"></a>语法

```
template <class T>
class ATL_NO_VTABLE IPersistPropertyBagImpl : public IPersistPropertyBag
```

#### <a name="parameters"></a>参数

*T*<br/>
派生自`IPersistPropertyBagImpl`的类。

## <a name="members"></a>成员

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[IPersistPropertyBagImpl::GetClassID](#getclassid)|检索对象的 CLSID。|
|[IPersistPropertyBagImpl::InitNew](#initnew)|初始化新创建的对象。 ATL 实现返回 S_OK。|
|[IPersistPropertyBagImpl::Load](#load)|从客户端提供的属性包加载对象的属性。|
|[IPersistPropertyBagImpl::Save](#save)|将对象的属性保存到客户端提供的属性包中。|

## <a name="remarks"></a>备注

[IPersistPropertyBag](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa768205\(v=vs.85\))接口允许对象将其属性保存到客户端提供的属性包。 类`IPersistPropertyBagImpl`提供此接口的默认实现, 并通过`IUnknown`在调试版本中将信息发送到转储设备来实现。

`IPersistPropertyBag`与[IPropertyBag](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa768196\(v=vs.85\))和[IErrorLog](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa768231\(v=vs.85\))一起工作。 后两个接口必须由客户端实现。 然后`IPropertyBag`, 客户端将保存并加载对象的各个属性。 通过`IErrorLog`, 对象和客户端都可以报告遇到的任何错误。

**相关文章**[Atl 教程](../../atl/active-template-library-atl-tutorial.md),[创建 atl 项目](../../atl/reference/creating-an-atl-project.md)

## <a name="inheritance-hierarchy"></a>继承层次结构

`IPersistPropertyBag`

`IPersistPropertyBagImpl`

## <a name="requirements"></a>要求

**标头:** atlcom。h

##  <a name="getclassid"></a>IPersistPropertyBagImpl:: GetClassID

检索对象的 CLSID。

```
STDMETHOD(GetClassID)(CLSID* pClassID);
```

### <a name="remarks"></a>备注

请参阅 Windows SDK 中的[IPersist:: GetClassID](/windows/win32/api/objidl/nf-objidl-ipersist-getclassid) 。

##  <a name="initnew"></a>IPersistPropertyBagImpl:: InitNew

初始化新创建的对象。

```
STDMETHOD(InitNew)();
```

### <a name="return-value"></a>返回值

返回 S_OK。

### <a name="remarks"></a>备注

请参阅 Windows SDK 中的[IPersistPropertyBag:: InitNew](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa768204\(v=vs.85\)) 。

##  <a name="load"></a>IPersistPropertyBagImpl:: Load

从客户端提供的属性包加载对象的属性。

```
STDMETHOD(Load)(LPPROPERTYBAG pPropBag, LPERRORLOG pErrorLog);
```

### <a name="remarks"></a>备注

ATL 使用对象的属性映射来检索此信息。

请参阅 Windows SDK 中的[IPersistPropertyBag:: Load](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa768206\(v=vs.85\)) 。

##  <a name="save"></a>IPersistPropertyBagImpl:: Save

将对象的属性保存到客户端提供的属性包中。

```
STDMETHOD(Save)(
    LPPROPERTYBAG pPropBag,
    BOOL fClearDirty,
    BOOL fSaveAllProperties);
```

### <a name="remarks"></a>备注

ATL 使用对象的属性映射来存储此信息。 默认情况下, 此方法将保存所有属性, 而不考虑*fSaveAllProperties*的值。

请参阅 Windows SDK 中的[IPersistPropertyBag:: Save](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa768207\(v=vs.85\)) 。

## <a name="see-also"></a>请参阅

[BEGIN_PROP_MAP](property-map-macros.md#begin_prop_map)<br/>
[类概述](../../atl/atl-class-overview.md)
