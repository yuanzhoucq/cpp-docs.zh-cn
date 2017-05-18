---
title: "CBindStatusCallback 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- asynchronous data transfer [C++]
- data transfer [C++]
- data transfer [C++], asynchronous
- CBindStatusCallback class
ms.assetid: 0f5da276-6031-4418-b2a9-a4750ef29e77
caps.latest.revision: 22
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 604a4bf49490ad2599c857eb3afd527d67e1e25b
ms.openlocfilehash: 50a0a27528f402cda5906658cd2c9cf57a5908e8
ms.contentlocale: zh-cn
ms.lasthandoff: 02/24/2017

---
# <a name="cbindstatuscallback-class"></a>CBindStatusCallback 类
此类实现 `IBindStatusCallback` 接口。  
  
> [!IMPORTANT]
>  不能在 Windows 运行时中执行的应用程序中使用此类及其成员。  
  
## <a name="syntax"></a>语法  
  
```
template <class T,
    int nBindFlags = BINDF_ASYNCHRONOUS |   BINDF_ASYNCSTORAGE | BINDF_GETNEWESTVERSION | BINDF_NOWRITECACHE>  
class ATL_NO_VTABLE CBindStatusCallback : public CComObjectRootEx
 <T ::_ThreadModel::ThreadModelNoCS>,
    public IBindStatusCallbackImpl<T>
```  
  
