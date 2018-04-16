---
title: "IDataObjectImpl 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
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
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 644f498a491605fb69b18ec53afee689f5f90a26
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="idataobjectimpl-class"></a>IDataObjectImpl 类
此类提供用于支持统一数据传输和管理连接的方法。  
  
> [!IMPORTANT]
>  此类及其成员无法在 Windows 运行时中执行的应用中使用。  
  
## <a name="syntax"></a>语法  
  
```
template<class T>  
class IDataObjectImpl
```  
  
#### <a name="parameters"></a>参数  
 `T`  
 你的类，派生自`IDataObjectImpl`。  
  
## <a name="members"></a>成员  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[IDataObjectImpl::DAdvise](#dadvise)|建立数据对象和通知接收器之间的连接。 这使通知接收器对象中接收的更改的通知。|  
|[IDataObjectImpl::DUnadvise](#dunadvise)|终止通过以前建立的连接`DAdvise`。|  
|[IDataObjectImpl::EnumDAdvise](#enumdadvise)|创建一个枚举器循环访问当前的通知连接。|  
|[IDataObjectImpl::EnumFormatEtc](#enumformatetc)|创建一个枚举器循环访问**FORMATETC**数据对象支持的结构。 ATL 实现返回**E_NOTIMPL**。|  
|[IDataObjectImpl::FireDataChange](#firedatachange)|将更改通知发送回每个通知接收器。|  
|[IDataObjectImpl::GetCanonicalFormatEtc](#getcanonicalformatetc)|检索逻辑上等效**FORMATETC**为一个更复杂的结构。 ATL 实现返回**E_NOTIMPL**。|  
|[IDataObjectImpl::GetData](#getdata)|将数据从数据对象传输到客户端。 数据描述中**FORMATETC**结构以及通过传输**STGMEDIUM**结构。|  
|[IDataObjectImpl::GetDataHere](#getdatahere)|类似于`GetData`，只是客户端必须分配**STGMEDIUM**结构。 ATL 实现返回**E_NOTIMPL**。|  
|[IDataObjectImpl::QueryGetData](#querygetdata)|确定数据对象是否支持特定**FORMATETC**传输数据的结构。 ATL 实现返回**E_NOTIMPL**。|  
|[IDataObjectImpl::SetData](#setdata)|将数据从客户端传输到数据对象。 ATL 实现返回**E_NOTIMPL**。|  
  
## <a name="remarks"></a>备注  
 [IDataObject](http://msdn.microsoft.com/library/windows/desktop/ms688421)接口提供了用于支持统一数据传输方法。 `IDataObject`使用标准格式结构[FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177)和[STGMEDIUM](http://msdn.microsoft.com/library/windows/desktop/ms683812)以检索和存储数据。  
  
 `IDataObject`此外管理连接来建议接收器，以处理数据更改通知。 为了使客户端接收此数据对象中的数据更改通知，在客户端必须实现[IAdviseSink](http://msdn.microsoft.com/library/windows/desktop/ms692513)调用建议接收器对象接口。 当客户端然后调用**IDataObject::DAdvise**，数据对象和通知接收器之间建立的连接。  
  
 类`IDataObjectImpl`提供的默认实现`IDataObject`并实现**IUnknown**信息发送给转储设备在调试生成。  
  
 **相关文章** [ATL 教程](../../atl/active-template-library-atl-tutorial.md)，[创建 ATL 项目](../../atl/reference/creating-an-atl-project.md)  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `IDataObject`  
  
 `IDataObjectImpl`  
  
## <a name="requirements"></a>惠?  
 **标头：** atlctl.h  
  
##  <a name="dadvise"></a>IDataObjectImpl::DAdvise  
 建立数据对象和通知接收器之间的连接。  
  
```
HRESULT DAdvise(
    FORMATETC* pformatetc,
    DWORD advf,
    IAdviseSink* pAdvSink,
    DWORD* pdwConnection);
```  
  
### <a name="remarks"></a>备注  
 这使通知接收器对象中接收的更改的通知。  
  
 若要终止连接，调用[DUnadvise](#dunadvise)。  
  
 请参阅[IDataObject::DAdvise](http://msdn.microsoft.com/library/windows/desktop/ms692579) Windows SDK 中。  
  
##  <a name="dunadvise"></a>IDataObjectImpl::DUnadvise  
 终止通过以前建立的连接[DAdvise](#dadvise)。  
  
```
HRESULT DUnadvise(DWORD dwConnection);
```  
  
### <a name="remarks"></a>备注  
 请参阅[IDataObject::DUnadvise](http://msdn.microsoft.com/library/windows/desktop/ms692448) Windows SDK 中。  
  
##  <a name="enumdadvise"></a>IDataObjectImpl::EnumDAdvise  
 创建一个枚举器循环访问当前的通知连接。  
  
```
HRESULT DAdvise(
    FORMATETC* pformatetc,
    DWORD advf,
    IAdviseSink* pAdvSink,
    DWORD* pdwConnection);
```  
  
### <a name="remarks"></a>备注  
 请参阅[IDataObject::EnumDAdvise](http://msdn.microsoft.com/library/windows/desktop/ms680127) Windows SDK 中。  
  
##  <a name="enumformatetc"></a>IDataObjectImpl::EnumFormatEtc  
 创建一个枚举器循环访问**FORMATETC**数据对象支持的结构。  
  
```
HRESULT EnumFormatEtc(  
    DWORD dwDirection,
    IEnumFORMATETC** ppenumFormatEtc);
```  
  
### <a name="remarks"></a>备注  
 请参阅[IDataObject::EnumFormatEtc](http://msdn.microsoft.com/library/windows/desktop/ms683979) Windows SDK 中。  
  
### <a name="return-value"></a>返回值  
 返回**E_NOTIMPL**。  
  
##  <a name="firedatachange"></a>IDataObjectImpl::FireDataChange  
 将更改通知发送回当前管理每个通知接收器。  
  
```
HRESULT FireDataChange();
```  
  
### <a name="return-value"></a>返回值  
 标准 `HRESULT` 值。  
  
##  <a name="getcanonicalformatetc"></a>IDataObjectImpl::GetCanonicalFormatEtc  
 检索逻辑上等效**FORMATETC**为一个更复杂的结构。  
  
```
HRESULT GetCanonicalFormatEtc(FORMATETC* pformatetcIn, FORMATETC* pformatetcOut);
```  
  
### <a name="return-value"></a>返回值  
 返回**E_NOTIMPL**。  
  
### <a name="remarks"></a>备注  
 请参阅[IDataObject::GetCanonicalFormatEtc](http://msdn.microsoft.com/library/windows/desktop/ms680685) Windows SDK 中。  
  
##  <a name="getdata"></a>IDataObjectImpl::GetData  
 将数据从数据对象传输到客户端。  
  
```
HRESULT GetData(
    FORMATETC* pformatetcIn,
    STGMEDIUM* pmedium);
```  
  
### <a name="remarks"></a>备注  
 *PformatetcIn*参数必须指定的存储介质类型**TYMED_MFPICT**。  
  
 请参阅[idataobject:: Getdata](http://msdn.microsoft.com/library/windows/desktop/ms678431) Windows SDK 中。  
  
##  <a name="getdatahere"></a>IDataObjectImpl::GetDataHere  
 类似于`GetData`，只是客户端必须分配**STGMEDIUM**结构。  
  
```
HRESULT GetDataHere(
    FORMATETC* pformatetc,
    STGMEDIUM* pmedium);
```  
  
### <a name="return-value"></a>返回值  
 返回**E_NOTIMPL**。  
  
### <a name="remarks"></a>备注  
 请参阅[IDataObject::GetDataHere](http://msdn.microsoft.com/library/windows/desktop/ms687266) Windows SDK 中。  
  
##  <a name="querygetdata"></a>IDataObjectImpl::QueryGetData  
 确定数据对象是否支持特定**FORMATETC**传输数据的结构。  
  
```
HRESULT QueryGetData(FORMATETC* pformatetc);
```  
  
### <a name="return-value"></a>返回值  
 返回**E_NOTIMPL**。  
  
### <a name="remarks"></a>备注  
 请参阅[IDataObject::QueryGetData](http://msdn.microsoft.com/library/windows/desktop/ms680637) Windows SDK 中。  
  
##  <a name="setdata"></a>IDataObjectImpl::SetData  
 将数据从客户端传输到数据对象。  
  
```
HRESULT SetData(
    FORMATETC* pformatetc,
    STGMEDIUM* pmedium,
    BOOL fRelease);
```  
  
### <a name="return-value"></a>返回值  
 返回**E_NOTIMPL**。  
  
### <a name="remarks"></a>备注  
 请参阅[IDataObject::SetData](http://msdn.microsoft.com/library/windows/desktop/ms686626) Windows SDK 中。  
  
## <a name="see-also"></a>请参阅  
 [类概述](../../atl/atl-class-overview.md)
