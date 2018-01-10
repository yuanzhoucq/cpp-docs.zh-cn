---
title: "CComControlBase 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CComControlBase
- ATLCTL/ATL::CComControlBase
- ATLCTL/ATL::CComControlBase::AppearanceType
- ATLCTL/ATL::CComControlBase::CComControlBase
- ATLCTL/ATL::CComControlBase::ControlQueryInterface
- ATLCTL/ATL::CComControlBase::DoesVerbActivate
- ATLCTL/ATL::CComControlBase::DoesVerbUIActivate
- ATLCTL/ATL::CComControlBase::DoVerbProperties
- ATLCTL/ATL::CComControlBase::FireViewChange
- ATLCTL/ATL::CComControlBase::GetAmbientAppearance
- ATLCTL/ATL::CComControlBase::GetAmbientAutoClip
- ATLCTL/ATL::CComControlBase::GetAmbientBackColor
- ATLCTL/ATL::CComControlBase::GetAmbientCharSet
- ATLCTL/ATL::CComControlBase::GetAmbientCodePage
- ATLCTL/ATL::CComControlBase::GetAmbientDisplayAsDefault
- ATLCTL/ATL::CComControlBase::GetAmbientDisplayName
- ATLCTL/ATL::CComControlBase::GetAmbientFont
- ATLCTL/ATL::CComControlBase::GetAmbientFontDisp
- ATLCTL/ATL::CComControlBase::GetAmbientForeColor
- ATLCTL/ATL::CComControlBase::GetAmbientLocaleID
- ATLCTL/ATL::CComControlBase::GetAmbientMessageReflect
- ATLCTL/ATL::CComControlBase::GetAmbientPalette
- ATLCTL/ATL::CComControlBase::GetAmbientProperty
- ATLCTL/ATL::CComControlBase::GetAmbientRightToLeft
- ATLCTL/ATL::CComControlBase::GetAmbientScaleUnits
- ATLCTL/ATL::CComControlBase::GetAmbientShowGrabHandles
- ATLCTL/ATL::CComControlBase::GetAmbientShowHatching
- ATLCTL/ATL::CComControlBase::GetAmbientSupportsMnemonics
- ATLCTL/ATL::CComControlBase::GetAmbientTextAlign
- ATLCTL/ATL::CComControlBase::GetAmbientTopToBottom
- ATLCTL/ATL::CComControlBase::GetAmbientUIDead
- ATLCTL/ATL::CComControlBase::GetAmbientUserMode
- ATLCTL/ATL::CComControlBase::GetDirty
- ATLCTL/ATL::CComControlBase::GetZoomInfo
- ATLCTL/ATL::CComControlBase::InPlaceActivate
- ATLCTL/ATL::CComControlBase::InternalGetSite
- ATLCTL/ATL::CComControlBase::OnDraw
- ATLCTL/ATL::CComControlBase::OnDrawAdvanced
- ATLCTL/ATL::CComControlBase::OnKillFocus
- ATLCTL/ATL::CComControlBase::OnMouseActivate
- ATLCTL/ATL::CComControlBase::OnPaint
- ATLCTL/ATL::CComControlBase::OnSetFocus
- ATLCTL/ATL::CComControlBase::PreTranslateAccelerator
- ATLCTL/ATL::CComControlBase::SendOnClose
- ATLCTL/ATL::CComControlBase::SendOnDataChange
- ATLCTL/ATL::CComControlBase::SendOnRename
- ATLCTL/ATL::CComControlBase::SendOnSave
- ATLCTL/ATL::CComControlBase::SendOnViewChange
- ATLCTL/ATL::CComControlBase::SetControlFocus
- ATLCTL/ATL::CComControlBase::SetDirty
- ATLCTL/ATL::CComControlBase::m_bAutoSize
- ATLCTL/ATL::CComControlBase::m_bDrawFromNatural
- ATLCTL/ATL::CComControlBase::m_bDrawGetDataInHimetric
- ATLCTL/ATL::CComControlBase::m_bInPlaceActive
- ATLCTL/ATL::CComControlBase::m_bInPlaceSiteEx
- ATLCTL/ATL::CComControlBase::m_bNegotiatedWnd
- ATLCTL/ATL::CComControlBase::m_bRecomposeOnResize
- ATLCTL/ATL::CComControlBase::m_bRequiresSave
- ATLCTL/ATL::CComControlBase::m_bResizeNatural
- ATLCTL/ATL::CComControlBase::m_bUIActive
- ATLCTL/ATL::CComControlBase::m_bUsingWindowRgn
- ATLCTL/ATL::CComControlBase::m_bWasOnceWindowless
- ATLCTL/ATL::CComControlBase::m_bWindowOnly
- ATLCTL/ATL::CComControlBase::m_bWndLess
- ATLCTL/ATL::CComControlBase::m_hWndCD
- ATLCTL/ATL::CComControlBase::m_nFreezeEvents
- ATLCTL/ATL::CComControlBase::m_rcPos
- ATLCTL/ATL::CComControlBase::m_sizeExtent
- ATLCTL/ATL::CComControlBase::m_sizeNatural
- ATLCTL/ATL::CComControlBase::m_spAdviseSink
- ATLCTL/ATL::CComControlBase::m_spAmbientDispatch
- ATLCTL/ATL::CComControlBase::m_spClientSite
- ATLCTL/ATL::CComControlBase::m_spDataAdviseHolder
- ATLCTL/ATL::CComControlBase::m_spInPlaceSite
- ATLCTL/ATL::CComControlBase::m_spOleAdviseHolder
dev_langs: C++
helpviewer_keywords: CComControlBase class
ms.assetid: 3d1bf022-acf2-4092-8283-ff8cee6332f3
caps.latest.revision: "20"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: d6109bfaf29ee26053bc1dcbb5af8f56a0612215
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="ccomcontrolbase-class"></a>CComControlBase 类
此类提供用于创建和管理 ATL 控件的方法。  
  
> [!IMPORTANT]
>  此类及其成员无法在 Windows 运行时中执行的应用中使用。  
  
## <a name="syntax"></a>语法  
  
```
class ATL_NO_VTABLE CComControlBase
```  
  
## <a name="members"></a>成员  
  
### <a name="public-typedefs"></a>公共 Typedef  
  
