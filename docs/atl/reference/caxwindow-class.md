---
title: "CAxWindow 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CAxWindowT
- CAxWindow
dev_langs:
- C++
helpviewer_keywords:
- CAxWindow class
- ATL, hosting ActiveX controls
ms.assetid: 85e79261-43e4-4770-bde0-1ff87f222b0f
caps.latest.revision: 24
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
ms.openlocfilehash: 202c68fa4044a7c7a6c47c52b8095c5e7227b56d
ms.lasthandoff: 02/24/2017

---
# <a name="caxwindow-class"></a>CAxWindow 类
此类提供用于操作承载 ActiveX 控件的窗口的方法。  
  
> [!IMPORTANT]
>  不能在 Windows 运行时中执行的应用程序中使用此类及其成员。  
  
## <a name="syntax"></a>语法  
  
```
class CAxWindow : public CWindow
```  
  
## <a name="members"></a>成员  
  
### <a name="methods"></a>方法  
  
|||  
|-|-|  
|[AttachControl](#attachcontrol)|将附加到现有 ActiveX 控件`CAxWindow`对象。|  
|[CAxWindow](#caxwindow)|构造 `CAxWindow` 对象。|  
|[CreateControl](#createcontrol)|创建 ActiveX 控件，初始化它并将它在宿主`CAxWindow`窗口。|  
|[CreateControlEx](#createcontrolex)|创建 ActiveX 控件，并从该控件中检索的接口指针 （或指针）。|  
|[GetWndClassName](#getwndclassname)|（静态）检索的预定义的类名`CAxWindow`对象。|  
|[QueryControl](#querycontrol)|检索**IUnknown**托管 ActiveX 控件。|  
|[QueryHost](#queryhost)|检索**IUnknown**指针`CAxWindow`对象。|  
|[SetExternalDispatch](#setexternaldispatch)|设置使用的外部调度接口`CAxWindow`对象。|  
|[SetExternalUIHandler](#setexternaluihandler)|设置外部**IDocHostUIHandler**所用接口`CAxWindow`对象。|  
  
### <a name="operators"></a>运算符  
  
|||  
|-|-|  
|[运算符 =](#operator_eq)|将分配**HWND**到某个现有**CAxWindow**对象。|  
  
## <a name="remarks"></a>备注  
 此类提供方法，用于操作窗口承载 ActiveX 控件。 承载的由" **AtlAxWin80"**，由其包装`CAxWindow`。  
  
 类`CAxWindow`的专用化作为实现`CAxWindowT`类。 此特殊化声明为︰  
  
 `typedef CAxWindowT<CWindow> CAxWindow;`  
  
 如果需要更改类的基类，则可以使用`CAxWindowT`并作为模板参数指定新的基类。  
  
## <a name="requirements"></a>要求  
 **标头︰** atlwin.h  
  
##  <a name="a-nameattachcontrola--caxwindowattachcontrol"></a><a name="attachcontrol"></a>CAxWindow::AttachControl  
 如果有人已不存在，并将指定的控件附加到主机，请创建一个新的宿主对象。  
  
```
HRESULT AttachControl(
    IUnknown* pControl,
    IUnknown** ppUnkContainer);
```  
  
### <a name="parameters"></a>参数  
 `pControl`  
 [in]一个指向**IUnknown**的控件。  
  
 `ppUnkContainer`  
 [out]一个指向**IUnknown**的主机 ( **AxWin**对象)。  
  
### <a name="return-value"></a>返回值  
 标准 `HRESULT` 值。  
  
### <a name="remarks"></a>备注  
 要附加的控件对象必须正确的初始化，然后再调`AttachControl`。  
  
##  <a name="a-namecaxwindowa--caxwindowcaxwindow"></a><a name="caxwindow"></a>CAxWindow::CAxWindow  
 构造`CAxWindow`对象使用现有的窗口对象句柄。  
  
```
CAxWindow(HWND hWnd = NULL);
```  
  
### <a name="parameters"></a>参数  
 `hWnd`  
 现有的窗口对象的句柄。  
  
##  <a name="a-namecreatecontrola--caxwindowcreatecontrol"></a><a name="createcontrol"></a>CAxWindow::CreateControl  
 创建 ActiveX 控件，初始化它并在指定窗口中承载它。  
  
```
HRESULT CreateControl(
    LPCOLESTR lpszName,
    IStream* pStream = NULL,
    IUnknown** ppUnkContainer = NULL);

HRESULT CreateControl(
    DWORD dwResID,
    IStream* pStream = NULL,
    IUnknown** ppUnkContainer = NULL);
```  
  
### <a name="parameters"></a>参数  
 `lpszName`  
 指向要创建控件的字符串的指针。 通过以下方式之一的格式必须︰  
  
-   例如，"MSCAL ProgID。Calendar.7"  
  
-   例如，"{8E27C92B-1264-101C-8A2F-040224009C02}"CLSID  
  
-   例如，"http://www.microsoft.com"URL  
  
-   对等活动文档的引用"file://\\\Documents\MyDoc.doc"  
  
-   如 HTML 片段"MSHTML:\<HTML&1;>\<正文&1;> 这是文本行\</正文&1;>\</HTML&1;>"  
  
    > [!NOTE]
    >  "MSHTML:"，以便它被指定为正在 MSHTML 流必须在之前的 HTML 片段。 Windows Mobile 平台支持的 ProgID 和 CLSID。 Windows CE 嵌入平台中，Windows Mobile CE IE 支持的支持以外所有类型包括 ProgID，CLSID、 URL、 都引用与活动文档的 HTML 片段。  
  
 `pStream`  
 [in]指向用于初始化该控件的属性流的指针。 可以是**NULL**。  
  
 `ppUnkContainer`  
 [out]将接收的指针的地址**IUnknown**的容器。 可以是**NULL**。  
  
 `dwResID`  
 一个 HTML 资源的资源 ID。 将创建并使用指定的资源加载 web 浏览器控件。  
  
### <a name="return-value"></a>返回值  
 标准 `HRESULT` 值。  
  
### <a name="remarks"></a>备注  
 如果使用此方法的第二个版本，则 HTML 控件创建并绑定到所标识的资源`dwResID`。  
  
 此方法为您提供了与调用相同的结果︰  
  
 [!code-cpp[NVC_ATL_Windowing #&42;](../../atl/codesnippet/cpp/caxwindow-class_1.cpp)]  
  
 请参阅[CAxWindow2T::CreateControlLic](../../atl/reference/caxwindow2t-class.md#createcontrollic)来创建、 初始化和承载授权的 ActiveX 控件。  
  
### <a name="example"></a>示例  
 请参阅[承载 ActiveX 控件使用 ATL AXHost](../../atl/hosting-activex-controls-using-atl-axhost.md)有关的示例，使用`CreateControl`。  
  
##  <a name="a-namecreatecontrolexa--caxwindowcreatecontrolex"></a><a name="createcontrolex"></a>CAxWindow::CreateControlEx  
 创建 ActiveX 控件，初始化它并在指定窗口中承载它。  
  
```
HRESULT CreateControlEx(
    LPCOLESTR lpszName,
    IStream* pStream = NULL,
    IUnknown** ppUnkContainer = NULL,
    IUnknown** ppUnkControl = NULL,
    REFIID iidSink = IID_NULL,
    IUnknown* punkSink = NULL);

HRESULT CreateControlEx(
    DWORD dwResID,
    IStream* pStream = NULL,
    IUnknown** ppUnkContainer = NULL,
    IUnknown** ppUnkControl = NULL,
    REFIID iidSink = IID_NULL,
    IUnknown* punkSink = NULL);
```  
  
### <a name="parameters"></a>参数  
 `lpszName`  
 指向要创建控件的字符串的指针。 通过以下方式之一的格式必须︰  
  
-   例如，"MSCAL ProgID。Calendar.7"  
  
-   例如，"{8E27C92B-1264-101C-8A2F-040224009C02}"CLSID  
  
-   例如，"http://www.microsoft.com"URL  
  
-   对等活动文档的引用"file://\\\Documents\MyDoc.doc"  
  
-   如 HTML 片段"MSHTML:\<HTML&1;>\<正文&1;> 这是文本行\</正文&1;>\</HTML&1;>"  
  
    > [!NOTE]
    >  "MSHTML:"，以便它被指定为正在 MSHTML 流必须在之前的 HTML 片段。 Windows Mobile 平台支持的 ProgID 和 CLSID。 Windows CE 嵌入平台中，Windows Mobile CE IE 支持的支持以外所有类型包括 ProgID，CLSID、 URL、 都引用与活动文档的 HTML 片段。  
  
 `pStream`  
 [in]指向用于初始化该控件的属性流的指针。 可以是**NULL**。  
  
 `ppUnkContainer`  
 [out]将接收的指针的地址**IUnknown**的容器。 可以是**NULL**。  
  
 `ppUnkControl`  
 [out]将接收的指针的地址**IUnknown**的控件。 可以是**NULL**。  
  
 `iidSink`  
 [in]在包含的对象上的传出接口的接口标识符。 可以是**IID_NULL**。  
  
 *punkSink*  
 [in]一个指向**IUnknown**要连接到指定的包含对象的连接点的接收器对象的接口`iidSink`。  
  
 `dwResID`  
 [in]一个 HTML 资源的资源 ID。 将创建并使用指定的资源加载 web 浏览器控件。  
  
### <a name="return-value"></a>返回值  
 标准 `HRESULT` 值。  
  
### <a name="remarks"></a>备注  
 此方法类似于是[CAxWindow::CreateControl](#createcontrol)，但与该方法中，不同`CreateControlEx`还允许您接收到新创建的控件的接口指针并将事件接收器设置为接收控件触发的事件。  
  
 请参阅[CAxWindow2T::CreateControlLicEx](../../atl/reference/caxwindow2t-class.md#createcontrollicex)来创建、 初始化和承载授权的 ActiveX 控件。  
  
### <a name="example"></a>示例  
 请参阅[承载 ActiveX 控件使用 ATL AXHost](../../atl/hosting-activex-controls-using-atl-axhost.md)有关的示例，使用`CreateControlEx`。  
  
##  <a name="a-namegetwndclassnamea--caxwindowgetwndclassname"></a><a name="getwndclassname"></a>CAxWindow::GetWndClassName  
 检索的窗口类的名称。  
  
```
static LPCTSTR GetWndClassName();
```  
  
### <a name="return-value"></a>返回值  
 指向包含可以承载未授权的 ActiveX 控件的窗口类的名称的字符串的指针。  
  
##  <a name="a-nameoperatoreqa--caxwindowoperator-"></a><a name="operator_eq"></a>CAxWindow::operator =  
 将分配`HWND`到某个现有`CAxWindow`对象。  
  
```
CAxWindow<TBase>& operator=(HWND hWnd);
```  
  
### <a name="parameters"></a>参数  
 `hWnd`  
 现有的窗口句柄。  
  
### <a name="return-value"></a>返回值  
 返回对当前 `CAxWindow` 对象的引用。  
  
##  <a name="a-namequerycontrola--caxwindowquerycontrol"></a><a name="querycontrol"></a>CAxWindow::QueryControl  
 检索所承载的控件的指定的接口。  
  
```
HRESULT QueryControl(REFIID iid, void** ppUnk);
template <class  Q>
HRESULT QueryControl(Q** ppUnk);
```  
  
### <a name="parameters"></a>参数  
 `iid`  
 [in]指定控件的接口的 IID。  
  
 `ppUnk`  
 [out]指向控件的接口的指针。 在此方法的模板版本，没有需要引用 ID，只要具有相关联的 UUID 类型化的接口进行传递。  
  
 `Q`  
 [in]正在查询的接口。  
  
### <a name="return-value"></a>返回值  
 标准 `HRESULT` 值。  
  
##  <a name="a-namequeryhosta--caxwindowqueryhost"></a><a name="queryhost"></a>CAxWindow::QueryHost  
 返回指定的主机的接口。  
  
```
HRESULT QueryHost(REFIID iid, void** ppUnk);
template <class  Q>
HRESULT QueryHost(Q** ppUnk);
```  
  
### <a name="parameters"></a>参数  
 `iid`  
 [in]指定控件的接口的 IID。  
  
 `ppUnk`  
 [out]指向主机上的接口的指针。 在此方法的模板版本，没有需要引用 ID，只要具有相关联的 UUID 类型化的接口进行传递。  
  
 `Q`  
 [in]正在查询的接口。  
  
### <a name="return-value"></a>返回值  
 标准 `HRESULT` 值。  
  
### <a name="remarks"></a>备注  
 主机的接口允许访问该窗口中承载的代码，由实现的基本功能**AxWin**。  
  
##  <a name="a-namesetexternaldispatcha--caxwindowsetexternaldispatch"></a><a name="setexternaldispatch"></a>CAxWindow::SetExternalDispatch  
 设置外部调度接口来`CAxWindow`对象。  
  
```
HRESULT SetExternalDispatch(IDispatch* pDisp);
```  
  
### <a name="parameters"></a>参数  
 `pDisp`  
 [in]一个指向`IDispatch`接口。  
  
### <a name="return-value"></a>返回值  
 标准 `HRESULT` 值。  
  
##  <a name="a-namesetexternaluihandlera--caxwindowsetexternaluihandler"></a><a name="setexternaluihandler"></a>CAxWindow::SetExternalUIHandler  
 设置外部[IDocHostUIHandlerDispatch](../../atl/reference/idochostuihandlerdispatch-interface.md)接口`CAxWindow`对象。  
  
```
HRESULT SetExternalUIHandler(IDocHostUIHandlerDispatch* pUIHandler);
```  
  
### <a name="parameters"></a>参数  
 *pUIHandler*  
 [in]一个指向**IDocHostUIHandlerDispatch**接口。  
  
### <a name="return-value"></a>返回值  
 标准 `HRESULT` 值。  
  
### <a name="remarks"></a>备注  
 外部`IDocHostUIHandlerDispatch`接口由主机的站点中查询的控件使用`IDocHostUIHandlerDispatch`接口。 WebBrowser 控件是执行此的一个控件。  
  
## <a name="see-also"></a>另请参阅  
 [ATLCON 示例](../../visual-cpp-samples.md)   
 [CWindow 类](../../atl/reference/cwindow-class.md)   
 [复合控件基础知识](../../atl/atl-composite-control-fundamentals.md)   
 [类概述](../../atl/atl-class-overview.md)   
 [控件包含常见问题](../../atl/atl-control-containment-faq.md)


