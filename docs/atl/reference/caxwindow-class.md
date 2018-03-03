---
title: "CAxWindow 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CAxWindow
- ATLWIN/ATL::CAxWindow
- ATLWIN/ATL::AttachControl
- ATLWIN/ATL::CreateControl
- ATLWIN/ATL::CreateControlEx
- ATLWIN/ATL::GetWndClassName
- ATLWIN/ATL::QueryControl
- ATLWIN/ATL::QueryHost
- ATLWIN/ATL::SetExternalDispatch
- ATLWIN/ATL::SetExternalUIHandler
dev_langs:
- C++
helpviewer_keywords:
- CAxWindow class
- ATL, hosting ActiveX controls
ms.assetid: 85e79261-43e4-4770-bde0-1ff87f222b0f
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 8848e8ecf85b073032561e2db52a0db1889911e6
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="caxwindow-class"></a>CAxWindow 类
此类提供用于操作承载 ActiveX 控件的窗口的方法。  
  
> [!IMPORTANT]
>  此类及其成员无法在 Windows 运行时中执行的应用中使用。  
  
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
|[CreateControl](#createcontrol)|创建 ActiveX 控件，初始化它，并承载它在`CAxWindow`窗口。|  
|[CreateControlEx](#createcontrolex)|创建 ActiveX 控件，并从控件中检索的接口指针 （或指针）。|  
|[GetWndClassName](#getwndclassname)|（静态）检索的预定义的类名称`CAxWindow`对象。|  
|[QueryControl](#querycontrol)|检索**IUnknown**托管 ActiveX 控件。|  
|[QueryHost](#queryhost)|检索**IUnknown**指针`CAxWindow`对象。|  
|[SetExternalDispatch](#setexternaldispatch)|设置使用的外部的调度接口`CAxWindow`对象。|  
|[SetExternalUIHandler](#setexternaluihandler)|设置外部**IDocHostUIHandler**接口由`CAxWindow`对象。|  
  
### <a name="operators"></a>运算符  
  
|||  
|-|-|  
|[运算符 =](#operator_eq)|将分配**HWND**到一个现有**CAxWindow**对象。|  
  
## <a name="remarks"></a>备注  
 此类提供方法，用于操作窗口承载 ActiveX 控件。 提供的托管" **AtlAxWin80"**，这由包装`CAxWindow`。  
  
 类`CAxWindow`作为专用化实现`CAxWindowT`类。 此专用化声明为：  
  
 `typedef CAxWindowT<CWindow> CAxWindow;`  
  
 如果你需要将基类更改，则可以使用`CAxWindowT`并作为模板参数指定新的基类。  
  
## <a name="requirements"></a>惠?  
 **标头：** atlwin.h  
  
##  <a name="attachcontrol"></a>CAxWindow::AttachControl  
 如果一个已不存在，将指定的控件附加到主机，请创建一个新的宿主对象。  
  
```
HRESULT AttachControl(
    IUnknown* pControl,
    IUnknown** ppUnkContainer);
```  
  
### <a name="parameters"></a>参数  
 `pControl`  
 [in]指向的指针**IUnknown**的控件。  
  
 `ppUnkContainer`  
 [out]指向的指针**IUnknown**的主机 ( **AxWin**对象)。  
  
### <a name="return-value"></a>返回值  
 标准 `HRESULT` 值。  
  
### <a name="remarks"></a>备注  
 要附加的控件对象必须正确初始化，然后再调`AttachControl`。  
  
##  <a name="caxwindow"></a>CAxWindow::CAxWindow  
 构造`CAxWindow`对象使用现有的窗口对象句柄。  
  
```
CAxWindow(HWND hWnd = NULL);
```  
  
### <a name="parameters"></a>参数  
 `hWnd`  
 现有的窗口对象的句柄。  
  
##  <a name="createcontrol"></a>CAxWindow::CreateControl  
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
 指向要创建控件的字符串的指针。 格式必须通过以下方式之一：  
  
-   例如"MSCAL ProgID。Calendar.7"  
  
-   例如"{8E27C92B-1264-101C-8A2F-040224009C02}"的 CLSID  
  
-   例如"http://www.microsoft.com"URL  
  
-   到如活动文档的引用"file://\\\Documents\MyDoc.doc"  
  
-   如的 HTML 片段"MSHTML:\<HTML >\<正文 > 这是一套文本\</b O >\</HTML >"  
  
    > [!NOTE]
    >  "MSHTML:"，以便它指定为 MSHTML 流必须在之前的 HTML 片段。 Windows Mobile 平台支持的 ProgID 和 CLSID。 Windows CE 嵌入平台中，Windows Mobile CE IE 支持支持以外的所有类型包括 ProgID，CLSID、 URL，都引用到活动文档时和的 HTML 片段。  
  
 `pStream`  
 [in]指向用于初始化的控件的属性流的指针。 可以是**NULL**。  
  
 `ppUnkContainer`  
 [out]将接收的指针的地址**IUnknown**的容器。 可以是**NULL**。  
  
 `dwResID`  
 HTML 资源的资源 ID。 将创建并使用指定的资源加载 WebBrowser 控件。  
  
### <a name="return-value"></a>返回值  
 标准 `HRESULT` 值。  
  
### <a name="remarks"></a>备注  
 如果使用此方法的第二个版本，则创建并绑定到所标识的资源的 HTML 控件`dwResID`。  
  
 此方法为您提供了与调用相同的结果：  
  
 [!code-cpp[NVC_ATL_Windowing#42](../../atl/codesnippet/cpp/caxwindow-class_1.cpp)]  
  
 请参阅[CAxWindow2T::CreateControlLic](../../atl/reference/caxwindow2t-class.md#createcontrollic)若要创建，初始化和承载授权的 ActiveX 控件。  
  
### <a name="example"></a>示例  
 请参阅[承载 ActiveX 控件使用 ATL AXHost](../../atl/hosting-activex-controls-using-atl-axhost.md)有关使用示例`CreateControl`。  
  
##  <a name="createcontrolex"></a>CAxWindow::CreateControlEx  
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
 指向要创建控件的字符串的指针。 格式必须通过以下方式之一：  
  
-   例如"MSCAL ProgID。Calendar.7"  
  
-   例如"{8E27C92B-1264-101C-8A2F-040224009C02}"的 CLSID  
  
-   例如"http://www.microsoft.com"URL  
  
-   到如活动文档的引用"file://\\\Documents\MyDoc.doc"  
  
-   如的 HTML 片段"MSHTML:\<HTML >\<正文 > 这是一套文本\</b O >\</HTML >"  
  
    > [!NOTE]
    >  "MSHTML:"，以便它指定为 MSHTML 流必须在之前的 HTML 片段。 Windows Mobile 平台支持的 ProgID 和 CLSID。 Windows CE 嵌入平台中，Windows Mobile CE IE 支持支持以外的所有类型包括 ProgID，CLSID、 URL，都引用到活动文档时和的 HTML 片段。  
  
 `pStream`  
 [in]指向用于初始化的控件的属性流的指针。 可以是**NULL**。  
  
 `ppUnkContainer`  
 [out]将接收的指针的地址**IUnknown**的容器。 可以是**NULL**。  
  
 `ppUnkControl`  
 [out]将接收的指针的地址**IUnknown**的控件。 可以是**NULL**。  
  
 `iidSink`  
 [in]包含的对象上的传出接口的接口标识符。 可以是**IID_NULL**。  
  
 *punkSink*  
 [in]指向的指针**IUnknown**要连接到指定的包含对象上的连接点的接收器对象的接口`iidSink`。  
  
 `dwResID`  
 [in]HTML 资源的资源 ID。 将创建并使用指定的资源加载 WebBrowser 控件。  
  
### <a name="return-value"></a>返回值  
 标准 `HRESULT` 值。  
  
### <a name="remarks"></a>备注  
 此方法类似于是[CAxWindow::CreateControl](#createcontrol)，而与该方法中，`CreateControlEx`还允许您接收到新创建的控件的接口指针并将事件接收器设置为接收控件触发的事件。  
  
 请参阅[CAxWindow2T::CreateControlLicEx](../../atl/reference/caxwindow2t-class.md#createcontrollicex)若要创建，初始化和承载授权的 ActiveX 控件。  
  
### <a name="example"></a>示例  
 请参阅[承载 ActiveX 控件使用 ATL AXHost](../../atl/hosting-activex-controls-using-atl-axhost.md)有关使用示例`CreateControlEx`。  
  
##  <a name="getwndclassname"></a>CAxWindow::GetWndClassName  
 检索窗口类的名称。  
  
```
static LPCTSTR GetWndClassName();
```  
  
### <a name="return-value"></a>返回值  
 指向包含可以承载未授权的 ActiveX 控件的窗口类名称的字符串的指针。  
  
##  <a name="operator_eq"></a>CAxWindow::operator =  
 将分配`HWND`到一个现有`CAxWindow`对象。  
  
```
CAxWindow<TBase>& operator=(HWND hWnd);
```  
  
### <a name="parameters"></a>参数  
 `hWnd`  
 现有的窗口的句柄。  
  
### <a name="return-value"></a>返回值  
 返回对当前 `CAxWindow` 对象的引用。  
  
##  <a name="querycontrol"></a>CAxWindow::QueryControl  
 检索托管控件的指定的接口。  
  
```
HRESULT QueryControl(REFIID iid, void** ppUnk);
template <class  Q>
HRESULT QueryControl(Q** ppUnk);
```  
  
### <a name="parameters"></a>参数  
 `iid`  
 [in]指定控件的接口的 IID。  
  
 `ppUnk`  
 [out]指向控件的接口的指针。 此方法的模板版本，在没有引用 ID 无需只要传递具有关联的 UUID 的类型化的接口。  
  
 `Q`  
 [in]正在查询的接口。  
  
### <a name="return-value"></a>返回值  
 标准 `HRESULT` 值。  
  
##  <a name="queryhost"></a>CAxWindow::QueryHost  
 返回指定的接口的主机。  
  
```
HRESULT QueryHost(REFIID iid, void** ppUnk);
template <class  Q>
HRESULT QueryHost(Q** ppUnk);
```  
  
### <a name="parameters"></a>参数  
 `iid`  
 [in]指定控件的接口的 IID。  
  
 `ppUnk`  
 [out]指向主机上的接口的指针。 此方法的模板版本，在没有引用 ID 无需只要传递具有关联的 UUID 的类型化的接口。  
  
 `Q`  
 [in]正在查询的接口。  
  
### <a name="return-value"></a>返回值  
 标准 `HRESULT` 值。  
  
### <a name="remarks"></a>备注  
 主机的接口允许访问实现的窗口承载代码的基础功能**AxWin**。  
  
##  <a name="setexternaldispatch"></a>CAxWindow::SetExternalDispatch  
 设置为使用的外部的调度接口`CAxWindow`对象。  
  
```
HRESULT SetExternalDispatch(IDispatch* pDisp);
```  
  
### <a name="parameters"></a>参数  
 `pDisp`  
 [in]指向的指针`IDispatch`接口。  
  
### <a name="return-value"></a>返回值  
 标准 `HRESULT` 值。  
  
##  <a name="setexternaluihandler"></a>CAxWindow::SetExternalUIHandler  
 设置外部[IDocHostUIHandlerDispatch](../../atl/reference/idochostuihandlerdispatch-interface.md)接口`CAxWindow`对象。  
  
```
HRESULT SetExternalUIHandler(IDocHostUIHandlerDispatch* pUIHandler);
```  
  
### <a name="parameters"></a>参数  
 *pUIHandler*  
 [in]指向的指针**IDocHostUIHandlerDispatch**接口。  
  
### <a name="return-value"></a>返回值  
 标准 `HRESULT` 值。  
  
### <a name="remarks"></a>备注  
 外部`IDocHostUIHandlerDispatch`查询主机的站点的控件使用接口`IDocHostUIHandlerDispatch`接口。 WebBrowser 控件是一个控件可完成此。  
  
## <a name="see-also"></a>请参阅  
 [ATLCON 示例](../../visual-cpp-samples.md)   
 [CWindow 类](../../atl/reference/cwindow-class.md)   
 [复合控件基础知识](../../atl/atl-composite-control-fundamentals.md)   
 [类概述](../../atl/atl-class-overview.md)   
 [控件包含常见问题](../../atl/atl-control-containment-faq.md)

