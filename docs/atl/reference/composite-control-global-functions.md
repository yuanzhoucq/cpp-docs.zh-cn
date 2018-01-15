---
title: "复合控件全局函数 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- atlhost/ATL::AtlAxDialogBox
- atlhost/ATL::AtlAxCreateDialog
- atlhost/ATL::AtlAxCreateControl
- atlhost/ATL::AtlAxCreateControlEx
- atlhost/ATL::AtlAxCreateControlLic
- atlhost/ATL::AtlAxCreateControlLicEx
- atlhost/ATL::AtlAxAttachControl
- atlhost/ATL::AtlAxGetHost
- atlhost/ATL::AtlAxGetControl
- atlhost/ATL::AtlSetChildSite
- atlhost/ATL::AtlAxWinInit
- atlhost/ATL::AtlAxWinTerm
- atlhost/ATL::AtlGetObjectSourceInterface
dev_langs: C++
helpviewer_keywords: composite controls, global functions
ms.assetid: 536884cd-e863-4c7a-ab0a-604dc60a0bbe
caps.latest.revision: "20"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: d5a062ea9477df9db026c75bc775df804ed86da4
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="composite-control-global-functions"></a>复合控件全局函数
用于创建对话框框中，以及用于创建、 承载和授权 ActiveX 控件，则这些函数提供支持。  
  
> [!IMPORTANT]
>  下表中列出的函数不能在 Windows 运行时中执行的应用程序。  
  
