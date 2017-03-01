---
title: "IOleObjectImpl 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- ATL.IOleObjectImpl
- ATL.IOleObjectImpl<T>
- ATL::IOleObjectImpl
- ATL::IOleObjectImpl<T>
- IOleObjectImpl
dev_langs:
- C++
helpviewer_keywords:
- ActiveX controls [C++], communication between container and control
- IOleObject, ATL implementation
- IOleObjectImpl class
ms.assetid: 59750b2d-1633-4a51-a4c2-6455b6b90c45
caps.latest.revision: 20
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
ms.sourcegitcommit: 604a4bf49490ad2599c857eb3afd527d67e1e25b
ms.openlocfilehash: b0b471b997bfdb4062f00b40864c347db78b114a
ms.lasthandoff: 02/24/2017

---
# <a name="ioleobjectimpl-class"></a>IOleObjectImpl 类
此类实现**IUnknown**并且是通过该容器与控件进行通信的主要接口。  
  
> [!IMPORTANT]
>  该类及其成员无法在 [!INCLUDE[wrt](../../atl/reference/includes/wrt_md.md)]中执行的应用程序中使用。  
  
## <a name="syntax"></a>语法  
  
```
template<class T>  
class ATL_NO_VTABLE IOleObjectImpl : public IOleObject
```  
  
#### <a name="parameters"></a>参数  
 `T`  
 您的类，派生自`IOleObjectImpl`。  
  
## <a name="members"></a>成员  
  
### <a name="public-methods"></a>公共方法  
  
