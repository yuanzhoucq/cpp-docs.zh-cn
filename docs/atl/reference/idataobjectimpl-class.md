---
title: IDataObjectImpl 类 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- data transfer [C++]
- data transfer [C++], Uniform Data Transfer
- IDataObjectImpl class
- IDataObject, ATL implementation
ms.assetid: b680f0f7-7795-40a1-a0f6-f48768201c89
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4a2684a3aab8480738d4d64a79681f1930113c71
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/29/2018
ms.locfileid: "43218922"
---
# <a name="idataobjectimpl-class"></a>IDataObjectImpl 类
此类提供用于支持统一数据传输和管理连接的方法。  
  
> [!IMPORTANT]
>  不能在 Windows 运行时中执行的应用程序中使用此类和其成员。  
  
## <a name="syntax"></a>语法  
  
```
template<class T>  
class IDataObjectImpl
```  
  
#### <a name="parameters"></a>参数  
 *T*  
 您的类，派生自`IDataObjectImpl`。  
  
## <a name="members"></a>成员  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[IDataObjectImpl::DAdvise](#dadvise)|建立数据对象和通知接收器之间的连接。 这使通知接收器对象中接收的更改通知。|  
|[IDataObjectImpl::DUnadvise](#dunadvise)|终止先前通过建立的连接`DAdvise`。|  
|[IDataObjectImpl::EnumDAdvise](#enumdadvise)|创建一个枚举器循环访问当前的通知连接。|  
|[IDataObjectImpl::EnumFormatEtc](#enumformatetc)|创建要循环访问的枚举数`FORMATETC`数据对象支持的结构。 ATL 实现返回 E_NOTIMPL。|  
|[IDataObjectImpl::FireDataChange](#firedatachange)|返回到每个通知接收器发送更改通知。|  
|[IDataObjectImpl::GetCanonicalFormatEtc](#getcanonicalformatetc)|检索逻辑上等效`FORMATETC`为一个更复杂的结构。 ATL 实现返回 E_NOTIMPL。|  
|[IDataObjectImpl::GetData](#getdata)|将数据从数据对象传输到客户端。 数据描述中`FORMATETC`结构，以及通过传输`STGMEDIUM`结构。|  
|[IDataObjectImpl::GetDataHere](#getdatahere)|类似于`GetData`，但客户端必须分配`STGMEDIUM`结构。 ATL 实现返回 E_NOTIMPL。|  
|[IDataObjectImpl::QueryGetData](#querygetdata)|确定数据对象是否支持特定`FORMATETC`传输数据的结构。 ATL 实现返回 E_NOTIMPL。|  
|[IDataObjectImpl::SetData](#setdata)|将数据从客户端传输到数据对象。 ATL 实现返回 E_NOTIMPL。|  
  
## <a name="remarks"></a>备注  
 [IDataObject](/windows/desktop/api/objidl/nn-objidl-idataobject)接口提供了方法，以支持统一数据传输。 `IDataObject` 使用标准格式结构[FORMATETC](/windows/desktop/api/objidl/ns-objidl-tagformatetc)并[STGMEDIUM](/windows/desktop/api/objidl/ns-objidl-tagstgmedium)检索和存储数据。  
  
 `IDataObject` 此外可管理向建议接收器来处理数据更改通知的连接。 为了使客户端以接收此数据对象中的数据更改通知，客户端必须实现[IAdviseSink](/windows/desktop/api/objidl/nn-objidl-iadvisesink)上一个名为通知接收器对象的接口。 当客户端然后调用`IDataObject::DAdvise`，数据对象和通知接收器之间建立连接。  
  
 类`IDataObjectImpl`提供的默认实现`IDataObject`并实现`IUnknown`信息发送给转储调试中的设备生成。  
  
 **相关文章** [ATL 教程](../../atl/active-template-library-atl-tutorial.md)，[创建 ATL 项目](../../atl/reference/creating-an-atl-project.md)  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `IDataObject`  
  
 `IDataObjectImpl`  
  
## <a name="requirements"></a>要求  
 **标头：** atlctl.h  
  
##  <a name="dadvise"></a>  IDataObjectImpl::DAdvise  
 建立数据对象和通知接收器之间的连接。  
  
```
HRESULT DAdvise(
    FORMATETC* pformatetc,
    DWORD advf,
    IAdviseSink* pAdvSink,
    DWORD* pdwConnection);
```  
  
### <a name="remarks"></a>备注  
 这使通知接收器对象中接收的更改通知。  
  
 若要终止的连接，调用[DUnadvise](#dunadvise)。  
  
 请参阅[IDataObject::DAdvise](/windows/desktop/api/objidl/nf-objidl-idataobject-dadvise) Windows SDK 中。  
  
##  <a name="dunadvise"></a>  IDataObjectImpl::DUnadvise  
 终止先前通过建立的连接[DAdvise](#dadvise)。  
  
```
HRESULT DUnadvise(DWORD dwConnection);
```  
  
### <a name="remarks"></a>备注  
 请参阅[IDataObject::DUnadvise](/windows/desktop/api/objidl/nf-objidl-idataobject-dunadvise) Windows SDK 中。  
  
##  <a name="enumdadvise"></a>  IDataObjectImpl::EnumDAdvise  
 创建一个枚举器循环访问当前的通知连接。  
  
```
HRESULT DAdvise(
    FORMATETC* pformatetc,
    DWORD advf,
    IAdviseSink* pAdvSink,
    DWORD* pdwConnection);
```  
  
### <a name="remarks"></a>备注  
 请参阅[IDataObject::EnumDAdvise](/windows/desktop/api/objidl/nf-objidl-idataobject-enumdadvise) Windows SDK 中。  
  
##  <a name="enumformatetc"></a>  IDataObjectImpl::EnumFormatEtc  
 创建要循环访问的枚举数`FORMATETC`数据对象支持的结构。  
  
```
HRESULT EnumFormatEtc(  
    DWORD dwDirection,
    IEnumFORMATETC** ppenumFormatEtc);
```  
  
### <a name="remarks"></a>备注  
 请参阅[IDataObject::EnumFormatEtc](/windows/desktop/api/objidl/nf-objidl-idataobject-enumformatetc) Windows SDK 中。  
  
### <a name="return-value"></a>返回值  
 返回 E_NOTIMPL。  
  
##  <a name="firedatachange"></a>  IDataObjectImpl::FireDataChange  
 返回到当前管理的每个通知接收器发送更改通知。  
  
```
HRESULT FireDataChange();
```  
  
### <a name="return-value"></a>返回值  
 标准的 HRESULT 值。  
  
##  <a name="getcanonicalformatetc"></a>  IDataObjectImpl::GetCanonicalFormatEtc  
 检索逻辑上等效`FORMATETC`为一个更复杂的结构。  
  
```
HRESULT GetCanonicalFormatEtc(FORMATETC* pformatetcIn, FORMATETC* pformatetcOut);
```  
  
### <a name="return-value"></a>返回值  
 返回 E_NOTIMPL。  
  
### <a name="remarks"></a>备注  
 请参阅[IDataObject::GetCanonicalFormatEtc](/windows/desktop/api/objidl/nf-objidl-idataobject-getcanonicalformatetc) Windows SDK 中。  
  
##  <a name="getdata"></a>  IDataObjectImpl::GetData  
 将数据从数据对象传输到客户端。  
  
```
HRESULT GetData(
    FORMATETC* pformatetcIn,
    STGMEDIUM* pmedium);
```  
  
### <a name="remarks"></a>备注  
 *PformatetcIn*参数必须指定 TYMED_MFPICT 存储介质类型。  
  
 请参阅[idataobject:: Getdata](/windows/desktop/api/objidl/nf-objidl-idataobject-getdata) Windows SDK 中。  
  
##  <a name="getdatahere"></a>  IDataObjectImpl::GetDataHere  
 类似于`GetData`，但客户端必须分配`STGMEDIUM`结构。  
  
```
HRESULT GetDataHere(
    FORMATETC* pformatetc,
    STGMEDIUM* pmedium);
```  
  
### <a name="return-value"></a>返回值  
 返回 E_NOTIMPL。  
  
### <a name="remarks"></a>备注  
 请参阅[IDataObject::GetDataHere](/windows/desktop/api/objidl/nf-objidl-idataobject-getdatahere) Windows SDK 中。  
  
##  <a name="querygetdata"></a>  IDataObjectImpl::QueryGetData  
 确定数据对象是否支持特定`FORMATETC`传输数据的结构。  
  
```
HRESULT QueryGetData(FORMATETC* pformatetc);
```  
  
### <a name="return-value"></a>返回值  
 返回 E_NOTIMPL。  
  
### <a name="remarks"></a>备注  
 请参阅[IDataObject::QueryGetData](/windows/desktop/api/objidl/nf-objidl-idataobject-querygetdata) Windows SDK 中。  
  
##  <a name="setdata"></a>  IDataObjectImpl::SetData  
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
 请参阅[IDataObject::SetData](/windows/desktop/api/objidl/nf-objidl-idataobject-setdata) Windows SDK 中。  
  
## <a name="see-also"></a>请参阅  
 [类概述](../../atl/atl-class-overview.md)
