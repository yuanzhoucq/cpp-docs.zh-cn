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
ms.openlocfilehash: 3c0cbe843aac172464683288d61e2aec2af60b68
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/22/2020
ms.locfileid: "81753554"
---
# <a name="cmfcribbonlinkctrl-class"></a>CMFCRibbonLinkCtrl 类

实现位于功能区上的超链接。 当单击此超链接时，可以打开网页。
有关详细信息，请参阅位于 Visual Studio 安装的**VC\\\\atlmfc src\\mfc**文件夹中的源代码。

## <a name="syntax"></a>语法

```
class CMFCRibbonLinkCtrl : public CMFCRibbonButton
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[CMFCRibbonLinkCtrl::CMFCRibbonLinkCtrl](#cmfcribbonlinkctrl)|构造并初始化一个 `CMFCRibbonLinkCtrl` 对象。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CMFCRibbonLinkCtrl::CopyFrom](#copyfrom)|（重写 `CMFCRibbonButton::CopyFrom`。）|
|[CMFC 功能链接Ctrl：获取压缩尺寸](#getcompactsize)|（覆盖[CMFC 功能按钮：获取压缩大小](../../mfc/reference/cmfcribbonbutton-class.md#getcompactsize).）|
|[CMFC剪链接Ctrl：获取链接](#getlink)|返回超链接的值。|
|[CMFC 功能链接Ctrl：获取常规大小](#getregularsize)|（覆盖[CMFC 功能按钮：获取常规大小](../../mfc/reference/cmfcribbonbutton-class.md#getregularsize).）|
|[CMFC 功能链接Ctrl：获取工具提示文本](#gettooltiptext)|（覆盖[CMFC 功能化按钮：获取工具提示文本](../../mfc/reference/cmfcribbonbutton-class.md#gettooltiptext).）|
|[CMFCRibbonLinkCtrl::IsDrawTooltipImage](#isdrawtooltipimage)|（重写 `CMFCRibbonButton::IsDrawTooltipImage`。）|
|[CMFCRibbonLinkCtrl::OnDraw](#ondraw)|（覆盖[CMFC 功能按钮：onDraw](../../mfc/reference/cmfcribbonbutton-class.md#ondraw).）|
|[CMFCRibbonLinkCtrl::OnDrawMenuImage](#ondrawmenuimage)|（覆盖[CMFC 功能基础元素：在DrawMenuImage.）](../../mfc/reference/cmfcribbonbaseelement-class.md#ondrawmenuimage)|
|[CMFCRibbonLinkCtrl::OnMouseMove](#onmousemove)|（重写 `CMFCRibbonButton::OnMouseMove`。）|
|[CMFCRibbonLinkCtrl::OnSetIcon](#onseticon)||
|[CMFCRibbonLinkCtrl::OpenLink](#openlink)|将打开超链接中指定的 Web 页。|
|[CMFCRibbonLinkCtrl::SetLink](#setlink)|设置超链接的值。|

## <a name="remarks"></a>备注

创建超链接后，请通过调用[CMFC 功能程序：：：添加](../../mfc/reference/cmfcribbonpanel-class.md#add)将其添加到面板中。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)\
•&nbsp;[CMFC功能基础元素](../../mfc/reference/cmfcribbonbaseelement-class.md)\
&nbsp;&nbsp;&nbsp;&nbsp;•&nbsp;[CMFC功能按钮](../../mfc/reference/cmfcribbonbutton-class.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;•&nbsp;[CMFC剪链接Ctrl](../../mfc/reference/cmfcribbonlinkctrl-class.md)

## <a name="requirements"></a>要求

**标题：** afxRibbonLinkCtrl.h

## <a name="cmfcribbonlinkctrlcmfcribbonlinkctrl"></a><a name="cmfcribbonlinkctrl"></a>CMFC 剪线链接Ctrl：：CMFC 剪线链接Ctrl

构造并初始化[CMFCRibbonLinkCtrl](../../mfc/reference/cmfcribbonlinkctrl-class.md)对象。

```
CMFCRibbonLinkCtrl(
    UINT nID,
    LPCTSTR lpszText,
    LPCTSTR lpszLink);
