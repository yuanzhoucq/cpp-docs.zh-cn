---
title: CPictureHolder 类
ms.date: 11/04/2016
f1_keywords:
- CPictureHolder
- AFXCTL/CPictureHolder
- AFXCTL/CPictureHolder::CPictureHolder
- AFXCTL/CPictureHolder::CreateEmpty
- AFXCTL/CPictureHolder::CreateFromBitmap
- AFXCTL/CPictureHolder::CreateFromIcon
- AFXCTL/CPictureHolder::CreateFromMetafile
- AFXCTL/CPictureHolder::GetDisplayString
- AFXCTL/CPictureHolder::GetPictureDispatch
- AFXCTL/CPictureHolder::GetType
- AFXCTL/CPictureHolder::Render
- AFXCTL/CPictureHolder::SetPictureDispatch
- AFXCTL/CPictureHolder::m_pPict
helpviewer_keywords:
- CPictureHolder [MFC], CPictureHolder
- CPictureHolder [MFC], CreateEmpty
- CPictureHolder [MFC], CreateFromBitmap
- CPictureHolder [MFC], CreateFromIcon
- CPictureHolder [MFC], CreateFromMetafile
- CPictureHolder [MFC], GetDisplayString
- CPictureHolder [MFC], GetPictureDispatch
- CPictureHolder [MFC], GetType
- CPictureHolder [MFC], Render
- CPictureHolder [MFC], SetPictureDispatch
- CPictureHolder [MFC], m_pPict
ms.assetid: a4f59775-704a-41dd-b5bd-2e531c95127a
ms.openlocfilehash: 067ea7238c48f2698d7bfe469e9c4be10129c065
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364052"
---
# <a name="cpictureholder-class"></a>CPictureHolder 类

实现图片属性，允许用户在控件中显示图片。

## <a name="syntax"></a>语法

```
class CPictureHolder
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[CPicture持有人：：CPictureHolder](#cpictureholder)|构造 `CPictureHolder` 对象。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CPicture持有人：创建空](#createempty)|创建一个空的 `CPictureHolder` 对象。|
|[CPicture持有人：：从位图创建](#createfrombitmap)|从位`CPictureHolder`图创建对象。|
|[CPicture持有人：从图标创建](#createfromicon)|从图标`CPictureHolder`创建对象。|
|[CPicture持有人：：从Metafile创建](#createfrommetafile)|从元`CPictureHolder`文件创建对象。|
|[CPicture持有人：获取显示字符串](#getdisplaystring)|检索控件容器的属性浏览器中显示的字符串。|
|[CPicture持有人：获取图片调度](#getpicturedispatch)|返回`CPictureHolder`对象的`IDispatch`接口。|
|[CPicture持有人：获取类型](#gettype)|告诉`CPictureHolder`对象是位图、元文件还是图标。|
|[CPicture持有人：呈现](#render)|渲染图片。|
|[CPicture持有人：：设置图片调度](#setpicturedispatch)|设置`CPictureHolder`对象的`IDispatch`接口。|

### <a name="public-data-members"></a>公共数据成员

|名称|说明|
|----------|-----------------|
|[CPicture持有人：m_pPict](#m_ppict)|指向图片对象的指针。|

## <a name="remarks"></a>备注

`CPictureHolder`没有基类。

使用"库存图片"属性，开发人员可以指定用于显示的位图、图标或元文件。

有关创建自定义图片属性的信息，请参阅文章[MFC ActiveX 控件：在 ActiveX 控件中使用图片](../../mfc/mfc-activex-controls-using-pictures-in-an-activex-control.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

`CPictureHolder`

## <a name="requirements"></a>要求

**标题：** afxctl.h

## <a name="cpictureholdercpictureholder"></a><a name="cpictureholder"></a>CPicture持有人：：CPictureHolder

构造 `CPictureHolder` 对象。

```
CPictureHolder();
```

## <a name="cpictureholdercreateempty"></a><a name="createempty"></a>CPicture持有人：创建空

创建空`CPictureHolder`对象并将其连接到`IPicture`接口。

```
BOOL CreateEmpty();
```

### <a name="return-value"></a>返回值

如果成功创建对象，则非零;否则 0。

## <a name="cpictureholdercreatefrombitmap"></a><a name="createfrombitmap"></a>CPicture持有人：：从位图创建

使用位图在 中初始化图片对象`CPictureHolder`。

```
BOOL CreateFromBitmap(
    UINT idResource);

BOOL CreateFromBitmap(
    CBitmap* pBitmap,
    CPalette* pPal = NULL,
    BOOL bTransferOwnership = TRUE);

BOOL CreateFromBitmap(
    HBITMAP hbm,
    HPALETTE hpal = NULL,
    BOOL bTransferOwnership = FALSE);
```

### <a name="parameters"></a>参数

*idResource*<br/>
位图资源的资源 ID。

*pBitmap*<br/>
指向[CBitmap](../../mfc/reference/cbitmap-class.md)对象的指针。

*pPal*<br/>
指向[CPalette](../../mfc/reference/cpalette-class.md)对象的指针。

*b 转让所有权*<br/>
指示图片对象是否将取得位图和调色板对象的所有权。

*Hbm*<br/>
处理从中`CPictureHolder`创建对象的位图。

*赫帕尔*<br/>
处理用于呈现位图的调色板。

### <a name="return-value"></a>返回值

如果成功创建对象，则非零;否则 0。

### <a name="remarks"></a>备注

如果*bTransport 所有权*为 TRUE，则在此调用返回后，调用方不应以任何方式使用位图或调色板对象。 如果*bTransport 所有权*为 FALSE，则调用方负责确保位图和调色板对象在图片对象的生存期内保持有效。

## <a name="cpictureholdercreatefromicon"></a><a name="createfromicon"></a>CPicture持有人：从图标创建

使用图标在 中初始化图片对象`CPictureHolder`。

```
BOOL CreateFromIcon(
    UINT idResource);

