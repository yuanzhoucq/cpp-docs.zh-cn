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
ms.openlocfilehash: 79edff8be6e2c37baa938fc5b624253932609e17
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/22/2020
ms.locfileid: "81754244"
---
# <a name="cmfclinkctrl-class"></a>CMFCLinkCtrl 类

类`CMFCLinkCtrl`将显示一个按钮作为超链接，并在单击按钮时调用链接的目标。

## <a name="syntax"></a>语法

```
class CMFCLinkCtrl : public CMFCButton
```

## <a name="members"></a>成员

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CMFCLinkCtrl：：SetURL](#seturl)|将指定的 URL 显示为按钮文本。|
|[CMFCLinkCtrl：：设置URL前缀](#seturlprefix)|设置 URL 的隐式协议（例如"http："）。|
|[CMFClinkctrl：：大小到内容](#sizetocontent)|调整按钮的大小以包含按钮文本或位图。|

### <a name="protected-methods"></a>受保护的方法

|名称|说明|
|----------|-----------------|
|[CMFClinkCtrl：在Draw焦点上](#ondrawfocusrect)|在绘制按钮的焦点矩形之前由框架调用。|

## <a name="remarks"></a>备注

单击派生自类的`CMFCLinkCtrl`按钮时，框架将按钮的 URL 作为参数传递给`ShellExecute`方法。 然后，`ShellExecute`该方法将打开 URL 的目标。

## <a name="example"></a>示例

下面的示例演示如何设置`CMFCLinkCtrl`对象的大小，以及如何在`CMFCLinkCtrl`对象中设置 URL 和工具提示。 此示例是["新控件"示例](../../overview/visual-cpp-samples.md)的一部分。

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

**标题：** afxlinkctrl.h

## <a name="cmfclinkctrlondrawfocusrect"></a><a name="ondrawfocusrect"></a>CMFClinkCtrl：在Draw焦点上

在绘制按钮的焦点矩形之前由框架调用。

```
virtual void OnDrawFocusRect(
    CDC* pDC,
    const CRect& rectClient);
```

### <a name="parameters"></a>参数

*pDC*<br/>
[在]指向设备上下文的指针。

*rectClient*<br/>
[在]绑定链接控件的矩形。

### <a name="remarks"></a>备注

如果要使用自己的代码绘制按钮的焦点矩形，请重写此方法。

## <a name="cmfclinkctrlseturl"></a><a name="seturl"></a>CMFCLinkCtrl：：SetURL

将指定的 URL 显示为按钮文本。

```cpp
void SetURL(LPCTSTR lpszURL);
```

### <a name="parameters"></a>参数

*lpszURL*<br/>
[在]要显示的按钮文本。

### <a name="remarks"></a>备注

## <a name="cmfclinkctrlseturlprefix"></a><a name="seturlprefix"></a>CMFCLinkCtrl：：设置URL前缀

设置 URL 的隐式协议（例如"http："）。

```cpp
void SetURLPrefix(LPCTSTR lpszPrefix);
```

### <a name="parameters"></a>参数

*lpszPrefix*<br/>
[在]URL 协议的前缀。

### <a name="remarks"></a>备注

使用此方法设置 URL 前缀。 前缀不显示在按钮的表面上，但您可以使用它帮助浏览到 URL 的目标。

## <a name="cmfclinkctrlsizetocontent"></a><a name="sizetocontent"></a>CMFClinkctrl：：大小到内容

调整按钮的大小以包含按钮文本或位图。

```
virtual CSize SizeToContent(
    BOOL bVCenter=FALSE,
    BOOL bHCenter=FALSE);
```

### <a name="parameters"></a>参数

*bV中心*<br/>
[在]TRUE 将按钮文本和位图垂直居中，在链接控件的顶部和底部之间;否则，FALSE。 默认值是 FALSE。

*bH中心*<br/>
[在]TRUE 将按钮文本和位图水平居中，水平位于链接控件的左右两侧;否则，FALSE。 默认值是 FALSE。

### <a name="return-value"></a>返回值

包含链接控件的新大小的[CSize](../../atl-mfc-shared/reference/csize-class.md)对象。

### <a name="remarks"></a>备注

## <a name="see-also"></a>请参阅

[层次结构图表](../../mfc/hierarchy-chart.md)<br/>
[类](../../mfc/reference/mfc-classes.md)<br/>
[链接课程](../../mfc/reference/clinkctrl-class.md)<br/>
[CMFCButton 类](../../mfc/reference/cmfcbutton-class.md)
