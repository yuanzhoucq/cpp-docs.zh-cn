---
title: "CAsyncMonikerFile 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CAsyncMonikerFile
dev_langs:
- C++
helpviewer_keywords:
- ActiveX controls [C++], asynchronous
- OLE controls [C++], asynchronous
- monikers [C++], MFC
- asynchronous controls [C++]
- CAsyncMonikerFile class
- IMoniker interface, binding
ms.assetid: 17378b66-a49a-4b67-88e3-7756ad26a2fc
caps.latest.revision: 23
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
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: eb8727e6fe884c98fe010beab072fb7268f2e2c4
ms.lasthandoff: 02/24/2017

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
|[CAsyncMonikerFile::CAsyncMonikerFile](#casyncmonikerfile)|构造 `CAsyncMonikerFile` 对象。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|说明|  
|----------|-----------------|  
|[CAsyncMonikerFile::Close](#close)|关闭并释放所有资源。|  
|[CAsyncMonikerFile::GetBinding](#getbinding)|检索指向异步传输绑定。|  
|[CAsyncMonikerFile::GetFormatEtc](#getformatetc)|获取流中的数据的格式。|  
|[CAsyncMonikerFile::Open](#open)|以异步方式打开的文件。|  
  
### <a name="protected-methods"></a>受保护的方法  
  
|名称|说明|  
|----------|-----------------|  
|[CAsyncMonikerFile::CreateBindStatusCallback](#createbindstatuscallback)|创建 COM 对象实现`IBindStatusCallback`。|  
|[CAsyncMonikerFile::GetBindInfo](#getbindinfo)|由 OLE 系统库请求上的信息来创建绑定的类型调用。|  
|[CAsyncMonikerFile::GetPriority](#getpriority)|由 OLE 系统库来获取绑定的优先级调用。|  
|[CAsyncMonikerFile::OnDataAvailable](#ondataavailable)|调用以根据其才可供客户端异步绑定期间提供数据。|  
|[CAsyncMonikerFile::OnLowResource](#onlowresource)|调用时资源不足。|  
|[CAsyncMonikerFile::OnProgress](#onprogress)|调用以指示数据下载过程的进度。|  
|[CAsyncMonikerFile::OnStartBinding](#onstartbinding)|当绑定正在启动时调用。|  
|[CAsyncMonikerFile::OnStopBinding](#onstopbinding)|当异步传输已停止时调用。|  
  
## <a name="remarks"></a>备注  
 派生自[CMonikerFile](../../mfc/reference/cmonikerfile-class.md)，后者又派生自[COleStreamFile](../../mfc/reference/colestreamfile-class.md)，`CAsyncMonikerFile`使用[IMoniker](http://msdn.microsoft.com/library/windows/desktop/ms679705)接口来以异步方式访问任何数据的流包括从 URL 异步加载的文件。 这些文件可以是 ActiveX 控件的数据路径属性。  
  
 异步名字对象主要是在启用 Internet 的应用程序和 ActiveX 控件中用于在文件传输过程中提供响应迅速的用户界面。 明显的例子是使用[CDataPathProperty](../../mfc/reference/cdatapathproperty-class.md)为 ActiveX 控件提供异步属性。 `CDataPathProperty`对象重复获得一个回调，以在长时间的属性交换过程中指示新数据的可用性。  
  
 有关如何在 Internet 应用程序中使用异步名字对象和 ActiveX 控件的详细信息，请参阅以下文章︰  
  
- [Internet 前几个步骤︰ 异步名字对象](../../mfc/asynchronous-monikers-on-the-internet.md)  
  
- [Internet 前几个步骤︰ ActiveX 控件](../../mfc/activex-controls-on-the-internet.md)  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CFile](../../mfc/reference/cfile-class.md)  
  
 [COleStreamFile](../../mfc/reference/colestreamfile-class.md)  
  
 [CMonikerFile](../../mfc/reference/cmonikerfile-class.md)  
  
 `CAsyncMonikerFile`  
  
## <a name="requirements"></a>要求  
 **标头︰** afxole.h  
  
##  <a name="a-namecasyncmonikerfilea--casyncmonikerfilecasyncmonikerfile"></a><a name="casyncmonikerfile"></a>CAsyncMonikerFile::CAsyncMonikerFile  
 构造 `CAsyncMonikerFile` 对象。  
  
```  
CAsyncMonikerFile();
```  
  
### <a name="remarks"></a>备注  
 它不会创建`IBindHost`接口。 `IBindHost`仅当您为其在提供时，才使用**打开**成员函数。  
  
 有关的说明`IBindHost`接口，请参阅[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-nameclosea--casyncmonikerfileclose"></a><a name="close"></a>CAsyncMonikerFile::Close  
 调用此函数可关闭并释放所有资源。  
  
```  
virtual void Close();
```  
  
### <a name="remarks"></a>备注  
 可以对未打开或已关闭的文件调用。  
  
##  <a name="a-namecreatebindstatuscallbacka--casyncmonikerfilecreatebindstatuscallback"></a><a name="createbindstatuscallback"></a>CAsyncMonikerFile::CreateBindStatusCallback  
 创建 COM 对象实现`IBindStatusCallback`。  
  
```  
virtual IUnknown* CreateBindStatusCallback(IUnknown* pUnkControlling);
```  
  
### <a name="parameters"></a>参数  
 `pUnkControlling`  
 为控制未知的指针 (外部**IUnknown**) 或**NULL**如果未使用聚合。  
  
### <a name="return-value"></a>返回值  
 如果`pUnkControlling`不是**NULL**，该函数返回一个指向内部**IUnknown**上新的 COM 对象支持`IBindStatusCallback`。 如果`pUnkControlling`是**NULL**，该函数返回一个指向**IUnknown**上新的 COM 对象支持`IBindStatusCallback`。  
  
### <a name="remarks"></a>备注  
 `CAsyncMonikerFile`需要实现一个 COM 对象`IBindStatusCallback`。 MFC 实现此类对象，并是聚合。 您可以重写`CreateBindStatusCallback`返回您自己的 COM 对象。 您的 COM 对象可以通过调用聚合 MFC 的实现`CreateBindStatusCallback`与您的 COM 对象控制未知。 使用实现的 COM 对象`CCmdTarget`COM 支持可以检索控制未知使用**CCmdTarget::GetControllingUnknown**。  
  
 或者，您的 COM 对象可以通过将委托到 MFC 的实现调用**CreateBindStatusCallback (NULL)**。  
  
 [CAsyncMonikerFile::Open](#open)调用`CreateBindStatusCallback`。  
  
 异步名字对象异步绑定的更多信息，请参阅[IBindStatusCallback](http://msdn.microsoft.com/library/ie/ms775060)接口和[如何异步绑定和存储工作](http://msdn.microsoft.com/library/windows/desktop/aa379152)。 有关聚合的讨论，请参阅[聚合](http://msdn.microsoft.com/library/windows/desktop/ms686558)。 所有三个主题位于[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-namegetbindinfoa--casyncmonikerfilegetbindinfo"></a><a name="getbindinfo"></a>CAsyncMonikerFile::GetBindInfo  
 从异步名字对象的客户端能够告诉它想要将绑定的异步名字对象调用。  
  
```  
virtual DWORD GetBindInfo() const;  
```  
  
### <a name="return-value"></a>返回值  
 检索的设置**IBindStatusCallBack**。 有关的说明`IBindStatusCallback`接口，请参阅[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="remarks"></a>备注  
 默认实现设置的绑定是异步的以使用存储媒体 （流），并使用数据推送模型。 如果你想要更改绑定的行为，重写此函数。  
  
 这么做的一个原因是将绑定而不数据推送模型使用的数据提取模型。 在数据拉入模型中，客户端驱动器绑定操作，并标记仅提供数据给客户端读取它时。 在数据推送模型中，名字对象硬盘异步绑定操作和不断地在新数据可用时通知客户端。  
  
##  <a name="a-namegetbindinga--casyncmonikerfilegetbinding"></a><a name="getbinding"></a>CAsyncMonikerFile::GetBinding  
 调用此函数可检索一个指向异步传输绑定。  
  
```  
IBinding* GetBinding() const;  
```  
  
### <a name="return-value"></a>返回值  
 一个指向`IBinding`异步传输开始时提供的接口。 返回**NULL**如果出于任何原因传输不能将其变为异步。  
  
### <a name="remarks"></a>备注  
 这使您能够控制的数据传输进程通过`IBinding`接口，例如，与**IBinding::Abort**， **IBinding::Pause**，和**IBinding::Resume**。  
  
 有关的说明`IBinding`接口，请参阅[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-namegetformatetca--casyncmonikerfilegetformatetc"></a><a name="getformatetc"></a>CAsyncMonikerFile::GetFormatEtc  
 调用此函数可检索的流中的数据格式。  
  
```  
FORMATETC* GetFormatEtc() const;  
```  
  
### <a name="return-value"></a>返回值  
 指向 Windows 结构的指针[FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177)为当前打开的流。 返回**NULL**如果标记没有绑定，如果不是异步的或者如果未开始异步操作。  
  
##  <a name="a-namegetprioritya--casyncmonikerfilegetpriority"></a><a name="getpriority"></a>CAsyncMonikerFile::GetPriority  
 从客户端的异步名字对象调用在绑定进程启动时接收到的线程绑定操作所指定的优先级。  
  
```  
virtual LONG GetPriority() const;  
```  
  
### <a name="return-value"></a>返回值  
 从该处异步传输会在发生与的优先级。 标准线程优先级标记之一︰ **THREAD_PRIORITY_ABOVE_NORMAL**， **THREAD_PRIORITY_BELOW_NORMAL**， **THREAD_PRIORITY_HIGHEST**， **THREAD_PRIORITY_IDLE**， **THREAD_PRIORITY_LOWEST**， **THREAD_PRIORITY_NORMAL**，和**THREAD_PRIORITY_TIME_CRITICAL**。 请参阅 Windows 函数[SetThreadPriority](http://msdn.microsoft.com/library/windows/desktop/ms686277)有关这些值的说明。  
  
### <a name="remarks"></a>备注  
 `GetPriority`不应进行直接调用。 **THREAD_PRIORITY_NORMAL**的默认实现返回。  
  
##  <a name="a-nameondataavailablea--casyncmonikerfileondataavailable"></a><a name="ondataavailable"></a>CAsyncMonikerFile::OnDataAvailable  
 异步名字对象调用`OnDataAvailable`若要提供给客户端数据，变得可用，在异步过程将绑定操作。  
  
```  
virtual void OnDataAvailable(DWORD dwSize, DWORD bscfFlag);
```  
  
### <a name="parameters"></a>参数  
 `dwSize`  
 可用的绑定开始后的数据累积量 （以字节为单位）。 可以是零，表示的数据量不针对此操作，或任何特定量变为可用。  
  
 *bscfFlag*  
 一个**BSCF**枚举值。 可以是一个或多个下列值︰  
  
- **BSCF_FIRSTDATANOTIFICATION**标识首次调用`OnDataAvailable`给定的绑定操作。  
  
- **BSCF_INTERMEDIATEDATANOTIFICATION**标识为一个中间调用`OnDataAvailable`绑定操作。  
  
- **BSCF_LASTDATANOTIFICATION**标识到最后一次调用`OnDataAvailable`绑定操作。  
  
### <a name="remarks"></a>备注  
 此函数的默认实现不执行任何操作。 请参阅有关示例实现下面的示例。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCWinInet #&5;](../../mfc/codesnippet/cpp/casyncmonikerfile-class_1.cpp)]  
  
##  <a name="a-nameonlowresourcea--casyncmonikerfileonlowresource"></a><a name="onlowresource"></a>CAsyncMonikerFile::OnLowResource  
 当资源不足时，调用由名字对象。  
  
```  
virtual void OnLowResource();
```  
  
### <a name="remarks"></a>备注  
 默认实现调用`GetBinding( )-> Abort( )`。  
  
##  <a name="a-nameonprogressa--casyncmonikerfileonprogress"></a><a name="onprogress"></a>CAsyncMonikerFile::OnProgress  
 调用由重复以指示此绑定操作，通常在合理时间间隔内较长的操作的当前进度的名字对象。  
  
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
 指示的预期最大值`ulProgress`到调用的持续时间为`OnProgress`对于此操作。  
  
 `ulStatusCode`  
 提供有关进度的绑定操作的其他信息。 有效的值取自`BINDSTATUS`枚举。 有关可能的值，请参阅备注。  
  
 `szStatusText`  
 当前进度，具体取决于值有关的信息`ulStatusCode`。 有关可能的值，请参阅备注。  
  
### <a name="remarks"></a>备注  
 可能的值有`ulStatusCode`(和`szStatusText`为每个值) 是︰  
  
 **BINDSTATUS_FINDINGRESOURCE**  
 绑定操作查找包含的对象或绑定到的存储资源。 `szStatusText`提供要搜索的资源的显示名称为 (例如，"www.microsoft.com")。  
  
 **BINDSTATUS_CONNECTING**  
 绑定操作连接到包含对象或绑定到的存储资源。 `szStatusText`提供 （例如 IP 地址） 连接到的资源的显示名称。  
  
 **BINDSTATUS_SENDINGREQUEST**  
 绑定操作正在请求的对象或绑定到的存储。 `szStatusText`提供对象 （例如，文件名称） 的显示名称。  
  
 **BINDSTATUS_REDIRECTING**  
 绑定操作已被重定向到不同的数据位置。 `szStatusText`提供新的数据位置的显示名称。  
  
 **BINDSTATUS_USINGCACHEDCOPY**  
 绑定操作从缓存的副本检索请求的对象或存储。 The `szStatusText` is **NULL**.  
  
 **BINDSTATUS_BEGINDOWNLOADDATA**  
 绑定操作已开始接收对象或绑定到的存储。 `szStatusText`提供的数据位置的显示名称。  
  
 **BINDSTATUS_DOWNLOADINGDATA**  
 绑定操作将继续接收对象或绑定到的存储。 `szStatusText`提供的数据位置的显示名称。  
  
 **BINDSTATUS_ENDDOWNLOADDATA**  
 绑定操作已完成接收的对象或绑定到的存储。 `szStatusText`提供的数据位置的显示名称。  
  
 **BINDSTATUS_CLASSIDAVAILABLE**  
 绑定到的实例是对象的几乎创建。 `szStatusText`提供允许客户端取消绑定操作的机会，如果所需的字符串格式中的新对象的 CLSID。  
  
##  <a name="a-nameonstartbindinga--casyncmonikerfileonstartbinding"></a><a name="onstartbinding"></a>CAsyncMonikerFile::OnStartBinding  
 重写此函数在对派生的类，以便绑定正在启动时执行操作。  
  
```  
virtual void OnStartBinding();
```  
  
### <a name="remarks"></a>备注  
 名字对象后调用此函数。 默认实现不执行任何操作。  
  
##  <a name="a-nameonstopbindinga--casyncmonikerfileonstopbinding"></a><a name="onstopbinding"></a>CAsyncMonikerFile::OnStopBinding  
 调用由绑定操作的末尾的名字对象。  
  
```  
virtual void OnStopBinding(HRESULT hresult, LPCTSTR szError);
```  
  
### <a name="parameters"></a>参数  
 `hresult`  
 `HRESULT` ，它是错误或警告值。  
  
 *szErrort*  
 描述错误的字符字符串。  
  
### <a name="remarks"></a>备注  
 重写此函数可在传输已停止时执行操作。 默认情况下，该函数会释放`IBinding`。  
  
 有关的说明`IBinding`接口，请参阅[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-nameopena--casyncmonikerfileopen"></a><a name="open"></a>CAsyncMonikerFile::Open  
 调用此成员函数以异步方式打开的文件。  
  
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
 指向要以异步方式打开文件的指针。 该文件可以是任何有效的 URL 或文件名。  
  
 `pError`  
 一个指向文件例外。 如果出现错误，必须先将它设置为原因。  
  
 `pMoniker`  
 对异步名字对象接口的指针`IMoniker`，精确的名字对象是使用可以检索文档的名字对象的组合**IOleClientSite::GetMoniker (** *OLEWHICHMK_CONTAINER* **)**，并从路径名称创建一个名字对象。 控件可以使用此名字对象进行绑定，但这不是该控件应将保存的名字对象。  
  
 *pBindHost*  
 一个指向`IBindHost`将用于从潜在的相对路径名创建标记的接口。 如果绑定主机无效或未提供名字对象，该调用将默认为**打开 (** `lpszFileName` **，**`pError`**)**。 有关的说明`IBindHost`接口，请参阅[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
 `pServiceProvider`  
 一个指向`IServiceProvider`接口。 如果服务提供程序无效或无法提供的服务`IBindHost`，调用默认为**打开 (** `lpszFileName` **，**`pError`**)**。  
  
 *pUnknown*  
 一个指向**IUnknown**接口。 如果`IServiceProvider`找到，则函数查询`IBindHost`。 如果服务提供程序无效或无法提供的服务`IBindHost`，调用默认为**打开 (** `lpszFileName` **，**`pError`**)**。  
  
### <a name="return-value"></a>返回值  
 如果成功，则打开该文件，则为非否则为 0。  
  
### <a name="remarks"></a>备注  
 此调用启动绑定过程。  
  
 可以使用的 URL 或文件名`lpszURL`参数。 例如：  
  
 [!code-cpp[NVC_MFCWinInet #&6;](../../mfc/codesnippet/cpp/casyncmonikerfile-class_2.cpp)]  
  
 - 或 -  
  
 [!code-cpp[NVC_MFCWinInet #&7;](../../mfc/codesnippet/cpp/casyncmonikerfile-class_3.cpp)]  
  
## <a name="see-also"></a>另请参阅  
 [CMonikerFile 类](../../mfc/reference/cmonikerfile-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CMonikerFile 类](../../mfc/reference/cmonikerfile-class.md)   
 [CDataPathProperty 类](../../mfc/reference/cdatapathproperty-class.md)

