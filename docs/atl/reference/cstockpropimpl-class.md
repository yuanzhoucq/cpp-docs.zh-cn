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
ms.openlocfilehash: bc349137661d7026e48688f8ef510958de270280
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/21/2020
ms.locfileid: "80075221"
---
# <a name="cstockpropimpl-class"></a>CStockPropImpl 类

此类提供用于支持常用属性值的方法。

> [!IMPORTANT]
> 此类及其成员不能用于在 Windows 运行时中执行的应用程序。

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

#### <a name="parameters"></a>parameters

*T*<br/>
实现控件并从 `CStockPropImpl`派生的类。

*InterfaceName*<br/>
公开常用属性的双重接口。

*piid*<br/>
指向 `InterfaceName`的 IID 的指针。

*plibid*<br/>
一个指针，指向包含 `InterfaceName`定义的类型库的 LIBID。

*wMajor*<br/>
类型库的主版本。 默认值为 1。

*wMinor*<br/>
类型库的次版本。 默认值为 0。

*tihclass*<br/>
用于管理*T*的类型信息的类。默认值为 `CComTypeInfoHolder`。

## <a name="members"></a>成员

### <a name="public-methods"></a>公共方法

|||
|-|-|
|[get_Appearance](#get_appearance)|调用此方法可获取控件使用的绘制样式，例如，平面或三维。|
|[get_AutoSize](#get_autosize)|调用此方法以获取标志的状态，该标志指示控件是否不能为任何其他大小。|
|[get_BackColor](#get_backcolor)|调用此方法可获取控件的背景色。|
|[get_BackStyle](#get_backstyle)|调用此方法可获取控件的背景样式（透明或不透明）。|
|[get_BorderColor](#get_bordercolor)|调用此方法可获取控件的边框颜色。|
|[get_BorderStyle](#get_borderstyle)|调用此方法可获取控件的边框样式。|
|[get_BorderVisible](#get_bordervisible)|调用此方法以获取标志的状态，该标志指示控件的边框是否可见。|
|[get_BorderWidth](#get_borderwidth)|调用此方法可获取控件边框的宽度（以像素为单位）。|
|[get_Caption](#get_caption)|调用此方法可获取对象标题中指定的文本。|
|[get_DrawMode](#get_drawmode)|调用此方法可获取控件的绘制模式，如 XOR 笔或反色。|
|[get_DrawStyle](#get_drawstyle)|调用此方法可获取控件的绘制样式，例如实线、虚线或点线。|
|[get_DrawWidth](#get_drawwidth)|调用此方法可获取控件的绘图方法使用的绘图宽度（以像素为单位）。|
|[get_Enabled](#get_enabled)|调用此方法以获取标志的状态，该标志指示是否已启用控件。|
|[get_FillColor](#get_fillcolor)|调用此方法可获取控件的填充颜色。|
|[get_FillStyle](#get_fillstyle)|调用此方法可获取控件的填充样式，例如，纯色、透明或交叉阴影。|
|[get_Font](#get_font)|调用此方法以获取指向控件的字体属性的指针。|
|[get_ForeColor](#get_forecolor)|调用此方法可获取控件的前景色。|
|[get_HWND](#get_hwnd)|调用此方法以获取与控件关联的窗口句柄。|
|[get_MouseIcon](#get_mouseicon)|调用此方法可获取要在鼠标位于控件上时显示的图形（图标、位图或图元文件）的图片属性。|
|[get_MousePointer](#get_mousepointer)|调用此方法可获取鼠标位于控件上时显示的鼠标指针的类型，例如，箭头、交叉或沙漏。|
|[get_Picture](#get_picture)|调用此方法可获取指向要显示的图形（图标、位图或图元文件）图片属性的指针。|
|[get_ReadyState](#get_readystate)|调用此方法可获取控件的就绪状态，例如，加载或加载。|
|[get_TabStop](#get_tabstop)|调用此方法以获取指示控件是否为制表位的标志。|
|[get_Text](#get_text)|调用此方法以获取与控件一起显示的文本。|
|[getvalid](#get_valid)|调用此方法可获取指示控件是否有效的标志的状态。|
|[get_Window](#get_window)|调用此方法以获取与控件关联的窗口句柄。 与[CStockPropImpl：： get_HWND](#get_hwnd)完全相同。|
|[put_Appearance](#put_appearance)|调用此方法以设置控件使用的绘制样式，例如，平面或三维。|
|[put_AutoSize](#put_autosize)|调用此方法以设置指示控件是否不能为任何其他大小的标志值。|
|[put_BackColor](#put_backcolor)|调用此方法可设置控件的背景色。|
|[put_BackStyle](#put_backstyle)|调用此方法可设置控件的背景样式。|
|[put_BorderColor](#put_bordercolor)|调用此方法可设置控件的边框颜色。|
|[put_BorderStyle](#put_borderstyle)|调用此方法可设置控件的边框样式。|
|[put_BorderVisible](#put_bordervisible)|调用此方法可设置标志的值，该值指示控件的边框是否可见。|
|[put_BorderWidth](#put_borderwidth)|调用此方法以设置控件边框的宽度。|
|[put_Caption](#put_caption)|调用此方法可设置要与控件一起显示的文本。|
|[put_DrawMode](#put_drawmode)|调用此方法以设置控件的绘制模式，例如 XOR 笔或反色。|
|[put_DrawStyle](#put_drawstyle)|调用此方法以设置控件的绘制样式，例如实线、虚线或点线。|
|[put_DrawWidth](#put_drawwidth)|调用此方法以设置控件的绘图方法使用的宽度（以像素为单位）。|
|[put_Enabled](#put_enabled)|调用此方法以设置指示是否启用控件的标志。|
|[put_FillColor](#put_fillcolor)|调用此方法可设置控件的填充颜色。|
|[put_FillStyle](#put_fillstyle)|调用此方法可设置控件的填充样式，例如，纯色、透明或交叉阴影。|
|[put_Font](#put_font)|调用此方法可设置控件的字体属性。|
|[put_ForeColor](#put_forecolor)|调用此方法以设置控件的前景色。|
|[put_HWND](#put_hwnd)|此方法返回 E_FAIL。|
|[put_MouseIcon](#put_mouseicon)|调用此方法可设置要在鼠标位于控件上时显示的图形（图标、位图或图元文件）的图片属性。|
|[put_MousePointer](#put_mousepointer)|调用此方法可设置鼠标位于控件上时显示的鼠标指针的类型，例如，箭头、交叉或沙漏。|
|[put_Picture](#put_picture)|调用此方法以设置要显示的图形的图片属性（图标、位图或图元文件）。|
|[put_ReadyState](#put_readystate)|调用此方法以设置控件的就绪状态，例如，加载或加载。|
|[put_TabStop](#put_tabstop)|调用此方法以设置指示控件是否为制表位的标志值。|
|[put_Text](#put_text)|调用此方法以设置与控件一起显示的文本。|
|[putvalid](#put_valid)|调用此方法以设置指示控件是否有效的标志。|
|[put_Window](#put_window)|此方法调用[CStockPropImpl：:p ut_HWND](#put_hwnd)，这会返回 E_FAIL。|
|[putref_Font](#putref_font)|调用此方法可设置控件的字体属性，具有引用计数。|
|[putref_MouseIcon](#putref_mouseicon)|调用此方法可设置在鼠标位于控件上时要显示的图形（图标、位图或图元文件）的图片属性，具有引用计数。|
|[putref_Picture](#putref_picture)|调用此方法以设置要显示的图形（图标、位图或图元文件）的图片属性，并具有引用计数。|

## <a name="remarks"></a>备注

`CStockPropImpl` 为每个常用属性提供**put**和**get**方法。 这些方法提供设置或获取与每个属性关联的数据成员所需的代码，并在任何属性发生更改时通知并与容器同步。

Visual Studio 通过其向导提供对常用属性的支持。 有关向控件添加常用属性的详细信息，请参阅[ATL 教程](../../atl/active-template-library-atl-tutorial.md)。

为了向后兼容，`CStockPropImpl` 还公开了 `get_Window` 和 `put_Window` 方法，这些方法只是分别调用 `get_HWND` 和 `put_HWND`。 `put_HWND` 的默认实现将返回 E_FAIL，因为 HWND 应为只读属性。

以下属性还具有**putref**实现：

- 字体

- MouseIcon

- Picture

这三个常用属性要求其相应的数据成员为类型 `CComPtr` 或其他一些类，通过赋值运算符提供正确的接口引用计数。

## <a name="inheritance-hierarchy"></a>继承层次结构

`T`

[IDispatchImpl](../../atl/reference/idispatchimpl-class.md)

`CStockPropImpl`

## <a name="requirements"></a>要求

**标头：** atlctl

##  <a name="cstockpropimplget_appearance"></a><a name="get_appearance"></a>CStockPropImpl：： get_Appearance

调用此方法可获取控件使用的绘制样式，例如，平面或三维。

```
HRESULT STDMETHODCALLTYPE get_Appearance(SHORT pnAppearance);
```

### <a name="parameters"></a>parameters

*pnAppearance*<br/>
用于接收控件的绘制样式的变量。

### <a name="return-value"></a>返回值

如果成功，则返回 S_OK; 否则返回错误 HRESULT。

##  <a name="cstockpropimplget_autosize"></a><a name="get_autosize"></a>CStockPropImpl：： get_AutoSize

调用此方法以获取标志的状态，该标志指示控件是否不能为任何其他大小。

```
HRESULT STDMETHODCALLTYPE get_Autosize(VARIANT_BOOL* pbAutoSize);
```

### <a name="parameters"></a>parameters

*pbAutoSize*<br/>
接收标志状态的变量。 如果为 TRUE，则表示控件不能为任何其他大小。

### <a name="return-value"></a>返回值

如果成功，则返回 S_OK; 否则返回错误 HRESULT。

##  <a name="cstockpropimplget_backcolor"></a><a name="get_backcolor"></a>CStockPropImpl：： get_BackColor

调用此方法可获取控件的背景色。

```
HRESULT STDMETHODCALLTYPE get_BackColor(OLE_COLOR* pclrBackColor);
```

### <a name="parameters"></a>parameters

*pclrBackColor*<br/>
用于接收控件的背景色的变量。

### <a name="return-value"></a>返回值

如果成功，则返回 S_OK; 否则返回错误 HRESULT。

##  <a name="cstockpropimplget_backstyle"></a><a name="get_backstyle"></a>CStockPropImpl：： get_BackStyle

调用此方法可获取控件的背景样式（透明或不透明）。

```
HRESULT STDMETHODCALLTYPE get_BackStyle(LONG* pnBackStyle);
```

### <a name="parameters"></a>parameters

*pnBackStyle*<br/>
用于接收控件的背景样式的变量。

### <a name="return-value"></a>返回值

如果成功，则返回 S_OK; 否则返回错误 HRESULT。

##  <a name="cstockpropimplget_bordercolor"></a><a name="get_bordercolor"></a>CStockPropImpl：： get_BorderColor

调用此方法可获取控件的边框颜色。

```
HRESULT STDMETHODCALLTYPE get_BorderColor(OLE_COLOR* pclrBorderColor);
```

### <a name="parameters"></a>parameters

*pclrBorderColor*<br/>
用于接收控件的边框颜色的变量。

### <a name="return-value"></a>返回值

如果成功，则返回 S_OK; 否则返回错误 HRESULT。

##  <a name="cstockpropimplget_borderstyle"></a><a name="get_borderstyle"></a>CStockPropImpl：： get_BorderStyle

调用此方法可获取控件的边框样式。

```
HRESULT STDMETHODCALLTYPE get_BorderStyle(LONG* pnBorderStyle);
```

### <a name="parameters"></a>parameters

*pnBorderStyle*<br/>
用于接收控件的边框样式的变量。

### <a name="return-value"></a>返回值

如果成功，则返回 S_OK; 否则返回错误 HRESULT。

##  <a name="cstockpropimplget_bordervisible"></a><a name="get_bordervisible"></a>CStockPropImpl：： get_BorderVisible

调用此方法以获取标志的状态，该标志指示控件的边框是否可见。

```
HRESULT STDMETHODCALLTYPE get_BorderVisible(VARIANT_BOOL* pbBorderVisible);
```

### <a name="parameters"></a>parameters

*pbBorderVisible*<br/>
接收标志状态的变量。 如果为 TRUE，则表示控件的边框可见。

### <a name="return-value"></a>返回值

如果成功，则返回 S_OK; 否则返回错误 HRESULT。

##  <a name="cstockpropimplget_borderwidth"></a><a name="get_borderwidth"></a>CStockPropImpl：： get_BorderWidth

调用此方法可获取控件边框的宽度。

```
HRESULT STDMETHODCALLTYPE get_BorderWidth(LONG* pnBorderWidth);
```

### <a name="parameters"></a>parameters

*pnBorderWidth*<br/>
用于接收控件的边框宽度的变量。

### <a name="return-value"></a>返回值

如果成功，则返回 S_OK; 否则返回错误 HRESULT。

##  <a name="cstockpropimplget_caption"></a><a name="get_caption"></a>CStockPropImpl：： get_Caption

调用此方法可获取对象标题中指定的文本。

```
HRESULT STDMETHODCALLTYPE get_Caption(BSTR* pbstrCaption);
```

### <a name="parameters"></a>parameters

*pbstrCaption*<br/>
要与控件一起显示的文本。

### <a name="return-value"></a>返回值

如果成功，则返回 S_OK; 否则返回错误 HRESULT。

##  <a name="cstockpropimplget_drawmode"></a><a name="get_drawmode"></a>CStockPropImpl：： get_DrawMode

调用此方法可获取控件的绘制模式，如 XOR 笔或反色。

```
HRESULT STDMETHODCALLTYPE get_DrawMode(LONG* pnDrawMode);
```

### <a name="parameters"></a>parameters

*pnDrawMode*<br/>
用于接收控件的绘制模式的变量。

### <a name="return-value"></a>返回值

如果成功，则返回 S_OK; 否则返回错误 HRESULT。

##  <a name="cstockpropimplget_drawstyle"></a><a name="get_drawstyle"></a>CStockPropImpl：： get_DrawStyle

调用此方法可获取控件的绘制样式，例如实线、虚线或点线。

```
HRESULT STDMETHODCALLTYPE get_DrawStyle(LONG* pnDrawStyle);
```

### <a name="parameters"></a>parameters

*pnDrawStyle*<br/>
用于接收控件的绘制样式的变量。

### <a name="return-value"></a>返回值

如果成功，则返回 S_OK; 否则返回错误 HRESULT。

##  <a name="cstockpropimplget_drawwidth"></a><a name="get_drawwidth"></a>CStockPropImpl：： get_DrawWidth

调用此方法可获取控件的绘图方法使用的绘图宽度（以像素为单位）。

```
HRESULT STDMETHODCALLTYPE get_DrawWidth(LONG* pnDrawWidth);
```

### <a name="parameters"></a>parameters

*pnDrawWidth*<br/>
用于接收控件的宽度值（以像素为单位）的变量。

### <a name="return-value"></a>返回值

如果成功，则返回 S_OK; 否则返回错误 HRESULT。

##  <a name="cstockpropimplget_enabled"></a><a name="get_enabled"></a>CStockPropImpl：： get_Enabled

调用此方法以获取标志的状态，该标志指示是否已启用控件。

```
HRESULT STDMETHODCALLTYPE get_Enabled(VARIANT_BOOL* pbEnabled);
```

### <a name="parameters"></a>parameters

*pbEnabled*<br/>
接收标志状态的变量。 如果为 TRUE，则表示已启用控件。

### <a name="return-value"></a>返回值

如果成功，则返回 S_OK; 否则返回错误 HRESULT。

##  <a name="cstockpropimplget_fillcolor"></a><a name="get_fillcolor"></a>CStockPropImpl：： get_FillColor

调用此方法可获取控件的填充颜色。

```
HRESULT STDMETHODCALLTYPE get_FillColor(OLE_COLOR* pclrFillColor);
```

### <a name="parameters"></a>parameters

*pclrFillColor*<br/>
用于接收控件的填充颜色的变量。

### <a name="return-value"></a>返回值

如果成功，则返回 S_OK; 否则返回错误 HRESULT。

##  <a name="cstockpropimplget_fillstyle"></a><a name="get_fillstyle"></a>CStockPropImpl：： get_FillStyle

调用此方法可获取控件的填充样式，例如，纯色、透明或 crosshatched。

```
HRESULT STDMETHODCALLTYPE get_FillStyle(LONG* pnFillStyle);
```

### <a name="parameters"></a>parameters

*pnFillStyle*<br/>
接收控件填充样式的变量。

### <a name="return-value"></a>返回值

如果成功，则返回 S_OK; 否则返回错误 HRESULT。

##  <a name="cstockpropimplget_font"></a><a name="get_font"></a>CStockPropImpl：： get_Font

调用此方法以获取指向控件的字体属性的指针。

```
HRESULT STDMETHODCALLTYPE get_Font(IFontDisp** ppFont);
```

### <a name="parameters"></a>parameters

*ppFont*<br/>
一个变量，该变量接收指向控件的字体属性的指针。

### <a name="return-value"></a>返回值

如果成功，则返回 S_OK; 否则返回错误 HRESULT。

##  <a name="cstockpropimplget_forecolor"></a><a name="get_forecolor"></a>CStockPropImpl：： get_ForeColor

调用此方法可获取控件的前景色。

```
HRESULT STDMETHODCALLTYPE get_ForeColor(OLE_COLOR* pclrForeColor);
```

### <a name="parameters"></a>parameters

*pclrForeColor*<br/>
用于接收控件前景色的变量。

### <a name="return-value"></a>返回值

如果成功，则返回 S_OK; 否则返回错误 HRESULT。

##  <a name="cstockpropimplget_hwnd"></a><a name="get_hwnd"></a>CStockPropImpl：： get_HWND

调用此方法以获取与控件关联的窗口句柄。

```
HRESULT STDMETHODCALLTYPE get_HWND(LONG_PTR* phWnd);
```

### <a name="parameters"></a>parameters

*phWnd*<br/>
与控件关联的窗口句柄。

### <a name="return-value"></a>返回值

如果成功，则返回 S_OK; 否则返回错误 HRESULT。

##  <a name="cstockpropimplget_mouseicon"></a><a name="get_mouseicon"></a>CStockPropImpl：： get_MouseIcon

调用此方法可获取要在鼠标位于控件上时显示的图形（图标、位图或图元文件）的图片属性。

```
HRESULT STDMETHODCALLTYPE get_MouseIcon(IPictureDisp** ppPicture);
```

### <a name="parameters"></a>parameters

*ppPicture*<br/>
一个变量，该变量接收指向图形的图片属性的指针。

### <a name="return-value"></a>返回值

如果成功，则返回 S_OK; 否则返回错误 HRESULT。

##  <a name="cstockpropimplget_mousepointer"></a><a name="get_mousepointer"></a>CStockPropImpl：： get_MousePointer

调用此方法可获取鼠标位于控件上时显示的鼠标指针的类型，例如，箭头、交叉或沙漏。

```
HRESULT STDMETHODCALLTYPE get_MousePointer(LONG* pnMousePointer);
```

### <a name="parameters"></a>parameters

*pnMousePointer*<br/>
接收鼠标指针类型的变量。

### <a name="return-value"></a>返回值

如果成功，则返回 S_OK; 否则返回错误 HRESULT。

##  <a name="cstockpropimplget_picture"></a><a name="get_picture"></a>CStockPropImpl：： get_Picture

调用此方法可获取指向要显示的图形（图标、位图或图元文件）图片属性的指针。

```
HRESULT STDMETHODCALLTYPE get_Picture(IPictureDisp** ppPicture);
```

### <a name="parameters"></a>parameters

*ppPicture*<br/>
一个变量，该变量接收指向图片属性的指针。 有关更多详细信息，请参阅[IPictureDisp](/windows/win32/api/ocidl/nn-ocidl-ipicturedisp) 。

### <a name="return-value"></a>返回值

如果成功，则返回 S_OK; 否则返回错误 HRESULT。

##  <a name="cstockpropimplget_readystate"></a><a name="get_readystate"></a>CStockPropImpl：： get_ReadyState

调用此方法可获取控件的就绪状态，例如，加载或加载。

```
HRESULT STDMETHODCALLTYPE get_ReadyState(LONG* pnReadyState);
```

### <a name="parameters"></a>parameters

*pnReadyState*<br/>
接收控件就绪状态的变量。

### <a name="return-value"></a>返回值

如果成功，则返回 S_OK; 否则返回错误 HRESULT。

##  <a name="cstockpropimplget_tabstop"></a><a name="get_tabstop"></a>CStockPropImpl：： get_TabStop

调用此方法以获取标志的状态，该标志指示控件是否为制表位。

```
HRESULT STDMETHODCALLTYPE get_TabStop(VARIANT_BOOL* pbTabStop);
```

### <a name="parameters"></a>parameters

*pbTabStop*<br/>
接收标志状态的变量。 如果为 TRUE，则指示控件为制表位。

### <a name="return-value"></a>返回值

如果成功，则返回 S_OK; 否则返回错误 HRESULT。

##  <a name="cstockpropimplget_text"></a><a name="get_text"></a>CStockPropImpl：： get_Text

调用此方法以获取与控件一起显示的文本。

```
HRESULT STDMETHODCALLTYPE get_Text(BSTR* pbstrText);
```

### <a name="parameters"></a>parameters

*pbstrText*<br/>
与控件一起显示的文本。

### <a name="return-value"></a>返回值

如果成功，则返回 S_OK; 否则返回错误 HRESULT。

##  <a name="cstockpropimplgetvalid"></a><a name="get_valid"></a>CStockPropImpl::getvalid

调用此方法可获取指示控件是否有效的标志的状态。

```
HRESULT STDMETHODCALLTYPE getvalid(VARIANT_BOOL* pbValid);
```

### <a name="parameters"></a>parameters

*pbValid*<br/>
接收标志状态的变量。 如果为 TRUE，则指示控件有效。

### <a name="return-value"></a>返回值

如果成功，则返回 S_OK; 否则返回错误 HRESULT。

##  <a name="cstockpropimplget_window"></a><a name="get_window"></a>CStockPropImpl：： get_Window

调用此方法以获取与控件关联的窗口句柄。 与[CStockPropImpl：： get_HWND](#get_hwnd)完全相同。

```
HRESULT STDMETHODCALLTYPE get_Window(LONG_PTR* phWnd);
```

### <a name="parameters"></a>parameters

*phWnd*<br/>
与控件关联的窗口句柄。

### <a name="return-value"></a>返回值

如果成功，则返回 S_OK; 否则返回错误 HRESULT。

##  <a name="cstockpropimplput_appearance"></a><a name="put_appearance"></a>CStockPropImpl：:p ut_Appearance

调用此方法以设置控件使用的绘制样式，例如，平面或三维。

```
HRESULT STDMETHODCALLTYPE put_Appearance(SHORT nAppearance);
```

### <a name="parameters"></a>parameters

*nAppearance*<br/>
控件使用的新绘制样式。

### <a name="return-value"></a>返回值

如果成功，则返回 S_OK; 否则返回错误 HRESULT。

##  <a name="cstockpropimplput_autosize"></a><a name="put_autosize"></a>CStockPropImpl：:p ut_AutoSize

调用此方法可设置标志的值，该值指示控件是否不能为任何其他大小。

```
HRESULT STDMETHODCALLTYPE put_AutoSize(VARIANT_BOOL bAutoSize,);
```

### <a name="parameters"></a>parameters

*bAutoSize*<br/>
如果控件不能为任何其他大小，则为 TRUE。

### <a name="return-value"></a>返回值

如果成功，则返回 S_OK; 否则返回错误 HRESULT。

##  <a name="cstockpropimplput_backcolor"></a><a name="put_backcolor"></a>CStockPropImpl：:p ut_BackColor

调用此方法可设置控件的背景色。

```
HRESULT STDMETHODCALLTYPE put_BackColor(OLE_COLOR clrBackColor);
```

### <a name="parameters"></a>parameters

*clrBackColor*<br/>
新的控件背景色。

### <a name="return-value"></a>返回值

如果成功，则返回 S_OK; 否则返回错误 HRESULT。

##  <a name="cstockpropimplput_backstyle"></a><a name="put_backstyle"></a>CStockPropImpl：:p ut_BackStyle

调用此方法可设置控件的背景样式。

```
HRESULT STDMETHODCALLTYPE put_BackStyle(LONG nBackStyle);
```

### <a name="parameters"></a>parameters

*nBackStyle*<br/>
新控件的背景样式。

### <a name="return-value"></a>返回值

如果成功，则返回 S_OK; 否则返回错误 HRESULT。

##  <a name="cstockpropimplput_bordercolor"></a><a name="put_bordercolor"></a>CStockPropImpl：:p ut_BorderColor

调用此方法可设置控件的边框颜色。

```
HRESULT STDMETHODCALLTYPE put_BorderColor(OLE_COLOR clrBorderColor);
```

### <a name="parameters"></a>parameters

*clrBorderColor*<br/>
新的边框颜色。 OLE_COLOR 的数据类型在内部表示为32位长整数。

### <a name="return-value"></a>返回值

如果成功，则返回 S_OK; 否则返回错误 HRESULT。

##  <a name="cstockpropimplput_borderstyle"></a><a name="put_borderstyle"></a>CStockPropImpl：:p ut_BorderStyle

调用此方法可设置控件的边框样式。

```
HRESULT STDMETHODCALLTYPE put_BorderStyle(LONG nBorderStyle);
```

### <a name="parameters"></a>parameters

*nBorderStyle*<br/>
新的边框样式。

### <a name="return-value"></a>返回值

如果成功，则返回 S_OK; 否则返回错误 HRESULT。

##  <a name="cstockpropimplput_bordervisible"></a><a name="put_bordervisible"></a>CStockPropImpl：:p ut_BorderVisible

调用此方法可设置标志的值，该值指示控件的边框是否可见。

```
HRESULT STDMETHODCALLTYPE put_BorderVisible(VARIANT_BOOL bBorderVisible);
```

### <a name="parameters"></a>parameters

*bBorderVisible*<br/>
如果边框可见，则为 TRUE。

### <a name="return-value"></a>返回值

如果成功，则返回 S_OK; 否则返回错误 HRESULT。

##  <a name="cstockpropimplput_borderwidth"></a><a name="put_borderwidth"></a>CStockPropImpl：:p ut_BorderWidth

调用此方法以设置控件边框的宽度。

```
HRESULT STDMETHODCALLTYPE put_BorderWidth(LONG nBorderWidth);
```

### <a name="parameters"></a>parameters

*nBorderWidth*<br/>
控件边框的新宽度。

### <a name="return-value"></a>返回值

如果成功，则返回 S_OK; 否则返回错误 HRESULT。

##  <a name="cstockpropimplput_caption"></a><a name="put_caption"></a>CStockPropImpl：:p ut_Caption

调用此方法可设置要与控件一起显示的文本。

```
HRESULT STDMETHODCALLTYPE put_Caption(BSTR bstrCaption);
```

### <a name="parameters"></a>parameters

*bstrCaption*<br/>
要与控件一起显示的文本。

### <a name="return-value"></a>返回值

如果成功，则返回 S_OK; 否则返回错误 HRESULT。

##  <a name="cstockpropimplput_drawmode"></a><a name="put_drawmode"></a>CStockPropImpl：:p ut_DrawMode

调用此方法以设置控件的绘制模式，例如 XOR 笔或反色。

```
HRESULT STDMETHODCALLTYPE put_DrawMode(LONG nDrawMode);
```

### <a name="parameters"></a>parameters

*nDrawMode*<br/>
控件的新绘制模式。

### <a name="return-value"></a>返回值

如果成功，则返回 S_OK; 否则返回错误 HRESULT。

##  <a name="cstockpropimplput_drawstyle"></a><a name="put_drawstyle"></a>CStockPropImpl：:p ut_DrawStyle

调用此方法以设置控件的绘制样式，例如实线、虚线或点线。

```
HRESULT STDMETHODCALLTYPE put_DrawStyle(LONG pnDrawStyle);
```

### <a name="parameters"></a>parameters

*nDrawStyle*<br/>
控件的新绘制样式。

### <a name="return-value"></a>返回值

如果成功，则返回 S_OK; 否则返回错误 HRESULT。

##  <a name="cstockpropimplput_drawwidth"></a><a name="put_drawwidth"></a>CStockPropImpl：:p ut_DrawWidth

调用此方法以设置控件的绘图方法使用的宽度（以像素为单位）。

```
HRESULT STDMETHODCALLTYPE put_DrawWidth(LONG nDrawWidth);
```

### <a name="parameters"></a>parameters

*nDrawWidth*<br/>
控件的绘图方法使用的新宽度。

### <a name="return-value"></a>返回值

如果成功，则返回 S_OK; 否则返回错误 HRESULT。

##  <a name="cstockpropimplput_enabled"></a><a name="put_enabled"></a>CStockPropImpl：:p ut_Enabled

调用此方法以设置指示是否启用控件的标志的值。

```
HRESULT STDMETHODCALLTYPE put_Enabled(VARIANT_BOOL bEnabled);
```

### <a name="parameters"></a>parameters

*bEnabled*<br/>
如果启用控件，则为 TRUE。

### <a name="return-value"></a>返回值

如果成功，则返回 S_OK; 否则返回错误 HRESULT。

##  <a name="cstockpropimplput_fillcolor"></a><a name="put_fillcolor"></a>CStockPropImpl：:p ut_FillColor

调用此方法可设置控件的填充颜色。

```
HRESULT STDMETHODCALLTYPE put_FillColor(OLE_COLOR clrFillColor);
```

### <a name="parameters"></a>parameters

*clrFillColor*<br/>
控件的新填充颜色。

### <a name="return-value"></a>返回值

如果成功，则返回 S_OK; 否则返回错误 HRESULT。

##  <a name="cstockpropimplput_fillstyle"></a><a name="put_fillstyle"></a>CStockPropImpl：:p ut_FillStyle

调用此方法可设置控件的填充样式，例如，纯色、透明或交叉阴影。

```
HRESULT STDMETHODCALLTYPE put_FillStyle(LONG nFillStyle);
```

### <a name="parameters"></a>parameters

*nFillStyle*<br/>
控件的新填充样式。

### <a name="return-value"></a>返回值

如果成功，则返回 S_OK; 否则返回错误 HRESULT。

##  <a name="cstockpropimplput_font"></a><a name="put_font"></a>CStockPropImpl：:p ut_Font

调用此方法可设置控件的字体属性。

```
HRESULT STDMETHODCALLTYPE put_Font(IFontDisp* pFont);
```

### <a name="parameters"></a>parameters

*pFont*<br/>
指向控件的字体属性的指针。

### <a name="return-value"></a>返回值

如果成功，则返回 S_OK; 否则返回错误 HRESULT。

##  <a name="cstockpropimplput_forecolor"></a><a name="put_forecolor"></a>CStockPropImpl：:p ut_ForeColor

调用此方法以设置控件的前景色。

```
HRESULT STDMETHODCALLTYPE put_ForeColor(OLE_COLOR clrForeColor);
```

### <a name="parameters"></a>parameters

*clrForeColor*<br/>
控件的新前景色。

### <a name="return-value"></a>返回值

如果成功，则返回 S_OK; 否则返回错误 HRESULT。

##  <a name="cstockpropimplput_hwnd"></a><a name="put_hwnd"></a>CStockPropImpl：:p ut_HWND

此方法返回 E_FAIL。

```
HRESULT STDMETHODCALLTYPE put_HWND(LONG_PTR /* hWnd */);
```

### <a name="parameters"></a>parameters

*hWnd*<br/>
保留。

### <a name="return-value"></a>返回值

返回 E_FAIL。

### <a name="remarks"></a>备注

窗口句柄是只读值。

##  <a name="cstockpropimplput_mouseicon"></a><a name="put_mouseicon"></a>CStockPropImpl：:p ut_MouseIcon

调用此方法可设置要在鼠标位于控件上时显示的图形（图标、位图或图元文件）的图片属性。

```
HRESULT STDMETHODCALLTYPE put_MouseIcon(IPictureDisp* pPicture);
```

### <a name="parameters"></a>parameters

*pPicture*<br/>
指向图形的图片属性的指针。

### <a name="return-value"></a>返回值

如果成功，则返回 S_OK; 否则返回错误 HRESULT。

##  <a name="cstockpropimplput_mousepointer"></a><a name="put_mousepointer"></a>CStockPropImpl：:p ut_MousePointer

调用此方法可设置鼠标位于控件上时显示的鼠标指针的类型，例如，箭头、交叉或沙漏。

```
HRESULT STDMETHODCALLTYPE put_MousePointer(LONG nMousePointer);
```

### <a name="parameters"></a>parameters

*nMousePointer*<br/>
鼠标指针的类型。

### <a name="return-value"></a>返回值

如果成功，则返回 S_OK; 否则返回错误 HRESULT。

##  <a name="cstockpropimplput_picture"></a><a name="put_picture"></a>CStockPropImpl：:p ut_Picture

调用此方法以设置要显示的图形的图片属性（图标、位图或图元文件）。

```
HRESULT STDMETHODCALLTYPE put_Picture(IPictureDisp* pPicture);
```

### <a name="parameters"></a>parameters

*pPicture*<br/>
指向图片属性的指针。 有关更多详细信息，请参阅[IPictureDisp](/windows/win32/api/ocidl/nn-ocidl-ipicturedisp) 。

### <a name="return-value"></a>返回值

如果成功，则返回 S_OK; 否则返回错误 HRESULT。

##  <a name="cstockpropimplput_readystate"></a><a name="put_readystate"></a>CStockPropImpl：:p ut_ReadyState

调用此方法以设置控件的就绪状态，例如，加载或加载。

```
HRESULT STDMETHODCALLTYPE put_ReadyState(LONG nReadyState);
```

### <a name="parameters"></a>parameters

*nReadyState*<br/>
控件的就绪状态。

### <a name="return-value"></a>返回值

如果成功，则返回 S_OK; 否则返回错误 HRESULT。

##  <a name="cstockpropimplput_tabstop"></a><a name="put_tabstop"></a>CStockPropImpl：:p ut_TabStop

调用此方法以设置指示控件是否为制表位的标志。

```
HRESULT STDMETHODCALLTYPE put_TabStop(VARIANT_BOOL bTabStop);
```

### <a name="parameters"></a>parameters

*bTabStop*<br/>
如果控件是制表位，则为 TRUE。

### <a name="return-value"></a>返回值

如果成功，则返回 S_OK; 否则返回错误 HRESULT。

##  <a name="cstockpropimplput_text"></a><a name="put_text"></a>CStockPropImpl：:p ut_Text

调用此方法以设置与控件一起显示的文本。

```
HRESULT STDMETHODCALLTYPE put_Text(BSTR bstrText);
```

### <a name="parameters"></a>parameters

*bstrText*<br/>
与控件一起显示的文本。

### <a name="return-value"></a>返回值

如果成功，则返回 S_OK; 否则返回错误 HRESULT。

##  <a name="cstockpropimplputvalid"></a><a name="put_valid"></a>CStockPropImpl：:p utvalid

调用此方法以设置指示控件是否有效的标志。

```
HRESULT STDMETHODCALLTYPE getvalid(VARIANT_BOOL bValid);
```

### <a name="parameters"></a>parameters

*bValid*<br/>
如果控件有效，则为 TRUE。

### <a name="return-value"></a>返回值

如果成功，则返回 S_OK; 否则返回错误 HRESULT。

##  <a name="cstockpropimplput_window"></a><a name="put_window"></a>CStockPropImpl：:p ut_Window

此方法调用[CStockPropImpl：:p ut_HWND](#put_hwnd)，这会返回 E_FAIL。

```
HRESULT STDMETHODCALLTYPE put_Window(LONG_PTR hWnd);
```

### <a name="parameters"></a>parameters

*hWnd*<br/>
窗口句柄。

### <a name="return-value"></a>返回值

返回 E_FAIL。

### <a name="remarks"></a>备注

窗口句柄是只读值。

##  <a name="cstockpropimplputref_font"></a><a name="putref_font"></a>CStockPropImpl：:p utref_Font

调用此方法可设置控件的字体属性，具有引用计数。

```
HRESULT STDMETHODCALLTYPE putref_Font(IFontDisp* pFont);
```

### <a name="parameters"></a>parameters

*pFont*<br/>
指向控件的字体属性的指针。

### <a name="return-value"></a>返回值

如果成功，则返回 S_OK; 否则返回错误 HRESULT。

### <a name="remarks"></a>备注

与 CStockPropImpl 相同[：:p ut_Font](#put_font)，但具有引用计数。

##  <a name="cstockpropimplputref_mouseicon"></a><a name="putref_mouseicon"></a>CStockPropImpl：:p utref_MouseIcon

调用此方法可设置在鼠标位于控件上时要显示的图形（图标、位图或图元文件）的图片属性，具有引用计数。

```
HRESULT STDMETHODCALLTYPE putref_MouseIcon(IPictureDisp* pPicture);
```

### <a name="parameters"></a>parameters

*pPicture*<br/>
指向图形的图片属性的指针。

### <a name="return-value"></a>返回值

如果成功，则返回 S_OK; 否则返回错误 HRESULT。

### <a name="remarks"></a>备注

与 CStockPropImpl 相同[：:p ut_MouseIcon](#put_mouseicon)，但具有引用计数。

##  <a name="cstockpropimplputref_picture"></a><a name="putref_picture"></a>CStockPropImpl：:p utref_Picture

调用此方法以设置要显示的图形（图标、位图或图元文件）的图片属性，并具有引用计数。

```
HRESULT STDMETHODCALLTYPE putref_Picture(IPictureDisp* pPicture);
```

### <a name="parameters"></a>parameters

*pPicture*<br/>
指向图片属性的指针。 有关更多详细信息，请参阅[IPictureDisp](/windows/win32/api/ocidl/nn-ocidl-ipicturedisp) 。

### <a name="return-value"></a>返回值

如果成功，则返回 S_OK; 否则返回错误 HRESULT。

### <a name="remarks"></a>备注

与 CStockPropImpl 相同[：:p ut_Picture](#put_picture)，但具有引用计数。

## <a name="see-also"></a>另请参阅

[类概述](../../atl/atl-class-overview.md)<br/>
[IDispatchImpl 类](../../atl/reference/idispatchimpl-class.md)
