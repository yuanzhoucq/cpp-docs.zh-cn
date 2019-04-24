---
title: COleIPFrameWnd 类
ms.date: 11/04/2016
f1_keywords:
- COleIPFrameWnd
- AFXOLE/COleIPFrameWnd
- AFXOLE/COleIPFrameWnd::COleIPFrameWnd
- AFXOLE/COleIPFrameWnd::OnCreateControlBars
- AFXOLE/COleIPFrameWnd::RepositionFrame
helpviewer_keywords:
- COleIPFrameWnd [MFC], COleIPFrameWnd
- COleIPFrameWnd [MFC], OnCreateControlBars
- COleIPFrameWnd [MFC], RepositionFrame
ms.assetid: 24abb2cb-826c-4dda-a287-d8a8900a5763
ms.openlocfilehash: 34388e635ba89d732ae3993074a2c8268e2289a3
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/18/2019
ms.locfileid: "58779607"
---
# <a name="coleipframewnd-class"></a>COleIPFrameWnd 类

应用程序就地编辑窗口的基。

## <a name="syntax"></a>语法

```
class COleIPFrameWnd : public CFrameWnd
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[COleIPFrameWnd::COleIPFrameWnd](#coleipframewnd)|构造 `COleIPFrameWnd` 对象。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[COleIPFrameWnd::OnCreateControlBars](#oncreatecontrolbars)|项激活进行就地编辑时由框架调用。|
|[COleIPFrameWnd::RepositionFrame](#repositionframe)|由框架调用以重新定位就地编辑窗口。|

## <a name="remarks"></a>备注

此类创建和位置控件容器应用程序的文档窗口中的条。 它还处理生成的嵌入通知[COleResizeBar](../../mfc/reference/coleresizebar-class.md)对象在用户调整的就地编辑窗口。

有关使用的详细信息`COleIPFrameWnd`，请参阅文章[激活](../../mfc/activation-cpp.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CFrameWnd](../../mfc/reference/cframewnd-class.md)

`COleIPFrameWnd`

## <a name="requirements"></a>要求

**标头：** afxole.h

##  <a name="coleipframewnd"></a>  COleIPFrameWnd::COleIPFrameWnd

构造`COleIPFrameWnd`对象并初始化其就地状态信息，它存储在类型 OLEINPLACEFRAMEINFO 的结构。

```
COleIPFrameWnd();
```

### <a name="remarks"></a>备注

有关详细信息，请参阅[OLEINPLACEFRAMEINFO](/windows/desktop/api/oleidl/ns-oleidl-tagoifi) Windows SDK 中。

##  <a name="oncreatecontrolbars"></a>  COleIPFrameWnd::OnCreateControlBars

框架将调用`OnCreateControlBars`时进行就地编辑激活某个项的功能。

```
virtual BOOL OnCreateControlBars(
    CWnd* pWndFrame,
    CWnd* pWndDoc);

virtual BOOL OnCreateControlBars(
    CFrameWnd* pWndFrame,
    CFrameWnd* pWndDoc);
```

### <a name="parameters"></a>参数

*pWndFrame*<br/>
向容器应用程序的框架窗口的指针。

*pWndDoc*<br/>
指向容器的文档级别窗口的指针。 如果容器是 SDI 应用程序，可以为 NULL。

### <a name="return-value"></a>返回值

非零值; 如果成功否则为为 0。

### <a name="remarks"></a>备注

默认实现不执行任何操作。 重写此函数可执行创建条形图控件时所需任何特殊处理。

##  <a name="repositionframe"></a>  COleIPFrameWnd::RepositionFrame

框架将调用`RepositionFrame`版式控件条和重新定位就地编辑窗口，因此它是可见的成员函数。

```
virtual void RepositionFrame(
    LPCRECT lpPosRect,
    LPCRECT lpClipRect);
```

### <a name="parameters"></a>参数

*lpPosRect*<br/>
指向`RECT`结构或`CRect`对象，其中包含的就地框架窗口的当前位置坐标，以像素为单位，相对于客户端区域。

*lpClipRect*<br/>
指向`RECT`结构或`CRect`对象，其中包含的就地框架窗口的当前剪辑矩形坐标，以像素为单位，相对于客户端区域。

### <a name="remarks"></a>备注

在容器窗口中的控件条的布局不同于执行的非 OLE 框架窗口。 非 OLE 框架窗口计算的位置控件条和其他对象从给定的框架窗口大小，如下所示调用[CFrameWnd::RecalcLayout](../../mfc/reference/cframewnd-class.md#recalclayout)。 客户端区域是什么仍后减去控件条和其他对象的空间。 一个`COleIPFrameWnd`窗口中，但是，根据给定的工作区定位工具栏。 换而言之， `CFrameWnd::RecalcLayout` "从在中，外部"起作用，而`COleIPFrameWnd::RepositionFrame`工作原理"从内到外。"

## <a name="see-also"></a>请参阅

[MFC 示例 HIERSVR](../../overview/visual-cpp-samples.md)<br/>
[CFrameWnd 类](../../mfc/reference/cframewnd-class.md)<br/>
[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[CFrameWnd 类](../../mfc/reference/cframewnd-class.md)
