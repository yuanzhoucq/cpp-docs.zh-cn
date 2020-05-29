---
title: IPersistStreamInitImpl 类
ms.date: 11/04/2016
f1_keywords:
- IPersistStreamInitImpl
- ATLCOM/ATL::IPersistStreamInitImpl
- ATLCOM/ATL::IPersistStreamInitImpl::GetClassID
- ATLCOM/ATL::IPersistStreamInitImpl::GetSizeMax
- ATLCOM/ATL::IPersistStreamInitImpl::InitNew
- ATLCOM/ATL::IPersistStreamInitImpl::IsDirty
- ATLCOM/ATL::IPersistStreamInitImpl::Load
- ATLCOM/ATL::IPersistStreamInitImpl::Save
helpviewer_keywords:
- IPersistStreamInit ATL implementation
- IPersistStreamInitImpl class
- streams, ATL
ms.assetid: ef217c3c-020f-4cf8-871e-ef68e57865b8
ms.openlocfilehash: 0d6ac4639ac0cfb97416ca80b7a2ec3903d7b8e6
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81326464"
---
# <a name="ipersiststreaminitimpl-class"></a>IPersistStreamInitImpl 类

此类实现`IUnknown`并提供[IPersistStreamInit](/windows/win32/api/ocidl/nn-ocidl-ipersiststreaminit)接口的默认实现。

> [!IMPORTANT]
> 此类及其成员不能在 Windows 运行时中执行的应用程序中使用。

## <a name="syntax"></a>语法

```
template<class T>
class ATL_NO_VTABLE IPersistStreamInitImpl
   : public IPersistStreamInit
```

#### <a name="parameters"></a>参数

*T*<br/>
您的类，派生自`IPersistStreamInitImpl`。

## <a name="members"></a>成员

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[I 坚持流化：：获取类ID](#getclassid)|检索对象的 CLSID。|
|[I 坚持流化：：获取 SizeMax](#getsizemax)|检索保存对象数据所需的流的大小。 ATL 实现返回E_NOTIMPL。|
|[I 坚持流化：：Initnew](#initnew)|初始化新创建的对象。|
|[我坚持流化：：是肮脏的](#isdirty)|检查对象的数据自上次保存以来是否已更改。|
|[I 坚持流化：：加载](#load)|从指定的流加载对象的属性。|
|[I 坚持流化：：保存](#save)|将对象的属性保存到指定的流。|

## <a name="remarks"></a>备注

[IPersistStreamInit](/windows/win32/api/ocidl/nn-ocidl-ipersiststreaminit)接口允许客户端请求对象加载，并将其持久数据保存到单个流中。 类`IPersistStreamInitImpl`通过在调试生成中向转储设备发送`IUnknown`信息来提供此接口的默认实现和实现。

**相关文章** [ATL 教程](../../atl/active-template-library-atl-tutorial.md)， 创建[ATL 项目](../../atl/reference/creating-an-atl-project.md)

## <a name="inheritance-hierarchy"></a>继承层次结构

`IPersistStreamInit`

`IPersistStreamInitImpl`

## <a name="requirements"></a>要求

**标题：** atlcom.h

## <a name="ipersiststreaminitimplgetclassid"></a><a name="getclassid"></a>I 坚持流化：：获取类ID

检索对象的 CLSID。

```
STDMETHOD(GetClassID)(CLSID* pClassID);
```

### <a name="remarks"></a>备注

请参阅[IPersist：在](/windows/win32/api/objidl/nf-objidl-ipersist-getclassid)Windows SDK 中获取 ClassID。

## <a name="ipersiststreaminitimplgetsizemax"></a><a name="getsizemax"></a>I 坚持流化：：获取 SizeMax

检索保存对象数据所需的流的大小。

```
STDMETHOD(GetSizeMax)(ULARGE_INTEGER FAR* pcbSize);
```

### <a name="return-value"></a>返回值

返回 E_NOTIMPL。

### <a name="remarks"></a>备注

请参阅[IPersistStreaminit：在](/windows/win32/api/ocidl/nf-ocidl-ipersiststreaminit-getsizemax)Windows SDK 中获取 SizeMax。

## <a name="ipersiststreaminitimplinitnew"></a><a name="initnew"></a>I 坚持流化：：Initnew

初始化新创建的对象。

```
STDMETHOD(InitNew)();
```

### <a name="remarks"></a>备注

请参阅[IPersistStreaminit：：Windows](/windows/win32/api/ocidl/nf-ocidl-ipersiststreaminit-initnew) SDK 中的"新"。

## <a name="ipersiststreaminitimplisdirty"></a><a name="isdirty"></a>我坚持流化：：是肮脏的

检查对象的数据自上次保存以来是否已更改。

```
STDMETHOD(IsDirty)();
```

### <a name="remarks"></a>备注

请参阅[IPersistStreaminit：Windows](/windows/win32/api/ocidl/nf-ocidl-ipersiststreaminit-isdirty) SDK 中脏话。

## <a name="ipersiststreaminitimplload"></a><a name="load"></a>I 坚持流化：：加载

从指定的流加载对象的属性。

```
STDMETHOD(Load)(LPSTREAM pStm);
```

### <a name="remarks"></a>备注

ATL 使用对象的属性映射来检索此信息。

请参阅[IPersistStreaminit：：](/windows/win32/api/ocidl/nf-ocidl-ipersiststreaminit-load)在 Windows SDK 中加载。

## <a name="ipersiststreaminitimplsave"></a><a name="save"></a>I 坚持流化：：保存

将对象的属性保存到指定的流。

```
STDMETHOD(Save)(LPSTREAM pStm, BOOL fClearDirty);
```

### <a name="remarks"></a>备注

ATL 使用对象的属性映射来存储此信息。

请参阅[IPersistStreamInit：：保存在](/windows/win32/api/ocidl/nf-ocidl-ipersiststreaminit-save)Windows SDK 中。

## <a name="see-also"></a>另请参阅

[存储和流](/windows/win32/Stg/storages-and-streams)<br/>
[类概述](../../atl/atl-class-overview.md)
