---
title: COleIPFramewnd 类
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
ms.openlocfilehash: 01e259cf01c42add26088b0cbd2f6dab311eb9b1
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374960"
---
# <a name="coleipframewnd-class"></a>COleIPFramewnd 类

应用程序就地编辑窗口的基。

## <a name="syntax"></a>语法

```
class COleIPFrameWnd : public CFrameWnd
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[COleIPFramewnd：COleIPFramewnd](#coleipframewnd)|构造 `COleIPFrameWnd` 对象。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[COleIPFramewnd：：在创建控制栏上](#oncreatecontrolbars)|当项目被激活进行就地编辑时，由框架调用。|
|[COleIPFramewnd：：重新定位框架](#repositionframe)|由框架调用重新定位就地编辑窗口。|

## <a name="remarks"></a>备注

此类在容器应用程序的文档窗口中创建和定位控制栏。 当用户调整就地编辑窗口的大小时，它还处理由嵌入式[COle ResizeBar](../../mfc/reference/coleresizebar-class.md)对象生成的通知。

有关使用`COleIPFrameWnd`的详细信息，请参阅文章[激活](../../mfc/activation-cpp.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CFrameWnd](../../mfc/reference/cframewnd-class.md)

`COleIPFrameWnd`

## <a name="requirements"></a>要求

**标题：** afxole.h

## <a name="coleipframewndcoleipframewnd"></a><a name="coleipframewnd"></a>COleIPFramewnd：COleIPFramewnd

构造`COleIPFrameWnd`对象并初始化其就地状态信息，这些信息存储在 OLEINPLACEFRAMEINFO 类型的结构中。

```
COleIPFrameWnd();
```

### <a name="remarks"></a>备注

有关详细信息，请参阅 Windows SDK 中的[OLEINPLACEFRAMEINFO。](/windows/win32/api/oleidl/ns-oleidl-oleinplaceframeinfo)

## <a name="coleipframewndoncreatecontrolbars"></a><a name="oncreatecontrolbars"></a>COleIPFramewnd：：在创建控制栏上

当激活项目进行`OnCreateControlBars`就地编辑时，框架将调用该函数。

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
指向容器应用程序的帧窗口的指针。

*普恩德多克*<br/>
指向容器的文档级窗口的指针。 如果容器是 SDI 应用程序，则可以为 NULL。

### <a name="return-value"></a>返回值

成功时为非零;否则，0。

### <a name="remarks"></a>备注

默认实现不执行任何操作。 重写此函数以在创建控制条时执行所需的任何特殊处理。

## <a name="coleipframewndrepositionframe"></a><a name="repositionframe"></a>COleIPFramewnd：：重新定位框架

框架调用`RepositionFrame`成员函数来布局控制栏并重新定位就地编辑窗口，以便所有控件都可见。

```
virtual void RepositionFrame(
    LPCRECT lpPosRect,
    LPCRECT lpClipRect);
```

### <a name="parameters"></a>参数

*lpPosRect*<br/>
指向`RECT`包含就地帧窗口`CRect`当前位置坐标的结构或对象（以像素为单位）相对于工作区的指针。

*lpClipRect*<br/>
指向`RECT`包含就地框架窗口`CRect`当前剪切矩形坐标的结构或对象（以像素为单位）相对于工作区的指针。

### <a name="remarks"></a>备注

容器窗口中的控制栏的布局不同于非 OLE 框架窗口执行的布局。 非 OLE 框架窗口计算来自给定帧窗口大小的控制条和其他对象的位置，如对[CFrameWnd 的调用：：recalcLayout](../../mfc/reference/cframewnd-class.md#recalclayout)。 工作区是减去控制条和其他对象的空间后保留的内容。 另`COleIPFrameWnd`一方面，窗口根据给定的工作区定位工具栏。 换句话说，`CFrameWnd::RecalcLayout`作品"从外面"，而`COleIPFrameWnd::RepositionFrame`工作"从内到外"。

## <a name="see-also"></a>另请参阅

[MFC 样品 HIERSVR](../../overview/visual-cpp-samples.md)<br/>
[CFrameWnd 类](../../mfc/reference/cframewnd-class.md)<br/>
[层次结构图表](../../mfc/hierarchy-chart.md)<br/>
[CFrameWnd 类](../../mfc/reference/cframewnd-class.md)