|名称|描述|  
|----------|-----------------|  
|[CComControlBase::AppearanceType](#appearancetype)|如果重写你`m_nAppearance`常用属性的类型不`short`。|  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[CComControlBase::CComControlBase](#ccomcontrolbase)|构造函数。|  
|[CComControlBase:: ~ CComControlBase](#dtor)|析构函数。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CComControlBase::ControlQueryInterface](#controlqueryinterface)|检索指向所请求的接口的指针。|  
|[CComControlBase::DoesVerbActivate](#doesverbactivate)|检查`iVerb`参数由`IOleObjectImpl::DoVerb`或者激活控件的用户界面 (`iVerb`等于`OLEIVERB_UIACTIVATE`)，定义当用户双击控件执行的操作 (`iVerb`等于`OLEIVERB_PRIMARY`)，显示控件 (`iVerb`等于`OLEIVERB_SHOW`)，或激活控件 (`iVerb`等于**OLEIVERB_INPLACEACTIVATE**)。|  
|[CComControlBase::DoesVerbUIActivate](#doesverbuiactivate)|检查`iVerb`参数由`IOleObjectImpl::DoVerb`导致控件的用户界面来激活并返回**TRUE**。|  
|[CComControlBase::DoVerbProperties](#doverbproperties)|显示控件的属性页。|  
|[CComControlBase::FireViewChange](#fireviewchange)|调用此方法可告知要重绘控件的容器或通知控件的视图已更改的已注册的通知接收器。|  
|[CComControlBase::GetAmbientAppearance](#getambientappearance)|检索**DISPID_AMBIENT_APPEARANCE**时，为控件设置的当前外观： 0 代表平面和 3d 1。|  
|[CComControlBase::GetAmbientAutoClip](#getambientautoclip)|检索**DISPID_AMBIENT_AUTOCLIP**、 一个标志，指示容器是否支持自动剪辑的控件的显示区域。|  
|[CComControlBase::GetAmbientBackColor](#getambientbackcolor)|检索**DISPID_AMBIENT_BACKCOLOR**，定义的容器的所有控件的环境背景色。|  
|[CComControlBase::GetAmbientCharSet](#getambientcharset)|检索**DISPID_AMBIENT_CHARSET**，对于所有控件，定义由容器设置的环境的字符集。|  
|[CComControlBase::GetAmbientCodePage](#getambientcodepage)|检索**DISPID_AMBIENT_CODEPAGE**，对于所有控件，定义由容器设置的环境的字符集。|  
|[CComControlBase::GetAmbientDisplayAsDefault](#getambientdisplayasdefault)|检索**DISPID_AMBIENT_DISPLAYASDEFAULT**，是一个标志**TRUE**如果容器已标记为默认按钮，此站点中的控件和一个按钮控件应因此绘制自行向粗的框架。|  
|[CComControlBase::GetAmbientDisplayName](#getambientdisplayname)|检索**DISPID_AMBIENT_DISPLAYNAME**，容器已提供给控件的名称。|  
|[CComControlBase::GetAmbientFont](#getambientfont)|检索指向容器的环境`IFont`接口。|  
|[CComControlBase::GetAmbientFontDisp](#getambientfontdisp)|检索指向容器的环境**IFontDisp**调度接口。|  
|[CComControlBase::GetAmbientForeColor](#getambientforecolor)|检索**DISPID_AMBIENT_FORECOLOR**，对于所有控件，定义由容器的环境前景色。|  
|[CComControlBase::GetAmbientLocaleID](#getambientlocaleid)|检索**DISPID_AMBIENT_LOCALEID**，容器使用的语言的标识符。|  
|[CComControlBase::GetAmbientMessageReflect](#getambientmessagereflect)|检索**DISPID_AMBIENT_MESSAGEREFLECT**、 一个标志，指示容器是否想要接收窗口消息 (如`WM_DRAWITEM`) 作为事件。|  
|[CComControlBase::GetAmbientPalette](#getambientpalette)|检索**DISPID_AMBIENT_PALETTE**，可用来访问容器的`HPALETTE`。|  
|[CComControlBase::GetAmbientProperty](#getambientproperty)|检索指定的容器属性`id`。|  
|[CComControlBase::GetAmbientRightToLeft](#getambientrighttoleft)|检索**DISPID_AMBIENT_RIGHTTOLEFT**，内容由容器中的显示方向。|  
|[CComControlBase::GetAmbientScaleUnits](#getambientscaleunits)|检索**DISPID_AMBIENT_SCALEUNITS**的容器 （如英寸或厘米） 为加标签显示的环境单位。|  
|[CComControlBase::GetAmbientShowGrabHandles](#getambientshowgrabhandles)|检索**DISPID_AMBIENT_SHOWGRABHANDLES**、 一个标志，指示容器是否允许要为其自身活动时显示抓取手柄的控件。|  
|[CComControlBase::GetAmbientShowHatching](#getambientshowhatching)|检索**DISPID_AMBIENT_SHOWHATCHING**、 一个标志，指示容器是否允许控件以将它显示用阴影图案 UI 处于活动状态时。|  
|[CComControlBase::GetAmbientSupportsMnemonics](#getambientsupportsmnemonics)|检索**DISPID_AMBIENT_SUPPORTSMNEMONICS**、 一个标志，指示容器是否支持键盘助记键。|  
|[CComControlBase::GetAmbientTextAlign](#getambienttextalign)|检索**DISPID_AMBIENT_TEXTALIGN**，由容器首选的文本对齐方式： 常规对齐 （左数字右，文本） 为 0、 1 表示左对齐、 居中对齐的 2 和右对齐的 3。|  
|[CComControlBase::GetAmbientTopToBottom](#getambienttoptobottom)|检索**DISPID_AMBIENT_TOPTOBOTTOM**，内容由容器中的显示方向。|  
|[CComControlBase::GetAmbientUIDead](#getambientuidead)|检索**DISPID_AMBIENT_UIDEAD**、 一个标志，指示容器是否想要响应用户界面操作的控件。|  
|[CComControlBase::GetAmbientUserMode](#getambientusermode)|检索**DISPID_AMBIENT_USERMODE**、 一个标志，指示容器是否处于运行模式 ( **TRUE**) 或设计模式 ( **FALSE**)。|  
|[CComControlBase::GetDirty](#getdirty)|返回的数据成员的值`m_bRequiresSave`。|  
|[CComControlBase::GetZoomInfo](#getzoominfo)|检索的 x 和 y 分子和缩放系数分母的值的控件为激活就地编辑。|  
|[CComControlBase::InPlaceActivate](#inplaceactivate)|使控件从任何状态中的动词的非活动状态转换到`iVerb`指示。|  
|[CComControlBase::InternalGetSite](#internalgetsite)|调用此方法来查询控件所在位置到标识的接口的指针。|  
|[CComControlBase::OnDraw](#ondraw)|重写此方法以绘制控件。|  
|[CComControlBase::OnDrawAdvanced](#ondrawadvanced)|默认值**OnDrawAdvanced**准备规范化的设备上下文进行绘制，然后调用你的控件类`OnDraw`方法。|  
|[CComControlBase::OnKillFocus](#onkillfocus)|检查该控件是处于就地活动状态并且具有有效的控制站点，则通知容器控件已失去焦点。|  
|[CComControlBase::OnMouseActivate](#onmouseactivate)|检查用户界面在用户模式下，则将激活的控件。|  
|[CComControlBase::OnPaint](#onpaint)|为绘制准备容器，获取控件的客户端区域中，然后调用的控件类`OnDraw`方法。|  
|[CComControlBase::OnSetFocus](#onsetfocus)|检查该控件是处于就地活动状态并且具有有效的控制站点，则通知容器控件获得焦点。|  
|[CComControlBase::PreTranslateAccelerator](#pretranslateaccelerator)|重写该方法以提供您自己的键盘快捷键处理程序。|  
|[CComControlBase::SendOnClose](#sendonclose)|通知注册已关闭该控件的建议持有的所有通知接收器。|  
|[CComControlBase::SendOnDataChange](#sendondatachange)|通知注册控制数据已更改的建议持有的所有通知接收器。|  
|[CComControlBase::SendOnRename](#sendonrename)|通知注册该控件具有新的名字对象的建议持有的所有通知接收器。|  
|[CComControlBase::SendOnSave](#sendonsave)|通知注册保存该控件的建议持有的所有通知接收器。|  
|[CComControlBase::SendOnViewChange](#sendonviewchange)|通知所有已注册的控件的视图已更改的通知接收器。|  
|[CComControlBase::SetControlFocus](#setcontrolfocus)|设置或删除到或从控件的键盘焦点。|  
|[CComControlBase::SetDirty](#setdirty)|设置的数据成员`m_bRequiresSave`到中的值`bDirty`。|  
  
### <a name="public-data-members"></a>公共数据成员  
  
|名称|描述|  
|----------|-----------------|  
|[CComControlBase::m_bAutoSize](#m_bautosize)|指示该控件不能为任何其他大小的标志。|  
|[CComControlBase::m_bDrawFromNatural](#m_bdrawfromnatural)|标志指示`IDataObjectImpl::GetData`和`CComControlBase::GetZoomInfo`应设置从控件大小`m_sizeNatural`而不是从`m_sizeExtent`。|  
|[CComControlBase::m_bDrawGetDataInHimetric](#m_bdrawgetdatainhimetric)|标志指示`IDataObjectImpl::GetData`应在绘制时使用 himetric 为单位，不像素。|  
|[CComControlBase::m_bInPlaceActive](#m_binplaceactive)|该标志指明控件处于就地活动状态。|  
|[CComControlBase::m_bInPlaceSiteEx](#m_binplacesiteex)|该标志指明容器支持**IOleInPlaceSiteEx**接口和 OCX96 控制功能，如无窗口和闪烁的控件。|  
|[CComControlBase::m_bNegotiatedWnd](#m_bnegotiatedwnd)|该标志指明控件具有与支持 OCX96 控件功能 （如闪烁和无窗口控件） 的容器进行协商和控件是开窗还是无窗口。|  
|[CComControlBase::m_bRecomposeOnResize](#m_brecomposeonresize)|该标志指明控件想要重排与其演示当容器更改控件的显示大小。|  
|[CComControlBase::m_bRequiresSave](#m_brequiressave)|指示自上次保存后，该控件已更改的标志。|  
|[CComControlBase::m_bResizeNatural](#m_bresizenatural)|标志，指示该控件想要调整大小其原始大小 （其未缩放物理大小） 容器时更改控件的显示大小。|  
|[CComControlBase::m_bUIActive](#m_buiactive)|标志，指示控件的用户界面，例如菜单和工具栏，处于活动状态。|  
|[CComControlBase::m_bUsingWindowRgn](#m_busingwindowrgn)|该标志指明控件使用提供容器的窗口区域。|  
|[CComControlBase::m_bWasOnceWindowless](#m_bwasoncewindowless)|指示该控件已无窗口，但可能也可能不是无窗口现在的标志。|  
|[CComControlBase::m_bWindowOnly](#m_bwindowonly)|指示该控件应开窗，即使容器支持无窗口控件的标志。|  
|[CComControlBase::m_bWndLess](#m_bwndless)|用于指示无窗口控件的标记。|  
|[CComControlBase::m_hWndCD](#m_hwndcd)|包含对与控件关联的窗口句柄的引用。|  
|[CComControlBase::m_nFreezeEvents](#m_nfreezeevents)|次数计数容器已冻结 （拒绝接受事件） 的事件，而无需干预的解除冻结的事件 （事件接受）。|  
|[CComControlBase::m_rcPos](#m_rcpos)|控件，以容器的坐标表示的位置，以像素为单位。|  
|[CComControlBase::m_sizeExtent](#m_sizeextent)|以 himetric 为单位 （每个单位是 0.01 毫米） 的特定显示控件的范围。|  
|[CComControlBase::m_sizeNatural](#m_sizenatural)|以 himetric 为单位 （每个单位是 0.01 毫米） 控件的物理大小。|  
|[CComControlBase::m_spAdviseSink](#m_spadvisesink)|指向通知连接对该容器的直接指针 (容器的[IAdviseSink](http://msdn.microsoft.com/library/windows/desktop/ms692513))。|  
|[CComControlBase::m_spAmbientDispatch](#m_spambientdispatch)|A`CComDispatchDriver`对象，允许您检索和设置容器的属性通过`IDispatch`指针。|  
|[CComControlBase::m_spClientSite](#m_spclientsite)|指向控件的客户端站点容器内的指针。|  
|[CComControlBase::m_spDataAdviseHolder](#m_spdataadviseholder)|提供一种标准意味着来保留数据对象之间的通知连接和建议的接收器。|  
|[CComControlBase::m_spInPlaceSite](#m_spinplacesite)|指向容器的[IOleInPlaceSite](http://msdn.microsoft.com/library/windows/desktop/ms686586)， [IOleInPlaceSiteEx](http://msdn.microsoft.com/library/windows/desktop/ms693461)，或[IOleInPlaceSiteWindowless](http://msdn.microsoft.com/library/windows/desktop/ms682300)接口指针。|  
|[CComControlBase::m_spOleAdviseHolder](#m_spoleadviseholder)|提供一种方法来保存的通知连接的标准实现。|  
  
## <a name="remarks"></a>备注  
 此类提供用于创建和管理 ATL 控件的方法。 [CComControl 类](../../atl/reference/ccomcontrol-class.md)派生自`CComControlBase`。 当你创建使用 ATL 控件向导的标准控制或 DHTML 控件时，向导将自动派生您的类从`CComControlBase`。  
  
 有关创建控件的详细信息，请参阅[ATL 教程](../../atl/active-template-library-atl-tutorial.md)。 有关 ATL 项目向导的详细信息，请参阅文章[创建 ATL 项目](../../atl/reference/creating-an-atl-project.md)。  
  
## <a name="requirements"></a>惠?  
 **标头：** atlctl.h  
  
##  <a name="appearancetype"></a>CComControlBase::AppearanceType  
 如果重写你**m_nAppearance**常用属性的类型不**短**。  
  
```
typedef short AppearanceType;
```  
  
### <a name="remarks"></a>备注  
 ATL 控件向导将添加**m_nAppearance**常用 short 类型的属性。 重写`AppearanceType`如果你使用不同的数据类型。  
  
##  <a name="ccomcontrolbase"></a>CComControlBase::CComControlBase  
 构造函数。  
  
```
CComControlBase(HWND& h);
```  
  
### <a name="parameters"></a>参数  
 `h`  
 与控件关联的窗口句柄。  
  
### <a name="remarks"></a>备注  
 初始化到 5080 X 5080 himetric 为单位的控件大小 ("X 2"的 2) 并初始化`CComControlBase`数据成员值复制到**NULL**或**FALSE**。  
  
##  <a name="dtor"></a>CComControlBase:: ~ CComControlBase  
 析构函数。  
  
```
~CComControlBase();
```  
  
### <a name="remarks"></a>备注  
 如果控件是开窗，`~CComControlBase`销毁通过调用[DestroyWindow](http://msdn.microsoft.com/library/windows/desktop/ms632682)。  
  
##  <a name="controlqueryinterface"></a>CComControlBase::ControlQueryInterface  
 检索指向所请求的接口的指针。  
  
```
virtual HRESULT ControlQueryInterface(const IID& iid,
    void** ppv);
```  
  
### <a name="parameters"></a>参数  
 `iid`  
 所请求接口的 GUID。  
  
 `ppv`  
 指向由标识的接口指针的指针`iid`，或**NULL**如果找不到该接口。  
  
### <a name="remarks"></a>备注  
 仅处理 COM 映射表中的接口。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATL_COM#15](../../atl/codesnippet/cpp/ccomcontrolbase-class_1.cpp)]  
  
##  <a name="doesverbactivate"></a>CComControlBase::DoesVerbActivate  
 检查`iVerb`参数由`IOleObjectImpl::DoVerb`或者激活控件的用户界面 (`iVerb`等于`OLEIVERB_UIACTIVATE`)，定义当用户双击控件执行的操作 (`iVerb`等于`OLEIVERB_PRIMARY`)，显示控件 (`iVerb`等于`OLEIVERB_SHOW`)，或激活控件 (`iVerb`等于**OLEIVERB_INPLACEACTIVATE**)。  
  
```
BOOL DoesVerbActivate(LONG iVerb);
```  
  
### <a name="parameters"></a>参数  
 `iVerb`  
 值，该值指示要执行的操作`DoVerb`。  
  
### <a name="return-value"></a>返回值  
 返回**TRUE**如果`iVerb`等于`OLEIVERB_UIACTIVATE`， `OLEIVERB_PRIMARY`， `OLEIVERB_SHOW`，或**OLEIVERB_INPLACEACTIVATE**; 否则为返回**FALSE**.  
  
### <a name="remarks"></a>备注  
 你可以重写此方法以定义你自己激活谓词。  
  
##  <a name="doesverbuiactivate"></a>CComControlBase::DoesVerbUIActivate  
 检查`iVerb`参数由`IOleObjectImpl::DoVerb`导致控件的用户界面来激活并返回**TRUE**。  
  
```
BOOL DoesVerbUIActivate(LONG iVerb);
```  
  
### <a name="parameters"></a>参数  
 `iVerb`  
 值，该值指示要执行的操作`DoVerb`。  
  
### <a name="return-value"></a>返回值  
 返回**TRUE**如果`iVerb`等于`OLEIVERB_UIACTIVATE`， `OLEIVERB_PRIMARY`， `OLEIVERB_SHOW`，或**OLEIVERB_INPLACEACTIVATE**。 否则，该方法返回**FALSE**。  
  
##  <a name="doverbproperties"></a>CComControlBase::DoVerbProperties  
 显示控件的属性页。  
  
```
HRESULT DoVerbProperties(LPCRECT /* prcPosRect */, HWND hwndParent);
```  
  
### <a name="parameters"></a>参数  
 `prcPosRec`  
 保留。  
  
 *hwndParent*  
 包含控件的窗口的句柄。  
  
### <a name="return-value"></a>返回值  
 一个标准的 HRESULT 值。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATL_COM#19](../../atl/codesnippet/cpp/ccomcontrolbase-class_2.cpp)]  
  
 [!code-cpp[NVC_ATL_COM#20](../../atl/codesnippet/cpp/ccomcontrolbase-class_3.h)]  
  
##  <a name="fireviewchange"></a>CComControlBase::FireViewChange  
 调用此方法可告知要重绘控件的容器或通知控件的视图已更改的已注册的通知接收器。  
  
```
HRESULT FireViewChange();
```  
  
### <a name="return-value"></a>返回值  
 一个标准的 HRESULT 值。  
  
### <a name="remarks"></a>备注  
 如果控件处于活动状态 (控件类数据成员[CComControlBase::m_bInPlaceActive](#m_binplaceactive)是**TRUE**)，通知你想要重新绘制整个控件的容器。 如果控件处于非活动状态，将通知注册控件的建议接收器 (通过控件类数据成员[CComControlBase::m_spAdviseSink](#m_spadvisesink)) 控件的视图已更改。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATL_COM#21](../../atl/codesnippet/cpp/ccomcontrolbase-class_4.cpp)]  
  
##  <a name="getambientappearance"></a>CComControlBase::GetAmbientAppearance  
 检索**DISPID_AMBIENT_APPEARANCE**时，为控件设置的当前外观： 0 代表平面和 3d 1。  
  
```
HRESULT GetAmbientAppearance(short& nAppearance);
```  
  
### <a name="parameters"></a>参数  
 `nAppearance`  
 属性**DISPID_AMBIENT_APPEARANCE**。  
  
### <a name="return-value"></a>返回值  
 一个标准的 HRESULT 值。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATL_COM#22](../../atl/codesnippet/cpp/ccomcontrolbase-class_5.h)]  
  
##  <a name="getambientautoclip"></a>CComControlBase::GetAmbientAutoClip  
 检索**DISPID_AMBIENT_AUTOCLIP**、 一个标志，指示容器是否支持自动剪辑的控件的显示区域。  
  
```
HRESULT GetAmbientAutoClip(BOOL& bAutoClip);
```  
  
### <a name="parameters"></a>参数  
 *bAutoClip*  
 属性**DISPID_AMBIENT_AUTOCLIP**。  
  
### <a name="return-value"></a>返回值  
 一个标准的 HRESULT 值。  
  
##  <a name="getambientbackcolor"></a>CComControlBase::GetAmbientBackColor  
 检索**DISPID_AMBIENT_BACKCOLOR**，定义的容器的所有控件的环境背景色。  
  
```
HRESULT GetAmbientBackColor(OLE_COLOR& BackColor);
```  
  
### <a name="parameters"></a>参数  
 *背景色*  
 属性**DISPID_AMBIENT_BACKCOLOR**。  
  
### <a name="return-value"></a>返回值  
 一个标准的 HRESULT 值。  
  
##  <a name="getambientcharset"></a>CComControlBase::GetAmbientCharSet  
 检索**DISPID_AMBIENT_CHARSET**，对于所有控件，定义由容器设置的环境的字符集。  
  
```
HRESULT GetAmbientCharSet(BSTR& bstrCharSet);
```  
  
### <a name="parameters"></a>参数  
 *bstrCharSet*  
 属性**DISPID_AMBIENT_CHARSET**。  
  
### <a name="return-value"></a>返回值  
 返回成功，则为 S_OK 或失败的错误 HRESULT。  
  
##  <a name="getambientcodepage"></a>CComControlBase::GetAmbientCodePage  
 检索**DISPID_AMBIENT_CODEPAGE**，定义的容器的所有控件的环境的代码页。  
  
```
HRESULT GetAmbientCodePage(ULONG& ulCodePage);
```  
  
### <a name="parameters"></a>参数  
 *ulCodePage*  
 属性**DISPID_AMBIENT_CODEPAGE**。  
  
### <a name="return-value"></a>返回值  
 返回成功，则为 S_OK 或失败的错误 HRESULT。  
  
##  <a name="getambientdisplayasdefault"></a>CComControlBase::GetAmbientDisplayAsDefault  
 检索**DISPID_AMBIENT_DISPLAYASDEFAULT**，是一个标志**TRUE**如果容器已标记为默认按钮，此站点中的控件和一个按钮控件应因此绘制自行向粗的框架。  
  
```
HRESULT GetAmbientDisplayAsDefault(BOOL& bDisplayAsDefault);
```  
  
### <a name="parameters"></a>参数  
 `bDisplayAsDefault`  
 属性**DISPID_AMBIENT_DISPLAYASDEFAULT**。  
  
### <a name="return-value"></a>返回值  
 一个标准的 HRESULT 值。  
  
##  <a name="getambientdisplayname"></a>CComControlBase::GetAmbientDisplayName  
 检索**DISPID_AMBIENT_DISPLAYNAME**，容器已提供给控件的名称。  
  
```
HRESULT GetAmbientDisplayName(BSTR& bstrDisplayName);
```  
  
### <a name="parameters"></a>参数  
 *bstrDisplayName*  
 属性**DISPID_AMBIENT_DISPLAYNAME**。  
  
### <a name="return-value"></a>返回值  
 一个标准的 HRESULT 值。  
  
##  <a name="getambientfont"></a>CComControlBase::GetAmbientFont  
 检索指向容器的环境`IFont`接口。  
  
```
HRESULT GetAmbientFont(IFont** ppFont);
```  
  
### <a name="parameters"></a>参数  
 `ppFont`  
 指向容器的环境[IFont](http://msdn.microsoft.com/library/windows/desktop/ms680673)接口。  
  
### <a name="return-value"></a>返回值  
 一个标准的 HRESULT 值。  
  
### <a name="remarks"></a>备注  
 如果属性是**NULL**，在指针位于**NULL**。 如果指针不**NULL**，调用方必须释放指针。  
  
##  <a name="getambientfontdisp"></a>CComControlBase::GetAmbientFontDisp  
 检索指向容器的环境**IFontDisp**调度接口。  
  
```
HRESULT GetAmbientFontDisp(IFontDisp** ppFont);
```  
  
### <a name="parameters"></a>参数  
 `ppFont`  
 指向容器的环境[IFontDisp](http://msdn.microsoft.com/library/windows/desktop/ms692695)调度接口。  
  
### <a name="return-value"></a>返回值  
 返回成功，则为 S_OK 或失败的错误 HRESULT。  
  
### <a name="remarks"></a>备注  
 如果属性是**NULL**，在指针位于**NULL**。 如果指针不**NULL**，调用方必须释放指针。  
  
##  <a name="getambientforecolor"></a>CComControlBase::GetAmbientForeColor  
 检索**DISPID_AMBIENT_FORECOLOR**，对于所有控件，定义由容器的环境前景色。  
  
```
HRESULT GetAmbientForeColor(OLE_COLOR& ForeColor);
```  
  
### <a name="parameters"></a>参数  
 *前景色*  
 属性**DISPID_AMBIENT_FORECOLOR**。  
  
### <a name="return-value"></a>返回值  
 一个标准的 HRESULT 值。  
  
##  <a name="getambientlocaleid"></a>CComControlBase::GetAmbientLocaleID  
 检索**DISPID_AMBIENT_LOCALEID**，容器使用的语言的标识符。  
  
```
HRESULT GetAmbientLocaleID(LCID& lcid);
```  
  
### <a name="parameters"></a>参数  
 `lcid`  
 属性**DISPID_AMBIENT_LOCALEID**。  
  
### <a name="return-value"></a>返回值  
 一个标准的 HRESULT 值。  
  
### <a name="remarks"></a>备注  
 该控件可以使用此标识符以适应其用户界面到不同的语言。  
  
##  <a name="getambientmessagereflect"></a>CComControlBase::GetAmbientMessageReflect  
 检索**DISPID_AMBIENT_MESSAGEREFLECT**、 一个标志，指示容器是否想要接收窗口消息 (如`WM_DRAWITEM`) 作为事件。  
  
```
HRESULT GetAmbientMessageReflect(BOOL& bMessageReflect);
```  
  
### <a name="parameters"></a>参数  
 `bMessageReflect`  
 属性**DISPID_AMBIENT_MESSAGEREFLECT**。  
  
### <a name="return-value"></a>返回值  
 一个标准的 HRESULT 值。  
  
##  <a name="getambientpalette"></a>CComControlBase::GetAmbientPalette  
 检索**DISPID_AMBIENT_PALETTE**，可用来访问容器的`HPALETTE`。  
  
```
HRESULT GetAmbientPalette(HPALETTE& hPalette);
```  
  
### <a name="parameters"></a>参数  
 `hPalette`  
 属性**DISPID_AMBIENT_PALETTE**。  
  
### <a name="return-value"></a>返回值  
 一个标准的 HRESULT 值。  
  
##  <a name="getambientproperty"></a>CComControlBase::GetAmbientProperty  
 检索指定的容器属性`dispid`。  
  
```
HRESULT GetAmbientProperty(DISPID dispid, VARIANT& var);
```  
  
### <a name="parameters"></a>参数  
 `dispid`  
 要检索的容器属性的标识符。  
  
 `var`  
 用于接收属性的变量。  
  
### <a name="return-value"></a>返回值  
 一个标准的 HRESULT 值。  
  
### <a name="remarks"></a>备注  
 ATL 提供了帮助程序函数来检索特定属性，例如，一组[CComControlBase::GetAmbientBackColor](#getambientbackcolor)。 如果没有可用的合适方法，使用`GetAmbientProperty`。  
  
##  <a name="getambientrighttoleft"></a>CComControlBase::GetAmbientRightToLeft  
 检索**DISPID_AMBIENT_RIGHTTOLEFT**，内容由容器中的显示方向。  
  
```
HRESULT GetAmbientRightToLeft(BOOL& bRightToLeft);
```  
  
### <a name="parameters"></a>参数  
 *bRightToLeft*  
 属性**DISPID_AMBIENT_RIGHTTOLEFT**。 设置为**TRUE**如果从右到左，显示内容**FALSE**如果右到左显示。  
  
### <a name="return-value"></a>返回值  
 返回成功，则为 S_OK 或失败的错误 HRESULT。  
  
##  <a name="getambientscaleunits"></a>CComControlBase::GetAmbientScaleUnits  
 检索**DISPID_AMBIENT_SCALEUNITS**的容器 （如英寸或厘米） 为加标签显示的环境单位。  
  
```
HRESULT GetAmbientScaleUnits(BSTR& bstrScaleUnits);
```  
  
### <a name="parameters"></a>参数  
 *bstrScaleUnits*  
 属性**DISPID_AMBIENT_SCALEUNITS**。  
  
### <a name="return-value"></a>返回值  
 一个标准的 HRESULT 值。  
  
##  <a name="getambientshowgrabhandles"></a>CComControlBase::GetAmbientShowGrabHandles  
 检索**DISPID_AMBIENT_SHOWGRABHANDLES**、 一个标志，指示容器是否允许要为其自身活动时显示抓取手柄的控件。  
  
```
HRESULT GetAmbientShowGrabHandles(BOOL& bShowGrabHandles);
```  
  
### <a name="parameters"></a>参数  
 *bShowGrabHandles*  
 属性**DISPID_AMBIENT_SHOWGRABHANDLES**。  
  
### <a name="return-value"></a>返回值  
 一个标准的 HRESULT 值。  
  
##  <a name="getambientshowhatching"></a>CComControlBase::GetAmbientShowHatching  
 检索**DISPID_AMBIENT_SHOWHATCHING**、 一个标志，指示容器是否允许控件以将它显示用阴影图案控件的用户界面处于活动状态时。  
  
```
HRESULT GetAmbientShowHatching(BOOL& bShowHatching);
```  
  
### <a name="parameters"></a>参数  
 *bShowHatching*  
 属性**DISPID_AMBIENT_SHOWHATCHING**。  
  
### <a name="return-value"></a>返回值  
 一个标准的 HRESULT 值。  
  
##  <a name="getambientsupportsmnemonics"></a>CComControlBase::GetAmbientSupportsMnemonics  
 检索**DISPID_AMBIENT_SUPPORTSMNEMONICS**、 一个标志，指示容器是否支持键盘助记键。  
  
```
HRESULT GetAmbientSupportsMnemonics(BOOL& bSupportsMnemonics);
```  
  
### <a name="parameters"></a>参数  
 *bSupportsMnemonics*  
 属性**DISPID_AMBIENT_SUPPORTSMNEMONICS**。  
  
### <a name="return-value"></a>返回值  
 一个标准的 HRESULT 值。  
  
##  <a name="getambienttextalign"></a>CComControlBase::GetAmbientTextAlign  
 检索**DISPID_AMBIENT_TEXTALIGN**，由容器首选的文本对齐方式： 常规对齐 （左数字右，文本） 为 0、 1 表示左对齐、 居中对齐的 2 和右对齐的 3。  
  
```
HRESULT GetAmbientTextAlign(short& nTextAlign);
```  
  
### <a name="parameters"></a>参数  
 *nTextAlign*  
 属性**DISPID_AMBIENT_TEXTALIGN**。  
  
### <a name="return-value"></a>返回值  
 一个标准的 HRESULT 值。  
  
##  <a name="getambienttoptobottom"></a>CComControlBase::GetAmbientTopToBottom  
 检索**DISPID_AMBIENT_TOPTOBOTTOM**，内容由容器中的显示方向。  
  
```
HRESULT GetAmbientTopToBottom(BOOL& bTopToBottom);
```  
  
### <a name="parameters"></a>参数  
 *bTopToBottom*  
 属性**DISPID_AMBIENT_TOPTOBOTTOM**。 设置为**TRUE**如果显示的文本从上到下， **FALSE**如果显示底部到顶部。  
  
### <a name="return-value"></a>返回值  
 返回成功，则为 S_OK 或失败的错误 HRESULT。  
  
##  <a name="getambientuidead"></a>CComControlBase::GetAmbientUIDead  
 检索**DISPID_AMBIENT_UIDEAD**、 一个标志，指示容器是否想要响应用户界面操作的控件。  
  
```
HRESULT GetAmbientUIDead(BOOL& bUIDead);
```  
  
### <a name="parameters"></a>参数  
 *bUIDead*  
 属性**DISPID_AMBIENT_UIDEAD**。  
  
### <a name="return-value"></a>返回值  
 一个标准的 HRESULT 值。  
  
### <a name="remarks"></a>备注  
 如果**TRUE**，控件不应作出响应。 此标志而不考虑适用**DISPID_AMBIENT_USERMODE**标志。 请参阅[CComControlBase::GetAmbientUserMode](#getambientusermode)。  
  
##  <a name="getambientusermode"></a>CComControlBase::GetAmbientUserMode  
 检索**DISPID_AMBIENT_USERMODE**、 一个标志，指示容器是否处于运行模式 ( **TRUE**) 或设计模式 ( **FALSE**)。  
  
```
HRESULT GetAmbientUserMode(BOOL& bUserMode);
```  
  
### <a name="parameters"></a>参数  
 `bUserMode`  
 属性**DISPID_AMBIENT_USERMODE**。  
  
### <a name="return-value"></a>返回值  
 一个标准的 HRESULT 值。  
  
##  <a name="getdirty"></a>CComControlBase::GetDirty  
 返回的数据成员的值`m_bRequiresSave`。  
  
```
BOOL GetDirty();
```  
  
### <a name="return-value"></a>返回值  
 返回的数据成员的值[m_bRequiresSave](#m_brequiressave)。  
  
### <a name="remarks"></a>备注  
 此值设置使用[CComControlBase::SetDirty](#setdirty)。  
  
##  <a name="getzoominfo"></a>CComControlBase::GetZoomInfo  
 检索的 x 和 y 分子和缩放系数分母的值的控件为激活就地编辑。  
  
```
void GetZoomInfo(ATL_DRAWINFO& di);
```  
  
### <a name="parameters"></a>参数  
 `di`  
 结构，它将保存缩放系数分子和分母。 有关详细信息，请参阅[ATL_DRAWINFO](../../atl/reference/atl-drawinfo-structure.md)。  
  
### <a name="remarks"></a>备注  
 缩放系数是其当前范围内的控件的原始大小的比例。  
  
##  <a name="inplaceactivate"></a>CComControlBase::InPlaceActivate  
 使控件从任何状态中的动词的非活动状态转换到`iVerb`指示。  
  
```
HRESULT InPlaceActivate(LONG iVerb, const RECT* prcPosRect = NULL);
```  
  
### <a name="parameters"></a>参数  
 `iVerb`  
 值，该值指示要执行的操作[IOleObjectImpl::DoVerb](../../atl/reference/ioleobjectimpl-class.md#doverb)。  
  
 *prcPosRect*  
 指向就地控件的位置的指针。  
  
### <a name="return-value"></a>返回值  
 一个标准的 HRESULT 值。  
  
### <a name="remarks"></a>备注  
 之前激活，此方法检查该控件具有客户端站点、 检查可见，该控件，获取父窗口中的控件的位置。 激活控件后，此方法将激活控件的用户界面，并通知容器以使控件可见。  
  
 此方法还会检索`IOleInPlaceSite`， **IOleInPlaceSiteEx**，或**IOleInPlaceSiteWindowless**控件的接口指针并将它存储在控件类的数据成员[CComControlBase::m_spInPlaceSite](#m_spinplacesite)。 控件类数据成员[CComControlBase::m_bInPlaceSiteEx](#m_binplacesiteex)， [CComControlBase::m_bWndLess](#m_bwndless)， [CComControlBase::m_bWasOnceWindowless](#m_bwasoncewindowless)，和[CComControlBase::m_bNegotiatedWnd](#m_bnegotiatedwnd)设置为 true，根据需要。  
  
##  <a name="internalgetsite"></a>CComControlBase::InternalGetSite  
 调用此方法来查询控件所在位置到标识的接口的指针。  
  
```
HRESULT InternalGetSite(REFIID riid, void** ppUnkSite);
```  
  
### <a name="parameters"></a>参数  
 `riid`  
 应在返回的接口指针的 IID `ppUnkSite`。  
  
 `ppUnkSite`  
 接收请求中的接口指针的指针变量的地址`riid`。  
  
### <a name="return-value"></a>返回值  
 返回成功，则为 S_OK 或失败的错误 HRESULT。  
  
### <a name="remarks"></a>备注  
 如果站点支持在请求的接口`riid`，指针会返回通过`ppUnkSite`。 否则为`ppUnkSite`设置为 NULL。  
  
##  <a name="m_bautosize"></a>CComControlBase::m_bAutoSize  
 指示该控件不能为任何其他大小的标志。  
  
```
unsigned m_bAutoSize:1;
```  
  
### <a name="remarks"></a>备注  
 通过检查此标志`IOleObjectImpl::SetExtent`并且，如果**TRUE**，导致要返回的函数**E_FAIL**。  
  
> [!NOTE]
>  若要使用你的控件类中将此数据成员，你必须将其声明为一个数据成员中你的控件类。 你的控件类将从基类继承该数据成员，因为它在基类中的联合内声明。  
  
 如果你添加**自动大小**选项[常用属性](../../atl/reference/stock-properties-atl-control-wizard.md)ATL 控件向导，该向导的选项卡自动在你的控件类中创建此数据成员、 创建 put 和 get 方法的属性并支持[IPropertyNotifySink](http://msdn.microsoft.com/library/windows/desktop/ms692638)以在属性变化时自动通知容器。  
  
##  <a name="m_bdrawfromnatural"></a>CComControlBase::m_bDrawFromNatural  
 标志指示`IDataObjectImpl::GetData`和`CComControlBase::GetZoomInfo`应设置从控件大小`m_sizeNatural`而不是从`m_sizeExtent`。  
  
```
unsigned m_bDrawFromNatural:1;
```  
  
### <a name="remarks"></a>备注  
  
> [!NOTE]
>  若要使用你的控件类中将此数据成员，你必须将其声明为一个数据成员中你的控件类。 你的控件类将从基类继承该数据成员，因为它在基类中的联合内声明。  
  
##  <a name="m_bdrawgetdatainhimetric"></a>CComControlBase::m_bDrawGetDataInHimetric  
 标志指示`IDataObjectImpl::GetData`应在绘制时使用 himetric 为单位，不像素。  
  
```
unsigned m_bDrawGetDataInHimetric:1;
```  
  
### <a name="remarks"></a>备注  
 每个逻辑的 HIMETRIC 单位是 0.01 毫米。  
  
> [!NOTE]
>  若要使用你的控件类中将此数据成员，你必须将其声明为一个数据成员中你的控件类。 你的控件类将从基类继承该数据成员，因为它在基类中的联合内声明。  
  
##  <a name="m_binplaceactive"></a>CComControlBase::m_bInPlaceActive  
 该标志指明控件处于就地活动状态。  
  
```
unsigned m_bInPlaceActive:1;
```  
  
### <a name="remarks"></a>备注  
 这意味着控件可见和其窗口，如果有的话，可见，但其菜单和工具栏可能未处于活动状态。 `m_bUIActive`标志指示控件的用户界面，例如菜单，还处于活动状态。  
  
> [!NOTE]
>  若要使用你的控件类中将此数据成员，你必须将其声明为一个数据成员中你的控件类。 你的控件类将从基类继承该数据成员，因为它在基类中的联合内声明。  
  
##  <a name="m_binplacesiteex"></a>CComControlBase::m_bInPlaceSiteEx  
 该标志指明容器支持**IOleInPlaceSiteEx**接口和 OCX96 控制功能，如无窗口和闪烁的控件。  
  
```
unsigned m_bInPlaceSiteEx:1;
```  
  
### <a name="remarks"></a>备注  
  
> [!NOTE]
>  若要使用你的控件类中将此数据成员，你必须将其声明为一个数据成员中你的控件类。 你的控件类将从基类继承该数据成员，因为它在基类中的联合内声明。  
  
 数据成员`m_spInPlaceSite`指向[IOleInPlaceSite](http://msdn.microsoft.com/library/windows/desktop/ms686586)， [IOleInPlaceSiteEx](http://msdn.microsoft.com/library/windows/desktop/ms693461)，或[IOleInPlaceSiteWindowless](http://msdn.microsoft.com/library/windows/desktop/ms682300)接口，具体取决于的值`m_bWndLess`和`m_bInPlaceSiteEx`标志。 (数据成员`m_bNegotiatedWnd`必须**TRUE**为`m_spInPlaceSite`指针才能有效。)  
  
 如果`m_bWndLess`是**FALSE**和`m_bInPlaceSiteEx`是**TRUE**，`m_spInPlaceSite`是**IOleInPlaceSiteEx**接口指针。 请参阅[m_spInPlaceSite](#m_spinplacesite)显示这些三个数据成员之间的关系的表。  
  
##  <a name="m_bnegotiatedwnd"></a>CComControlBase::m_bNegotiatedWnd  
 该标志指明控件具有与支持 OCX96 控件功能 （如闪烁和无窗口控件） 的容器进行协商和控件是开窗还是无窗口。  
  
```
unsigned m_bNegotiatedWnd:1;
```  
  
### <a name="remarks"></a>备注  
  
> [!NOTE]
>  若要使用你的控件类中将此数据成员，你必须将其声明为一个数据成员中你的控件类。 你的控件类将从基类继承该数据成员，因为它在基类中的联合内声明。  
  
 `m_bNegotiatedWnd`标志必须为**TRUE**为`m_spInPlaceSite`指针才能有效。  
  
##  <a name="m_brecomposeonresize"></a>CComControlBase::m_bRecomposeOnResize  
 该标志指明控件想要重排与其演示当容器更改控件的显示大小。  
  
```
unsigned m_bRecomposeOnResize:1;
```  
  
### <a name="remarks"></a>备注  
  
> [!NOTE]
>  若要使用你的控件类中将此数据成员，你必须将其声明为一个数据成员中你的控件类。 你的控件类将从基类继承该数据成员，因为它在基类中的联合内声明。  
  
 通过检查此标志[IOleObjectImpl::SetExtent](../../atl/reference/ioleobjectimpl-class.md#setextent)并且，如果**TRUE**，`SetExtent`通知查看更改的容器。 如果设置此标志， **OLEMISC_RECOMPOSEONRESIZE**中位[OLEMISC](http://msdn.microsoft.com/library/windows/desktop/ms678497)枚举还应将设置。  
  
##  <a name="m_brequiressave"></a>CComControlBase::m_bRequiresSave  
 指示自上次保存后，该控件已更改的标志。  
  
```
unsigned m_bRequiresSave:1;
```  
  
### <a name="remarks"></a>备注  
 值`m_bRequiresSave`可以用来设置[CComControlBase::SetDirty](#setdirty)和与检索到[CComControlBase::GetDirty](#getdirty)。  
  
> [!NOTE]
>  若要使用你的控件类中将此数据成员，你必须将其声明为一个数据成员中你的控件类。 你的控件类将从基类继承该数据成员，因为它在基类中的联合内声明。  
  
##  <a name="m_bresizenatural"></a>CComControlBase::m_bResizeNatural  
 标志，指示该控件想要调整大小其原始大小 （其未缩放物理大小） 容器时更改控件的显示大小。  
  
```
unsigned m_bResizeNatural:1;
```  
  
### <a name="remarks"></a>备注  
 通过检查此标志`IOleObjectImpl::SetExtent`并且，如果**TRUE**，大小传入`SetExtent`分配给`m_sizeNatural`。  
  
 大小传入`SetExtent`始终将分配给`m_sizeExtent`，而不考虑的值的`m_bResizeNatural`。  
  
> [!NOTE]
>  若要使用你的控件类中将此数据成员，你必须将其声明为一个数据成员中你的控件类。 你的控件类将从基类继承该数据成员，因为它在基类中的联合内声明。  
  
##  <a name="m_buiactive"></a>CComControlBase::m_bUIActive  
 标志，指示控件的用户界面，例如菜单和工具栏，处于活动状态。  
  
```
unsigned m_bUIActive:1;
```  
  
### <a name="remarks"></a>备注  
 `m_bInPlaceActive`标志指示控件是否处于活动状态，但不是其用户界面处于活动状态。  
  
> [!NOTE]
>  若要使用你的控件类中将此数据成员，你必须将其声明为一个数据成员中你的控件类。 你的控件类将从基类继承该数据成员，因为它在基类中的联合内声明。  
  
##  <a name="m_busingwindowrgn"></a>CComControlBase::m_bUsingWindowRgn  
 该标志指明控件使用提供容器的窗口区域。  
  
```
unsigned m_bUsingWindowRgn:1;
```  
  
### <a name="remarks"></a>备注  
  
> [!NOTE]
>  若要使用你的控件类中将此数据成员，你必须将其声明为一个数据成员中你的控件类。 你的控件类将从基类继承该数据成员，因为它在基类中的联合内声明。  
  
##  <a name="m_bwasoncewindowless"></a>CComControlBase::m_bWasOnceWindowless  
 指示该控件已无窗口，但可能也可能不是无窗口现在的标志。  
  
```
unsigned m_bWasOnceWindowless:1;
```  
  
### <a name="remarks"></a>备注  
  
> [!NOTE]
>  若要使用你的控件类中将此数据成员，你必须将其声明为一个数据成员中你的控件类。 你的控件类将从基类继承该数据成员，因为它在基类中的联合内声明。  
  
##  <a name="m_bwindowonly"></a>CComControlBase::m_bWindowOnly  
 指示该控件应开窗，即使容器支持无窗口控件的标志。  
  
```
unsigned m_bWindowOnly:1;
```  
  
### <a name="remarks"></a>备注  
  
> [!NOTE]
>  若要使用你的控件类中将此数据成员，你必须将其声明为一个数据成员中你的控件类。 你的控件类将从基类继承该数据成员，因为它在基类中的联合内声明。  
  
##  <a name="m_bwndless"></a>CComControlBase::m_bWndLess  
 用于指示无窗口控件的标记。  
  
```
unsigned m_bWndLess:1;
```  
  
### <a name="remarks"></a>备注  
  
> [!NOTE]
>  若要使用你的控件类中将此数据成员，你必须将其声明为一个数据成员中你的控件类。 你的控件类将从基类继承该数据成员，因为它在基类中的联合内声明。  
  
 数据成员`m_spInPlaceSite`指向[IOleInPlaceSite](http://msdn.microsoft.com/library/windows/desktop/ms686586)， [IOleInPlaceSiteEx](http://msdn.microsoft.com/library/windows/desktop/ms693461)，或[IOleInPlaceSiteWindowless](http://msdn.microsoft.com/library/windows/desktop/ms682300)接口，具体取决于的值`m_bWndLess`和[CComControlBase::m_bInPlaceSiteEx](#m_binplacesiteex)标志。 (数据成员[CComControlBase::m_bNegotiatedWnd](#m_bnegotiatedwnd)必须**TRUE**为[CComControlBase::m_spInPlaceSite](#m_spinplacesite)指针才能有效。)  
  
 如果`m_bWndLess`是**TRUE**，`m_spInPlaceSite`是**IOleInPlaceSiteWindowless**接口指针。 请参阅[CComControlBase::m_spInPlaceSite](#m_spinplacesite)显示这些数据成员之间的完整关系的表。  
  
##  <a name="m_hwndcd"></a>CComControlBase::m_hWndCD  
 包含对与控件关联的窗口句柄的引用。  
  
```
HWND& m_hWndCD;
```  
  
### <a name="remarks"></a>备注  
  
> [!NOTE]
>  若要使用你的控件类中将此数据成员，你必须将其声明为一个数据成员中你的控件类。 你的控件类将从基类继承该数据成员，因为它在基类中的联合内声明。  
  
##  <a name="m_nfreezeevents"></a>CComControlBase::m_nFreezeEvents  
 次数计数容器已冻结 （拒绝接受事件） 的事件，而无需干预的解除冻结的事件 （事件接受）。  
  
```
short m_nFreezeEvents;
```  
  
### <a name="remarks"></a>备注  
  
> [!NOTE]
>  若要使用你的控件类中将此数据成员，你必须将其声明为一个数据成员中你的控件类。 你的控件类将从基类继承该数据成员，因为它在基类中的联合内声明。  
  
##  <a name="m_rcpos"></a>CComControlBase::m_rcPos  
 控件，以容器的坐标表示的位置，以像素为单位。  
  
```
RECT m_rcPos;
```  
  
### <a name="remarks"></a>备注  
  
> [!NOTE]
>  若要使用你的控件类中将此数据成员，你必须将其声明为一个数据成员中你的控件类。 你的控件类将从基类继承该数据成员，因为它在基类中的联合内声明。  
  
##  <a name="m_sizeextent"></a>CComControlBase::m_sizeExtent  
 以 himetric 为单位 （每个单位是 0.01 毫米） 的特定显示控件的范围。  
  
```
SIZE m_sizeExtent;
```  
  
### <a name="remarks"></a>备注  
  
> [!NOTE]
>  若要使用你的控件类中将此数据成员，你必须将其声明为一个数据成员中你的控件类。 你的控件类将从基类继承该数据成员，因为它在基类中的联合内声明。  
  
 此大小是通过显示进行缩放。 中指定控件的物理大小`m_sizeNatural`数据成员，并且固定。  
  
 你可以将大小转换为全局函数的像素[AtlHiMetricToPixel](pixel-himetric-conversion-global-functions.md#atlhimetrictopixel)。  
  
##  <a name="m_sizenatural"></a>CComControlBase::m_sizeNatural  
 以 himetric 为单位 （每个单位是 0.01 毫米） 控件的物理大小。  
  
```
SIZE m_sizeNatural;
```  
  
### <a name="remarks"></a>备注  
  
> [!NOTE]
>  若要使用你的控件类中将此数据成员，你必须将其声明为一个数据成员中你的控件类。 你的控件类将从基类继承该数据成员，因为它在基类中的联合内声明。  
  
 此大小固定的时的大小以`m_sizeExtent`按显示进行缩放。  
  
 你可以将大小转换为全局函数的像素[AtlHiMetricToPixel](pixel-himetric-conversion-global-functions.md#atlhimetrictopixel)。  
  
##  <a name="m_spadvisesink"></a>CComControlBase::m_spAdviseSink  
 指向通知连接对该容器的直接指针 (容器的[IAdviseSink](http://msdn.microsoft.com/library/windows/desktop/ms692513))。  
  
```
CComPtr<IAdviseSink>
    m_spAdviseSink;
```     
  
### <a name="remarks"></a>备注  
  
> [!NOTE]
>  若要使用你的控件类中将此数据成员，你必须将其声明为一个数据成员中你的控件类。 你的控件类将从基类继承该数据成员，因为它在基类中的联合内声明。  
  
##  <a name="m_spambientdispatch"></a>CComControlBase::m_spAmbientDispatch  
 A`CComDispatchDriver`对象，允许您检索和设置对象的属性通过`IDispatch`指针。  
  
```
CComDispatchDriver m_spAmbientDispatch;
```  
  
### <a name="remarks"></a>备注  
  
> [!NOTE]
>  若要使用你的控件类中将此数据成员，你必须将其声明为一个数据成员中你的控件类。 你的控件类将从基类继承该数据成员，因为它在基类中的联合内声明。  
  
##  <a name="m_spclientsite"></a>CComControlBase::m_spClientSite  
 指向控件的客户端站点容器内的指针。  
  
```
CComPtr<IOleClientSite>
    m_spClientSite;
```     
  
### <a name="remarks"></a>备注  
  
> [!NOTE]
>  若要使用你的控件类中将此数据成员，你必须将其声明为一个数据成员中你的控件类。 你的控件类将从基类继承该数据成员，因为它在基类中的联合内声明。  
  
##  <a name="m_spdataadviseholder"></a>CComControlBase::m_spDataAdviseHolder  
 提供一种标准意味着来保留数据对象之间的通知连接和建议的接收器。  
  
```
CComPtr<IDataAdviseHolder>
    m_spDataAdviseHolder;
```     
  
### <a name="remarks"></a>备注  
  
> [!NOTE]
>  若要使用你的控件类中将此数据成员，你必须将其声明为一个数据成员中你的控件类。 你的控件类将从基类继承该数据成员，因为它在基类中的联合内声明。  
  
 数据对象是一个控件，可以传输数据，并实现[IDataObject](http://msdn.microsoft.com/library/windows/desktop/ms688421)，其方法指定的数据格式和传输媒体。  
  
 接口`m_spDataAdviseHolder`实现[IDataObject::DAdvise](http://msdn.microsoft.com/library/windows/desktop/ms692579)和[IDataObject::DUnadvise](http://msdn.microsoft.com/library/windows/desktop/ms692448)建立和删除到容器的通知连接方法。 控件的容器必须通过支持实现建议接收器[IAdviseSink](http://msdn.microsoft.com/library/windows/desktop/ms692513)接口。  
  
##  <a name="m_spinplacesite"></a>CComControlBase::m_spInPlaceSite  
 指向容器的[IOleInPlaceSite](http://msdn.microsoft.com/library/windows/desktop/ms686586)， [IOleInPlaceSiteEx](http://msdn.microsoft.com/library/windows/desktop/ms693461)，或[IOleInPlaceSiteWindowless](http://msdn.microsoft.com/library/windows/desktop/ms682300)接口指针。  
  
```
CComPtr<IOleInPlaceSiteWindowless>
    m_spInPlaceSite;
```     
  
### <a name="remarks"></a>备注  
  
> [!NOTE]
>  若要使用你的控件类中将此数据成员，你必须将其声明为一个数据成员中你的控件类。 你的控件类将从基类继承该数据成员，因为它在基类中的联合内声明。  
  
 `m_spInPlaceSite`指针无效才[m_bNegotiatedWnd](#m_bnegotiatedwnd)标志**TRUE**。  
  
 下表显示如何`m_spInPlaceSite`指针类型取决于[m_bWndLess](#m_bwndless)和[m_bInPlaceSiteEx](#m_binplacesiteex)数据成员标志：  
  
|m_spInPlaceSite 类型|m_bWndLess 值|m_bInPlaceSiteEx 值|  
|---------------------------|-----------------------|-----------------------------|  
|**IOleInPlaceSiteWindowless**|**TRUE**|**TRUE**或**FALSE**|  
|**IOleInPlaceSiteEx**|**FALSE**|**TRUE**|  
|`IOleInPlaceSite`|**FALSE**|**FALSE**|  
  
##  <a name="m_spoleadviseholder"></a>CComControlBase::m_spOleAdviseHolder  
 提供一种方法来保存的通知连接的标准实现。  
  
```
CComPtr<IOleAdviseHolder>
    m_spOleAdviseHolder;
```     
  
### <a name="remarks"></a>备注  
  
> [!NOTE]
>  若要使用你的控件类中将此数据成员，你必须将其声明为一个数据成员中你的控件类。 你的控件类将从基类继承该数据成员，因为它在基类中的联合内声明。  
  
 接口`m_spOleAdviseHolder`实现[IOleObject::Advise](http://msdn.microsoft.com/library/windows/desktop/ms686573)和[IOleObject::Unadvise](http://msdn.microsoft.com/library/windows/desktop/ms693749)建立和删除到容器的通知连接方法。 控件的容器必须通过支持实现建议接收器[IAdviseSink](http://msdn.microsoft.com/library/windows/desktop/ms692513)接口。  
  
##  <a name="ondraw"></a>CComControlBase::OnDraw  
 重写此方法以绘制控件。  
  
```
virtual HRESULT OnDraw(ATL_DRAWINFO& di);
```  
  
### <a name="parameters"></a>参数  
 `di`  
 对引用[ATL_DRAWINFO](../../atl/reference/atl-drawinfo-structure.md)结构，其中包含图形信息，如绘图方面，控件边界，并绘制以或不优化。  
  
### <a name="return-value"></a>返回值  
 标准 `HRESULT` 值。  
  
### <a name="remarks"></a>备注  
 默认值`OnDraw`删除或还原的设备上下文或不执行任何操作，具体取决于在中设置的标志[CComControlBase::OnDrawAdvanced](#ondrawadvanced)。  
  
 `OnDraw`方法自动添加到你的控件类，当使用 ATL 控件向导创建你的控件。 向导的默认`OnDraw`用"ATL 8.0"的标签绘制矩形。  
  
### <a name="example"></a>示例  
 请参阅示例[CComControlBase::GetAmbientAppearance](#getambientappearance)。  
  
##  <a name="ondrawadvanced"></a>CComControlBase::OnDrawAdvanced  
 默认值`OnDrawAdvanced`准备规范化的设备上下文进行绘制，然后调用你的控件类`OnDraw`方法。  
  
```
virtual HRESULT OnDrawAdvanced(ATL_DRAWINFO& di);
```  
  
### <a name="parameters"></a>参数  
 `di`  
 对引用[ATL_DRAWINFO](../../atl/reference/atl-drawinfo-structure.md)结构，其中包含图形信息，如绘图方面，控件边界，并绘制以或不优化。  
  
### <a name="return-value"></a>返回值  
 标准 `HRESULT` 值。  
  
### <a name="remarks"></a>备注  
 如果你想要接受不规范化它的情况下传递由容器的设备上下文，重写此方法。  
  
 请参阅[CComControlBase::OnDraw](#ondraw)有关详细信息。  
  
##  <a name="onkillfocus"></a>CComControlBase::OnKillFocus  
 检查该控件是处于就地活动状态并且具有有效的控制站点，则通知容器控件已失去焦点。  
  
```
LRESULT OnKillFocus(UINT /* nMsg */,
    WPARAM /* wParam */,
    LPARAM /* lParam */,
    BOOL& bHandled);
```  
  
### <a name="parameters"></a>参数  
 `nMsg`  
 保留。  
  
 `wParam`  
 保留。  
  
 `lParam`  
 保留。  
  
 `bHandled`  
 该标志指示是否已成功处理的窗口消息。 默认值为 `FALSE`。  
  
### <a name="return-value"></a>返回值  
 始终返回 1。  
  
##  <a name="onmouseactivate"></a>CComControlBase::OnMouseActivate  
 检查用户界面在用户模式下，则将激活的控件。  
  
```
LRESULT OnMouseActivate(UINT /* nMsg */,
    WPARAM /* wParam */,
    LPARAM /* lParam */,
    BOOL& bHandled);
```  
  
### <a name="parameters"></a>参数  
 `nMsg`  
 保留。  
  
 `wParam`  
 保留。  
  
 `lParam`  
 保留。  
  
 `bHandled`  
 该标志指示是否已成功处理的窗口消息。 默认值为 `FALSE`。  
  
### <a name="return-value"></a>返回值  
 始终返回 1。  
  
##  <a name="onpaint"></a>CComControlBase::OnPaint  
 为绘制准备容器，获取控件的客户端区域中，然后调用的控件类`OnDrawAdvanced`方法。  
  
```
LRESULT OnPaint(UINT /* nMsg */,
    WPARAM wParam,
    LPARAM /* lParam */,
    BOOL& /* lResult */);
```  
  
### <a name="parameters"></a>参数  
 `nMsg`  
 保留。  
  
 `wParam`  
 现有 HDC。  
  
 `lParam`  
 保留。  
  
 `lResult`  
 保留。  
  
### <a name="return-value"></a>返回值  
 始终返回零。  
  
### <a name="remarks"></a>备注  
 如果`wParam`不为 NULL，`OnPaint`假定它包含有效 HDC 并使用它而不是[CComControlBase::m_hWndCD](#m_hwndcd)。  
  
##  <a name="onsetfocus"></a>CComControlBase::OnSetFocus  
 检查该控件是处于就地活动状态并且具有有效的控制站点，则通知容器控件获得焦点。  
  
```
LRESULT OnSetFocus(UINT /* nMsg */,
    WPARAM /* wParam */,
    LPARAM /* lParam */,
    BOOL& bHandled);
```  
  
### <a name="parameters"></a>参数  
 `nMsg`  
 保留。  
  
 `wParam`  
 保留。  
  
 `lParam`  
 保留。  
  
 `bHandled`  
 该标志指示是否已成功处理的窗口消息。 默认值为 `FALSE`。  
  
### <a name="return-value"></a>返回值  
 始终返回 1。  
  
### <a name="remarks"></a>备注  
 发送通知到容器控件已收到焦点。  
  
##  <a name="pretranslateaccelerator"></a>CComControlBase::PreTranslateAccelerator  
 重写该方法以提供您自己的键盘快捷键处理程序。  
  
```
BOOL PreTranslateAccelerator(LPMSG /* pMsg */,
    HRESULT& /* hRet */);
```  
  
### <a name="parameters"></a>参数  
 `pMsg`  
 保留。  
  
 *hRet*  
 保留。  
  
### <a name="return-value"></a>返回值  
 默认情况下返回**FALSE**。  
  
##  <a name="sendonclose"></a>CComControlBase::SendOnClose  
 通知注册已关闭该控件的建议持有的所有通知接收器。  
  
```
HRESULT SendOnClose();
```  
  
### <a name="return-value"></a>返回值  
 返回成功，则为 S_OK 或失败的错误 HRESULT。  
  
### <a name="remarks"></a>备注  
 发送通知控件已关闭其通知接收器。  
  
##  <a name="sendondatachange"></a>CComControlBase::SendOnDataChange  
 通知注册控制数据已更改的建议持有的所有通知接收器。  
  
```
HRESULT SendOnDataChange(DWORD advf = 0);
```  
  
### <a name="parameters"></a>参数  
 *一个指针*  
 建议标志，用于指定如何对的调用[IAdviseSink::OnDataChange](http://msdn.microsoft.com/library/windows/desktop/ms687283)进行。 值为[一个指针](http://msdn.microsoft.com/library/windows/desktop/ms693742)枚举。  
  
### <a name="return-value"></a>返回值  
 返回成功，则为 S_OK 或失败的错误 HRESULT。  
  
##  <a name="sendonrename"></a>CComControlBase::SendOnRename  
 通知注册该控件具有新的名字对象的建议持有的所有通知接收器。  
  
```
HRESULT SendOnRename(IMoniker* pmk);
```  
  
### <a name="parameters"></a>参数  
 *pmk*  
 控件的新名字对象的指针。  
  
### <a name="return-value"></a>返回值  
 返回成功，则为 S_OK 或失败的错误 HRESULT。  
  
### <a name="remarks"></a>备注  
 发送通知的控件的标记已更改。  
  
##  <a name="sendonsave"></a>CComControlBase::SendOnSave  
 通知注册保存该控件的建议持有的所有通知接收器。  
  
```
HRESULT SendOnSave();
```  
  
### <a name="return-value"></a>返回值  
 返回成功，则为 S_OK 或失败的错误 HRESULT。  
  
### <a name="remarks"></a>备注  
 发送通知控件具有刚保存其数据。  
  
##  <a name="sendonviewchange"></a>CComControlBase::SendOnViewChange  
 通知所有已注册的控件的视图已更改的通知接收器。  
  
```
HRESULT SendOnViewChange(DWORD dwAspect, LONG lindex = -1);
```  
  
### <a name="parameters"></a>参数  
 `dwAspect`  
 方面或控件视图中。  
  
 *索引*  
 已更改视图的部分。 仅为-1 是有效的。  
  
### <a name="return-value"></a>返回值  
 返回成功，则为 S_OK 或失败的错误 HRESULT。  
  
### <a name="remarks"></a>备注  
 `SendOnViewChange`调用[IAdviseSink::OnViewChange](http://msdn.microsoft.com/library/windows/desktop/ms694337)。 唯一的值的*索引*当前支持为-1，指示整个视图是感兴趣。  
  
##  <a name="setcontrolfocus"></a>CComControlBase::SetControlFocus  
 设置或删除到或从控件的键盘焦点。  
  
```
BOOL SetControlFocus(BOOL bGrab);
```  
  
### <a name="parameters"></a>参数  
 *bGrab*  
 如果**TRUE**，将键盘焦点设置为调用控件。 如果**FALSE**，通过调用控件中，删除键盘焦点，提供它具有焦点。  
  
### <a name="return-value"></a>返回值  
 返回**TRUE**如果控件已成功接收到焦点; 否则为**FALSE**。  
  
### <a name="remarks"></a>备注  
 对于有窗口控件，Windows API 函数[SetFocus](http://msdn.microsoft.com/library/windows/desktop/ms646312)调用。 对于无窗口控件， [IOleInPlaceSiteWindowless::SetFocus](http://msdn.microsoft.com/library/windows/desktop/ms679745)调用。 通过此调用，无窗口控件获取键盘焦点，并可以响应窗口消息。  
  
##  <a name="setdirty"></a>CComControlBase::SetDirty  
 设置的数据成员`m_bRequiresSave`到中的值`bDirty`。  
  
```
void SetDirty(BOOL bDirty);
```  
  
### <a name="parameters"></a>参数  
 `bDirty`  
 数据成员值[CComControlBase::m_bRequiresSave](#m_brequiressave)。  
  
### <a name="remarks"></a>备注  
 **SetDirty(TRUE)**应调用以控制已更改自上次保存后的标志。 值`m_bRequiresSave`使用检索[CComControlBase::GetDirty](#getdirty)。  
  
## <a name="see-also"></a>请参阅  
 [CComControl 类](../../atl/reference/ccomcontrol-class.md)   
 [类概述](../../atl/atl-class-overview.md)
