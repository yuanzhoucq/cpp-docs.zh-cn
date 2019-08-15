---
title: CBindStatusCallback 类
ms.date: 11/04/2016
f1_keywords:
- CBindStatusCallback
- ATLCTL/ATL::CBindStatusCallback
- ATLCTL/ATL::CBindStatusCallback::CBindStatusCallback
- ATLCTL/ATL::CBindStatusCallback::Download
- ATLCTL/ATL::CBindStatusCallback::GetBindInfo
- ATLCTL/ATL::CBindStatusCallback::GetPriority
- ATLCTL/ATL::CBindStatusCallback::OnDataAvailable
- ATLCTL/ATL::CBindStatusCallback::OnLowResource
- ATLCTL/ATL::CBindStatusCallback::OnObjectAvailable
- ATLCTL/ATL::CBindStatusCallback::OnProgress
- ATLCTL/ATL::CBindStatusCallback::OnStartBinding
- ATLCTL/ATL::CBindStatusCallback::OnStopBinding
- ATLCTL/ATL::CBindStatusCallback::StartAsyncDownload
- ATLCTL/ATL::CBindStatusCallback::m_dwAvailableToRead
- ATLCTL/ATL::CBindStatusCallback::m_dwTotalRead
- ATLCTL/ATL::CBindStatusCallback::m_pFunc
- ATLCTL/ATL::CBindStatusCallback::m_pT
- ATLCTL/ATL::CBindStatusCallback::m_spBindCtx
- ATLCTL/ATL::CBindStatusCallback::m_spBinding
- ATLCTL/ATL::CBindStatusCallback::m_spMoniker
- ATLCTL/ATL::CBindStatusCallback::m_spStream
helpviewer_keywords:
- asynchronous data transfer [C++]
- data transfer [C++]
- data transfer [C++], asynchronous
- CBindStatusCallback class
ms.assetid: 0f5da276-6031-4418-b2a9-a4750ef29e77
ms.openlocfilehash: 89c65ff034cf7471c379b28116a741b62269a00c
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69497605"
---
# <a name="cbindstatuscallback-class"></a>CBindStatusCallback 类

此类实现 `IBindStatusCallback` 接口。

> [!IMPORTANT]
>  此类及其成员不能用于在 Windows 运行时中执行的应用程序。

## <a name="syntax"></a>语法

```
template <class T,
    int nBindFlags = BINDF_ASYNCHRONOUS | BINDF_ASYNCSTORAGE | BINDF_GETNEWESTVERSION | BINDF_NOWRITECACHE>
class ATL_NO_VTABLE CBindStatusCallback : public CComObjectRootEx <T ::_ThreadModel::ThreadModelNoCS>,
    public IBindStatusCallbackImpl<T>
```

#### <a name="parameters"></a>参数

*T*<br/>
您的类包含将在接收数据时调用的函数。

