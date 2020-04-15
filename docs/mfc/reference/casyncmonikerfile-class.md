---
title: CAsyncMonikerFile 类
ms.date: 11/04/2016
f1_keywords:
- CAsyncMonikerFile
- AFXOLE/CAsyncMonikerFile
- AFXOLE/CAsyncMonikerFile::CAsyncMonikerFile
- AFXOLE/CAsyncMonikerFile::Close
- AFXOLE/CAsyncMonikerFile::GetBinding
- AFXOLE/CAsyncMonikerFile::GetFormatEtc
- AFXOLE/CAsyncMonikerFile::Open
- AFXOLE/CAsyncMonikerFile::CreateBindStatusCallback
- AFXOLE/CAsyncMonikerFile::GetBindInfo
- AFXOLE/CAsyncMonikerFile::GetPriority
- AFXOLE/CAsyncMonikerFile::OnDataAvailable
- AFXOLE/CAsyncMonikerFile::OnLowResource
- AFXOLE/CAsyncMonikerFile::OnProgress
- AFXOLE/CAsyncMonikerFile::OnStartBinding
- AFXOLE/CAsyncMonikerFile::OnStopBinding
helpviewer_keywords:
- CAsyncMonikerFile [MFC], CAsyncMonikerFile
- CAsyncMonikerFile [MFC], Close
- CAsyncMonikerFile [MFC], GetBinding
- CAsyncMonikerFile [MFC], GetFormatEtc
- CAsyncMonikerFile [MFC], Open
- CAsyncMonikerFile [MFC], CreateBindStatusCallback
- CAsyncMonikerFile [MFC], GetBindInfo
- CAsyncMonikerFile [MFC], GetPriority
- CAsyncMonikerFile [MFC], OnDataAvailable
- CAsyncMonikerFile [MFC], OnLowResource
- CAsyncMonikerFile [MFC], OnProgress
- CAsyncMonikerFile [MFC], OnStartBinding
- CAsyncMonikerFile [MFC], OnStopBinding
ms.assetid: 17378b66-a49a-4b67-88e3-7756ad26a2fc
ms.openlocfilehash: 57ab463445f249b4e9393f19af103b7588962d5e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376998"
---
# <a name="casyncmonikerfile-class"></a>CAsyncMonikerFile 类

提供功能以在 ActiveX 控件（原为 OLE 控件）中使用异步名字对象。

## <a name="syntax"></a>语法

