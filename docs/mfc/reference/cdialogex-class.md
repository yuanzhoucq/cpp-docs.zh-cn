---
title: CDialogEx 类
ms.date: 11/04/2016
f1_keywords:
- CDialogEx
- AFXDIALOGEX/CDialogEx
- AFXDIALOGEX/CDialogEx::CDialogEx
- AFXDIALOGEX/CDialogEx::SetBackgroundColor
- AFXDIALOGEX/CDialogEx::SetBackgroundImage
helpviewer_keywords:
- CDialogEx [MFC], CDialogEx
- CDialogEx [MFC], SetBackgroundColor
- CDialogEx [MFC], SetBackgroundImage
ms.assetid: a6ed3b1f-aef8-4b66-ac78-2160faf63c13
ms.openlocfilehash: 717e560035d42957c16168097577d0c8c589e3c7
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/22/2020
ms.locfileid: "81753348"
---
# <a name="cdialogex-class"></a>CDialogEx 类

`CDialogEx`类指定对话框的背景色和背景图像。

## <a name="syntax"></a>语法

```
class CDialogEx : public CDialog
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[CDialogEx::CDialogEx](#cdialogex)|构造 `CDialogEx` 对象。|
|`CDialogEx::~CDialogEx`|析构函数。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CDialogEx::SetBackgroundColor](#setbackgroundcolor)|设置对话框的背景色。|
|[CDialogEx::SetBackgroundImage](#setbackgroundimage)|设置对话框的背景图像。|

## <a name="remarks"></a>备注

若要使用`CDialogEx`类，则从`CDialogEx`类而不是`CDialog`类派生对话框类。

对话框图像存储在资源文件中。 该框架将自动删除从资源文件加载的任何图像。 要以编程方式删除当前背景图像，请调用[CDialogEx：：Set背景图像](#setbackgroundimage)方法或实现`OnDestroy`事件处理程序。 调用[CDialogEx：：Set背景图像](#setbackgroundimage)方法时，将参数`HBITMAP`作为图像句柄传递。 如果`CDialogEx`标记是`m_bAutoDestroyBmp`，`TRUE`对象将取得图像的所有权并将其删除。

对象`CDialogEx`可以是[CMFCPopupMenu 类](../../mfc/reference/cmfcpopupmenu-class.md)对象的父对象。 [CMFCPopupMenu 类](../../mfc/reference/cmfcpopupmenu-class.md)对象在`CDialogEx::SetActiveMenu`[CMFCPopupMenu 类](../../mfc/reference/cmfcpopupmenu-class.md)对象打开时调用该方法。 之后，`CDialogEx`对象处理任何菜单事件，直到[CMFCPopupMenu 类](../../mfc/reference/cmfcpopupmenu-class.md)对象关闭。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CDialogEx](../../mfc/reference/cdialogex-class.md)

## <a name="requirements"></a>要求

**标题：** afxdialogex.h

## <a name="cdialogexcdialogex"></a><a name="cdialogex"></a>CDialogEx：CDialogEx

构造 `CDialogEx` 对象。

```
CDialogEx(
    UINT nIDTemplate,
    CWnd* pParent=NULL);

CDialogEx(
    LPCTSTR lpszTemplateName,
    CWnd* pParentWnd=NULL);
```

### <a name="parameters"></a>参数

*nIDTemplate*<br/>
[在]对话框模板的资源 ID。

*lpszTemplate 名称*<br/>
[在]对话框模板的资源名称。

*p 父级*<br/>
[在]指向父窗口的指针。 默认值为 NULL。

*pparentwnd*<br/>
[在]指向父窗口的指针。 默认值为 NULL。

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

## <a name="cdialogexsetbackgroundcolor"></a><a name="setbackgroundcolor"></a>CDialogEx：：设置背景颜色

设置对话框的背景色。

```cpp
void SetBackgroundColor(
    COLORREF color,
    BOOL bRepaint=TRUE);
```

### <a name="parameters"></a>参数

*颜色*<br/>
[在]RGB 颜色值。

*bRepaint*<br/>
[在]TRUE 可立即更新屏幕;否则，FALSE。 默认值为 TRUE。

### <a name="remarks"></a>备注

## <a name="cdialogexsetbackgroundimage"></a><a name="setbackgroundimage"></a>CDialogEx：：设置背景图像

设置对话框的背景图像。

```cpp
void SetBackgroundImage(
    HBITMAP hBitmap,
    BackgroundLocation location=BACKGR_TILE,
    BOOL bAutoDestroy=TRUE,
    BOOL bRepaint=TRUE);

BOOL SetBackgroundImage(
    UINT uiBmpResId,
    BackgroundLocation location=BACKGR_TILE,
    BOOL bRepaint=TRUE);
```

### <a name="parameters"></a>参数

*hBitmap*<br/>
[在]背景图像的句柄。

*乌布布雷西德*<br/>
[在]背景图像的资源 ID。

*location*<br/>
[在]指定图像位置`CDialogEx::BackgroundLocation`的值之一。 有效值包括BACKGR_TILE、BACKGR_TOPLEFT、BACKGR_TOPRIGHT、BACKGR_BOTTOMLEFT和BACKGR_BOTTOMRIGHT。 默认值为BACKGR_TILE。

*bAuto销毁*<br/>
[在]TRUE 自动销毁背景图像;否则，FALSE。

*bRepaint*<br/>
[在]TRUE 可立即重绘对话框;否则，FALSE。

### <a name="return-value"></a>返回值

在第二个方法重载语法中，如果该方法成功，则为 TRUE;否则，FALSE。

### <a name="remarks"></a>备注

指定的图像不会拉伸以适合对话框工作区。

## <a name="see-also"></a>请参阅

[层次结构图表](../../mfc/hierarchy-chart.md)<br/>
[类](../../mfc/reference/mfc-classes.md)<br/>
[CMFCPopupMenu 类](../../mfc/reference/cmfcpopupmenu-class.md)<br/>
[CContextMenuManager 类](../../mfc/reference/ccontextmenumanager-class.md)
