---
title: IThreadPoolConfig 接口 |Microsoft Docs
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
ms.openlocfilehash: 156a0a827a67e80369ca8b834b62bcf0e431ab14
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46076341"
---
# <a name="ithreadpoolconfig-interface"></a>IThreadPoolConfig 接口

此接口提供用于配置的线程池的方法。

> [!IMPORTANT]
>  不能在 Windows 运行时中执行的应用程序中使用此类和其成员。

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
|[GetTimeout](#gettimeout)|调用此方法以获取最长时间以毫秒为单位，线程池将等待一个线程来关闭的情况下。|
|[SetSize](#setsize)|调用此方法以设置在池中的线程数。|
|[SetTimeout](#settimeout)|调用此方法，以毫秒为单位，线程池将等待一个线程来关闭的情况下设置最长的时间。|

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

*pnNumThreads*<br/>
[out]，如果成功，接收变量的线程数在池中的地址。

### <a name="return-value"></a>返回值

返回成功，则为 S_OK 或失败时的错误 HRESULT。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_Utilities#134](../../atl/codesnippet/cpp/ithreadpoolconfig-interface_1.cpp)]

##  <a name="gettimeout"></a>  IThreadPoolConfig::GetTimeout

调用此方法以获取最长时间以毫秒为单位，线程池将等待一个线程来关闭的情况下。

```
STDMETHOD(GetTimeout)(DWORD* pdwMaxWait);
```

### <a name="parameters"></a>参数

*pdwMaxWait*<br/>
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

*nNumThreads*<br/>
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

*dwMaxWait*<br/>
以毫秒为单位，线程池将等待一个线程来关闭请求的最大时间。

### <a name="return-value"></a>返回值

返回成功，则为 S_OK 或失败时的错误 HRESULT。

### <a name="example"></a>示例

请参阅[IThreadPoolConfig::GetSize](#getsize)。

## <a name="see-also"></a>请参阅

[类](../../atl/reference/atl-classes.md)<br/>
[CThreadPool 类](../../atl/reference/cthreadpool-class.md)
