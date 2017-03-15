---
title: "IThreadPoolConfig 界面 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- IThreadPoolConfig
- ATL::IThreadPoolConfig
- ATL.IThreadPoolConfig
dev_langs:
- C++
helpviewer_keywords:
- IThreadPoolConfig interface
ms.assetid: 69e642bf-6925-46e6-9a37-cce52231b1cc
caps.latest.revision: 24
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
translationtype: Machine Translation
ms.sourcegitcommit: 604a4bf49490ad2599c857eb3afd527d67e1e25b
ms.openlocfilehash: e10885373442890978feff42cda99309692a21d0
ms.lasthandoff: 02/24/2017

---
# <a name="ithreadpoolconfig-interface"></a>IThreadPoolConfig 接口
此接口提供用于配置一个线程池的方法。  
  
> [!IMPORTANT]
>  该类及其成员无法在 [!INCLUDE[wrt](../../atl/reference/includes/wrt_md.md)]中执行的应用程序中使用。  
  
## <a name="syntax"></a>语法  
  
```
__interface
    __declspec(uuid("B1F64757-6E88-4fa2-8886-7848B0D7E660")) IThreadPoolConfig : public IUnknown
```  
  
## <a name="members"></a>成员  
  
### <a name="methods"></a>方法  
  
|||  
|-|-|  
|[GetSize](#getsize)|调用此方法以获取在池中的线程数。|  
|[GetTimeout](#gettimeout)|调用此方法以获取以毫秒为单位，线程池可以关闭一个线程将等待的最长时间。|  
|[SetSize](#setsize)|调用此方法以设置池中的线程数。|  
|[SetTimeout](#settimeout)|调用此方法以设置以毫秒为单位，线程池可以关闭一个线程将等待的最长时间。|  
  
## <a name="remarks"></a>备注  
 此接口由实现[CThreadPool](../../atl/reference/cthreadpool-class.md)。  
  
## <a name="requirements"></a>要求  
 **标头︰** atlutil.h  
  
##  <a name="a-namegetsizea--ithreadpoolconfiggetsize"></a><a name="getsize"></a>IThreadPoolConfig::GetSize  
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
 [!code-cpp[NVC_ATL_Utilities #&134;](../../atl/codesnippet/cpp/ithreadpoolconfig-interface_1.cpp)]  
  
##  <a name="a-namegettimeouta--ithreadpoolconfiggettimeout"></a><a name="gettimeout"></a>IThreadPoolConfig::GetTimeout  
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
  
##  <a name="a-namesetsizea--ithreadpoolconfigsetsize"></a><a name="setsize"></a>IThreadPoolConfig::SetSize  
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
  
##  <a name="a-namesettimeouta--ithreadpoolconfigsettimeout"></a><a name="settimeout"></a>IThreadPoolConfig::SetTimeout  
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
 [类](../../atl/reference/atl-classes.md)   
 [CThreadPool 类](../../atl/reference/cthreadpool-class.md)

