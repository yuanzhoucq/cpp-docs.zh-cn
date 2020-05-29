---
title: CStockPropImpl 类
ms.date: 05/06/2019
f1_keywords:
- CStockPropImpl
- ATLCTL/ATL::CStockPropImpl
- ATLCTL/ATL::get_Appearance
- ATLCTL/ATL::get_AutoSize
- ATLCTL/ATL::get_BackColor
- ATLCTL/ATL::get_BackStyle
- ATLCTL/ATL::get_BorderColor
- ATLCTL/ATL::get_BorderStyle
- ATLCTL/ATL::get_BorderVisible
- ATLCTL/ATL::get_BorderWidth
- ATLCTL/ATL::get_Caption
- ATLCTL/ATL::get_DrawMode
- ATLCTL/ATL::get_DrawStyle
- ATLCTL/ATL::get_DrawWidth
- ATLCTL/ATL::get_Enabled
- ATLCTL/ATL::get_FillColor
- ATLCTL/ATL::get_FillStyle
- ATLCTL/ATL::get_Font
- ATLCTL/ATL::get_ForeColor
- ATLCTL/ATL::get_HWND
- ATLCTL/ATL::get_MouseIcon
- ATLCTL/ATL::get_MousePointer
- ATLCTL/ATL::get_Picture
- ATLCTL/ATL::get_ReadyState
- ATLCTL/ATL::get_TabStop
- ATLCTL/ATL::get_Text
- ATLCTL/ATL::getvalid
- ATLCTL/ATL::get_Window
- ATLCTL/ATL::put_Appearance
- ATLCTL/ATL::put_AutoSize
- ATLCTL/ATL::put_BackColor
- ATLCTL/ATL::put_BackStyle
- ATLCTL/ATL::put_BorderColor
- ATLCTL/ATL::put_BorderStyle
- ATLCTL/ATL::put_BorderVisible
- ATLCTL/ATL::put_BorderWidth
- ATLCTL/ATL::put_Caption
- ATLCTL/ATL::put_DrawMode
- ATLCTL/ATL::put_DrawStyle
- ATLCTL/ATL::put_DrawWidth
- ATLCTL/ATL::put_Enabled
- ATLCTL/ATL::put_FillColor
- ATLCTL/ATL::put_FillStyle
- ATLCTL/ATL::put_Font
- ATLCTL/ATL::put_ForeColor
- ATLCTL/ATL::put_HWND
- ATLCTL/ATL::put_MouseIcon
- ATLCTL/ATL::put_MousePointer
- ATLCTL/ATL::put_Picture
- ATLCTL/ATL::put_ReadyState
- ATLCTL/ATL::put_TabStop
- ATLCTL/ATL::put_Text
- ATLCTL/ATL::putvalid
- ATLCTL/ATL::put_Window
- ATLCTL/ATL::putref_Font
- ATLCTL/ATL::putref_MouseIcon
- ATLCTL/ATL::putref_Picture
helpviewer_keywords:
- CStockPropImpl class
- controls [ATL], stock properties
- stock properties, ATL controls
ms.assetid: 45f11d7d-6580-4a0e-872d-3bc8b836cfda
ms.openlocfilehash: 0aaeb1b6de0febfd5fc0d41cbcc7bad41c607af4
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81330675"
---
# <a name="cstockpropimpl-class"></a>CStockPropImpl 类

此类提供支持股票属性值的方法。

> [!IMPORTANT]
> 此类及其成员不能在 Windows 运行时中执行的应用程序中使用。

## <a name="syntax"></a>语法

```
template <
    class T,
    class InterfaceName,
    const IID* piid = &_ATL_IIDOF(InterfaceName),
    const GUID* plibid = &CComModule::m_libid,
    WORD wMajor = 1,
    WORD wMinor = 0,
    class tihclass = CcomTypeInfoHolder>
class ATL_NO_VTABLE CStockPropImpl :
    public IDispatchImpl<InterfaceName, piid, plibid, wMajor, wMinor, tihclass>
```

#### <a name="parameters"></a>参数

*T*<br/>
实现控件并从 派生的类`CStockPropImpl`。

*接口名称*<br/>
公开股票属性的双接口。

*皮伊德*<br/>
指向 IID 的`InterfaceName`指针。

*普利比德*<br/>
指向类型库的 LIBID 的指针，其中包含`InterfaceName`的定义。

*w 主要*<br/>
类型库的主版本。 默认值为 1。

*wMinor*<br/>
类型库的次版本。 默认值为 0。

*提赫班*<br/>
用于管理*T*的类型信息的类。默认值为`CComTypeInfoHolder`。

## <a name="members"></a>成员

### <a name="public-methods"></a>公共方法

