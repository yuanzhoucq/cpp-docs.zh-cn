---
title: CComControlBase 类
ms.date: 11/04/2016
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
helpviewer_keywords:
- CComControlBase class
ms.assetid: 3d1bf022-acf2-4092-8283-ff8cee6332f3
ms.openlocfilehash: fa7562f49834bf71da6bd095aec19360a43f1538
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50447952"
---
# <a name="ccomcontrolbase-class"></a>CComControlBase 类

此类提供用于创建和管理 ATL 控件的方法。

> [!IMPORTANT]
>  不能在 Windows 运行时中执行的应用程序中使用此类和其成员。

## <a name="syntax"></a>语法

```
class ATL_NO_VTABLE CComControlBase
```

## <a name="members"></a>成员

### <a name="public-typedefs"></a>公共 Typedef

|名称|描述|
|----------|-----------------|
|[CComControlBase::AppearanceType](#appearancetype)|如果重写你`m_nAppearance`常用属性的类型不是**短**。|

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[CComControlBase::CComControlBase](#ccomcontrolbase)|构造函数。|
|[CComControlBase:: ~ CComControlBase](#dtor)|析构函数。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CComControlBase::ControlQueryInterface](#controlqueryinterface)|检索指向所请求的接口的指针。|
|[CComControlBase::DoesVerbActivate](#doesverbactivate)|检查两个*iVerb*使用的参数`IOleObjectImpl::DoVerb`或者激活控件的用户界面 (*iVerb*等于 OLEIVERB_UIACTIVATE)，定义当用户双击所执行的操作控件 (*iVerb*等于 OLEIVERB_PRIMARY)，显示控件 (*iVerb*等于 OLEIVERB_SHOW)，或激活的控件 (*iVerb*等于 OLEIVERB_INPLACEACTIVATE)。|
|[CComControlBase::DoesVerbUIActivate](#doesverbuiactivate)|检查两个*iVerb*使用的参数`IOleObjectImpl::DoVerb`会导致控件的用户界面激活，则返回 TRUE。|
|[CComControlBase::DoVerbProperties](#doverbproperties)|显示控件的属性页。|
|[CComControlBase::FireViewChange](#fireviewchange)|调用此方法以通知容器重绘该控件，或通知控件的视图已更改的已注册的通知接收器。|
|[CComControlBase::GetAmbientAppearance](#getambientappearance)|检索 DISPID_AMBIENT_APPEARANCE，设置控件的当前外观： 0 表示平面，1 表示 3D。|
|[CComControlBase::GetAmbientAutoClip](#getambientautoclip)|检索 DISPID_AMBIENT_AUTOCLIP，一个标志，指示容器是否支持自动的控件显示区域的剪辑。|
|[CComControlBase::GetAmbientBackColor](#getambientbackcolor)|检索 DISPID_AMBIENT_BACKCOLOR，由容器定义的所有控件的环境背景色。|
|[CComControlBase::GetAmbientCharSet](#getambientcharset)|检索 DISPID_AMBIENT_CHARSET，对于所有控件，由容器定义的环境的字符集。|
|[CComControlBase::GetAmbientCodePage](#getambientcodepage)|检索 DISPID_AMBIENT_CODEPAGE，对于所有控件，由容器定义的环境的字符集。|
|[CComControlBase::GetAmbientDisplayAsDefault](#getambientdisplayasdefault)|检索 DISPID_AMBIENT_DISPLAYASDEFAULT，如果容器已标记为默认按钮，此站点中的控件和因此按钮控件应绘制本身使用较粗的框架，则为 TRUE 的标志。|
|[CComControlBase::GetAmbientDisplayName](#getambientdisplayname)|检索 DISPID_AMBIENT_DISPLAYNAME，容器具有提供给控件的名称。|
|[CComControlBase::GetAmbientFont](#getambientfont)|检索指向容器的环境`IFont`接口。|
|[CComControlBase::GetAmbientFontDisp](#getambientfontdisp)|检索指向容器的环境`IFontDisp`调度接口。|
|[CComControlBase::GetAmbientForeColor](#getambientforecolor)|检索 DISPID_AMBIENT_FORECOLOR，由容器定义的所有控件的环境前景色。|
|[CComControlBase::GetAmbientLocaleID](#getambientlocaleid)|检索 DISPID_AMBIENT_LOCALEID，容器使用的语言的标识符。|
|[CComControlBase::GetAmbientMessageReflect](#getambientmessagereflect)|检索 DISPID_AMBIENT_MESSAGEREFLECT，一个标志，指示容器是否想要接收窗口消息 （例如 WM_DRAWITEM) 作为事件。|
|[CComControlBase::GetAmbientPalette](#getambientpalette)|检索 DISPID_AMBIENT_PALETTE，用来访问容器的 HPALETTE。|
|[CComControlBase::GetAmbientProperty](#getambientproperty)|检索指定的容器属性*id*。|
|[CComControlBase::GetAmbientRightToLeft](#getambientrighttoleft)|检索 DISPID_AMBIENT_RIGHTTOLEFT，内容由容器的方向。|
|[CComControlBase::GetAmbientScaleUnits](#getambientscaleunits)|检索 DISPID_AMBIENT_SCALEUNITS 的容器 （如英寸还是按厘米） 的标签显示的环境单位。|
|[CComControlBase::GetAmbientShowGrabHandles](#getambientshowgrabhandles)|检索 DISPID_AMBIENT_SHOWGRABHANDLES，一个标志，指示容器是否允许要为其自身活动时显示握柄的控件。|
|[CComControlBase::GetAmbientShowHatching](#getambientshowhatching)|检索 DISPID_AMBIENT_SHOWHATCHING，一个标志，指示容器是否允许该控件以将它显示用阴影图案 UI 处于活动状态时。|
|[CComControlBase::GetAmbientSupportsMnemonics](#getambientsupportsmnemonics)|检索 DISPID_AMBIENT_SUPPORTSMNEMONICS，一个标志，指示容器是否支持键盘助记键。|
|[CComControlBase::GetAmbientTextAlign](#getambienttextalign)|检索 DISPID_AMBIENT_TEXTALIGN，首选的容器的文本对齐方式： 常规对齐 （左数字右，文本） 为 0、 1 表示左对齐、 居中对齐的 2 和 3 为右对齐。|
|[CComControlBase::GetAmbientTopToBottom](#getambienttoptobottom)|检索 DISPID_AMBIENT_TOPTOBOTTOM，内容由容器的方向。|
|[CComControlBase::GetAmbientUIDead](#getambientuidead)|检索 DISPID_AMBIENT_UIDEAD，一个标志，指示容器是否想要响应用户界面操作的控件。|
|[CComControlBase::GetAmbientUserMode](#getambientusermode)|检索 DISPID_AMBIENT_USERMODE，一个标志，指示容器是否处于运行模式 (TRUE) 或设计模式 (FALSE)。|
|[CComControlBase::GetDirty](#getdirty)|返回的数据成员的值`m_bRequiresSave`。|
|[CComControlBase::GetZoomInfo](#getzoominfo)|检索的 x 和 y 值的分子和分母的缩放系数为激活控件的就地编辑。|
|[CComControlBase::InPlaceActivate](#inplaceactivate)|使控件从非活动状态到任何状态中的谓词转换*iVerb*指示。|
|[CComControlBase::InternalGetSite](#internalgetsite)|调用此方法以指向标识接口的控件站点中查询。|
|[CComControlBase::OnDraw](#ondraw)|重写此方法以绘制控件。|
|[CComControlBase::OnDrawAdvanced](#ondrawadvanced)|默认值`OnDrawAdvanced`准备正常化的设备上下文进行绘图，然后调用您的控件类的`OnDraw`方法。|
|[CComControlBase::OnKillFocus](#onkillfocus)|检查该控件是处于就地活动状态并且具有有效的控件站点，则告知容器控件已丢失焦点。|
|[CComControlBase::OnMouseActivate](#onmouseactivate)|检查 UI 在用户模式下，则将激活的控件。|
|[CComControlBase::OnPaint](#onpaint)|用于绘制准备容器，获取控件的客户端区域，然后调用控件类`OnDraw`方法。|
|[CComControlBase::OnSetFocus](#onsetfocus)|检查该控件是处于就地活动状态并且具有有效的控件站点，则告知容器控件已获得焦点。|
|[CComControlBase::PreTranslateAccelerator](#pretranslateaccelerator)|重写此方法以提供自己的键盘快捷键处理程序。|
|[CComControlBase::SendOnClose](#sendonclose)|通知注册已关闭该控件的通知持有者的所有通知接收器。|
|[CComControlBase::SendOnDataChange](#sendondatachange)|通知控件数据已更改的通知持有者向注册的所有通知接收器。|
|[CComControlBase::SendOnRename](#sendonrename)|通知注册到该控件具有新的名字对象的建议持有者的所有通知接收器。|
|[CComControlBase::SendOnSave](#sendonsave)|通知注册到保存该控件的通知持有者的所有通知接收器。|
|[CComControlBase::SendOnViewChange](#sendonviewchange)|向所有已注册控件的视图已更改的通知接收器通知。|
|[CComControlBase::SetControlFocus](#setcontrolfocus)|设置或删除与该控件的键盘焦点。|
|[CComControlBase::SetDirty](#setdirty)|设置的数据成员`m_bRequiresSave`中的值*bDirty*。|

### <a name="public-data-members"></a>公共数据成员

|名称|描述|
|----------|-----------------|
|[CComControlBase::m_bAutoSize](#m_bautosize)|指示该控件不能为其他任何大小的标志。|
|[CComControlBase::m_bDrawFromNatural](#m_bdrawfromnatural)|标志，指示`IDataObjectImpl::GetData`并`CComControlBase::GetZoomInfo`应设置从控件的大小`m_sizeNatural`而不是从`m_sizeExtent`。|
|[CComControlBase::m_bDrawGetDataInHimetric](#m_bdrawgetdatainhimetric)|标志，指示`IDataObjectImpl::GetData`时应使用 HIMETRIC 单元并不是以像素绘制。|
|[CComControlBase::m_bInPlaceActive](#m_binplaceactive)|指示该控件处于就地活动状态的标记。|
|[CComControlBase::m_bInPlaceSiteEx](#m_binplacesiteex)|指示容器支持的标记`IOleInPlaceSiteEx`接口和 OCX96 控制功能，例如无窗口和闪烁控件。|
|[CComControlBase::m_bNegotiatedWnd](#m_bnegotiatedwnd)|指示控件具有与有关对 OCX96 控件功能 （如闪烁和无窗口控件） 的支持的容器进行协商和控件是开窗或无窗口的标记。|
|[CComControlBase::m_bRecomposeOnResize](#m_brecomposeonresize)|指示的控件希望当容器控件的显示大小更改时重新编写其演示文稿的标记。|
|[CComControlBase::m_bRequiresSave](#m_brequiressave)|指示自上次保存以来已更改控件的标记。|
|[CComControlBase::m_bResizeNatural](#m_bresizenatural)|标志，指示该控件要调整其原始大小 （图像不成比例的物理大小） 时将容器更改控件的显示大小。|
|[CComControlBase::m_bUIActive](#m_buiactive)|标志，指示控件的用户界面，如菜单和工具栏，处于活动状态。|
|[CComControlBase::m_bUsingWindowRgn](#m_busingwindowrgn)|指示控件使用提供容器的窗口区域的标记。|
|[CComControlBase::m_bWasOnceWindowless](#m_bwasoncewindowless)|指示控件已被无窗口，但可能会或可能不是无窗口现在的标记。|
|[CComControlBase::m_bWindowOnly](#m_bwindowonly)|指示该控件应开窗，即使容器支持无窗口控件的标记。|
|[CComControlBase::m_bWndLess](#m_bwndless)|指示无窗口控件的标记。|
|[CComControlBase::m_hWndCD](#m_hwndcd)|包含对与控件关联的窗口句柄的引用。|
|[CComControlBase::m_nFreezeEvents](#m_nfreezeevents)|次数的计数在容器已冻结 （拒绝接受事件） 的事件，而无需干预的解除冻结的事件 （事件接受）。|
|[CComControlBase::m_rcPos](#m_rcpos)|以像素为单位的控件，以容器的坐标表示的位置。|
|[CComControlBase::m_sizeExtent](#m_sizeextent)|以 HIMETRIC 为单位 （每个单位是 0.01 毫米） 的特定显示控件的范围。|
|[CComControlBase::m_sizeNatural](#m_sizenatural)|控件以 HIMETRIC 为单位 （每个单位是 0.01 毫米） 的物理大小。|
|[CComControlBase::m_spAdviseSink](#m_spadvisesink)|指向通知连接在容器上的直接指针 (该容器[IAdviseSink](/windows/desktop/api/objidl/nn-objidl-iadvisesink))。|
|[CComControlBase::m_spAmbientDispatch](#m_spambientdispatch)|一个`CComDispatchDriver`对象，它允许您检索和设置容器的属性通过`IDispatch`指针。|
|[CComControlBase::m_spClientSite](#m_spclientsite)|指向控件的客户端站点容器中的指针。|
|[CComControlBase::m_spDataAdviseHolder](#m_spdataadviseholder)|提供了一种标准方法来保存数据对象之间的通知连接，以及建议接收器。|
|[CComControlBase::m_spInPlaceSite](#m_spinplacesite)|对容器的指针[IOleInPlaceSite](/windows/desktop/api/oleidl/nn-oleidl-ioleinplacesite)， [IOleInPlaceSiteEx](/windows/desktop/api/ocidl/nn-ocidl-ioleinplacesiteex)，或[IOleInPlaceSiteWindowless](/windows/desktop/api/ocidl/nn-ocidl-ioleinplacesitewindowless)接口指针。|
|[CComControlBase::m_spOleAdviseHolder](#m_spoleadviseholder)|提供了一种方法来保存通知连接的标准实现。|

## <a name="remarks"></a>备注

此类提供用于创建和管理 ATL 控件的方法。 [CComControl 类](../../atl/reference/ccomcontrol-class.md)派生自`CComControlBase`。 创建使用 ATL 控件向导的标准控件或 DHTML 控件时，向导将自动派生您的类从`CComControlBase`。

有关创建控件的详细信息，请参阅[ATL 教程](../../atl/active-template-library-atl-tutorial.md)。 ATL 项目向导的详细信息，请参阅文章[创建 ATL 项目](../../atl/reference/creating-an-atl-project.md)。

## <a name="requirements"></a>要求

**标头：** atlctl.h

##  <a name="appearancetype"></a>  CComControlBase::AppearanceType

如果重写你`m_nAppearance`常用属性的类型不是**短**。

```
typedef short AppearanceType;
```

### <a name="remarks"></a>备注

ATL 控件向导添加`m_nAppearance`常见 short 类型的属性。 重写`AppearanceType`如果使用不同的数据类型。

##  <a name="ccomcontrolbase"></a>  CComControlBase::CComControlBase

构造函数。

```
CComControlBase(HWND& h);
```

### <a name="parameters"></a>参数

*h*<br/>
与控件关联的窗口句柄。

### <a name="remarks"></a>备注

初始化到 5080 X 5080 HIMETRIC 为单位的控件大小 ("X 2"2) 和初始化`CComControlBase`数据成员值为 NULL 或 FALSE。

##  <a name="dtor"></a>  CComControlBase:: ~ CComControlBase

析构函数。

```
~CComControlBase();
```

### <a name="remarks"></a>备注

如果控件有窗口，`~CComControlBase`销毁它通过调用[DestroyWindow](/windows/desktop/api/winuser/nf-winuser-destroywindow)。

##  <a name="controlqueryinterface"></a>  CComControlBase::ControlQueryInterface

检索指向所请求的接口的指针。

```
virtual HRESULT ControlQueryInterface(const IID& iid,
    void** ppv);
```

### <a name="parameters"></a>参数

*iid*<br/>
所请求的接口的 GUID。

*ppv*<br/>
通过标识的接口指针的指针*iid*，或如果找不到该接口，则为 NULL。

### <a name="remarks"></a>备注

仅处理 COM 映射表中的接口。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_COM#15](../../atl/codesnippet/cpp/ccomcontrolbase-class_1.cpp)]

##  <a name="doesverbactivate"></a>  CComControlBase::DoesVerbActivate

检查两个*iVerb*使用的参数`IOleObjectImpl::DoVerb`或者激活控件的用户界面 (*iVerb*等于 OLEIVERB_UIACTIVATE)，定义当用户双击所执行的操作控件 (*iVerb*等于 OLEIVERB_PRIMARY)，显示控件 (*iVerb*等于 OLEIVERB_SHOW)，或激活的控件 (*iVerb*等于 OLEIVERB_INPLACEACTIVATE)。

```
BOOL DoesVerbActivate(LONG iVerb);
```

### <a name="parameters"></a>参数

*iVerb*<br/>
值，该值指示要由执行的操作`DoVerb`。

### <a name="return-value"></a>返回值

返回 true; 否则*iVerb*等于 OLEIVERB_UIACTIVATE、 OLEIVERB_PRIMARY、 OLEIVERB_SHOW 或 OLEIVERB_INPLACEACTIVATE; 否则，返回 FALSE。

### <a name="remarks"></a>备注

您可以重写此方法以定义你自己激活谓词。

##  <a name="doesverbuiactivate"></a>  CComControlBase::DoesVerbUIActivate

检查两个*iVerb*使用的参数`IOleObjectImpl::DoVerb`会导致控件的用户界面激活，则返回 TRUE。

```
BOOL DoesVerbUIActivate(LONG iVerb);
```

### <a name="parameters"></a>参数

*iVerb*<br/>
值，该值指示要由执行的操作`DoVerb`。

### <a name="return-value"></a>返回值

返回 true; 否则*iVerb*等于 OLEIVERB_UIACTIVATE、 OLEIVERB_PRIMARY、 OLEIVERB_SHOW 或 OLEIVERB_INPLACEACTIVATE。 否则，该方法返回 FALSE。

##  <a name="doverbproperties"></a>  CComControlBase::DoVerbProperties

显示控件的属性页。

```
HRESULT DoVerbProperties(LPCRECT /* prcPosRect */, HWND hwndParent);
```

### <a name="parameters"></a>参数

*prcPosRec*<br/>
保留。

*hwndParent*<br/>
包含控件的窗口的句柄。

### <a name="return-value"></a>返回值

一个标准的 HRESULT 值。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_COM#19](../../atl/codesnippet/cpp/ccomcontrolbase-class_2.cpp)]

[!code-cpp[NVC_ATL_COM#20](../../atl/codesnippet/cpp/ccomcontrolbase-class_3.h)]

##  <a name="fireviewchange"></a>  CComControlBase::FireViewChange

调用此方法以通知容器重绘该控件，或通知控件的视图已更改的已注册的通知接收器。

```
HRESULT FireViewChange();
```

### <a name="return-value"></a>返回值

一个标准的 HRESULT 值。

### <a name="remarks"></a>备注

如果控件处于活动状态 (控件类数据成员[CComControlBase::m_bInPlaceActive](#m_binplaceactive)为 TRUE)，通知你想要重新绘制整个控件的容器。 如果控件处于非活动状态，将通知控件的已注册通知接收器 (通过控件类数据成员[CComControlBase::m_spAdviseSink](#m_spadvisesink)) 控件的视图已更改。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_COM#21](../../atl/codesnippet/cpp/ccomcontrolbase-class_4.cpp)]

##  <a name="getambientappearance"></a>  CComControlBase::GetAmbientAppearance

检索 DISPID_AMBIENT_APPEARANCE，设置控件的当前外观： 0 表示平面，1 表示 3D。

```
HRESULT GetAmbientAppearance(short& nAppearance);
```

### <a name="parameters"></a>参数

*nAppearance*<br/>
DISPID_AMBIENT_APPEARANCE 属性。

### <a name="return-value"></a>返回值

一个标准的 HRESULT 值。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_COM#22](../../atl/codesnippet/cpp/ccomcontrolbase-class_5.h)]

##  <a name="getambientautoclip"></a>  CComControlBase::GetAmbientAutoClip

检索 DISPID_AMBIENT_AUTOCLIP，一个标志，指示容器是否支持自动的控件显示区域的剪辑。

```
HRESULT GetAmbientAutoClip(BOOL& bAutoClip);
```

### <a name="parameters"></a>参数

*bAutoClip*<br/>
DISPID_AMBIENT_AUTOCLIP 属性。

### <a name="return-value"></a>返回值

一个标准的 HRESULT 值。

##  <a name="getambientbackcolor"></a>  CComControlBase::GetAmbientBackColor

检索 DISPID_AMBIENT_BACKCOLOR，由容器定义的所有控件的环境背景色。

```
HRESULT GetAmbientBackColor(OLE_COLOR& BackColor);
```

### <a name="parameters"></a>参数

*背景色*<br/>
DISPID_AMBIENT_BACKCOLOR 属性。

### <a name="return-value"></a>返回值

一个标准的 HRESULT 值。

##  <a name="getambientcharset"></a>  CComControlBase::GetAmbientCharSet

检索 DISPID_AMBIENT_CHARSET，对于所有控件，由容器定义的环境的字符集。

```
HRESULT GetAmbientCharSet(BSTR& bstrCharSet);
```

### <a name="parameters"></a>参数

*bstrCharSet*<br/>
DISPID_AMBIENT_CHARSET 属性。

### <a name="return-value"></a>返回值

返回成功，则为 S_OK 或失败时的错误 HRESULT。

##  <a name="getambientcodepage"></a>  CComControlBase::GetAmbientCodePage

检索 DISPID_AMBIENT_CODEPAGE，由容器定义的所有控件的环境的代码页。

```
HRESULT GetAmbientCodePage(ULONG& ulCodePage);
```

### <a name="parameters"></a>参数

*ulCodePage*<br/>
DISPID_AMBIENT_CODEPAGE 属性。

### <a name="return-value"></a>返回值

返回成功，则为 S_OK 或失败时的错误 HRESULT。

##  <a name="getambientdisplayasdefault"></a>  CComControlBase::GetAmbientDisplayAsDefault

检索 DISPID_AMBIENT_DISPLAYASDEFAULT，如果容器已标记为默认按钮，此站点中的控件和因此按钮控件应绘制本身使用较粗的框架，则为 TRUE 的标志。

```
HRESULT GetAmbientDisplayAsDefault(BOOL& bDisplayAsDefault);
```

### <a name="parameters"></a>参数

*bDisplayAsDefault*<br/>
DISPID_AMBIENT_DISPLAYASDEFAULT 属性。

### <a name="return-value"></a>返回值

一个标准的 HRESULT 值。

##  <a name="getambientdisplayname"></a>  CComControlBase::GetAmbientDisplayName

检索 DISPID_AMBIENT_DISPLAYNAME，容器具有提供给控件的名称。

```
HRESULT GetAmbientDisplayName(BSTR& bstrDisplayName);
```

### <a name="parameters"></a>参数

*bstrDisplayName*<br/>
DISPID_AMBIENT_DISPLAYNAME 属性。

### <a name="return-value"></a>返回值

一个标准的 HRESULT 值。

##  <a name="getambientfont"></a>  CComControlBase::GetAmbientFont

检索指向容器的环境`IFont`接口。

```
HRESULT GetAmbientFont(IFont** ppFont);
```

### <a name="parameters"></a>参数

*ppFont*<br/>
指向容器的环境[IFont](/windows/desktop/api/ocidl/nn-ocidl-ifont)接口。

### <a name="return-value"></a>返回值

一个标准的 HRESULT 值。

### <a name="remarks"></a>备注

如果该属性为 NULL，则指针为 NULL。 如果不为 NULL 指针，调用方必须释放指针。

##  <a name="getambientfontdisp"></a>  CComControlBase::GetAmbientFontDisp

检索指向容器的环境`IFontDisp`调度接口。

```
HRESULT GetAmbientFontDisp(IFontDisp** ppFont);
```

### <a name="parameters"></a>参数

*ppFont*<br/>
指向容器的环境[IFontDisp](https://msdn.microsoft.com/library/windows/desktop/ms692695)调度接口。

### <a name="return-value"></a>返回值

返回成功，则为 S_OK 或失败时的错误 HRESULT。

### <a name="remarks"></a>备注

如果该属性为 NULL，则指针为 NULL。 如果不为 NULL 指针，调用方必须释放指针。

##  <a name="getambientforecolor"></a>  CComControlBase::GetAmbientForeColor

检索 DISPID_AMBIENT_FORECOLOR，由容器定义的所有控件的环境前景色。

```
HRESULT GetAmbientForeColor(OLE_COLOR& ForeColor);
```

### <a name="parameters"></a>参数

*前景色*<br/>
DISPID_AMBIENT_FORECOLOR 属性。

### <a name="return-value"></a>返回值

一个标准的 HRESULT 值。

##  <a name="getambientlocaleid"></a>  CComControlBase::GetAmbientLocaleID

检索 DISPID_AMBIENT_LOCALEID，容器使用的语言的标识符。

```
HRESULT GetAmbientLocaleID(LCID& lcid);
```

### <a name="parameters"></a>参数

*lcid*<br/>
DISPID_AMBIENT_LOCALEID 属性。

### <a name="return-value"></a>返回值

一个标准的 HRESULT 值。

### <a name="remarks"></a>备注

该控件可以使用此标识符以适应不同语言到其用户界面。

##  <a name="getambientmessagereflect"></a>  CComControlBase::GetAmbientMessageReflect

检索 DISPID_AMBIENT_MESSAGEREFLECT，一个标志，指示容器是否想要接收窗口消息 (如`WM_DRAWITEM`) 作为事件。

```
HRESULT GetAmbientMessageReflect(BOOL& bMessageReflect);
```

### <a name="parameters"></a>参数

*bMessageReflect*<br/>
DISPID_AMBIENT_MESSAGEREFLECT 属性。

### <a name="return-value"></a>返回值

一个标准的 HRESULT 值。

##  <a name="getambientpalette"></a>  CComControlBase::GetAmbientPalette

检索 DISPID_AMBIENT_PALETTE，用来访问容器的 HPALETTE。

```
HRESULT GetAmbientPalette(HPALETTE& hPalette);
```

### <a name="parameters"></a>参数

*hPalette*<br/>
DISPID_AMBIENT_PALETTE 属性。

### <a name="return-value"></a>返回值

一个标准的 HRESULT 值。

##  <a name="getambientproperty"></a>  CComControlBase::GetAmbientProperty

检索指定的容器属性*dispid*。

```
HRESULT GetAmbientProperty(DISPID dispid, VARIANT& var);
```

### <a name="parameters"></a>参数

*dispid*<br/>
要检索的容器属性的标识符。

*var*<br/>
若要接收属性的变量。

### <a name="return-value"></a>返回值

一个标准的 HRESULT 值。

### <a name="remarks"></a>备注

ATL 提供了一组帮助程序函数来检索特定属性，例如， [CComControlBase::GetAmbientBackColor](#getambientbackcolor)。 如果不没有可用的任何合适的方法，则使用`GetAmbientProperty`。

##  <a name="getambientrighttoleft"></a>  CComControlBase::GetAmbientRightToLeft

检索 DISPID_AMBIENT_RIGHTTOLEFT，内容由容器的方向。

```
HRESULT GetAmbientRightToLeft(BOOL& bRightToLeft);
```

### <a name="parameters"></a>参数

*bRightToLeft*<br/>
DISPID_AMBIENT_RIGHTTOLEFT 属性。 如果内容从右到左显示，则设置为 TRUE，否则，为 FALSE 到右显示左侧。

### <a name="return-value"></a>返回值

返回成功，则为 S_OK 或失败时的错误 HRESULT。

##  <a name="getambientscaleunits"></a>  CComControlBase::GetAmbientScaleUnits

检索 DISPID_AMBIENT_SCALEUNITS 的容器 （如英寸还是按厘米） 的标签显示的环境单位。

```
HRESULT GetAmbientScaleUnits(BSTR& bstrScaleUnits);
```

### <a name="parameters"></a>参数

*bstrScaleUnits*<br/>
DISPID_AMBIENT_SCALEUNITS 属性。

### <a name="return-value"></a>返回值

一个标准的 HRESULT 值。

##  <a name="getambientshowgrabhandles"></a>  CComControlBase::GetAmbientShowGrabHandles

检索 DISPID_AMBIENT_SHOWGRABHANDLES，一个标志，指示容器是否允许要为其自身活动时显示握柄的控件。

```
HRESULT GetAmbientShowGrabHandles(BOOL& bShowGrabHandles);
```

### <a name="parameters"></a>参数

*bShowGrabHandles*<br/>
DISPID_AMBIENT_SHOWGRABHANDLES 属性。

### <a name="return-value"></a>返回值

一个标准的 HRESULT 值。

##  <a name="getambientshowhatching"></a>  CComControlBase::GetAmbientShowHatching

检索 DISPID_AMBIENT_SHOWHATCHING，一个标志，指示容器是否允许以将它显示用阴影图案时处于活动状态的控件的用户界面的控件。

```
HRESULT GetAmbientShowHatching(BOOL& bShowHatching);
```

### <a name="parameters"></a>参数

*bShowHatching*<br/>
DISPID_AMBIENT_SHOWHATCHING 属性。

### <a name="return-value"></a>返回值

一个标准的 HRESULT 值。

##  <a name="getambientsupportsmnemonics"></a>  CComControlBase::GetAmbientSupportsMnemonics

检索 DISPID_AMBIENT_SUPPORTSMNEMONICS，一个标志，指示容器是否支持键盘助记键。

```
HRESULT GetAmbientSupportsMnemonics(BOOL& bSupportsMnemonics);
```

### <a name="parameters"></a>参数

*bSupportsMnemonics*<br/>
DISPID_AMBIENT_SUPPORTSMNEMONICS 属性。

### <a name="return-value"></a>返回值

一个标准的 HRESULT 值。

##  <a name="getambienttextalign"></a>  CComControlBase::GetAmbientTextAlign

检索 DISPID_AMBIENT_TEXTALIGN，首选的容器的文本对齐方式： 常规对齐 （左数字右，文本） 为 0、 1 表示左对齐、 居中对齐的 2 和 3 为右对齐。

```
HRESULT GetAmbientTextAlign(short& nTextAlign);
```

### <a name="parameters"></a>参数

*nTextAlign*<br/>
DISPID_AMBIENT_TEXTALIGN 属性。

### <a name="return-value"></a>返回值

一个标准的 HRESULT 值。

##  <a name="getambienttoptobottom"></a>  CComControlBase::GetAmbientTopToBottom

检索 DISPID_AMBIENT_TOPTOBOTTOM，内容由容器的方向。

```
HRESULT GetAmbientTopToBottom(BOOL& bTopToBottom);
```

### <a name="parameters"></a>参数

*bTopToBottom*<br/>
DISPID_AMBIENT_TOPTOBOTTOM 属性。 设置为 TRUE，如果显示的文本从上到下，否则，为 FALSE 显示底部到顶部。

### <a name="return-value"></a>返回值

返回成功，则为 S_OK 或失败时的错误 HRESULT。

##  <a name="getambientuidead"></a>  CComControlBase::GetAmbientUIDead

检索 DISPID_AMBIENT_UIDEAD，一个标志，指示容器是否想要响应用户界面操作的控件。

```
HRESULT GetAmbientUIDead(BOOL& bUIDead);
```

### <a name="parameters"></a>参数

*bUIDead*<br/>
DISPID_AMBIENT_UIDEAD 属性。

### <a name="return-value"></a>返回值

一个标准的 HRESULT 值。

### <a name="remarks"></a>备注

如果为 TRUE，控件不应作出响应。 此标志适用而不考虑 DISPID_AMBIENT_USERMODE 标志。 请参阅[CComControlBase::GetAmbientUserMode](#getambientusermode)。

##  <a name="getambientusermode"></a>  CComControlBase::GetAmbientUserMode

检索 DISPID_AMBIENT_USERMODE，一个标志，指示容器是否处于运行模式 (TRUE) 或设计模式 (FALSE)。

```
HRESULT GetAmbientUserMode(BOOL& bUserMode);
```

### <a name="parameters"></a>参数

*bUserMode*<br/>
DISPID_AMBIENT_USERMODE 属性。

### <a name="return-value"></a>返回值

一个标准的 HRESULT 值。

##  <a name="getdirty"></a>  CComControlBase::GetDirty

返回的数据成员的值`m_bRequiresSave`。

```
BOOL GetDirty();
```

### <a name="return-value"></a>返回值

返回的数据成员的值[m_bRequiresSave](#m_brequiressave)。

### <a name="remarks"></a>备注

此值设置为使用[CComControlBase::SetDirty](#setdirty)。

##  <a name="getzoominfo"></a>  CComControlBase::GetZoomInfo

检索的 x 和 y 值的分子和分母的缩放系数为激活控件的就地编辑。

```
void GetZoomInfo(ATL_DRAWINFO& di);
```

### <a name="parameters"></a>参数

*di*<br/>
结构，它将保存缩放系数分子和分母。 有关详细信息，请参阅[ATL_DRAWINFO](../../atl/reference/atl-drawinfo-structure.md)。

### <a name="remarks"></a>备注

缩放系数为其当前范围内的控件的自然大小的比例。

##  <a name="inplaceactivate"></a>  CComControlBase::InPlaceActivate

使控件从非活动状态到任何状态中的谓词转换*iVerb*指示。

```
HRESULT InPlaceActivate(LONG iVerb, const RECT* prcPosRect = NULL);
```

### <a name="parameters"></a>参数

*iVerb*<br/>
值，该值指示要由执行的操作[IOleObjectImpl::DoVerb](../../atl/reference/ioleobjectimpl-class.md#doverb)。

*prcPosRect*<br/>
指针，指向就地控件的位置。

### <a name="return-value"></a>返回值

一个标准的 HRESULT 值。

### <a name="remarks"></a>备注

之前激活，此方法检查该控件具有客户端站点，检查可见，控件，获取控件的父窗口中的位置。 激活控件后，此方法激活控件的用户界面，并告知容器使控件可见。

此方法还会检索`IOleInPlaceSite`， `IOleInPlaceSiteEx`，或`IOleInPlaceSiteWindowless`控件的接口指针并将其存储在控件类数据成员[CComControlBase::m_spInPlaceSite](#m_spinplacesite)。 控件类数据成员[CComControlBase::m_bInPlaceSiteEx](#m_binplacesiteex)， [CComControlBase::m_bWndLess](#m_bwndless)， [CComControlBase::m_bWasOnceWindowless](#m_bwasoncewindowless)，并且[CComControlBase::m_bNegotiatedWnd](#m_bnegotiatedwnd)设置为 true，根据需要。

##  <a name="internalgetsite"></a>  CComControlBase::InternalGetSite

调用此方法以指向标识接口的控件站点中查询。

```
HRESULT InternalGetSite(REFIID riid, void** ppUnkSite);
```

### <a name="parameters"></a>参数

*riid*<br/>
应在返回的接口指针的 IID *ppUnkSite*。

*ppUnkSite*<br/>
接收请求中的接口指针的指针变量的地址*riid*。

### <a name="return-value"></a>返回值

返回成功，则为 S_OK 或失败时的错误 HRESULT。

### <a name="remarks"></a>备注

如果站点支持在所请求的接口*riid*，通过返回的指针*ppUnkSite*。 否则为*ppUnkSite*设置为 NULL。

##  <a name="m_bautosize"></a>  CComControlBase::m_bAutoSize

指示该控件不能为其他任何大小的标志。

```
unsigned m_bAutoSize:1;
```

### <a name="remarks"></a>备注

通过检查此标志`IOleObjectImpl::SetExtent`和，如果为 TRUE，将导致函数返回 E_FAIL。

> [!NOTE]
>  若要使用此数据成员在你的控件类内，你必须将其声明为数据成员控件类中。 基类中联合中声明，因此，你的控件类不将从基类继承此数据成员。

如果您将添加**自动调整大小**选项卡上[常用属性](../../atl/reference/stock-properties-atl-control-wizard.md)ATL 控件向导，该向导的选项卡自动在你的控件类中创建此数据成员、 创建 put 和 get 方法的属性并支持[IPropertyNotifySink](/windows/desktop/api/ocidl/nn-ocidl-ipropertynotifysink)属性发生更改时自动通知容器。

##  <a name="m_bdrawfromnatural"></a>  CComControlBase::m_bDrawFromNatural

标志，指示`IDataObjectImpl::GetData`并`CComControlBase::GetZoomInfo`应设置从控件的大小`m_sizeNatural`而不是从`m_sizeExtent`。

```
unsigned m_bDrawFromNatural:1;
```

### <a name="remarks"></a>备注

> [!NOTE]
>  若要使用此数据成员在你的控件类内，你必须将其声明为数据成员控件类中。 基类中联合中声明，因此，你的控件类不将从基类继承此数据成员。

##  <a name="m_bdrawgetdatainhimetric"></a>  CComControlBase::m_bDrawGetDataInHimetric

标志，指示`IDataObjectImpl::GetData`时应使用 HIMETRIC 单元并不是以像素绘制。

```
unsigned m_bDrawGetDataInHimetric:1;
```

### <a name="remarks"></a>备注

每个逻辑的 HIMETRIC 单位是 0.01 毫米。

> [!NOTE]
>  若要使用此数据成员在你的控件类内，你必须将其声明为数据成员控件类中。 基类中联合中声明，因此，你的控件类不将从基类继承此数据成员。

##  <a name="m_binplaceactive"></a>  CComControlBase::m_bInPlaceActive

指示该控件处于就地活动状态的标记。

```
unsigned m_bInPlaceActive:1;
```

### <a name="remarks"></a>备注

这意味着控件可见和其窗口，如果有，可见，但其菜单和工具栏可能不处于活动状态。 `m_bUIActive`标志指示控件的用户界面，如菜单、 还处于活动状态。

> [!NOTE]
>  若要使用此数据成员在你的控件类内，你必须将其声明为数据成员控件类中。 基类中联合中声明，因此，你的控件类不将从基类继承此数据成员。

##  <a name="m_binplacesiteex"></a>  CComControlBase::m_bInPlaceSiteEx

指示容器支持的标记`IOleInPlaceSiteEx`接口和 OCX96 控制功能，例如无窗口和闪烁控件。

```
unsigned m_bInPlaceSiteEx:1;
```

### <a name="remarks"></a>备注

> [!NOTE]
>  若要使用此数据成员在你的控件类内，你必须将其声明为数据成员控件类中。 基类中联合中声明，因此，你的控件类不将从基类继承此数据成员。

数据成员`m_spInPlaceSite`指向[IOleInPlaceSite](/windows/desktop/api/oleidl/nn-oleidl-ioleinplacesite)， [IOleInPlaceSiteEx](/windows/desktop/api/ocidl/nn-ocidl-ioleinplacesiteex)，或[IOleInPlaceSiteWindowless](/windows/desktop/api/ocidl/nn-ocidl-ioleinplacesitewindowless)接口，具体取决于值`m_bWndLess`和`m_bInPlaceSiteEx`标志。 (数据成员`m_bNegotiatedWnd`必须为 TRUE 的`m_spInPlaceSite`指针有效。)

如果`m_bWndLess`为 FALSE 并`m_bInPlaceSiteEx`为 TRUE，`m_spInPlaceSite`是`IOleInPlaceSiteEx`接口指针。 请参阅[m_spInPlaceSite](#m_spinplacesite)显示以下三个数据成员之间的关系的表。

##  <a name="m_bnegotiatedwnd"></a>  CComControlBase::m_bNegotiatedWnd

指示控件具有与有关对 OCX96 控件功能 （如闪烁和无窗口控件） 的支持的容器进行协商和控件是开窗或无窗口的标记。

```
unsigned m_bNegotiatedWnd:1;
```

### <a name="remarks"></a>备注

> [!NOTE]
>  若要使用此数据成员在你的控件类内，你必须将其声明为数据成员控件类中。 基类中联合中声明，因此，你的控件类不将从基类继承此数据成员。

`m_bNegotiatedWnd`标志必须为 TRUE 的`m_spInPlaceSite`指针有效。

##  <a name="m_brecomposeonresize"></a>  CComControlBase::m_bRecomposeOnResize

指示的控件希望当容器控件的显示大小更改时重新编写其演示文稿的标记。

```
unsigned m_bRecomposeOnResize:1;
```

### <a name="remarks"></a>备注

> [!NOTE]
>  若要使用此数据成员在你的控件类内，你必须将其声明为数据成员控件类中。 基类中联合中声明，因此，你的控件类不将从基类继承此数据成员。

通过检查此标志[IOleObjectImpl::SetExtent](../../atl/reference/ioleobjectimpl-class.md#setextent)和，如果为 TRUE，`SetExtent`通知查看更改的容器。 如果设置此标志，OLEMISC_RECOMPOSEONRESIZE 位[OLEMISC](/windows/desktop/api/oleidl/ne-oleidl-tagolemisc)枚举还应设置。

##  <a name="m_brequiressave"></a>  CComControlBase::m_bRequiresSave

指示自上次保存以来已更改控件的标记。

```
unsigned m_bRequiresSave:1;
```

### <a name="remarks"></a>备注

值`m_bRequiresSave`可以用来设置[CComControlBase::SetDirty](#setdirty)并使用检索到[CComControlBase::GetDirty](#getdirty)。

> [!NOTE]
>  若要使用此数据成员在你的控件类内，你必须将其声明为数据成员控件类中。 基类中联合中声明，因此，你的控件类不将从基类继承此数据成员。

##  <a name="m_bresizenatural"></a>  CComControlBase::m_bResizeNatural

标志，指示该控件要调整其原始大小 （图像不成比例的物理大小） 时将容器更改控件的显示大小。

```
unsigned m_bResizeNatural:1;
```

### <a name="remarks"></a>备注

通过检查此标志`IOleObjectImpl::SetExtent`而且，如果为 TRUE，到传递的大小`SetExtent`分配给`m_sizeNatural`。

大小传入`SetExtent`始终分配给`m_sizeExtent`，而不考虑的值的`m_bResizeNatural`。

> [!NOTE]
>  若要使用此数据成员在你的控件类内，你必须将其声明为数据成员控件类中。 基类中联合中声明，因此，你的控件类不将从基类继承此数据成员。

##  <a name="m_buiactive"></a>  CComControlBase::m_bUIActive

标志，指示控件的用户界面，如菜单和工具栏，处于活动状态。

```
unsigned m_bUIActive:1;
```

### <a name="remarks"></a>备注

`m_bInPlaceActive`标志指示该控件处于活动状态，但不是其用户界面处于活动状态。

> [!NOTE]
>  若要使用此数据成员在你的控件类内，你必须将其声明为数据成员控件类中。 基类中联合中声明，因此，你的控件类不将从基类继承此数据成员。

##  <a name="m_busingwindowrgn"></a>  CComControlBase::m_bUsingWindowRgn

指示控件使用提供容器的窗口区域的标记。

```
unsigned m_bUsingWindowRgn:1;
```

### <a name="remarks"></a>备注

> [!NOTE]
>  若要使用此数据成员在你的控件类内，你必须将其声明为数据成员控件类中。 基类中联合中声明，因此，你的控件类不将从基类继承此数据成员。

##  <a name="m_bwasoncewindowless"></a>  CComControlBase::m_bWasOnceWindowless

指示控件已被无窗口，但可能会或可能不是无窗口现在的标记。

```
unsigned m_bWasOnceWindowless:1;
```

### <a name="remarks"></a>备注

> [!NOTE]
>  若要使用此数据成员在你的控件类内，你必须将其声明为数据成员控件类中。 基类中联合中声明，因此，你的控件类不将从基类继承此数据成员。

##  <a name="m_bwindowonly"></a>  CComControlBase::m_bWindowOnly

指示该控件应开窗，即使容器支持无窗口控件的标记。

```
unsigned m_bWindowOnly:1;
```

### <a name="remarks"></a>备注

> [!NOTE]
>  若要使用此数据成员在你的控件类内，你必须将其声明为数据成员控件类中。 基类中联合中声明，因此，你的控件类不将从基类继承此数据成员。

##  <a name="m_bwndless"></a>  CComControlBase::m_bWndLess

指示无窗口控件的标记。

```
unsigned m_bWndLess:1;
```

### <a name="remarks"></a>备注

> [!NOTE]
>  若要使用此数据成员在你的控件类内，你必须将其声明为数据成员控件类中。 基类中联合中声明，因此，你的控件类不将从基类继承此数据成员。

数据成员`m_spInPlaceSite`指向[IOleInPlaceSite](/windows/desktop/api/oleidl/nn-oleidl-ioleinplacesite)， [IOleInPlaceSiteEx](/windows/desktop/api/ocidl/nn-ocidl-ioleinplacesiteex)，或[IOleInPlaceSiteWindowless](/windows/desktop/api/ocidl/nn-ocidl-ioleinplacesitewindowless)接口，具体取决于值`m_bWndLess`并[CComControlBase::m_bInPlaceSiteEx](#m_binplacesiteex)标志。 (数据成员[CComControlBase::m_bNegotiatedWnd](#m_bnegotiatedwnd)必须为 TRUE 的[CComControlBase::m_spInPlaceSite](#m_spinplacesite)指针有效。)

如果`m_bWndLess`为 TRUE 时，`m_spInPlaceSite`是`IOleInPlaceSiteWindowless`接口指针。 请参阅[CComControlBase::m_spInPlaceSite](#m_spinplacesite)显示这些数据成员之间的完成关系表。

##  <a name="m_hwndcd"></a>  CComControlBase::m_hWndCD

包含对与控件关联的窗口句柄的引用。

```
HWND& m_hWndCD;
```

### <a name="remarks"></a>备注

> [!NOTE]
>  若要使用此数据成员在你的控件类内，你必须将其声明为数据成员控件类中。 基类中联合中声明，因此，你的控件类不将从基类继承此数据成员。

##  <a name="m_nfreezeevents"></a>  CComControlBase::m_nFreezeEvents

次数的计数在容器已冻结 （拒绝接受事件） 的事件，而无需干预的解除冻结的事件 （事件接受）。

```
short m_nFreezeEvents;
```

### <a name="remarks"></a>备注

> [!NOTE]
>  若要使用此数据成员在你的控件类内，你必须将其声明为数据成员控件类中。 基类中联合中声明，因此，你的控件类不将从基类继承此数据成员。

##  <a name="m_rcpos"></a>  CComControlBase::m_rcPos

以像素为单位的控件，以容器的坐标表示的位置。

```
RECT m_rcPos;
```

### <a name="remarks"></a>备注

> [!NOTE]
>  若要使用此数据成员在你的控件类内，你必须将其声明为数据成员控件类中。 基类中联合中声明，因此，你的控件类不将从基类继承此数据成员。

##  <a name="m_sizeextent"></a>  CComControlBase::m_sizeExtent

以 HIMETRIC 为单位 （每个单位是 0.01 毫米） 的特定显示控件的范围。

```
SIZE m_sizeExtent;
```

### <a name="remarks"></a>备注

> [!NOTE]
>  若要使用此数据成员在你的控件类内，你必须将其声明为数据成员控件类中。 基类中联合中声明，因此，你的控件类不将从基类继承此数据成员。

此大小缩放的显示。 在中指定控件的物理大小`m_sizeNatural`数据成员并且固定不变。

可以将大小转换为全局函数的像素[AtlHiMetricToPixel](pixel-himetric-conversion-global-functions.md#atlhimetrictopixel)。

##  <a name="m_sizenatural"></a>  CComControlBase::m_sizeNatural

控件以 HIMETRIC 为单位 （每个单位是 0.01 毫米） 的物理大小。

```
SIZE m_sizeNatural;
```

### <a name="remarks"></a>备注

> [!NOTE]
>  若要使用此数据成员在你的控件类内，你必须将其声明为数据成员控件类中。 基类中联合中声明，因此，你的控件类不将从基类继承此数据成员。

此大小固定的同时在大小`m_sizeExtent`显示缩放。

可以将大小转换为全局函数的像素[AtlHiMetricToPixel](pixel-himetric-conversion-global-functions.md#atlhimetrictopixel)。

##  <a name="m_spadvisesink"></a>  CComControlBase::m_spAdviseSink

指向通知连接在容器上的直接指针 (该容器[IAdviseSink](/windows/desktop/api/objidl/nn-objidl-iadvisesink))。

```
CComPtr<IAdviseSink>
    m_spAdviseSink;
```

### <a name="remarks"></a>备注

> [!NOTE]
>  若要使用此数据成员在你的控件类内，你必须将其声明为数据成员控件类中。 基类中联合中声明，因此，你的控件类不将从基类继承此数据成员。

##  <a name="m_spambientdispatch"></a>  CComControlBase::m_spAmbientDispatch

一个`CComDispatchDriver`对象，它允许您检索和设置对象的属性通过`IDispatch`指针。

```
CComDispatchDriver m_spAmbientDispatch;
```

### <a name="remarks"></a>备注

> [!NOTE]
>  若要使用此数据成员在你的控件类内，你必须将其声明为数据成员控件类中。 基类中联合中声明，因此，你的控件类不将从基类继承此数据成员。

##  <a name="m_spclientsite"></a>  CComControlBase::m_spClientSite

指向控件的客户端站点容器中的指针。

```
CComPtr<IOleClientSite>
    m_spClientSite;
```

### <a name="remarks"></a>备注

> [!NOTE]
>  若要使用此数据成员在你的控件类内，你必须将其声明为数据成员控件类中。 基类中联合中声明，因此，你的控件类不将从基类继承此数据成员。

##  <a name="m_spdataadviseholder"></a>  CComControlBase::m_spDataAdviseHolder

提供了一种标准方法来保存数据对象之间的通知连接，以及建议接收器。

```
CComPtr<IDataAdviseHolder>
    m_spDataAdviseHolder;
```

### <a name="remarks"></a>备注

> [!NOTE]
>  若要使用此数据成员在你的控件类内，你必须将其声明为数据成员控件类中。 基类中联合中声明，因此，你的控件类不将从基类继承此数据成员。

数据对象是一个控件，可将数据传输，并实现[IDataObject](/windows/desktop/api/objidl/nn-objidl-idataobject)，其方法指定的数据格式和传输媒体。

接口`m_spDataAdviseHolder`实现[IDataObject::DAdvise](/windows/desktop/api/objidl/nf-objidl-idataobject-dadvise)并[IDataObject::DUnadvise](/windows/desktop/api/objidl/nf-objidl-idataobject-dunadvise)建立和删除通知连接到容器的方法。 控件的容器必须通过支持实现建议接收器[IAdviseSink](/windows/desktop/api/objidl/nn-objidl-iadvisesink)接口。

##  <a name="m_spinplacesite"></a>  CComControlBase::m_spInPlaceSite

对容器的指针[IOleInPlaceSite](/windows/desktop/api/oleidl/nn-oleidl-ioleinplacesite)， [IOleInPlaceSiteEx](/windows/desktop/api/ocidl/nn-ocidl-ioleinplacesiteex)，或[IOleInPlaceSiteWindowless](/windows/desktop/api/ocidl/nn-ocidl-ioleinplacesitewindowless)接口指针。

```
CComPtr<IOleInPlaceSiteWindowless>
    m_spInPlaceSite;
```

### <a name="remarks"></a>备注

> [!NOTE]
>  若要使用此数据成员在你的控件类内，你必须将其声明为数据成员控件类中。 基类中联合中声明，因此，你的控件类不将从基类继承此数据成员。

`m_spInPlaceSite`指针无效，仅当[m_bNegotiatedWnd](#m_bnegotiatedwnd)标志为 TRUE。

下表显示如何`m_spInPlaceSite`取决于指针类型[m_bWndLess](#m_bwndless)并[m_bInPlaceSiteEx](#m_binplacesiteex)数据成员标志：

|m_spInPlaceSite 类型|m_bWndLess 值|m_bInPlaceSiteEx 值|
|---------------------------|-----------------------|-----------------------------|
|`IOleInPlaceSiteWindowless`|true|TRUE 或 FALSE|
|`IOleInPlaceSiteEx`|false|true|
|`IOleInPlaceSite`|false|false|

##  <a name="m_spoleadviseholder"></a>  CComControlBase::m_spOleAdviseHolder

提供了一种方法来保存通知连接的标准实现。

```
CComPtr<IOleAdviseHolder>
    m_spOleAdviseHolder;
```

### <a name="remarks"></a>备注

> [!NOTE]
>  若要使用此数据成员在你的控件类内，你必须将其声明为数据成员控件类中。 基类中联合中声明，因此，你的控件类不将从基类继承此数据成员。

接口`m_spOleAdviseHolder`实现[IOleObject::Advise](/windows/desktop/api/oleidl/nf-oleidl-ioleobject-advise)并[IOleObject::Unadvise](/windows/desktop/api/oleidl/nf-oleidl-ioleobject-unadvise)建立和删除通知连接到容器的方法。 控件的容器必须通过支持实现建议接收器[IAdviseSink](/windows/desktop/api/objidl/nn-objidl-iadvisesink)接口。

##  <a name="ondraw"></a>  CComControlBase::OnDraw

重写此方法以绘制控件。

```
virtual HRESULT OnDraw(ATL_DRAWINFO& di);
```

### <a name="parameters"></a>参数

*di*<br/>
对引用[ATL_DRAWINFO](../../atl/reference/atl-drawinfo-structure.md)结构，其中包含如绘图方面，控件边界的绘图信息和绘图优化与否。

### <a name="return-value"></a>返回值

标准的 HRESULT 值。

### <a name="remarks"></a>备注

默认值`OnDraw`删除或还原的设备上下文或不执行任何操作，具体取决于中设置标志[CComControlBase::OnDrawAdvanced](#ondrawadvanced)。

`OnDraw`方法自动添加到你的控件类，当使用 ATL 控件向导创建您的控件。 向导的默认`OnDraw`用"ATL 8.0"的标签绘制矩形。

### <a name="example"></a>示例

有关示例，请参阅[CComControlBase::GetAmbientAppearance](#getambientappearance)。

##  <a name="ondrawadvanced"></a>  CComControlBase::OnDrawAdvanced

默认值`OnDrawAdvanced`准备正常化的设备上下文进行绘图，然后调用您的控件类的`OnDraw`方法。

```
virtual HRESULT OnDrawAdvanced(ATL_DRAWINFO& di);
```

### <a name="parameters"></a>参数

*di*<br/>
对引用[ATL_DRAWINFO](../../atl/reference/atl-drawinfo-structure.md)结构，其中包含如绘图方面，控件边界的绘图信息和绘图优化与否。

### <a name="return-value"></a>返回值

标准的 HRESULT 值。

### <a name="remarks"></a>备注

如果你想要接受其传递由容器的设备上下文，重写此方法。

请参阅[CComControlBase::OnDraw](#ondraw)的更多详细信息。

##  <a name="onkillfocus"></a>  CComControlBase::OnKillFocus

检查该控件是处于就地活动状态并且具有有效的控件站点，则告知容器控件已丢失焦点。

```
LRESULT OnKillFocus(UINT /* nMsg */,
    WPARAM /* wParam */,
    LPARAM /* lParam */,
    BOOL& bHandled);
```

### <a name="parameters"></a>参数

*nMsg*<br/>
保留。

*wParam*<br/>
保留。

*lParam*<br/>
保留。

*bHandled*<br/>
该标志指示是否已成功处理的窗口消息。 默认值为 FALSE。

### <a name="return-value"></a>返回值

始终返回 1。

##  <a name="onmouseactivate"></a>  CComControlBase::OnMouseActivate

检查 UI 在用户模式下，则将激活的控件。

```
LRESULT OnMouseActivate(UINT /* nMsg */,
    WPARAM /* wParam */,
    LPARAM /* lParam */,
    BOOL& bHandled);
```

### <a name="parameters"></a>参数

*nMsg*<br/>
保留。

*wParam*<br/>
保留。

*lParam*<br/>
保留。

*bHandled*<br/>
该标志指示是否已成功处理的窗口消息。 默认值为 FALSE。

### <a name="return-value"></a>返回值

始终返回 1。

##  <a name="onpaint"></a>  CComControlBase::OnPaint

用于绘制准备容器，获取控件的客户端区域，然后调用控件类`OnDrawAdvanced`方法。

```
LRESULT OnPaint(UINT /* nMsg */,
    WPARAM wParam,
    LPARAM /* lParam */,
    BOOL& /* lResult */);
```

### <a name="parameters"></a>参数

*nMsg*<br/>
保留。

*wParam*<br/>
现有的 HDC。

*lParam*<br/>
保留。

*lResult*<br/>
保留。

### <a name="return-value"></a>返回值

始终返回零。

### <a name="remarks"></a>备注

如果*wParam*不为 NULL，`OnPaint`假定包含有效 HDC，并使用它而不是[CComControlBase::m_hWndCD](#m_hwndcd)。

##  <a name="onsetfocus"></a>  CComControlBase::OnSetFocus

检查该控件是处于就地活动状态并且具有有效的控件站点，则告知容器控件已获得焦点。

```
LRESULT OnSetFocus(UINT /* nMsg */,
    WPARAM /* wParam */,
    LPARAM /* lParam */,
    BOOL& bHandled);
```

### <a name="parameters"></a>参数

*nMsg*<br/>
保留。

*wParam*<br/>
保留。

*lParam*<br/>
保留。

*bHandled*<br/>
该标志指示是否已成功处理的窗口消息。 默认值为 FALSE。

### <a name="return-value"></a>返回值

始终返回 1。

### <a name="remarks"></a>备注

发送到的容器控件已收到焦点的通知。

##  <a name="pretranslateaccelerator"></a>  CComControlBase::PreTranslateAccelerator

重写此方法以提供自己的键盘快捷键处理程序。

```
BOOL PreTranslateAccelerator(LPMSG /* pMsg */,
    HRESULT& /* hRet */);
```

### <a name="parameters"></a>参数

*pMsg*<br/>
保留。

*hRet*<br/>
保留。

### <a name="return-value"></a>返回值

默认情况下返回 FALSE。

##  <a name="sendonclose"></a>  CComControlBase::SendOnClose

通知注册已关闭该控件的通知持有者的所有通知接收器。

```
HRESULT SendOnClose();
```

### <a name="return-value"></a>返回值

返回成功，则为 S_OK 或失败时的错误 HRESULT。

### <a name="remarks"></a>备注

发送通知控件已关闭其通知接收器。

##  <a name="sendondatachange"></a>  CComControlBase::SendOnDataChange

通知控件数据已更改的通知持有者向注册的所有通知接收器。

```
HRESULT SendOnDataChange(DWORD advf = 0);
```

### <a name="parameters"></a>参数

*一个指针*<br/>
建议标志，用于指定如何在调用[IAdviseSink::OnDataChange](/windows/desktop/api/objidl/nf-objidl-iadvisesink-ondatachange)进行。 值取自[一个指针](/windows/desktop/api/objidl/ne-objidl-tagadvf)枚举。

### <a name="return-value"></a>返回值

返回成功，则为 S_OK 或失败时的错误 HRESULT。

##  <a name="sendonrename"></a>  CComControlBase::SendOnRename

通知注册到该控件具有新的名字对象的建议持有者的所有通知接收器。

```
HRESULT SendOnRename(IMoniker* pmk);
```

### <a name="parameters"></a>参数

*pmk*<br/>
控件的新名字对象的指针。

### <a name="return-value"></a>返回值

返回成功，则为 S_OK 或失败时的错误 HRESULT。

### <a name="remarks"></a>备注

将发送一条通知，该控件的名字对象已更改。

##  <a name="sendonsave"></a>  CComControlBase::SendOnSave

通知注册到保存该控件的通知持有者的所有通知接收器。

```
HRESULT SendOnSave();
```

### <a name="return-value"></a>返回值

返回成功，则为 S_OK 或失败时的错误 HRESULT。

### <a name="remarks"></a>备注

发送通知，该控件只是保存其数据。

##  <a name="sendonviewchange"></a>  CComControlBase::SendOnViewChange

向所有已注册控件的视图已更改的通知接收器通知。

```
HRESULT SendOnViewChange(DWORD dwAspect, LONG lindex = -1);
```

### <a name="parameters"></a>参数

*dwAspect*<br/>
外观或控件的视图。

*lindex*<br/>
视图已更改的部分。 仅为-1 是有效的。

### <a name="return-value"></a>返回值

返回成功，则为 S_OK 或失败时的错误 HRESULT。

### <a name="remarks"></a>备注

`SendOnViewChange` 调用[IAdviseSink::OnViewChange](/windows/desktop/api/objidl/nf-objidl-iadvisesink-onviewchange)。 唯一的值*索引*目前支持为-1，指示感兴趣的是整个视图。

##  <a name="setcontrolfocus"></a>  CComControlBase::SetControlFocus

设置或删除与该控件的键盘焦点。

```
BOOL SetControlFocus(BOOL bGrab);
```

### <a name="parameters"></a>参数

*bGrab*<br/>
如果为 TRUE，则设置为调用控件的键盘焦点。 如果为 FALSE，键盘焦点从控件中移除调用，提供具有焦点。

### <a name="return-value"></a>返回值

如果该控件已成功接收到焦点，则将返回 TRUE否则为 FALSE。

### <a name="remarks"></a>备注

对于有窗口控件，Windows API 函数[SetFocus](https://msdn.microsoft.com/library/windows/desktop/ms646312)调用。 对于无窗口控件[IOleInPlaceSiteWindowless::SetFocus](/windows/desktop/api/ocidl/nf-ocidl-ioleinplacesitewindowless-setfocus)调用。 通过此调用，无窗口控件获取键盘焦点，并能够响应窗口消息。

##  <a name="setdirty"></a>  CComControlBase::SetDirty

设置的数据成员`m_bRequiresSave`中的值*bDirty*。

```
void SetDirty(BOOL bDirty);
```

### <a name="parameters"></a>参数

*bDirty*<br/>
数据成员的值[CComControlBase::m_bRequiresSave](#m_brequiressave)。

### <a name="remarks"></a>备注

`SetDirty(TRUE)` 应调用来标记，自上次保存以来已更改该控件。 值`m_bRequiresSave`通过检索[CComControlBase::GetDirty](#getdirty)。

## <a name="see-also"></a>请参阅

[CComControl 类](../../atl/reference/ccomcontrol-class.md)<br/>
[类概述](../../atl/atl-class-overview.md)
