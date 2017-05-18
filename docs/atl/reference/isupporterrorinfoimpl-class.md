---
title: "ISupportErrorInfoImpl 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
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
caps.latest.revision: 23
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 604a4bf49490ad2599c857eb3afd527d67e1e25b
ms.openlocfilehash: 320cb27d1d22a5e4240861c934e9bcfabd731bad
ms.contentlocale: zh-cn
ms.lasthandoff: 02/24/2017

---
# <a name="isupporterrorinfoimpl-class"></a>ISupportErrorInfoImpl 类
此类提供的默认实现[ISupportErrorInfo 接口](http://msdn.microsoft.com/en-us/42d33066-36b4-4a5b-aa5d-46682e560f32)和只有一个接口将生成错误对某个对象时，可以使用。  
  
> [!IMPORTANT]
>  该类及其成员无法在 [!INCLUDE[wrt](../../atl/reference/includes/wrt_md.md)]中执行的应用程序中使用。  
  
## <a name="syntax"></a>语法  
  
```
template<const IID* piid>  
class ATL_NO_VTABLE ISupportErrorInfoImpl 
   : public ISupportErrorInfo
```  
  
#### <a name="parameters"></a>参数  
 `piid`  
 一个指向支持的接口的 IID [IErrorInfo](http://msdn.microsoft.com/en-us/4dda6909-2d9a-4727-ae0c-b5f90dcfa447)。  
  
## <a name="members"></a>成员  
  
### <a name="public-methods"></a>公共方法  
  
|名称|说明|  
|----------|-----------------|  
|[ISupportErrorInfoImpl::InterfaceSupportsErrorInfo](#interfacesupportserrorinfo)|该值指示标识接口`riid`支持[IErrorInfo](http://msdn.microsoft.com/en-us/4dda6909-2d9a-4727-ae0c-b5f90dcfa447)接口。|  
  
## <a name="remarks"></a>备注  
 [ISupportErrorInfo 接口](http://msdn.microsoft.com/en-us/42d33066-36b4-4a5b-aa5d-46682e560f32)可确保错误信息，可以返回到客户端。 对象使用**IErrorInfo**必须实现**ISupportErrorInfo**。  
  
 类`ISupportErrorInfoImpl`提供的默认实现**ISupportErrorInfo**和只有一个接口将生成错误对某个对象时，可以使用。 例如:   
  
 [!code-cpp[NVC_ATL_COM&#48;](../../atl/codesnippet/cpp/isupporterrorinfoimpl-class_1.h)]  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `ISupportErrorInfo`  
  
 `ISupportErrorInfoImpl`  
  
## <a name="requirements"></a>要求  
 **标头︰** atlcom.h  
  
##  <a name="interfacesupportserrorinfo"></a>ISupportErrorInfoImpl::InterfaceSupportsErrorInfo  
 该值指示标识接口`riid`支持[IErrorInfo](http://msdn.microsoft.com/en-us/4dda6909-2d9a-4727-ae0c-b5f90dcfa447)接口。  
  
```
STDMETHOD(InterfaceSupportsErrorInfo)(REFIID riid);
```  
  
### <a name="remarks"></a>备注  
 请参阅[ISupportErrorInfo::InterfaceSupportsErrorInfo](http://msdn.microsoft.com/en-us/a54ef18d-ee3f-4483-ac4a-99d758f0960a)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="getsize"></a>IThreadPoolConfig::GetSize  
 调用此方法以获取在池中的线程数。  
  
```
STDMETHOD(GetSize)(int* pnNumThreads);
```  
  
### <a name="parameters"></a>参数  
 `pnNumThreads`  
 [out]接收的变量，在成功时的线程数在池中的地址。  
  
### <a name="return-value"></a>返回值  
 返回成功，则为 S_OK 或失败的错误 HRESULT。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATL_Utilities #&134;](../../atl/codesnippet/cpp/isupporterrorinfoimpl-class_2.cpp)]  
  
##  <a name="gettimeout"></a>IThreadPoolConfig::GetTimeout  
 调用此方法以获取以毫秒为单位，线程池可以关闭一个线程将等待的最长时间。  
  
```
STDMETHOD(GetTimeout)(DWORD* pdwMaxWait);
```  
  
### <a name="parameters"></a>参数  
 `pdwMaxWait`  
 [out]成功时，接收的最长时间以毫秒为单位，线程池将等到有线程，若要关闭的情况下，该变量的地址。  
  
### <a name="return-value"></a>返回值  
 返回成功，则为 S_OK 或失败的错误 HRESULT。  
  
### <a name="example"></a>示例  
 请参阅[IThreadPoolConfig::GetSize](#getsize)。  
  
##  <a name="setsize"></a>IThreadPoolConfig::SetSize  
 调用此方法以设置池中的线程数。  
  
```
STDMETHOD(SetSize)int nNumThreads);
```  
  
### <a name="parameters"></a>参数  
 `nNumThreads`  
 请求的池中的线程数。  
  
 如果`nNumThreads`是负数，其绝对值的数值将乘以要获取的线程总数的计算机中的处理器数。  
  
 如果`nNumThreads`为零， [ATLS_DEFAULT_THREADSPERPROC](http://msdn.microsoft.com/library/e0dcf107-72a9-4122-abb4-83c63aa7d571)将乘以要获取的线程总数的计算机中的处理器数。  
  
### <a name="return-value"></a>返回值  
 返回成功，则为 S_OK 或失败的错误 HRESULT。  
  
### <a name="example"></a>示例  
 请参阅[IThreadPoolConfig::GetSize](#getsize)。  
  
##  <a name="settimeout"></a>IThreadPoolConfig::SetTimeout  
 调用此方法以设置以毫秒为单位，线程池可以关闭一个线程将等待的最长时间。  
  
```
STDMETHOD(SetTimeout)(DWORD dwMaxWait);
```  
  
### <a name="parameters"></a>参数  
 `dwMaxWait`  
 以毫秒为单位，线程池可以关闭一个线程将等待请求的最大时间。  
  
### <a name="return-value"></a>返回值  
 返回成功，则为 S_OK 或失败的错误 HRESULT。  
  
### <a name="example"></a>示例  
 请参阅[IThreadPoolConfig::GetSize](#getsize)。  
  
## <a name="see-also"></a>另请参阅  
 [类概述](../../atl/atl-class-overview.md)

