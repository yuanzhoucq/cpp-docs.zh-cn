---
title: IDataObjectImpl 类
ms.date: 11/04/2016
f1_keywords:
- IDataObjectImpl
- ATLCTL/ATL::IDataObjectImpl
- ATLCTL/ATL::IDataObjectImpl::DAdvise
- ATLCTL/ATL::IDataObjectImpl::DUnadvise
- ATLCTL/ATL::IDataObjectImpl::EnumDAdvise
- ATLCTL/ATL::IDataObjectImpl::EnumFormatEtc
- ATLCTL/ATL::IDataObjectImpl::FireDataChange
- ATLCTL/ATL::IDataObjectImpl::GetCanonicalFormatEtc
- ATLCTL/ATL::IDataObjectImpl::GetData
- ATLCTL/ATL::IDataObjectImpl::GetDataHere
- ATLCTL/ATL::IDataObjectImpl::QueryGetData
- ATLCTL/ATL::IDataObjectImpl::SetData
helpviewer_keywords:
- data transfer [C++]
- data transfer [C++], Uniform Data Transfer
- IDataObjectImpl class
- IDataObject, ATL implementation
ms.assetid: b680f0f7-7795-40a1-a0f6-f48768201c89
ms.openlocfilehash: 618f8248a03297120ae2504bcb30ba8f080b184d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81329843"
---
# <a name="idataobjectimpl-class"></a>IDataObjectImpl 类

此类提供支持统一数据传输和管理连接的方法。

> [!IMPORTANT]
> 此类及其成员不能在 Windows 运行时中执行的应用程序中使用。

## <a name="syntax"></a>语法

```
template<class T>
class IDataObjectImpl
```

#### <a name="parameters"></a>参数

*T*<br/>
您的类，派生自`IDataObjectImpl`。

