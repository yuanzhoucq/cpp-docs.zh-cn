---
title: CFontHolder 类
ms.date: 11/04/2016
f1_keywords:
- CFontHolder
- AFXCTL/CFontHolder
- AFXCTL/CFontHolder::CFontHolder
- AFXCTL/CFontHolder::GetDisplayString
- AFXCTL/CFontHolder::GetFontDispatch
- AFXCTL/CFontHolder::GetFontHandle
- AFXCTL/CFontHolder::InitializeFont
- AFXCTL/CFontHolder::QueryTextMetrics
- AFXCTL/CFontHolder::ReleaseFont
- AFXCTL/CFontHolder::Select
- AFXCTL/CFontHolder::SetFont
- AFXCTL/CFontHolder::m_pFont
helpviewer_keywords:
- CFontHolder [MFC], CFontHolder
- CFontHolder [MFC], GetDisplayString
- CFontHolder [MFC], GetFontDispatch
- CFontHolder [MFC], GetFontHandle
- CFontHolder [MFC], InitializeFont
- CFontHolder [MFC], QueryTextMetrics
- CFontHolder [MFC], ReleaseFont
- CFontHolder [MFC], Select
- CFontHolder [MFC], SetFont
- CFontHolder [MFC], m_pFont
ms.assetid: 728ab472-0c97-440d-889f-1324c6e1b6b8
ms.openlocfilehash: 36fbebc39101c5534bd52d4f79fee5286487a6e0
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/22/2020
ms.locfileid: "81754996"
---
# <a name="cfontholder-class"></a>CFontHolder 类

实现常用字体属性并封装 Windows 字体对象和 `IFont` 接口的功能。

## <a name="syntax"></a>语法

```
class CFontHolder
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[CFontHolder：C方霍尔德](#cfontholder)|构造 `CFontHolder` 对象。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CFontHolder：：获取显示字符串](#getdisplaystring)|检索容器属性浏览器中显示的字符串。|
|[CFontHolder：获取方调度](#getfontdispatch)|返回字体的`IDispatch`界面。|
|[CFontHolder：：获取方瑟柄](#getfonthandle)|将句柄返回到 Windows 字体。|
|[CFontHolder：：初始化字体](#initializefont)|初始化`CFontHolder`对象。|
|[CFontHolder：：查询文本参数](#querytextmetrics)|检索相关字体的信息。|
|[CFont持有人：：释放字体](#releasefont)|断开`CFontHolder`对象与 和`IFont``IFontNotification`接口的连接。|
|[CFontHolder：：选择](#select)|在设备上下文中选择字体资源。|
|[CFontHolder：：设置字体](#setfont)|将`CFontHolder`对象连接到`IFont`接口。|

### <a name="public-data-members"></a>公共数据成员

|名称|说明|
|----------|-----------------|
|[CFontHolder：：m_pFont](#m_pfont)|指向`CFontHolder`对象接口的`IFont`指针。|

## <a name="remarks"></a>备注

`CFontHolder`没有基类。

使用此类可实现控件的自定义字体属性。 有关创建此类属性的信息，请参阅["ActiveX 控件：使用字体](../../mfc/mfc-activex-controls-using-fonts.md)"一文。

## <a name="inheritance-hierarchy"></a>继承层次结构

`CFontHolder`

## <a name="requirements"></a>要求

**标题：** afxctl.h

## <a name="cfontholdercfontholder"></a><a name="cfontholder"></a>CFontHolder：C方霍尔德

构造 `CFontHolder` 对象。

```
explicit CFontHolder(LPPROPERTYNOTIFYSINK pNotify);
```

### <a name="parameters"></a>参数

*p 通知*<br/>
指向字体界面的`IPropertyNotifySink`指针。

### <a name="remarks"></a>备注

在使用结果`InitializeFont`对象之前，必须调用它来初始化结果对象。

## <a name="cfontholdergetdisplaystring"></a><a name="getdisplaystring"></a>CFontHolder：：获取显示字符串

检索可在容器的属性浏览器中显示的字符串。

```
BOOL GetDisplayString(CString& strValue);
```

### <a name="parameters"></a>参数

*strValue*<br/>
引用用于保存显示字符串的[CString。](../../atl-mfc-shared/reference/cstringt-class.md)

### <a name="return-value"></a>返回值

如果已成功检索字符串，则非零;否则 0。

## <a name="cfontholdergetfontdispatch"></a><a name="getfontdispatch"></a>CFontHolder：获取方调度

调用此功能以检索指向字体调度界面的指针。

```
LPFONTDISP GetFontDispatch();
```

### <a name="return-value"></a>返回值

指向`CFontHolder`对象接口的`IFontDisp`指针。 请注意，调用`GetFontDispatch`的函数在使用此`IUnknown::Release`接口指针时必须调用它。

### <a name="remarks"></a>备注

呼叫`InitializeFont`前呼叫`GetFontDispatch`。

## <a name="cfontholdergetfonthandle"></a><a name="getfonthandle"></a>CFontHolder：：获取方瑟柄

调用此函数以获取 Windows 字体的句柄。

```
HFONT GetFontHandle();

