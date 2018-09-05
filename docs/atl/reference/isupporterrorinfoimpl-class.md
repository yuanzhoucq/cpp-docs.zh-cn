---
title: ISupportErrorInfoImpl 类 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- ISupportErrorInfoImpl
- ATLCOM/ATL::ISupportErrorInfoImpl
- ATLCOM/ATL::ISupportErrorInfoImpl::InterfaceSupportsErrorInfo
dev_langs:
- C++
helpviewer_keywords:
- ISupportErrorInfo ATL implementation
- ISupportErrorInfoImpl class
- error information, ATL
ms.assetid: e33a4b11-a123-41cf-bcea-7b19743902af
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b82299db31a7452a05cdfe709221facda09c3615
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/04/2018
ms.locfileid: "43676070"
---
# <a name="isupporterrorinfoimpl-class"></a>ISupportErrorInfoImpl 类
此类提供的默认实现[ISupportErrorInfo 接口](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-isupporterrorinfo)和单个接口在生成对象上的错误时，可以使用。  
  
> [!IMPORTANT]
>  不能在 Windows 运行时中执行的应用程序中使用此类和其成员。  
  
## <a name="syntax"></a>语法  
  
```
template<const IID* piid>  
class ATL_NO_VTABLE ISupportErrorInfoImpl 
   : public ISupportErrorInfo
```  
  
#### <a name="parameters"></a>参数  
 *piid*  
 指向支持的接口的 IID [IErrorInfo](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-ierrorinfo)。  
  
## <a name="members"></a>成员  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[ISupportErrorInfoImpl::InterfaceSupportsErrorInfo](#interfacesupportserrorinfo)|指示标识接口是否`riid`支持[IErrorInfo](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-ierrorinfo)接口。|  
  
## <a name="remarks"></a>备注  
 [ISupportErrorInfo 接口](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-isupporterrorinfo)可确保错误信息，可以返回到客户端。 对象使用`IErrorInfo`必须实现`ISupportErrorInfo`。  
  
 类`ISupportErrorInfoImpl`提供的默认实现`ISupportErrorInfo`和单个接口在生成对象上的错误时，可以使用。 例如：  
  
 [!code-cpp[NVC_ATL_COM#48](../../atl/codesnippet/cpp/isupporterrorinfoimpl-class_1.h)]  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `ISupportErrorInfo`  
  
 `ISupportErrorInfoImpl`  
  
## <a name="requirements"></a>要求  
 **标头：** atlcom.h  
  
##  <a name="interfacesupportserrorinfo"></a>  ISupportErrorInfoImpl::InterfaceSupportsErrorInfo  
 指示标识接口是否`riid`支持[IErrorInfo](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-ierrorinfo)接口。  
  
```
STDMETHOD(InterfaceSupportsErrorInfo)(REFIID riid);
```  
  
### <a name="remarks"></a>备注  
 请参阅[ISupportErrorInfo::InterfaceSupportsErrorInfo](/previous-versions/windows/desktop/api/oaidl/nf-oaidl-isupporterrorinfo-interfacesupportserrorinfo) Windows SDK 中。  
  
##  <a name="getsize"></a>  IThreadPoolConfig::GetSize  
 调用此方法以获取池中的线程数。  
  
```
STDMETHOD(GetSize)(int* pnNumThreads);
```  
  
### <a name="parameters"></a>参数  
 *pnNumThreads*  
 [out]，如果成功，接收变量的线程数在池中的地址。  
  
### <a name="return-value"></a>返回值  
 返回成功，则为 S_OK 或失败时的错误 HRESULT。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATL_Utilities#134](../../atl/codesnippet/cpp/isupporterrorinfoimpl-class_2.cpp)]  
  
##  <a name="gettimeout"></a>  IThreadPoolConfig::GetTimeout  
 调用此方法以获取最长时间以毫秒为单位，线程池将等待一个线程来关闭的情况下。  
  
```
STDMETHOD(GetTimeout)(DWORD* pdwMaxWait);
```  
  
### <a name="parameters"></a>参数  
 *pdwMaxWait*  
 [out]成功后，接收的最长时间以毫秒为单位，线程池将等待一个线程来关闭的情况下的变量的地址。  
  
### <a name="return-value"></a>返回值  
 返回成功，则为 S_OK 或失败时的错误 HRESULT。  
  
### <a name="example"></a>示例  
 请参阅[IThreadPoolConfig::GetSize](#getsize)。  
  
##  <a name="setsize"></a>  IThreadPoolConfig::SetSize  
 调用此方法以设置在池中的线程数。  
  
```
STDMETHOD(SetSize)int nNumThreads);
```  
  
### <a name="parameters"></a>参数  
 *nNumThreads*  
 请求的池中的线程数。  
  
 如果*nNumThreads*是负数，其绝对值的数值将乘以中要获取的线程总数的计算机的处理器数。  
  
 如果*nNumThreads*为零，ATLS_DEFAULT_THREADSPERPROC 将乘以中要获取的线程总数的计算机的处理器数。  
  
### <a name="return-value"></a>返回值  
 返回成功，则为 S_OK 或失败时的错误 HRESULT。  
  
### <a name="example"></a>示例  
 请参阅[IThreadPoolConfig::GetSize](#getsize)。  
  
##  <a name="settimeout"></a>  IThreadPoolConfig::SetTimeout  
 调用此方法，以毫秒为单位，线程池将等待一个线程来关闭的情况下设置最长的时间。  
  
```
STDMETHOD(SetTimeout)(DWORD dwMaxWait);
```  
  
### <a name="parameters"></a>参数  
 *dwMaxWait*  
 以毫秒为单位，线程池将等待一个线程来关闭请求的最大时间。  
  
### <a name="return-value"></a>返回值  
 返回成功，则为 S_OK 或失败时的错误 HRESULT。  
  
### <a name="example"></a>示例  
 请参阅[IThreadPoolConfig::GetSize](#getsize)。  
  
## <a name="see-also"></a>请参阅  
 [类概述](../../atl/atl-class-overview.md)