## <a name="members"></a>成员

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[IDataObjectimpl：:D建议](#dadvise)|在数据对象和通知接收器之间建立连接。 这使建议接收器能够接收对象中更改的通知。|
|[IDataObjectimpl：:D无建议](#dunadvise)|终止以前通过`DAdvise`建立的连接。|
|[IDataObjectimpl：：枚举建议](#enumdadvise)|创建枚举器以通过当前咨询连接迭代。|
|[IDataObjectimple：：枚举格式](#enumformatetc)|创建枚举器以循环浏览数据对象支持`FORMATETC`的结构。 ATL 实现返回E_NOTIMPL。|
|[IDataObjectimpl：：火数据更改](#firedatachange)|将更改通知发送回每个通知接收器。|
|[IDataObjectimpl：：获取规范格式](#getcanonicalformatetc)|检索与更复杂的结构在逻辑`FORMATETC`上等效的结构。 ATL 实现返回E_NOTIMPL。|
|[IDataObjectimpl：：获取数据](#getdata)|将数据从数据对象传输到客户端。 数据在`FORMATETC`结构中描述，并通过`STGMEDIUM`结构传输。|
|[IDataObjectimpl：：获取数据在这里](#getdatahere)|与`GetData`类似 ，但客户端必须分配`STGMEDIUM`结构。 ATL 实现返回E_NOTIMPL。|
|[IDataObjectimpl：：查询获取数据](#querygetdata)|确定数据对象是否支持用于传输数据`FORMATETC`的特定结构。 ATL 实现返回E_NOTIMPL。|
|[IDataObjectimpl：：集数据](#setdata)|将数据从客户端传输到数据对象。 ATL 实现返回E_NOTIMPL。|

## <a name="remarks"></a>备注

[IDataObject](/windows/win32/api/objidl/nn-objidl-idataobject)接口提供了支持统一数据传输的方法。 `IDataObject`使用标准格式结构[FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc)和[STGMEDIUM](/windows/win32/api/objidl/ns-objidl-ustgmedium~r1)来检索和存储数据。

`IDataObject`还管理连接，建议接收器处理数据更改通知。 为了使客户端从数据对象接收数据更改通知，客户端必须在称为建议接收器的对象上实现[IAdviseSink](/windows/win32/api/objidl/nn-objidl-iadvisesink)接口。 当客户端然后调用`IDataObject::DAdvise`时 ，数据对象和通知接收器之间建立连接。

类`IDataObjectImpl`通过在调试生成中向`IDataObject`转储设备`IUnknown`发送信息来提供 和 实现的默认实现。

**相关文章** [ATL 教程](../../atl/active-template-library-atl-tutorial.md)， 创建[ATL 项目](../../atl/reference/creating-an-atl-project.md)

## <a name="inheritance-hierarchy"></a>继承层次结构

`IDataObject`

`IDataObjectImpl`

## <a name="requirements"></a>要求

**标题：** atlctl.h

## <a name="idataobjectimpldadvise"></a><a name="dadvise"></a>IDataObjectimpl：:D建议

在数据对象和通知接收器之间建立连接。

```
HRESULT DAdvise(
    FORMATETC* pformatetc,
    DWORD advf,
    IAdviseSink* pAdvSink,
    DWORD* pdwConnection);
```

### <a name="remarks"></a>备注

这使建议接收器能够接收对象中更改的通知。

要终止连接，请致电[DUnadvise](#dunadvise)。

请参阅[IDataObject：:D Windows](/windows/win32/api/objidl/nf-objidl-idataobject-dadvise) SDK 中的建议。

## <a name="idataobjectimpldunadvise"></a><a name="dunadvise"></a>IDataObjectimpl：:D无建议

终止以前通过[DAdvise](#dadvise)建立的连接。

```
HRESULT DUnadvise(DWORD dwConnection);
```

### <a name="remarks"></a>备注

请参阅[IDataObject：:D在](/windows/win32/api/objidl/nf-objidl-idataobject-dunadvise)Windows SDK 中提供"不建议"。

## <a name="idataobjectimplenumdadvise"></a><a name="enumdadvise"></a>IDataObjectimpl：：枚举建议

创建枚举器以通过当前咨询连接迭代。

```
HRESULT DAdvise(
    FORMATETC* pformatetc,
    DWORD advf,
    IAdviseSink* pAdvSink,
    DWORD* pdwConnection);
```

### <a name="remarks"></a>备注

请参阅[IDataObject：：在](/windows/win32/api/objidl/nf-objidl-idataobject-enumdadvise)Windows SDK 中提供枚举建议。

## <a name="idataobjectimplenumformatetc"></a><a name="enumformatetc"></a>IDataObjectimple：：枚举格式

创建枚举器以循环浏览数据对象支持`FORMATETC`的结构。

```
HRESULT EnumFormatEtc(
    DWORD dwDirection,
    IEnumFORMATETC** ppenumFormatEtc);
```

### <a name="remarks"></a>备注

请参阅[IDataObject：：Windows SDK 中的枚举格式。](/windows/win32/api/objidl/nf-objidl-idataobject-enumformatetc)

### <a name="return-value"></a>返回值

返回 E_NOTIMPL。

## <a name="idataobjectimplfiredatachange"></a><a name="firedatachange"></a>IDataObjectimpl：：火数据更改

将更改通知发送回当前正在管理的每个通知接收器。

```
HRESULT FireDataChange();
```

### <a name="return-value"></a>返回值

标准 HRESULT 值。

## <a name="idataobjectimplgetcanonicalformatetc"></a><a name="getcanonicalformatetc"></a>IDataObjectimpl：：获取规范格式

检索与更复杂的结构在逻辑`FORMATETC`上等效的结构。

```
HRESULT GetCanonicalFormatEtc(FORMATETC* pformatetcIn, FORMATETC* pformatetcOut);
```

### <a name="return-value"></a>返回值

返回 E_NOTIMPL。

### <a name="remarks"></a>备注

请参阅[IDataObject：在](/windows/win32/api/objidl/nf-objidl-idataobject-getcanonicalformatetc)Windows SDK 中获取规范格式。

## <a name="idataobjectimplgetdata"></a><a name="getdata"></a>IDataObjectimpl：：获取数据

将数据从数据对象传输到客户端。

```
HRESULT GetData(
    FORMATETC* pformatetcIn,
    STGMEDIUM* pmedium);
```

### <a name="remarks"></a>备注

*pformatetcIn*参数必须指定存储介质类型的TYMED_MFPICT。

请参阅[IDataObject：获取](/windows/win32/api/objidl/nf-objidl-idataobject-getdata)Windows SDK 中的数据。

## <a name="idataobjectimplgetdatahere"></a><a name="getdatahere"></a>IDataObjectimpl：：获取数据在这里

与`GetData`类似 ，但客户端必须分配`STGMEDIUM`结构。

```
HRESULT GetDataHere(
    FORMATETC* pformatetc,
    STGMEDIUM* pmedium);
```

### <a name="return-value"></a>返回值

返回 E_NOTIMPL。

### <a name="remarks"></a>备注

请参阅[IDataObject：在](/windows/win32/api/objidl/nf-objidl-idataobject-getdatahere)Windows SDK 中获取数据。

## <a name="idataobjectimplquerygetdata"></a><a name="querygetdata"></a>IDataObjectimpl：：查询获取数据

确定数据对象是否支持用于传输数据`FORMATETC`的特定结构。

```
HRESULT QueryGetData(FORMATETC* pformatetc);
```

### <a name="return-value"></a>返回值

返回 E_NOTIMPL。

### <a name="remarks"></a>备注

请参阅[IDataObject：：查询 Windows](/windows/win32/api/objidl/nf-objidl-idataobject-querygetdata) SDK 中的数据获取数据。

## <a name="idataobjectimplsetdata"></a><a name="setdata"></a>IDataObjectimpl：：集数据

将数据从客户端传输到数据对象。

```
HRESULT SetData(
    FORMATETC* pformatetc,
    STGMEDIUM* pmedium,
    BOOL fRelease);
```

### <a name="return-value"></a>返回值

返回 E_NOTIMPL。

### <a name="remarks"></a>备注

请参阅[IDataObject：在](/windows/win32/api/objidl/nf-objidl-idataobject-setdata)Windows SDK 中设置数据。

## <a name="see-also"></a>另请参阅

[类概述](../../atl/atl-class-overview.md)
