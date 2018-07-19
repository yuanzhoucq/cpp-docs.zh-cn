---
title: CAsyncMonikerFile 类 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 31d16279b4de6c0cca0d37161a37ce5e39b85b7b
ms.sourcegitcommit: 6408139d5f5ff8928f056bde93d20eecb3520361
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2018
ms.locfileid: "37339342"
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
|[CAsyncMonikerFile::GetBinding](#getbinding)|检索指向绑定的异步传输。|  
|[CAsyncMonikerFile::GetFormatEtc](#getformatetc)|检索流中的数据的格式。|  
|[CAsyncMonikerFile::Open](#open)|以异步方式打开文件。|  
  
### <a name="protected-methods"></a>受保护的方法  
  
|名称|描述|  
|----------|-----------------|  
|[CAsyncMonikerFile::CreateBindStatusCallback](#createbindstatuscallback)|创建 COM 对象实现`IBindStatusCallback`。|  
|[CAsyncMonikerFile::GetBindInfo](#getbindinfo)|调用由 OLE 系统库上的 bind，以便创建类型的请求信息。|  
|[CAsyncMonikerFile::GetPriority](#getpriority)|调用由 OLE 系统库来获取绑定的优先级。|  
|[CAsyncMonikerFile::OnDataAvailable](#ondataavailable)|调用以将其异步绑定操作期间提供给客户端提供数据。|  
|[CAsyncMonikerFile::OnLowResource](#onlowresource)|当资源不足时调用。|  
|[CAsyncMonikerFile::OnProgress](#onprogress)|调用以指示数据下载进程上的进度。|  
|[CAsyncMonikerFile::OnStartBinding](#onstartbinding)|当绑定启动时调用。|  
|[CAsyncMonikerFile::OnStopBinding](#onstopbinding)|当异步传输已停止时调用。|  
  
## <a name="remarks"></a>备注  
 派生自[CMonikerFile](../../mfc/reference/cmonikerfile-class.md)，后者又派生自[COleStreamFile](../../mfc/reference/colestreamfile-class.md)，`CAsyncMonikerFile`使用[IMoniker](http://msdn.microsoft.com/library/windows/desktop/ms679705)接口来访问任何数据的流以异步方式，包括从 URL 异步加载文件。 文件可以是 ActiveX 控件的数据路径属性。  
  
 异步名字对象主要是在连接 Internet 的应用程序和 ActiveX 控件中用于文件传输过程中提供响应式用户界面。 最好的例子是使用[CDataPathProperty](../../mfc/reference/cdatapathproperty-class.md)为 ActiveX 控件提供异步属性。 `CDataPathProperty`对象将重复进行回调以在较长时间的属性交换过程中指示新数据的可用性。  
  
 有关如何在 Internet 应用程序中使用异步名字对象和 ActiveX 控件的详细信息，请参阅以下文章：  
  
- [异步名字对象 Internet 前几个步骤：](../../mfc/asynchronous-monikers-on-the-internet.md)  
  
- [Internet 前几个步骤： ActiveX 控件](../../mfc/activex-controls-on-the-internet.md)  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CFile](../../mfc/reference/cfile-class.md)  
  
 [COleStreamFile](../../mfc/reference/colestreamfile-class.md)  
  
 [CMonikerFile](../../mfc/reference/cmonikerfile-class.md)  
  
 `CAsyncMonikerFile`  
  
## <a name="requirements"></a>要求  
 **标头：** afxole.h  
  
##  <a name="casyncmonikerfile"></a>  CAsyncMonikerFile::CAsyncMonikerFile  
 构造 `CAsyncMonikerFile` 对象。  
  
```  
CAsyncMonikerFile();
```  
  
### <a name="remarks"></a>备注  
 它不会创建`IBindHost`接口。 `IBindHost` 仅当你提供在使用`Open`成员函数。  
  
 有关的说明`IBindHost`接口，请参阅 Windows SDK。  
  
##  <a name="close"></a>  CAsyncMonikerFile::Close  
 调用此函数来关闭并释放所有资源。  
  
```  
virtual void Close();
```  
  
### <a name="remarks"></a>备注  
 可以在未打开或已关闭的文件上调用。  
  
##  <a name="createbindstatuscallback"></a>  CAsyncMonikerFile::CreateBindStatusCallback  
 创建 COM 对象实现`IBindStatusCallback`。  
  
```  
virtual IUnknown* CreateBindStatusCallback(IUnknown* pUnkControlling);
```  
  
### <a name="parameters"></a>参数  
 *pUnkControlling*  
 指向控制未知的 (外部`IUnknown`) 或如果未使用聚合，则为 NULL。  
  
### <a name="return-value"></a>返回值  
 如果*pUnkControlling*不为 NULL，该函数返回一个指向内部`IUnknown`新的 COM 对象支持`IBindStatusCallback`。 如果`pUnkControlling`为 NULL，该函数返回一个指向`IUnknown`新的 COM 对象支持`IBindStatusCallback`。  
  
### <a name="remarks"></a>备注  
 `CAsyncMonikerFile` 需要实现一个 COM 对象`IBindStatusCallback`。 MFC 实现此类对象，并且它是聚合。 您可以重写`CreateBindStatusCallback`返回您自己的 COM 对象。 COM 对象可以通过调用聚合 MFC 的实现`CreateBindStatusCallback`与 COM 对象控制未知。 使用实现 COM 对象`CCmdTarget`COM 支持可以检索控制未知使用`CCmdTarget::GetControllingUnknown`。  
  
 或者，您的 COM 对象可以委托到 MFC 的实现通过调用`CreateBindStatusCallback( NULL )`。  
  
 [CAsyncMonikerFile::Open](#open)调用`CreateBindStatusCallback`。  
  
 有关异步名字对象和异步绑定的详细信息，请参阅[IBindStatusCallback](http://msdn.microsoft.com/library/ie/ms775060)接口并[如何异步绑定和存储工作](http://msdn.microsoft.com/library/windows/desktop/aa379152)。 有关聚合的讨论，请参阅[聚合](http://msdn.microsoft.com/library/windows/desktop/ms686558)。 所有三个主题，请在 Windows SDK 中。  
  
##  <a name="getbindinfo"></a>  CAsyncMonikerFile::GetBindInfo  
 从异步名字对象的客户端向它想要绑定的异步名字对象调用。  
  
```  
virtual DWORD GetBindInfo() const;  
```  
  
### <a name="return-value"></a>返回值  
 检索的设置`IBindStatusCallBack`。 有关的说明`IBindStatusCallback`接口，请参阅 Windows SDK。  
  
### <a name="remarks"></a>备注  
 默认实现设置要是异步的以使用存储介质 （流），并使用数据推送模型的绑定。 如果你想要更改绑定的行为来覆盖此函数。  
  
 执行此操作的原因之一是使用数据拉取模型，而不数据推送模型绑定。 在数据拉取模型中，客户端驱动器绑定操作，名字对象只提供了数据向客户端时读取它。 在数据推送模型中，名字对象驱动器异步绑定操作，并持续在新数据可用时通知客户端。  
  
##  <a name="getbinding"></a>  CAsyncMonikerFile::GetBinding  
 调用此函数可检索到异步传输绑定的指针。  
  
```  
IBinding* GetBinding() const;  
```  
  
### <a name="return-value"></a>返回值  
 一个指向`IBinding`接口提供异步传输开始时。 不能成为以异步方式返回 NULL，如果出于任何原因导致传输。  
  
### <a name="remarks"></a>备注  
 这允许你控制的数据传输过程通过`IBinding`接口，例如，使用`IBinding::Abort`， `IBinding::Pause`，和`IBinding::Resume`。  
  
 有关的说明`IBinding`接口，请参阅 Windows SDK。  
  
##  <a name="getformatetc"></a>  CAsyncMonikerFile::GetFormatEtc  
 调用此函数可检索的流中的数据格式。  
  
```  
FORMATETC* GetFormatEtc() const;  
```  
  
### <a name="return-value"></a>返回值  
 指向 Windows 结构的指针[FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177)为当前打开的流。 如果名字对象没有绑定，如果不是异步的或者未开始异步操作返回 NULL。  
  
##  <a name="getpriority"></a>  CAsyncMonikerFile::GetPriority  
 调用异步名字对象的客户端从绑定进程开始接收为线程指定绑定操作的优先级。  
  
```  
virtual LONG GetPriority() const;  
```  
  
### <a name="return-value"></a>返回值  
 异步传输会发生的优先级。 一个标准的线程优先级标志： THREAD_PRIORITY_ABOVE_NORMAL、 THREAD_PRIORITY_BELOW_NORMAL、 THREAD_PRIORITY_HIGHEST、 THREAD_PRIORITY_IDLE、 THREAD_PRIORITY_LOWEST、 THREAD_PRIORITY_NORMAL 和 THREAD_PRIORITY_TIME_CRITICAL。 请参阅 Windows 函数[SetThreadPriority](http://msdn.microsoft.com/library/windows/desktop/ms686277)有关这些值的说明。  
  
### <a name="remarks"></a>备注  
 `GetPriority` 应不直接调用。 THREAD_PRIORITY_NORMAL 返回的默认实现。  
  
##  <a name="ondataavailable"></a>  CAsyncMonikerFile::OnDataAvailable  
 异步名字对象调用`OnDataAvailable`变得可用，可在客户端中提供数据，在异步绑定操作。  
  
```  
virtual void OnDataAvailable(DWORD dwSize, DWORD bscfFlag);
```  
  
### <a name="parameters"></a>参数  
 *dwSize*  
 数据可用后的绑定的开始累积量 （以字节为单位）。 可以是零，表示没有与操作相关的数据量或特定数量变得可用。  
  
 *bscfFlag*  
 一个 BSCF 枚举值。 可以是一个或多个以下值：  
  
- BSCF_FIRSTDATANOTIFICATION 标识首次调用`OnDataAvailable`给定的绑定操作。  
  
- BSCF_INTERMEDIATEDATANOTIFICATION 标识对的中间调用`OnDataAvailable`绑定操作。  
  
- BSCF_LASTDATANOTIFICATION 标识上次调用`OnDataAvailable`绑定操作。  
  
### <a name="remarks"></a>备注  
 此函数的默认实现不执行任何操作。 请参阅有关的示例实现下面的示例。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCWinInet#5](../../mfc/codesnippet/cpp/casyncmonikerfile-class_1.cpp)]  
  
##  <a name="onlowresource"></a>  CAsyncMonikerFile::OnLowResource  
 当资源不足时，调用由该名字。  
  
```  
virtual void OnLowResource();
```  
  
### <a name="remarks"></a>备注  
 默认实现将调用`GetBinding( )-> Abort( )`。  
  
##  <a name="onprogress"></a>  CAsyncMonikerFile::OnProgress  
 由重复要指示此绑定操作，通常在合理的时间间隔内较长的操作的当前进度的名字对象调用。  
  
```  
virtual void OnProgress(
    ULONG ulProgress,  
    ULONG ulProgressMax,  
    ULONG ulStatusCode,  
    LPCTSTR szStatusText);
```  
  
### <a name="parameters"></a>参数  
 *ulProgress*  
 指示绑定操作相对于所示的预期最大值的当前进度*ulProgressMax*。  
  
 *ulProgressMax*  
 指示的预期最大值*ulProgress*的调用的持续时间`OnProgress`对于此操作。  
  
 *ulStatusCode*  
 提供有关进度的绑定操作的其他信息。 有效的值取自`BINDSTATUS`枚举。 有关可能的值，请参阅备注。  
  
 *szStatusText*  
 当前正在进行，具体取决于值有关的信息*ulStatusCode*。 有关可能的值，请参阅备注。  
  
### <a name="remarks"></a>备注  
 可能的值*ulStatusCode* (与*szStatusText*每个值) 是：  
  
 BINDSTATUS_FINDINGRESOURCE  
 绑定操作查找包含的对象或绑定到的存储空间的资源。 *SzStatusText*提供要搜索的资源的显示名称为 (例如，"www.microsoft.com")。  
  
 BINDSTATUS_CONNECTING  
 绑定操作连接到包含的对象或绑定到的存储空间的资源。 *SzStatusText*提供 （例如 IP 地址） 连接到的资源的显示名称。  
  
 BINDSTATUS_SENDINGREQUEST  
 绑定操作正在请求的对象或绑定到的存储空间。 *SzStatusText*提供对象 （例如，文件名称） 的显示名称。  
  
 BINDSTATUS_REDIRECTING  
 绑定操作已被重定向到不同的数据位置。 *SzStatusText*提供新的数据位置的显示名称。  
  
 BINDSTATUS_USINGCACHEDCOPY  
 绑定操作从缓存副本中检索请求的对象或存储。 *SzStatusText*为 NULL。  
  
 BINDSTATUS_BEGINDOWNLOADDATA  
 绑定操作已开始接收的对象或绑定到的存储空间。 *SzStatusText*提供的数据位置的显示名称。  
  
 BINDSTATUS_DOWNLOADINGDATA  
 绑定操作将继续接收的对象或绑定到的存储空间。 *SzStatusText*提供的数据位置的显示名称。  
  
 BINDSTATUS_ENDDOWNLOADDATA  
 在绑定操作完成后收到的对象或绑定到的存储空间。 *SzStatusText*提供的数据位置的显示名称。  
  
 BINDSTATUS_CLASSIDAVAILABLE  
 绑定到的实例是对象的进行创建。 *SzStatusText*提供允许客户端有机会取消绑定操作中，如果所需的字符串格式的新对象的 CLSID。  
  
##  <a name="onstartbinding"></a>  CAsyncMonikerFile::OnStartBinding  
 重写此函数来执行操作，当绑定启动时在派生类中。  
  
```  
virtual void OnStartBinding();
```  
  
### <a name="remarks"></a>备注  
 调用此函数是返回名字对象。 默认实现不执行任何操作。  
  
##  <a name="onstopbinding"></a>  CAsyncMonikerFile::OnStopBinding  
 调用绑定操作结束时的名字对象。  
  
```  
virtual void OnStopBinding(HRESULT hresult, LPCTSTR szError);
```  
  
### <a name="parameters"></a>参数  
 *hresult*  
 HRESULT 的错误或警告值。  
  
 *szErrort*  
 描述错误的字符字符串。  
  
### <a name="remarks"></a>备注  
 重写此函数可传输停止时执行操作。 默认情况下，该函数会释放`IBinding`。  
  
 有关的说明`IBinding`接口，请参阅 Windows SDK。  
  
##  <a name="open"></a>  CAsyncMonikerFile::Open  
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
 *lpszURL*  
 指向要以异步方式打开文件的指针。 该文件可以是任何有效的 URL 或文件名。  
  
 *pError*  
 指向文件异常的指针。 发生错误，必须先将它设置为原因。  
  
 *pMoniker*  
 对异步名字对象接口指针`IMoniker`，精确的名字对象的组合的文档的名字对象，后者可以检索与`IOleClientSite::GetMoniker(OLEWHICHMK_CONTAINER)`，并从路径名称创建一个名字对象。 控件可以使用此名字对象进行绑定，但这不是该控件应将保存的名字对象。  
  
 *pBindHost*  
 一个指向`IBindHost`将用于创建从潜在的相对路径名的名字对象的接口。 如果绑定主机无效或未提供一个名字对象，该调用将默认为`Open(lpszFileName,pError)`。 有关的说明`IBindHost`接口，请参阅 Windows SDK。  
  
 *pServiceProvider*  
 指向 `IServiceProvider` 接口的指针。 如果服务提供程序无效或无法提供的服务`IBindHost`，在调用默认为`Open(lpszFileName,pError)`。  
  
 *pUnknown*  
 指向 `IUnknown` 接口的指针。 如果`IServiceProvider`找到，则该函数查询`IBindHost`。 如果服务提供程序无效或无法提供的服务`IBindHost`，在调用默认为`Open(lpszFileName,pError)`。  
  
### <a name="return-value"></a>返回值  
 如果成功，则打开该文件，非零值否则为 0。  
  
### <a name="remarks"></a>备注  
 此调用启动绑定过程。  
  
 可以使用某一 URL 或者文件名*lpszURL*参数。 例如：  
  
 [!code-cpp[NVC_MFCWinInet#6](../../mfc/codesnippet/cpp/casyncmonikerfile-class_2.cpp)]  
  
 - 或 -  
  
 [!code-cpp[NVC_MFCWinInet#7](../../mfc/codesnippet/cpp/casyncmonikerfile-class_3.cpp)]  
  
## <a name="see-also"></a>请参阅  
 [CMonikerFile 类](../../mfc/reference/cmonikerfile-class.md)   
 [层次结构图表](../../mfc/hierarchy-chart.md)   
 [CMonikerFile 类](../../mfc/reference/cmonikerfile-class.md)   
 [CDataPathProperty 类](../../mfc/reference/cdatapathproperty-class.md)
