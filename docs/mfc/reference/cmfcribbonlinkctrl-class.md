---
title: CMFCRibbonLinkCtrl 类
ms.date: 11/04/2016
f1_keywords:
- CMFCRibbonLinkCtrl
- AFXRIBBONLINKCTRL/CMFCRibbonLinkCtrl
- AFXRIBBONLINKCTRL/CMFCRibbonLinkCtrl::CMFCRibbonLinkCtrl
- AFXRIBBONLINKCTRL/CMFCRibbonLinkCtrl::CopyFrom
- AFXRIBBONLINKCTRL/CMFCRibbonLinkCtrl::GetCompactSize
- AFXRIBBONLINKCTRL/CMFCRibbonLinkCtrl::GetLink
- AFXRIBBONLINKCTRL/CMFCRibbonLinkCtrl::GetRegularSize
- AFXRIBBONLINKCTRL/CMFCRibbonLinkCtrl::GetToolTipText
- AFXRIBBONLINKCTRL/CMFCRibbonLinkCtrl::IsDrawTooltipImage
- AFXRIBBONLINKCTRL/CMFCRibbonLinkCtrl::OnDraw
- AFXRIBBONLINKCTRL/CMFCRibbonLinkCtrl::OnDrawMenuImage
- AFXRIBBONLINKCTRL/CMFCRibbonLinkCtrl::OnMouseMove
- AFXRIBBONLINKCTRL/CMFCRibbonLinkCtrl::OnSetIcon
- AFXRIBBONLINKCTRL/CMFCRibbonLinkCtrl::OpenLink
- AFXRIBBONLINKCTRL/CMFCRibbonLinkCtrl::SetLink
helpviewer_keywords:
- CMFCRibbonLinkCtrl [MFC], CMFCRibbonLinkCtrl
- CMFCRibbonLinkCtrl [MFC], CopyFrom
- CMFCRibbonLinkCtrl [MFC], GetCompactSize
- CMFCRibbonLinkCtrl [MFC], GetLink
- CMFCRibbonLinkCtrl [MFC], GetRegularSize
- CMFCRibbonLinkCtrl [MFC], GetToolTipText
- CMFCRibbonLinkCtrl [MFC], IsDrawTooltipImage
- CMFCRibbonLinkCtrl [MFC], OnDraw
- CMFCRibbonLinkCtrl [MFC], OnDrawMenuImage
- CMFCRibbonLinkCtrl [MFC], OnMouseMove
- CMFCRibbonLinkCtrl [MFC], OnSetIcon
- CMFCRibbonLinkCtrl [MFC], OpenLink
- CMFCRibbonLinkCtrl [MFC], SetLink
ms.assetid: 77ae1941-e0ab-4a9d-911e-1752d34c079b
ms.openlocfilehash: 9f47e5a3a25120370bd618ac3a89de76761fa61a
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/04/2019
ms.locfileid: "57287786"
---
# <a name="cmfcribbonlinkctrl-class"></a>CMFCRibbonLinkCtrl 类

实现位于功能区上的超链接。 当单击此超链接时，可以打开网页。
有关更多详细信息，请参阅中的源代码**VC\\atlmfc\\src\\mfc**的 Visual Studio 安装文件夹。

## <a name="syntax"></a>语法

```
class CMFCRibbonLinkCtrl : public CMFCRibbonButton
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[CMFCRibbonLinkCtrl::CMFCRibbonLinkCtrl](#cmfcribbonlinkctrl)|构造并初始化一个 `CMFCRibbonLinkCtrl` 对象。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CMFCRibbonLinkCtrl::CopyFrom](#copyfrom)|（重写 `CMFCRibbonButton::CopyFrom`。）|
|[CMFCRibbonLinkCtrl::GetCompactSize](#getcompactsize)|(重写[cmfcribbonbutton:: Getcompactsize](../../mfc/reference/cmfcribbonbutton-class.md#getcompactsize)。)|
|[CMFCRibbonLinkCtrl::GetLink](#getlink)|返回超链接的值。|
|[CMFCRibbonLinkCtrl::GetRegularSize](#getregularsize)|(重写[cmfcribbonbutton:: Getregularsize](../../mfc/reference/cmfcribbonbutton-class.md#getregularsize)。)|
|[CMFCRibbonLinkCtrl::GetToolTipText](#gettooltiptext)|(重写[cmfcribbonbutton:: Gettooltiptext](../../mfc/reference/cmfcribbonbutton-class.md#gettooltiptext)。)|
|[CMFCRibbonLinkCtrl::IsDrawTooltipImage](#isdrawtooltipimage)|（重写 `CMFCRibbonButton::IsDrawTooltipImage`。）|
|[CMFCRibbonLinkCtrl::OnDraw](#ondraw)|(重写[cmfcribbonbutton:: Ondraw](../../mfc/reference/cmfcribbonbutton-class.md#ondraw)。)|
|[CMFCRibbonLinkCtrl::OnDrawMenuImage](#ondrawmenuimage)|(重写[cmfcribbonbaseelement:: Ondrawmenuimage](../../mfc/reference/cmfcribbonbaseelement-class.md#ondrawmenuimage)。)|
|[CMFCRibbonLinkCtrl::OnMouseMove](#onmousemove)|（重写 `CMFCRibbonButton::OnMouseMove`。）|
|[CMFCRibbonLinkCtrl::OnSetIcon](#onseticon)||
|[CMFCRibbonLinkCtrl::OpenLink](#openlink)|将打开超链接中指定的 Web 页。|
|[CMFCRibbonLinkCtrl::SetLink](#setlink)|设置超链接的值。|

## <a name="remarks"></a>备注

创建超链接后，将其添加到一个面板，通过调用[cmfcribbonpanel:: Add](../../mfc/reference/cmfcribbonpanel-class.md#add)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md) [CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)

[CMFCRibbonButton](../../mfc/reference/cmfcribbonbutton-class.md) [CMFCRibbonLinkCtrl](../../mfc/reference/cmfcribbonlinkctrl-class.md)

## <a name="requirements"></a>要求

**标头：** afxRibbonLinkCtrl.h

##  <a name="cmfcribbonlinkctrl"></a>  CMFCRibbonLinkCtrl::CMFCRibbonLinkCtrl

构造并初始化[CMFCRibbonLinkCtrl](../../mfc/reference/cmfcribbonlinkctrl-class.md)对象。

```
CMFCRibbonLinkCtrl(
    UINT nID,
    LPCTSTR lpszText,
    LPCTSTR lpszLink);
