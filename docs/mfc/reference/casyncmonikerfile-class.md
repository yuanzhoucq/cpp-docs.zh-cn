---
title: "CAsyncMonikerFile 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
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
dev_langs:
- C++
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
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 546e251f3387175812e6ba7f8cfed5d8a878d658
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
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
|[CAsyncMonikerFile::GetBinding](#getbinding)|检索指向异步传输绑定。|  
|[CAsyncMonikerFile::GetFormatEtc](#getformatetc)|检索流中的数据的格式。|  
|[CAsyncMonikerFile::Open](#open)|以异步方式打开文件。|  
  
### <a name="protected-methods"></a>受保护的方法  
  
|名称|描述|  
|----------|-----------------|  
|[CAsyncMonikerFile::CreateBindStatusCallback](#createbindstatuscallback)|创建 COM 对象实现`IBindStatusCallback`。|  
|[CAsyncMonikerFile::GetBindInfo](#getbindinfo)|调用由 OLE 系统库上的一种绑定创建的请求信息。|  
|[CAsyncMonikerFile::GetPriority](#getpriority)|调用由 OLE 系统库，以获取绑定的优先级。|  
|[CAsyncMonikerFile::OnDataAvailable](#ondataavailable)|调用以变得在异步绑定操作期间可用于客户端提供数据。|  
|[CAsyncMonikerFile::OnLowResource](#onlowresource)|当资源不足时调用。|  
|[CAsyncMonikerFile::OnProgress](#onprogress)|调用以指示在下载过程的数据的进度。|  
|[CAsyncMonikerFile::OnStartBinding](#onstartbinding)|当绑定正在启动时调用。|  
|[CAsyncMonikerFile::OnStopBinding](#onstopbinding)|当异步传输已停止时调用。|  
  
## <a name="remarks"></a>备注  
 派生自[CMonikerFile](../../mfc/reference/cmonikerfile-class.md)，后者又派生自[COleStreamFile](../../mfc/reference/colestreamfile-class.md)，`CAsyncMonikerFile`使用[IMoniker](http://msdn.microsoft.com/library/windows/desktop/ms679705)接口来访问任何数据的流以异步方式，包括从 URL 异步加载文件。 文件可以是 ActiveX 控件的数据路径属性。  
  
 异步名字对象主要是在启用 Internet 的应用程序和 ActiveX 控件中用于在文件传输过程中提供响应用户界面。 明显的例子是使用[CDataPathProperty](../../mfc/reference/cdatapathproperty-class.md)为 ActiveX 控件提供异步属性。 `CDataPathProperty`对象重复获得回调来指示期间长时间的属性交换过程的新数据的可用性。  
  
 有关如何在 Internet 应用程序中使用异步名字对象和 ActiveX 控件的详细信息，请参阅以下文章：  
  
- [Internet 前几个步骤： 异步名字对象](../../mfc/asynchronous-monikers-on-the-internet.md)  
  
- [Internet 前几个步骤： ActiveX 控件](../../mfc/activex-controls-on-the-internet.md)  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CFile](../../mfc/reference/cfile-class.md)  
  
 [COleStreamFile](../../mfc/reference/colestreamfile-class.md)  
  
 [CMonikerFile](../../mfc/reference/cmonikerfile-class.md)  
  
 `CAsyncMonikerFile`  
  
## <a name="requirements"></a>惠?  
 **标头：** afxole.h  
  
##  <a name="casyncmonikerfile"></a>CAsyncMonikerFile::CAsyncMonikerFile  
 构造 `CAsyncMonikerFile` 对象。  
  
```  
CAsyncMonikerFile();
```  
  
### <a name="remarks"></a>备注  
 它不会创建`IBindHost`接口。 `IBindHost`仅当你提供在使用**打开**成员函数。  
  
 有关的说明`IBindHost`接口，请参阅 Windows SDK。  
  
##  <a name="close"></a>CAsyncMonikerFile::Close  
 调用此函数可关闭并释放所有资源。  
  
```  
virtual void Close();
```  
  
### <a name="remarks"></a>备注  
 可以在未打开或已关闭的文件上调用。  
  
##  <a name="createbindstatuscallback"></a>CAsyncMonikerFile::CreateBindStatusCallback  
 创建 COM 对象实现`IBindStatusCallback`。  
  
```  
virtual IUnknown* CreateBindStatusCallback(IUnknown* pUnkControlling);
```  
  
### <a name="parameters"></a>参数  
 `pUnkControlling`  
 指向控制未知的 (外部**IUnknown**) 或**NULL**如果未使用聚合。  
  
### <a name="return-value"></a>返回值  
 如果`pUnkControlling`不**NULL**，该函数将指针返回到内部**IUnknown**上新的 COM 对象支持`IBindStatusCallback`。 如果`pUnkControlling`是**NULL**，该函数返回一个指向**IUnknown**上新的 COM 对象支持`IBindStatusCallback`。  
  
### <a name="remarks"></a>备注  
 `CAsyncMonikerFile`需要一个 COM 对象，该对象实现`IBindStatusCallback`。 MFC 实现此类对象，并是聚合。 您可以重写`CreateBindStatusCallback`以返回你自己的 COM 对象。 COM 对象可以通过调用聚合 MFC 的实现`CreateBindStatusCallback`与 COM 对象控制未知。 使用实现的 COM 对象`CCmdTarget`COM 支持可以检索控制未知使用**CCmdTarget::GetControllingUnknown**。  
  
 或者，您的 COM 对象可以委托到 MFC 的实现通过调用**CreateBindStatusCallback (NULL)**。  
  
 [CAsyncMonikerFile::Open](#open)调用`CreateBindStatusCallback`。  
  
 有关异步名字对象和异步绑定的详细信息，请参阅[IBindStatusCallback](http://msdn.microsoft.com/library/ie/ms775060)接口和[如何异步绑定和存储工作](http://msdn.microsoft.com/library/windows/desktop/aa379152)。 有关聚合的讨论，请参阅[聚合](http://msdn.microsoft.com/library/windows/desktop/ms686558)。 所有三个主题是 Windows SDK 中。  
  
##  <a name="getbindinfo"></a>CAsyncMonikerFile::GetBindInfo  
 从异步名字对象的客户端，以告诉它想要将绑定的异步名字对象调用。  
  
```  
virtual DWORD GetBindInfo() const;  
```  
  
### <a name="return-value"></a>返回值  
 将检索的设置**IBindStatusCallBack**。 有关的说明`IBindStatusCallback`接口，请参阅 Windows SDK。  
  
### <a name="remarks"></a>备注  
 默认实现设置是异步的以使用存储介质 （流），并使用数据推送模型的绑定。 如果你想要更改绑定的行为，重写此函数。  
  
 执行此操作的一个原因是将绑定而不数据推送模型中使用数据拉取模型。 在数据拉入模型中，客户端驱动器绑定操作中，并标记仅提供数据给客户端读取它时。 在数据推送模型中，名字对象驱动器异步绑定操作和持续在新数据可用时通知客户端。  
  
##  <a name="getbinding"></a>CAsyncMonikerFile::GetBinding  
 调用此函数可检索异步传输绑定的指针。  
  
```  
IBinding* GetBinding() const;  
```  
  
### <a name="return-value"></a>返回值  
 指向的指针`IBinding`异步传输开始时提供的接口。 返回**NULL**如果出于任何原因传输不能成为以异步方式。  
  
### <a name="remarks"></a>备注  
 这允许你控制的数据传输进程通过`IBinding`接口，例如，与**IBinding::Abort**， **IBinding::Pause**，和**IBinding::Resume**.  
  
 有关的说明`IBinding`接口，请参阅 Windows SDK。  
  
##  <a name="getformatetc"></a>CAsyncMonikerFile::GetFormatEtc  
 调用此函数可检索的流中的数据格式。  
  
```  
FORMATETC* GetFormatEtc() const;  
```  
  
### <a name="return-value"></a>返回值  
 指向 Windows 结构的指针[FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177)为当前打开的流。 返回**NULL**如果标记尚未绑定，如果它不是异步的或者如果未开始异步操作。  
  
##  <a name="getpriority"></a>CAsyncMonikerFile::GetPriority  
 从客户端的异步名字对象调用在绑定进程启动时接收到线程给定绑定操作的优先级。  
  
```  
virtual LONG GetPriority() const;  
```  
  
### <a name="return-value"></a>返回值  
 从该处异步传输将发生的优先级。 一个标准的线程优先级标志： **THREAD_PRIORITY_ABOVE_NORMAL**， **THREAD_PRIORITY_BELOW_NORMAL**， **THREAD_PRIORITY_HIGHEST**， **THREAD_PRIORITY_IDLE**， **THREAD_PRIORITY_LOWEST**， **THREAD_PRIORITY_NORMAL**，和**THREAD_PRIORITY_TIME_CRITICAL**。 请参阅 Windows 函数[SetThreadPriority](http://msdn.microsoft.com/library/windows/desktop/ms686277)有关这些值的说明。  
  
### <a name="remarks"></a>备注  
 `GetPriority`应不直接调用。 **THREAD_PRIORITY_NORMAL**返回的默认实现。  
  
##  <a name="ondataavailable"></a>CAsyncMonikerFile::OnDataAvailable  
 异步名字对象调用`OnDataAvailable`变得可用，将向客户端提供数据，在异步过程绑定操作。  
  
```  
virtual void OnDataAvailable(DWORD dwSize, DWORD bscfFlag);
```  
  
### <a name="parameters"></a>参数  
 `dwSize`  
 提供的绑定开始以来的数据累积量 （以字节为单位）。 可以是零，表示的数据量与此操作，无关，或任何特定数量变为可用。  
  
 *bscfFlag*  
 A **BSCF**枚举值。 可以是一个或多个以下值：  
  
- **BSCF_FIRSTDATANOTIFICATION**标识首次调用`OnDataAvailable`给定的绑定操作。  
  
- **BSCF_INTERMEDIATEDATANOTIFICATION**标识对的中间调用`OnDataAvailable`绑定操作。  
  
- **BSCF_LASTDATANOTIFICATION**标识上次调用`OnDataAvailable`绑定操作。  
  
### <a name="remarks"></a>备注  
 此函数的默认实现不执行任何操作。 请参阅下面的示例，有关示例实现。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCWinInet#5](../../mfc/codesnippet/cpp/casyncmonikerfile-class_1.cpp)]  
  
##  <a name="onlowresource"></a>CAsyncMonikerFile::OnLowResource  
 当资源不足时，调用由名字对象。  
  
```  
virtual void OnLowResource();
```  
  
### <a name="remarks"></a>备注  
 默认实现调用`GetBinding( )-> Abort( )`。  
  
##  <a name="onprogress"></a>CAsyncMonikerFile::OnProgress  
 调用由重复以指示此绑定的操作，通常在合理时间间隔内较长的操作的当前进度的名字对象。  
  
```  
virtual void OnProgress(
    ULONG ulProgress,  
    ULONG ulProgressMax,  
    ULONG ulStatusCode,  
    LPCTSTR szStatusText);
```  
  
### <a name="parameters"></a>参数  
 `ulProgress`  
 指示相对于所示的预期最大绑定操作的当前进度`ulProgressMax`。  
  
 `ulProgressMax`  
 指示预期的最大值的`ulProgress`到调用的持续时间为`OnProgress`对于此操作。  
  
 `ulStatusCode`  
 提供有关进度的绑定操作的其他信息。 有效的值，将从`BINDSTATUS`枚举。 有关可能的值，请参阅备注。  
  
 `szStatusText`  
 有关当前过程，具体取决于的值的信息`ulStatusCode`。 有关可能的值，请参阅备注。  
  
### <a name="remarks"></a>备注  
 可能的值有`ulStatusCode`(和`szStatusText`每个值) 是：  
  
 **BINDSTATUS_FINDINGRESOURCE**  
 绑定操作发现包含对象或绑定到的存储资源。 `szStatusText`提供要搜索的资源的显示名称为 (例如，"www.microsoft.com")。  
  
 **BINDSTATUS_CONNECTING**  
 绑定操作正在连接到包含对象或绑定到的存储资源。 `szStatusText`提供 （例如，IP 地址） 连接到的资源的显示名称。  
  
 **BINDSTATUS_SENDINGREQUEST**  
 绑定操作正在请求的对象或绑定到的存储。 `szStatusText`提供对象 （例如，文件名） 的显示名称。  
  
 **BINDSTATUS_REDIRECTING**  
 绑定操作已被重定向到不同的数据位置。 `szStatusText`提供新的数据位置的显示名称。  
  
 **BINDSTATUS_USINGCACHEDCOPY**  
 绑定操作正在检索请求的对象或存储缓存副本。 `szStatusText`是**NULL**。  
  
 **BINDSTATUS_BEGINDOWNLOADDATA**  
 绑定操作已开始接收要绑定到的存储的对象。 `szStatusText`提供的数据位置的显示名称。  
  
 **BINDSTATUS_DOWNLOADINGDATA**  
 绑定操作将继续接收要绑定到的存储的对象。 `szStatusText`提供的数据位置的显示名称。  
  
 **BINDSTATUS_ENDDOWNLOADDATA**  
 在绑定操作完成后接收的对象或绑定到的存储。 `szStatusText`提供的数据位置的显示名称。  
  
 **BINDSTATUS_CLASSIDAVAILABLE**  
 要绑定到对象的实例是只是关于创建。 `szStatusText`提供允许客户端的机会取消绑定操作中，如果需要字符串格式中的新对象的 CLSID。  
  
##  <a name="onstartbinding"></a>CAsyncMonikerFile::OnStartBinding  
 重写此函数在执行操作时绑定正在启动你派生类中。  
  
```  
virtual void OnStartBinding();
```  
  
### <a name="remarks"></a>备注  
 由名字对象返回调用此函数。 默认实现不执行任何操作。  
  
##  <a name="onstopbinding"></a>CAsyncMonikerFile::OnStopBinding  
 调用由名字对象绑定操作的末尾。  
  
```  
virtual void OnStopBinding(HRESULT hresult, LPCTSTR szError);
```  
  
### <a name="parameters"></a>参数  
 `hresult`  
 `HRESULT` ，它是错误或警告值。  
  
 *szErrort*  
 描述错误的字符字符串。  
  
### <a name="remarks"></a>备注  
 重写此函数可在传输已停止时执行操作。 默认情况下，函数会释放`IBinding`。  
  
 有关的说明`IBinding`接口，请参阅 Windows SDK。  
  
##  <a name="open"></a>CAsyncMonikerFile::Open  
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
 `lpszURL`  
 指向要以异步方式打开以文件的指针。 文件可以是任何有效的 URL 或文件名。  
  
 `pError`  
 指向文件异常的指针。 发生错误，必须先将它设置为可能的原因。  
  
 `pMoniker`  
 指向异步名字对象接口的指针`IMoniker`，是组合使用可以检索文档的名字对象的精确名字对象**IOleClientSite::GetMoniker (** *OLEWHICHMK_容器* **)**，并创建从路径名的名字对象。 控件可以使用此标记将绑定，但这不是该控件应将保存的名字对象。  
  
 *pBindHost*  
 指向的指针`IBindHost`将用于从可能相对路径名创建标记的接口。 如果绑定主机无效或未提供名字对象，调用将默认为**打开 (** `lpszFileName` **，**`pError`**)**。 有关的说明`IBindHost`接口，请参阅 Windows SDK。  
  
 `pServiceProvider`  
 指向 `IServiceProvider` 接口的指针。 如果服务提供程序无效或无法提供的服务`IBindHost`，调用默认为**打开 (** `lpszFileName` **，**`pError`**)**。  
  
 *pUnknown*  
 指向的指针**IUnknown**接口。 如果`IServiceProvider`找到，则对的函数查询`IBindHost`。 如果服务提供程序无效或无法提供的服务`IBindHost`，调用默认为**打开 (** `lpszFileName` **，**`pError`**)**。  
  
### <a name="return-value"></a>返回值  
 如果成功，则打开该文件则为非 0否则为 0。  
  
### <a name="remarks"></a>备注  
 此调用启动绑定过程。  
  
 你可以使用 URL 或文件名`lpszURL`参数。 例如:  
  
 [!code-cpp[NVC_MFCWinInet#6](../../mfc/codesnippet/cpp/casyncmonikerfile-class_2.cpp)]  
  
 - 或 -  
  
 [!code-cpp[NVC_MFCWinInet#7](../../mfc/codesnippet/cpp/casyncmonikerfile-class_3.cpp)]  
  
## <a name="see-also"></a>请参阅  
 [CMonikerFile 类](../../mfc/reference/cmonikerfile-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CMonikerFile 类](../../mfc/reference/cmonikerfile-class.md)   
 [CDataPathProperty 类](../../mfc/reference/cdatapathproperty-class.md)
