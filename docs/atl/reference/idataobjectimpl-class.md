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
ms.openlocfilehash: 379dd3304d96afcd2b0e98ec4a98f1bac64d4ad9
ms.sourcegitcommit: 13f42c339fb7af935e3a93ac80e350d5e784c9f1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/31/2020
ms.locfileid: "87470766"
---
# <a name="idataobjectimpl-class"></a>IDataObjectImpl 类

此类提供用于支持统一数据传输和管理连接的方法。

> [!IMPORTANT]
> 此类及其成员不能用于在 Windows 运行时中执行的应用程序。

## <a name="syntax"></a>语法

```
template<class T>
class IDataObjectImpl
```

#### <a name="parameters"></a>参数

*T*<br/>
派生自的类 `IDataObjectImpl` 。

## <a name="members"></a>成员

### <a name="public-methods"></a>公共方法

|“属性”|描述|
|----------|-----------------|
|[IDataObjectImpl：:D 建议](#dadvise)|在数据对象和通知接收器之间建立连接。 这样，通知接收器就可以接收对象中更改的通知。|
|[IDataObjectImpl：:D Unadvise](#dunadvise)|终止先前通过建立的连接 `DAdvise` 。|
|[IDataObjectImpl::EnumDAdvise](#enumdadvise)|创建一个枚举器，用于循环访问当前的通知连接。|
|[IDataObjectImpl：： EnumFormatEtc](#enumformatetc)|创建一个枚举器，用于循环访问 `FORMATETC` 数据对象支持的结构。 ATL 实现返回 E_NOTIMPL。|
|[IDataObjectImpl::FireDataChange](#firedatachange)|将更改通知发送回每个建议接收器。|
|[IDataObjectImpl::GetCanonicalFormatEtc](#getcanonicalformatetc)|检索逻辑上等效于 `FORMATETC` 更复杂的结构。 ATL 实现返回 E_NOTIMPL。|
|[IDataObjectImpl：：](#getdata)|将数据从数据对象传输到客户端。 数据在结构中进行了描述 `FORMATETC` ，并通过结构传输 `STGMEDIUM` 。|
|[IDataObjectImpl：： GetDataHere](#getdatahere)|与类似 `GetData` ，不同之处在于，客户端必须分配 `STGMEDIUM` 结构。 ATL 实现返回 E_NOTIMPL。|
|[IDataObjectImpl::QueryGetData](#querygetdata)|确定数据对象是否支持 `FORMATETC` 用于传输数据的特定结构。 ATL 实现返回 E_NOTIMPL。|
|[IDataObjectImpl：： SetData](#setdata)|将数据从客户端传输到数据对象。 ATL 实现返回 E_NOTIMPL。|

## <a name="remarks"></a>备注

[IDataObject](/windows/win32/api/objidl/nn-objidl-idataobject)接口提供支持统一数据传输的方法。 `IDataObject`使用标准格式结构[FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc)和[STGMEDIUM](/windows/win32/api/objidl/ns-objidl-ustgmedium-r1)检索和存储数据。

`IDataObject`还管理连接以便通知接收器处理数据更改通知。 为了使客户端能够从数据对象接收数据更改通知，客户端必须在称为建议接收器的对象上实现[IAdviseSink](/windows/win32/api/objidl/nn-objidl-iadvisesink)接口。 当客户端调用时 `IDataObject::DAdvise` ，将在数据对象和通知接收器之间建立连接。

类 `IDataObjectImpl` 提供的默认实现 `IDataObject` ，并 `IUnknown` 通过在调试版本中将信息发送到转储设备来实现。

**相关文章** [ATL 教程](../../atl/active-template-library-atl-tutorial.md)，[创建 atl 项目](../../atl/reference/creating-an-atl-project.md)

## <a name="inheritance-hierarchy"></a>继承层次结构

`IDataObject`

`IDataObjectImpl`

## <a name="requirements"></a>要求

**标头：** atlctl

## <a name="idataobjectimpldadvise"></a><a name="dadvise"></a>IDataObjectImpl：:D 建议

在数据对象和通知接收器之间建立连接。

```
HRESULT DAdvise(
    FORMATETC* pformatetc,
    DWORD advf,
    IAdviseSink* pAdvSink,
    DWORD* pdwConnection);
```

### <a name="remarks"></a>备注

这样，通知接收器就可以接收对象中更改的通知。

若要终止连接，请调用[DUnadvise](#dunadvise)。

请参阅 Windows SDK 中的[IDataObject：:D 建议](/windows/win32/api/objidl/nf-objidl-idataobject-dadvise)。

## <a name="idataobjectimpldunadvise"></a><a name="dunadvise"></a>IDataObjectImpl：:D Unadvise

终止先前通过[DAdvise](#dadvise)建立的连接。

```
HRESULT DUnadvise(DWORD dwConnection);
```

### <a name="remarks"></a>备注

请参阅 IDataObject： Windows SDK 中的[：:D unadvise](/windows/win32/api/objidl/nf-objidl-idataobject-dunadvise) 。

## <a name="idataobjectimplenumdadvise"></a><a name="enumdadvise"></a>IDataObjectImpl::EnumDAdvise

创建一个枚举器，用于循环访问当前的通知连接。

```
HRESULT DAdvise(
    FORMATETC* pformatetc,
    DWORD advf,
    IAdviseSink* pAdvSink,
    DWORD* pdwConnection);
```

### <a name="remarks"></a>备注

请参阅 Windows SDK 中的[IDataObject：： EnumDAdvise](/windows/win32/api/objidl/nf-objidl-idataobject-enumdadvise) 。

## <a name="idataobjectimplenumformatetc"></a><a name="enumformatetc"></a>IDataObjectImpl：： EnumFormatEtc

创建一个枚举器，用于循环访问 `FORMATETC` 数据对象支持的结构。

```
HRESULT EnumFormatEtc(
    DWORD dwDirection,
    IEnumFORMATETC** ppenumFormatEtc);
```

### <a name="remarks"></a>备注

请参阅 Windows SDK 中的[IDataObject：： EnumFormatEtc](/windows/win32/api/objidl/nf-objidl-idataobject-enumformatetc) 。

### <a name="return-value"></a>返回值

返回 E_NOTIMPL。

## <a name="idataobjectimplfiredatachange"></a><a name="firedatachange"></a>IDataObjectImpl::FireDataChange

将更改通知发送回当前正在管理的每个通知接收器。

```
HRESULT FireDataChange();
```

### <a name="return-value"></a>返回值

标准的 HRESULT 值。

## <a name="idataobjectimplgetcanonicalformatetc"></a><a name="getcanonicalformatetc"></a>IDataObjectImpl::GetCanonicalFormatEtc

检索逻辑上等效于 `FORMATETC` 更复杂的结构。

```
HRESULT GetCanonicalFormatEtc(FORMATETC* pformatetcIn, FORMATETC* pformatetcOut);
```

### <a name="return-value"></a>返回值

返回 E_NOTIMPL。

### <a name="remarks"></a>备注

请参阅 Windows SDK 中的[IDataObject：： GetCanonicalFormatEtc](/windows/win32/api/objidl/nf-objidl-idataobject-getcanonicalformatetc) 。

## <a name="idataobjectimplgetdata"></a><a name="getdata"></a>IDataObjectImpl：：

将数据从数据对象传输到客户端。

```
HRESULT GetData(
    FORMATETC* pformatetcIn,
    STGMEDIUM* pmedium);
```

### <a name="remarks"></a>备注

*PformatetcIn*参数必须指定 TYMED_MFPICT 的存储中等类型。

请参阅 Windows SDK 中的[IDataObject：：：：](/windows/win32/api/objidl/nf-objidl-idataobject-getdata) 。

## <a name="idataobjectimplgetdatahere"></a><a name="getdatahere"></a>IDataObjectImpl：： GetDataHere

与类似 `GetData` ，不同之处在于，客户端必须分配 `STGMEDIUM` 结构。

```
HRESULT GetDataHere(
    FORMATETC* pformatetc,
    STGMEDIUM* pmedium);
```

### <a name="return-value"></a>返回值

返回 E_NOTIMPL。

### <a name="remarks"></a>备注

请参阅 Windows SDK 中的[IDataObject：： GetDataHere](/windows/win32/api/objidl/nf-objidl-idataobject-getdatahere) 。

## <a name="idataobjectimplquerygetdata"></a><a name="querygetdata"></a>IDataObjectImpl::QueryGetData

确定数据对象是否支持 `FORMATETC` 用于传输数据的特定结构。

```
HRESULT QueryGetData(FORMATETC* pformatetc);
```

### <a name="return-value"></a>返回值

返回 E_NOTIMPL。

### <a name="remarks"></a>备注

请参阅 Windows SDK 中的[IDataObject：： QueryGetData](/windows/win32/api/objidl/nf-objidl-idataobject-querygetdata) 。

## <a name="idataobjectimplsetdata"></a><a name="setdata"></a>IDataObjectImpl：： SetData

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

请参阅 Windows SDK 中的[IDataObject：： SetData](/windows/win32/api/objidl/nf-objidl-idataobject-setdata) 。

## <a name="see-also"></a>请参阅

[类概述](../../atl/atl-class-overview.md)
