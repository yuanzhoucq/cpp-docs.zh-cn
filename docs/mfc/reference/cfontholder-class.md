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
ms.openlocfilehash: 04de8141469f82bdd1fbb6adc1bae94d6026324c
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69506448"
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
|[CFontHolder::GetFontHandle](#getfonthandle)|返回 Windows 字体的句柄。|
|[CFontHolder::InitializeFont](#initializefont)|`CFontHolder`初始化对象。|
|[CFontHolder::QueryTextMetrics](#querytextmetrics)|检索相关字体的信息。|
|[CFontHolder::ReleaseFont](#releasefont)|`CFontHolder`断开对象`IFont`与和`IFontNotification`接口的连接。|
|[CFontHolder::Select](#select)|在设备上下文中选择字体资源。|
|[CFontHolder::SetFont](#setfont)|将对象连接到`IFont`接口。 `CFontHolder`|

### <a name="public-data-members"></a>公共数据成员

|名称|描述|
|----------|-----------------|
|[CFontHolder::m_pFont](#m_pfont)|`CFontHolder` 指向`IFont`对象接口的指针。|

## <a name="remarks"></a>备注

`CFontHolder`没有基类。

使用此类实现控件的自定义字体属性。 有关创建此类属性的信息, 请参阅[文章 ActiveX 控件:使用字体](../../mfc/mfc-activex-controls-using-fonts.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

`CFontHolder`

## <a name="requirements"></a>要求

**标头:** afxctl。h

##  <a name="cfontholder"></a>CFontHolder::CFontHolder

构造 `CFontHolder` 对象。

```
explicit CFontHolder(LPPROPERTYNOTIFYSINK pNotify);
```

### <a name="parameters"></a>参数

*pNotify*<br/>
指向字体`IPropertyNotifySink`接口的指针。

### <a name="remarks"></a>备注

使用之前, `InitializeFont`必须先调用来初始化生成的对象。

##  <a name="getdisplaystring"></a>CFontHolder::GetDisplayString

检索可在容器的属性浏览器中显示的字符串。

```
BOOL GetDisplayString(CString& strValue);
```

### <a name="parameters"></a>参数

*strValue*<br/>
对用于保存显示字符串的[CString](../../atl-mfc-shared/reference/cstringt-class.md)的引用。

### <a name="return-value"></a>返回值

如果成功检索到该字符串, 则为非零值;否则为0。

##  <a name="getfontdispatch"></a>CFontHolder::GetFontDispatch

调用此函数可检索指向字体的调度接口的指针。

```
LPFONTDISP GetFontDispatch();
```

### <a name="return-value"></a>返回值

`CFontHolder` 指向`IFontDisp`对象接口的指针。 请注意, 调用`GetFontDispatch`的函数必须在完成后调用`IUnknown::Release`此接口指针。

### <a name="remarks"></a>备注

在`InitializeFont` 调用`GetFontDispatch`前调用。

##  <a name="getfonthandle"></a>CFontHolder::GetFontHandle

调用此函数可获取 Windows 字体的句柄。

```
HFONT GetFontHandle();

HFONT GetFontHandle(
    long cyLogical,
    long cyHimetric);
```

### <a name="parameters"></a>参数

*cyLogical*<br/>
绘制控件的矩形的高度 (以逻辑单位表示)。

*cyHimetric*<br/>
控件的高度 (以 MM_HIMETRIC 单位为单位)。

### <a name="return-value"></a>返回值

Font 对象的句柄;否则为 NULL。

### <a name="remarks"></a>备注

*CyLogical*和*cyHimetric*的比率用于计算以 MM_HIMETRIC 单位表示的字体磅值的正确显示大小 (以逻辑单位表示):

显示大小 = ( *cyLogical* / *cyHimetric*) X 字体大小

不带参数的版本将返回为屏幕正确调整字体大小的句柄。

##  <a name="initializefont"></a>CFontHolder::InitializeFont

`CFontHolder`初始化对象。

```
void InitializeFont(
    const FONTDESC* pFontDesc = NULL,
    LPDISPATCH pFontDispAmbient = NULL);
```

### <a name="parameters"></a>参数

*pFontDesc*<br/>
指向字体说明结构 ( [FONTDESC](/windows/win32/api/olectl/ns-olectl-fontdesc)) 的指针, 该结构指定字体的特征。

*pFontDispAmbient*<br/>
指向容器环境字体属性的指针。

### <a name="remarks"></a>备注

如果*pFontDispAmbient*不为 NULL, 则`CFontHolder`对象连接到容器的环境字体属性`IFont`所使用的接口的克隆。

如果*pFontDispAmbient*为 NULL, 则将通过从*pFontDesc*指向的字体说明创建一个新的字体对象, 如果*pFontDesc*为 null, 则从默认的说明创建一个。

构造`CFontHolder`对象之后调用此函数。

##  <a name="m_pfont"></a>CFontHolder::m_pFont

`CFontHolder` 指向`IFont`对象接口的指针。

```
LPFONT m_pFont;
```

##  <a name="querytextmetrics"></a>CFontHolder::QueryTextMetrics

检索有关由`CFontHolder`对象表示的物理字体的信息。

```
void QueryTextMetrics(LPTEXTMETRIC lptm);
```

### <a name="parameters"></a>参数

*lptm*<br/>
指向将接收信息的[TEXTMETRIC](/windows/win32/api/wingdi/ns-wingdi-textmetricw)结构的指针。

##  <a name="releasefont"></a>CFontHolder::ReleaseFont

此函数将`CFontHolder`对象从其`IFont`接口断开连接。

```
void ReleaseFont();
```

##  <a name="select"></a>CFontHolder:: Select

调用此函数可将控件的字体选择到指定的设备上下文中。

```
CFont* Select(
    CDC* pDC,
    long cyLogical,
    long cyHimetric);
```

### <a name="parameters"></a>参数

*pDC*<br/>
选定字体的设备上下文。

*cyLogical*<br/>
绘制控件的矩形的高度 (以逻辑单位表示)。

*cyHimetric*<br/>
控件的高度 (以 MM_HIMETRIC 单位为单位)。

### <a name="return-value"></a>返回值

指向要替换的字体的指针。

### <a name="remarks"></a>备注

有关*cyLogical*和*cyHimetric*参数的讨论, 请参阅[GetFontHandle](#getfonthandle) 。

##  <a name="setfont"></a>CFontHolder::SetFont

释放任何现有字体并将`CFontHolder`对象连接`IFont`到接口。

```
void SetFont(LPFONT pNewFont);
```

### <a name="parameters"></a>参数

*pNewFont*<br/>
指向新`IFont`接口的指针。

## <a name="see-also"></a>请参阅

[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[CPropExchange 类](../../mfc/reference/cpropexchange-class.md)
