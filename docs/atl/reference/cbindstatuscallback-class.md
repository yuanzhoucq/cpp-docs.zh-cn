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
ms.openlocfilehash: 0ae7f4fcdba18be84d99140e395b6f2ac3db792a
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/22/2020
ms.locfileid: "81748208"
---
# <a name="cbindstatuscallback-class"></a>CBindStatusCallback 类

此类实现 `IBindStatusCallback` 接口。

> [!IMPORTANT]
> 此类及其成员不能在 Windows 运行时中执行的应用程序中使用。

## <a name="syntax"></a>语法

```
template <class T,
    int nBindFlags = BINDF_ASYNCHRONOUS | BINDF_ASYNCSTORAGE | BINDF_GETNEWESTVERSION | BINDF_NOWRITECACHE>
class ATL_NO_VTABLE CBindStatusCallback : public CComObjectRootEx <T ::_ThreadModel::ThreadModelNoCS>,
    public IBindStatusCallbackImpl<T>
```

#### <a name="parameters"></a>参数

*T*<br/>
包含将在接收数据时调用的函数的类。

*n 绑定标志*<br/>
指定[GetBindInfo](#getbindinfo)返回的绑定标志。 默认实现将绑定设置为异步，检索数据/对象的最新版本，并且不将检索到的数据存储在磁盘缓存中。

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[C绑定状态回调：：C绑定状态回调](#cbindstatuscallback)|构造函数。|
|[C绑定状态回调：：*C绑定状态回调](#dtor)|析构函数。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CBind状态回拨：:D自己的负载](#download)|启动下载过程、创建`CBindStatusCallback`对象和调用`StartAsyncDownload`的静态方法。|
|[CBind状态回拨：：获取绑定信息](#getbindinfo)|由异步名字对象调用，以请求有关要创建的绑定类型的信息。|
|[CBind状态回拨：：获取优先级](#getpriority)|由异步名字对象调用，以获得绑定操作的优先级。 ATL 实现返回`E_NOTIMPL`。|
|[CBind状态回拨：：OnData 可用](#ondataavailable)|调用以在应用程序可用时向应用程序提供数据。 读取数据，然后调用传递给它的函数以使用数据。|
|[CBind状态回调：：在低资源](#onlowresource)|在资源不足时调用。 ATL 实现返回S_OK。|
|[CBind状态回调：：打开对象可用](#onobjectavailable)|由异步名字对象调用，将对象接口指针传递给应用程序。 ATL 实现返回S_OK。|
|[CBind状态回拨：：在进度上](#onprogress)|调用 以指示数据下载过程的进度。 ATL 实现返回S_OK。|
|[CBind状态回调：：打开绑定](#onstartbinding)|启动绑定时调用。|
|[CBind状态回调：：打开绑定](#onstopbinding)|在异步数据传输停止时调用。|
|[CBind状态回拨：：开始同步下载](#startasyncdownload)|初始化可用字节和读取到零的字节，从 URL 创建推送类型的流对象，并在每次数据可用时调用`OnDataAvailable`。|

### <a name="public-data-members"></a>公共数据成员

|名称|说明|
|----------|-----------------|
|[CBind状态回拨：：m_dwAvailableToRead](#m_dwavailabletoread)|可供读取的字节数。|
|[CBind状态回拨：：m_dwTotalRead](#m_dwtotalread)|读取的字节总数。|
|[CBind状态回拨：：m_pFunc](#m_pfunc)|指向数据可用时调用的函数的指针。|
|[CBind状态回拨：：m_pT](#m_pt)|指向请求异步数据传输的对象的指针。|
|[CBind状态回拨：：m_spBindCtx](#m_spbindctx)|指向当前绑定操作的[IBindCtx](/windows/win32/api/objidl/nn-objidl-ibindctx)接口。|
|[CBind状态回拨：：m_spBinding](#m_spbinding)|指向当前绑定`IBinding`操作的接口的指针。|
|[CBind状态回拨：：m_spMoniker](#m_spmoniker)|指向[IMoniker](/windows/win32/api/objidl/nn-objidl-imoniker)接口的 URL。|
|[CBind状态回拨：：m_spStream](#m_spstream)|指向数据传输的[IStream](/windows/win32/api/objidl/nn-objidl-istream)接口。|

## <a name="remarks"></a>备注

`CBindStatusCallback` 类实现 `IBindStatusCallback` 接口。 `IBindStatusCallback`必须由应用程序实现，以便它可以从异步数据传输接收通知。 系统提供的异步名字项使用`IBindStatusCallback`方法发送和接收有关对象和对象中的异步数据传输的信息。

通常，该`CBindStatusCallback`对象与特定的绑定操作相关联。 例如，在[ASYNC](../../overview/visual-cpp-samples.md)示例中，当您设置 URL 属性时，它会在`CBindStatusCallback`调用 中创建一`Download`个对象，

[!code-cpp[NVC_ATL_Windowing#86](../../atl/codesnippet/cpp/cbindstatuscallback-class_1.h)]

异步名字对象使用回调函数`OnData`在应用程序具有数据时调用应用程序。 异步名字由系统提供。

## <a name="inheritance-hierarchy"></a>继承层次结构

`CComObjectRootBase`

`IBindStatusCallback`

[CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)

`CBindStatusCallback`

## <a name="requirements"></a>要求

**标题：** atlctl.h

## <a name="cbindstatuscallbackcbindstatuscallback"></a><a name="cbindstatuscallback"></a>C绑定状态回调：：C绑定状态回调

构造函数。

```
CBindStatusCallback();
```

### <a name="remarks"></a>备注

创建一个对象来接收有关异步数据传输的通知。 通常，为每个绑定操作创建一个对象。

构造函数还会初始化[m_pT，](#m_pt)并将[m_pFunc](#m_pfunc)到 NULL。

## <a name="cbindstatuscallbackcbindstatuscallback"></a><a name="dtor"></a>C绑定状态回调：：*C绑定状态回调

析构函数。

```
~CBindStatusCallback();
```

### <a name="remarks"></a>备注

释放所有分配的资源。

## <a name="cbindstatuscallbackdownload"></a><a name="download"></a>CBind状态回拨：:D自己的负载

创建对象`CBindStatusCallback`和调用`StartAsyncDownload`以从指定的 URL 以异步方式下载数据。

```
static HRESULT Download(
    T* pT,
    ATL_PDATAAVAILABLE pFunc,
    BSTR bstrURL,
    IUnknown* pUnkContainer = NULL,
    BOOL bRelative = FALSE);
```

### <a name="parameters"></a>参数

*铂*<br/>
[在]指向请求异步数据传输的对象的指针。 对象`CBindStatusCallback`在此对象的类上被模板化。

*普丰克*<br/>
[在]指向接收读取数据的函数的指针。 该函数是对象类型`T`类的成员。 有关语法和示例，请参阅[StartAsync下载](#startasyncdownload)。

*bstrURL*<br/>
[在]要从中获取数据的 URL。 可以是任何有效的 URL 或文件名。 不能为 NULL。 例如：

`CComBSTR mybstr =_T("http://somesite/data.htm")`

*pUnk容器*<br/>
[在]容器`IUnknown`的 。 默认情况下为 NULL。

*b 相对*<br/>
[在]指示 URL 是相对的还是绝对的标记。 默认情况下，FALSE 表示 URL 是绝对的。

### <a name="return-value"></a>返回值

标准 HRESULT 值之一。

### <a name="remarks"></a>备注

每次数据可用时，它都会通过`OnDataAvailable`发送到对象。 `OnDataAvailable`读取数据并调用*pFunc*指向的功能（例如，存储数据或将其打印到屏幕）。

## <a name="cbindstatuscallbackgetbindinfo"></a><a name="getbindinfo"></a>CBind状态回拨：：获取绑定信息

被叫来告诉名字对象如何绑定。

```
STDMETHOD(GetBindInfo)(
    DWORD* pgrfBSCF,
    BINDINFO* pbindinfo);
```

### <a name="parameters"></a>参数

*pgrfBSCF*<br/>
[出]指向 BINDF 枚举值的指针，指示绑定操作应如何发生。 默认情况下，使用以下枚举值进行设置：

BINDF_ASYNCHRONOUS异步下载。

当`OnDataAvailable`数据尚未可用时BINDF_ASYNCSTORAGE返回E_PENDING，而不是在数据可用之前进行阻塞。

BINDF_GETNEWESTVERSION 绑定操作应检索数据的最新版本。

BINDF_NOWRITECACHE 绑定操作不应将检索到的数据存储在磁盘缓存中。

*普宾德福*<br/>
[进出]指向结构的指针`BINDINFO`，提供有关对象希望如何进行绑定的详细信息。

### <a name="return-value"></a>返回值

标准 HRESULT 值之一。

### <a name="remarks"></a>备注

默认实现将绑定设置为异步并使用数据推送模型。 在数据推送模型中，名字对象驱动异步绑定操作，并在有新数据可用时持续通知客户端。

## <a name="cbindstatuscallbackgetpriority"></a><a name="getpriority"></a>CBind状态回拨：：获取优先级

由异步名字对象调用，以获得绑定操作的优先级。

```
STDMETHOD(GetPriority)(LONG* pnPriority);
```

### <a name="parameters"></a>参数

*pn优先级*<br/>
[出]**LONG**变量的地址，在成功时，接收优先级。

### <a name="return-value"></a>返回值

返回 E_NOTIMPL。

## <a name="cbindstatuscallbackm_dwavailabletoread"></a><a name="m_dwavailabletoread"></a>CBind状态回拨：：m_dwAvailableToRead

可用于存储可供读取的字节数。

```
DWORD m_dwAvailableToRead;
```

### <a name="remarks"></a>备注

初始化为零。 `StartAsyncDownload`

## <a name="cbindstatuscallbackm_dwtotalread"></a><a name="m_dwtotalread"></a>CBind状态回拨：：m_dwTotalRead

异步数据传输中读取的字节的累计总数。

```
DWORD m_dwTotalRead;
```

### <a name="remarks"></a>备注

每次`OnDataAvailable`按实际读取的字节数调用增量。 初始化为零。 `StartAsyncDownload`

## <a name="cbindstatuscallbackm_pfunc"></a><a name="m_pfunc"></a>CBind状态回拨：：m_pFunc

在读取可用数据（`m_pFunc`例如，存储`OnDataAvailable`数据或将其打印到屏幕上）后，将调用 指向 的函数。

```
ATL_PDATAAVAILABLE m_pFunc;
```

### <a name="remarks"></a>备注

指向的`m_pFunc`函数是对象类的成员，具有以下语法：

```cpp
void Function_Name(
   CBindStatusCallback<T>* pbsc,
   BYTE* pBytes,
   DWORD dwSize
   );
```

## <a name="cbindstatuscallbackm_pt"></a><a name="m_pt"></a>CBind状态回拨：：m_pT

指向请求异步数据传输的对象的指针。

```
T* m_pT;
```

### <a name="remarks"></a>备注

对象`CBindStatusCallback`在此对象的类上被模板化。

## <a name="cbindstatuscallbackm_spbindctx"></a><a name="m_spbindctx"></a>CBind状态回拨：：m_spBindCtx

指向[IBindCtx](/windows/win32/api/objidl/nn-objidl-ibindctx)接口的指针，该接口提供对绑定上下文的访问（存储有关特定名字绑定操作的信息的对象）。

```
CComPtr<IBindCtx> m_spBindCtx;
```

### <a name="remarks"></a>备注

在 中`StartAsyncDownload`初始化。

## <a name="cbindstatuscallbackm_spbinding"></a><a name="m_spbinding"></a>CBind状态回拨：：m_spBinding

指向当前绑定操作`IBinding`的接口的指针。

```
CComPtr<IBinding> m_spBinding;
```

### <a name="remarks"></a>备注

在 中`OnStartBinding`初始化并在`OnStopBinding`中释放。

## <a name="cbindstatuscallbackm_spmoniker"></a><a name="m_spmoniker"></a>CBind状态回拨：：m_spMoniker

指向[IMoniker](/windows/win32/api/objidl/nn-objidl-imoniker)接口的指针，用于 URL。

```
CComPtr<IMoniker> m_spMoniker;
```

### <a name="remarks"></a>备注

在 中`StartAsyncDownload`初始化。

## <a name="cbindstatuscallbackm_spstream"></a><a name="m_spstream"></a>CBind状态回拨：：m_spStream

指向当前绑定操作的[IStream](/windows/win32/api/objidl/nn-objidl-istream)接口的指针。

```
CComPtr<IStream> m_spStream;
```

### <a name="remarks"></a>备注

当 BCSF`STGMEDIUM`标志BCSF_FIRSTDATANOTIFICATION并在 BCSF 标志BCSF_LASTDATANOTIFICATION时从结构中初始化`OnDataAvailable`。

## <a name="cbindstatuscallbackondataavailable"></a><a name="ondataavailable"></a>CBind状态回拨：：OnData 可用

系统提供的异步名字对象调用`OnDataAvailable`在对象可用时向对象提供数据。

```
STDMETHOD(
    OnDataAvailable)(DWORD grfBSCF,
    DWORD dwSize,
    FORMATETC* /* pformatetc */,
    STGMEDIUM* pstgmed);
```

### <a name="parameters"></a>参数

*grfBSCF*<br/>
[在]BSCF 枚举值。 以下一项或多项：BSCF_FIRSTDATANOTIFICATION、BSCF_INTERMEDIARYDATANOTIFICATION或BSCF_LASTDATANOTIFICATION。

*dwSize*<br/>
[在]自绑定开始以来可用的数据的累积量（以字节为单位）。 可以是零，指示数据量不相关或没有可用的特定数量。

*波波里奇*<br/>
[在]指向包含可用数据的格式的[FORMATETC](/windows/win32/com/the-formatetc-structure)结构的指针。 如果没有格式，可以CF_NULL。

*psgmed*<br/>
[在]指向保存当前可用实际数据的[STGMEDIUM](/windows/win32/com/the-stgmedium-structure)结构的指针。

### <a name="return-value"></a>返回值

标准 HRESULT 值之一。

### <a name="remarks"></a>备注

`OnDataAvailable`读取数据，然后调用对象的类的方法（例如，存储数据或将其打印到屏幕）。 有关详细信息[，请参阅 CBind 状态回拨：：启动同步下载](#startasyncdownload)。

## <a name="cbindstatuscallbackonlowresource"></a><a name="onlowresource"></a>CBind状态回调：：在低资源

在资源不足时调用。

```
STDMETHOD(OnLowResource)(DWORD /* dwReserved */);
```

### <a name="parameters"></a>参数

*dw保留*<br/>
保留。

### <a name="return-value"></a>返回值

返回S_OK。

## <a name="cbindstatuscallbackonobjectavailable"></a><a name="onobjectavailable"></a>CBind状态回调：：打开对象可用

由异步名字对象调用，将对象接口指针传递给应用程序。

```
STDMETHOD(OnObjectAvailable)(REFID /* riid */, IUnknown* /* punk */);
```

### <a name="parameters"></a>参数

*riid*<br/>
请求接口的接口标识符。 未使用。

*朋 克*<br/>
I未知接口的地址。 未使用。

### <a name="return-value"></a>返回值

返回S_OK。

## <a name="cbindstatuscallbackonprogress"></a><a name="onprogress"></a>CBind状态回拨：：在进度上

调用 以指示数据下载过程的进度。

```
STDMETHOD(OnProgress)(
    ULONG /* ulProgress */,
    ULONG /* ulProgressMax */,
    ULONG /* ulStatusCode */,
    LPCWSTRONG /* szStatusText */);
```

### <a name="parameters"></a>参数

*乌尔进步*<br/>
未签名的长整数。 未使用。

*ulProgressMax*<br/>
未签名的长整数未使用。

*ulStatus代码*<br/>
未签名的长整数。 未使用。

*szStatusText*<br/>
字符串值的地址。 未使用。

### <a name="return-value"></a>返回值

返回S_OK。

## <a name="cbindstatuscallbackonstartbinding"></a><a name="onstartbinding"></a>CBind状态回调：：打开绑定

将数据成员[m_spBinding](#m_spbinding)到`IBinding`*pBinding*中的指针。

```
STDMETHOD(OnStartBinding)(DWORD /* dwReserved */, IBinding* pBinding);
```

### <a name="parameters"></a>参数

*dw保留*<br/>
保留供将来使用。

*p绑定*<br/>
[在]当前绑定操作的 IBinding 接口的地址。 这不能为 NULL。 客户端应在此指针上调用 AddRef，以保持对绑定对象的引用。

## <a name="cbindstatuscallbackonstopbinding"></a><a name="onstopbinding"></a>CBind状态回调：：打开绑定

释放数据`IBinding`成员[m_spBinding](#m_spbinding)中的指针。

```
STDMETHOD(OnStopBinding)(HRESULT hresult, LPCWSTR /* szError */);
```

### <a name="parameters"></a>参数

*h结果*<br/>
从绑定操作返回的状态代码。

*szError*<br/>
字符串值的地址。 未使用。

### <a name="remarks"></a>备注

由系统提供的异步名字对象调用，以指示绑定操作的结束。

## <a name="cbindstatuscallbackstartasyncdownload"></a><a name="startasyncdownload"></a>CBind状态回拨：：开始同步下载

开始从指定的 URL 以异步方式下载数据。

```
HRESULT StartAsyncDownload(
    T* pT,
    ATL_PDATAAVAILABLE pFunc,
    BSTR bstrURL,
    IUnknown* pUnkContainer = NULL,
    BOOL bRelative = FALSE);
```

### <a name="parameters"></a>参数

*铂*<br/>
[在]指向请求异步数据传输的对象的指针。 对象`CBindStatusCallback`在此对象的类上被模板化。

*普丰克*<br/>
[在]指向接收正在读取的数据的函数的指针。 该函数是对象类型`T`类的成员。 有关语法和示例，请参阅**备注**。

*bstrURL*<br/>
[在]要从中获取数据的 URL。 可以是任何有效的 URL 或文件名。 不能为 NULL。 例如：

`CComBSTR mybstr =_T("http://somesite/data.htm")`

*pUnk容器*<br/>
[在]容器`IUnknown`的 。 默认情况下为 NULL。

*b 相对*<br/>
[在]指示 URL 是相对的还是绝对的标记。 默认情况下，FALSE 表示 URL 是绝对的。

### <a name="return-value"></a>返回值

标准 HRESULT 值之一。

### <a name="remarks"></a>备注

每次数据可用时，它都会通过`OnDataAvailable`发送到对象。 `OnDataAvailable`读取数据并调用*pFunc*指向的功能（例如，存储数据或将其打印到屏幕）。

*pFunc*指向的函数是对象类的成员，具有以下语法：

```cpp
void Function_Name(
    CBindStatusCallback<T>* pbsc,
    BYTE* pBytes,
    DWORD dwSize);
```

在下面的示例中（取自[ASYNC](../../overview/visual-cpp-samples.md)示例），函数`OnData`将接收到的数据写入文本框中。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_Windowing#87](../../atl/codesnippet/cpp/cbindstatuscallback-class_2.h)]

## <a name="see-also"></a>另请参阅

[类概述](../../atl/atl-class-overview.md)
