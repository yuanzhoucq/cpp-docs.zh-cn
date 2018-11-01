---
title: CMFCLinkCtrl 类
ms.date: 11/04/2016
f1_keywords:
- CMFCLinkCtrl
- AFXLINKCTRL/CMFCLinkCtrl
- AFXLINKCTRL/CMFCLinkCtrl::SetURL
- AFXLINKCTRL/CMFCLinkCtrl::SetURLPrefix
- AFXLINKCTRL/CMFCLinkCtrl::SizeToContent
- AFXLINKCTRL/CMFCLinkCtrl::OnDrawFocusRect
helpviewer_keywords:
- CMFCLinkCtrl [MFC], SetURL
- CMFCLinkCtrl [MFC], SetURLPrefix
- CMFCLinkCtrl [MFC], SizeToContent
- CMFCLinkCtrl [MFC], OnDrawFocusRect
ms.assetid: 80f3874d-7cc8-410e-9ff1-62a225f5034b
ms.openlocfilehash: bc43dcaf077bc97e3ff589a12bee6a8eac6aeed1
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50608580"
---
# <a name="cmfclinkctrl-class"></a>CMFCLinkCtrl 类

`CMFCLinkCtrl`类按钮显示为超链接，并单击该按钮时调用链接的目标。

## <a name="syntax"></a>语法

```
class CMFCLinkCtrl : public CMFCButton
```

## <a name="members"></a>成员

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CMFCLinkCtrl::SetURL](#seturl)|将指定的 URL 显示为按钮文本。|
|[CMFCLinkCtrl::SetURLPrefix](#seturlprefix)|设置隐式协议 (例如，"http:") 的 url。|
|[CMFCLinkCtrl::SizeToContent](#sizetocontent)|调整大小的按钮，以包含按钮文本或位图。|

### <a name="protected-methods"></a>受保护的方法

|名称|描述|
|----------|-----------------|
|[CMFCLinkCtrl::OnDrawFocusRect](#ondrawfocusrect)|在绘制聚焦框的按钮之前由框架调用。|

## <a name="remarks"></a>备注

当您单击一个按钮来派生自`CMFCLinkCtrl`类，则框架会将按钮的 URL 传递的参数作为`ShellExecute`方法。 然后`ShellExecute`方法打开的 url 目标。

## <a name="example"></a>示例

下面的示例演示如何设置的大小`CMFCLinkCtrl`对象，以及如何设置 url 和中的工具提示`CMFCLinkCtrl`对象。 此示例摘自[新的控件示例](../../visual-cpp-samples.md)。

[!code-cpp[NVC_MFC_NewControls#9](../../mfc/reference/codesnippet/cpp/cmfclinkctrl-class_1.h)]
[!code-cpp[NVC_MFC_NewControls#10](../../mfc/reference/codesnippet/cpp/cmfclinkctrl-class_2.cpp)]

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CButton](../../mfc/reference/cbutton-class.md)

[CMFCButton](../../mfc/reference/cmfcbutton-class.md)

[CMFCLinkCtrl](../../mfc/reference/cmfclinkctrl-class.md)

## <a name="requirements"></a>要求

**标头：** afxlinkctrl.h

##  <a name="ondrawfocusrect"></a>  CMFCLinkCtrl::OnDrawFocusRect

在绘制聚焦框的按钮之前由框架调用。

```
virtual void OnDrawFocusRect(
    CDC* pDC,
    const CRect& rectClient);
```

### <a name="parameters"></a>参数

*pDC*<br/>
[in]指向设备上下文的指针。

*rectClient*<br/>
[in]限定为链接控件的矩形。

### <a name="remarks"></a>备注

当你想要使用你自己的代码来绘制按钮的聚焦框时，重写此方法。

##  <a name="seturl"></a>  CMFCLinkCtrl::SetURL

将指定的 URL 显示为按钮文本。

```
void SetURL(LPCTSTR lpszURL);
```

### <a name="parameters"></a>参数

*lpszURL*<br/>
[in]要显示的按钮文本。

### <a name="remarks"></a>备注

##  <a name="seturlprefix"></a>  CMFCLinkCtrl::SetURLPrefix

设置隐式协议 (例如，"http:") 的 url。

```
void SetURLPrefix(LPCTSTR lpszPrefix);
```

### <a name="parameters"></a>参数

*lpszPrefix*<br/>
[in]URL 协议的前缀。

### <a name="remarks"></a>备注

使用此方法设置的 URL 前缀。 前缀不会显示在按钮的人脸，但可以使用它来帮助浏览到的 URL 目标。

##  <a name="sizetocontent"></a>  CMFCLinkCtrl::SizeToContent

调整大小的按钮，以包含按钮文本或位图。

```
virtual CSize SizeToContent(
    BOOL bVCenter=FALSE,
    BOOL bHCenter=FALSE);
```

### <a name="parameters"></a>参数

*bVCenter*<br/>
[in]为 TRUE，则按钮文本和位图的顶部和底部的链接控件; 之间的垂直居中否则为 FALSE。 默认值是 FALSE。

*bHCenter*<br/>
[in]为 TRUE，则按钮文本和位图的左侧和右侧的链接控件; 之间的水平居中否则为 FALSE。 默认值是 FALSE。

### <a name="return-value"></a>返回值

一个[CSize](../../atl-mfc-shared/reference/csize-class.md)对象，其中包含链接控件的新大小。

### <a name="remarks"></a>备注

## <a name="see-also"></a>请参阅

[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[类](../../mfc/reference/mfc-classes.md)<br/>
[CLinkCtrl 类](../../mfc/reference/clinkctrl-class.md)<br/>
[CMFCButton 类](../../mfc/reference/cmfcbutton-class.md)