HFONT GetFontHandle(
    long cyLogical,
    long cyHimetric);
```

### <a name="parameters"></a>参数

*cyLogic*<br/>
以逻辑单位表示绘制控件的矩形的高度。

*环测量*<br/>
控件的高度（以MM_HIMETRIC单位为单位）。

### <a name="return-value"></a>返回值

字体对象的句柄;否则 NULL。

### <a name="remarks"></a>备注

*cyLogic*和*cyHimetric*的比率用于计算以MM_HIMETRIC为单位表示的字体点大小的正确显示大小：

显示大小 = （ *cyLogic* / *cyhimetric*） X 字体大小

没有参数的版本会为屏幕返回正确大小的字体的句柄。

## <a name="cfontholderinitializefont"></a><a name="initializefont"></a>CFontHolder：：初始化字体

初始化`CFontHolder`对象。

```cpp
void InitializeFont(
    const FONTDESC* pFontDesc = NULL,
    LPDISPATCH pFontDispAmbient = NULL);
```

### <a name="parameters"></a>参数

*普丰德斯茨*<br/>
指向指定字体特征的字体描述结构 （ [FONTDESC](/windows/win32/api/olectl/ns-olectl-fontdesc)） 的指针。

*pFontDisp环境*<br/>
指向容器的环境字体属性的指针。

### <a name="remarks"></a>备注

如果*pFontDispAmbient*不是 NULL，则`CFontHolder`对象将连接到容器的环境字体`IFont`属性使用的接口的克隆。

如果*pFontDispAmbient*为 NULL，则从*pFontDesc*指向的字体说明创建新的字体对象，或者从默认说明创建*pFontDesc（如果 pFontDesc*为 NULL）。

构造`CFontHolder`对象后调用此函数。

## <a name="cfontholderm_pfont"></a><a name="m_pfont"></a>CFontHolder：：m_pFont

指向`CFontHolder`对象接口的`IFont`指针。

```
LPFONT m_pFont;
```

## <a name="cfontholderquerytextmetrics"></a><a name="querytextmetrics"></a>CFontHolder：：查询文本参数

检索`CFontHolder`对象表示的物理字体的信息。

```cpp
void QueryTextMetrics(LPTEXTMETRIC lptm);
```

### <a name="parameters"></a>参数

*lptm*<br/>
指向将接收信息的[TEXTMETRIC](/windows/win32/api/wingdi/ns-wingdi-textmetricw)结构的指针。

## <a name="cfontholderreleasefont"></a><a name="releasefont"></a>CFont持有人：：释放字体

此函数断开`CFontHolder`对象与其`IFont`接口的连接。

```cpp
void ReleaseFont();
```

## <a name="cfontholderselect"></a><a name="select"></a>CFontHolder：：选择

调用此功能以在指定的设备上下文中选择控件的字体。

```
CFont* Select(
    CDC* pDC,
    long cyLogical,
    long cyHimetric);
```

### <a name="parameters"></a>参数

*pDC*<br/>
选择字体的设备上下文。

*cyLogic*<br/>
以逻辑单位表示绘制控件的矩形的高度。

*环测量*<br/>
控件的高度（以MM_HIMETRIC单位为单位）。

### <a name="return-value"></a>返回值

指向要替换的字体的指针。

### <a name="remarks"></a>备注

有关*cyLogic*和*cyHimetric*参数的讨论，请参阅[GetFontHandle。](#getfonthandle)

## <a name="cfontholdersetfont"></a><a name="setfont"></a>CFontHolder：：设置字体

释放任何现有字体并将`CFontHolder`对象连接到`IFont`接口。

```cpp
void SetFont(LPFONT pNewFont);
```

### <a name="parameters"></a>参数

*p 纽丰特*<br/>
指向新`IFont`接口的指针。

## <a name="see-also"></a>请参阅

[层次结构图表](../../mfc/hierarchy-chart.md)<br/>
[CPropExchange 类](../../mfc/reference/cpropexchange-class.md)
