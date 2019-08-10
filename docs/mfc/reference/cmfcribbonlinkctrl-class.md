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
ms.openlocfilehash: 12a83e45176f7fc6020da1f0d0ee5923ef0f466c
ms.sourcegitcommit: bd7ddc044f9083246614b602ef6a758775313214
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/09/2019
ms.locfileid: "68866168"
---
# <a name="cmfcribbonlinkctrl-class"></a>CMFCRibbonLinkCtrl 类

实现位于功能区上的超链接。 当单击此超链接时，可以打开网页。
有关更多详细信息, 请参阅位于 Visual Studio 安装的**VC\\atlmfc\\src\\mfc**文件夹中的源代码。

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
|[CMFCRibbonLinkCtrl::GetCompactSize](#getcompactsize)|(重写[CMFCRibbonButton:: GetCompactSize](../../mfc/reference/cmfcribbonbutton-class.md#getcompactsize)。)|
|[CMFCRibbonLinkCtrl::GetLink](#getlink)|返回超链接的值。|
|[CMFCRibbonLinkCtrl::GetRegularSize](#getregularsize)|(重写[CMFCRibbonButton:: GetRegularSize](../../mfc/reference/cmfcribbonbutton-class.md#getregularsize)。)|
|[CMFCRibbonLinkCtrl::GetToolTipText](#gettooltiptext)|(重写[CMFCRibbonButton:: GetToolTipText](../../mfc/reference/cmfcribbonbutton-class.md#gettooltiptext)。)|
|[CMFCRibbonLinkCtrl::IsDrawTooltipImage](#isdrawtooltipimage)|（重写 `CMFCRibbonButton::IsDrawTooltipImage`。）|
|[CMFCRibbonLinkCtrl::OnDraw](#ondraw)|(重写[CMFCRibbonButton:: OnDraw](../../mfc/reference/cmfcribbonbutton-class.md#ondraw)。)|
|[CMFCRibbonLinkCtrl::OnDrawMenuImage](#ondrawmenuimage)|(重写[CMFCRibbonBaseElement:: OnDrawMenuImage](../../mfc/reference/cmfcribbonbaseelement-class.md#ondrawmenuimage)。)|
|[CMFCRibbonLinkCtrl::OnMouseMove](#onmousemove)|（重写 `CMFCRibbonButton::OnMouseMove`。）|
|[CMFCRibbonLinkCtrl::OnSetIcon](#onseticon)||
|[CMFCRibbonLinkCtrl::OpenLink](#openlink)|将打开超链接中指定的 Web 页。|
|[CMFCRibbonLinkCtrl::SetLink](#setlink)|设置超链接的值。|

## <a name="remarks"></a>备注

创建超链接后, 可通过调用[CMFCRibbonPanel:: add](../../mfc/reference/cmfcribbonpanel-class.md#add)将其添加到面板。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)\
└&nbsp;[CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)\
&nbsp;&nbsp;&nbsp;&nbsp;└&nbsp;[CMFCRibbonButton](../../mfc/reference/cmfcribbonbutton-class.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;└&nbsp;[CMFCRibbonLinkCtrl](../../mfc/reference/cmfcribbonlinkctrl-class.md)

## <a name="requirements"></a>要求

**标头:** afxRibbonLinkCtrl

##  <a name="cmfcribbonlinkctrl"></a>CMFCRibbonLinkCtrl::CMFCRibbonLinkCtrl

构造并初始化[CMFCRibbonLinkCtrl](../../mfc/reference/cmfcribbonlinkctrl-class.md)对象。

```
CMFCRibbonLinkCtrl(
    UINT nID,
    LPCTSTR lpszText,
    LPCTSTR lpszLink);
```

### <a name="parameters"></a>参数

*nID*<br/>
中指定单击链接控件时执行的命令的命令 ID。

*lpszText*<br/>
中指定要在链接控件上显示的标签。

*lpszLink*<br/>
中指定与链接控件关联的超链接。

### <a name="example"></a>示例

下面的示例演示如何使用`CMFCRibbonLinkCtrl`类的构造函数。 此代码片段是[功能区小工具示例](../../overview/visual-cpp-samples.md)的一部分。

[!code-cpp[NVC_MFC_RibbonGadgets#1](../../mfc/reference/codesnippet/cpp/cmfcribbonlinkctrl-class_1.cpp)]

##  <a name="copyfrom"></a>CMFCRibbonLinkCtrl:: CopyFrom

```
virtual void CopyFrom(const CMFCRibbonBaseElement& src);
```

### <a name="parameters"></a>参数

[in] *src*<br/>

### <a name="remarks"></a>备注

##  <a name="getcompactsize"></a>CMFCRibbonLinkCtrl:: GetCompactSize

```
virtual CSize GetCompactSize(CDC* pDC);
```

### <a name="parameters"></a>参数

[in] *pDC*<br/>

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

##  <a name="getlink"></a>CMFCRibbonLinkCtrl::GetLink

返回超链接的值。

```
LPCTSTR GetLink() const;
```

### <a name="return-value"></a>返回值

超链接的当前值。

### <a name="remarks"></a>备注

##  <a name="getregularsize"></a>CMFCRibbonLinkCtrl:: GetRegularSize

```
virtual CSize GetRegularSize(CDC* pDC);
```

### <a name="parameters"></a>参数

[in] *pDC*<br/>

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

##  <a name="gettooltiptext"></a>CMFCRibbonLinkCtrl:: GetToolTipText

```
virtual CString GetToolTipText() const;
```

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

##  <a name="ondrawmenuimage"></a>CMFCRibbonLinkCtrl:: OnDrawMenuImage

```
virtual BOOL OnDrawMenuImage(CDC*, CRect);
```

### <a name="parameters"></a>参数

中*CDC&#42;*<br/>
中*CRect*<br/>

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

##  <a name="onmousemove"></a>CMFCRibbonLinkCtrl:: OnMouseMove

```
virtual void OnMouseMove(CPoint point);
```

### <a name="parameters"></a>参数

中*点*<br/>

### <a name="remarks"></a>备注

##  <a name="onseticon"></a>  CMFCRibbonLinkCtrl::OnSetIcon

```
virtual void OnSetIcon();
```

### <a name="remarks"></a>备注

##  <a name="openlink"></a>CMFCRibbonLinkCtrl::OpenLink

将打开超链接中指定的 Web 页。

```
BOOL OpenLink();
```

### <a name="return-value"></a>返回值

如果成功打开关联的网页, 则为 TRUE;否则为 FALSE。

### <a name="remarks"></a>备注

使用与`CMFCRibbonLinkCtrl`对象关联的超链接打开网页。

##  <a name="setlink"></a>  CMFCRibbonLinkCtrl::SetLink

设置超链接的值。

```
void SetLink(LPCTSTR lpszLink);
```

### <a name="parameters"></a>参数

*lpszLink*<br/>
中指定超链接文本。

## <a name="see-also"></a>请参阅

[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[类](../../mfc/reference/mfc-classes.md)<br/>
[CMFCRibbonButton 类](../../mfc/reference/cmfcribbonbutton-class.md)