|名称|说明|  
|----------|-----------------|  
|[IOleObjectImpl::Advise](#advise)|建立与该控件的通知连接。|  
|[IOleObjectImpl::Close](#close)|从运行加载更改控件状态。|  
|[IOleObjectImpl::DoVerb](#doverb)|指示要执行其中一个枚举的操作的控件。|  
|[IOleObjectImpl::DoVerbDiscardUndo](#doverbdiscardundo)|指示要放弃任何正在维护的还原状态的控件。|  
|[IOleObjectImpl::DoVerbHide](#doverbhide)|指示要从视图中删除其用户界面的控件。|  
|[IOleObjectImpl::DoVerbInPlaceActivate](#doverbinplaceactivate)|运行该控件并安装其窗口，但不会安装该控件的用户界面。|  
|[IOleObjectImpl::DoVerbOpen](#doverbopen)|使控件在单独的窗口是打开编辑。|  
|[IOleObjectImpl::DoVerbPrimary](#doverbprimary)|当用户双击该控件，则执行指定的操作。 控件定义，通常要激活的操作中就地控件。|  
|[IOleObjectImpl::DoVerbShow](#doverbshow)|向用户显示的新插入的控件。|  
|[IOleObjectImpl::DoVerbUIActivate](#doverbuiactivate)|被控制就地激活，并显示控件的用户界面，如菜单和工具栏。|  
|[IOleObjectImpl::EnumAdvise](#enumadvise)|枚举该控件的通知连接。|  
|[IOleObjectImpl::EnumVerbs](#enumverbs)|枚举该控件的操作。|  
|[IOleObjectImpl::GetClientSite](#getclientsite)|检索控件的客户端的站点。|  
|[IOleObjectImpl::GetClipboardData](#getclipboarddata)|从剪贴板检索数据。 ATL 实现返回**E_NOTIMPL**。|  
|[IOleObjectImpl::GetExtent](#getextent)|检索控件的显示区域的范围。|  
|[IOleObjectImpl::GetMiscStatus](#getmiscstatus)|检索控件的状态。|  
|[IOleObjectImpl::GetMoniker](#getmoniker)|检索控件的标记。 ATL 实现返回**E_NOTIMPL**。|  
|[IOleObjectImpl::GetUserClassID](#getuserclassid)|检索控件的类标识符。|  
|[IOleObjectImpl::GetUserType](#getusertype)|检索控件的用户类型名称。|  
|[IOleObjectImpl::InitFromData](#initfromdata)|初始化从所选数据的控件。 ATL 实现返回**E_NOTIMPL**。|  
|[IOleObjectImpl::IsUpToDate](#isuptodate)|如果该控件是最新的检查。 ATL 实现返回`S_OK`。|  
|[IOleObjectImpl::OnPostVerbDiscardUndo](#onpostverbdiscardundo)|由调用[DoVerbDiscardUndo](#doverbdiscardundo)放弃撤消状态之后。|  
|[IOleObjectImpl::OnPostVerbHide](#onpostverbhide)|由调用[DoVerbHide](#doverbhide)则隐藏该控件后。|  
|[IOleObjectImpl::OnPostVerbInPlaceActivate](#onpostverbinplaceactivate)|由调用[DoVerbInPlaceActivate](#doverbinplaceactivate)就地激活该控件后。|  
|[IOleObjectImpl::OnPostVerbOpen](#onpostverbopen)|由调用[DoVerbOpen](#doverbopen)已为编辑的单独窗口中打开该控件后。|  
|[IOleObjectImpl::OnPostVerbShow](#onpostverbshow)|由调用[DoVerbShow](#doverbshow)控件进行可见后。|  
|[IOleObjectImpl::OnPostVerbUIActivate](#onpostverbuiactivate)|由调用[DoVerbUIActivate](#doverbuiactivate)激活了控件的用户界面。|  
|[IOleObjectImpl::OnPreVerbDiscardUndo](#onpreverbdiscardundo)|由调用[DoVerbDiscardUndo](#doverbdiscardundo)撤消之前，状态将被丢弃。|  
|[IOleObjectImpl::OnPreVerbHide](#onpreverbhide)|由调用[DoVerbHide](#doverbhide)隐藏控件之前。|  
|[IOleObjectImpl::OnPreVerbInPlaceActivate](#onpreverbinplaceactivate)|由调用[DoVerbInPlaceActivate](#doverbinplaceactivate)就地激活控件之前。|  
|[IOleObjectImpl::OnPreVerbOpen](#onpreverbopen)|由调用[DoVerbOpen](#doverbopen)已为编辑的单独窗口中打开该控件之前。|  
|[IOleObjectImpl::OnPreVerbShow](#onpreverbshow)|由调用[DoVerbShow](#doverbshow)控件已可见之前。|  
|[IOleObjectImpl::OnPreVerbUIActivate](#onpreverbuiactivate)|由调用[DoVerbUIActivate](#doverbuiactivate)控件的用户界面已被激活之前。|  
|[IOleObjectImpl::SetClientSite](#setclientsite)|该控件将告知其客户端站点容器中。|  
|[IOleObjectImpl::SetColorScheme](#setcolorscheme)|如果有的话，给控件的应用程序，建议配色方案。 ATL 实现返回**E_NOTIMPL**。|  
|[IOleObjectImpl::SetExtent](#setextent)|设置控件的显示区域的程度。|  
|[IOleObjectImpl::SetHostNames](#sethostnames)|指示控件的容器应用程序和容器文档的名称。|  
|[IOleObjectImpl::SetMoniker](#setmoniker)|其标记为可告知控件。 ATL 实现返回**E_NOTIMPL**。|  
|[IOleObjectImpl::Unadvise](#unadvise)|删除与该控件的通知连接。|  
|[IOleObjectImpl::Update](#update)|可更新控件。 ATL 实现返回`S_OK`。|  
  
## <a name="remarks"></a>备注  
 [IOleObject](http://msdn.microsoft.com/library/windows/desktop/dd542709)接口是通过该容器与控件进行通信的主要接口。 类`IOleObjectImpl`提供此接口的默认实现，并实现**IUnknown**中调试设备信息发送给转储生成。  
  
 **相关文章** [ATL 教程](../../atl/active-template-library-atl-tutorial.md)，[创建 ATL 项目](../../atl/reference/creating-an-atl-project.md)  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `IOleObject`  
  
 `IOleObjectImpl`  
  
## <a name="requirements"></a>要求  
 **标头︰** atlctl.h  
  
##  <a name="a-nameadvisea--ioleobjectimpladvise"></a><a name="advise"></a>IOleObjectImpl::Advise  
 建立与该控件的通知连接。  
  
```
STDMETHOD(Advise)(
    IAdviseSink* pAdvSink,
    DWORD* pdwConnection);
```  
  
### <a name="remarks"></a>备注  
 请参阅[IOleObject::Advise](http://msdn.microsoft.com/library/windows/desktop/ms686573)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-nameclosea--ioleobjectimplclose"></a><a name="close"></a>IOleObjectImpl::Close  
 从运行加载更改控件状态。  
  
```
STDMETHOD(Close)(DWORD dwSaveOption);
```  
  
### <a name="remarks"></a>备注  
 停用该控件，并销毁控制窗口，如果它存在。 如果该控件类数据成员[CComControlBase::m_bRequiresSave](../../atl/reference/ccomcontrolbase-class.md#m_brequiressave)是**TRUE**和`dwSaveOption`参数为`OLECLOSE_SAVEIFDIRTY`或`OLECLOSE_PROMPTSAVE`，在关闭前保存控件属性。  
  
 指针在控件类数据成员中持有[CComControlBase::m_spInPlaceSite](../../atl/reference/ccomcontrolbase-class.md#m_spinplacesite)和[CComControlBase::m_spAdviseSink](../../atl/reference/ccomcontrolbase-class.md#m_spadvisesink)会被释放，和数据成员[CComControlBase::m_bNegotiatedWnd](../../atl/reference/ccomcontrolbase-class.md#m_bnegotiatedwnd)， [CComControlBase::m_bWndless](../../atl/reference/ccomcontrolbase-class.md#m_bwndless)，和[CComControlBase::m_bInPlaceSiteEx](../../atl/reference/ccomcontrolbase-class.md#m_binplacesiteex)设置为**FALSE**。  
  
 请参阅[IOleObject::Close](http://msdn.microsoft.com/library/windows/desktop/ms683922)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-namedoverba--ioleobjectimpldoverb"></a><a name="doverb"></a>IOleObjectImpl::DoVerb  
 指示要执行其中一个枚举的操作的控件。  
  
```
STDMETHOD(DoVerb)(
    LONG iVerb,
    LPMSG /* pMsg */,
    IOleClientSite* pActiveSite,
    LONG /* lindex */,
    HWND hwndParent,
    LPCRECT lprcPosRect);
```  
  
### <a name="remarks"></a>备注  
 具体取决于值`iVerb`，ATL 之一`DoVerb`帮助器函数调用，如下所示︰  
  
|*iVerb*值|调用 DoVerb 帮助器函数|  
|-------------------|-----------------------------------|  
|**OLEIVERB_DISCARDUNDOSTATE**|[DoVerbDiscardUndo](#doverbdiscardundo)|  
|`OLEIVERB_HIDE`|[DoVerbHide](#doverbhide)|  
|**OLEIVERB_INPLACEACTIVATE**|[DoVerbInPlaceActivate](#doverbinplaceactivate)|  
|`OLEIVERB_OPEN`|[DoVerbOpen](#doverbopen)|  
|`OLEIVERB_PRIMARY`|[DoVerbPrimary](#doverbprimary)|  
|**OLEIVERB_PROPERTIES**|[CComControlBase::DoVerbProperties](../../atl/reference/ccomcontrolbase-class.md#doverbproperties)|  
|`OLEIVERB_SHOW`|[DoVerbShow](#doverbshow)|  
|`OLEIVERB_UIACTIVATE`|[DoVerbUIActivate](#doverbuiactivate)|  
  
 请参阅[IOleObject::DoVerb](http://msdn.microsoft.com/library/windows/desktop/ms694508)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-namedoverbdiscardundoa--ioleobjectimpldoverbdiscardundo"></a><a name="doverbdiscardundo"></a>IOleObjectImpl::DoVerbDiscardUndo  
 指示要放弃任何正在维护的还原状态的控件。  
  
```
HRESULT DoVerbDiscardUndo(LPCRECT /* prcPosRect */, HWND /* hwndParent */);
```  
  
### <a name="parameters"></a>参数  
 `prcPosRec`  
 [in]指向容器的矩形想要绘制到的控件。  
  
 *hwndParent*  
 [in]包含控件的窗口句柄。  
  
### <a name="return-value"></a>返回值  
 返回 `S_OK`。  
  
##  <a name="a-namedoverbhidea--ioleobjectimpldoverbhide"></a><a name="doverbhide"></a>IOleObjectImpl::DoVerbHide  
 停用和删除控件的用户界面，并将隐藏控件。  
  
```
HRESULT DoVerbHide(LPCRECT /* prcPosRect */, HWND /* hwndParent */);
```  
  
### <a name="parameters"></a>参数  
 `prcPosRec`  
 [in]指向容器的矩形想要绘制到的控件。  
  
 *hwndParent*  
 [in]包含控件的窗口句柄。 不使用 ATL 实现中。  
  
### <a name="return-value"></a>返回值  
 返回 `S_OK`。  
  
##  <a name="a-namedoverbinplaceactivatea--ioleobjectimpldoverbinplaceactivate"></a><a name="doverbinplaceactivate"></a>IOleObjectImpl::DoVerbInPlaceActivate  
 运行该控件并安装其窗口，但不会安装该控件的用户界面。  
  
```
HRESULT DoVerbInPlaceActivate(LPCRECT prcPosRect, HWND /* hwndParent */);
```  
  
### <a name="parameters"></a>参数  
 `prcPosRec`  
 [in]指向容器的矩形想要绘制到的控件。  
  
 *hwndParent*  
 [in]包含控件的窗口句柄。 不使用 ATL 实现中。  
  
### <a name="return-value"></a>返回值  
 其中一个标准`HRESULT`值。  
  
### <a name="remarks"></a>备注  
 通过调用激活就地控件[CComControlBase::InPlaceActivate](../../atl/reference/ccomcontrolbase-class.md#inplaceactivate)。 除非控件类数据成员`m_bWindowOnly`是**TRUE**，`DoVerbInPlaceActivate`第一次尝试激活该控件作为无窗口控件 (可能只有容器支持[IOleInPlaceSiteWindowless](http://msdn.microsoft.com/library/windows/desktop/ms682300))。 如果失败，则函数尝试激活具有扩展功能的控件 (可能只有容器支持[IOleInPlaceSiteEx](http://msdn.microsoft.com/library/windows/desktop/ms693461))。 如果失败，则函数尝试激活的控件具有不扩展的功能 (可能只有容器支持[IOleInPlaceSite](http://msdn.microsoft.com/library/windows/desktop/ms686586))。 如果激活成功，该函数将通知容器控件已激活。  
  
##  <a name="a-namedoverbopena--ioleobjectimpldoverbopen"></a><a name="doverbopen"></a>IOleObjectImpl::DoVerbOpen  
 使控件在单独的窗口是打开编辑。  
  
```
HRESULT DoVerbOpen(LPCRECT /* prcPosRect */, HWND /* hwndParent */);
```  
  
### <a name="parameters"></a>参数  
 `prcPosRec`  
 [in]指向容器的矩形想要绘制到的控件。  
  
 *hwndParent*  
 [in]包含控件的窗口句柄。  
  
### <a name="return-value"></a>返回值  
 返回 `S_OK`。  
  
##  <a name="a-namedoverbprimarya--ioleobjectimpldoverbprimary"></a><a name="doverbprimary"></a>IOleObjectImpl::DoVerbPrimary  
 定义当用户双击该控件时采取的操作。  
  
```
HRESULT DoVerbPrimary(LPCRECT prcPosRect, HWND hwndParent);
```  
  
### <a name="parameters"></a>参数  
 `prcPosRec`  
 [in]指向容器的矩形想要绘制到的控件。  
  
 *hwndParent*  
 [in]包含控件的窗口句柄。  
  
### <a name="return-value"></a>返回值  
 其中一个标准`HRESULT`值。  
  
### <a name="remarks"></a>备注  
 默认情况下，设置为显示的属性页。 可以覆盖此设置在控件类中调用不同的行为，通过双击;例如，播放视频或转处于就地活动状态。  
  
##  <a name="a-namedoverbshowa--ioleobjectimpldoverbshow"></a><a name="doverbshow"></a>IOleObjectImpl::DoVerbShow  
 告知容器以使控件可见。  
  
```
HRESULT DoVerbShow(LPCRECT prcPosRect, HWND /* hwndParent */);
```  
  
### <a name="parameters"></a>参数  
 `prcPosRec`  
 [in]指向容器的矩形想要绘制到的控件。  
  
 *hwndParent*  
 [in]包含控件的窗口句柄。 不使用 ATL 实现中。  
  
### <a name="return-value"></a>返回值  
 其中一个标准`HRESULT`值。  
  
##  <a name="a-namedoverbuiactivatea--ioleobjectimpldoverbuiactivate"></a><a name="doverbuiactivate"></a>IOleObjectImpl::DoVerbUIActivate  
 激活控件的用户界面，并通知容器通过复合菜单替换为其菜单。  
  
```
HRESULT DoVerbUIActivate(LPCRECT prcPosRect, HWND /* hwndParent */);
```  
  
### <a name="parameters"></a>参数  
 `prcPosRec`  
 [in]指向容器的矩形想要绘制到的控件。  
  
 *hwndParent*  
 [in]包含控件的窗口句柄。 不使用 ATL 实现中。  
  
### <a name="return-value"></a>返回值  
 其中一个标准`HRESULT`值。  
  
##  <a name="a-nameenumadvisea--ioleobjectimplenumadvise"></a><a name="enumadvise"></a>IOleObjectImpl::EnumAdvise  
 提供的对于此控件的已注册通知连接的枚举。  
  
```
STDMETHOD(EnumAdvise)(IEnumSTATDATA** ppenumAdvise);
```  
  
### <a name="remarks"></a>备注  
 请参阅[IOleObject::EnumAdvise](http://msdn.microsoft.com/library/windows/desktop/ms682355)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-nameenumverbsa--ioleobjectimplenumverbs"></a><a name="enumverbs"></a>IOleObjectImpl::EnumVerbs  
 对于此控件提供的已注册操作 （谓词） 的枚举，通过调用**OleRegEnumVerbs**。  
  
```
STDMETHOD(EnumVerbs)(IEnumOLEVERB** ppEnumOleVerb);
```  
  
### <a name="remarks"></a>备注  
 可以将谓词添加到你的项目的.rgs 文件。 有关示例，请参阅 CIRCCTL。在 RGS [CIRC](../../visual-cpp-samples.md)示例。  
  
 请参阅[ioleobject:: Enumverbs](http://msdn.microsoft.com/library/windows/desktop/ms692781)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-namegetclientsitea--ioleobjectimplgetclientsite"></a><a name="getclientsite"></a>IOleObjectImpl::GetClientSite  
 将指针放在控件类数据成员中[CComControlBase::m_spClientSite](../../atl/reference/ccomcontrolbase-class.md#m_spclientsite)到*ppClientSite* ，并增加对指针的引用计数。  
  
```
STDMETHOD(GetClientSite)(IOleClientSite** ppClientSite);
```  
  
### <a name="remarks"></a>备注  
 请参阅[IOleObject::GetClientSite](http://msdn.microsoft.com/library/windows/desktop/ms692603)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-namegetclipboarddataa--ioleobjectimplgetclipboarddata"></a><a name="getclipboarddata"></a>IOleObjectImpl::GetClipboardData  
 从剪贴板检索数据。  
  
```
STDMETHOD(GetClipboardData)(    
    DWORD /* dwReserved */,
    IDataObject** /* ppDataObject */);
```  
  
### <a name="return-value"></a>返回值  
 返回**E_NOTIMPL**。  
  
### <a name="remarks"></a>备注  
 请参阅[IOleObject::GetClipboardData](http://msdn.microsoft.com/library/windows/desktop/ms682288)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-namegetextenta--ioleobjectimplgetextent"></a><a name="getextent"></a>IOleObjectImpl::GetExtent  
 检索正在运行控件的显示大小以 himetric 为单位 （每个单元&0;.01 毫米）。  
  
```
STDMETHOD(GetExtent)(
    DWORD dwDrawAspect,
    SIZEL* psizel);
```  
  
### <a name="remarks"></a>备注  
 在控件类数据成员中存储大小[CComControlBase::m_sizeExtent](../../atl/reference/ccomcontrolbase-class.md#m_sizeextent)。  
  
 请参阅[IOleObject::GetExtent](http://msdn.microsoft.com/library/windows/desktop/ms692325)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-namegetmiscstatusa--ioleobjectimplgetmiscstatus"></a><a name="getmiscstatus"></a>IOleObjectImpl::GetMiscStatus  
 将指针返回到该控件的已注册的状态信息，通过调用**OleRegGetMiscStatus**。  
  
```
STDMETHOD(GetMiscStatus)(
    DWORD dwAspect,
    DWORD* pdwStatus);
```  
  
### <a name="remarks"></a>备注  
 状态信息包括所支持的控件和演示文稿数据的行为。 可以将状态信息添加到你的项目的.rgs 文件。  
  
 请参阅[IOleObject::GetMiscStatus](http://msdn.microsoft.com/library/windows/desktop/ms678521)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-namegetmonikera--ioleobjectimplgetmoniker"></a><a name="getmoniker"></a>IOleObjectImpl::GetMoniker  
 检索控件的标记。  
  
```
STDMETHOD(GetMoniker)(
    DWORD /* dwAssign */,
    DWORD /* dwWhichMoniker */,
    IMoniker** /* ppmk */);
```  
  
### <a name="return-value"></a>返回值  
 返回**E_NOTIMPL**。  
  
### <a name="remarks"></a>备注  
 请参阅[IOleObject::GetMoniker](http://msdn.microsoft.com/library/windows/desktop/ms686576)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-namegetuserclassida--ioleobjectimplgetuserclassid"></a><a name="getuserclassid"></a>IOleObjectImpl::GetUserClassID  
 返回控件的类标识符。  
  
```
STDMETHOD(GetUserClassID)(CLSID* pClsid);
```  
  
### <a name="remarks"></a>备注  
 请参阅[IOleObject::GetUserClassID](http://msdn.microsoft.com/library/windows/desktop/ms682313)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-namegetusertypea--ioleobjectimplgetusertype"></a><a name="getusertype"></a>IOleObjectImpl::GetUserType  
 通过调用返回控件的用户类型名称**OleRegGetUserType**。  
  
```
STDMETHOD(GetUserType)(
    DWORD dwFormOfType,
    LPOLESTR* pszUserType);
```  
  
### <a name="remarks"></a>备注  
 用户类型名称用于在用户界面元素，如菜单和对话框中显示。 您可以更改您的项目的.rgs 文件中的用户类型名称。  
  
 请参阅[IOleObject::GetUserType](http://msdn.microsoft.com/library/windows/desktop/ms688643)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-nameinitfromdataa--ioleobjectimplinitfromdata"></a><a name="initfromdata"></a>IOleObjectImpl::InitFromData  
 初始化从所选数据的控件。  
  
```
STDMETHOD(InitFromData)(
    IDataObject* /* pDataObject */,
    BOOL /* fCreation */,
    DWORD /* dwReserved */);
```  
  
### <a name="return-value"></a>返回值  
 返回**E_NOTIMPL**。  
  
### <a name="remarks"></a>备注  
 请参阅[IOleObject::InitFromData](http://msdn.microsoft.com/library/windows/desktop/ms688510)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-nameisuptodatea--ioleobjectimplisuptodate"></a><a name="isuptodate"></a>IOleObjectImpl::IsUpToDate  
 如果该控件是最新的检查。  
  
```
STDMETHOD(IsUpToDate)(void);
```  
  
### <a name="return-value"></a>返回值  
 返回 `S_OK`。  
  
### <a name="remarks"></a>备注  
 请参阅[IOleObject::IsUpToDate](http://msdn.microsoft.com/library/windows/desktop/ms686624)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-nameonpostverbdiscardundoa--ioleobjectimplonpostverbdiscardundo"></a><a name="onpostverbdiscardundo"></a>IOleObjectImpl::OnPostVerbDiscardUndo  
 由调用[DoVerbDiscardUndo](#doverbdiscardundo)放弃撤消状态之后。  
  
```
HRESULT OnPostVerbDiscardUndo();
```  
  
### <a name="return-value"></a>返回值  
 返回 `S_OK`。  
  
### <a name="remarks"></a>备注  
 使用重写此方法执行后放弃撤消状态所需的代码。  
  
##  <a name="a-nameonpostverbhidea--ioleobjectimplonpostverbhide"></a><a name="onpostverbhide"></a>IOleObjectImpl::OnPostVerbHide  
 由调用[DoVerbHide](#doverbhide)则隐藏该控件后。  
  
```
HRESULT OnPostVerbHide();
```  
  
### <a name="return-value"></a>返回值  
 返回 `S_OK`。  
  
### <a name="remarks"></a>备注  
 重写此方法，则隐藏该控件后执行所需的代码。  
  
##  <a name="a-nameonpostverbinplaceactivatea--ioleobjectimplonpostverbinplaceactivate"></a><a name="onpostverbinplaceactivate"></a>IOleObjectImpl::OnPostVerbInPlaceActivate  
 由调用[DoVerbInPlaceActivate](#doverbinplaceactivate)就地激活该控件后。  
  
```
HRESULT OnPostVerbInPlaceActivate();
```  
  
### <a name="return-value"></a>返回值  
 返回 `S_OK`。  
  
### <a name="remarks"></a>备注  
 重写此方法与你希望在就地激活该控件后执行的代码。  
  
##  <a name="a-nameonpostverbopena--ioleobjectimplonpostverbopen"></a><a name="onpostverbopen"></a>IOleObjectImpl::OnPostVerbOpen  
 由调用[DoVerbOpen](#doverbopen)已为编辑的单独窗口中打开该控件后。  
  
```
HRESULT OnPostVerbOpen();
```  
  
### <a name="return-value"></a>返回值  
 返回 `S_OK`。  
  
### <a name="remarks"></a>备注  
 重写此方法与你希望以进行编辑的单独窗口中打开该控件后执行的代码。  
  
##  <a name="a-nameonpostverbshowa--ioleobjectimplonpostverbshow"></a><a name="onpostverbshow"></a>IOleObjectImpl::OnPostVerbShow  
 由调用[DoVerbShow](#doverbshow)控件进行可见后。  
  
```
HRESULT OnPostVerbShow();
```  
  
### <a name="return-value"></a>返回值  
 返回 `S_OK`。  
  
### <a name="remarks"></a>备注  
 重写此方法与你希望在该控件已可见后执行的代码。  
  
##  <a name="a-nameonpostverbuiactivatea--ioleobjectimplonpostverbuiactivate"></a><a name="onpostverbuiactivate"></a>IOleObjectImpl::OnPostVerbUIActivate  
 由调用[DoVerbUIActivate](#doverbuiactivate)激活了控件的用户界面。  
  
```
HRESULT OnPostVerbUIActivate();
```  
  
### <a name="return-value"></a>返回值  
 返回 `S_OK`。  
  
### <a name="remarks"></a>备注  
 重写此方法与所需执行激活控件的用户界面后的代码。  
  
##  <a name="a-nameonpreverbdiscardundoa--ioleobjectimplonpreverbdiscardundo"></a><a name="onpreverbdiscardundo"></a>IOleObjectImpl::OnPreVerbDiscardUndo  
 由调用[DoVerbDiscardUndo](#doverbdiscardundo)撤消之前，状态将被丢弃。  
  
```
HRESULT OnPreVerbDiscardUndo();
```  
  
### <a name="return-value"></a>返回值  
 返回 `S_OK`。  
  
### <a name="remarks"></a>备注  
 若要防止撤消状态被放弃，重写此方法以返回的错误 HRESULT。  
  
##  <a name="a-nameonpreverbhidea--ioleobjectimplonpreverbhide"></a><a name="onpreverbhide"></a>IOleObjectImpl::OnPreVerbHide  
 由调用[DoVerbHide](#doverbhide)隐藏控件之前。  
  
```
HRESULT OnPreVerbHide();
```  
  
### <a name="return-value"></a>返回值  
 返回 `S_OK`。  
  
### <a name="remarks"></a>备注  
 若要防止该控件要隐藏，请重写此方法以返回的错误 HRESULT。  
  
##  <a name="a-nameonpreverbinplaceactivatea--ioleobjectimplonpreverbinplaceactivate"></a><a name="onpreverbinplaceactivate"></a>IOleObjectImpl::OnPreVerbInPlaceActivate  
 由调用[DoVerbInPlaceActivate](#doverbinplaceactivate)就地激活控件之前。  
  
```
HRESULT OnPreVerbInPlaceActivate();
```  
  
### <a name="return-value"></a>返回值  
 返回 `S_OK`。  
  
### <a name="remarks"></a>备注  
 若要防止该控件就地激活，重写此方法以返回的错误 HRESULT。  
  
##  <a name="a-nameonpreverbopena--ioleobjectimplonpreverbopen"></a><a name="onpreverbopen"></a>IOleObjectImpl::OnPreVerbOpen  
 由调用[DoVerbOpen](#doverbopen)已为编辑的单独窗口中打开该控件之前。  
  
```
HRESULT OnPreVerbOpen();
```  
  
### <a name="return-value"></a>返回值  
 返回 `S_OK`。  
  
### <a name="remarks"></a>备注  
 若要防止控件正在打开可供编辑的单独窗口中，重写此方法以返回的错误 HRESULT。  
  
##  <a name="a-nameonpreverbshowa--ioleobjectimplonpreverbshow"></a><a name="onpreverbshow"></a>IOleObjectImpl::OnPreVerbShow  
 由调用[DoVerbShow](#doverbshow)控件已可见之前。  
  
```
HRESULT OnPreVerbShow();
```  
  
### <a name="return-value"></a>返回值  
 返回 `S_OK`。  
  
### <a name="remarks"></a>备注  
 若要防止该控件被设置为可见，重写此方法以返回的错误 HRESULT。  
  
##  <a name="a-nameonpreverbuiactivatea--ioleobjectimplonpreverbuiactivate"></a><a name="onpreverbuiactivate"></a>IOleObjectImpl::OnPreVerbUIActivate  
 由调用[DoVerbUIActivate](#doverbuiactivate)控件的用户界面已被激活之前。  
  
```
HRESULT OnPreVerbUIActivate();
```  
  
### <a name="return-value"></a>返回值  
 返回 `S_OK`。  
  
### <a name="remarks"></a>备注  
 若要防止激活控件的用户界面，重写此方法以返回的错误 HRESULT。  
  
##  <a name="a-namesetclientsitea--ioleobjectimplsetclientsite"></a><a name="setclientsite"></a>IOleObjectImpl::SetClientSite  
 该控件将告知其客户端站点容器中。  
  
```
STDMETHOD(SetClientSite)(IOleClientSite* pClientSite);
```  
  
### <a name="remarks"></a>备注  
 该方法会返回`S_OK`。  
  
 请参阅[IOleObject::SetClientSite](http://msdn.microsoft.com/library/windows/desktop/ms684013)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-namesetcolorschemea--ioleobjectimplsetcolorscheme"></a><a name="setcolorscheme"></a>IOleObjectImpl::SetColorScheme  
 如果有的话，给控件的应用程序，建议配色方案。  
  
```
STDMETHOD(SetColorScheme)(LOGPALETTE* /* pLogPal */);
```  
  
### <a name="return-value"></a>返回值  
 返回**E_NOTIMPL**。  
  
### <a name="remarks"></a>备注  
 请参阅[IOleObject::SetColorScheme](http://msdn.microsoft.com/library/windows/desktop/ms683971)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-namesetextenta--ioleobjectimplsetextent"></a><a name="setextent"></a>IOleObjectImpl::SetExtent  
 设置控件的显示区域的程度。  
  
```
STDMETHOD(SetExtent)(
    DWORD dwDrawAspect,
    SIZEL* psizel);
```  
  
### <a name="remarks"></a>备注  
 否则为`SetExtent`存储所指向的值`psizel`在控件类数据成员中[CComControlBase::m_sizeExtent](../../atl/reference/ccomcontrolbase-class.md#m_sizeextent)。 此值为以 himetric 为单位 （每个单元&0;.01 毫米）。  
  
 如果该控件类数据成员[CComControlBase::m_bResizeNatural](../../atl/reference/ccomcontrolbase-class.md#m_bresizenatural)是**TRUE**，`SetExtent`还可存储指向的值`psizel`在控件类数据成员中[CComControlBase::m_sizeNatural](../../atl/reference/ccomcontrolbase-class.md#m_sizenatural)。  
  
 如果该控件类数据成员[CComControlBase::m_bRecomposeOnResize](../../atl/reference/ccomcontrolbase-class.md#m_brecomposeonresize)是**TRUE**，`SetExtent`调用`SendOnDataChange`和`SendOnViewChange`通知注册控件大小已更改的通知持有者的所有通知接收器。  
  
 请参阅[IOleObject::SetExtent](http://msdn.microsoft.com/library/windows/desktop/ms694330)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-namesethostnamesa--ioleobjectimplsethostnames"></a><a name="sethostnames"></a>IOleObjectImpl::SetHostNames  
 指示控件的容器应用程序和容器文档的名称。  
  
```
STDMETHOD(SetHostNames)(LPCOLESTR /* szContainerApp */, LPCOLESTR /* szContainerObj */);
```  
  
### <a name="return-value"></a>返回值  
 返回 `S_OK`。  
  
### <a name="remarks"></a>备注  
 请参阅[IOleObject::SetHostNames](http://msdn.microsoft.com/library/windows/desktop/ms680642)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-namesetmonikera--ioleobjectimplsetmoniker"></a><a name="setmoniker"></a>IOleObjectImpl::SetMoniker  
 其标记为可告知控件。  
  
```
STDMETHOD(SetMoniker)(
    DWORD /* dwWhichMoniker */,
    IMoniker** /* pmk */);
```  
  
### <a name="return-value"></a>返回值  
 返回**E_NOTIMPL**。  
  
### <a name="remarks"></a>备注  
 请参阅[IOleObject::SetMoniker](http://msdn.microsoft.com/library/windows/desktop/ms679671)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-nameunadvisea--ioleobjectimplunadvise"></a><a name="unadvise"></a>IOleObjectImpl::Unadvise  
 删除通知连接存储在控件类`m_spOleAdviseHolder`数据成员。  
  
```
STDMETHOD(Unadvise)(DWORD dwConnection);
```  
  
### <a name="remarks"></a>备注  
 请参阅[IOleObject::Unadvise](http://msdn.microsoft.com/library/windows/desktop/ms693749)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-nameupdatea--ioleobjectimplupdate"></a><a name="update"></a>IOleObjectImpl::Update  
 可更新控件。  
  
```
STDMETHOD(Update)(void);
```  
  
### <a name="return-value"></a>返回值  
 返回 `S_OK`。  
  
### <a name="remarks"></a>备注  
 请参阅[IOleObject::Update](http://msdn.microsoft.com/library/windows/desktop/ms679699)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
## <a name="see-also"></a>另请参阅  
 [CComControl 类](../../atl/reference/ccomcontrol-class.md)   
 [ActiveX 控件接口](http://msdn.microsoft.com/library/windows/desktop/ms692724)   
 [类概述](../../atl/atl-class-overview.md)