|||  
|-|-|  
|[AtlAxDialogBox](#atlaxdialogbox)|从用户提供的对话框模板创建模式对话框。 生成的对话框中可以包含 ActiveX 控件。|  
|[AtlAxCreateDialog](#atlaxcreatedialog)|从用户提供的对话框模板创建无模式对话框。 生成的对话框中可以包含 ActiveX 控件。|  
|[AtlAxCreateControl](#atlaxcreatecontrol)|创建 ActiveX 控件，初始化它并在指定窗口中承载它。|  
|[AtlAxCreateControlEx](#atlaxcreatecontrolex)|创建 ActiveX 控件，初始化它，承载它在指定窗口中，并从控件中检索的接口指针 （或指针）。|  
|[AtlAxCreateControlLic](#atlaxcreatecontrollic)|创建授权的 ActiveX 控件，初始化它并在指定窗口中承载它。|  
|[AtlAxCreateControlLicEx](#atlaxcreatecontrollicex)|创建授权的 ActiveX 控件、 对其进行初始化，承载它在指定窗口中，并从控件中检索的接口指针 （或指针）。|  
|[AtlAxAttachControl](#atlaxattachcontrol)|将以前创建的控件附加到指定窗口。|  
|[AtlAxGetHost](#atlaxgethost)|用于获取指向指定窗口 （如果有） 的容器的直接接口指针提供其句柄。|  
|[AtlAxGetControl](#atlaxgetcontrol)|用于获取在指定窗口 （如果有），包含的控件的直接接口指针提供其句柄。|  
|[AtlSetChildSite](#atlsetchildsite)|初始化**IUnknown**的子站点。|  
|[AtlAxWinInit](#atlaxwininit)|初始化 AxWin 对象的宿主代码。|  
|[AtlAxWinTerm](#atlaxwinterm)|取消初始化 AxWin 对象的宿主代码。|  
|[AtlGetObjectSourceInterface](#atlgetobjectsourceinterface)|返回有关的默认源接口的对象的信息。|  

## <a name="requirements"></a>惠?  
 **标头：** atlhost.h  

##  <a name="atlaxdialogbox"></a>AtlAxDialogBox  
 从用户提供的对话框模板创建模式对话框。  
   
```
ATLAPI_(int) AtlAxDialogBox(
    HINSTANCE hInstance,
    LPCWSTR lpTemplateName,
    HWND hWndParent,
    DLGPROC lpDialogProc,
    LPARAM dwInitParam);
```  
  
### <a name="parameters"></a>参数  
 `hInstance`  
 [in]标识其可执行文件包含对话框模板的模块的实例。  
  
 `lpTemplateName`  
 [in]标识对话框模板。 此参数是指向指定的对话框模板的名称的以 null 结尾的字符字符串的指针或指定的对话框模板的资源标识符的整数值。 如果该参数指定的资源标识符，其高序位字必须是零，并且其低序位字必须包含的标识符。 你可以使用[MAKEINTRESOURCE](http://msdn.microsoft.com/library/windows/desktop/ms648029)宏来创建此值。  
  
 `hWndParent`  
 [in]标识拥有对话框中的窗口。  
  
 `lpDialogProc`  
 [in]指向对话框过程。 有关对话框过程的详细信息，请参阅[DialogProc](http://msdn.microsoft.com/library/windows/desktop/ms645469)。  
  
 `dwInitParam`  
 [in]指定要传递给的对话框中的值**lParam**参数**WM_INITDIALOG**消息。  
  
### <a name="return-value"></a>返回值  
 一个标准的 HRESULT 值。  
  
### <a name="remarks"></a>备注  
 若要使用**AtlAxDialogBox**与包含 ActiveX 控件的对话框模板，请指定有效的**CLSID**， **APPID**或 URL 字符串作为*文本*字段**控件**一部分对话框资源，以及"AtlAxWin80"作为*类名*字段相同的部分。 以下内容演示的哪些有效**控件**部分可能如下所示：  
  
```  
CONTROL    "{04FE35E9-ADBC-4f1d-83FE-8FA4D1F71C7F}", IDC_TEST,  
    "AtlAxWin80", WS_GROUP | WS_TABSTOP, 0, 0, 100, 100  
```  
  
 编辑资源脚本的详细信息，请参阅[如何： 以文本格式打开资源脚本文件](../../windows/how-to-open-a-resource-script-file-in-text-format.md)。 控制资源定义语句的详细信息，请参阅[常见控制参数](http://msdn.microsoft.com/library/windows/desktop/aa380902)下 Windows SDK*: SDK 工具*。  
  
 有关常规中的对话框的详细信息，请参阅[对话框](http://msdn.microsoft.com/library/windows/desktop/ms645452)和[CreateDialogParam](http://msdn.microsoft.com/library/windows/desktop/ms645445) Windows SDK 中。  
  
##  <a name="atlaxcreatedialog"></a>AtlAxCreateDialog  
 从用户提供的对话框模板创建无模式对话框。  
  
```
ATLAPI_(HWND) AtlAxCreateDialog(
    HINSTANCE hInstance,
    LPCWSTR lpTemplateName,
    HWND hWndParent,
    DLGPROC lpDialogProc,
    LPARAM dwInitParam);
```  
  
### <a name="parameters"></a>参数  
 `hInstance`  
 [in]标识其可执行文件包含对话框模板的模块的实例。  
  
 `lpTemplateName`  
 [in]标识对话框模板。 此参数是指向指定的对话框模板的名称的以 null 结尾的字符字符串的指针或指定的对话框模板的资源标识符的整数值。 如果该参数指定的资源标识符，其高序位字必须是零，并且其低序位字必须包含的标识符。 你可以使用[MAKEINTRESOURCE](http://msdn.microsoft.com/library/windows/desktop/ms648029)宏来创建此值。  
  
 `hWndParent`  
 [in]标识拥有对话框中的窗口。  
  
 `lpDialogProc`  
 [in]指向对话框过程。 有关对话框过程的详细信息，请参阅[DialogProc](http://msdn.microsoft.com/library/windows/desktop/ms645469)。  
  
 `dwInitParam`  
 [in]指定要传递给的对话框中的值**lParam**参数**WM_INITDIALOG**消息。  
  
### <a name="return-value"></a>返回值  
 一个标准的 HRESULT 值。  
  
### <a name="remarks"></a>备注  
 生成的对话框中可以包含 ActiveX 控件。  
  
 请参阅[CreateDialog](http://msdn.microsoft.com/library/windows/desktop/ms645434)和[CreateDialogParam](http://msdn.microsoft.com/library/windows/desktop/ms645445) Windows SDK 中。  
  
##  <a name="atlaxcreatecontrol"></a>AtlAxCreateControl  
 创建 ActiveX 控件，初始化它并在指定窗口中承载它。  
  

```
ATLAPI AtlAxCreateControl(
    LPCOLESTR lpszName,
    HWND hWnd,
    IStream* pStream,
    IUnknown** ppUnkContainer);
```  
  
### <a name="parameters"></a>参数  
 `lpszName`  
 指向要传递到的控件的字符串的指针。 格式必须通过以下方式之一：  
  
-   例如"MSCAL ProgID。Calendar.7"  
  
-   例如"{8E27C92B-1264-101C-8A2F-040224009C02}"的 CLSID  
  
-   例如"http://www.microsoft.com"URL  
  
-   到如活动文档的引用"file://\\\Documents\MyDoc.doc"  
  
-   如的 HTML 片段"MSHTML:\<HTML >\<正文 > 这是一套文本\</b O >\</HTML >"  
  
    > [!NOTE]
    >  "MSHTML:"，以便它指定为 MSHTML 流必须在之前的 HTML 片段。  
  
 `hWnd`  
 [in]控件将附加到的窗口的句柄。  
  
 `pStream`  
 [in]指向用于初始化的控件的属性流的指针。 可以是**NULL**。  
  
 `ppUnkContainer`  
 [out]将接收的指针的地址**IUnknown**的容器。 可以是**NULL**。  
  
### <a name="return-value"></a>返回值  
 一个标准的 HRESULT 值。  
  
### <a name="remarks"></a>备注  
 此全局函数可与调用相同的结果[AtlAxCreateControlEx](#atlaxcreatecontrolex)( `lpszName` **，** `hWnd` **，** `pStream` **、 NULL、 空、 NULL、 空**);。  
  
 若要创建授权的 ActiveX 控件，请参阅[AtlAxCreateControlLic](#atlaxcreatecontrollic)。  
  
##  <a name="atlaxcreatecontrolex"></a>AtlAxCreateControlEx  
 创建 ActiveX 控件，初始化它并在指定窗口中承载它。 也可以创建新控件的接口指针和事件接收器。  
  
```
ATLAPI AtlAxCreateControlEx(
    LPCOLESTR lpszName,
    HWND hWnd,
    IStream* pStream,
    IUnknown** ppUnkContainer,
    IUnknown** ppUnkControl,
    REFIID iidSink = IID_NULL,
    IUnknown* punkSink = NULL);
```  
  
### <a name="parameters"></a>参数  
 `lpszName`  
 指向要传递到的控件的字符串的指针。 格式必须通过以下方式之一：  
  
-   例如"MSCAL ProgID。Calendar.7"  
  
-   例如"{8E27C92B-1264-101C-8A2F-040224009C02}"的 CLSID  
  
-   例如"http://www.microsoft.com"URL  
  
-   到如活动文档的引用"file://\\\Documents\MyDoc.doc"  
  
-   如的 HTML 片段"MSHTML:\<HTML >\<正文 > 这是一套文本\</b O >\</HTML >"  
  
    > [!NOTE]
    >  "MSHTML:"，以便它指定为 MSHTML 流必须在之前的 HTML 片段。  
  
 `hWnd`  
 [in]控件将附加到的窗口的句柄。  
  
 `pStream`  
 [in]指向用于初始化的控件的属性流的指针。 可以是**NULL**。  
  
 `ppUnkContainer`  
 [out]将接收的指针的地址**IUnknown**的容器。 可以是**NULL**。  
  
 `ppUnkControl`  
 [out]将接收的指针的地址**IUnknown**的创建的控件。 可以是**NULL**。  
  
 `iidSink`  
 包含的对象上的传出接口的接口标识符。  
  
 *punkSink*  
 指向的指针**IUnknown**要连接到由指定的连接点的接收器对象的接口`iidSink`上包含的对象已成功创建后的包含对象。  
  
### <a name="return-value"></a>返回值  
 一个标准的 HRESULT 值。  
  
### <a name="remarks"></a>备注  
 `AtlAxCreateControlEx`类似于[AtlAxCreateControl](#atlaxcreatecontrol)但还允许您接收到新创建的控件的接口指针并将事件接收器设置为接收控件触发的事件。  
  
 若要创建授权的 ActiveX 控件，请参阅[AtlAxCreateControlLicEx](#atlaxcreatecontrollicex)。  
  
##  <a name="atlaxcreatecontrollic"></a>AtlAxCreateControlLic  
 创建授权的 ActiveX 控件，初始化它并在指定窗口中承载它。  

```
ATLAPI AtlAxCreateControlLic(
    LPCOLESTR lpszName,
    HWND hWnd,
    IStream* pStream,
    IUnknown** ppUnkContainer,
    BSTR bstrLic = NULL);
```  
  
### <a name="parameters"></a>参数  
 `lpszName`  
 指向要传递到的控件的字符串的指针。 格式必须通过以下方式之一：  
  
-   例如"MSCAL ProgID。Calendar.7"  
  
-   例如"{8E27C92B-1264-101C-8A2F-040224009C02}"的 CLSID  
  
-   例如"http://www.microsoft.com"URL  
  
-   到如活动文档的引用"file://\\\Documents\MyDoc.doc"  
  
-   如的 HTML 片段"MSHTML:\<HTML >\<正文 > 这是一套文本\</b O >\</HTML >"  
  
    > [!NOTE]
    >  "MSHTML:"，以便它指定为 MSHTML 流必须在之前的 HTML 片段。  
  
 `hWnd`  
 控件将附加到的窗口的句柄。  
  
 `pStream`  
 指向用于初始化的控件的属性流的指针。 可以是**NULL**。  
  
 `ppUnkContainer`  
 将接收的指针的地址**IUnknown**的容器。 可以是**NULL**。  
  
 `bstrLic`  
 包含控件的许可证 BSTR。  
  
### <a name="return-value"></a>返回值  
 一个标准的 HRESULT 值。  
  
### <a name="example"></a>示例  
 请参阅[承载 ActiveX 控件使用 ATL AXHost](../../atl/hosting-activex-controls-using-atl-axhost.md)有关如何使用的示例`AtlAxCreateControlLic`。  
  
##  <a name="atlaxcreatecontrollicex"></a>AtlAxCreateControlLicEx  
 创建授权的 ActiveX 控件，初始化它并在指定窗口中承载它。 也可以创建新控件的接口指针和事件接收器。  
  
```
ATLAPI AtlAxCreateControlLicEx(
    LPCOLESTR lpszName,
    HWND hWnd,
    IStream* pStream,
    IUnknown** ppUnkContainer,
    IUnknown** ppUnkControl,
    REFIID iidSink = IID_NULL,
    IUnknown* punkSink = NULL,
    BSTR bstrLic = NULL);
```  
  
### <a name="parameters"></a>参数  
 `lpszName`  
 指向要传递到的控件的字符串的指针。 格式必须通过以下方式之一：  
  
-   例如"MSCAL ProgID。Calendar.7"  
  
-   例如"{8E27C92B-1264-101C-8A2F-040224009C02}"的 CLSID  
  
-   例如"http://www.microsoft.com"URL  
  
-   到如活动文档的引用"file://\\\Documents\MyDoc.doc"  
  
-   如的 HTML 片段"MSHTML:\<HTML >\<正文 > 这是一套文本\</b O >\</HTML >"  
  
    > [!NOTE]
    >  "MSHTML:"，以便它指定为 MSHTML 流必须在之前的 HTML 片段。  
  
 `hWnd`  
 控件将附加到的窗口的句柄。  
  
 `pStream`  
 指向用于初始化的控件的属性流的指针。 可以是**NULL**。  
  
 `ppUnkContainer`  
 将接收的指针的地址**IUnknown**的容器。 可以是**NULL**。  
  
 `ppUnkControl`  
 [out]将接收的指针的地址**IUnknown**的创建的控件。 可以是**NULL**。  
  
 `iidSink`  
 包含的对象上的传出接口的接口标识符。  
  
 *punkSink*  
 指向的指针**IUnknown**要连接到由指定的连接点的接收器对象的接口`iidSink`上包含的对象已成功创建后的包含对象。  
  
 `bstrLic`  
 包含控件的许可证 BSTR。  
  
### <a name="return-value"></a>返回值  
 一个标准的 HRESULT 值。  
  
### <a name="remarks"></a>备注  
 `AtlAxCreateControlLicEx`类似于[AtlAxCreateControlLic](#atlaxcreatecontrollic)但还允许您接收到新创建的控件的接口指针并将事件接收器设置为接收控件触发的事件。  
  
### <a name="example"></a>示例  
 请参阅[承载 ActiveX 控件使用 ATL AXHost](../../atl/hosting-activex-controls-using-atl-axhost.md)有关如何使用的示例`AtlAxCreateControlLicEx`。  
  
##  <a name="atlaxattachcontrol"></a>AtlAxAttachControl  
 将以前创建的控件附加到指定窗口。  
  
```
ATLAPI AtlAxAttachControl(
    IUnknown* pControl,
    HWND hWnd,
    IUnknown** ppUnkContainer);
```  
  
### <a name="parameters"></a>参数  
 `pControl`  
 [in]指向的指针**IUnknown**的控件。  
  
 `hWnd`  
 [in]将主机控件的窗口的句柄。  
  
 `ppUnkContainer`  
 [out]指针到指向**IUnknown**的容器对象。  
  
### <a name="return-value"></a>返回值  
 一个标准的 HRESULT 值。  
  
### <a name="remarks"></a>备注  
 使用[AtlAxCreateControlEx](#atlaxcreatecontrolex)和[AtlAxCreateControl](#atlaxcreatecontrol)可以同时创建并附加一个控件。  
  
> [!NOTE]
>  要附加的控件对象必须正确初始化，然后再调`AtlAxAttachControl`。  
  
##  <a name="atlaxgethost"></a>AtlAxGetHost  
 获取指向指定窗口（如果有）的容器的直接接口指针（在给定容器的句柄的情况下）。  
  
```
ATLAPI AtlAxGetHost(HWND h, IUnknown** pp);
```  
  
### <a name="parameters"></a>参数  
 `h`  
 [in]托管控件窗口的句柄。  
  
 `pp`  
 [out]**IUnknown**的容器的控件。  
  
### <a name="return-value"></a>返回值  
 一个标准的 HRESULT 值。  
  
##  <a name="atlaxgetcontrol"></a>AtlAxGetControl  
 获取指向包含在指定窗口内的控件的直接接口指针（在给定控件的句柄的情况下）。  
  
```
ATLAPI AtlAxGetControl(HWND h, IUnknown** pp);
```  
  
### <a name="parameters"></a>参数  
 `h`  
 [in]托管控件窗口的句柄。  
  
 `pp`  
 [out]**IUnknown**正在承载的控件。  
  
### <a name="return-value"></a>返回值  
 一个标准的 HRESULT 值。  
  
##  <a name="atlsetchildsite"></a>AtlSetChildSite  
 调用此函数可将子对象的站点设置**IUnknown**的父对象。  
  
```
HRESULT AtlSetChildSite(IUnknown* punkChild, IUnknown* punkParent);
```  
  
### <a name="parameters"></a>参数  
 *punkChild*  
 [in]指向的指针**IUnknown**子接口。  
  
 `punkParent`  
 [in]指向的指针**IUnknown**的父级的接口。  
  
### <a name="return-value"></a>返回值  
 一个标准的 HRESULT 值。  
  
##  <a name="atlaxwininit"></a>AtlAxWinInit  
 此函数初始化 ATL 的控件承载代码通过注册**"AtlAxWin80"**和**"AtlAxWinLic80"**窗口类以及一些自定义窗口消息。  
  
```
ATLAPI_(BOOL) AtlAxWinInit();
```  
  
### <a name="return-value"></a>返回值  
 如果控件承载代码的初始化成功; 则为非 0否则为**FALSE**。  
  
### <a name="remarks"></a>备注  
 使用 ATL 控件承载 API 之前，必须调用此函数。 对此函数调用**"AtlAxWin"**窗口类可在调用[CreateWindow](http://msdn.microsoft.com/library/windows/desktop/ms632679)或[CreateWindowEx](http://msdn.microsoft.com/library/windows/desktop/ms632680)，如 Windows SDK 中所述。  

##  <a name="atlaxwinterm"></a>AtlAxWinTerm  
 此函数取消初始化 ATL 的控件承载代码通过注销**"AtlAxWin80"**和**"AtlAxWinLic80"**窗口类。  
  
```
inline BOOL AtlAxWinTerm();
```  
  
### <a name="return-value"></a>返回值  
 始终返回**TRUE**。  
  
### <a name="remarks"></a>备注  
 此函数只调用[UnregisterClass](http://msdn.microsoft.com/library/windows/desktop/ms644899) Windows SDK 中所述。  
  
 调用此函数已被销毁所有现有主机窗口，如果调用之后进行清理[AtlAxWinInit](#atlaxwininit)并且不再需要创建主机窗口。 如果你不调用此函数，窗口类将自动取消注册在进程终止时。  
  
##  <a name="atlgetobjectsourceinterface"></a>AtlGetObjectSourceInterface  
 调用此函数可检索有关对象的默认源接口的信息。  
  
```
ATLAPI AtlGetObjectSourceInterface(
    IUnknown* punkObj,
    GUID* plibid,
    IID* piid,
    unsigned short* pdwMajor,
    unsigned short* pdwMinor);
```  
  
### <a name="parameters"></a>参数  
 `punkObj`  
 [in]指向为其返回信息的对象的指针。  
  
 `plibid`  
 [out]指向包含源接口的定义的类型库的 LIBID 的指针。  
  
 `piid`  
 [out]指向对象的默认源接口的接口 ID 的指针。  
  
 *pdwMajor*  
 [out]指向包含源接口的定义的类型库的主版本号的指针。  
  
 *pdwMinor*  
 [out]指向包含源接口的定义的类型库的次版本号的指针。  
  
### <a name="return-value"></a>返回值  
 一个标准的 HRESULT 值。  
  
### <a name="remarks"></a>备注  
 `AtlGetObjectSourceInterface`可以为您提供的默认源接口，以及 LIBID 和主要的接口 ID 和描述该接口的类型库的次版本号。  
  
> [!NOTE]
>  此函数可成功检索所请求的信息，该对象表示由`punkObj`必须实现`IDispatch`(并返回类型信息通过**IDispatch::GetTypeInfo**) 以及它还必须实现`IProvideClassInfo2`或`IPersist`。 源接口的类型信息必须处于相同的类型库的类型信息作为`IDispatch`。  
  
### <a name="example"></a>示例  
 下面的示例显示可以如何定义事件接收器类中， `CEasySink`，可以将传递到的模板参数的数目可减少`IDispEventImpl`到裸机 essentials。 `EasyAdvise`和`EasyUnadvise`使用`AtlGetObjectSourceInterface`初始化[IDispEventImpl](../../atl/reference/idispeventimpl-class.md)成员之前调用[DispEventAdvise](idispeventsimpleimpl-class.md#dispeventadvise)或[DispEventUnadvise](idispeventsimpleimpl-class.md#dispeventunadvise)。  
  
 [!code-cpp[NVC_ATL_Windowing#93](../../atl/codesnippet/cpp/composite-control-global-functions_1.h)]  
  
## <a name="see-also"></a>请参阅  
 [函数](../../atl/reference/atl-functions.md)   
 [复合控件宏](../../atl/reference/composite-control-macros.md)