#### <a name="parameters"></a>参数  
 `T`  
 包含接收到数据时将调用的函数的类。  
  
 *nBindFlags*  
 指定由返回的绑定标志[GetBindInfo](#getbindinfo)。 默认实现设置的绑定是异步的检索最新版本的数据/对象，而不将检索到的数据存储在磁盘缓存。  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|说明|  
|----------|-----------------|  
|[CBindStatusCallback::CBindStatusCallback](#cbindstatuscallback)|构造函数。|  
|[CBindStatusCallback:: ~ CBindStatusCallback](#dtor)|析构函数。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CBindStatusCallback::Download](#download)|静态方法，开始下载过程中，创建`CBindStatusCallback`对象，并调用`StartAsyncDownload`。|  
|[CBindStatusCallback::GetBindInfo](#getbindinfo)|要创建的绑定的类型的请求信息的异步名字对象由调用。|  
|[CBindStatusCallback::GetPriority](#getpriority)|调用异步名字对象中，以获取绑定操作的优先级。 ATL 实现返回`E_NOTIMPL`。|  
|[CBindStatusCallback::OnDataAvailable](#ondataavailable)|调用以将数据提供给您的应用程序变得可用。 读取的数据，然后调用传递给它要使用的数据的函数。|  
|[CBindStatusCallback::OnLowResource](#onlowresource)|调用时资源不足。 ATL 实现返回`S_OK`。|  
|[CBindStatusCallback::OnObjectAvailable](#onobjectavailable)|要将对象的接口指针传递给您的应用程序的异步名字对象由调用。 ATL 实现返回`S_OK`。|  
|[CBindStatusCallback::OnProgress](#onprogress)|调用以指示数据下载进程的进度。 ATL 实现返回`S_OK`。|  
|[CBindStatusCallback::OnStartBinding](#onstartbinding)|启动绑定时调用。|  
|[CBindStatusCallback::OnStopBinding](#onstopbinding)|当异步数据传输已停止时调用。|  
|[CBindStatusCallback::StartAsyncDownload](#startasyncdownload)|初始化可用的字节数，并且为零，读取的字节数从一个 URL，并调用创建推送类型 stream 对象`OnDataAvailable`每次数据时可用。|  
  
### <a name="public-data-members"></a>公共数据成员  
  
|名称|说明|  
|----------|-----------------|  
|[CBindStatusCallback::m_dwAvailableToRead](#m_dwavailabletoread)|可读取的字节数。|  
|[CBindStatusCallback::m_dwTotalRead](#m_dwtotalread)|读取的字节的总数。|  
|[CBindStatusCallback::m_pFunc](#m_pfunc)|指向函数的调用在数据可用时。|  
|[CBindStatusCallback::m_pT](#m_pt)|请求异步数据传输对象的指针。|  
|[CBindStatusCallback::m_spBindCtx](#m_spbindctx)|指向[IBindCtx](http://msdn.microsoft.com/library/windows/desktop/ms693755)当前绑定操作的接口。|  
|[CBindStatusCallback::m_spBinding](#m_spbinding)|指向`IBinding`当前绑定操作的接口。|  
|[CBindStatusCallback::m_spMoniker](#m_spmoniker)|指向[IMoniker](http://msdn.microsoft.com/library/windows/desktop/ms679705)界面要使用的 URL。|  
|[CBindStatusCallback::m_spStream](#m_spstream)|指向[IStream](http://msdn.microsoft.com/library/windows/desktop/aa380034)数据传输的接口。|  
  
## <a name="remarks"></a>备注  
 `CBindStatusCallback` 类实现 `IBindStatusCallback` 接口。 `IBindStatusCallback`必须实现您的应用程序以便它可以从异步数据传输的接收通知。 系统提供的异步名字对象使用`IBindStatusCallback`方法来发送和接收的异步数据有关的信息传输到和从您的对象。  
  
 通常情况下，`CBindStatusCallback`对象将与特定的绑定操作相关联。 例如，在[异步](../../visual-cpp-samples.md)示例中，当您设置 URL 属性，它会创建`CBindStatusCallback`对象对的调用中`Download`:  
  
 [!code-cpp[NVC_ATL_Windowing #&86;](../../atl/codesnippet/cpp/cbindstatuscallback-class_1.h)]  
  
 异步名字对象使用的回调函数`OnData`时要调用你的应用程序具有的数据。 异步名字对象是由系统提供的。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `CComObjectRootBase`  
  
 `IBindStatusCallback`  
  
 [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)  
  
 `CBindStatusCallback`  
  
## <a name="requirements"></a>要求  
 **标头︰** atlctl.h  
  
##  <a name="cbindstatuscallback"></a>CBindStatusCallback::CBindStatusCallback  
 构造函数。  
  
```
CBindStatusCallback();
```  
  
### <a name="remarks"></a>备注  
 创建要接收通知有关异步数据传输的对象。 通常情况下，为每个绑定操作创建一个对象。  
  
 构造函数还初始化[m_pT](#m_pt)和[m_pFunc](#m_pfunc)到**NULL**。  
  
##  <a name="dtor"></a>CBindStatusCallback:: ~ CBindStatusCallback  
 析构函数。  
  
```
~CBindStatusCallback();
```  
  
### <a name="remarks"></a>备注  
 释放所有已分配的资源。  
  
##  <a name="download"></a>CBindStatusCallback::Download  
 创建`CBindStatusCallback`对象并调用`StartAsyncDownload`开始以异步方式从指定的 URL 下载数据。  
  
```
static HRESULT Download(  
    T* pT,
    ATL_PDATAAVAILABLE pFunc,
    BSTR bstrURL,
    IUnknown* pUnkContainer = NULL,
    BOOL bRelative = FALSE);
```  
  
### <a name="parameters"></a>参数  
 *pT*  
 [in]指向请求异步数据传输的对象的指针。 `CBindStatusCallback`针对此对象的类模板对象。  
  
 *pFunc*  
 [in]指向接收读取的数据的函数的指针。 该函数是对象的类型类的成员`T`。 请参阅[StartAsyncDownload](#startasyncdownload)有关语法和示例。  
  
 `bstrURL`  
 [in]要从其获取数据的 URL。 可以是任何有效的 URL 或文件名称。 不能为**NULL**。 例如:   
  
 `CComBSTR mybstr =_T("http://somesite/data.htm")`  
  
 `pUnkContainer`  
 [in]**IUnknown**的容器。 **NULL**默认情况下。  
  
 `bRelative`  
 [in]指示该 URL 相对值还是绝对值的标志。 **FALSE**默认情况下，这意味着 URL 是绝对地址。  
  
### <a name="return-value"></a>返回值  
 其中一个标准`HRESULT`值。  
  
### <a name="remarks"></a>备注  
 每次有可用数据发送到的对象通过`OnDataAvailable`。 `OnDataAvailable`读取的数据并调用函数所指向*pFunc* （例如，若要将数据存储或将其打印到屏幕）。  
  
##  <a name="getbindinfo"></a>CBindStatusCallback::GetBindInfo  
 调用以指示如何将绑定的名字对象。  
  
```
STDMETHOD(GetBindInfo)(
    DWORD* pgrfBSCF,
    BINDINFO* pbindinfo);
```  
  
### <a name="parameters"></a>参数  
 *pgrfBSCF*  
 [out]一个指向**BINDF**枚举值，该值指示应发生绑定操作的方式。 默认情况下，使用下面的枚举值设置︰  
  
 **BINDF_ASYNCHRONOUS**异步下载。  
  
 **BINDF_ASYNCSTORAGE** `OnDataAvailable`返回**E_PENDING**时数据尚不可用而不是阻止，直到有可用数据。  
  
 **BINDF_GETNEWESTVERSION**绑定操作应该在检索数据的最新版本。  
  
 **BINDF_NOWRITECACHE**绑定操作不应在磁盘缓存中存储检索到的数据。  
  
 *pbindinfo*  
 [in、 out]一个指向**绑定信息**结构提供有关如何对象想要发生绑定的详细信息。  
  
### <a name="return-value"></a>返回值  
 其中一个标准`HRESULT`值。  
  
### <a name="remarks"></a>备注  
 默认实现设置的绑定是异步的并使用数据推送模型。 在数据推送模型中，名字对象硬盘异步绑定操作和不断地在新数据可用时通知客户端。  
  
##  <a name="getpriority"></a>CBindStatusCallback::GetPriority  
 调用异步名字对象中，以获取绑定操作的优先级。  
  
```
STDMETHOD(GetPriority)(LONG* pnPriority);
```  
  
### <a name="parameters"></a>参数  
 *pnPriority*  
 [out]地址的指针**长**，成功时，接收变量的优先级。  
  
### <a name="return-value"></a>返回值  
 返回**E_NOTIMPL**。  
  
##  <a name="m_dwavailabletoread"></a>CBindStatusCallback::m_dwAvailableToRead  
 可以用于存储可供读取的字节数。  
  
```
DWORD m_dwAvailableToRead;
```  
  
### <a name="remarks"></a>备注  
 初始化将注意力集中在`StartAsyncDownload`。  
  
##  <a name="m_dwtotalread"></a>CBindStatusCallback::m_dwTotalRead  
 在异步数据传输中读取字节的累积总数。  
  
```
DWORD m_dwTotalRead;
```  
  
### <a name="remarks"></a>备注  
 每次递增`OnDataAvailable`由实际读取的字节数。 初始化将注意力集中在`StartAsyncDownload`。  
  
##  <a name="m_pfunc"></a>CBindStatusCallback::m_pFunc  
 指向函数`m_pFunc`由调用`OnDataAvailable`将可用的数据 （例如，若要将数据存储或将其打印到屏幕） 后。  
  
```
ATL_PDATAAVAILABLE m_pFunc;
```  
  
### <a name="remarks"></a>备注  
 指向函数`m_pFunc`是对象的类的成员并且具有以下语法︰  
  
```  
void Function_Name(  
   CBindStatusCallback<T>* pbsc,  
   BYTE* pBytes,  
   DWORD dwSize  
   );  
```  
  
##  <a name="m_pt"></a>CBindStatusCallback::m_pT  
 指向请求异步数据传输的对象的指针。  
  
```
T* m_pT;
```  
  
### <a name="remarks"></a>备注  
 `CBindStatusCallback`针对此对象的类模板对象。  
  
##  <a name="m_spbindctx"></a>CBindStatusCallback::m_spBindCtx  
 一个指向[IBindCtx](http://msdn.microsoft.com/library/windows/desktop/ms693755)提供的绑定上下文 （存储特定的名字对象绑定操作有关的信息的对象） 的访问接口。  
  
```
CComPtr<IBindCtx> m_spBindCtx;
```  
  
### <a name="remarks"></a>备注  
 在初始化`StartAsyncDownload`。  
  
##  <a name="m_spbinding"></a>CBindStatusCallback::m_spBinding  
 一个指向`IBinding`当前绑定操作的接口。  
  
```
CComPtr<IBinding> m_spBinding;
```  
  
### <a name="remarks"></a>备注  
 在初始化`OnStartBinding`和发布在`OnStopBinding`。  
  
##  <a name="m_spmoniker"></a>CBindStatusCallback::m_spMoniker  
 一个指向[IMoniker](http://msdn.microsoft.com/library/windows/desktop/ms679705)界面要使用的 URL。  
  
```
CComPtr<IMoniker> m_spMoniker;
```  
  
### <a name="remarks"></a>备注  
 在初始化`StartAsyncDownload`。  
  
##  <a name="m_spstream"></a>CBindStatusCallback::m_spStream  
 一个指向[IStream](http://msdn.microsoft.com/library/windows/desktop/aa380034)当前绑定操作的接口。  
  
```
CComPtr<IStream> m_spStream;
```  
  
### <a name="remarks"></a>备注  
 在初始化`OnDataAvailable`从**STGMEDIUM**结构时**BCSF**标志是**BCSF_FIRSTDATANOTIFICATION**时释放**BCSF**标志是**BCSF_LASTDATANOTIFICATION**。  
  
##  <a name="ondataavailable"></a>CBindStatusCallback::OnDataAvailable  
 系统提供的异步名字对象调用`OnDataAvailable`以提供对对象的数据变得可用。  
  
```
STDMETHOD(  
    OnDataAvailable)(DWORD grfBSCF,
    DWORD dwSize,
    FORMATETC* /* pformatetc */,
    STGMEDIUM* pstgmed);
```  
  
### <a name="parameters"></a>参数  
 *grfBSCF*  
 [in]一个**BSCF**枚举值。 一个或多项操作︰ **BSCF_FIRSTDATANOTIFICATION**， **BSCF_INTERMEDIARYDATANOTIFICATION**，或**BSCF_LASTDATANOTIFICATION**。  
  
 `dwSize`  
 [in]可用的绑定开始后的数据累积量 （以字节为单位）。 可以是零，表示没有相关的数据量或任何特定量变为可用。  
  
 *pformatetc*  
 [in]指向[FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682242)结构，其中包含可用数据的格式。 如果没有格式，可以是**CF_NULL**。  
  
 *pstgmed*  
 [in]指向[STGMEDIUM](http://msdn.microsoft.com/library/windows/desktop/ms695269)保存现已推出的实际数据的结构。  
  
### <a name="return-value"></a>返回值  
 其中一个标准`HRESULT`值。  
  
### <a name="remarks"></a>备注  
 `OnDataAvailable`读取的数据，然后调用对象的类 （例如，若要将数据存储或将其打印到屏幕） 的方法。 请参阅[CBindStatusCallback::StartAsyncDownload](#startasyncdownload)有关的详细信息。  
  
##  <a name="onlowresource"></a>CBindStatusCallback::OnLowResource  
 调用时资源不足。  
  
```
STDMETHOD(OnLowResource)(DWORD /* dwReserved */);
```  
  
### <a name="parameters"></a>参数  
 `dwReserved`  
 保留。  
  
### <a name="return-value"></a>返回值  
 返回 `S_OK`。  
  
##  <a name="onobjectavailable"></a>CBindStatusCallback::OnObjectAvailable  
 要将对象的接口指针传递给您的应用程序的异步名字对象由调用。  
  
```
STDMETHOD(OnObjectAvailable)(REFID /* riid */, IUnknown* /* punk */);
```  
  
### <a name="parameters"></a>参数  
 `riid`  
 所请求的接口的接口标识符。 未使用。  
  
 `punk`  
 IUnknown 接口的地址。 未使用。  
  
### <a name="return-value"></a>返回值  
 返回 `S_OK`。  
  
##  <a name="onprogress"></a>CBindStatusCallback::OnProgress  
 调用以指示数据下载进程的进度。  
  
```
STDMETHOD(OnProgress)(
    ULONG /* ulProgress */,
    ULONG /* ulProgressMax */,
    ULONG /* ulStatusCode */,
    LPCWSTRONG /* szStatusText */);
```  
  
### <a name="parameters"></a>参数  
 `ulProgress`  
 无符号长整数。 未使用。  
  
 `ulProgressMax`  
 无符号长整数未使用。  
  
 `ulStatusCode`  
 无符号长整数。 未使用。  
  
 `szStatusText`  
 一个字符串值的地址。 未使用。  
  
### <a name="return-value"></a>返回值  
 返回 `S_OK`。  
  
##  <a name="onstartbinding"></a>CBindStatusCallback::OnStartBinding  
 设置数据成员[m_spBinding](#m_spbinding)到`IBinding`中的指针`pBinding`。  
  
```
STDMETHOD(OnStartBinding)(DWORD /* dwReserved */, IBinding* pBinding);
```  
  
### <a name="parameters"></a>参数  
 `dwReserved`  
 留待将来使用。  
  
 `pBinding`  
 [in]当前的 IBinding 接口地址绑定操作。 这不能为 NULL。 客户端应在需要对绑定对象的引用该指针上调用 AddRef。  
  
##  <a name="onstopbinding"></a>CBindStatusCallback::OnStopBinding  
 版本`IBinding`中的数据成员的指针[m_spBinding](#m_spbinding)。  
  
```
STDMETHOD(OnStopBinding)(HRESULT hresult, LPCWSTR /* szError */);
```  
  
### <a name="parameters"></a>参数  
 `hresult`  
 从绑定操作返回状态代码。  
  
 szStatusText  
 一个字符串值，未使用的地址。  
  
### <a name="remarks"></a>备注  
 调用由系统提供异步名字对象以指示绑定操作的结束。  
  
##  <a name="startasyncdownload"></a>CBindStatusCallback::StartAsyncDownload  
 启动异步下载数据，从指定的 URL。  
  
```
HRESULT StartAsyncDownload(  
    T* pT,
    ATL_PDATAAVAILABLE pFunc,
    BSTR bstrURL,
    IUnknown* pUnkContainer = NULL,
    BOOL bRelative = FALSE);
```  
  
### <a name="parameters"></a>参数  
 *pT*  
 [in]指向请求异步数据传输的对象的指针。 `CBindStatusCallback`针对此对象的类模板对象。  
  
 *pFunc*  
 [in]指向接收所读取的数据的函数的指针。 该函数是对象的类型类的成员`T`。 请参阅**备注**有关语法和示例。  
  
 `bstrURL`  
 [in]要从其获取数据的 URL。 可以是任何有效的 URL 或文件名称。 不能为**NULL**。 例如:   
  
 `CComBSTR mybstr =_T("http://somesite/data.htm")`  
  
 `pUnkContainer`  
 [in]**IUnknown**的容器。 **NULL**默认情况下。  
  
 `bRelative`  
 [in]指示该 URL 相对值还是绝对值的标志。 **FALSE**默认情况下，这意味着 URL 是绝对地址。  
  
### <a name="return-value"></a>返回值  
 其中一个标准`HRESULT`值。  
  
### <a name="remarks"></a>备注  
 每次有可用数据发送到的对象通过`OnDataAvailable`。 `OnDataAvailable`读取的数据并调用函数所指向*pFunc* （例如，若要将数据存储或将其打印到屏幕）。  
  
 指向函数*pFunc*是对象的类的成员并且具有以下语法︰  
  
 `void Function_Name(`  
  
 `CBindStatusCallback<T>*` `pbsc` `,`  
  
 `BYTE*` `pBytes` `,`  
  
 `DWORD` `dwSize`  
  
 `);`  
  
 在下面的示例 (摘自[异步](../../visual-cpp-samples.md)示例)，该函数`OnData`将接收到的数据写入到文本框。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATL_Windowing #&87;](../../atl/codesnippet/cpp/cbindstatuscallback-class_2.h)]  
  
## <a name="see-also"></a>另请参阅  
 [类概述](../../atl/atl-class-overview.md)