BOOL CreateFromIcon(
    HICON hIcon,
    BOOL bTransferOwnership = FALSE);
```

### <a name="parameters"></a>参数

*idResource*<br/>
位图资源的资源 ID。

*hIcon*<br/>
处理从中`CPictureHolder`创建对象的图标。

*b 转让所有权*<br/>
指示图片对象是否将取得图标对象的所有权。

### <a name="return-value"></a>返回值

如果成功创建对象，则非零;否则 0。

### <a name="remarks"></a>备注

如果*bTransport 所有权*为 TRUE，则在此调用返回后，调用方不应以任何方式使用图标对象。 如果*bTransport 所有权*为 FALSE，则调用方负责确保图标对象在图片对象的生存期内保持有效。

## <a name="cpictureholdercreatefrommetafile"></a><a name="createfrommetafile"></a>CPicture持有人：：从Metafile创建

使用元文件初始化 中的图片对象`CPictureHolder`。

```
BOOL CreateFromMetafile(
    HMETAFILE hmf,
    int xExt,
    int yExt,
    BOOL bTransferOwnership = FALSE);
```

### <a name="parameters"></a>参数

*姆夫*<br/>
处理用于创建`CPictureHolder`对象的元文件。

*xExt*<br/>
图片的 X 范围。

*yExt*<br/>
图片的 Y 范围。

*b 转让所有权*<br/>
指示图片对象是否将取得元文件对象的所有权。

### <a name="return-value"></a>返回值

如果成功创建对象，则非零;否则 0。

### <a name="remarks"></a>备注

如果*bTransport 所有权*为 TRUE，则调用方不应在此调用返回后以任何方式使用元文件对象。 如果*bTransport 所有权*为 FALSE，则调用方负责确保元文件对象在图片对象的生存期内保持有效。

## <a name="cpictureholdergetdisplaystring"></a><a name="getdisplaystring"></a>CPicture持有人：获取显示字符串

检索容器的属性浏览器中显示的字符串。

```
BOOL GetDisplayString(CString& strValue);
```

### <a name="parameters"></a>参数

*strValue*<br/>
引用用于保存显示字符串的[CString。](../../atl-mfc-shared/reference/cstringt-class.md)

### <a name="return-value"></a>返回值

如果已成功检索字符串，则非零;否则 0。

## <a name="cpictureholdergetpicturedispatch"></a><a name="getpicturedispatch"></a>CPicture持有人：获取图片调度

此函数返回指向`CPictureHolder`对象接口的`IPictureDisp`指针。

```
LPPICTUREDISP GetPictureDispatch();
```

### <a name="return-value"></a>返回值

指向`CPictureHolder`对象接口的`IPictureDisp`指针。

### <a name="remarks"></a>备注

调用方在完成此`Release`指针后必须调用它。

## <a name="cpictureholdergettype"></a><a name="gettype"></a>CPicture持有人：获取类型

指示图片是位图、元文件还是图标。

```
short GetType();
```

### <a name="return-value"></a>返回值

指示图片类型的值。 可能的值及其含义如下：

|“值”|含义|
|-----------|-------------|
|PICTYPE_UNINITIALIZED|`CPictureHolder`对象是统一的。|
|PICTYPE_NONE|`CPictureHolder`对象为空。|
|PICTYPE_BITMAP|图片是位图。|
|PICTYPE_METAFILE|图片是一个元文件。|
|PICTYPE_ICON|图片是一个图标。|

## <a name="cpictureholderm_ppict"></a><a name="m_ppict"></a>CPicture持有人：m_pPict

指向`CPictureHolder`对象接口的`IPicture`指针。

```
LPPICTURE m_pPict;
```

## <a name="cpictureholderrender"></a><a name="render"></a>CPicture持有人：呈现

在*rcRender*引用的矩形中渲染图片。

```
void Render(
    CDC* pDC,
    const CRect& rcRender,
    const CRect& rcWBounds);
```

### <a name="parameters"></a>参数

*pDC*<br/>
指向要呈现图片的显示上下文。

*rcRender*<br/>
要在其中渲染图片的矩形。

*rcWBounds*<br/>
表示呈现图片的对象的边界矩形的矩形。 对于控件，此矩形是传递给[COleControl：：：onDraw](../../mfc/reference/colecontrol-class.md#ondraw)的重写的*rcBounds*参数。

## <a name="cpictureholdersetpicturedispatch"></a><a name="setpicturedispatch"></a>CPicture持有人：：设置图片调度

将`CPictureHolder`对象连接到`IPictureDisp`接口。

```
void SetPictureDispatch(LPPICTUREDISP pDisp);
```

### <a name="parameters"></a>参数

*pDisp*<br/>
指向新`IPictureDisp`接口的指针。

## <a name="see-also"></a>另请参阅

[层次结构图表](../../mfc/hierarchy-chart.md)<br/>
[CFontHolder 类](../../mfc/reference/cfontholder-class.md)
