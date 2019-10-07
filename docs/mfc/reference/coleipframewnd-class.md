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
ms.openlocfilehash: 8eab2ddfc778900b53d77105f1d8215a2c095e9f
ms.sourcegitcommit: 180f63704f6ddd07a4172a93b179cf0733fd952d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/06/2019
ms.locfileid: "70741563"
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
|[COleIPFrameWnd：： COleIPFrameWnd](#coleipframewnd)|构造 `COleIPFrameWnd` 对象。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[COleIPFrameWnd::OnCreateControlBars](#oncreatecontrolbars)|当激活某项以进行就地编辑时，由框架调用。|
|[COleIPFrameWnd::RepositionFrame](#repositionframe)|由框架调用以重定位就地编辑窗口。|

## <a name="remarks"></a>备注

此类在容器应用程序的文档窗口中创建并定位控件条。 当用户调整就地编辑窗口的大小时，它还处理嵌入[COleResizeBar](../../mfc/reference/coleresizebar-class.md)对象生成的通知。

有关使用`COleIPFrameWnd`的详细信息，请参阅文章[激活](../../mfc/activation-cpp.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CFrameWnd](../../mfc/reference/cframewnd-class.md)

`COleIPFrameWnd`

## <a name="requirements"></a>要求

**标头：** afxole

##  <a name="coleipframewnd"></a>COleIPFrameWnd：： COleIPFrameWnd

构造一个`COleIPFrameWnd`对象并初始化其就地状态信息，该信息存储在 OLEINPLACEFRAMEINFO 类型的结构中。

```
COleIPFrameWnd();
```

### <a name="remarks"></a>备注

有关详细信息，请参阅 Windows SDK 中的[OLEINPLACEFRAMEINFO](/windows/win32/api/oleidl/ns-oleidl-oleinplaceframeinfo) 。

##  <a name="oncreatecontrolbars"></a>COleIPFrameWnd：： Oncreatecontrolbars 以便

当激活某项`OnCreateControlBars`以进行就地编辑时，框架将调用该函数。

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
指向容器应用程序框架窗口的指针。

*pWndDoc*<br/>
指向容器文档级窗口的指针。 如果容器是 SDI 应用程序，则可以为 NULL。

### <a name="return-value"></a>返回值

如果成功，则为非零;否则为0。

### <a name="remarks"></a>备注

默认实现不执行任何操作。 重写此函数以在创建控件条时执行所需的任何特殊处理。

##  <a name="repositionframe"></a>COleIPFrameWnd：： RepositionFrame

框架调用`RepositionFrame`成员函数来布置控件条并重新定位就地编辑窗口，使其全部可见。

```
virtual void RepositionFrame(
    LPCRECT lpPosRect,
    LPCRECT lpClipRect);
```

### <a name="parameters"></a>参数

*lpPosRect*<br/>
指向`RECT` 结构`CRect`或对象的指针，该对象包含就地框架窗口的当前位置坐标（以像素为单位），相对于工作区。

*lpClipRect*<br/>
指向`RECT`结构的指针`CRect`或包含就地框架窗口的当前剪辑矩形坐标（以像素为单位）相对于工作区的对象。

### <a name="remarks"></a>备注

容器窗口中的控件条布局不同于非 OLE 框架窗口执行的布局。 非 OLE 框架窗口根据给定的框架窗口大小计算控件条和其他对象的位置，如对[CFrameWnd：： RecalcLayout](../../mfc/reference/cframewnd-class.md#recalclayout)的调用。 工作区是指在控制栏和其他对象的空间被减去后保留的区域。 另一方面`COleIPFrameWnd` ，窗口根据给定的工作区定位工具栏。 换句话说， `CFrameWnd::RecalcLayout`在中的 "从外" 工作， `COleIPFrameWnd::RepositionFrame`从内到外 "工作"。

## <a name="see-also"></a>请参阅

[MFC 示例 HIERSVR](../../overview/visual-cpp-samples.md)<br/>
[CFrameWnd 类](../../mfc/reference/cframewnd-class.md)<br/>
[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[CFrameWnd 类](../../mfc/reference/cframewnd-class.md)
