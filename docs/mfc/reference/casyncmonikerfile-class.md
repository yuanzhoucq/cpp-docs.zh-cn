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
ms.openlocfilehash: cd399368e46e4e9a86b4c6260e07aee07b80defb
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69507498"
---
# <a name="casyncmonikerfile-class"></a>CAsyncMonikerFile 类

提供功能以在 ActiveX 控件（原为 OLE 控件）中使用异步名字对象。

## <a name="syntax"></a>语法

```
class CAsyncMonikerFile : public CMonikerFile
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[CAsyncMonikerFile::CAsyncMonikerFile](#casyncmonikerfile)|构造 `CAsyncMonikerFile` 对象。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CAsyncMonikerFile::Close](#close)|关闭并释放所有资源。|
|[CAsyncMonikerFile::GetBinding](#getbinding)|检索指向异步传输绑定的指针。|
|[CAsyncMonikerFile::GetFormatEtc](#getformatetc)|检索流中数据的格式。|
|[CAsyncMonikerFile::Open](#open)|以异步方式打开文件。|

### <a name="protected-methods"></a>受保护的方法

|名称|描述|
|----------|-----------------|
|[CAsyncMonikerFile::CreateBindStatusCallback](#createbindstatuscallback)|创建一个实现`IBindStatusCallback`的 COM 对象。|
|[CAsyncMonikerFile::GetBindInfo](#getbindinfo)|由 OLE 系统库调用以请求要创建的绑定类型的信息。|
|[CAsyncMonikerFile::GetPriority](#getpriority)|由 OLE 系统库调用以获取绑定的优先级。|
|[CAsyncMonikerFile::OnDataAvailable](#ondataavailable)|调用以提供在异步绑定操作过程中可供客户端使用的数据。|
|[CAsyncMonikerFile::OnLowResource](#onlowresource)|当资源不足时调用。|
|[CAsyncMonikerFile::OnProgress](#onprogress)|调用以指示数据下载进程的进度。|
|[CAsyncMonikerFile::OnStartBinding](#onstartbinding)|当绑定启动时调用。|
|[CAsyncMonikerFile::OnStopBinding](#onstopbinding)|当异步传输停止时调用。|

## <a name="remarks"></a>备注

从[CMonikerFile](../../mfc/reference/cmonikerfile-class.md)派生而来, 后者又派生自[COleStreamFile](../../mfc/reference/colestreamfile-class.md), `CAsyncMonikerFile`它使用[IMoniker](/windows/win32/api/objidl/nn-objidl-imoniker)接口异步访问任何数据流, 包括从 URL 异步加载文件。 这些文件可以是 ActiveX 控件的数据路径属性。

异步名字对象主要用于启用了 Internet 的应用程序和 ActiveX 控件, 以便在文件传输过程中提供响应式用户界面。 这种情况的一个典型示例是使用[CDataPathProperty](../../mfc/reference/cdatapathproperty-class.md)为 ActiveX 控件提供异步属性。 在`CDataPathProperty`冗长的属性交换过程中, 对象将重复获取回调以指示新数据的可用性。

有关如何在 Internet 应用程序中使用异步名字对象和 ActiveX 控件的详细信息, 请参阅以下文章:

- [Internet 优先步骤:异步名字对象](../../mfc/asynchronous-monikers-on-the-internet.md)

- [Internet 优先步骤:ActiveX 控件](../../mfc/activex-controls-on-the-internet.md)

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CFile](../../mfc/reference/cfile-class.md)

[COleStreamFile](../../mfc/reference/colestreamfile-class.md)

[CMonikerFile](../../mfc/reference/cmonikerfile-class.md)

`CAsyncMonikerFile`

## <a name="requirements"></a>要求

**标头:** afxole

##  <a name="casyncmonikerfile"></a>CAsyncMonikerFile:: CAsyncMonikerFile

构造 `CAsyncMonikerFile` 对象。

```
CAsyncMonikerFile();
```

### <a name="remarks"></a>备注

它不会创建`IBindHost`接口。 `IBindHost`仅当在`Open`成员函数中提供时才使用。

有关`IBindHost`接口的说明, 请参阅 Windows SDK。

##  <a name="close"></a>CAsyncMonikerFile:: Close

调用此函数可关闭并释放所有资源。

```
virtual void Close();
```

### <a name="remarks"></a>备注

可对未打开或已关闭的文件调用。

##  <a name="createbindstatuscallback"></a>CAsyncMonikerFile:: CreateBindStatusCallback

创建一个实现`IBindStatusCallback`的 COM 对象。

```
virtual IUnknown* CreateBindStatusCallback(IUnknown* pUnkControlling);
```

### <a name="parameters"></a>参数

*pUnkControlling*<br/>
指向 "控制未知" (外部`IUnknown`) 的指针; 如果未使用聚合, 则为 NULL。

### <a name="return-value"></a>返回值

如果*pUnkControlling*不为 NULL, 则该函数返回一个指针, 该`IUnknown`指针指向支持`IBindStatusCallback`的新 COM 对象上的内部。 如果`pUnkControlling`为 NULL, 则函数返回指向支持`IBindStatusCallback`的新`IUnknown` COM 对象上的的指针。

### <a name="remarks"></a>备注

`CAsyncMonikerFile`需要一个实现`IBindStatusCallback`的 COM 对象。 MFC 实现此类对象, 而且它是可聚合的。 可以重写`CreateBindStatusCallback`以返回自己的 COM 对象。 通过`CreateBindStatusCallback`使用 com 对象的 "未知" 控制, com 对象可聚合 MFC 的实现。 使用`CCmdTarget` com 支持实现的 com 对象可以使用`CCmdTarget::GetControllingUnknown`检索控制未知。

或者, 您的 COM 对象可以通过调用`CreateBindStatusCallback( NULL )`委托给 MFC 的实现。

[CAsyncMonikerFile:: Open](#open)调用`CreateBindStatusCallback`。

有关异步名字对象和异步绑定的详细信息, 请参阅[IBindStatusCallback](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/ms775060\(v=vs.85\))接口和[异步绑定和存储的工作方式](/windows/win32/Stg/how-asynchronous-binding-and-storage-work)。 有关聚合的讨论, 请参阅[聚合](/windows/win32/com/aggregation)。 Windows SDK 中都有三个主题。

##  <a name="getbindinfo"></a>CAsyncMonikerFile:: GetBindInfo

从异步名字对象的客户端调用以通知异步名字对象如何绑定。

```
virtual DWORD GetBindInfo() const;
```

### <a name="return-value"></a>返回值

检索的设置`IBindStatusCallBack`。 有关`IBindStatusCallback`接口的说明, 请参阅 Windows SDK。

### <a name="remarks"></a>备注

默认实现将绑定设置为异步, 使用存储介质 (流), 并使用数据推送模型。 如果要更改绑定的行为, 请重写此函数。

执行此操作的一个原因是使用数据提取模型而不是数据推送模型进行绑定。 在数据请求模型中, 客户端驱动绑定操作, 并且名字对象只在读取时向客户端提供数据。 在数据推送模型中, 名字对象驱动异步绑定操作, 并在有新数据可用时持续通知客户端。

##  <a name="getbinding"></a>CAsyncMonikerFile:: GetBinding

调用此函数可检索指向异步传输绑定的指针。

```
IBinding* GetBinding() const;
```

### <a name="return-value"></a>返回值

指向异步传输开始`IBinding`时提供的接口的指针。 如果出于任何原因而无法以异步方式进行传输, 则返回 NULL。

### <a name="remarks"></a>备注

`IBinding`这允许您通过接口控制数据传输过程, 例如, 使用`IBinding::Abort`、 `IBinding::Pause`和`IBinding::Resume`。

有关`IBinding`接口的说明, 请参阅 Windows SDK。

##  <a name="getformatetc"></a>CAsyncMonikerFile:: GetFormatEtc

调用此函数可检索流中数据的格式。

```
FORMATETC* GetFormatEtc() const;
```

### <a name="return-value"></a>返回值

指向当前打开的流的 Windows 结构[FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc)的指针。 如果名字对象不是异步的, 或者异步操作尚未开始, 则返回 NULL。

##  <a name="getpriority"></a>CAsyncMonikerFile:: GetPriority

在绑定过程中, 从异步名字对象的客户端调用, 以接收到绑定操作的线程的优先级。

```
virtual LONG GetPriority() const;
```

### <a name="return-value"></a>返回值

将进行异步传输的优先级。 标准线程优先级标志之一:THREAD_PRIORITY_ABOVE_NORMAL、THREAD_PRIORITY_BELOW_NORMAL、THREAD_PRIORITY_HIGHEST、THREAD_PRIORITY_IDLE、THREAD_PRIORITY_LOWEST、THREAD_PRIORITY_NORMAL 和 THREAD_PRIORITY_TIME_CRITICAL。 有关这些值的说明, 请参阅 Windows 函数[参见 setthreadpriority](/windows/win32/api/processthreadsapi/nf-processthreadsapi-setthreadpriority) 。

### <a name="remarks"></a>备注

`GetPriority`不应直接调用。 THREAD_PRIORITY_NORMAL 由默认实现返回。

##  <a name="ondataavailable"></a>CAsyncMonikerFile:: OnDataAvailable

异步的名字对象`OnDataAvailable`调用, 用于在异步绑定操作过程中将数据提供给客户端。

```
virtual void OnDataAvailable(DWORD dwSize, DWORD bscfFlag);
```

### <a name="parameters"></a>参数

*dwSize*<br/>
自绑定开始以来可用数据的累计量 (以字节为单位)。 可以为零, 表示数据量与操作无关, 或者没有特定的可用量。

*bscfFlag*<br/>
BSCF 枚举值。 可以是以下一个或多个值:

- BSCF_FIRSTDATANOTIFICATION 标识给定绑定操作的`OnDataAvailable`第一次调用。

- BSCF_INTERMEDIATEDATANOTIFICATION 标识对绑定操作`OnDataAvailable`的中间调用。

- BSCF_LASTDATANOTIFICATION 标识绑定操作的最后`OnDataAvailable`一次调用。

### <a name="remarks"></a>备注

此函数的默认实现不执行任何操作。 有关示例实现, 请参阅以下示例。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCWinInet#5](../../mfc/codesnippet/cpp/casyncmonikerfile-class_1.cpp)]

##  <a name="onlowresource"></a>CAsyncMonikerFile:: OnLowResource

当资源不足时由名字对象调用。

```
virtual void OnLowResource();
```

### <a name="remarks"></a>备注

默认实现调用`GetBinding( )-> Abort( )`。

##  <a name="onprogress"></a>CAsyncMonikerFile:: OnProgress

重复由名字对象调用以指示此绑定操作的当前进度, 通常在较长的操作期间有合理的间隔。

```
virtual void OnProgress(
    ULONG ulProgress,
    ULONG ulProgressMax,
    ULONG ulStatusCode,
    LPCTSTR szStatusText);