```
class CAsyncMonikerFile : public CMonikerFile
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[CAsyncMoniker文件：CAsyncMoniker文件](#casyncmonikerfile)|构造 `CAsyncMonikerFile` 对象。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CAsyncMoniker文件：关闭](#close)|关闭并释放所有资源。|
|[CAsyncMoniker文件：获取绑定](#getbinding)|检索指向异步传输绑定的指针。|
|[CAsyncMonker文件：：获取格式](#getformatetc)|检索流中数据的格式。|
|[CAsyncMoniker文件：：打开](#open)|异步打开文件。|

### <a name="protected-methods"></a>受保护的方法

|名称|说明|
|----------|-----------------|
|[CAsyncMoniker 文件：：创建绑定状态回调](#createbindstatuscallback)|创建实现`IBindStatusCallback`的 COM 对象。|
|[CAsyncMoniker文件：：获取宾德信息](#getbindinfo)|由 OLE 系统库调用，以请求有关要创建的绑定类型的信息。|
|[CAsyncMoniker文件：获取优先级](#getpriority)|由 OLE 系统库调用，以获得绑定的优先级。|
|[CAsyncMoniker文件：：OnData可用](#ondataavailable)|调用以在异步绑定操作期间向客户端提供数据。|
|[CAsyncMonker文件：：在洛资源](#onlowresource)|在资源不足时调用。|
|[CAsyncMoniker 文件：：在进度上](#onprogress)|已调用以指示数据下载过程的进度。|
|[CAsyncMonker 文件：：开始绑定](#onstartbinding)|启动绑定时调用。|
|[CAsyncMonker 文件：：打开绑定](#onstopbinding)|在异步传输停止时调用。|

## <a name="remarks"></a>备注

从[CMonikerFile](../../mfc/reference/cmonikerfile-class.md)派生，而[COleStreamFile](../../mfc/reference/colestreamfile-class.md)则`CAsyncMonikerFile`使用[IMoniker](/windows/win32/api/objidl/nn-objidl-imoniker)接口异步访问任何数据流，包括从 URL 以异步方式加载文件。 这些文件可以是 ActiveX 控件的数据路径属性。

异步名字器主要用于支持 Internet 的应用程序和 ActiveX 控件，以在文件传输期间提供响应式用户界面。 这方面的一个主要示例是使用[CDataPath 属性](../../mfc/reference/cdatapathproperty-class.md)为 ActiveX 控件提供异步属性。 对象`CDataPathProperty`将反复收到回调，以指示在冗长的属换过程中新数据的可用性。

有关如何在 Internet 应用程序中使用异步名字器和 ActiveX 控件的详细信息，请参阅以下文章：

- [互联网第一步：异步月友](../../mfc/asynchronous-monikers-on-the-internet.md)

- [互联网第一步：主动X控制](../../mfc/activex-controls-on-the-internet.md)

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CFile](../../mfc/reference/cfile-class.md)

[COleStream文件](../../mfc/reference/colestreamfile-class.md)

[CMonikerFile](../../mfc/reference/cmonikerfile-class.md)

`CAsyncMonikerFile`

## <a name="requirements"></a>要求

**标题：** afxole.h

## <a name="casyncmonikerfilecasyncmonikerfile"></a><a name="casyncmonikerfile"></a>CAsyncMoniker文件：CAsyncMoniker文件

构造 `CAsyncMonikerFile` 对象。

```
CAsyncMonikerFile();
```

### <a name="remarks"></a>备注

它不创建`IBindHost`接口。 `IBindHost`仅当在`Open`成员函数中提供时才使用。

有关接口的说明，`IBindHost`请参阅 Windows SDK。

## <a name="casyncmonikerfileclose"></a><a name="close"></a>CAsyncMoniker文件：关闭

调用此函数以关闭和释放所有资源。

```
virtual void Close();
```

### <a name="remarks"></a>备注

可以调用未打开或已关闭的文件。

## <a name="casyncmonikerfilecreatebindstatuscallback"></a><a name="createbindstatuscallback"></a>CAsyncMoniker 文件：：创建绑定状态回调

创建实现`IBindStatusCallback`的 COM 对象。

```
virtual IUnknown* CreateBindStatusCallback(IUnknown* pUnkControlling);
```

### <a name="parameters"></a>参数

*pUnk控制*<br/>
如果不使用聚合，则指向控制未知`IUnknown`（外部 ） 或 NULL 的指针。

### <a name="return-value"></a>返回值

如果*pUnk控制*不是 NULL，则函数将返回指向支持`IUnknown``IBindStatusCallback`的新 COM 对象上的内部的指针。 如果`pUnkControlling`为 NULL，则函数返回指向支持`IUnknown``IBindStatusCallback`的新 COM 对象上的 指针。

### <a name="remarks"></a>备注

`CAsyncMonikerFile`需要实现`IBindStatusCallback`的 COM 对象。 MFC 实现这样的对象，它是可聚合的。 您可以重写`CreateBindStatusCallback`以返回自己的 COM 对象。 您的 COM 对象可以通过调用`CreateBindStatusCallback`控制未知 COM 对象的 MFC 实现来聚合 MFC 的实现。 使用`CCmdTarget`COM 支持实现的 COM 对象可以使用 检索`CCmdTarget::GetControllingUnknown`未知控制。

或者，您的 COM 对象可以通过调用`CreateBindStatusCallback( NULL )`来委派到 MFC 的实现。

[CAsyncMoniker文件：打开](#open)呼叫`CreateBindStatusCallback`。

有关异步名字器和异步绑定的详细信息，请参阅[IBindStatus 回调](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/ms775060\(v=vs.85\))接口以及[异步绑定和存储的工作原理](/windows/win32/Stg/how-asynchronous-binding-and-storage-work)。 有关聚合的讨论，请参阅[聚合](/windows/win32/com/aggregation)。 所有三个主题都在 Windows SDK 中。

## <a name="casyncmonikerfilegetbindinfo"></a><a name="getbindinfo"></a>CAsyncMoniker文件：：获取宾德信息

从异步名字的客户端调用，告诉异步名字对象如何绑定。

```
virtual DWORD GetBindInfo() const;
```

### <a name="return-value"></a>返回值

检索 的设置`IBindStatusCallBack`。 有关接口的说明，`IBindStatusCallback`请参阅 Windows SDK。

### <a name="remarks"></a>备注

默认实现将绑定设置为异步、使用存储介质（流）并使用数据推送模型。 如果要更改绑定的行为，将重写此函数。

这样做的一个原因是使用数据拉模型而不是数据推送模型进行绑定。 在数据提取模型中，客户端驱动绑定操作，而名字对象仅在读取客户端时向客户端提供数据。 在数据推送模型中，名字对象驱动异步绑定操作，并在有新数据可用时持续通知客户端。

## <a name="casyncmonikerfilegetbinding"></a><a name="getbinding"></a>CAsyncMoniker文件：获取绑定

调用此函数以检索指向异步传输绑定的指针。

```
IBinding* GetBinding() const;
```

### <a name="return-value"></a>返回值

指向异步传输`IBinding`开始时提供的接口的指针。 如果由于任何原因无法异步进行传输，则返回 NULL。

### <a name="remarks"></a>备注

`IBinding`这允许您通过接口控制数据传输过程，例如，`IBinding::Abort`使用 和`IBinding::Pause`。 `IBinding::Resume`

有关接口的说明，`IBinding`请参阅 Windows SDK。

## <a name="casyncmonikerfilegetformatetc"></a><a name="getformatetc"></a>CAsyncMonker文件：：获取格式

调用此函数以检索流中数据的格式。

```
FORMATETC* GetFormatEtc() const;
```

### <a name="return-value"></a>返回值

指向当前打开的流的 Windows 结构[FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc)的指针。 如果名字对象尚未绑定，则返回 NULL，如果它不是异步的，或者异步操作尚未开始。

## <a name="casyncmonikerfilegetpriority"></a><a name="getpriority"></a>CAsyncMoniker文件：获取优先级

当绑定进程开始接收绑定操作的线程的优先级时，从异步名字项的客户端调用。

```
virtual LONG GetPriority() const;
```

### <a name="return-value"></a>返回值

异步传输的优先级。 标准线程优先级标志之一：THREAD_PRIORITY_ABOVE_NORMAL、THREAD_PRIORITY_BELOW_NORMAL、THREAD_PRIORITY_HIGHEST、THREAD_PRIORITY_IDLE、THREAD_PRIORITY_LOWEST、THREAD_PRIORITY_NORMAL 和THREAD_PRIORITY_TIME_CRITICAL。 有关这些值的说明，请参阅 Windows 函数[SetThreadPriority。](/windows/win32/api/processthreadsapi/nf-processthreadsapi-setthreadpriority)

### <a name="remarks"></a>备注

`GetPriority`不应直接调用。 THREAD_PRIORITY_NORMAL由默认实现返回。

## <a name="casyncmonikerfileondataavailable"></a><a name="ondataavailable"></a>CAsyncMoniker文件：：OnData可用

异步名字对象调用`OnDataAvailable`在异步绑定操作期间向客户端提供数据。

```
virtual void OnDataAvailable(DWORD dwSize, DWORD bscfFlag);
```

### <a name="parameters"></a>参数

*dwSize*<br/>
自绑定开始以来可用的数据的累积量（以字节为单位）。 可以是零，指示数据量与操作无关，或者没有可用的特定量。

*bscfFlag*<br/>
BSCF 枚举值。 可以是以下一个或多个值：

- BSCF_FIRSTDATANOTIFICATION 标识给定绑定操作的第`OnDataAvailable`一个调用。

- BSCF_INTERMEDIATEDATANOTIFICATION 标识绑定操作的中间`OnDataAvailable`调用。

- BSCF_LASTDATANOTIFICATION 标识绑定操作的最后一`OnDataAvailable`个调用。

### <a name="remarks"></a>备注

此函数的默认实现不执行任何操作。 有关示例实现，请参阅以下示例。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCWinInet#5](../../mfc/codesnippet/cpp/casyncmonikerfile-class_1.cpp)]

## <a name="casyncmonikerfileonlowresource"></a><a name="onlowresource"></a>CAsyncMonker文件：：在洛资源

当资源不足时，由名字对象调用。

```
virtual void OnLowResource();
```

### <a name="remarks"></a>备注

默认实现调用`GetBinding( )-> Abort( )`。

## <a name="casyncmonikerfileonprogress"></a><a name="onprogress"></a>CAsyncMoniker 文件：：在进度上

名字对象反复调用以指示此绑定操作的当前进度，通常在长时间操作期间以合理的间隔进行。

```
virtual void OnProgress(
    ULONG ulProgress,
    ULONG ulProgressMax,
    ULONG ulStatusCode,
    LPCTSTR szStatusText);