```

### <a name="parameters"></a>参数

*nID*<br/>
[在]指定单击链接控件时执行的命令的命令 ID。

*lpszText*<br/>
[在]指定要显示在链接控件上的标签。

*lpszLink*<br/>
[在]指定与链接控件关联的超链接。

### <a name="example"></a>示例

下面的示例演示如何使用`CMFCRibbonLinkCtrl`类的构造函数。 此代码段是[功能区小工具示例的一](../../overview/visual-cpp-samples.md)部分。

[!code-cpp[NVC_MFC_RibbonGadgets#1](../../mfc/reference/codesnippet/cpp/cmfcribbonlinkctrl-class_1.cpp)]

## <a name="cmfcribbonlinkctrlcopyfrom"></a><a name="copyfrom"></a>CMFC剪发链接Ctrl：：从复制

```
virtual void CopyFrom(const CMFCRibbonBaseElement& src);
```

### <a name="parameters"></a>参数

[在]*斯尔克*<br/>

### <a name="remarks"></a>备注

## <a name="cmfcribbonlinkctrlgetcompactsize"></a><a name="getcompactsize"></a>CMFC 功能链接Ctrl：获取压缩尺寸

```
virtual CSize GetCompactSize(CDC* pDC);
```

### <a name="parameters"></a>参数

[在]*pDC*<br/>

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

## <a name="cmfcribbonlinkctrlgetlink"></a><a name="getlink"></a>CMFC剪链接Ctrl：获取链接

返回超链接的值。

```
LPCTSTR GetLink() const;
```

### <a name="return-value"></a>返回值

超链接的当前值。

### <a name="remarks"></a>备注

## <a name="cmfcribbonlinkctrlgetregularsize"></a><a name="getregularsize"></a>CMFC 功能链接Ctrl：获取常规大小

```
virtual CSize GetRegularSize(CDC* pDC);
```

### <a name="parameters"></a>参数

[在]*pDC*<br/>

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

## <a name="cmfcribbonlinkctrlgettooltiptext"></a><a name="gettooltiptext"></a>CMFC 功能链接Ctrl：获取工具提示文本

```
virtual CString GetToolTipText() const;
```

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

## <a name="cmfcribbonlinkctrlondrawmenuimage"></a><a name="ondrawmenuimage"></a>CMFC功能链接Ctrl：在DrawMenu图像

```
virtual BOOL OnDrawMenuImage(CDC*, CRect);
```

### <a name="parameters"></a>参数

[在]*CDC&#42;*<br/>
[在]*CRect*<br/>

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

## <a name="cmfcribbonlinkctrlisdrawtooltipimage"></a><a name="isdrawtooltipimage"></a>CMFC 剪贴链接Ctrl：：正在绘制工具提示图像

```
virtual BOOL IsDrawTooltipImage() const;
```

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

## <a name="cmfcribbonlinkctrlondraw"></a><a name="ondraw"></a>CMFC里赛林Ctrl：在画上

```
virtual void OnDraw(CDC* pDC);
```

### <a name="parameters"></a>参数

[在]*pDC*<br/>

### <a name="remarks"></a>备注

## <a name="cmfcribbonlinkctrlonmousemove"></a><a name="onmousemove"></a>CMFC里塞林克Ctrl：在鼠标移动

```
virtual void OnMouseMove(CPoint point);
```

### <a name="parameters"></a>参数

[在]*点*<br/>

### <a name="remarks"></a>备注

## <a name="cmfcribbonlinkctrlonseticon"></a><a name="onseticon"></a>CMFC剪链接Ctrl：onSeticon

```
virtual void OnSetIcon();
```

### <a name="remarks"></a>备注

## <a name="cmfcribbonlinkctrlopenlink"></a><a name="openlink"></a>CMFC剪链接Ctrl：：打开链接

将打开超链接中指定的 Web 页。

```
BOOL OpenLink();
```

### <a name="return-value"></a>返回值

如果关联的网页已成功打开，则为 TRUE;否则，FALSE。

### <a name="remarks"></a>备注

使用与`CMFCRibbonLinkCtrl`对象关联的超链接打开网页。

## <a name="cmfcribbonlinkctrlsetlink"></a><a name="setlink"></a>CMFC 剪线链接：：设置链接

设置超链接的值。

```cpp
void SetLink(LPCTSTR lpszLink);
```

### <a name="parameters"></a>参数

*lpszLink*<br/>
[在]指定超链接文本。

## <a name="see-also"></a>请参阅

[层次结构图表](../../mfc/hierarchy-chart.md)<br/>
[类](../../mfc/reference/mfc-classes.md)<br/>
[CMFC 功能按钮类](../../mfc/reference/cmfcribbonbutton-class.md)
