---
title: IThreadPoolConfig 接口
ms.date: 11/04/2016
f1_keywords:
- IThreadPoolConfig
- ATLUTIL/ATL::IThreadPoolConfig
- ATLUTIL/ATL::GetSize
- ATLUTIL/ATL::GetTimeout
- ATLUTIL/ATL::SetSize
- ATLUTIL/ATL::SetTimeout
helpviewer_keywords:
- IThreadPoolConfig interface
ms.assetid: 69e642bf-6925-46e6-9a37-cce52231b1cc
ms.openlocfilehash: e4b90534fa89ef2aeffe4cd682d92efc16452487
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81326355"
---
# <a name="ithreadpoolconfig-interface"></a>IThreadPoolConfig 接口

此接口提供了配置线程池的方法。

> [!IMPORTANT]
> 此类及其成员不能在 Windows 运行时中执行的应用程序中使用。

## <a name="syntax"></a>语法

```
__interface
    __declspec(uuid("B1F64757-6E88-4fa2-8886-7848B0D7E660")) IThreadPoolConfig : public IUnknown
```

## <a name="members"></a>成员

### <a name="methods"></a>方法

|||
|-|-|
|[GetSize](#getsize)|调用此方法获取池中的线程数。|
|[获取超时](#gettimeout)|调用此方法，获取线程池将等待线程关闭的最大时间（以毫秒为单位）。|
|[设置大小](#setsize)|调用此方法以设置池中的线程数。|
|[设置超时](#settimeout)|调用此方法以设置线程池将等待线程关闭的最大时间（以毫秒为单位）。|

## <a name="remarks"></a>备注

此接口由[CThreadPool](../../atl/reference/cthreadpool-class.md)实现。

## <a name="requirements"></a>要求

**标题：** atlutil.h

## <a name="ithreadpoolconfiggetsize"></a><a name="getsize"></a>IThreadPool 配置：：获取 Size

调用此方法获取池中的线程数。

```
STDMETHOD(GetSize)(int* pnNumThreads);
```

### <a name="parameters"></a>参数

*pnNumThreads*<br/>
[出]变量的地址，在成功时，接收池中的线程数。

### <a name="return-value"></a>返回值

返回成功S_OK，或失败时返回错误 HRESULT。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_Utilities#134](../../atl/codesnippet/cpp/ithreadpoolconfig-interface_1.cpp)]

## <a name="ithreadpoolconfiggettimeout"></a><a name="gettimeout"></a>IThreadPool 配置：：获取超时

调用此方法，获取线程池将等待线程关闭的最大时间（以毫秒为单位）。

```
STDMETHOD(GetTimeout)(DWORD* pdwMaxWait);
```

### <a name="parameters"></a>参数

*pdwMaxWait*<br/>
[出]变量的地址，在成功时，接收线程池将等待线程关闭的最大时间（以毫秒为单位）。

### <a name="return-value"></a>返回值

返回成功S_OK，或失败时返回错误 HRESULT。

### <a name="example"></a>示例

请参阅[IThreadPool 配置：：获取 Size](#getsize)。

## <a name="ithreadpoolconfigsetsize"></a><a name="setsize"></a>IThreadPool 配置：：设置大小

调用此方法以设置池中的线程数。

```
STDMETHOD(SetSize)int nNumThreads);
```

### <a name="parameters"></a>参数

*nNumThreads*<br/>
池中请求的线程数。

如果*nNumThreads*为负值，则其绝对值将乘以计算机中的处理器数，以获得线程总数。

如果*nNumThreads*为零，ATLS_DEFAULT_THREADSPERPROC将乘以计算机中的处理器数，以获得线程总数。

### <a name="return-value"></a>返回值

返回成功S_OK，或失败时返回错误 HRESULT。

### <a name="example"></a>示例

请参阅[IThreadPool 配置：：获取 Size](#getsize)。

## <a name="ithreadpoolconfigsettimeout"></a><a name="settimeout"></a>IThreadPool 配置：：设置超时

调用此方法以设置线程池将等待线程关闭的最大时间（以毫秒为单位）。

```
STDMETHOD(SetTimeout)(DWORD dwMaxWait);
```

### <a name="parameters"></a>参数

*dwMaxWait*<br/>
请求的最大时间（以毫秒为单位）用于线程池将等待线程关闭。

### <a name="return-value"></a>返回值

返回成功S_OK，或失败时返回错误 HRESULT。

### <a name="example"></a>示例

请参阅[IThreadPool 配置：：获取 Size](#getsize)。

## <a name="see-also"></a>另请参阅

[类](../../atl/reference/atl-classes.md)<br/>
[CThreadPool 类](../../atl/reference/cthreadpool-class.md)
