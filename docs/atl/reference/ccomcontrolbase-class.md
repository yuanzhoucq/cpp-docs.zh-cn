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
ms.openlocfilehash: 36afd716009848ccd2e2f0ab966f66f573acdfd8
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69497389"
---
# <a name="ccomcontrolbase-class"></a>CComControlBase 类

此类提供用于创建和管理 ATL 控件的方法。

> [!IMPORTANT]
>  此类及其成员不能用于在 Windows 运行时中执行的应用程序。

## <a name="syntax"></a>语法

```
class ATL_NO_VTABLE CComControlBase
```

## <a name="members"></a>成员

### <a name="public-typedefs"></a>公共 Typedef

|name|描述|
|----------|-----------------|
|[CComControlBase::AppearanceType](#appearancetype)|如果`m_nAppearance` stock 属性的类型不是**short**, 请重写。|

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[CComControlBase::CComControlBase](#ccomcontrolbase)|构造函数。|
|[CComControlBase:: ~ CComControlBase](#dtor)|析构函数。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CComControlBase::ControlQueryInterface](#controlqueryinterface)|检索指向所请求的接口的指针。|
|[CComControlBase::DoesVerbActivate](#doesverbactivate)|`IOleObjectImpl::DoVerb`检查使用的*iVerb*参数是否激活控件的用户界面 (*iVerb*等于 OLEIVERB_UIACTIVATE), 定义用户双击控件时执行的操作 (*iVerb*等于 OLEIVERB_主副本)、显示控件 (*iVerb*等于 OLEIVERB_SHOW) 或激活控件 (*iVerb*等于 OLEIVERB_INPLACEACTIVATE)。|
|[CComControlBase::DoesVerbUIActivate](#doesverbuiactivate)|检查使用`IOleObjectImpl::DoVerb`的*iVerb*参数是否会导致控件的用户界面激活并返回 TRUE。|
|[CComControlBase::DoVerbProperties](#doverbproperties)|显示控件的属性页。|
|[CComControlBase::FireViewChange](#fireviewchange)|调用此方法可告诉容器重绘控件, 或通知已注册的通知接收器控件的视图已更改。|
|[CComControlBase::GetAmbientAppearance](#getambientappearance)|检索控件的当前外观设置 DISPID_AMBIENT_APPEARANCE:0表示平面, 1 表示三维。|
|[CComControlBase::GetAmbientAutoClip](#getambientautoclip)|检索 DISPID_AMBIENT_AUTOCLIP, 它是一个标志, 指示容器是否支持控件显示区域的自动剪辑。|
|[CComControlBase::GetAmbientBackColor](#getambientbackcolor)|检索 DISPID_AMBIENT_BACKCOLOR, 它是由容器定义的所有控件的环境背景色。|
|[CComControlBase::GetAmbientCharSet](#getambientcharset)|检索容器定义的所有控件的环境字符集 (DISPID_AMBIENT_CHARSET)。|
|[CComControlBase::GetAmbientCodePage](#getambientcodepage)|检索容器定义的所有控件的环境字符集 (DISPID_AMBIENT_CODEPAGE)。|
|[CComControlBase::GetAmbientDisplayAsDefault](#getambientdisplayasdefault)|检索 DISPID_AMBIENT_DISPLAYASDEFAULT, 这是一个标志, 如果容器已将此站点中的控件标记为默认按钮, 则该标志为 TRUE, 因此按钮控件应使用较粗的帧绘制其自身。|
|[CComControlBase::GetAmbientDisplayName](#getambientdisplayname)|检索 DISPID_AMBIENT_DISPLAYNAME, 它是容器提供给控件的名称。|
|[CComControlBase::GetAmbientFont](#getambientfont)|检索指向容器环境`IFont`接口的指针。|
|[CComControlBase::GetAmbientFontDisp](#getambientfontdisp)|检索指向容器环境`IFontDisp`调度接口的指针。|
|[CComControlBase::GetAmbientForeColor](#getambientforecolor)|检索由容器定义的所有控件的环境前景色 DISPID_AMBIENT_FORECOLOR。|
|[CComControlBase::GetAmbientLocaleID](#getambientlocaleid)|检索 DISPID_AMBIENT_LOCALEID, 它是容器使用的语言的标识符。|
|[CComControlBase::GetAmbientMessageReflect](#getambientmessagereflect)|检索 DISPID_AMBIENT_MESSAGEREFLECT, 它是一个标志, 指示容器是否想要将窗口消息 (如 WM_DRAWITEM) 作为事件接收。|
|[CComControlBase::GetAmbientPalette](#getambientpalette)|检索用于访问容器的 HPALETTE 的 DISPID_AMBIENT_PALETTE。|
|[CComControlBase::GetAmbientProperty](#getambientproperty)|检索由*id*指定的容器属性。|
|[CComControlBase::GetAmbientRightToLeft](#getambientrighttoleft)|检索 DISPID_AMBIENT_RIGHTTOLEFT, 其中内容由容器显示的方向。|
|[CComControlBase::GetAmbientScaleUnits](#getambientscaleunits)|检索 DISPID_AMBIENT_SCALEUNITS, 容器的环境单位 (例如英寸或厘米) 显示标记。|
|[CComControlBase::GetAmbientShowGrabHandles](#getambientshowgrabhandles)|检索 DISPID_AMBIENT_SHOWGRABHANDLES, 它是一个标志, 指示容器是否允许控件在活动时显示其自身的抓取柄。|
|[CComControlBase::GetAmbientShowHatching](#getambientshowhatching)|检索 DISPID_AMBIENT_SHOWHATCHING, 它是一个标志, 指示容器是否允许控件在 UI 处于活动状态时显示为阴影模式。|
|[CComControlBase::GetAmbientSupportsMnemonics](#getambientsupportsmnemonics)|检索 DISPID_AMBIENT_SUPPORTSMNEMONICS, 它是一个标志, 指示容器是否支持键盘助记键。|
|[CComControlBase::GetAmbientTextAlign](#getambienttextalign)|检索 DISPID_AMBIENT_TEXTALIGN, 它是容器首选的文本对齐方式:如果为 0, 则表示常规对齐方式 (数字右、文本左侧)、1表示左对齐、2表示居中对齐和3表示右对齐。|
|[CComControlBase::GetAmbientTopToBottom](#getambienttoptobottom)|检索 DISPID_AMBIENT_TOPTOBOTTOM, 其中内容由容器显示的方向。|
|[CComControlBase::GetAmbientUIDead](#getambientuidead)|检索 DISPID_AMBIENT_UIDEAD, 它是一个标志, 指示容器是否希望控件响应用户界面操作。|
|[CComControlBase::GetAmbientUserMode](#getambientusermode)|检索 DISPID_AMBIENT_USERMODE, 它是一个标志, 用于指示容器处于运行模式 (TRUE) 还是设计模式 (FALSE)。|
|[CComControlBase::GetDirty](#getdirty)|返回数据成员`m_bRequiresSave`的值。|
|[CComControlBase::GetZoomInfo](#getzoominfo)|检索为就地编辑激活的控件的缩放系数的 x 和 y 值。|
|[CComControlBase::InPlaceActivate](#inplaceactivate)|使控件从非活动状态过渡到*iVerb*中的谓词所指示的状态。|
|[CComControlBase::InternalGetSite](#internalgetsite)|调用此方法可在控制站点中查询指向标识接口的指针。|
|[CComControlBase::OnDraw](#ondraw)|重写此方法以绘制控件。|
|[CComControlBase::OnDrawAdvanced](#ondrawadvanced)|默认情况`OnDrawAdvanced`下, 准备用于绘制的规范化设备上下文, 然后调用控件类`OnDraw`的方法。|
|[CComControlBase::OnKillFocus](#onkillfocus)|检查控件是否处于就地活动状态并具有有效的控制站点, 然后通知容器控件已失去焦点。|
|[CComControlBase::OnMouseActivate](#onmouseactivate)|检查 UI 是否处于用户模式, 然后激活控件。|
|[CComControlBase::OnPaint](#onpaint)|准备用于绘制的容器, 获取该控件的工作区, 然后调用该控件类的`OnDraw`方法。|
|[CComControlBase::OnSetFocus](#onsetfocus)|检查控件是否处于就地活动状态并具有有效的控制站点, 然后通知容器控件已获得焦点。|
|[CComControlBase::PreTranslateAccelerator](#pretranslateaccelerator)|重写此方法以提供您自己的键盘快捷键处理程序。|
|[CComControlBase::SendOnClose](#sendonclose)|通知所有注册了通知持有人的通知接收器控件已关闭。|
|[CComControlBase::SendOnDataChange](#sendondatachange)|通知所有注册了通知持有人的通知接收器控制数据已更改。|
|[CComControlBase::SendOnRename](#sendonrename)|通知所有注册了通知持有人的通知接收器控件都有一个新的名字对象。|
|[CComControlBase::SendOnSave](#sendonsave)|通知所有注册了通知持有人的通知接收器已保存控件。|
|[CComControlBase::SendOnViewChange](#sendonviewchange)|通知所有已注册的通知接收器控件的视图已更改。|
|[CComControlBase::SetControlFocus](#setcontrolfocus)|设置或删除控件中的键盘焦点。|
|[CComControlBase::SetDirty](#setdirty)|将数据成员`m_bRequiresSave`设置为*bDirty*中的值。|

### <a name="public-data-members"></a>公共数据成员

|名称|描述|
|----------|-----------------|
|[CComControlBase::m_bAutoSize](#m_bautosize)|指示控件不能为任何其他大小的标志。|
|[CComControlBase::m_bDrawFromNatural](#m_bdrawfromnatural)|一个`IDataObjectImpl::GetData`标志, 它`CComControlBase::GetZoomInfo`指示和应`m_sizeNatural`设置控件大小, 而不`m_sizeExtent`是来自。|
|[CComControlBase::m_bDrawGetDataInHimetric](#m_bdrawgetdatainhimetric)|一个标志, `IDataObjectImpl::GetData`指示在绘制时应使用 HIMETRIC 单位, 而不是像素。|
|[CComControlBase::m_bInPlaceActive](#m_binplaceactive)|指示控件是否处于就地活动状态的标志。|
|[CComControlBase::m_bInPlaceSiteEx](#m_binplacesiteex)|标志, 指示容器支持`IOleInPlaceSiteEx` interface 和 OCX96 控件功能, 如无窗口和无闪烁控件。|
|[CComControlBase::m_bNegotiatedWnd](#m_bnegotiatedwnd)|指示控件是否已与容器协商的标记, 该容器涉及对 OCX96 控件功能 (如无闪烁和无窗口控件) 的支持, 以及控件是有窗口还是无窗口控件。|
|[CComControlBase::m_bRecomposeOnResize](#m_brecomposeonresize)|一个标志, 用于指示当容器更改控件的显示大小时, 控件要 recompose 其演示文稿。|
|[CComControlBase::m_bRequiresSave](#m_brequiressave)|一个标志, 用于指示控件自上次保存后已发生更改。|
|[CComControlBase::m_bResizeNatural](#m_bresizenatural)|一个标志, 用于指示当容器更改控件的显示大小时, 控件要调整其自然范围 (其未缩放的物理大小)。|
|[CComControlBase::m_bUIActive](#m_buiactive)|指示控件的用户界面 (如菜单和工具栏) 处于活动状态的标志。|
|[CComControlBase::m_bUsingWindowRgn](#m_busingwindowrgn)|标志, 该标志指示控件使用容器提供的窗口区域。|
|[CComControlBase::m_bWasOnceWindowless](#m_bwasoncewindowless)|标志, 该标志指示控件已经处于无窗口窗口, 但现在可以或可能不是无窗口。|
|[CComControlBase::m_bWindowOnly](#m_bwindowonly)|指示控件应为窗口的标志, 即使容器支持无窗口控件。|
|[CComControlBase::m_bWndLess](#m_bwndless)|指示控件无窗口的标志。|
|[CComControlBase::m_hWndCD](#m_hwndcd)|包含对与控件关联的窗口句柄的引用。|
|[CComControlBase::m_nFreezeEvents](#m_nfreezeevents)|容器在不干预事件 (接受事件) 的情况下冻结事件 (拒绝接受事件) 的次数。|
|[CComControlBase::m_rcPos](#m_rcpos)|控件的位置 (以像素为单位), 以容器的坐标表示。|
|[CComControlBase::m_sizeExtent](#m_sizeextent)|对于特定显示, 以 HIMETRIC 单位 (每个单位为0.01 毫米) 的控件范围。|
|[CComControlBase::m_sizeNatural](#m_sizenatural)|控件的物理大小, 以 HIMETRIC 单位 (每个单位为0.01 毫米)。|
|[CComControlBase::m_spAdviseSink](#m_spadvisesink)|指向容器上的通知连接的直接指针 (容器的[IAdviseSink](/windows/win32/api/objidl/nn-objidl-iadvisesink))。|
|[CComControlBase::m_spAmbientDispatch](#m_spambientdispatch)|一个`CComDispatchDriver`对象, 它允许您`IDispatch`通过指针检索和设置容器的属性。|
|[CComControlBase::m_spClientSite](#m_spclientsite)|指向容器中控件的客户端站点的指针。|
|[CComControlBase::m_spDataAdviseHolder](#m_spdataadviseholder)|提供用于在数据对象和通知接收器之间保存通知连接的标准方法。|
|[CComControlBase::m_spInPlaceSite](#m_spinplacesite)|指向容器的[IOleInPlaceSite](/windows/win32/api/oleidl/nn-oleidl-ioleinplacesite)、 [IOleInPlaceSiteEx](/windows/win32/api/ocidl/nn-ocidl-ioleinplacesiteex)或[IOleInPlaceSiteWindowless](/windows/win32/api/ocidl/nn-ocidl-ioleinplacesitewindowless)接口指针的指针。|
|[CComControlBase::m_spOleAdviseHolder](#m_spoleadviseholder)|提供了一种用于保存咨询连接的标准实现方式。|

## <a name="remarks"></a>备注

此类提供用于创建和管理 ATL 控件的方法。 [CComControl 类](../../atl/reference/ccomcontrol-class.md)派生`CComControlBase`自。 使用 ATL 控件向导创建标准控件或 DHTML 控件时, 向导将自动从`CComControlBase`派生您的类。

有关创建控件的详细信息, 请参阅[ATL 教程](../../atl/active-template-library-atl-tutorial.md)。 有关 ATL 项目向导的详细信息, 请参阅文章[创建 Atl 项目](../../atl/reference/creating-an-atl-project.md)。

## <a name="requirements"></a>要求

**标头:** atlctl

##  <a name="appearancetype"></a>CComControlBase::AppearanceType

如果`m_nAppearance` stock 属性的类型不是**short**, 请重写。

```
typedef short AppearanceType;
```

### <a name="remarks"></a>备注

ATL 控件向导添加`m_nAppearance` short 类型的常用属性。 如果`AppearanceType`使用其他数据类型, 则重写。

##  <a name="ccomcontrolbase"></a>CComControlBase::CComControlBase

构造函数。

```
CComControlBase(HWND& h);
```

### <a name="parameters"></a>参数

*h*<br/>
与控件关联的窗口的句柄。

### <a name="remarks"></a>备注

将控件大小初始化为 5080X5080 HIMETRIC 单位 (2 "X2"), 并将`CComControlBase`数据成员值初始化为 NULL 或 FALSE。

##  <a name="dtor"></a>CComControlBase:: ~ CComControlBase

析构函数。

```
~CComControlBase();
```

### <a name="remarks"></a>备注

如果控件是开窗控件`~CComControlBase`的, 则通过调用[DestroyWindow](/windows/win32/api/winuser/nf-winuser-destroywindow)将其销毁。

##  <a name="controlqueryinterface"></a>CComControlBase::ControlQueryInterface

检索指向所请求的接口的指针。

```
virtual HRESULT ControlQueryInterface(const IID& iid,
    void** ppv);
```

### <a name="parameters"></a>参数

*iid*<br/>
所请求的接口的 GUID。

*ppv*<br/>
指向由*iid*标识的接口指针的指针; 如果找不到接口, 则为 NULL。

### <a name="remarks"></a>备注

仅处理 COM 映射表中的接口。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_COM#15](../../atl/codesnippet/cpp/ccomcontrolbase-class_1.cpp)]

##  <a name="doesverbactivate"></a>  CComControlBase::DoesVerbActivate

`IOleObjectImpl::DoVerb`检查使用的*iVerb*参数是否激活控件的用户界面 (*iVerb*等于 OLEIVERB_UIACTIVATE), 定义用户双击控件时执行的操作 (*iVerb*等于 OLEIVERB_主副本)、显示控件 (*iVerb*等于 OLEIVERB_SHOW) 或激活控件 (*iVerb*等于 OLEIVERB_INPLACEACTIVATE)。

```
BOOL DoesVerbActivate(LONG iVerb);
```

### <a name="parameters"></a>参数

*iVerb*<br/>
值, 指示要执行`DoVerb`的操作。

### <a name="return-value"></a>返回值

如果*iVerb*等于 OLEIVERB_UIACTIVATE、OLEIVERB_PRIMARY、OLEIVERB_SHOW 或 OLEIVERB_INPLACEACTIVATE, 则返回 TRUE;否则, 返回 FALSE。

### <a name="remarks"></a>备注

你可以重写此方法以定义你自己的激活谓词。

##  <a name="doesverbuiactivate"></a>  CComControlBase::DoesVerbUIActivate

检查使用`IOleObjectImpl::DoVerb`的*iVerb*参数是否会导致控件的用户界面激活并返回 TRUE。

```
BOOL DoesVerbUIActivate(LONG iVerb);
```

### <a name="parameters"></a>参数

*iVerb*<br/>
值, 指示要执行`DoVerb`的操作。

### <a name="return-value"></a>返回值

如果*iVerb*等于 OLEIVERB_UIACTIVATE、OLEIVERB_PRIMARY、OLEIVERB_SHOW 或 OLEIVERB_INPLACEACTIVATE, 则返回 TRUE。 否则, 此方法将返回 FALSE。

##  <a name="doverbproperties"></a>CComControlBase::D oVerbProperties

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

标准的 HRESULT 值之一。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_COM#19](../../atl/codesnippet/cpp/ccomcontrolbase-class_2.cpp)]

[!code-cpp[NVC_ATL_COM#20](../../atl/codesnippet/cpp/ccomcontrolbase-class_3.h)]

##  <a name="fireviewchange"></a>CComControlBase::FireViewChange

调用此方法可告诉容器重绘控件, 或通知已注册的通知接收器控件的视图已更改。

```
HRESULT FireViewChange();
```

### <a name="return-value"></a>返回值

标准的 HRESULT 值之一。

### <a name="remarks"></a>备注

如果该控件处于活动状态 (控制类数据成员[CComControlBase:: m_bInPlaceActive](#m_binplaceactive)为 TRUE), 则通知容器要重绘整个控件。 如果控件处于非活动状态, 则通知控件的已注册的通知接收器 (通过控制类数据成员[CComControlBase:: m_spAdviseSink](#m_spadvisesink)), 该控件的视图已更改。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_COM#21](../../atl/codesnippet/cpp/ccomcontrolbase-class_4.cpp)]

##  <a name="getambientappearance"></a>CComControlBase::GetAmbientAppearance

检索控件的当前外观设置 DISPID_AMBIENT_APPEARANCE:0表示平面, 1 表示三维。

```
HRESULT GetAmbientAppearance(short& nAppearance);
```

### <a name="parameters"></a>参数

*nAppearance*<br/>
DISPID_AMBIENT_APPEARANCE 属性。

### <a name="return-value"></a>返回值

标准的 HRESULT 值之一。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_COM#22](../../atl/codesnippet/cpp/ccomcontrolbase-class_5.h)]

##  <a name="getambientautoclip"></a>CComControlBase::GetAmbientAutoClip

检索 DISPID_AMBIENT_AUTOCLIP, 它是一个标志, 指示容器是否支持控件显示区域的自动剪辑。

```
HRESULT GetAmbientAutoClip(BOOL& bAutoClip);
```

### <a name="parameters"></a>参数

*bAutoClip*<br/>
DISPID_AMBIENT_AUTOCLIP 属性。

### <a name="return-value"></a>返回值

标准的 HRESULT 值之一。

##  <a name="getambientbackcolor"></a>CComControlBase::GetAmbientBackColor

检索 DISPID_AMBIENT_BACKCOLOR, 它是由容器定义的所有控件的环境背景色。

```
HRESULT GetAmbientBackColor(OLE_COLOR& BackColor);
```

### <a name="parameters"></a>参数

*BackColor*<br/>
DISPID_AMBIENT_BACKCOLOR 属性。

### <a name="return-value"></a>返回值

标准的 HRESULT 值之一。

##  <a name="getambientcharset"></a>CComControlBase::GetAmbientCharSet

检索容器定义的所有控件的环境字符集 (DISPID_AMBIENT_CHARSET)。

```
HRESULT GetAmbientCharSet(BSTR& bstrCharSet);
```

### <a name="parameters"></a>参数

*bstrCharSet*<br/>
DISPID_AMBIENT_CHARSET 属性。

### <a name="return-value"></a>返回值

如果成功, 则返回 S_OK, 否则返回错误 HRESULT。

##  <a name="getambientcodepage"></a>CComControlBase::GetAmbientCodePage

检索由容器定义的所有控件的环境代码页 DISPID_AMBIENT_CODEPAGE。

```
HRESULT GetAmbientCodePage(ULONG& ulCodePage);
```

### <a name="parameters"></a>参数

*ulCodePage*<br/>
DISPID_AMBIENT_CODEPAGE 属性。

### <a name="return-value"></a>返回值

如果成功, 则返回 S_OK, 否则返回错误 HRESULT。

##  <a name="getambientdisplayasdefault"></a>CComControlBase::GetAmbientDisplayAsDefault

检索 DISPID_AMBIENT_DISPLAYASDEFAULT, 这是一个标志, 如果容器已将此站点中的控件标记为默认按钮, 则该标志为 TRUE, 因此按钮控件应使用较粗的帧绘制其自身。

```
HRESULT GetAmbientDisplayAsDefault(BOOL& bDisplayAsDefault);
```

### <a name="parameters"></a>参数

*bDisplayAsDefault*<br/>
DISPID_AMBIENT_DISPLAYASDEFAULT 属性。

### <a name="return-value"></a>返回值

标准的 HRESULT 值之一。

##  <a name="getambientdisplayname"></a>CComControlBase::GetAmbientDisplayName

检索 DISPID_AMBIENT_DISPLAYNAME, 它是容器提供给控件的名称。

```
HRESULT GetAmbientDisplayName(BSTR& bstrDisplayName);
```

### <a name="parameters"></a>参数

*bstrDisplayName*<br/>
DISPID_AMBIENT_DISPLAYNAME 属性。

### <a name="return-value"></a>返回值

标准的 HRESULT 值之一。

##  <a name="getambientfont"></a>CComControlBase::GetAmbientFont

检索指向容器环境`IFont`接口的指针。

```
HRESULT GetAmbientFont(IFont** ppFont);
```

### <a name="parameters"></a>参数

*ppFont*<br/>
指向容器环境[IFont](/windows/win32/api/ocidl/nn-ocidl-ifont)接口的指针。

### <a name="return-value"></a>返回值

标准的 HRESULT 值之一。

### <a name="remarks"></a>备注

如果属性为 NULL, 则指针为 NULL。 如果指针不为 NULL, 则调用方必须释放指针。

##  <a name="getambientfontdisp"></a>CComControlBase::GetAmbientFontDisp

检索指向容器环境`IFontDisp`调度接口的指针。

```
HRESULT GetAmbientFontDisp(IFontDisp** ppFont);
```

### <a name="parameters"></a>参数

*ppFont*<br/>
指向容器环境[IFontDisp](/windows/win32/api/ocidl/nn-ocidl-ifontdisp)调度接口的指针。

### <a name="return-value"></a>返回值

如果成功, 则返回 S_OK, 否则返回错误 HRESULT。

### <a name="remarks"></a>备注

如果属性为 NULL, 则指针为 NULL。 如果指针不为 NULL, 则调用方必须释放指针。

##  <a name="getambientforecolor"></a>CComControlBase::GetAmbientForeColor

检索由容器定义的所有控件的环境前景色 DISPID_AMBIENT_FORECOLOR。

```
HRESULT GetAmbientForeColor(OLE_COLOR& ForeColor);
```

### <a name="parameters"></a>参数

*ForeColor*<br/>
DISPID_AMBIENT_FORECOLOR 属性。

### <a name="return-value"></a>返回值

标准的 HRESULT 值之一。

##  <a name="getambientlocaleid"></a>CComControlBase::GetAmbientLocaleID

检索 DISPID_AMBIENT_LOCALEID, 它是容器使用的语言的标识符。

```
HRESULT GetAmbientLocaleID(LCID& lcid);
```

### <a name="parameters"></a>参数

*lcid*<br/>
DISPID_AMBIENT_LOCALEID 属性。

### <a name="return-value"></a>返回值

标准的 HRESULT 值之一。

### <a name="remarks"></a>备注

控件可以使用此标识符来改编不同语言的用户界面。

##  <a name="getambientmessagereflect"></a>CComControlBase::GetAmbientMessageReflect

检索 DISPID_AMBIENT_MESSAGEREFLECT, 它是一个标志, 指示容器是否想要将窗口消息 ( `WM_DRAWITEM`如) 作为事件接收。

```
HRESULT GetAmbientMessageReflect(BOOL& bMessageReflect);
```

### <a name="parameters"></a>参数

*bMessageReflect*<br/>
DISPID_AMBIENT_MESSAGEREFLECT 属性。

### <a name="return-value"></a>返回值

标准的 HRESULT 值之一。

##  <a name="getambientpalette"></a>CComControlBase::GetAmbientPalette

检索用于访问容器的 HPALETTE 的 DISPID_AMBIENT_PALETTE。

```
HRESULT GetAmbientPalette(HPALETTE& hPalette);
```

### <a name="parameters"></a>参数

*hPalette*<br/>
DISPID_AMBIENT_PALETTE 属性。

### <a name="return-value"></a>返回值

标准的 HRESULT 值之一。

##  <a name="getambientproperty"></a>CComControlBase::GetAmbientProperty

检索*dispid*指定的容器属性。

```
HRESULT GetAmbientProperty(DISPID dispid, VARIANT& var);
```

### <a name="parameters"></a>参数

*dispid*<br/>
要检索的容器属性的标识符。

*var*<br/>
用于接收属性的变量。

### <a name="return-value"></a>返回值

标准的 HRESULT 值之一。

### <a name="remarks"></a>备注

ATL 提供一组用于检索特定属性的帮助器函数, 例如[CComControlBase:: GetAmbientBackColor](#getambientbackcolor)。 如果没有合适的可用方法, 请使用`GetAmbientProperty`。

##  <a name="getambientrighttoleft"></a>CComControlBase::GetAmbientRightToLeft

检索 DISPID_AMBIENT_RIGHTTOLEFT, 其中内容由容器显示的方向。

```
HRESULT GetAmbientRightToLeft(BOOL& bRightToLeft);
```

### <a name="parameters"></a>参数

*bRightToLeft*<br/>
DISPID_AMBIENT_RIGHTTOLEFT 属性。 如果内容从右向左显示, 则设置为 TRUE, 如果内容从左向右显示, 则设置为 FALSE。

### <a name="return-value"></a>返回值

如果成功, 则返回 S_OK, 否则返回错误 HRESULT。

##  <a name="getambientscaleunits"></a>CComControlBase::GetAmbientScaleUnits

检索 DISPID_AMBIENT_SCALEUNITS, 容器的环境单位 (例如英寸或厘米) 显示标记。

```
HRESULT GetAmbientScaleUnits(BSTR& bstrScaleUnits);
```

### <a name="parameters"></a>参数

*bstrScaleUnits*<br/>
DISPID_AMBIENT_SCALEUNITS 属性。

### <a name="return-value"></a>返回值

标准的 HRESULT 值之一。

##  <a name="getambientshowgrabhandles"></a>CComControlBase::GetAmbientShowGrabHandles

检索 DISPID_AMBIENT_SHOWGRABHANDLES, 它是一个标志, 指示容器是否允许控件在活动时显示其自身的抓取柄。

```
HRESULT GetAmbientShowGrabHandles(BOOL& bShowGrabHandles);
```

### <a name="parameters"></a>参数

*bShowGrabHandles*<br/>
DISPID_AMBIENT_SHOWGRABHANDLES 属性。

### <a name="return-value"></a>返回值

标准的 HRESULT 值之一。

##  <a name="getambientshowhatching"></a>CComControlBase::GetAmbientShowHatching

检索 DISPID_AMBIENT_SHOWHATCHING, 它是一个标志, 指示容器是否允许控件在控件的用户界面处于活动状态时显示为阴影模式。

```
HRESULT GetAmbientShowHatching(BOOL& bShowHatching);
```

### <a name="parameters"></a>参数

*bShowHatching*<br/>
DISPID_AMBIENT_SHOWHATCHING 属性。

### <a name="return-value"></a>返回值

标准的 HRESULT 值之一。

##  <a name="getambientsupportsmnemonics"></a>CComControlBase::GetAmbientSupportsMnemonics

检索 DISPID_AMBIENT_SUPPORTSMNEMONICS, 它是一个标志, 指示容器是否支持键盘助记键。

```
HRESULT GetAmbientSupportsMnemonics(BOOL& bSupportsMnemonics);
```

### <a name="parameters"></a>参数

*bSupportsMnemonics*<br/>
DISPID_AMBIENT_SUPPORTSMNEMONICS 属性。

### <a name="return-value"></a>返回值

标准的 HRESULT 值之一。

##  <a name="getambienttextalign"></a>CComControlBase::GetAmbientTextAlign

检索 DISPID_AMBIENT_TEXTALIGN, 它是容器首选的文本对齐方式:如果为 0, 则表示常规对齐方式 (数字右、文本左侧)、1表示左对齐、2表示居中对齐和3表示右对齐。

```
HRESULT GetAmbientTextAlign(short& nTextAlign);
```

### <a name="parameters"></a>参数

*nTextAlign*<br/>
DISPID_AMBIENT_TEXTALIGN 属性。

### <a name="return-value"></a>返回值

标准的 HRESULT 值之一。

##  <a name="getambienttoptobottom"></a>CComControlBase::GetAmbientTopToBottom

检索 DISPID_AMBIENT_TOPTOBOTTOM, 其中内容由容器显示的方向。

```
HRESULT GetAmbientTopToBottom(BOOL& bTopToBottom);
```

### <a name="parameters"></a>参数

*bTopToBottom*<br/>
DISPID_AMBIENT_TOPTOBOTTOM 属性。 如果文本显示为从上到下, 则设置为 TRUE, 如果文本显示底部到顶部, 则设置为 FALSE。

### <a name="return-value"></a>返回值

如果成功, 则返回 S_OK, 否则返回错误 HRESULT。

##  <a name="getambientuidead"></a>CComControlBase::GetAmbientUIDead

检索 DISPID_AMBIENT_UIDEAD, 它是一个标志, 指示容器是否希望控件响应用户界面操作。

```
HRESULT GetAmbientUIDead(BOOL& bUIDead);
```

### <a name="parameters"></a>参数

*bUIDead*<br/>
DISPID_AMBIENT_UIDEAD 属性。

### <a name="return-value"></a>返回值

标准的 HRESULT 值之一。

### <a name="remarks"></a>备注

如果为 TRUE, 则控件不应响应。 无论 DISPID_AMBIENT_USERMODE 标志如何, 此标志都适用。 请参阅[CComControlBase:: GetAmbientUserMode](#getambientusermode)。

##  <a name="getambientusermode"></a>CComControlBase::GetAmbientUserMode

检索 DISPID_AMBIENT_USERMODE, 它是一个标志, 用于指示容器处于运行模式 (TRUE) 还是设计模式 (FALSE)。

```
HRESULT GetAmbientUserMode(BOOL& bUserMode);
```

### <a name="parameters"></a>参数

*bUserMode*<br/>
DISPID_AMBIENT_USERMODE 属性。

### <a name="return-value"></a>返回值

标准的 HRESULT 值之一。

##  <a name="getdirty"></a>CComControlBase::GetDirty

返回数据成员`m_bRequiresSave`的值。

```
BOOL GetDirty();
```

### <a name="return-value"></a>返回值

返回数据成员[m_bRequiresSave](#m_brequiressave)的值。

### <a name="remarks"></a>备注

此值是使用[CComControlBase:: SetDirty](#setdirty)设置的。

##  <a name="getzoominfo"></a>CComControlBase::GetZoomInfo

检索为就地编辑激活的控件的缩放系数的 x 和 y 值。

```
void GetZoomInfo(ATL_DRAWINFO& di);
```

### <a name="parameters"></a>参数

*di*<br/>
将保存缩放系数的分子和分母的结构。 有关详细信息, 请参阅[ATL_DRAWINFO](../../atl/reference/atl-drawinfo-structure.md)。

### <a name="remarks"></a>备注

缩放因子是控件的自然大小与当前范围的比例。

##  <a name="inplaceactivate"></a>  CComControlBase::InPlaceActivate

使控件从非活动状态过渡到*iVerb*中的谓词所指示的状态。

```
HRESULT InPlaceActivate(LONG iVerb, const RECT* prcPosRect = NULL);
```

### <a name="parameters"></a>参数

*iVerb*<br/>
值, 指示要由 IOleObjectImpl 执行的操作[::D overb](../../atl/reference/ioleobjectimpl-class.md#doverb)。

*prcPosRect*<br/>
指向就地控件的位置的指针。

### <a name="return-value"></a>返回值

标准的 HRESULT 值之一。

### <a name="remarks"></a>备注

在激活之前, 此方法会检查控件是否具有客户端站点, 检查控件的可见程度, 并获取控件在父窗口中的位置。 激活控件后, 此方法会激活控件的用户界面, 并通知容器使控件可见。

此方法还将检索`IOleInPlaceSite`控件`IOleInPlaceSiteEx`的、 `IOleInPlaceSiteWindowless`或接口指针, 并将其存储在控件类的数据成员[CComControlBase:: m_spInPlaceSite](#m_spinplacesite)中。 根据需要将控件类数据成员[CComControlBase:: m_bInPlaceSiteEx](#m_binplacesiteex)、 [CComControlBase:: m_bWndLess](#m_bwndless)、 [CComControlBase:: M_bWasOnceWindowless](#m_bwasoncewindowless)和[CComControlBase:: m_bNegotiatedWnd](#m_bnegotiatedwnd)设置为 true。

##  <a name="internalgetsite"></a>CComControlBase::InternalGetSite

调用此方法可在控制站点中查询指向标识接口的指针。

```
HRESULT InternalGetSite(REFIID riid, void** ppUnkSite);
```

### <a name="parameters"></a>参数

*riid*<br/>
应在*ppUnkSite*中返回的接口指针的 IID。

*ppUnkSite*<br/>
指针变量的地址, 该变量接收在*riid*中请求的接口指针。

### <a name="return-value"></a>返回值

如果成功, 则返回 S_OK, 否则返回错误 HRESULT。

### <a name="remarks"></a>备注

如果站点支持在*riid*中请求的接口, 则会通过*ppUnkSite*返回指针。 否则, *ppUnkSite*将设置为 NULL。

##  <a name="m_bautosize"></a>CComControlBase::m_bAutoSize

指示控件不能为任何其他大小的标志。

```
unsigned m_bAutoSize:1;
```

### <a name="remarks"></a>备注

此标志由`IOleObjectImpl::SetExtent`检查, 如果为 TRUE, 则会导致函数返回 E_FAIL。

> [!NOTE]
>  若要在控件类中使用此数据成员, 必须将其声明为控件类中的数据成员。 控件类将不会从基类继承此数据成员, 因为它是在基类的联合中声明的。

如果在 ATL 控件向导的 "[常用属性](../../atl/reference/stock-properties-atl-control-wizard.md)" 选项卡上添加 "**自动调整大小**" 选项, 向导将在控件类中自动创建此数据成员, 为属性创建 put 和 get 方法, 并支持[IPropertyNotifySink](/windows/win32/api/ocidl/nn-ocidl-ipropertynotifysink)当属性更改时, 自动通知容器。

##  <a name="m_bdrawfromnatural"></a>CComControlBase::m_bDrawFromNatural

一个`IDataObjectImpl::GetData`标志, 它`CComControlBase::GetZoomInfo`指示和应`m_sizeNatural`设置控件大小, 而不`m_sizeExtent`是来自。

```
unsigned m_bDrawFromNatural:1;
```

### <a name="remarks"></a>备注

> [!NOTE]
>  若要在控件类中使用此数据成员, 必须将其声明为控件类中的数据成员。 控件类将不会从基类继承此数据成员, 因为它是在基类的联合中声明的。

##  <a name="m_bdrawgetdatainhimetric"></a>CComControlBase::m_bDrawGetDataInHimetric

一个标志, `IDataObjectImpl::GetData`指示在绘制时应使用 HIMETRIC 单位, 而不是像素。

```
unsigned m_bDrawGetDataInHimetric:1;
```

### <a name="remarks"></a>备注

每个逻辑 HIMETRIC 单位为0.01 毫米。

> [!NOTE]
>  若要在控件类中使用此数据成员, 必须将其声明为控件类中的数据成员。 控件类将不会从基类继承此数据成员, 因为它是在基类的联合中声明的。

##  <a name="m_binplaceactive"></a>  CComControlBase::m_bInPlaceActive

指示控件是否处于就地活动状态的标志。

```
unsigned m_bInPlaceActive:1;
```

### <a name="remarks"></a>备注

这意味着控件可见并且其窗口 (如果有) 可见, 但其菜单和工具栏可能不处于活动状态。 `m_bUIActive`标志指示控件的用户界面 (如菜单) 也处于活动状态。

> [!NOTE]
>  若要在控件类中使用此数据成员, 必须将其声明为控件类中的数据成员。 控件类将不会从基类继承此数据成员, 因为它是在基类的联合中声明的。

##  <a name="m_binplacesiteex"></a>CComControlBase::m_bInPlaceSiteEx

标志, 指示容器支持`IOleInPlaceSiteEx` interface 和 OCX96 控件功能, 如无窗口和无闪烁控件。

```
unsigned m_bInPlaceSiteEx:1;
```

### <a name="remarks"></a>备注

> [!NOTE]
>  若要在控件类中使用此数据成员, 必须将其声明为控件类中的数据成员。 控件类将不会从基类继承此数据成员, 因为它是在基类的联合中声明的。

数据`m_spInPlaceSite`成员指向[IOleInPlaceSite](/windows/win32/api/oleidl/nn-oleidl-ioleinplacesite)、 [IOleInPlaceSiteEx](/windows/win32/api/ocidl/nn-ocidl-ioleinplacesiteex)或[IOleInPlaceSiteWindowless](/windows/win32/api/ocidl/nn-ocidl-ioleinplacesitewindowless) `m_bWndLess`接口, 具体取决于和`m_bInPlaceSiteEx`标志的值。 (若要使`m_bNegotiatedWnd` `m_spInPlaceSite`指针有效, 数据成员必须为 TRUE。)

如果`m_bWndLess`为 FALSE 且`m_bInPlaceSiteEx` 为TRUE`m_spInPlaceSite` , 则为接口指针。`IOleInPlaceSiteEx` 请参阅[m_spInPlaceSite](#m_spinplacesite) , 了解这三个数据成员之间的关系。

##  <a name="m_bnegotiatedwnd"></a>CComControlBase::m_bNegotiatedWnd

指示控件是否已与容器协商的标记, 该容器涉及对 OCX96 控件功能 (如无闪烁和无窗口控件) 的支持, 以及控件是有窗口还是无窗口控件。

```
unsigned m_bNegotiatedWnd:1;
```

### <a name="remarks"></a>备注

> [!NOTE]
>  若要在控件类中使用此数据成员, 必须将其声明为控件类中的数据成员。 控件类将不会从基类继承此数据成员, 因为它是在基类的联合中声明的。

若要使`m_spInPlaceSite`指针有效,标志必须为TRUE。`m_bNegotiatedWnd`

##  <a name="m_brecomposeonresize"></a>CComControlBase::m_bRecomposeOnResize

一个标志, 用于指示当容器更改控件的显示大小时, 控件要 recompose 其演示文稿。

```
unsigned m_bRecomposeOnResize:1;
```

### <a name="remarks"></a>备注

> [!NOTE]
>  若要在控件类中使用此数据成员, 必须将其声明为控件类中的数据成员。 控件类将不会从基类继承此数据成员, 因为它是在基类的联合中声明的。

此标志由[IOleObjectImpl:: SetExtent](../../atl/reference/ioleobjectimpl-class.md#setextent)检查, 如果为 TRUE, `SetExtent`则将视图更改通知容器。 如果设置了此标志, 则还应设置[OLEMISC](/windows/win32/api/oleidl/ne-oleidl-olemisc)枚举中的 OLEMISC_RECOMPOSEONRESIZE 位。

##  <a name="m_brequiressave"></a>CComControlBase::m_bRequiresSave

一个标志, 用于指示控件自上次保存后已发生更改。

```
unsigned m_bRequiresSave:1;
```

### <a name="remarks"></a>备注

的值`m_bRequiresSave`可以设置为[CComControlBase:: SetDirty](#setdirty) , 并检索[CComControlBase:: GetDirty](#getdirty)。

> [!NOTE]
>  若要在控件类中使用此数据成员, 必须将其声明为控件类中的数据成员。 控件类将不会从基类继承此数据成员, 因为它是在基类的联合中声明的。

##  <a name="m_bresizenatural"></a>CComControlBase::m_bResizeNatural

一个标志, 用于指示当容器更改控件的显示大小时, 控件要调整其自然范围 (其未缩放的物理大小)。

```
unsigned m_bResizeNatural:1;
```

### <a name="remarks"></a>备注

此标志由`IOleObjectImpl::SetExtent`进行检查, 如果为 TRUE, 则将`SetExtent`传入的大小分配`m_sizeNatural`给。

传入`SetExtent`的大小始终`m_sizeExtent`分配给, `m_bResizeNatural`而不考虑的值。

> [!NOTE]
>  若要在控件类中使用此数据成员, 必须将其声明为控件类中的数据成员。 控件类将不会从基类继承此数据成员, 因为它是在基类的联合中声明的。

##  <a name="m_buiactive"></a>CComControlBase::m_bUIActive

指示控件的用户界面 (如菜单和工具栏) 处于活动状态的标志。

```
unsigned m_bUIActive:1;
```

### <a name="remarks"></a>备注

`m_bInPlaceActive`标志指示该控件处于活动状态, 但不指示其用户界面处于活动状态。

> [!NOTE]
>  若要在控件类中使用此数据成员, 必须将其声明为控件类中的数据成员。 控件类将不会从基类继承此数据成员, 因为它是在基类的联合中声明的。

##  <a name="m_busingwindowrgn"></a>CComControlBase::m_bUsingWindowRgn

标志, 该标志指示控件使用容器提供的窗口区域。

```
unsigned m_bUsingWindowRgn:1;
```

### <a name="remarks"></a>备注

> [!NOTE]
>  若要在控件类中使用此数据成员, 必须将其声明为控件类中的数据成员。 控件类将不会从基类继承此数据成员, 因为它是在基类的联合中声明的。

##  <a name="m_bwasoncewindowless"></a>CComControlBase::m_bWasOnceWindowless

标志, 该标志指示控件已经处于无窗口窗口, 但现在可以或可能不是无窗口。

```
unsigned m_bWasOnceWindowless:1;
```

### <a name="remarks"></a>备注

> [!NOTE]
>  若要在控件类中使用此数据成员, 必须将其声明为控件类中的数据成员。 控件类将不会从基类继承此数据成员, 因为它是在基类的联合中声明的。

##  <a name="m_bwindowonly"></a>CComControlBase::m_bWindowOnly

指示控件应为窗口的标志, 即使容器支持无窗口控件。

```
unsigned m_bWindowOnly:1;
```

### <a name="remarks"></a>备注

> [!NOTE]
>  若要在控件类中使用此数据成员, 必须将其声明为控件类中的数据成员。 控件类将不会从基类继承此数据成员, 因为它是在基类的联合中声明的。

##  <a name="m_bwndless"></a>CComControlBase::m_bWndLess

指示控件无窗口的标志。

```
unsigned m_bWndLess:1;
```

### <a name="remarks"></a>备注

> [!NOTE]
>  若要在控件类中使用此数据成员, 必须将其声明为控件类中的数据成员。 控件类将不会从基类继承此数据成员, 因为它是在基类的联合中声明的。

`m_spInPlaceSite`数据成员指向[IOleInPlaceSite](/windows/win32/api/oleidl/nn-oleidl-ioleinplacesite)、 [IOleInPlaceSiteEx](/windows/win32/api/ocidl/nn-ocidl-ioleinplacesiteex)或[IOleInPlaceSiteWindowless](/windows/win32/api/ocidl/nn-ocidl-ioleinplacesitewindowless) `m_bWndLess`接口, 具体取决于和[CComControlBase:: m_bInPlaceSiteEx](#m_binplacesiteex)标志的值。 (对于要有效的[CComControlBase:: m_spInPlaceSite](#m_spinplacesite)指针, 数据成员[CComControlBase:: M_BNEGOTIATEDWND](#m_bnegotiatedwnd)必须为 TRUE。)

如果`m_bWndLess`为 TRUE, `m_spInPlaceSite`则为`IOleInPlaceSiteWindowless`接口指针。 有关显示这些数据成员之间的完整关系的表, 请参阅[CComControlBase:: m_spInPlaceSite](#m_spinplacesite) 。

##  <a name="m_hwndcd"></a>CComControlBase::m_hWndCD

包含对与控件关联的窗口句柄的引用。

```
HWND& m_hWndCD;
```

### <a name="remarks"></a>备注

> [!NOTE]
>  若要在控件类中使用此数据成员, 必须将其声明为控件类中的数据成员。 控件类将不会从基类继承此数据成员, 因为它是在基类的联合中声明的。

##  <a name="m_nfreezeevents"></a>CComControlBase::m_nFreezeEvents

容器在不干预事件 (接受事件) 的情况下冻结事件 (拒绝接受事件) 的次数。

```
short m_nFreezeEvents;
```

### <a name="remarks"></a>备注

> [!NOTE]
>  若要在控件类中使用此数据成员, 必须将其声明为控件类中的数据成员。 控件类将不会从基类继承此数据成员, 因为它是在基类的联合中声明的。

##  <a name="m_rcpos"></a>CComControlBase::m_rcPos

控件的位置 (以像素为单位), 以容器的坐标表示。

```
RECT m_rcPos;
```

### <a name="remarks"></a>备注

> [!NOTE]
>  若要在控件类中使用此数据成员, 必须将其声明为控件类中的数据成员。 控件类将不会从基类继承此数据成员, 因为它是在基类的联合中声明的。

##  <a name="m_sizeextent"></a>CComControlBase::m_sizeExtent

对于特定显示, 以 HIMETRIC 单位 (每个单位为0.01 毫米) 的控件范围。

```
SIZE m_sizeExtent;
```

### <a name="remarks"></a>备注

> [!NOTE]
>  若要在控件类中使用此数据成员, 必须将其声明为控件类中的数据成员。 控件类将不会从基类继承此数据成员, 因为它是在基类的联合中声明的。

此大小由显示比例缩放。 控件的物理大小在`m_sizeNatural`数据成员中指定并且是固定的。

可以通过全局函数[AtlHiMetricToPixel](pixel-himetric-conversion-global-functions.md#atlhimetrictopixel)将大小转换为像素。

##  <a name="m_sizenatural"></a>CComControlBase::m_sizeNatural

控件的物理大小, 以 HIMETRIC 单位 (每个单位为0.01 毫米)。

```
SIZE m_sizeNatural;
```

### <a name="remarks"></a>备注

> [!NOTE]
>  若要在控件类中使用此数据成员, 必须将其声明为控件类中的数据成员。 控件类将不会从基类继承此数据成员, 因为它是在基类的联合中声明的。

此大小是固定的, 而中`m_sizeExtent`的大小则按显示比例缩放。

可以通过全局函数[AtlHiMetricToPixel](pixel-himetric-conversion-global-functions.md#atlhimetrictopixel)将大小转换为像素。

##  <a name="m_spadvisesink"></a>CComControlBase::m_spAdviseSink

指向容器上的通知连接的直接指针 (容器的[IAdviseSink](/windows/win32/api/objidl/nn-objidl-iadvisesink))。

```
CComPtr<IAdviseSink>
    m_spAdviseSink;
```

### <a name="remarks"></a>备注

> [!NOTE]
>  若要在控件类中使用此数据成员, 必须将其声明为控件类中的数据成员。 控件类将不会从基类继承此数据成员, 因为它是在基类的联合中声明的。

##  <a name="m_spambientdispatch"></a>CComControlBase::m_spAmbientDispatch

一个`CComDispatchDriver`对象, 它允许您`IDispatch`通过指针检索和设置对象的属性。

```
CComDispatchDriver m_spAmbientDispatch;
```

### <a name="remarks"></a>备注

> [!NOTE]
>  若要在控件类中使用此数据成员, 必须将其声明为控件类中的数据成员。 控件类将不会从基类继承此数据成员, 因为它是在基类的联合中声明的。

##  <a name="m_spclientsite"></a>CComControlBase::m_spClientSite

指向容器中控件的客户端站点的指针。

```
CComPtr<IOleClientSite>
    m_spClientSite;
```

### <a name="remarks"></a>备注

> [!NOTE]
>  若要在控件类中使用此数据成员, 必须将其声明为控件类中的数据成员。 控件类将不会从基类继承此数据成员, 因为它是在基类的联合中声明的。

##  <a name="m_spdataadviseholder"></a>CComControlBase::m_spDataAdviseHolder

提供用于在数据对象和通知接收器之间保存通知连接的标准方法。

```
CComPtr<IDataAdviseHolder>
    m_spDataAdviseHolder;
```

### <a name="remarks"></a>备注

> [!NOTE]
>  若要在控件类中使用此数据成员, 必须将其声明为控件类中的数据成员。 控件类将不会从基类继承此数据成员, 因为它是在基类的联合中声明的。

数据对象是一种可以传输数据并实现[IDataObject](/windows/win32/api/objidl/nn-objidl-idataobject)的控件, 其方法指定数据的格式和传输媒介。

接口`m_spDataAdviseHolder`实现[IDataObject::D advise](/windows/win32/api/objidl/nf-objidl-idataobject-dadvise)和[IDataObject::D unadvise](/windows/win32/api/objidl/nf-objidl-idataobject-dunadvise)方法, 建立和删除到容器的通知连接。 控件的容器必须支持[IAdviseSink](/windows/win32/api/objidl/nn-objidl-iadvisesink)接口, 才能实现一个通知接收器。

##  <a name="m_spinplacesite"></a>CComControlBase::m_spInPlaceSite

指向容器的[IOleInPlaceSite](/windows/win32/api/oleidl/nn-oleidl-ioleinplacesite)、 [IOleInPlaceSiteEx](/windows/win32/api/ocidl/nn-ocidl-ioleinplacesiteex)或[IOleInPlaceSiteWindowless](/windows/win32/api/ocidl/nn-ocidl-ioleinplacesitewindowless)接口指针的指针。

```
CComPtr<IOleInPlaceSiteWindowless>
    m_spInPlaceSite;
```

### <a name="remarks"></a>备注

> [!NOTE]
>  若要在控件类中使用此数据成员, 必须将其声明为控件类中的数据成员。 控件类将不会从基类继承此数据成员, 因为它是在基类的联合中声明的。

仅`m_spInPlaceSite`当[m_bNegotiatedWnd](#m_bnegotiatedwnd)标志为 TRUE 时, 指针才有效。

下表显示`m_spInPlaceSite`指针类型如何依赖于[m_bWndLess](#m_bwndless)和[m_bInPlaceSiteEx](#m_binplacesiteex)数据成员标志:

|m_spInPlaceSite Type|m_bWndLess 值|m_bInPlaceSiteEx 值|
|---------------------------|-----------------------|-----------------------------|
|`IOleInPlaceSiteWindowless`|TRUE|TRUE 或 FALSE|
|`IOleInPlaceSiteEx`|FALSE|TRUE|
|`IOleInPlaceSite`|FALSE|FALSE|

##  <a name="m_spoleadviseholder"></a>CComControlBase::m_spOleAdviseHolder

提供了一种用于保存咨询连接的标准实现方式。

```
CComPtr<IOleAdviseHolder>
    m_spOleAdviseHolder;
```

### <a name="remarks"></a>备注

> [!NOTE]
>  若要在控件类中使用此数据成员, 必须将其声明为控件类中的数据成员。 控件类将不会从基类继承此数据成员, 因为它是在基类的联合中声明的。

接口`m_spOleAdviseHolder`实现[IOleObject:: Advise](/windows/win32/api/oleidl/nf-oleidl-ioleobject-advise)和[IOleObject:: Unadvise](/windows/win32/api/oleidl/nf-oleidl-ioleobject-unadvise)方法, 以建立和删除到容器的通知连接。 控件的容器必须支持[IAdviseSink](/windows/win32/api/objidl/nn-objidl-iadvisesink)接口, 才能实现一个通知接收器。

##  <a name="ondraw"></a>CComControlBase:: OnDraw

重写此方法以绘制控件。

```
virtual HRESULT OnDraw(ATL_DRAWINFO& di);
```

### <a name="parameters"></a>参数

*di*<br/>
对[ATL_DRAWINFO](../../atl/reference/atl-drawinfo-structure.md)结构的引用, 该结构包含绘制方位、控件边界以及绘图是否经过优化。

### <a name="return-value"></a>返回值

标准的 HRESULT 值。

### <a name="remarks"></a>备注

默认情况`OnDraw`下, 会删除或还原设备上下文, 或不执行任何操作, 具体取决于在[CComControlBase:: OnDrawAdvanced](#ondrawadvanced)中设置的标志。

使用`OnDraw` ATL 控件向导创建控件时, 会自动将一个方法添加到控件类中。 向导的默认值`OnDraw`绘制一个带有 "ATL 8.0" 标签的矩形。

### <a name="example"></a>示例

请参阅[CComControlBase:: GetAmbientAppearance](#getambientappearance)的示例。

##  <a name="ondrawadvanced"></a>CComControlBase::OnDrawAdvanced

默认情况`OnDrawAdvanced`下, 准备用于绘制的规范化设备上下文, 然后调用控件类`OnDraw`的方法。

```
virtual HRESULT OnDrawAdvanced(ATL_DRAWINFO& di);
```

### <a name="parameters"></a>参数

*di*<br/>
对[ATL_DRAWINFO](../../atl/reference/atl-drawinfo-structure.md)结构的引用, 该结构包含绘制方位、控件边界以及绘图是否经过优化。

### <a name="return-value"></a>返回值

标准的 HRESULT 值。

### <a name="remarks"></a>备注

如果要接受由容器传递的设备上下文而不对其进行规范化, 请重写此方法。

有关更多详细信息, 请参阅[CComControlBase:: OnDraw](#ondraw) 。

##  <a name="onkillfocus"></a>CComControlBase::OnKillFocus

检查控件是否处于就地活动状态并具有有效的控制站点, 然后通知容器控件已失去焦点。

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
指示是否已成功处理窗口消息的标志。 默认值为 FALSE。

### <a name="return-value"></a>返回值

始终返回1。

##  <a name="onmouseactivate"></a>CComControlBase::OnMouseActivate

检查 UI 是否处于用户模式, 然后激活控件。

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
指示是否已成功处理窗口消息的标志。 默认值为 FALSE。

### <a name="return-value"></a>返回值

始终返回1。

##  <a name="onpaint"></a>CComControlBase:: OnPaint

准备用于绘制的容器, 获取该控件的工作区, 然后调用该控件类的`OnDrawAdvanced`方法。

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

如果*wParam*不为 NULL, `OnPaint`则假定它包含有效的 HDC, 并使用它而不是[CComControlBase:: m_hWndCD](#m_hwndcd)。

##  <a name="onsetfocus"></a>CComControlBase:: OnSetFocus

检查控件是否处于就地活动状态并具有有效的控制站点, 然后通知容器控件已获得焦点。

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
指示是否已成功处理窗口消息的标志。 默认值为 FALSE。

### <a name="return-value"></a>返回值

始终返回1。

### <a name="remarks"></a>备注

将通知发送到控件已接收到焦点的容器。

##  <a name="pretranslateaccelerator"></a>CComControlBase::P reTranslateAccelerator

重写此方法以提供您自己的键盘快捷键处理程序。

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

默认情况下, 返回 FALSE。

##  <a name="sendonclose"></a>CComControlBase::SendOnClose

通知所有注册了通知持有人的通知接收器控件已关闭。

```
HRESULT SendOnClose();
```

### <a name="return-value"></a>返回值

如果成功, 则返回 S_OK, 否则返回错误 HRESULT。

### <a name="remarks"></a>备注

发送通知, 指示控件已关闭其通知接收器。

##  <a name="sendondatachange"></a>CComControlBase::SendOnDataChange

通知所有注册了通知持有人的通知接收器控制数据已更改。

```
HRESULT SendOnDataChange(DWORD advf = 0);
```

### <a name="parameters"></a>参数

*advf*<br/>
指定对[IAdviseSink:: OnDataChange](/windows/win32/api/objidl/nf-objidl-iadvisesink-ondatachange)的调用方式的建议标志。 值来自[ADVF](/windows/win32/api/objidl/ne-objidl-advf)枚举。

### <a name="return-value"></a>返回值

如果成功, 则返回 S_OK, 否则返回错误 HRESULT。

##  <a name="sendonrename"></a>CComControlBase::SendOnRename

通知所有注册了通知持有人的通知接收器控件都有一个新的名字对象。

```
HRESULT SendOnRename(IMoniker* pmk);
```

### <a name="parameters"></a>参数

*pmk*<br/>
指向控件的新名字对象的指针。

### <a name="return-value"></a>返回值

如果成功, 则返回 S_OK, 否则返回错误 HRESULT。

### <a name="remarks"></a>备注

发送通知, 指示控件的名字对象已更改。

##  <a name="sendonsave"></a>CComControlBase::SendOnSave

通知所有注册了通知持有人的通知接收器已保存控件。

```
HRESULT SendOnSave();
```

### <a name="return-value"></a>返回值

如果成功, 则返回 S_OK, 否则返回错误 HRESULT。

### <a name="remarks"></a>备注

发送控件刚刚保存其数据的通知。

##  <a name="sendonviewchange"></a>CComControlBase::SendOnViewChange

通知所有已注册的通知接收器控件的视图已更改。

```
HRESULT SendOnViewChange(DWORD dwAspect, LONG lindex = -1);
```

### <a name="parameters"></a>参数

*dwAspect*<br/>
控件的方位或视图。

*lindex*<br/>
视图中已更改的部分。 仅-1 有效。

### <a name="return-value"></a>返回值

如果成功, 则返回 S_OK, 否则返回错误 HRESULT。

### <a name="remarks"></a>备注

`SendOnViewChange`调用[IAdviseSink:: OnViewChange](/windows/win32/api/objidl/nf-objidl-iadvisesink-onviewchange)。 当前支持的*lindex*值为-1, 指示整个视图是相关的。

##  <a name="setcontrolfocus"></a>CComControlBase::SetControlFocus

设置或删除控件中的键盘焦点。

```
BOOL SetControlFocus(BOOL bGrab);
```

### <a name="parameters"></a>参数

*bGrab*<br/>
如果为 TRUE, 则将键盘焦点设置到调用控件。 如果为 FALSE, 则在调用控件中删除键盘焦点 (前提是它有焦点)。

### <a name="return-value"></a>返回值

如果控件成功接收焦点, 则返回 TRUE;否则为 FALSE。

### <a name="remarks"></a>备注

对于有窗口的控件, 将调用 Windows API 函数[SetFocus](/windows/win32/api/winuser/nf-winuser-setfocus) 。 对于无窗口控件, 将调用[IOleInPlaceSiteWindowless:: SetFocus](/windows/win32/api/ocidl/nf-ocidl-ioleinplacesitewindowless-setfocus) 。 通过此调用, 无窗口控件获取键盘焦点并可以响应窗口消息。

##  <a name="setdirty"></a>CComControlBase::SetDirty

将数据成员`m_bRequiresSave`设置为*bDirty*中的值。

```
void SetDirty(BOOL bDirty);
```

### <a name="parameters"></a>参数

*bDirty*<br/>
数据成员[CComControlBase:: m_bRequiresSave](#m_brequiressave)的值。

### <a name="remarks"></a>备注

`SetDirty(TRUE)`应调用以标志控件自上次保存后已发生更改。 的值`m_bRequiresSave`是用[CComControlBase:: GetDirty](#getdirty)检索的。

## <a name="see-also"></a>请参阅

[CComControl 类](../../atl/reference/ccomcontrol-class.md)<br/>
[类概述](../../atl/atl-class-overview.md)