```

### <a name="parameters"></a>参数

*乌尔进步*<br/>
指示绑定操作相对于*ulProgressMax*中指示的预期最大值的当前进度。

*ulProgressMax*<br/>
指示此操作调用`OnProgress`期间*ulProgress*的预期最大值。

*ulStatus代码*<br/>
提供有关绑定操作进度的其他信息。 有效值取自`BINDSTATUS`枚举。 有关可能的值，请参阅备注。

*szStatusText*<br/>
有关当前进度的信息，具体取决于*ulStatusCode*的值。 有关可能的值，请参阅备注。

### <a name="remarks"></a>备注

*ulStatusCode（* 以及每个值的*szStatusText）* 的可能值为：

|||
|-|-|
|BINDSTATUS_FINDINGRESOURCE  |绑定操作是查找保存对象或存储绑定到的资源。 *szStatusText*提供要搜索的资源的显示名称（例如，"www.microsoft.com"）。  |
|BINDSTATUS_CONNECTING  |绑定操作连接到保存对象或存储绑定到的资源。 *szStatusText*提供所连接的资源（例如，IP 地址）的显示名称。  |
|BINDSTATUS_SENDINGREQUEST|绑定操作请求绑定的对象或存储。 *szStatusText*提供对象的显示名称（例如，文件名）。|
|BINDSTATUS_REDIRECTING  |绑定操作已重定向到其他数据位置。 *szStatusText*提供新数据位置的显示名称。  |
|BINDSTATUS_USINGCACHEDCOPY  |绑定操作是从缓存的副本检索请求的对象或存储。 *szStatusText*为 NULL。  |
|BINDSTATUS_BEGINDOWNLOADDATA  |绑定操作已开始接收绑定的对象或存储。 *szStatusText*提供数据位置的显示名称。|
|BINDSTATUS_DOWNLOADINGDATA  |绑定操作继续接收绑定的对象或存储。 *szStatusText*提供数据位置的显示名称。  |
|BINDSTATUS_ENDDOWNLOADDATA  |绑定操作已完成接收要绑定的对象或存储。 *szStatusText*提供数据位置的显示名称。  |
|BINDSTATUS_CLASSIDAVAILABLE  |绑定到的对象的实例即将创建。 *szStatusText*以字符串格式提供新对象的 CLSID，允许客户端根据需要取消绑定操作。  |

## <a name="casyncmonikerfileonstartbinding"></a><a name="onstartbinding"></a>CAsyncMonker 文件：：开始绑定

覆盖派生类中的此函数，在启动绑定时执行操作。

```
virtual void OnStartBinding();
```

### <a name="remarks"></a>备注

此函数由名字对象调用回。 默认实现不执行任何操作。

## <a name="casyncmonikerfileonstopbinding"></a><a name="onstopbinding"></a>CAsyncMonker 文件：：打开绑定

由绑定操作结束时的绰号调用。

```
virtual void OnStopBinding(HRESULT hresult, LPCTSTR szError);
```

### <a name="parameters"></a>参数

*h结果*<br/>
错误或警告值的 HRESULT。

*什洛特*<br/>
描述错误的字符串。

### <a name="remarks"></a>备注

重写此函数以在停止传输时执行操作。 默认情况下，函数将释放`IBinding`。

有关接口的说明，`IBinding`请参阅 Windows SDK。

## <a name="casyncmonikerfileopen"></a><a name="open"></a>CAsyncMoniker文件：：打开

调用此成员函数以异步打开文件。

```
virtual BOOL Open(
    LPCTSTR lpszURL,
    CFileException* pError = NULL);