```

### <a name="parameters"></a>参数

*nID*<br/>
[in]指定在单击链接控件时执行该命令的命令 ID。

*lpszText*<br/>
[in]指定要在链接控件上显示的标签。

*lpszLink*<br/>
[in]指定与链接控件关联的超链接。

### <a name="example"></a>示例

下面的示例演示如何使用的构造函数`CMFCRibbonLinkCtrl`类。 此代码片段属于[功能区的小工具示例](../../visual-cpp-samples.md)。

[!code-cpp[NVC_MFC_RibbonGadgets#1](../../mfc/reference/codesnippet/cpp/cmfcribbonlinkctrl-class_1.cpp)]

##  <a name="copyfrom"></a>  CMFCRibbonLinkCtrl::CopyFrom

```
virtual void CopyFrom(const CMFCRibbonBaseElement& src);
```

### <a name="parameters"></a>参数

[in] *src*<br/>

### <a name="remarks"></a>备注

##  <a name="getcompactsize"></a>  CMFCRibbonLinkCtrl::GetCompactSize

```
virtual CSize GetCompactSize(CDC* pDC);
```

### <a name="parameters"></a>参数

[in] *pDC*<br/>

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

##  <a name="getlink"></a>  CMFCRibbonLinkCtrl::GetLink

返回超链接的值。

```
LPCTSTR GetLink() const;
```

### <a name="return-value"></a>返回值

超链接的当前值。

### <a name="remarks"></a>备注

##  <a name="getregularsize"></a>  CMFCRibbonLinkCtrl::GetRegularSize

```
virtual CSize GetRegularSize(CDC* pDC);
```

### <a name="parameters"></a>参数

[in] *pDC*<br/>

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

##  <a name="gettooltiptext"></a>  CMFCRibbonLinkCtrl::GetToolTipText

```
virtual CString GetToolTipText() const;
```

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

##  <a name="ondrawmenuimage"></a>  CMFCRibbonLinkCtrl::OnDrawMenuImage

```
virtual BOOL OnDrawMenuImage(CDC*, CRect);
```

### <a name="parameters"></a>参数

[in] *CDC&#42;*<br/>
[in] *CRect*<br/>

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

##  <a name="isdrawtooltipimage"></a>  CMFCRibbonLinkCtrl::IsDrawTooltipImage

```
virtual BOOL IsDrawTooltipImage() const;
```

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

##  <a name="ondraw"></a>  CMFCRibbonLinkCtrl::OnDraw

```
virtual void OnDraw(CDC* pDC);
```

### <a name="parameters"></a>参数

[in] *pDC*<br/>

### <a name="remarks"></a>备注

##  <a name="onmousemove"></a>  CMFCRibbonLinkCtrl::OnMouseMove

```
virtual void OnMouseMove(CPoint point);
```

### <a name="parameters"></a>参数

[in] *point*<br/>

### <a name="remarks"></a>备注

##  <a name="onseticon"></a>  CMFCRibbonLinkCtrl::OnSetIcon

```
virtual void OnSetIcon();
```

### <a name="remarks"></a>备注

##  <a name="openlink"></a>  CMFCRibbonLinkCtrl::OpenLink

将打开超链接中指定的 Web 页。

```
BOOL OpenLink();
```

### <a name="return-value"></a>返回值

如果成功，则打开关联的网页，则返回 TRUE否则为 FALSE。

### <a name="remarks"></a>备注

将使用相应的超链接的网页打开`CMFCRibbonLinkCtrl`对象。

##  <a name="setlink"></a>  CMFCRibbonLinkCtrl::SetLink

设置超链接的值。

```
void SetLink(LPCTSTR lpszLink);
```

### <a name="parameters"></a>参数

*lpszLink*<br/>
[in]指定的超链接文本。

## <a name="see-also"></a>请参阅

[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[类](../../mfc/reference/mfc-classes.md)<br/>
[CMFCRibbonButton 类](../../mfc/reference/cmfcribbonbutton-class.md)