```

### <a name="parameters"></a>参数

*ulProgress*<br/>
指示绑定操作的当前进度, 相对于*ulProgressMax*中指示的预期最大值。

*ulProgressMax*<br/>
指示此操作的调用`OnProgress`持续时间内的预期最大*ulProgress*值。

*ulStatusCode*<br/>
提供有关绑定操作进度的其他信息。 有效值取自`BINDSTATUS`枚举。 有关可能的值, 请参阅备注。

*szStatusText*<br/>
有关当前进度的信息, 具体取决于*ulStatusCode*的值。 有关可能的值, 请参阅备注。

### <a name="remarks"></a>备注

*UlStatusCode* (和每个值的*szStatusText* ) 的可能值为:

|||
|-|-|
|BINDSTATUS_FINDINGRESOURCE  |绑定操作正在查找保存要绑定到的对象或存储的资源。 *SzStatusText*提供要搜索的资源的显示名称 (例如, "www.microsoft.com")。  |
|BINDSTATUS_CONNECTING  |绑定操作将连接到保存要绑定到的对象或存储的资源。 *SzStatusText*提供要连接到的资源 (例如 IP 地址) 的显示名称。  |
|BINDSTATUS_SENDINGREQUEST|绑定操作请求将对象或存储绑定到。 *SzStatusText*提供对象的显示名称 (例如, 文件名)。|
|BINDSTATUS_REDIRECTING  |绑定操作已重定向到不同的数据位置。 *SzStatusText*提供新数据位置的显示名称。  |
|BINDSTATUS_USINGCACHEDCOPY  |绑定操作正在从缓存副本中检索请求的对象或存储。 *SzStatusText*为 NULL。  |
|BINDSTATUS_BEGINDOWNLOADDATA  |绑定操作已开始接收要绑定到的对象或存储。 *SzStatusText*提供数据位置的显示名称。|
|BINDSTATUS_DOWNLOADINGDATA  |绑定操作将继续接收要绑定到的对象或存储。 *SzStatusText*提供数据位置的显示名称。  |
|BINDSTATUS_ENDDOWNLOADDATA  |绑定操作已完成接收要绑定到的对象或存储。 *SzStatusText*提供数据位置的显示名称。  |
|BINDSTATUS_CLASSIDAVAILABLE  |要绑定到的对象的实例即将创建。 *SzStatusText*以字符串格式提供新对象的 CLSID, 从而允许客户端根据需要取消绑定操作。  |

##  <a name="onstartbinding"></a>CAsyncMonikerFile:: OnStartBinding

在派生类中重写此函数, 以便在启动绑定时执行操作。

```
virtual void OnStartBinding();
```

### <a name="remarks"></a>备注

此函数由名字对象回调。 默认实现不执行任何操作。

##  <a name="onstopbinding"></a>CAsyncMonikerFile:: OnStopBinding

绑定操作结束时由名字对象调用。

```
virtual void OnStopBinding(HRESULT hresult, LPCTSTR szError);
```

### <a name="parameters"></a>参数

*hresult*<br/>
作为错误或警告值的 HRESULT。

*szErrort*<br/>
描述错误的字符串。

### <a name="remarks"></a>备注

重写此函数以在传输停止时执行操作。 默认情况下, 该函数`IBinding`将释放。

有关`IBinding`接口的说明, 请参阅 Windows SDK。

##  <a name="open"></a>CAsyncMonikerFile:: Open

调用此成员函数以异步方式打开文件。

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
指向要异步打开的文件的指针。 该文件可以是任何有效的 URL 或文件名。

*pError*<br/>
指向文件异常的指针。 如果发生错误, 则会将其设置为原因。

*pMoniker*<br/>
指向异步名字对象接口`IMoniker`的指针, 精确的名字对象, 它是文档自己的名字对象的组合, 你可以使用`IOleClientSite::GetMoniker(OLEWHICHMK_CONTAINER)`检索它, 以及从路径名称创建的名字对象。 控件可以使用此名字对象进行绑定, 但这不是控件应保存的名字对象。

*pBindHost*<br/>
指向`IBindHost`接口的指针, 该接口将用于基于可能的相对路径名创建名字对象。 如果绑定主机无效或未提供名字对象, 则调用默认为`Open(lpszFileName,pError)`。 有关`IBindHost`接口的说明, 请参阅 Windows SDK。

*pServiceProvider*<br/>
指向 `IServiceProvider` 接口的指针。 如果服务提供程序无效或无法为提供服务`IBindHost`, 则调用默认为。 `Open(lpszFileName,pError)`

*pUnknown*<br/>
指向 `IUnknown` 接口的指针。 如果`IServiceProvider`找到了, 则函数将`IBindHost`查询。 如果服务提供程序无效或无法为提供服务`IBindHost`, 则调用默认为。 `Open(lpszFileName,pError)`

### <a name="return-value"></a>返回值

如果成功打开文件, 则为非零值;否则为0。

### <a name="remarks"></a>备注

此调用启动绑定过程。

可以对*lpszURL*参数使用 URL 或文件名。 例如:

[!code-cpp[NVC_MFCWinInet#6](../../mfc/codesnippet/cpp/casyncmonikerfile-class_2.cpp)]

\- 或 -

[!code-cpp[NVC_MFCWinInet#7](../../mfc/codesnippet/cpp/casyncmonikerfile-class_3.cpp)]

## <a name="see-also"></a>请参阅

[CMonikerFile 类](../../mfc/reference/cmonikerfile-class.md)<br/>
[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[CMonikerFile 类](../../mfc/reference/cmonikerfile-class.md)<br/>
[CDataPathProperty 类](../../mfc/reference/cdatapathproperty-class.md)
