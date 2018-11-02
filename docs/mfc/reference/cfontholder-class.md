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
ms.openlocfilehash: 24a33aafa279f47bcfabd1ac3f3ee8d4abd4c731
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50659636"
---
# <a name="cfontholder-class"></a>CFontHolder 类

实现常用字体属性并封装 Windows 字体对象和 `IFont` 接口的功能。

## <a name="syntax"></a>语法

```
class CFontHolder
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[CFontHolder::CFontHolder](#cfontholder)|构造 `CFontHolder` 对象。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CFontHolder::GetDisplayString](#getdisplaystring)|检索容器的属性浏览器中显示的字符串。|
|[CFontHolder::GetFontDispatch](#getfontdispatch)|返回字体的`IDispatch`接口。|
|[CFontHolder::GetFontHandle](#getfonthandle)|返回的句柄 Windows 字体。|
|[CFontHolder::InitializeFont](#initializefont)|初始化`CFontHolder`对象。|
|[CFontHolder::QueryTextMetrics](#querytextmetrics)|检索相关字体信息。|
|[CFontHolder::ReleaseFont](#releasefont)|断开`CFontHolder`对象从`IFont`和`IFontNotification`接口。|
|[CFontHolder::Select](#select)|选择到设备上下文的字体资源。|
|[CFontHolder::SetFont](#setfont)|连接`CFontHolder`对象传递给`IFont`接口。|

### <a name="public-data-members"></a>公共数据成员

|名称|描述|
|----------|-----------------|
|[CFontHolder::m_pFont](#m_pfont)|一个指向`CFontHolder`对象的`IFont`接口。|

## <a name="remarks"></a>备注

`CFontHolder` 没有基类。

此类用于实现您的控件的自定义字体属性。 有关创建此类属性的信息，请参阅文章[ActiveX 控件： 使用字体](../../mfc/mfc-activex-controls-using-fonts.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

`CFontHolder`

## <a name="requirements"></a>要求

**标头：** afxctl.h

##  <a name="cfontholder"></a>  CFontHolder::CFontHolder

构造 `CFontHolder` 对象。

```
explicit CFontHolder(LPPROPERTYNOTIFYSINK pNotify);
```

### <a name="parameters"></a>参数

*pNotify*<br/>
指向字体的`IPropertyNotifySink`接口。

### <a name="remarks"></a>备注

必须调用`InitializeFont`初始化生成的对象，然后再使用它。

##  <a name="getdisplaystring"></a>  CFontHolder::GetDisplayString

检索可以在容器的属性浏览器中显示的字符串。

```
BOOL GetDisplayString(CString& strValue);
```

### <a name="parameters"></a>参数

*strValue*<br/>
引用[CString](../../atl-mfc-shared/reference/cstringt-class.md)要保存的显示字符串。

### <a name="return-value"></a>返回值

已成功检索的字符串; 如果非零值否则为 0。

##  <a name="getfontdispatch"></a>  CFontHolder::GetFontDispatch

调用此函数可检索指向字体的调度接口的指针。

```
LPFONTDISP GetFontDispatch();
```

### <a name="return-value"></a>返回值

一个指向`CFontHolder`对象的`IFontDisp`接口。 请注意，该函数的调用`GetFontDispatch`必须调用`IUnknown::Release`上完成它时此接口指针。

### <a name="remarks"></a>备注

调用`InitializeFont`之前调用`GetFontDispatch`。

##  <a name="getfonthandle"></a>  CFontHolder::GetFontHandle

调用此函数可获取为 Windows 字体的句柄。

```
HFONT GetFontHandle();

HFONT GetFontHandle(
    long cyLogical,
    long cyHimetric);
```

### <a name="parameters"></a>参数

*cyLogical*<br/>
使用逻辑单位，在其中绘制控件的矩形的高度。

*cyHimetric*<br/>
MM_HIMETRIC 单位，该控件的高度。

### <a name="return-value"></a>返回值

字体对象中; 的句柄否则为，为 NULL。

### <a name="remarks"></a>备注

比率*cyLogical*并*cyHimetric*用于计算的正确显示大小，以逻辑单位，以 MM_HIMETRIC 单位表示的字体的磅值：

显示大小 = ( *cyLogical* / *cyHimetric*) X 字体大小

不带任何参数的版本返回的句柄正确设置屏幕大小的字体。

##  <a name="initializefont"></a>  CFontHolder::InitializeFont

初始化`CFontHolder`对象。

```
void InitializeFont(
    const FONTDESC* pFontDesc = NULL,
    LPDISPATCH pFontDispAmbient = NULL);
```

### <a name="parameters"></a>参数

*pFontDesc*<br/>
字体描述结构的指针 ( [FONTDESC](/windows/desktop/api/olectl/ns-olectl-tagfontdesc))，它指定字体的特征。

*pFontDispAmbient*<br/>
指向容器的环境字体属性。

### <a name="remarks"></a>备注

如果*pFontDispAmbient*不为 NULL，`CFontHolder`对象连接到的克隆`IFont`接口使用的容器的环境字体属性。

如果*pFontDispAmbient*为 NULL，则新字体对象已从指向字体描述*pFontDesc*或者，如果*pFontDesc*从默认值为 NULL，说明。

在构造之后调用此函数`CFontHolder`对象。

##  <a name="m_pfont"></a>  CFontHolder::m_pFont

一个指向`CFontHolder`对象的`IFont`接口。

```
LPFONT m_pFont;
```

##  <a name="querytextmetrics"></a>  CFontHolder::QueryTextMetrics

检索信息所表示的物理字体`CFontHolder`对象。

```
void QueryTextMetrics(LPTEXTMETRIC lptm);
```

### <a name="parameters"></a>参数

*lptm*<br/>
一个指向[TEXTMETRIC](/windows/desktop/api/wingdi/ns-wingdi-tagtextmetrica)结构，它将接收的信息。

##  <a name="releasefont"></a>  CFontHolder::ReleaseFont

此函数将断开连接`CFontHolder`对象从其`IFont`接口。

```
void ReleaseFont();
```

##  <a name="select"></a>  CFontHolder::Select

调用此函数可指定的设备上下文中选择控件的字体。

```
CFont* Select(
    CDC* pDC,
    long cyLogical,
    long cyHimetric);
```

### <a name="parameters"></a>参数

*pDC*<br/>
在其中选择字体的设备上下文。

*cyLogical*<br/>
使用逻辑单位，在其中绘制控件的矩形的高度。

*cyHimetric*<br/>
MM_HIMETRIC 单位，该控件的高度。

### <a name="return-value"></a>返回值

指向要替换的字体的指针。

### <a name="remarks"></a>备注

请参阅[GetFontHandle](#getfonthandle)有关的讨论*cyLogical*并*cyHimetric*参数。

##  <a name="setfont"></a>  CFontHolder::SetFont

释放任何现有字体并连接`CFontHolder`对象传递给`IFont`接口。

```
void SetFont(LPFONT pNewFont);
```

### <a name="parameters"></a>参数

*pNewFont*<br/>
指向新`IFont`接口。

## <a name="see-also"></a>请参阅

[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[CPropExchange 类](../../mfc/reference/cpropexchange-class.md)