*nBindFlags*<br/>
指定[GetBindInfo](#getbindinfo)返回的绑定标志。 默认实现将绑定设置为异步, 检索数据/对象的最新版本, 并且不会将检索到的数据存储在磁盘缓存中。

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[CBindStatusCallback::CBindStatusCallback](#cbindstatuscallback)|构造函数。|
|[CBindStatusCallback:: ~ CBindStatusCallback](#dtor)|析构函数。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CBindStatusCallback::Download](#download)|用于启动下载过程、创建`CBindStatusCallback`对象和调用`StartAsyncDownload`的静态方法。|
|[CBindStatusCallback::GetBindInfo](#getbindinfo)|由异步名字对象调用以请求要创建的绑定类型的信息。|
|[CBindStatusCallback::GetPriority](#getpriority)|由异步名字对象调用以获取绑定操作的优先级。 ATL 实现返回`E_NOTIMPL`。|
|[CBindStatusCallback::OnDataAvailable](#ondataavailable)|调用以在应用程序可用时向其提供数据。 读取数据, 然后调用传递给它的函数以使用数据。|
|[CBindStatusCallback::OnLowResource](#onlowresource)|当资源不足时调用。 ATL 实现返回 S_OK。|
|[CBindStatusCallback::OnObjectAvailable](#onobjectavailable)|由异步名字对象调用, 以将对象接口指针传递到应用程序。 ATL 实现返回 S_OK。|
|[CBindStatusCallback::OnProgress](#onprogress)|调用以指示数据下载进程的进度。 ATL 实现返回 S_OK。|
|[CBindStatusCallback::OnStartBinding](#onstartbinding)|当绑定启动时调用。|
|[CBindStatusCallback::OnStopBinding](#onstopbinding)|当异步数据传输停止时调用。|
|[CBindStatusCallback::StartAsyncDownload](#startasyncdownload)|初始化可用字节数和读取到零的字节数, 从 URL 创建推送类型流对象, 并在每`OnDataAvailable`次数据可用时调用。|

### <a name="public-data-members"></a>公共数据成员

|名称|描述|
|----------|-----------------|
|[CBindStatusCallback::m_dwAvailableToRead](#m_dwavailabletoread)|可读取的字节数。|
|[CBindStatusCallback::m_dwTotalRead](#m_dwtotalread)|读取的总字节数。|
|[CBindStatusCallback::m_pFunc](#m_pfunc)|指向在数据可用时调用的函数的指针。|
|[CBindStatusCallback::m_pT](#m_pt)|指向请求异步数据传输的对象的指针。|
|[CBindStatusCallback::m_spBindCtx](#m_spbindctx)|指向当前绑定操作的[IBindCtx](/windows/win32/api/objidl/nn-objidl-ibindctx)接口的指针。|
|[CBindStatusCallback::m_spBinding](#m_spbinding)|指向当前绑定`IBinding`操作的接口的指针。|
|[CBindStatusCallback::m_spMoniker](#m_spmoniker)|指向要使用的 URL 的[IMoniker](/windows/win32/api/objidl/nn-objidl-imoniker)接口的指针。|
|[CBindStatusCallback::m_spStream](#m_spstream)|指向数据传输的[IStream](/windows/win32/api/objidl/nn-objidl-istream)接口的指针。|

## <a name="remarks"></a>备注

`CBindStatusCallback` 类实现 `IBindStatusCallback` 接口。 `IBindStatusCallback`必须由您的应用程序实现, 以便它可以从异步数据传输接收通知。 系统提供的异步名字对象使用`IBindStatusCallback`方法来发送和接收与对象之间的异步数据传输的相关信息。

通常, `CBindStatusCallback`对象与特定的绑定操作相关联。 例如, 在[异步](../../overview/visual-cpp-samples.md)示例中, 在设置 URL 属性时, 它将`CBindStatusCallback` `Download`在对的调用中创建对象:

[!code-cpp[NVC_ATL_Windowing#86](../../atl/codesnippet/cpp/cbindstatuscallback-class_1.h)]

当应用程序包含数据时, `OnData`异步名字对象使用回调函数调用它。 异步名字对象由系统提供。

## <a name="inheritance-hierarchy"></a>继承层次结构

`CComObjectRootBase`

`IBindStatusCallback`

[CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)

`CBindStatusCallback`

## <a name="requirements"></a>要求

**标头:** atlctl

##  <a name="cbindstatuscallback"></a>CBindStatusCallback::CBindStatusCallback

构造函数。

```
CBindStatusCallback();
```

### <a name="remarks"></a>备注

创建一个对象, 用于接收有关异步数据传输的通知。 通常, 会为每个绑定操作创建一个对象。

构造函数还将[m_pT](#m_pt)和[M_PFUNC](#m_pfunc)初始化为 NULL。

##  <a name="dtor"></a>CBindStatusCallback:: ~ CBindStatusCallback

析构函数。

```
~CBindStatusCallback();
```

### <a name="remarks"></a>备注

释放所有已分配的资源。

##  <a name="download"></a>CBindStatusCallback::D o)

创建一个`CBindStatusCallback`对象, 并`StartAsyncDownload`调用以从指定的 URL 异步下载数据。

```
static HRESULT Download(
    T* pT,
    ATL_PDATAAVAILABLE pFunc,
    BSTR bstrURL,
    IUnknown* pUnkContainer = NULL,
    BOOL bRelative = FALSE);
```

### <a name="parameters"></a>参数

*pT*<br/>
中指向请求异步数据传输的对象的指针。 `CBindStatusCallback`对象在此对象的类上是模板化的。

*pFunc*<br/>
中指向函数的指针, 该函数接收所读取的数据。 函数是对象的类型`T`的类的成员。 有关语法和示例, 请参阅[StartAsyncDownload](#startasyncdownload) 。

*bstrURL*<br/>
中要从中获取数据的 URL。 可以是任何有效的 URL 或文件名。 不能为 NULL。 例如:

`CComBSTR mybstr =_T("http://somesite/data.htm")`

*pUnkContainer*<br/>
中`IUnknown`容器的。 默认值为 NULL。

*bRelative*<br/>
中指示 URL 是相对路径还是绝对 URL 的标志。 默认值为 FALSE, 表示 URL 是绝对的。

### <a name="return-value"></a>返回值

标准的 HRESULT 值之一。

### <a name="remarks"></a>备注

每次有数据可用时, 都会通过`OnDataAvailable`发送到对象。 `OnDataAvailable`读取数据并调用*pFunc*所指向的函数 (例如, 存储数据或将其打印到屏幕)。

##  <a name="getbindinfo"></a>  CBindStatusCallback::GetBindInfo

调用以告知名字对象如何绑定。

```
STDMETHOD(GetBindInfo)(
    DWORD* pgrfBSCF,
    BINDINFO* pbindinfo);
```

### <a name="parameters"></a>参数

*pgrfBSCF*<br/>
弄指向 BINDF 枚举值的指针, 指示绑定操作应如何发生。 默认情况下, 使用以下枚举值设置:

BINDF_ASYNCHRONOUS 异步下载。

数据`OnDataAvailable`不可用时, BINDF_ASYNCSTORAGE 将返回 E_PENDING, 而不会在数据可用之前进行阻止。

BINDF_GETNEWESTVERSION 绑定操作应检索最新版本的数据。

BINDF_NOWRITECACHE 绑定操作不应将检索到的数据存储在磁盘缓存中。

*pbindinfo*<br/>
[in, out]指向`BINDINFO`结构的指针, 该结构提供有关对象如何进行绑定的详细信息。

### <a name="return-value"></a>返回值

标准的 HRESULT 值之一。

### <a name="remarks"></a>备注

默认实现将绑定设置为异步, 并使用数据推送模型。 在数据推送模型中, 名字对象驱动异步绑定操作, 并在有新数据可用时持续通知客户端。

##  <a name="getpriority"></a>CBindStatusCallback:: GetPriority

由异步名字对象调用以获取绑定操作的优先级。

```
STDMETHOD(GetPriority)(LONG* pnPriority);
```

### <a name="parameters"></a>参数

*pnPriority*<br/>
弄成功时接收优先级的**长**变量的地址。

### <a name="return-value"></a>返回值

返回 E_NOTIMPL。

##  <a name="m_dwavailabletoread"></a>  CBindStatusCallback::m_dwAvailableToRead

可用于存储可读取的字节数。

```
DWORD m_dwAvailableToRead;
```

### <a name="remarks"></a>备注

在中`StartAsyncDownload`初始化为零。

##  <a name="m_dwtotalread"></a>  CBindStatusCallback::m_dwTotalRead

异步数据传输中读取的字节的累积总数。

```
DWORD m_dwTotalRead;
```

### <a name="remarks"></a>备注

每次`OnDataAvailable`由实际读取的字节数调用时递增。 在中`StartAsyncDownload`初始化为零。

##  <a name="m_pfunc"></a>CBindStatusCallback::m_pFunc

指向`m_pFunc`的函数在读取可用数据 ( `OnDataAvailable`例如存储数据或将其打印到屏幕) 后由调用。

```
ATL_PDATAAVAILABLE m_pFunc;
```

### <a name="remarks"></a>备注

指向的`m_pFunc`函数是对象类的成员, 并且具有以下语法:

```
void Function_Name(
   CBindStatusCallback<T>* pbsc,
   BYTE* pBytes,
   DWORD dwSize
   );
```

##  <a name="m_pt"></a>  CBindStatusCallback::m_pT

指向请求异步数据传输的对象的指针。

```
T* m_pT;
```

### <a name="remarks"></a>备注

`CBindStatusCallback`对象在此对象的类上是模板化的。

##  <a name="m_spbindctx"></a>  CBindStatusCallback::m_spBindCtx

指向[IBindCtx](/windows/win32/api/objidl/nn-objidl-ibindctx)接口的指针, 该接口提供对绑定上下文 (存储有关特定名字对象绑定操作的信息的对象) 的访问。

```
CComPtr<IBindCtx> m_spBindCtx;
```

### <a name="remarks"></a>备注

在中`StartAsyncDownload`进行了初始化。

##  <a name="m_spbinding"></a>CBindStatusCallback::m_spBinding

指向当前绑定操作`IBinding`的接口的指针。

```
CComPtr<IBinding> m_spBinding;
```

### <a name="remarks"></a>备注

已在中初始化`OnStopBinding`并在中发布。`OnStartBinding`

##  <a name="m_spmoniker"></a>  CBindStatusCallback::m_spMoniker

指向要使用的 URL 的[IMoniker](/windows/win32/api/objidl/nn-objidl-imoniker)接口的指针。

```
CComPtr<IMoniker> m_spMoniker;
```

### <a name="remarks"></a>备注

在中`StartAsyncDownload`进行了初始化。

##  <a name="m_spstream"></a>  CBindStatusCallback::m_spStream

指向当前绑定操作的[IStream](/windows/win32/api/objidl/nn-objidl-istream)接口的指针。

```
CComPtr<IStream> m_spStream;
```

### <a name="remarks"></a>备注

当 BCSF `OnDataAvailable`标志为`STGMEDIUM` BCSF_FIRSTDATANOTIFICATION 并在 BCSF 标志为 BCSF_LASTDATANOTIFICATION 时发布时, 从结构中进行了初始化。

##  <a name="ondataavailable"></a>CBindStatusCallback:: OnDataAvailable

系统提供的异步名字对象调用`OnDataAvailable` , 在对象可用时向其提供数据。

```
STDMETHOD(
    OnDataAvailable)(DWORD grfBSCF,
    DWORD dwSize,
    FORMATETC* /* pformatetc */,
    STGMEDIUM* pstgmed);
```

### <a name="parameters"></a>参数

*grfBSCF*<br/>
中BSCF 枚举值。 以下一项或多项操作:BSCF_FIRSTDATANOTIFICATION、BSCF_INTERMEDIARYDATANOTIFICATION 或 BSCF_LASTDATANOTIFICATION。

*dwSize*<br/>
中自绑定开始以来可用数据的累计量 (以字节为单位)。 可以为零, 表示数据量不相关或没有特定的可用量。

*pformatetc*<br/>
中指向[FORMATETC](/windows/win32/com/the-formatetc-structure)结构的指针, 该结构包含可用数据的格式。 如果没有格式, 则可以是 CF_NULL。

*pstgmed*<br/>
中指向[STGMEDIUM](/windows/win32/com/the-stgmedium-structure)结构的指针, 该结构包含当前可用的实际数据。

### <a name="return-value"></a>返回值

标准的 HRESULT 值之一。

### <a name="remarks"></a>备注

`OnDataAvailable`读取数据, 然后调用对象的类的方法 (例如, 存储数据或将数据打印到屏幕)。 有关详细信息, 请参阅[CBindStatusCallback:: StartAsyncDownload](#startasyncdownload) 。

##  <a name="onlowresource"></a>CBindStatusCallback::OnLowResource

当资源不足时调用。

```
STDMETHOD(OnLowResource)(DWORD /* dwReserved */);
```

### <a name="parameters"></a>参数

*dwReserved*<br/>
保留。

### <a name="return-value"></a>返回值

返回 S_OK。

##  <a name="onobjectavailable"></a>  CBindStatusCallback::OnObjectAvailable

由异步名字对象调用, 以将对象接口指针传递到应用程序。

```
STDMETHOD(OnObjectAvailable)(REFID /* riid */, IUnknown* /* punk */);
```

### <a name="parameters"></a>参数

*riid*<br/>
请求的接口的接口标识符。 未使用。

*punk*<br/>
IUnknown 接口的地址。 未使用。

### <a name="return-value"></a>返回值

返回 S_OK。

##  <a name="onprogress"></a>  CBindStatusCallback::OnProgress

调用以指示数据下载进程的进度。

```
STDMETHOD(OnProgress)(
    ULONG /* ulProgress */,
    ULONG /* ulProgressMax */,
    ULONG /* ulStatusCode */,
    LPCWSTRONG /* szStatusText */);
```

### <a name="parameters"></a>参数

*ulProgress*<br/>
无符号长整数。 未使用。

*ulProgressMax*<br/>
未使用无符号长整数。

*ulStatusCode*<br/>
无符号长整数。 未使用。

*szStatusText*<br/>
字符串值的地址。 未使用。

### <a name="return-value"></a>返回值

返回 S_OK。

##  <a name="onstartbinding"></a>CBindStatusCallback::OnStartBinding

将数据成员[m_spBinding](#m_spbinding)设置为`IBinding` *pBinding*中的指针。

```
STDMETHOD(OnStartBinding)(DWORD /* dwReserved */, IBinding* pBinding);
```

### <a name="parameters"></a>参数

*dwReserved*<br/>
留待将来使用。

*pBinding*<br/>
中当前绑定操作的 IBinding 接口的地址。 此值不能为 NULL。 客户端应对此指针调用 AddRef, 以保留对绑定对象的引用。

##  <a name="onstopbinding"></a>CBindStatusCallback::OnStopBinding

释放数据`IBinding`成员[m_spBinding](#m_spbinding)中的指针。

```
STDMETHOD(OnStopBinding)(HRESULT hresult, LPCWSTR /* szError */);
```

### <a name="parameters"></a>参数

*hresult*<br/>
从绑定操作返回的状态代码。

*szError*<br/>
字符串值的地址。 未使用。

### <a name="remarks"></a>备注

由系统提供的异步名字对象调用, 指示绑定操作结束。

##  <a name="startasyncdownload"></a>CBindStatusCallback::StartAsyncDownload

开始从指定的 URL 异步下载数据。

```
HRESULT StartAsyncDownload(
    T* pT,
    ATL_PDATAAVAILABLE pFunc,
    BSTR bstrURL,
    IUnknown* pUnkContainer = NULL,
    BOOL bRelative = FALSE);
```

### <a name="parameters"></a>参数

*pT*<br/>
中指向请求异步数据传输的对象的指针。 `CBindStatusCallback`对象在此对象的类上是模板化的。

*pFunc*<br/>
中指向函数的指针, 该函数接收所读取的数据。 函数是对象的类型`T`的类的成员。 有关语法和示例, 请参阅**备注**。

*bstrURL*<br/>
中要从中获取数据的 URL。 可以是任何有效的 URL 或文件名。 不能为 NULL。 例如:

`CComBSTR mybstr =_T("http://somesite/data.htm")`

*pUnkContainer*<br/>
中`IUnknown`容器的。 默认值为 NULL。

*bRelative*<br/>
中指示 URL 是相对路径还是绝对 URL 的标志。 默认值为 FALSE, 表示 URL 是绝对的。

### <a name="return-value"></a>返回值

标准的 HRESULT 值之一。

### <a name="remarks"></a>备注

每次有数据可用时, 都会通过`OnDataAvailable`发送到对象。 `OnDataAvailable`读取数据并调用*pFunc*所指向的函数 (例如, 存储数据或将其打印到屏幕)。

*PFunc*指向的函数是对象类的成员, 并且具有以下语法:

```
void Function_Name(
    CBindStatusCallback<T>* pbsc,
    BYTE* pBytes,
    DWORD dwSize);
```

在下面的示例中 (取自[ASYNC](../../overview/visual-cpp-samples.md)示例), 函数`OnData`将接收的数据写入文本框。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_Windowing#87](../../atl/codesnippet/cpp/cbindstatuscallback-class_2.h)]

## <a name="see-also"></a>请参阅

[类概述](../../atl/atl-class-overview.md)
