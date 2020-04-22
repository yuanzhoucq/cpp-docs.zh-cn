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
ms.openlocfilehash: 15cfa205337248181f02e6a1218d49e75bda58e6
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/22/2020
ms.locfileid: "81748112"
---
# <a name="ccomcontrolbase-class"></a>CComControlBase 类

此类提供用于创建和管理 ATL 控件的方法。

> [!IMPORTANT]
> 此类及其成员不能在 Windows 运行时中执行的应用程序中使用。

## <a name="syntax"></a>语法

```
class ATL_NO_VTABLE CComControlBase
```

## <a name="members"></a>成员

### <a name="public-typedefs"></a>公共 Typedef

|名称|说明|
|----------|-----------------|
|[CCom 控制库：外观类型](#appearancetype)|如果`m_nAppearance`股票属性不是**短**型，请覆盖。|

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[CCom控制库：CCom控制库](#ccomcontrolbase)|构造函数。|
|[CCom 控制库：*CCom控制库](#dtor)|析构函数。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CCom 控制库：：控制查询接口](#controlqueryinterface)|检索指向所请求的接口的指针。|
|[CComControlBase：:DesVerb激活](#doesverbactivate)|检查`IOleObjectImpl::DoVerb`所使用的*iVerb*参数是否激活控件的用户界面 *（iVerb*等于OLEIVERB_UIACTIVATE），定义用户双击控件时执行的操作 *（iVerb*等于OLEIVERB_PRIMARY）、显示控件 *（iVerb*等于OLEIVERB_SHOW）或激活控件 *（iVerb*等于OLEIVERB_INPLACEACTIVATE）。|
|[CComControlBase：:DesVerbUI激活](#doesverbuiactivate)|检查 所使用的`IOleObjectImpl::DoVerb` *iVerb*参数是否导致控件的用户界面激活并返回 TRUE。|
|[CComControlBase：:DoVerb属性](#doverbproperties)|显示控件的属性页。|
|[CCom 控制库：：火视图更改](#fireviewchange)|调用此方法告诉容器重新绘制控件，或通知已注册的通知接收器控件的视图已更改。|
|[CComControlBase：获取环境外观](#getambientappearance)|检索DISPID_AMBIENT_APPEARANCE，控件的当前外观设置为：0 表示平面，1 表示 3D。|
|[CCom 控制库：获取环境自动剪辑](#getambientautoclip)|检索DISPID_AMBIENT_AUTOCLIP，指示容器是否支持自动剪切控件显示区域的标志。|
|[CCom 控制库：获取环境背面颜色](#getambientbackcolor)|检索DISPID_AMBIENT_BACKCOLOR，即容器定义的所有控件的环境背景颜色。|
|[CComControlBase：获取环境字符集](#getambientcharset)|检索DISPID_AMBIENT_CHARSET，即由容器定义的所有控件的环境字符集。|
|[CCom 控制库：获取环境码页](#getambientcodepage)|检索DISPID_AMBIENT_CODEPAGE，即由容器定义的所有控件的环境字符集。|
|[CCom 控制库：获取环境显示作为默认](#getambientdisplayasdefault)|检索DISPID_AMBIENT_DISPLAYASDEFAULT，如果容器将此站点中的控件标记为默认按钮，则该标志为 TRUE，因此按钮控件应使用较粗的框架绘制自身。|
|[CCom 控制库：获取环境显示名称](#getambientdisplayname)|检索DISPID_AMBIENT_DISPLAYNAME，容器提供给控件的名称。|
|[CComControlBase：获取环境字体](#getambientfont)|检索指向容器环境`IFont`接口的指针。|
|[CComControlBase：获取环境方迪普](#getambientfontdisp)|检索指向容器的环境`IFontDisp`调度接口的指针。|
|[CComControlBase：获取环境福彩](#getambientforecolor)|检索DISPID_AMBIENT_FORECOLOR，即容器定义的所有控件的环境前景颜色。|
|[CComControlBase：获取环境区域ID](#getambientlocaleid)|检索容器使用的语言的DISPID_AMBIENT_LOCALEID标识符。|
|[CComControlBase：获取环境信息反射](#getambientmessagereflect)|检索DISPID_AMBIENT_MESSAGEREFLECT，一个指示容器是否要接收窗口消息（如WM_DRAWITEM）作为事件的标志。|
|[CCom 控制库：获取环境调色板](#getambientpalette)|检索用于访问容器的 HPALETTE 的DISPID_AMBIENT_PALETTE。|
|[CComControlBase：获取环境属性](#getambientproperty)|检索*id*指定的容器属性。|
|[CCom 控制库：获取环境右到左侧](#getambientrighttoleft)|检索DISPID_AMBIENT_RIGHTTOLEFT，容器显示内容的方向。|
|[CCom 控制库：获取环境规模单位](#getambientscaleunits)|检索DISPID_AMBIENT_SCALEUNITS，容器的环境单位（如英寸或厘米）用于标记显示。|
|[CCom 控制库：获取环境显示抓手](#getambientshowgrabhandles)|检索DISPID_AMBIENT_SHOWGRABHANDLES，一个标志指示容器是否允许控件在活动时显示自身的抓取控点。|
|[CCom 控制库：获取环境显示填充](#getambientshowhatching)|检索DISPID_AMBIENT_SHOWHATCHING，一个标志，指示容器是否允许控件在 UI 处于活动状态时使用阴影模式显示自身。|
|[CComControlBase：获取环境支持Mnemonic](#getambientsupportsmnemonics)|检索DISPID_AMBIENT_SUPPORTSMNEMONICS，一个指示容器是否支持键盘助记符的标志。|
|[CComControlBase：获取环境文本对齐](#getambienttextalign)|检索DISPID_AMBIENT_TEXTALIGN、容器首选的文本对齐：0 表示一般对齐（数字右侧，文本左侧），左对齐为 1，中心对齐为 2，右对齐为 3。|
|[CCom 控制库：获取环境顶底](#getambienttoptobottom)|检索DISPID_AMBIENT_TOPTOBOTTOM，容器显示内容的方向。|
|[CComControlBase：获取环境UI死](#getambientuidead)|检索DISPID_AMBIENT_UIDEAD，指示容器是否希望控件响应用户界面操作的标志。|
|[CCom 控制库：获取环境用户模式](#getambientusermode)|检索DISPID_AMBIENT_USERMODE，指示容器处于运行模式 （TRUE） 还是设计模式 （FALSE） 的标志。|
|[CComControlBase：获取脏](#getdirty)|返回数据成员`m_bRequiresSave`的值。|
|[CComControlBase：获取Zoominfo](#getzoominfo)|检索为就地编辑而激活的控件的缩放因子的分子和分母的 x 和 y 值。|
|[CCom 控制库：就地激活](#inplaceactivate)|使控件从非活动状态转换为*iVerb*中动词指示的任何状态。|
|[CComControlBase：内部获取网站](#internalgetsite)|调用此方法以查询控件站点以寻找指向已标识接口的指针。|
|[CComControlBase：ONDraw](#ondraw)|重写此方法以绘制控件。|
|[CComControlBase：OnDraw高级](#ondrawadvanced)|默认值`OnDrawAdvanced`为绘图准备规范化的设备上下文，然后调用控件类`OnDraw`的方法。|
|[CComControlBase：：在基尔焦点上](#onkillfocus)|检查控件是否就地处于活动状态，并且具有有效的控制站点，然后通知容器控件已失去焦点。|
|[CComControlBase：鼠标激活](#onmouseactivate)|检查 UI 是否处于用户模式，然后激活控件。|
|[CComControlBase：：上漆](#onpaint)|准备容器进行绘制，获取控件的工作区，然后调用控件类`OnDraw`的方法。|
|[CComControlBase：关于焦点](#onsetfocus)|检查控件是否就地处于活动状态，并且具有有效的控制站点，然后通知容器控件已获得焦点。|
|[CComControlBase：:P重新翻译加速器](#pretranslateaccelerator)|重写此方法以提供您自己的键盘快捷键处理程序。|
|[CCom 控制库：：发送关闭](#sendonclose)|通知在通知持有人登记的所有通知接收器，该控制已关闭。|
|[CCom 控制库：：发送数据更改](#sendondatachange)|通知向通知持有人注册的所有通知接收器控制数据已更改。|
|[CCom 控制库：：发送重新命名](#sendonrename)|通知所有在通知持有人登记的咨询接收器，该控制具有新的名字。|
|[CCom 控制库：：发送保存](#sendonsave)|通知向通知持有人登记的所有通知接收器，该控制已保存。|
|[CCom 控制库：：发送视图更改](#sendonviewchange)|通知所有已注册的通知接收器控件的视图已更改。|
|[CCom 控制库：设置控制焦点](#setcontrolfocus)|设置或移除键盘对焦到控件或从控件。|
|[CCom 控制库：：设置脏](#setdirty)|将数据成员`m_bRequiresSave`设置为*bDirty*中的值。|

### <a name="public-data-members"></a>公共数据成员

|名称|说明|
|----------|-----------------|
|[CComControlBase：m_bAutoSize](#m_bautosize)|指示控件的标志不能是任何其他大小。|
|[CComControlBase：m_bDrawFromNatural](#m_bdrawfromnatural)|指示 和`IDataObjectImpl::GetData``CComControlBase::GetZoomInfo`应从 而不是 从`m_sizeNatural``m_sizeExtent`设置控件大小的标志。|
|[CCom控制库：m_bDrawGetDataInHimetric](#m_bdrawgetdatainhimetric)|指示绘制时`IDataObjectImpl::GetData`应使用 HIMETRIC 单位而不是像素的标志。|
|[CComControlBase：m_bInPlaceActive](#m_binplaceactive)|指示控件已就地处于活动状态的标志。|
|[CComControlBase：m_bInPlaceSiteEx](#m_binplacesiteex)|指示容器的标志支持`IOleInPlaceSiteEx`接口和 OCX96 控制功能，如无窗口和无闪烁控件。|
|[CCom 控制库：：m_bNegotiatedWnd](#m_bnegotiatedwnd)|指示控件是否已与容器协商支持 OCX96 控制功能（如无闪烁和无窗口控件）以及控件是窗口还是无窗口。|
|[CComControlBase：m_bRecomposeOnResize](#m_brecomposeonresize)|指示控件的标志希望在容器更改控件的显示大小时重新调整其演示文稿。|
|[CComControlBase：m_bRequiresSave](#m_brequiressave)|指示控件自上次保存以来已更改的标志。|
|[CComControlBase：m_bResizeNatural](#m_bresizenatural)|指示控件的标志希望在容器更改控件的显示大小时调整其自然范围（其未缩放的物理大小）。|
|[CComControlBase：m_bUIActive](#m_buiactive)|指示控件用户界面（如菜单和工具栏）的标志处于活动状态。|
|[CCom 控制库：：m_bUsingWindowRgn](#m_busingwindowrgn)|指示控件正在使用容器提供的窗口区域的标志。|
|[CCom控制库：m_bWasOnceWindowless](#m_bwasoncewindowless)|指示控件已无窗口的标志，但现在可能已无窗口，也可能不是无窗口。|
|[CComControlBase：m_bWindowOnly](#m_bwindowonly)|指示控件的标志应窗口，即使容器支持无窗口控件也是如此。|
|[CComControlBase：m_bWndLess](#m_bwndless)|指示控件无窗口的标志。|
|[CComControlBase：m_hWndCD](#m_hwndcd)|包含对与控件关联的窗口句柄的引用。|
|[CComControlBase：m_nFreezeEvents](#m_nfreezeevents)|计算容器冻结事件（拒绝接受事件）的次数，而不干预事件解冻（接受事件）。|
|[CComControlBase：m_rcPos](#m_rcpos)|控件的像素位置，以容器的坐标表示。|
|[CComControlBase：m_sizeExtent](#m_sizeextent)|特定显示器的控制范围（以 HIMETRIC 单位为单位（每个单位为 0.01 毫米）。|
|[CComControlBase：m_sizeNatural](#m_sizenatural)|以 HIMETRIC 单位（每个单位为 0.01 毫米）的控制的物理大小。|
|[CComControlBase：m_spAdviseSink](#m_spadvisesink)|指向容器上的咨询连接的直接指针（容器的[IAdviseSink）。](/windows/win32/api/objidl/nn-objidl-iadvisesink)|
|[CComControlBase：m_spAmbientDispatch](#m_spambientdispatch)|一`CComDispatchDriver`个对象，允许您通过`IDispatch`指针检索和设置容器的属性。|
|[CComControlBase：m_spClientSite](#m_spclientsite)|指向容器中控件的客户端站点的指针。|
|[CComControlBase：m_spDataAdviseHolder](#m_spdataadviseholder)|提供一种标准方法，用于在数据对象和通知接收器之间保持咨询连接。|
|[CCom控制库：m_spInPlaceSite](#m_spinplacesite)|指向容器的[IOleInPlaceSite、IOleInPlaceSiteEx](/windows/win32/api/oleidl/nn-oleidl-ioleinplacesite)或[IOleInPlace无窗口](/windows/win32/api/ocidl/nn-ocidl-ioleinplacesitewindowless)接口指针的指针。 [IOleInPlaceSiteEx](/windows/win32/api/ocidl/nn-ocidl-ioleinplacesiteex)|
|[CComControlBase：m_spOleAdviseHolder](#m_spoleadviseholder)|提供保存咨询连接的方法的标准实现。|

## <a name="remarks"></a>备注

此类提供用于创建和管理 ATL 控件的方法。 [CComControl 类](../../atl/reference/ccomcontrol-class.md)派生自`CComControlBase`。 使用 ATL 控件向导创建标准控件或 DHTML 控件时，向导将自动从`CComControlBase`派生类。

有关创建控件的详细信息，请参阅[ATL 教程](../../atl/active-template-library-atl-tutorial.md)。 有关 ATL 项目向导的详细信息，请参阅创建[ATL 项目](../../atl/reference/creating-an-atl-project.md)的文章。

## <a name="requirements"></a>要求

**标题：** atlctl.h

## <a name="ccomcontrolbaseappearancetype"></a><a name="appearancetype"></a>CCom 控制库：外观类型

如果`m_nAppearance`股票属性不是**短**型，请覆盖。

```
typedef short AppearanceType;
```

### <a name="remarks"></a>备注

ATL 控制向导添加`m_nAppearance`短型的股票属性。 如果使用`AppearanceType`其他数据类型，则覆盖。

## <a name="ccomcontrolbaseccomcontrolbase"></a><a name="ccomcontrolbase"></a>CCom控制库：CCom控制库

构造函数。

```
CComControlBase(HWND& h);
```

### <a name="parameters"></a>参数

*H*<br/>
与控件关联的窗口的句柄。

### <a name="remarks"></a>备注

将控制大小初始化为 5080X5080 HIMETRIC 单位（2"X2"），并将`CComControlBase`数据成员值初始化为 NULL 或 FALSE。

## <a name="ccomcontrolbaseccomcontrolbase"></a><a name="dtor"></a>CCom 控制库：*CCom控制库

析构函数。

```
~CComControlBase();
```

### <a name="remarks"></a>备注

如果控件是窗口的，则`~CComControlBase`通过调用["销毁窗口"](/windows/win32/api/winuser/nf-winuser-destroywindow)来销毁它。

## <a name="ccomcontrolbasecontrolqueryinterface"></a><a name="controlqueryinterface"></a>CCom 控制库：：控制查询接口

检索指向所请求的接口的指针。

```
virtual HRESULT ControlQueryInterface(const IID& iid,
    void** ppv);
```

### <a name="parameters"></a>参数

*Iid*<br/>
请求的接口的 GUID。

*Ppv*<br/>
指向*iid*标识的接口指针，如果找不到接口，则指向 NULL 的指针。

### <a name="remarks"></a>备注

仅处理 COM 地图表中的接口。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_COM#15](../../atl/codesnippet/cpp/ccomcontrolbase-class_1.cpp)]

## <a name="ccomcontrolbasedoesverbactivate"></a><a name="doesverbactivate"></a>CComControlBase：:DesVerb激活

检查`IOleObjectImpl::DoVerb`所使用的*iVerb*参数是否激活控件的用户界面 *（iVerb*等于OLEIVERB_UIACTIVATE），定义用户双击控件时执行的操作 *（iVerb*等于OLEIVERB_PRIMARY）、显示控件 *（iVerb*等于OLEIVERB_SHOW）或激活控件 *（iVerb*等于OLEIVERB_INPLACEACTIVATE）。

```
BOOL DoesVerbActivate(LONG iVerb);
```

### <a name="parameters"></a>参数

*iVerb*<br/>
指示要执行的操作`DoVerb`的值。

### <a name="return-value"></a>返回值

如果*iVerb*等于OLEIVERB_UIACTIVATE、OLEIVERB_PRIMARY、OLEIVERB_SHOW 或OLEIVERB_INPLACEACTIVATE，则返回 TRUE;否则，返回 FALSE。

### <a name="remarks"></a>备注

您可以重写此方法来定义自己的激活谓词。

## <a name="ccomcontrolbasedoesverbuiactivate"></a><a name="doesverbuiactivate"></a>CComControlBase：:DesVerbUI激活

检查 所使用的`IOleObjectImpl::DoVerb` *iVerb*参数是否导致控件的用户界面激活并返回 TRUE。

```
BOOL DoesVerbUIActivate(LONG iVerb);
```

### <a name="parameters"></a>参数

*iVerb*<br/>
指示要执行的操作`DoVerb`的值。

### <a name="return-value"></a>返回值

如果*iVerb*等于OLEIVERB_UIACTIVATE、OLEIVERB_PRIMARY、OLEIVERB_SHOW 或OLEIVERB_INPLACEACTIVATE，则返回 TRUE。 否则，该方法将返回 FALSE。

## <a name="ccomcontrolbasedoverbproperties"></a><a name="doverbproperties"></a>CComControlBase：:DoVerb属性

显示控件的属性页。

```
HRESULT DoVerbProperties(LPCRECT /* prcPosRect */, HWND hwndParent);
```

### <a name="parameters"></a>参数

*prcPosRec*<br/>
保留。

*hwnd 家长*<br/>
包含控件的窗口的句柄。

### <a name="return-value"></a>返回值

标准 HRESULT 值之一。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_COM#19](../../atl/codesnippet/cpp/ccomcontrolbase-class_2.cpp)]

[!code-cpp[NVC_ATL_COM#20](../../atl/codesnippet/cpp/ccomcontrolbase-class_3.h)]

## <a name="ccomcontrolbasefireviewchange"></a><a name="fireviewchange"></a>CCom 控制库：：火视图更改

调用此方法告诉容器重新绘制控件，或通知已注册的通知接收器控件的视图已更改。

```
HRESULT FireViewChange();
```

### <a name="return-value"></a>返回值

标准 HRESULT 值之一。

### <a name="remarks"></a>备注

如果控件处于活动状态（控件类数据成员[CComControlBase：：m_bInPlaceActive](#m_binplaceactive)为 TRUE），则通知要重绘整个控件的容器。 如果控件处于非活动状态，则通知控件的已注册通知接收器（通过控件类数据成员[CComControlBase：：m_spAdviseSink）](#m_spadvisesink)该控件的视图已更改。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_COM#21](../../atl/codesnippet/cpp/ccomcontrolbase-class_4.cpp)]

## <a name="ccomcontrolbasegetambientappearance"></a><a name="getambientappearance"></a>CComControlBase：获取环境外观

检索DISPID_AMBIENT_APPEARANCE，控件的当前外观设置为：0 表示平面，1 表示 3D。

```
HRESULT GetAmbientAppearance(short& nAppearance);
```

### <a name="parameters"></a>参数

*n 外观*<br/>
该属性DISPID_AMBIENT_APPEARANCE。

### <a name="return-value"></a>返回值

标准 HRESULT 值之一。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_COM#22](../../atl/codesnippet/cpp/ccomcontrolbase-class_5.h)]

## <a name="ccomcontrolbasegetambientautoclip"></a><a name="getambientautoclip"></a>CCom 控制库：获取环境自动剪辑

检索DISPID_AMBIENT_AUTOCLIP，指示容器是否支持自动剪切控件显示区域的标志。

```
HRESULT GetAmbientAutoClip(BOOL& bAutoClip);
```

### <a name="parameters"></a>参数

*b自动剪辑*<br/>
属性DISPID_AMBIENT_AUTOCLIP。

### <a name="return-value"></a>返回值

标准 HRESULT 值之一。

## <a name="ccomcontrolbasegetambientbackcolor"></a><a name="getambientbackcolor"></a>CCom 控制库：获取环境背面颜色

检索DISPID_AMBIENT_BACKCOLOR，即容器定义的所有控件的环境背景颜色。

```
HRESULT GetAmbientBackColor(OLE_COLOR& BackColor);
```

### <a name="parameters"></a>参数

*背面颜色*<br/>
该物业DISPID_AMBIENT_BACKCOLOR。

### <a name="return-value"></a>返回值

标准 HRESULT 值之一。

## <a name="ccomcontrolbasegetambientcharset"></a><a name="getambientcharset"></a>CComControlBase：获取环境字符集

检索DISPID_AMBIENT_CHARSET，即由容器定义的所有控件的环境字符集。

```
HRESULT GetAmbientCharSet(BSTR& bstrCharSet);
```

### <a name="parameters"></a>参数

*bstrCharSet*<br/>
属性DISPID_AMBIENT_CHARSET。

### <a name="return-value"></a>返回值

返回成功S_OK，或失败时返回错误 HRESULT。

## <a name="ccomcontrolbasegetambientcodepage"></a><a name="getambientcodepage"></a>CCom 控制库：获取环境码页

检索DISPID_AMBIENT_CODEPAGE，即容器定义的所有控件的环境代码页。

```
HRESULT GetAmbientCodePage(ULONG& ulCodePage);
```

### <a name="parameters"></a>参数

*ulCodepage*<br/>
该物业DISPID_AMBIENT_CODEPAGE。

### <a name="return-value"></a>返回值

返回成功S_OK，或失败时返回错误 HRESULT。

## <a name="ccomcontrolbasegetambientdisplayasdefault"></a><a name="getambientdisplayasdefault"></a>CCom 控制库：获取环境显示作为默认

检索DISPID_AMBIENT_DISPLAYASDEFAULT，如果容器将此站点中的控件标记为默认按钮，则该标志为 TRUE，因此按钮控件应使用较粗的框架绘制自身。

```
HRESULT GetAmbientDisplayAsDefault(BOOL& bDisplayAsDefault);
```

### <a name="parameters"></a>参数

*b 显示默认*<br/>
属性DISPID_AMBIENT_DISPLAYASDEFAULT。

### <a name="return-value"></a>返回值

标准 HRESULT 值之一。

## <a name="ccomcontrolbasegetambientdisplayname"></a><a name="getambientdisplayname"></a>CCom 控制库：获取环境显示名称

检索DISPID_AMBIENT_DISPLAYNAME，容器提供给控件的名称。

```
HRESULT GetAmbientDisplayName(BSTR& bstrDisplayName);
```

### <a name="parameters"></a>参数

*bstrDisplay名称*<br/>
该物业DISPID_AMBIENT_DISPLAYNAME。

### <a name="return-value"></a>返回值

标准 HRESULT 值之一。

## <a name="ccomcontrolbasegetambientfont"></a><a name="getambientfont"></a>CComControlBase：获取环境字体

检索指向容器环境`IFont`接口的指针。

```
HRESULT GetAmbientFont(IFont** ppFont);
```

### <a name="parameters"></a>参数

*ppFont*<br/>
指向容器环境[IFont](/windows/win32/api/ocidl/nn-ocidl-ifont)接口的指针。

### <a name="return-value"></a>返回值

标准 HRESULT 值之一。

### <a name="remarks"></a>备注

如果属性为 NULL，则指针为 NULL。 如果指针不是 NULL，则调用方必须释放指针。

## <a name="ccomcontrolbasegetambientfontdisp"></a><a name="getambientfontdisp"></a>CComControlBase：获取环境方迪普

检索指向容器的环境`IFontDisp`调度接口的指针。

```
HRESULT GetAmbientFontDisp(IFontDisp** ppFont);
```

### <a name="parameters"></a>参数

*ppFont*<br/>
指向容器的环境[IFontDisp](/windows/win32/api/ocidl/nn-ocidl-ifontdisp)调度接口的指针。

### <a name="return-value"></a>返回值

返回成功S_OK，或失败时返回错误 HRESULT。

### <a name="remarks"></a>备注

如果属性为 NULL，则指针为 NULL。 如果指针不是 NULL，则调用方必须释放指针。

## <a name="ccomcontrolbasegetambientforecolor"></a><a name="getambientforecolor"></a>CComControlBase：获取环境福彩

检索DISPID_AMBIENT_FORECOLOR，即容器定义的所有控件的环境前景颜色。

```
HRESULT GetAmbientForeColor(OLE_COLOR& ForeColor);
```

### <a name="parameters"></a>参数

*前色*<br/>
该物业DISPID_AMBIENT_FORECOLOR。

### <a name="return-value"></a>返回值

标准 HRESULT 值之一。

## <a name="ccomcontrolbasegetambientlocaleid"></a><a name="getambientlocaleid"></a>CComControlBase：获取环境区域ID

检索容器使用的语言的DISPID_AMBIENT_LOCALEID标识符。

```
HRESULT GetAmbientLocaleID(LCID& lcid);
```

### <a name="parameters"></a>参数

*lcid*<br/>
该物业DISPID_AMBIENT_LOCALEID。

### <a name="return-value"></a>返回值

标准 HRESULT 值之一。

### <a name="remarks"></a>备注

控件可以使用此标识符将其用户界面调整到不同的语言。

## <a name="ccomcontrolbasegetambientmessagereflect"></a><a name="getambientmessagereflect"></a>CComControlBase：获取环境信息反射

检索DISPID_AMBIENT_MESSAGEREFLECT，一个指示容器是否要接收窗口消息（如`WM_DRAWITEM`）作为事件的标志。

```
HRESULT GetAmbientMessageReflect(BOOL& bMessageReflect);
```

### <a name="parameters"></a>参数

*b消息反射*<br/>
该物业DISPID_AMBIENT_MESSAGEREFLECT。

### <a name="return-value"></a>返回值

标准 HRESULT 值之一。

## <a name="ccomcontrolbasegetambientpalette"></a><a name="getambientpalette"></a>CCom 控制库：获取环境调色板

检索用于访问容器的 HPALETTE 的DISPID_AMBIENT_PALETTE。

```
HRESULT GetAmbientPalette(HPALETTE& hPalette);
```

### <a name="parameters"></a>参数

*hPalette*<br/>
该物业DISPID_AMBIENT_PALETTE。

### <a name="return-value"></a>返回值

标准 HRESULT 值之一。

## <a name="ccomcontrolbasegetambientproperty"></a><a name="getambientproperty"></a>CComControlBase：获取环境属性

检索*由 dispid*指定的容器属性。

```
HRESULT GetAmbientProperty(DISPID dispid, VARIANT& var);
```

### <a name="parameters"></a>参数

*不一部分*<br/>
要检索的容器属性的标识符。

*var*<br/>
要接收属性的变量。

### <a name="return-value"></a>返回值

标准 HRESULT 值之一。

### <a name="remarks"></a>备注

ATL 提供了一组帮助程序函数来检索特定属性，例如[CComControlBase：：获取环境返回颜色](#getambientbackcolor)。 如果没有合适的方法可用，请使用`GetAmbientProperty`。

## <a name="ccomcontrolbasegetambientrighttoleft"></a><a name="getambientrighttoleft"></a>CCom 控制库：获取环境右到左侧

检索DISPID_AMBIENT_RIGHTTOLEFT，容器显示内容的方向。

```
HRESULT GetAmbientRightToLeft(BOOL& bRightToLeft);
```

### <a name="parameters"></a>参数

*bRighttoLeft*<br/>
该属性DISPID_AMBIENT_RIGHTTOLEFT。 如果内容从右向左显示，则设置为 TRUE;如果内容从左到右显示，则为 FALSE。

### <a name="return-value"></a>返回值

返回成功S_OK，或失败时返回错误 HRESULT。

## <a name="ccomcontrolbasegetambientscaleunits"></a><a name="getambientscaleunits"></a>CCom 控制库：获取环境规模单位

检索DISPID_AMBIENT_SCALEUNITS，容器的环境单位（如英寸或厘米）用于标记显示。

```
HRESULT GetAmbientScaleUnits(BSTR& bstrScaleUnits);
```

### <a name="parameters"></a>参数

*bstrScale单位*<br/>
该物业DISPID_AMBIENT_SCALEUNITS。

### <a name="return-value"></a>返回值

标准 HRESULT 值之一。

## <a name="ccomcontrolbasegetambientshowgrabhandles"></a><a name="getambientshowgrabhandles"></a>CCom 控制库：获取环境显示抓手

检索DISPID_AMBIENT_SHOWGRABHANDLES，一个标志指示容器是否允许控件在活动时显示自身的抓取控点。

```
HRESULT GetAmbientShowGrabHandles(BOOL& bShowGrabHandles);
```

### <a name="parameters"></a>参数

*b 显示GrabHandles*<br/>
该物业DISPID_AMBIENT_SHOWGRABHANDLES。

### <a name="return-value"></a>返回值

标准 HRESULT 值之一。

## <a name="ccomcontrolbasegetambientshowhatching"></a><a name="getambientshowhatching"></a>CCom 控制库：获取环境显示填充

检索DISPID_AMBIENT_SHOWHATCHING，一个标志，指示容器是否允许控件在控件的用户界面处于活动状态时使用阴影模式显示自身。

```
HRESULT GetAmbientShowHatching(BOOL& bShowHatching);
```

### <a name="parameters"></a>参数

*b 显示填充*<br/>
属性DISPID_AMBIENT_SHOWHATCHING。

### <a name="return-value"></a>返回值

标准 HRESULT 值之一。

## <a name="ccomcontrolbasegetambientsupportsmnemonics"></a><a name="getambientsupportsmnemonics"></a>CComControlBase：获取环境支持Mnemonic

检索DISPID_AMBIENT_SUPPORTSMNEMONICS，一个指示容器是否支持键盘助记符的标志。

```
HRESULT GetAmbientSupportsMnemonics(BOOL& bSupportsMnemonics);
```

### <a name="parameters"></a>参数

*b 支持Mnemonics*<br/>
该属性DISPID_AMBIENT_SUPPORTSMNEMONICS。

### <a name="return-value"></a>返回值

标准 HRESULT 值之一。

## <a name="ccomcontrolbasegetambienttextalign"></a><a name="getambienttextalign"></a>CComControlBase：获取环境文本对齐

检索DISPID_AMBIENT_TEXTALIGN、容器首选的文本对齐：0 表示一般对齐（数字右侧，文本左侧），左对齐为 1，中心对齐为 2，右对齐为 3。

```
HRESULT GetAmbientTextAlign(short& nTextAlign);
```

### <a name="parameters"></a>参数

*n文本对齐*<br/>
属性DISPID_AMBIENT_TEXTALIGN。

### <a name="return-value"></a>返回值

标准 HRESULT 值之一。

## <a name="ccomcontrolbasegetambienttoptobottom"></a><a name="getambienttoptobottom"></a>CCom 控制库：获取环境顶底

检索DISPID_AMBIENT_TOPTOBOTTOM，容器显示内容的方向。

```
HRESULT GetAmbientTopToBottom(BOOL& bTopToBottom);
```

### <a name="parameters"></a>参数

*bTopto底部*<br/>
房产DISPID_AMBIENT_TOPTOBOTTOM。 如果文本从上到下显示，则设置为 TRUE;如果文本从下显示到顶部，则 FALSE。

### <a name="return-value"></a>返回值

返回成功S_OK，或失败时返回错误 HRESULT。

## <a name="ccomcontrolbasegetambientuidead"></a><a name="getambientuidead"></a>CComControlBase：获取环境UI死

检索DISPID_AMBIENT_UIDEAD，指示容器是否希望控件响应用户界面操作的标志。

```
HRESULT GetAmbientUIDead(BOOL& bUIDead);
```

### <a name="parameters"></a>参数

*bUIDead*<br/>
该酒店DISPID_AMBIENT_UIDEAD。

### <a name="return-value"></a>返回值

标准 HRESULT 值之一。

### <a name="remarks"></a>备注

如果为 TRUE，则控件不应响应。 此标志适用于DISPID_AMBIENT_USERMODE标志。 请参阅[CComControlBase：获取环境用户模式](#getambientusermode)。

## <a name="ccomcontrolbasegetambientusermode"></a><a name="getambientusermode"></a>CCom 控制库：获取环境用户模式

检索DISPID_AMBIENT_USERMODE，指示容器处于运行模式 （TRUE） 还是设计模式 （FALSE） 的标志。

```
HRESULT GetAmbientUserMode(BOOL& bUserMode);
```

### <a name="parameters"></a>参数

*用户模式*<br/>
属性DISPID_AMBIENT_USERMODE。

### <a name="return-value"></a>返回值

标准 HRESULT 值之一。

## <a name="ccomcontrolbasegetdirty"></a><a name="getdirty"></a>CComControlBase：获取脏

返回数据成员`m_bRequiresSave`的值。

```
BOOL GetDirty();
```

### <a name="return-value"></a>返回值

返回数据成员[m_bRequiresSave](#m_brequiressave)的值。

### <a name="remarks"></a>备注

此值使用[CComControlBase 设置：：设置脏话](#setdirty)。

## <a name="ccomcontrolbasegetzoominfo"></a><a name="getzoominfo"></a>CComControlBase：获取Zoominfo

检索为就地编辑而激活的控件的缩放因子的分子和分母的 x 和 y 值。

```cpp
void GetZoomInfo(ATL_DRAWINFO& di);
```

### <a name="parameters"></a>参数

*地*<br/>
保存缩放因子的分子和分母的结构。 有关详细信息，请参阅[ATL_DRAWINFO](../../atl/reference/atl-drawinfo-structure.md)。

### <a name="remarks"></a>备注

缩放系数是控件的自然大小与其当前范围的比例。

## <a name="ccomcontrolbaseinplaceactivate"></a><a name="inplaceactivate"></a>CCom 控制库：就地激活

使控件从非活动状态转换为*iVerb*中动词指示的任何状态。

```
HRESULT InPlaceActivate(LONG iVerb, const RECT* prcPosRect = NULL);
```

### <a name="parameters"></a>参数

*iVerb*<br/>
指示[IOleObjectImpl：:DoVerb](../../atl/reference/ioleobjectimpl-class.md#doverb)） 要执行的操作的值。

*prcPosRect*<br/>
指向就地控件的位置的指针。

### <a name="return-value"></a>返回值

标准 HRESULT 值之一。

### <a name="remarks"></a>备注

在激活之前，此方法检查控件是否具有客户端站点，检查控件的可见量，并在父窗口中获取控件的位置。 激活控件后，此方法将激活控件的用户界面，并告诉容器使控件可见。

此方法还检索控件的`IOleInPlaceSite`、`IOleInPlaceSiteEx`或`IOleInPlaceSiteWindowless`接口指针，并将其存储在控件类的数据成员[CComControlBase：m_spInPlaceSite](#m_spinplacesite)。 控制类数据成员 CComControlBase：：m_bInPlaceSiteEx、CComControlBase：m_bWndLess、CComControlBase：：m_bWasOnceWindowless 和[CComControlBase：m_bNegotiatedWnd](#m_bnegotiatedwnd)根据需要设置为 true。 [CComControlBase::m_bInPlaceSiteEx](#m_binplacesiteex) [CComControlBase::m_bWndLess](#m_bwndless) [CComControlBase::m_bWasOnceWindowless](#m_bwasoncewindowless)

## <a name="ccomcontrolbaseinternalgetsite"></a><a name="internalgetsite"></a>CComControlBase：内部获取网站

调用此方法以查询控件站点以寻找指向已标识接口的指针。

```
HRESULT InternalGetSite(REFIID riid, void** ppUnkSite);
```

### <a name="parameters"></a>参数

*riid*<br/>
应在*ppUnkSite*中返回的接口指针的 IID。

*ppUnkSite*<br/>
接收*riid*中请求的接口指针的指针变量的地址。

### <a name="return-value"></a>返回值

返回成功S_OK，或失败时返回错误 HRESULT。

### <a name="remarks"></a>备注

如果站点支持*riid*中请求的接口，则指针将通过*ppUnkSite*返回。 否则 *，ppUnkSite*设置为 NULL。

## <a name="ccomcontrolbasem_bautosize"></a><a name="m_bautosize"></a>CComControlBase：m_bAutoSize

指示控件的标志不能是任何其他大小。

```
unsigned m_bAutoSize:1;
```

### <a name="remarks"></a>备注

此标志由`IOleObjectImpl::SetExtent`和（如果 TRUE）检查，则会导致函数返回E_FAIL。

> [!NOTE]
> 要在控件类中使用此数据成员，必须将其声明为控件类中的数据成员。 控件类不会从基类继承此数据成员，因为它在基类中的联合中声明。

如果在 ATL 控件向导[的"库存属性](../../atl/reference/stock-properties-atl-control-wizard.md)"选项卡上添加 **"自动大小**"选项，向导将自动在控件类中创建此数据成员，为属性创建 put 和 get 方法，并支持[IPropertyNotifySink](/windows/win32/api/ocidl/nn-ocidl-ipropertynotifysink)在属性更改时自动通知容器。

## <a name="ccomcontrolbasem_bdrawfromnatural"></a><a name="m_bdrawfromnatural"></a>CComControlBase：m_bDrawFromNatural

指示 和`IDataObjectImpl::GetData``CComControlBase::GetZoomInfo`应从 而不是 从`m_sizeNatural``m_sizeExtent`设置控件大小的标志。

```
unsigned m_bDrawFromNatural:1;
```

### <a name="remarks"></a>备注

> [!NOTE]
> 要在控件类中使用此数据成员，必须将其声明为控件类中的数据成员。 控件类不会从基类继承此数据成员，因为它在基类中的联合中声明。

## <a name="ccomcontrolbasem_bdrawgetdatainhimetric"></a><a name="m_bdrawgetdatainhimetric"></a>CCom控制库：m_bDrawGetDataInHimetric

指示绘制时`IDataObjectImpl::GetData`应使用 HIMETRIC 单位而不是像素的标志。

```
unsigned m_bDrawGetDataInHimetric:1;
```

### <a name="remarks"></a>备注

每个逻辑 HIMETRIC 单位为 0.01 毫米。

> [!NOTE]
> 要在控件类中使用此数据成员，必须将其声明为控件类中的数据成员。 控件类不会从基类继承此数据成员，因为它在基类中的联合中声明。

## <a name="ccomcontrolbasem_binplaceactive"></a><a name="m_binplaceactive"></a>CComControlBase：m_bInPlaceActive

指示控件已就地处于活动状态的标志。

```
unsigned m_bInPlaceActive:1;
```

### <a name="remarks"></a>备注

这意味着控件是可见的，并且其窗口（如果有）可见，但其菜单和工具栏可能不处于活动状态。 该`m_bUIActive`标志指示控件的用户界面（如菜单）也处于活动状态。

> [!NOTE]
> 要在控件类中使用此数据成员，必须将其声明为控件类中的数据成员。 控件类不会从基类继承此数据成员，因为它在基类中的联合中声明。

## <a name="ccomcontrolbasem_binplacesiteex"></a><a name="m_binplacesiteex"></a>CComControlBase：m_bInPlaceSiteEx

指示容器的标志支持`IOleInPlaceSiteEx`接口和 OCX96 控制功能，如无窗口和无闪烁控件。

```
unsigned m_bInPlaceSiteEx:1;
```

### <a name="remarks"></a>备注

> [!NOTE]
> 要在控件类中使用此数据成员，必须将其声明为控件类中的数据成员。 控件类不会从基类继承此数据成员，因为它在基类中的联合中声明。

`m_spInPlaceSite`数据成员指向[IOleInPlaceSite、IOleInPlaceSiteEx](/windows/win32/api/oleidl/nn-oleidl-ioleinplacesite)或[IOleInPlaceSite 无窗口](/windows/win32/api/ocidl/nn-ocidl-ioleinplacesitewindowless)接口，具体取决于`m_bWndLess`和`m_bInPlaceSiteEx`标志的值。 [IOleInPlaceSiteEx](/windows/win32/api/ocidl/nn-ocidl-ioleinplacesiteex) （数据成员`m_bNegotiatedWnd`必须为 TRUE，`m_spInPlaceSite`指针才能有效。

如果`m_bWndLess`FALSE`m_bInPlaceSiteEx`为 TRUE，`m_spInPlaceSite`则`IOleInPlaceSiteEx`为接口指针。 有关显示这三个数据成员之间关系的表，请参阅[m_spInPlaceSite。](#m_spinplacesite)

## <a name="ccomcontrolbasem_bnegotiatedwnd"></a><a name="m_bnegotiatedwnd"></a>CCom 控制库：：m_bNegotiatedWnd

指示控件是否已与容器协商支持 OCX96 控制功能（如无闪烁和无窗口控件）以及控件是窗口还是无窗口。

```
unsigned m_bNegotiatedWnd:1;
```

### <a name="remarks"></a>备注

> [!NOTE]
> 要在控件类中使用此数据成员，必须将其声明为控件类中的数据成员。 控件类不会从基类继承此数据成员，因为它在基类中的联合中声明。

该`m_bNegotiatedWnd`标志必须为 TRUE，`m_spInPlaceSite`指针才能有效。

## <a name="ccomcontrolbasem_brecomposeonresize"></a><a name="m_brecomposeonresize"></a>CComControlBase：m_bRecomposeOnResize

指示控件的标志希望在容器更改控件的显示大小时重新调整其演示文稿。

```
unsigned m_bRecomposeOnResize:1;
```

### <a name="remarks"></a>备注

> [!NOTE]
> 要在控件类中使用此数据成员，必须将其声明为控件类中的数据成员。 控件类不会从基类继承此数据成员，因为它在基类中的联合中声明。

此标志由[IOleObjectImpl：：SetAndina](../../atl/reference/ioleobjectimpl-class.md#setextent)检查，如果`SetExtent`为 TRUE，则通知容器的视图更改。 如果设置了此标志，也应设置[OLEMISC](/windows/win32/api/oleidl/ne-oleidl-olemisc)枚举中的OLEMISC_RECOMPOSEONRESIZE位。

## <a name="ccomcontrolbasem_brequiressave"></a><a name="m_brequiressave"></a>CComControlBase：m_bRequiresSave

指示控件自上次保存以来已更改的标志。

```
unsigned m_bRequiresSave:1;
```

### <a name="remarks"></a>备注

的值`m_bRequiresSave`可以使用[CComControlBase 设置：设置脏，](#setdirty)并检索[CComControlBase：：获取脏。](#getdirty)

> [!NOTE]
> 要在控件类中使用此数据成员，必须将其声明为控件类中的数据成员。 控件类不会从基类继承此数据成员，因为它在基类中的联合中声明。

## <a name="ccomcontrolbasem_bresizenatural"></a><a name="m_bresizenatural"></a>CComControlBase：m_bResizeNatural

指示控件的标志希望在容器更改控件的显示大小时调整其自然范围（其未缩放的物理大小）。

```
unsigned m_bResizeNatural:1;
```

### <a name="remarks"></a>备注

此标志由 和`IOleObjectImpl::SetExtent`（如果 TRUE）检查，则传入`SetExtent`的大小将分配给`m_sizeNatural`。

传入`SetExtent`的大小始终分配给`m_sizeExtent`，而不考虑 的值。 `m_bResizeNatural`

> [!NOTE]
> 要在控件类中使用此数据成员，必须将其声明为控件类中的数据成员。 控件类不会从基类继承此数据成员，因为它在基类中的联合中声明。

## <a name="ccomcontrolbasem_buiactive"></a><a name="m_buiactive"></a>CComControlBase：m_bUIActive

指示控件用户界面（如菜单和工具栏）的标志处于活动状态。

```
unsigned m_bUIActive:1;
```

### <a name="remarks"></a>备注

该`m_bInPlaceActive`标志指示控件处于活动状态，但指示其用户界面处于活动状态。

> [!NOTE]
> 要在控件类中使用此数据成员，必须将其声明为控件类中的数据成员。 控件类不会从基类继承此数据成员，因为它在基类中的联合中声明。

## <a name="ccomcontrolbasem_busingwindowrgn"></a><a name="m_busingwindowrgn"></a>CCom 控制库：：m_bUsingWindowRgn

指示控件正在使用容器提供的窗口区域的标志。

```
unsigned m_bUsingWindowRgn:1;
```

### <a name="remarks"></a>备注

> [!NOTE]
> 要在控件类中使用此数据成员，必须将其声明为控件类中的数据成员。 控件类不会从基类继承此数据成员，因为它在基类中的联合中声明。

## <a name="ccomcontrolbasem_bwasoncewindowless"></a><a name="m_bwasoncewindowless"></a>CCom控制库：m_bWasOnceWindowless

指示控件已无窗口的标志，但现在可能已无窗口，也可能不是无窗口。

```
unsigned m_bWasOnceWindowless:1;
```

### <a name="remarks"></a>备注

> [!NOTE]
> 要在控件类中使用此数据成员，必须将其声明为控件类中的数据成员。 控件类不会从基类继承此数据成员，因为它在基类中的联合中声明。

## <a name="ccomcontrolbasem_bwindowonly"></a><a name="m_bwindowonly"></a>CComControlBase：m_bWindowOnly

指示控件的标志应窗口，即使容器支持无窗口控件也是如此。

```
unsigned m_bWindowOnly:1;
```

### <a name="remarks"></a>备注

> [!NOTE]
> 要在控件类中使用此数据成员，必须将其声明为控件类中的数据成员。 控件类不会从基类继承此数据成员，因为它在基类中的联合中声明。

## <a name="ccomcontrolbasem_bwndless"></a><a name="m_bwndless"></a>CComControlBase：m_bWndLess

指示控件无窗口的标志。

```
unsigned m_bWndLess:1;
```

### <a name="remarks"></a>备注

> [!NOTE]
> 要在控件类中使用此数据成员，必须将其声明为控件类中的数据成员。 控件类不会从基类继承此数据成员，因为它在基类中的联合中声明。

`m_spInPlaceSite`数据成员指向[IOleInPlaceSite、IOleInPlaceSiteEx](/windows/win32/api/oleidl/nn-oleidl-ioleinplacesite)或[IOleInPlaceSite 无窗口](/windows/win32/api/ocidl/nn-ocidl-ioleinplacesitewindowless)接口，具体取决于`m_bWndLess`和[CComControlBase：m_bInPlaceSiteEx](#m_binplacesiteex)标志的值。 [IOleInPlaceSiteEx](/windows/win32/api/ocidl/nn-ocidl-ioleinplacesiteex) （数据成员[CComControlBase：：m_bNegotiatedWnd](#m_bnegotiatedwnd)必须为[TRUE，CComControlBase：：m_spInPlaceSite](#m_spinplacesite)指针才能有效。

如果`m_bWndLess`为 TRUE，`m_spInPlaceSite`则`IOleInPlaceSiteWindowless`是接口指针。 有关显示这些数据成员之间完整关系的表，请参阅[CComControlBase：：m_spInPlaceSite。](#m_spinplacesite)

## <a name="ccomcontrolbasem_hwndcd"></a><a name="m_hwndcd"></a>CComControlBase：m_hWndCD

包含对与控件关联的窗口句柄的引用。

```
HWND& m_hWndCD;
```

### <a name="remarks"></a>备注

> [!NOTE]
> 要在控件类中使用此数据成员，必须将其声明为控件类中的数据成员。 控件类不会从基类继承此数据成员，因为它在基类中的联合中声明。

## <a name="ccomcontrolbasem_nfreezeevents"></a><a name="m_nfreezeevents"></a>CComControlBase：m_nFreezeEvents

计算容器冻结事件（拒绝接受事件）的次数，而不干预事件解冻（接受事件）。

```
short m_nFreezeEvents;
```

### <a name="remarks"></a>备注

> [!NOTE]
> 要在控件类中使用此数据成员，必须将其声明为控件类中的数据成员。 控件类不会从基类继承此数据成员，因为它在基类中的联合中声明。

## <a name="ccomcontrolbasem_rcpos"></a><a name="m_rcpos"></a>CComControlBase：m_rcPos

控件的像素位置，以容器的坐标表示。

```
RECT m_rcPos;
```

### <a name="remarks"></a>备注

> [!NOTE]
> 要在控件类中使用此数据成员，必须将其声明为控件类中的数据成员。 控件类不会从基类继承此数据成员，因为它在基类中的联合中声明。

## <a name="ccomcontrolbasem_sizeextent"></a><a name="m_sizeextent"></a>CComControlBase：m_sizeExtent

特定显示器的控制范围（以 HIMETRIC 单位为单位（每个单位为 0.01 毫米）。

```
SIZE m_sizeExtent;
```

### <a name="remarks"></a>备注

> [!NOTE]
> 要在控件类中使用此数据成员，必须将其声明为控件类中的数据成员。 控件类不会从基类继承此数据成员，因为它在基类中的联合中声明。

此大小由显示屏缩放。 控件的物理大小在数据成员中`m_sizeNatural`指定且固定。

您可以使用全局函数[AtlHiMetricToPixel](pixel-himetric-conversion-global-functions.md#atlhimetrictopixel)将大小转换为像素。

## <a name="ccomcontrolbasem_sizenatural"></a><a name="m_sizenatural"></a>CComControlBase：m_sizeNatural

以 HIMETRIC 单位（每个单位为 0.01 毫米）的控制的物理大小。

```
SIZE m_sizeNatural;
```

### <a name="remarks"></a>备注

> [!NOTE]
> 要在控件类中使用此数据成员，必须将其声明为控件类中的数据成员。 控件类不会从基类继承此数据成员，因为它在基类中的联合中声明。

此大小是固定的，而 中的`m_sizeExtent`大小由显示屏缩放。

您可以使用全局函数[AtlHiMetricToPixel](pixel-himetric-conversion-global-functions.md#atlhimetrictopixel)将大小转换为像素。

## <a name="ccomcontrolbasem_spadvisesink"></a><a name="m_spadvisesink"></a>CComControlBase：m_spAdviseSink

指向容器上的咨询连接的直接指针（容器的[IAdviseSink）。](/windows/win32/api/objidl/nn-objidl-iadvisesink)

```
CComPtr<IAdviseSink>
    m_spAdviseSink;
```

### <a name="remarks"></a>备注

> [!NOTE]
> 要在控件类中使用此数据成员，必须将其声明为控件类中的数据成员。 控件类不会从基类继承此数据成员，因为它在基类中的联合中声明。

## <a name="ccomcontrolbasem_spambientdispatch"></a><a name="m_spambientdispatch"></a>CComControlBase：m_spAmbientDispatch

允许您`CComDispatchDriver`通过`IDispatch`指针检索和设置对象属性的对象。

```
CComDispatchDriver m_spAmbientDispatch;
```

### <a name="remarks"></a>备注

> [!NOTE]
> 要在控件类中使用此数据成员，必须将其声明为控件类中的数据成员。 控件类不会从基类继承此数据成员，因为它在基类中的联合中声明。

## <a name="ccomcontrolbasem_spclientsite"></a><a name="m_spclientsite"></a>CComControlBase：m_spClientSite

指向容器中控件的客户端站点的指针。

```
CComPtr<IOleClientSite>
    m_spClientSite;
```

### <a name="remarks"></a>备注

> [!NOTE]
> 要在控件类中使用此数据成员，必须将其声明为控件类中的数据成员。 控件类不会从基类继承此数据成员，因为它在基类中的联合中声明。

## <a name="ccomcontrolbasem_spdataadviseholder"></a><a name="m_spdataadviseholder"></a>CComControlBase：m_spDataAdviseHolder

提供一种标准方法，用于在数据对象和通知接收器之间保持咨询连接。

```
CComPtr<IDataAdviseHolder>
    m_spDataAdviseHolder;
```

### <a name="remarks"></a>备注

> [!NOTE]
> 要在控件类中使用此数据成员，必须将其声明为控件类中的数据成员。 控件类不会从基类继承此数据成员，因为它在基类中的联合中声明。

数据对象是一种控件，可以传输数据并实现[IDataObject，](/windows/win32/api/objidl/nn-objidl-idataobject)其方法指定数据的格式和传输介质。

该接口`m_spDataAdviseHolder`实现[IDataObject：:D建议](/windows/win32/api/objidl/nf-objidl-idataobject-dadvise)和[IDataObject：:D建立](/windows/win32/api/objidl/nf-objidl-idataobject-dunadvise)和删除容器的咨询连接的不知情方法。 控件的容器必须通过支持[IAdviseSink](/windows/win32/api/objidl/nn-objidl-iadvisesink)接口来实现通知接收器。

## <a name="ccomcontrolbasem_spinplacesite"></a><a name="m_spinplacesite"></a>CCom控制库：m_spInPlaceSite

指向容器的[IOleInPlaceSite、IOleInPlaceSiteEx](/windows/win32/api/oleidl/nn-oleidl-ioleinplacesite)或[IOleInPlace无窗口](/windows/win32/api/ocidl/nn-ocidl-ioleinplacesitewindowless)接口指针的指针。 [IOleInPlaceSiteEx](/windows/win32/api/ocidl/nn-ocidl-ioleinplacesiteex)

```
CComPtr<IOleInPlaceSiteWindowless>
    m_spInPlaceSite;
```

### <a name="remarks"></a>备注

> [!NOTE]
> 要在控件类中使用此数据成员，必须将其声明为控件类中的数据成员。 控件类不会从基类继承此数据成员，因为它在基类中的联合中声明。

仅当`m_spInPlaceSite`[m_bNegotiatedWnd](#m_bnegotiatedwnd)标志为 TRUE 时，指针才有效。

下表显示了`m_spInPlaceSite`指针类型如何依赖于[m_bWndLess](#m_bwndless)和[m_bInPlaceSiteEx](#m_binplacesiteex)数据成员标志：

|m_spInPlaceSite类型|m_bWndLess值|m_bInPlaceSiteEx值|
|---------------------------|-----------------------|-----------------------------|
|`IOleInPlaceSiteWindowless`|TRUE|真或假|
|`IOleInPlaceSiteEx`|FALSE|TRUE|
|`IOleInPlaceSite`|FALSE|FALSE|

## <a name="ccomcontrolbasem_spoleadviseholder"></a><a name="m_spoleadviseholder"></a>CComControlBase：m_spOleAdviseHolder

提供保存咨询连接的方法的标准实现。

```
CComPtr<IOleAdviseHolder>
    m_spOleAdviseHolder;
```

### <a name="remarks"></a>备注

> [!NOTE]
> 要在控件类中使用此数据成员，必须将其声明为控件类中的数据成员。 控件类不会从基类继承此数据成员，因为它在基类中的联合中声明。

接口`m_spOleAdviseHolder`实现[IOleObject：：建议](/windows/win32/api/oleidl/nf-oleidl-ioleobject-advise)和[IOleObject：：取消建议](/windows/win32/api/oleidl/nf-oleidl-ioleobject-unadvise)方法来建立和删除到容器的咨询连接。 控件的容器必须通过支持[IAdviseSink](/windows/win32/api/objidl/nn-objidl-iadvisesink)接口来实现通知接收器。

## <a name="ccomcontrolbaseondraw"></a><a name="ondraw"></a>CComControlBase：ONDraw

重写此方法以绘制控件。

```
virtual HRESULT OnDraw(ATL_DRAWINFO& di);
```

### <a name="parameters"></a>参数

*地*<br/>
对包含绘图信息（如绘制方面、控制边界以及绘图是否优化）[的ATL_DRAWINFO](../../atl/reference/atl-drawinfo-structure.md)结构的引用。

### <a name="return-value"></a>返回值

标准 HRESULT 值。

### <a name="remarks"></a>备注

默认`OnDraw`删除或还原设备上下文或不执行任何操作，具体取决于[CComControlBase 中设置的标志：onDrawAdvanced](#ondrawadvanced)。

使用`OnDraw`ATL 控件向导创建控件时，方法将自动添加到控件类中。 向导的默认值`OnDraw`绘制一个带有"ATL 8.0"标签的矩形。

### <a name="example"></a>示例

请参阅[CComControlBase 的示例：获取环境外观](#getambientappearance)。

## <a name="ccomcontrolbaseondrawadvanced"></a><a name="ondrawadvanced"></a>CComControlBase：OnDraw高级

默认值`OnDrawAdvanced`为绘图准备规范化的设备上下文，然后调用控件类`OnDraw`的方法。

```
virtual HRESULT OnDrawAdvanced(ATL_DRAWINFO& di);
```

### <a name="parameters"></a>参数

*地*<br/>
对包含绘图信息（如绘制方面、控制边界以及绘图是否优化）[的ATL_DRAWINFO](../../atl/reference/atl-drawinfo-structure.md)结构的引用。

### <a name="return-value"></a>返回值

标准 HRESULT 值。

### <a name="remarks"></a>备注

如果要接受容器传递的设备上下文而不使其规范化，则重写此方法。

有关详细信息[，请参阅 CComControlBase：OnDraw。](#ondraw)

## <a name="ccomcontrolbaseonkillfocus"></a><a name="onkillfocus"></a>CComControlBase：：在基尔焦点上

检查控件是否就地处于活动状态，并且具有有效的控制站点，然后通知容器控件已失去焦点。

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
指示窗口消息是否成功处理的标志。 默认值为 FALSE。

### <a name="return-value"></a>返回值

始终返回 1。

## <a name="ccomcontrolbaseonmouseactivate"></a><a name="onmouseactivate"></a>CComControlBase：鼠标激活

检查 UI 是否处于用户模式，然后激活控件。

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
指示窗口消息是否成功处理的标志。 默认值为 FALSE。

### <a name="return-value"></a>返回值

始终返回 1。

## <a name="ccomcontrolbaseonpaint"></a><a name="onpaint"></a>CComControlBase：：上漆

准备容器进行绘制，获取控件的工作区，然后调用控件类`OnDrawAdvanced`的方法。

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
现有 HDC。

*lParam*<br/>
保留。

*lResult*<br/>
保留。

### <a name="return-value"></a>返回值

始终返回零。

### <a name="remarks"></a>备注

如果*wParam*不是`OnPaint`NULL，则假定它包含有效的 HDC，并使用它而不是[CComControlBase：：m_hWndCD](#m_hwndcd)。

## <a name="ccomcontrolbaseonsetfocus"></a><a name="onsetfocus"></a>CComControlBase：关于焦点

检查控件是否就地处于活动状态，并且具有有效的控制站点，然后通知容器控件已获得焦点。

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
指示窗口消息是否成功处理的标志。 默认值为 FALSE。

### <a name="return-value"></a>返回值

始终返回 1。

### <a name="remarks"></a>备注

向容器发送控件已收到焦点的通知。

## <a name="ccomcontrolbasepretranslateaccelerator"></a><a name="pretranslateaccelerator"></a>CComControlBase：:P重新翻译加速器

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

默认情况下，返回 FALSE。

## <a name="ccomcontrolbasesendonclose"></a><a name="sendonclose"></a>CCom 控制库：：发送关闭

通知在通知持有人登记的所有通知接收器，该控制已关闭。

```
HRESULT SendOnClose();
```

### <a name="return-value"></a>返回值

返回成功S_OK，或失败时返回错误 HRESULT。

### <a name="remarks"></a>备注

发送控件已关闭其通知接收器的通知。

## <a name="ccomcontrolbasesendondatachange"></a><a name="sendondatachange"></a>CCom 控制库：：发送数据更改

通知向通知持有人注册的所有通知接收器控制数据已更改。

```
HRESULT SendOnDataChange(DWORD advf = 0);
```

### <a name="parameters"></a>参数

*阿德夫夫*<br/>
建议指示如何调用[IAdviseSink：：onDataChange 的标志](/windows/win32/api/objidl/nf-objidl-iadvisesink-ondatachange)。 值来自[ADVF](/windows/win32/api/objidl/ne-objidl-advf)枚举。

### <a name="return-value"></a>返回值

返回成功S_OK，或失败时返回错误 HRESULT。

## <a name="ccomcontrolbasesendonrename"></a><a name="sendonrename"></a>CCom 控制库：：发送重新命名

通知所有在通知持有人登记的咨询接收器，该控制具有新的名字。

```
HRESULT SendOnRename(IMoniker* pmk);
```

### <a name="parameters"></a>参数

*pmk*<br/>
指向控件的新名字对象。

### <a name="return-value"></a>返回值

返回成功S_OK，或失败时返回错误 HRESULT。

### <a name="remarks"></a>备注

发送控件的绰号已更改的通知。

## <a name="ccomcontrolbasesendonsave"></a><a name="sendonsave"></a>CCom 控制库：：发送保存

通知向通知持有人登记的所有通知接收器，该控制已保存。

```
HRESULT SendOnSave();
```

### <a name="return-value"></a>返回值

返回成功S_OK，或失败时返回错误 HRESULT。

### <a name="remarks"></a>备注

发送控件刚刚保存其数据的通知。

## <a name="ccomcontrolbasesendonviewchange"></a><a name="sendonviewchange"></a>CCom 控制库：：发送视图更改

通知所有已注册的通知接收器控件的视图已更改。

```
HRESULT SendOnViewChange(DWORD dwAspect, LONG lindex = -1);
```

### <a name="parameters"></a>参数

*dwAspect*<br/>
控件的方面或视图。

*利索引*<br/>
已更改的视图部分。 只有 -1 有效。

### <a name="return-value"></a>返回值

返回成功S_OK，或失败时返回错误 HRESULT。

### <a name="remarks"></a>备注

`SendOnViewChange`调用[I 建议 Sink：：打开视图更改](/windows/win32/api/objidl/nf-objidl-iadvisesink-onviewchange)。 当前支持的*lindex*的唯一值是 -1，这表明整个视图是感兴趣的。

## <a name="ccomcontrolbasesetcontrolfocus"></a><a name="setcontrolfocus"></a>CCom 控制库：设置控制焦点

设置或移除键盘对焦到控件或从控件。

```
BOOL SetControlFocus(BOOL bGrab);
```

### <a name="parameters"></a>参数

*bGrab*<br/>
如果为 TRUE，则将键盘焦点设置到呼叫控件。 如果 FALSE，则从呼叫控件中删除键盘焦点，前提是其具有焦点。

### <a name="return-value"></a>返回值

如果控件成功接收焦点，则返回 TRUE;否则，FALSE。

### <a name="remarks"></a>备注

对于窗口控件，调用 Windows API 函数[SetFocus。](/windows/win32/api/winuser/nf-winuser-setfocus) 对于无窗口控件[，IOleInPlaceSite 无窗口：：setFocus](/windows/win32/api/ocidl/nf-ocidl-ioleinplacesitewindowless-setfocus)调用。 通过此调用，无窗口控件获取键盘焦点并可以响应窗口消息。

## <a name="ccomcontrolbasesetdirty"></a><a name="setdirty"></a>CCom 控制库：：设置脏

将数据成员`m_bRequiresSave`设置为*bDirty*中的值。

```cpp
void SetDirty(BOOL bDirty);
```

### <a name="parameters"></a>参数

*bDirty*<br/>
数据成员[CComControlBase 的值：：m_bRequiresSave](#m_brequiressave)。

### <a name="remarks"></a>备注

`SetDirty(TRUE)`应调用 以标记控件自上次保存以来已更改。 的值`m_bRequiresSave`使用[CComControlBase 检索：：获取脏。](#getdirty)

## <a name="see-also"></a>请参阅

[CComControl 类](../../atl/reference/ccomcontrol-class.md)<br/>
[类概述](../../atl/atl-class-overview.md)