virtual BOOL Open(
    IMoniker* pMoniker,
    CFileException* pError = NULL);

virtual BOOL Open(
    LPCTSTR lpszURL,
    IBindHost* pBindHost,
    CFileException* pError = NULL);

virtual BOOL Open(
    IMoniker* pMoniker,
    IBindHost* pBindHost,
    CFileException* pError = NULL);

virtual BOOL Open(
    LPCTSTR lpszURL,
    IServiceProvider* pServiceProvider,
    CFileException* pError = NULL);

virtual BOOL Open(
    IMoniker* pMoniker,
    IServiceProvider* pServiceProvider,
    CFileException* pError = NULL);

virtual BOOL Open(
    LPCTSTR lpszURL,
    IUnknown* pUnknown,
    CFileException* pError = NULL);

virtual BOOL Open(
    IMoniker* pMoniker,
    IUnknown* pUnknown,
    CFileException* pError = NULL);
```

### <a name="parameters"></a>参数

*lpszURL*<br/>
要异步打开的文件指针。 该文件可以是任何有效的 URL 或文件名。

*pError*<br/>
指向文件异常的指针。 如果出现错误，它将设置为原因。

*普莫尼克尔*<br/>
指向异步名字器接口`IMoniker`的指针，一个精确的名字对象，它是文档自己的名字对象的组合，您可以使用 检索`IOleClientSite::GetMoniker(OLEWHICHMK_CONTAINER)`，以及从路径名称创建的名字对象。 控件可以使用此名字绑定，但这不是控件应保存的名字。

*pBindHost*<br/>
指向接口的`IBindHost`指针，用于从潜在相对路径名称创建名字对象。 如果绑定主机无效或未提供名字对象，则调用默认为`Open(lpszFileName,pError)`。 有关接口的说明，`IBindHost`请参阅 Windows SDK。

*p服务提供商*<br/>
指向 `IServiceProvider` 接口的指针。 如果服务提供商无效或无法为`IBindHost`提供 服务，则调用默认为`Open(lpszFileName,pError)`。

*p 未知*<br/>
指向 `IUnknown` 接口的指针。 如果`IServiceProvider`找到，则函数将查询`IBindHost`。 如果服务提供商无效或无法为`IBindHost`提供 服务，则调用默认为`Open(lpszFileName,pError)`。

### <a name="return-value"></a>返回值

如果文件成功打开，则非零;否则 0。

### <a name="remarks"></a>备注

此调用启动绑定进程。

可以使用 URL 或文件名进行*lpszURL*参数。 例如：

[!code-cpp[NVC_MFCWinInet#6](../../mfc/codesnippet/cpp/casyncmonikerfile-class_2.cpp)]

\- 或 -

[!code-cpp[NVC_MFCWinInet#7](../../mfc/codesnippet/cpp/casyncmonikerfile-class_3.cpp)]

## <a name="see-also"></a>另请参阅

[CMonikerFile 类](../../mfc/reference/cmonikerfile-class.md)<br/>
[层次结构图表](../../mfc/hierarchy-chart.md)<br/>
[CMonikerFile 类](../../mfc/reference/cmonikerfile-class.md)<br/>
[CDataPathProperty 类](../../mfc/reference/cdatapathproperty-class.md)