|||
|-|-|
|[get_Appearance](#get_appearance)|调用此方法获取控件使用的绘制样式，例如平面或 3D。|
|[get_AutoSize](#get_autosize)|调用此方法以获取指示控件是否不能为任何其他大小的标志的状态。|
|[get_BackColor](#get_backcolor)|调用此方法以获取控件的背景颜色。|
|[get_BackStyle](#get_backstyle)|调用此方法获取控件的背景样式，无论是透明还是不透明。|
|[get_BorderColor](#get_bordercolor)|调用此方法以获取控件的边框颜色。|
|[get_BorderStyle](#get_borderstyle)|调用此方法以获取控件的边框样式。|
|[get_BorderVisible](#get_bordervisible)|调用此方法以获取指示控件的边框是否可见的标志的状态。|
|[get_BorderWidth](#get_borderwidth)|调用此方法获取控件边框的宽度（以像素为单位）。|
|[get_Caption](#get_caption)|调用此方法以获取对象标题中指定的文本。|
|[get_DrawMode](#get_drawmode)|调用此方法以获取控件的绘图模式，例如 XOR 笔或反转颜色。|
|[get_DrawStyle](#get_drawstyle)|调用此方法获取控件的绘图样式，例如，实体、虚线或虚线。|
|[get_DrawWidth](#get_drawwidth)|调用此方法以获取控件的绘图方法使用的绘图宽度（以像素为单位）。|
|[get_Enabled](#get_enabled)|调用此方法以获取指示控件是否已启用的标志的状态。|
|[get_FillColor](#get_fillcolor)|调用此方法以获取控件的填充颜色。|
|[get_FillStyle](#get_fillstyle)|调用此方法获取控件的填充样式，例如，实心、透明或交叉阴影。|
|[get_Font](#get_font)|调用此方法以获取指向控件的字体属性的指针。|
|[get_ForeColor](#get_forecolor)|调用此方法以获取控件的前景颜色。|
|[get_HWND](#get_hwnd)|调用此方法以获取与控件关联的窗口句柄。|
|[get_MouseIcon](#get_mouseicon)|调用此方法以获取鼠标位于控件上时要显示的图形（图标、位图或元文件）的图片属性。|
|[get_MousePointer](#get_mousepointer)|调用此方法可获取鼠标位于控件（例如箭头、交叉或沙漏）上时显示的鼠标指针类型。|
|[get_Picture](#get_picture)|调用此方法以获取指向要显示的图形（图标、位图或元文件）的图片属性的指针。|
|[get_ReadyState](#get_readystate)|调用此方法以获取控件的就绪状态，例如加载或加载。|
|[get_TabStop](#get_tabstop)|调用此方法以获取指示控件是否为制表位标志的标志。|
|[get_Text](#get_text)|调用此方法获取控件中显示的文本。|
|[获得有效](#get_valid)|调用此方法以获取指示控件是否有效的标志的状态。|
|[get_Window](#get_window)|调用此方法以获取与控件关联的窗口句柄。 与[CStockPropImpl 相同：get_HWND](#get_hwnd)。|
|[put_Appearance](#put_appearance)|调用此方法以设置控件使用的绘制样式，例如平面或 3D。|
|[put_AutoSize](#put_autosize)|调用此方法以设置指示控件不能为任何其他大小的标志的值。|
|[put_BackColor](#put_backcolor)|调用此方法以设置控件的背景颜色。|
|[put_BackStyle](#put_backstyle)|调用此方法以设置控件的背景样式。|
|[put_BorderColor](#put_bordercolor)|调用此方法以设置控件的边框颜色。|
|[put_BorderStyle](#put_borderstyle)|调用此方法以设置控件的边框样式。|
|[put_BorderVisible](#put_bordervisible)|调用此方法以设置指示控件的边框是否可见的标志的值。|
|[put_BorderWidth](#put_borderwidth)|调用此方法以设置控件边框的宽度。|
|[put_Caption](#put_caption)|调用此方法以将要与控件一起显示的文本设置为"|
|[put_DrawMode](#put_drawmode)|调用此方法以设置控件的绘图模式，例如 XOR 笔或反转颜色。|
|[put_DrawStyle](#put_drawstyle)|调用此方法以设置控件的绘图样式，例如，实体、虚线或虚线。|
|[put_DrawWidth](#put_drawwidth)|调用此方法以设置控件的绘图方法使用的宽度（以像素为单位）。|
|[put_Enabled](#put_enabled)|调用此方法以设置指示控件是否已启用的标志。|
|[put_FillColor](#put_fillcolor)|调用此方法以设置控件的填充颜色。|
|[put_FillStyle](#put_fillstyle)|调用此方法以设置控件的填充样式，例如，实心、透明或交叉阴影。|
|[put_Font](#put_font)|调用此方法以设置控件的字体属性。|
|[put_ForeColor](#put_forecolor)|调用此方法以设置控件的前景颜色。|
|[put_HWND](#put_hwnd)|此方法返回E_FAIL。|
|[put_MouseIcon](#put_mouseicon)|调用此方法可设置鼠标位于控件上时要显示的图形（图标、位图或元文件）的图片属性。|
|[put_MousePointer](#put_mousepointer)|调用此方法可设置鼠标位于控件上时显示的鼠标指针类型，例如箭头、十字或沙漏。|
|[put_Picture](#put_picture)|调用此方法以设置要显示的图形（图标、位图或元文件）的图片属性。|
|[put_ReadyState](#put_readystate)|调用此方法以设置控件的就绪状态，例如加载或加载。|
|[put_TabStop](#put_tabstop)|调用此方法以设置指示控件是否为制表位的标志的值。|
|[put_Text](#put_text)|调用此方法以设置控件中显示的文本。|
|[放有效](#put_valid)|调用此方法以设置指示控件是否有效的标志。|
|[put_Window](#put_window)|此方法称为[CStockPropimpl：:put_HWND](#put_hwnd)，它返回E_FAIL。|
|[putref_Font](#putref_font)|调用此方法以设置控件的字体属性，并带有引用计数。|
|[putref_MouseIcon](#putref_mouseicon)|调用此方法可设置鼠标位于控件上时要显示的图形（图标、位图或元文件）的图片属性，并带有引用计数。|
|[putref_Picture](#putref_picture)|调用此方法以设置要显示的图形（图标、位图或元文件）的图片属性，并带有引用计数。|

## <a name="remarks"></a>备注

`CStockPropImpl`为每个股票属性提供**放和****获取**方法。 这些方法提供了必要的代码，用于设置或获取与每个属性关联的数据成员，并在任何属性发生更改时通知容器并与容器同步。

Visual Studio 通过其向导支持股票属性。 有关向控件添加股票属性的详细信息，请参阅[ATL 教程](../../atl/active-template-library-atl-tutorial.md)。

对于向后兼容性，`CStockPropImpl`还公开`get_Window`和`put_Window`分别调用`get_HWND`和`put_HWND`的方法。 由于 HWND 应该是只读属性，因此返回的`put_HWND`默认实现E_FAIL。

以下属性还具有**putref**实现：

- 字体

- 鼠标图标

- Picture

相同的三个库存属性要求其相应的数据成员的类型`CComPtr`或其他一些类通过赋值运算符提供正确的接口引用计数。

## <a name="inheritance-hierarchy"></a>继承层次结构

`T`

[IDispatchImpl](../../atl/reference/idispatchimpl-class.md)

`CStockPropImpl`

## <a name="requirements"></a>要求

**标题：** atlctl.h

## <a name="cstockpropimplget_appearance"></a><a name="get_appearance"></a>CStockPropimpl：get_Appearance

调用此方法获取控件使用的绘制样式，例如平面或 3D。

```
HRESULT STDMETHODCALLTYPE get_Appearance(SHORT pnAppearance);
```

### <a name="parameters"></a>参数

*pn外观*<br/>
接收控件的绘制样式的变量。

### <a name="return-value"></a>返回值

返回成功S_OK，或失败时返回错误 HRESULT。

## <a name="cstockpropimplget_autosize"></a><a name="get_autosize"></a>CStockPropimpl：：get_AutoSize

调用此方法以获取指示控件是否不能为任何其他大小的标志的状态。

```
HRESULT STDMETHODCALLTYPE get_Autosize(VARIANT_BOOL* pbAutoSize);
```

### <a name="parameters"></a>参数

*pb 自动大小*<br/>
接收标志状态的变量。 TRUE 表示控件不能是任何其他大小。

### <a name="return-value"></a>返回值

返回成功S_OK，或失败时返回错误 HRESULT。

## <a name="cstockpropimplget_backcolor"></a><a name="get_backcolor"></a>CStockPropimpl：：get_BackColor

调用此方法以获取控件的背景颜色。

```
HRESULT STDMETHODCALLTYPE get_BackColor(OLE_COLOR* pclrBackColor);
```

### <a name="parameters"></a>参数

*pclrBackColor*<br/>
接收控件背景颜色的变量。

### <a name="return-value"></a>返回值

返回成功S_OK，或失败时返回错误 HRESULT。

## <a name="cstockpropimplget_backstyle"></a><a name="get_backstyle"></a>CStockPropimpl：：get_BackStyle

调用此方法获取控件的背景样式，无论是透明还是不透明。

```
HRESULT STDMETHODCALLTYPE get_BackStyle(LONG* pnBackStyle);
```

### <a name="parameters"></a>参数

*pnBackStyle*<br/>
接收控件的背景样式的变量。

### <a name="return-value"></a>返回值

返回成功S_OK，或失败时返回错误 HRESULT。

## <a name="cstockpropimplget_bordercolor"></a><a name="get_bordercolor"></a>CStockPropimpl：：get_BorderColor

调用此方法以获取控件的边框颜色。

```
HRESULT STDMETHODCALLTYPE get_BorderColor(OLE_COLOR* pclrBorderColor);
```

### <a name="parameters"></a>参数

*pclr边框颜色*<br/>
接收控件边框颜色的变量。

### <a name="return-value"></a>返回值

返回成功S_OK，或失败时返回错误 HRESULT。

## <a name="cstockpropimplget_borderstyle"></a><a name="get_borderstyle"></a>CStockPropimpl：：get_BorderStyle

调用此方法以获取控件的边框样式。

```
HRESULT STDMETHODCALLTYPE get_BorderStyle(LONG* pnBorderStyle);
```

### <a name="parameters"></a>参数

*pn边框样式*<br/>
接收控件边框样式的变量。

### <a name="return-value"></a>返回值

返回成功S_OK，或失败时返回错误 HRESULT。

## <a name="cstockpropimplget_bordervisible"></a><a name="get_bordervisible"></a>CStockPropimpl：get_BorderVisible

调用此方法以获取指示控件的边框是否可见的标志的状态。

```
HRESULT STDMETHODCALLTYPE get_BorderVisible(VARIANT_BOOL* pbBorderVisible);
```

### <a name="parameters"></a>参数

*pb 边界可见*<br/>
接收标志状态的变量。 TRUE 表示控件的边框可见。

### <a name="return-value"></a>返回值

返回成功S_OK，或失败时返回错误 HRESULT。

## <a name="cstockpropimplget_borderwidth"></a><a name="get_borderwidth"></a>CStockPropimpl：get_BorderWidth

调用此方法获取控件边框的宽度。

```
HRESULT STDMETHODCALLTYPE get_BorderWidth(LONG* pnBorderWidth);
```

### <a name="parameters"></a>参数

*pn边框宽度*<br/>
接收控件的边框宽度的变量。

### <a name="return-value"></a>返回值

返回成功S_OK，或失败时返回错误 HRESULT。

## <a name="cstockpropimplget_caption"></a><a name="get_caption"></a>CStockPropimpl：get_Caption

调用此方法以获取对象标题中指定的文本。

```
HRESULT STDMETHODCALLTYPE get_Caption(BSTR* pbstrCaption);
```

### <a name="parameters"></a>参数

*pbstrCaption*<br/>
要与控件一起显示的文本。

### <a name="return-value"></a>返回值

返回成功S_OK，或失败时返回错误 HRESULT。

## <a name="cstockpropimplget_drawmode"></a><a name="get_drawmode"></a>CStockPropimpl：get_DrawMode

调用此方法以获取控件的绘图模式，例如 XOR 笔或反转颜色。

```
HRESULT STDMETHODCALLTYPE get_DrawMode(LONG* pnDrawMode);
```

### <a name="parameters"></a>参数

*pnDraw模式*<br/>
接收控件的绘图模式的变量。

### <a name="return-value"></a>返回值

返回成功S_OK，或失败时返回错误 HRESULT。

## <a name="cstockpropimplget_drawstyle"></a><a name="get_drawstyle"></a>CStockPropimpl：get_DrawStyle

调用此方法获取控件的绘图样式，例如，实体、虚线或虚线。

```
HRESULT STDMETHODCALLTYPE get_DrawStyle(LONG* pnDrawStyle);
```

### <a name="parameters"></a>参数

*pnDraw样式*<br/>
接收控件的绘图样式的变量。

### <a name="return-value"></a>返回值

返回成功S_OK，或失败时返回错误 HRESULT。

## <a name="cstockpropimplget_drawwidth"></a><a name="get_drawwidth"></a>CStockPropimpl：get_DrawWidth

调用此方法以获取控件的绘图方法使用的绘图宽度（以像素为单位）。

```
HRESULT STDMETHODCALLTYPE get_DrawWidth(LONG* pnDrawWidth);
```

### <a name="parameters"></a>参数

*pnDraw 宽度*<br/>
接收控件宽度值（以像素为单位）的变量。

### <a name="return-value"></a>返回值

返回成功S_OK，或失败时返回错误 HRESULT。

## <a name="cstockpropimplget_enabled"></a><a name="get_enabled"></a>CStockPropimpl：get_Enabled

调用此方法以获取指示控件是否已启用的标志的状态。

```
HRESULT STDMETHODCALLTYPE get_Enabled(VARIANT_BOOL* pbEnabled);
```

### <a name="parameters"></a>参数

*pb 启用*<br/>
接收标志状态的变量。 TRUE 表示控件已启用。

### <a name="return-value"></a>返回值

返回成功S_OK，或失败时返回错误 HRESULT。

## <a name="cstockpropimplget_fillcolor"></a><a name="get_fillcolor"></a>CStockPropimpl：get_FillColor

调用此方法以获取控件的填充颜色。

```
HRESULT STDMETHODCALLTYPE get_FillColor(OLE_COLOR* pclrFillColor);
```

### <a name="parameters"></a>参数

*pclr 填充颜色*<br/>
接收控件填充颜色的变量。

### <a name="return-value"></a>返回值

返回成功S_OK，或失败时返回错误 HRESULT。

## <a name="cstockpropimplget_fillstyle"></a><a name="get_fillstyle"></a>CStockPropimpl：get_FillStyle

调用此方法获取控件的填充样式，例如，实心、透明或交叉填充。

```
HRESULT STDMETHODCALLTYPE get_FillStyle(LONG* pnFillStyle);
```

### <a name="parameters"></a>参数

*pn 填充样式*<br/>
接收控件填充样式的变量。

### <a name="return-value"></a>返回值

返回成功S_OK，或失败时返回错误 HRESULT。

## <a name="cstockpropimplget_font"></a><a name="get_font"></a>CStockPropimpl：：get_Font

调用此方法以获取指向控件的字体属性的指针。

```
HRESULT STDMETHODCALLTYPE get_Font(IFontDisp** ppFont);
```

### <a name="parameters"></a>参数

*ppFont*<br/>
接收指向控件字体属性的指针的变量。

### <a name="return-value"></a>返回值

返回成功S_OK，或失败时返回错误 HRESULT。

## <a name="cstockpropimplget_forecolor"></a><a name="get_forecolor"></a>CStockPropimpl：get_ForeColor

调用此方法以获取控件的前景颜色。

```
HRESULT STDMETHODCALLTYPE get_ForeColor(OLE_COLOR* pclrForeColor);
```

### <a name="parameters"></a>参数

*pclrForeColor*<br/>
接收控件前景颜色的变量。

### <a name="return-value"></a>返回值

返回成功S_OK，或失败时返回错误 HRESULT。

## <a name="cstockpropimplget_hwnd"></a><a name="get_hwnd"></a>CStockPropimpl：：get_HWND

调用此方法以获取与控件关联的窗口句柄。

```
HRESULT STDMETHODCALLTYPE get_HWND(LONG_PTR* phWnd);
```

### <a name="parameters"></a>参数

*phwnd*<br/>
与控件关联的窗口句柄。

### <a name="return-value"></a>返回值

返回成功S_OK，或失败时返回错误 HRESULT。

## <a name="cstockpropimplget_mouseicon"></a><a name="get_mouseicon"></a>CStockPropimpl：get_MouseIcon

调用此方法以获取鼠标位于控件上时要显示的图形（图标、位图或元文件）的图片属性。

```
HRESULT STDMETHODCALLTYPE get_MouseIcon(IPictureDisp** ppPicture);
```

### <a name="parameters"></a>参数

*ppPicture*<br/>
接收指向图形图片属性的指针的变量。

### <a name="return-value"></a>返回值

返回成功S_OK，或失败时返回错误 HRESULT。

## <a name="cstockpropimplget_mousepointer"></a><a name="get_mousepointer"></a>CStockPropimpl：：get_MousePointer

调用此方法可获取鼠标位于控件（例如箭头、交叉或沙漏）上时显示的鼠标指针类型。

```
HRESULT STDMETHODCALLTYPE get_MousePointer(LONG* pnMousePointer);
```

### <a name="parameters"></a>参数

*pnMousePointer*<br/>
接收鼠标指针类型的变量。

### <a name="return-value"></a>返回值

返回成功S_OK，或失败时返回错误 HRESULT。

## <a name="cstockpropimplget_picture"></a><a name="get_picture"></a>CStockPropimpl：：get_Picture

调用此方法以获取指向要显示的图形（图标、位图或元文件）的图片属性的指针。

```
HRESULT STDMETHODCALLTYPE get_Picture(IPictureDisp** ppPicture);
```

### <a name="parameters"></a>参数

*ppPicture*<br/>
接收指向图片属性的指针的变量。 有关详细信息[，请参阅 IPictureDisp。](/windows/win32/api/ocidl/nn-ocidl-ipicturedisp)

### <a name="return-value"></a>返回值

返回成功S_OK，或失败时返回错误 HRESULT。

## <a name="cstockpropimplget_readystate"></a><a name="get_readystate"></a>CStockPropimpl：get_ReadyState

调用此方法以获取控件的就绪状态，例如加载或加载。

```
HRESULT STDMETHODCALLTYPE get_ReadyState(LONG* pnReadyState);
```

### <a name="parameters"></a>参数

*pnReadyState*<br/>
接收控件就绪状态的变量。

### <a name="return-value"></a>返回值

返回成功S_OK，或失败时返回错误 HRESULT。

## <a name="cstockpropimplget_tabstop"></a><a name="get_tabstop"></a>CStockPropimpl：get_TabStop

调用此方法以获取指示控件是否为制表位的标志的状态。

```
HRESULT STDMETHODCALLTYPE get_TabStop(VARIANT_BOOL* pbTabStop);
```

### <a name="parameters"></a>参数

*pbTabStop*<br/>
接收标志状态的变量。 TRUE 表示控件是制表位。

### <a name="return-value"></a>返回值

返回成功S_OK，或失败时返回错误 HRESULT。

## <a name="cstockpropimplget_text"></a><a name="get_text"></a>CStockPropimpl：：get_Text

调用此方法获取控件中显示的文本。

```
HRESULT STDMETHODCALLTYPE get_Text(BSTR* pbstrText);
```

### <a name="parameters"></a>参数

*pbstrText*<br/>
控件中显示的文本。

### <a name="return-value"></a>返回值

返回成功S_OK，或失败时返回错误 HRESULT。

## <a name="cstockpropimplgetvalid"></a><a name="get_valid"></a>CStockPropimpl：：获取有效

调用此方法以获取指示控件是否有效的标志的状态。

```
HRESULT STDMETHODCALLTYPE getvalid(VARIANT_BOOL* pbValid);
```

### <a name="parameters"></a>参数

*pb 有效*<br/>
接收标志状态的变量。 TRUE 表示控件有效。

### <a name="return-value"></a>返回值

返回成功S_OK，或失败时返回错误 HRESULT。

## <a name="cstockpropimplget_window"></a><a name="get_window"></a>CStockPropimpl：get_Window

调用此方法以获取与控件关联的窗口句柄。 与[CStockPropImpl 相同：get_HWND](#get_hwnd)。

```
HRESULT STDMETHODCALLTYPE get_Window(LONG_PTR* phWnd);
```

### <a name="parameters"></a>参数

*phwnd*<br/>
与控件关联的窗口句柄。

### <a name="return-value"></a>返回值

返回成功S_OK，或失败时返回错误 HRESULT。

## <a name="cstockpropimplput_appearance"></a><a name="put_appearance"></a>CStockPropimpl：:put_外观

调用此方法以设置控件使用的绘制样式，例如平面或 3D。

```
HRESULT STDMETHODCALLTYPE put_Appearance(SHORT nAppearance);
```

### <a name="parameters"></a>参数

*n 外观*<br/>
控件将使用的新绘制样式。

### <a name="return-value"></a>返回值

返回成功S_OK，或失败时返回错误 HRESULT。

## <a name="cstockpropimplput_autosize"></a><a name="put_autosize"></a>CStockPropimpl：:put_自动大小

调用此方法以设置指示控件不能为任何其他大小的标志的值。

```
HRESULT STDMETHODCALLTYPE put_AutoSize(VARIANT_BOOL bAutoSize,);
```

### <a name="parameters"></a>参数

*b 自动大小*<br/>
如果控件不能是任何其他大小，则为 TRUE。

### <a name="return-value"></a>返回值

返回成功S_OK，或失败时返回错误 HRESULT。

## <a name="cstockpropimplput_backcolor"></a><a name="put_backcolor"></a>CStockPropimpl：:put_背面颜色

调用此方法以设置控件的背景颜色。

```
HRESULT STDMETHODCALLTYPE put_BackColor(OLE_COLOR clrBackColor);
```

### <a name="parameters"></a>参数

*clrBackColor*<br/>
新的控件背景颜色。

### <a name="return-value"></a>返回值

返回成功S_OK，或失败时返回错误 HRESULT。

## <a name="cstockpropimplput_backstyle"></a><a name="put_backstyle"></a>CStockPropimpl：:put_背面风格

调用此方法以设置控件的背景样式。

```
HRESULT STDMETHODCALLTYPE put_BackStyle(LONG nBackStyle);
```

### <a name="parameters"></a>参数

*nBack样式*<br/>
新的控件背景样式。

### <a name="return-value"></a>返回值

返回成功S_OK，或失败时返回错误 HRESULT。

## <a name="cstockpropimplput_bordercolor"></a><a name="put_bordercolor"></a>CStockPropimpl：:put_边框颜色

调用此方法以设置控件的边框颜色。

```
HRESULT STDMETHODCALLTYPE put_BorderColor(OLE_COLOR clrBorderColor);
```

### <a name="parameters"></a>参数

*clrBorderColor*<br/>
新的边框颜色。 OLE_COLOR数据类型在内部表示为 32 位长整数。

### <a name="return-value"></a>返回值

返回成功S_OK，或失败时返回错误 HRESULT。

## <a name="cstockpropimplput_borderstyle"></a><a name="put_borderstyle"></a>CStockPropimpl：:put_边框风格

调用此方法以设置控件的边框样式。

```
HRESULT STDMETHODCALLTYPE put_BorderStyle(LONG nBorderStyle);
```

### <a name="parameters"></a>参数

*n边框样式*<br/>
新的边框样式。

### <a name="return-value"></a>返回值

返回成功S_OK，或失败时返回错误 HRESULT。

## <a name="cstockpropimplput_bordervisible"></a><a name="put_bordervisible"></a>CStockPropimpl：:put_边界可见

调用此方法以设置指示控件的边框是否可见的标志的值。

```
HRESULT STDMETHODCALLTYPE put_BorderVisible(VARIANT_BOOL bBorderVisible);
```

### <a name="parameters"></a>参数

*b 边界可见*<br/>
如果边框为可见，则为 TRUE。

### <a name="return-value"></a>返回值

返回成功S_OK，或失败时返回错误 HRESULT。

## <a name="cstockpropimplput_borderwidth"></a><a name="put_borderwidth"></a>CStockPropimpl：:put_边界宽度

调用此方法以设置控件边框的宽度。

```
HRESULT STDMETHODCALLTYPE put_BorderWidth(LONG nBorderWidth);
```

### <a name="parameters"></a>参数

*n 边框宽度*<br/>
控件边框的新宽度。

### <a name="return-value"></a>返回值

返回成功S_OK，或失败时返回错误 HRESULT。

## <a name="cstockpropimplput_caption"></a><a name="put_caption"></a>CStockPropimpl：:put_标题

调用此方法以将要与控件一起显示的文本设置为"

```
HRESULT STDMETHODCALLTYPE put_Caption(BSTR bstrCaption);
```

### <a name="parameters"></a>参数

*bstrCaption*<br/>
要与控件一起显示的文本。

### <a name="return-value"></a>返回值

返回成功S_OK，或失败时返回错误 HRESULT。

## <a name="cstockpropimplput_drawmode"></a><a name="put_drawmode"></a>CStockPropimpl：:put_DrawMode

调用此方法以设置控件的绘图模式，例如 XOR 笔或反转颜色。

```
HRESULT STDMETHODCALLTYPE put_DrawMode(LONG nDrawMode);
```

### <a name="parameters"></a>参数

*nDrawMode*<br/>
控件的新绘图模式。

### <a name="return-value"></a>返回值

返回成功S_OK，或失败时返回错误 HRESULT。

## <a name="cstockpropimplput_drawstyle"></a><a name="put_drawstyle"></a>CStockPropimpl：:put_DrawStyle

调用此方法以设置控件的绘图样式，例如，实体、虚线或虚线。

```
HRESULT STDMETHODCALLTYPE put_DrawStyle(LONG pnDrawStyle);
```

### <a name="parameters"></a>参数

*nDraw样式*<br/>
控件的新绘图样式。

### <a name="return-value"></a>返回值

返回成功S_OK，或失败时返回错误 HRESULT。

## <a name="cstockpropimplput_drawwidth"></a><a name="put_drawwidth"></a>CStockPropimpl：:put_DrawWidth

调用此方法以设置控件的绘图方法使用的宽度（以像素为单位）。

```
HRESULT STDMETHODCALLTYPE put_DrawWidth(LONG nDrawWidth);
```

### <a name="parameters"></a>参数

*nDrawWidth*<br/>
控件的绘图方法将使用的新宽度。

### <a name="return-value"></a>返回值

返回成功S_OK，或失败时返回错误 HRESULT。

## <a name="cstockpropimplput_enabled"></a><a name="put_enabled"></a>CStockPropimpl：:put_启用

调用此方法以设置指示控件是否启用的标志的值。

```
HRESULT STDMETHODCALLTYPE put_Enabled(VARIANT_BOOL bEnabled);
```

### <a name="parameters"></a>参数

*b 启用*<br/>
如果启用了控件，则为 TRUE。

### <a name="return-value"></a>返回值

返回成功S_OK，或失败时返回错误 HRESULT。

## <a name="cstockpropimplput_fillcolor"></a><a name="put_fillcolor"></a>CStockPropimpl：:put_FillColor

调用此方法以设置控件的填充颜色。

```
HRESULT STDMETHODCALLTYPE put_FillColor(OLE_COLOR clrFillColor);
```

### <a name="parameters"></a>参数

*clrFillColor*<br/>
控件的新填充颜色。

### <a name="return-value"></a>返回值

返回成功S_OK，或失败时返回错误 HRESULT。

## <a name="cstockpropimplput_fillstyle"></a><a name="put_fillstyle"></a>CStockPropimpl：:put_FillStyle

调用此方法以设置控件的填充样式，例如，实心、透明或交叉阴影。

```
HRESULT STDMETHODCALLTYPE put_FillStyle(LONG nFillStyle);
```

### <a name="parameters"></a>参数

*n 填充样式*<br/>
控件的新填充样式。

### <a name="return-value"></a>返回值

返回成功S_OK，或失败时返回错误 HRESULT。

## <a name="cstockpropimplput_font"></a><a name="put_font"></a>CStockPropimpl：:put_Font

调用此方法以设置控件的字体属性。

```
HRESULT STDMETHODCALLTYPE put_Font(IFontDisp* pFont);
```

### <a name="parameters"></a>参数

*pFont*<br/>
指向控件的字体属性的指针。

### <a name="return-value"></a>返回值

返回成功S_OK，或失败时返回错误 HRESULT。

## <a name="cstockpropimplput_forecolor"></a><a name="put_forecolor"></a>CStockPropimpl：:put_前色

调用此方法以设置控件的前景颜色。

```
HRESULT STDMETHODCALLTYPE put_ForeColor(OLE_COLOR clrForeColor);
```

### <a name="parameters"></a>参数

*clrForeColor*<br/>
控件的新前景颜色。

### <a name="return-value"></a>返回值

返回成功S_OK，或失败时返回错误 HRESULT。

## <a name="cstockpropimplput_hwnd"></a><a name="put_hwnd"></a>CStockPropimpl：:put_HWND

此方法返回E_FAIL。

```
HRESULT STDMETHODCALLTYPE put_HWND(LONG_PTR /* hWnd */);
```

### <a name="parameters"></a>参数

*hwnd*<br/>
保留。

### <a name="return-value"></a>返回值

返回E_FAIL。

### <a name="remarks"></a>备注

窗口句柄是只读值。

## <a name="cstockpropimplput_mouseicon"></a><a name="put_mouseicon"></a>CStockPropimpl：:put_鼠标图标

调用此方法可设置鼠标位于控件上时要显示的图形（图标、位图或元文件）的图片属性。

```
HRESULT STDMETHODCALLTYPE put_MouseIcon(IPictureDisp* pPicture);
```

### <a name="parameters"></a>参数

*p图片*<br/>
指向图形的图片属性的指针。

### <a name="return-value"></a>返回值

返回成功S_OK，或失败时返回错误 HRESULT。

## <a name="cstockpropimplput_mousepointer"></a><a name="put_mousepointer"></a>CStockPropimpl：:put_鼠标指针

调用此方法可设置鼠标位于控件上时显示的鼠标指针类型，例如箭头、十字或沙漏。

```
HRESULT STDMETHODCALLTYPE put_MousePointer(LONG nMousePointer);
```

### <a name="parameters"></a>参数

*nMousePointer*<br/>
鼠标指针的类型。

### <a name="return-value"></a>返回值

返回成功S_OK，或失败时返回错误 HRESULT。

## <a name="cstockpropimplput_picture"></a><a name="put_picture"></a>CStockPropimpl：:put_图片

调用此方法以设置要显示的图形（图标、位图或元文件）的图片属性。

```
HRESULT STDMETHODCALLTYPE put_Picture(IPictureDisp* pPicture);
```

### <a name="parameters"></a>参数

*p图片*<br/>
指向图片属性的指针。 有关详细信息[，请参阅 IPictureDisp。](/windows/win32/api/ocidl/nn-ocidl-ipicturedisp)

### <a name="return-value"></a>返回值

返回成功S_OK，或失败时返回错误 HRESULT。

## <a name="cstockpropimplput_readystate"></a><a name="put_readystate"></a>CStockPropimpl：:put_就绪状态

调用此方法以设置控件的就绪状态，例如加载或加载。

```
HRESULT STDMETHODCALLTYPE put_ReadyState(LONG nReadyState);
```

### <a name="parameters"></a>参数

*n 就绪状态*<br/>
控件的就绪状态。

### <a name="return-value"></a>返回值

返回成功S_OK，或失败时返回错误 HRESULT。

## <a name="cstockpropimplput_tabstop"></a><a name="put_tabstop"></a>CStockPropimpl：:put_TabStop

调用此方法以设置指示控件是否为制表位标志的标志。

```
HRESULT STDMETHODCALLTYPE put_TabStop(VARIANT_BOOL bTabStop);
```

### <a name="parameters"></a>参数

*bTabStop*<br/>
如果控件是制表位，则为 TRUE。

### <a name="return-value"></a>返回值

返回成功S_OK，或失败时返回错误 HRESULT。

## <a name="cstockpropimplput_text"></a><a name="put_text"></a>CStockPropimpl：:put_文本

调用此方法以设置控件中显示的文本。

```
HRESULT STDMETHODCALLTYPE put_Text(BSTR bstrText);
```

### <a name="parameters"></a>参数

*bstrText*<br/>
控件中显示的文本。

### <a name="return-value"></a>返回值

返回成功S_OK，或失败时返回错误 HRESULT。

## <a name="cstockpropimplputvalid"></a><a name="put_valid"></a>CStockPropimpl：:p

调用此方法以设置指示控件是否有效的标志。

```
HRESULT STDMETHODCALLTYPE getvalid(VARIANT_BOOL bValid);
```

### <a name="parameters"></a>参数

*b 有效*<br/>
如果控件有效，则为 TRUE。

### <a name="return-value"></a>返回值

返回成功S_OK，或失败时返回错误 HRESULT。

## <a name="cstockpropimplput_window"></a><a name="put_window"></a>CStockPropimpl：:put_窗口

此方法称为[CStockPropimpl：:put_HWND](#put_hwnd)，它返回E_FAIL。

```
HRESULT STDMETHODCALLTYPE put_Window(LONG_PTR hWnd);
```

### <a name="parameters"></a>参数

*hwnd*<br/>
窗口句柄。

### <a name="return-value"></a>返回值

返回E_FAIL。

### <a name="remarks"></a>备注

窗口句柄是只读值。

## <a name="cstockpropimplputref_font"></a><a name="putref_font"></a>CStockPropimpl：:putref_Font

调用此方法以设置控件的字体属性，并带有引用计数。

```
HRESULT STDMETHODCALLTYPE putref_Font(IFontDisp* pFont);
```

### <a name="parameters"></a>参数

*pFont*<br/>
指向控件的字体属性的指针。

### <a name="return-value"></a>返回值

返回成功S_OK，或失败时返回错误 HRESULT。

### <a name="remarks"></a>备注

与[CStockPropImpl：:put_Font](#put_font)相同，但具有参考计数。

## <a name="cstockpropimplputref_mouseicon"></a><a name="putref_mouseicon"></a>CStockPropimpl：:putref_MouseIcon

调用此方法可设置鼠标位于控件上时要显示的图形（图标、位图或元文件）的图片属性，并带有引用计数。

```
HRESULT STDMETHODCALLTYPE putref_MouseIcon(IPictureDisp* pPicture);
```

### <a name="parameters"></a>参数

*p图片*<br/>
指向图形的图片属性的指针。

### <a name="return-value"></a>返回值

返回成功S_OK，或失败时返回错误 HRESULT。

### <a name="remarks"></a>备注

与[CStockPropImpl：:put_MouseIcon](#put_mouseicon)相同，但具有参考计数。

## <a name="cstockpropimplputref_picture"></a><a name="putref_picture"></a>CStockPropImpl：:p乌特雷夫_图片

调用此方法以设置要显示的图形（图标、位图或元文件）的图片属性，并带有引用计数。

```
HRESULT STDMETHODCALLTYPE putref_Picture(IPictureDisp* pPicture);
```

### <a name="parameters"></a>参数

*p图片*<br/>
指向图片属性的指针。 有关详细信息[，请参阅 IPictureDisp。](/windows/win32/api/ocidl/nn-ocidl-ipicturedisp)

### <a name="return-value"></a>返回值

返回成功S_OK，或失败时返回错误 HRESULT。

### <a name="remarks"></a>备注

与[CStockPropImpl：:put_Picture）](#put_picture)相同，但具有参考计数。

## <a name="see-also"></a>另请参阅

[类概述](../../atl/atl-class-overview.md)<br/>
[IDispatchImpl 类](../../atl/reference/idispatchimpl-class.md)
