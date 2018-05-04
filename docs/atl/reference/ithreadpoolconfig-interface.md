---
title: IThreadPoolConfig 接口 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- IThreadPoolConfig
- ATLUTIL/ATL::IThreadPoolConfig
- ATLUTIL/ATL::GetSize
- ATLUTIL/ATL::GetTimeout
- ATLUTIL/ATL::SetSize
- ATLUTIL/ATL::SetTimeout
dev_langs:
- C++
helpviewer_keywords:
- IThreadPoolConfig interface
ms.assetid: 69e642bf-6925-46e6-9a37-cce52231b1cc
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 237671ce971d54209f3889fd93396fb4e0a42fee
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="ithreadpoolconfig-interface"></a>IThreadPoolConfig 接口
此接口提供用于配置线程池的方法。  
  
> [!IMPORTANT]
>  此类及其成员无法在 Windows 运行时中执行的应用中使用。  
  
## <a name="syntax"></a>语法  
  
```
__interface
    __declspec(uuid("B1F64757-6E88-4fa2-8886-7848B0D7E660")) IThreadPoolConfig : public IUnknown
```  
  
## <a name="members"></a>成员  
  
### <a name="methods"></a>方法  
  
|||  
|-|-|  
|[GetSize](#getsize)|调用此方法以获取池中的线程数。|  
|[GetTimeout](#gettimeout)|调用此方法以获取的最长时间以毫秒为单位，线程池将等待线程关闭。|  
|[SetSize](#setsize)|调用此方法以设置池中的线程数。|  
|[SetTimeout](#settimeout)|调用此方法以设置的最长时间以毫秒为单位，线程池将等待线程关闭。|  
  
## <a name="remarks"></a>备注  
 此接口由实现[CThreadPool](../../atl/reference/cthreadpool-class.md)。  
  
## <a name="requirements"></a>要求  
 **标头：** atlutil.h  
  
##  <a name="getsize"></a>  IThreadPoolConfig::GetSize  
 调用此方法以获取池中的线程数。  
  
```
STDMETHOD(GetSize)(int* pnNumThreads);
```  
  
### <a name="parameters"></a>参数  
 `pnNumThreads`  
 [out]接收的变量，在成功时的线程数在池中的地址。  
  
### <a name="return-value"></a>返回值  
 返回成功，则为 S_OK 或失败的错误 HRESULT。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATL_Utilities#134](../../atl/codesnippet/cpp/ithreadpoolconfig-interface_1.cpp)]  
  
##  <a name="gettimeout"></a>  IThreadPoolConfig::GetTimeout  
 调用此方法以获取的最长时间以毫秒为单位，线程池将等待线程关闭。  
  
```
STDMETHOD(GetTimeout)(DWORD* pdwMaxWait);
```  
  
### <a name="parameters"></a>参数  
 `pdwMaxWait`  
 [out]变量的成功时，接收的最长时间以毫秒为单位，线程池将等待线程关闭的地址。  
  
### <a name="return-value"></a>返回值  
 返回成功，则为 S_OK 或失败的错误 HRESULT。  
  
### <a name="example"></a>示例  
 请参阅[IThreadPoolConfig::GetSize](#getsize)。  
  
##  <a name="setsize"></a>  IThreadPoolConfig::SetSize  
 调用此方法以设置池中的线程数。  
  
```
STDMETHOD(SetSize)int nNumThreads);
```  
  
### <a name="parameters"></a>参数  
 `nNumThreads`  
 请求的池中的线程数。  
  
 如果`nNumThreads`为负，其绝对值的数值将乘以要获取的线程总数的机中的处理器数。  
  
 如果`nNumThreads`为零， [ATLS_DEFAULT_THREADSPERPROC](http://msdn.microsoft.com/library/e0dcf107-72a9-4122-abb4-83c63aa7d571)将乘以要获取的线程总数的机中的处理器数。  
  
### <a name="return-value"></a>返回值  
 返回成功，则为 S_OK 或失败的错误 HRESULT。  
  
### <a name="example"></a>示例  
 请参阅[IThreadPoolConfig::GetSize](#getsize)。  
  
##  <a name="settimeout"></a>  IThreadPoolConfig::SetTimeout  
 调用此方法以设置的最长时间以毫秒为单位，线程池将等待线程关闭。  
  
```
STDMETHOD(SetTimeout)(DWORD dwMaxWait);
```  
  
### <a name="parameters"></a>参数  
 `dwMaxWait`  
 以毫秒为单位，线程池将等待线程关闭请求的最大时间。  
  
### <a name="return-value"></a>返回值  
 返回成功，则为 S_OK 或失败的错误 HRESULT。  
  
### <a name="example"></a>示例  
 请参阅[IThreadPoolConfig::GetSize](#getsize)。  
  
## <a name="see-also"></a>请参阅  
 [类](../../atl/reference/atl-classes.md)   
 [CThreadPool 类](../../atl/reference/cthreadpool-class.md)
