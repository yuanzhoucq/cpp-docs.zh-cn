---
title: COleDropTarget 类
ms.date: 11/04/2016
f1_keywords:
- COleDropTarget
- AFXOLE/COleDropTarget
- AFXOLE/COleDropTarget::COleDropTarget
- AFXOLE/COleDropTarget::OnDragEnter
- AFXOLE/COleDropTarget::OnDragLeave
- AFXOLE/COleDropTarget::OnDragOver
- AFXOLE/COleDropTarget::OnDragScroll
- AFXOLE/COleDropTarget::OnDrop
- AFXOLE/COleDropTarget::OnDropEx
- AFXOLE/COleDropTarget::Register
- AFXOLE/COleDropTarget::Revoke
helpviewer_keywords:
- COleDropTarget [MFC], COleDropTarget
- COleDropTarget [MFC], OnDragEnter
- COleDropTarget [MFC], OnDragLeave
- COleDropTarget [MFC], OnDragOver
- COleDropTarget [MFC], OnDragScroll
- COleDropTarget [MFC], OnDrop
- COleDropTarget [MFC], OnDropEx
- COleDropTarget [MFC], Register
- COleDropTarget [MFC], Revoke
ms.assetid: a58c9a48-6a93-4357-b078-4594df258311
ms.openlocfilehash: 9a1633ed48c763b986f3421c33589a05f8bba126
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/18/2019
ms.locfileid: "58781635"
---
# <a name="coledroptarget-class"></a>COleDropTarget 类

提供窗口和 OLE 库之间的通信机制。

## <a name="syntax"></a>语法

```
class COleDropTarget : public CCmdTarget
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[COleDropTarget::COleDropTarget](#coledroptarget)|构造 `COleDropTarget` 对象。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[COleDropTarget::OnDragEnter](#ondragenter)|当光标首次进入窗口时调用。|
|[COleDropTarget::OnDragLeave](#ondragleave)|将光标拖出窗口时调用。|
|[COleDropTarget::OnDragOver](#ondragover)|当光标拖至窗口上重复调用。|
|[COleDropTarget::OnDragScroll](#ondragscroll)|调用以确定是否将光标拖到窗口的滚动区域。|
|[COleDropTarget::OnDrop](#ondrop)|当数据放入窗口中，默认处理程序时调用。|
|[COleDropTarget::OnDropEx](#ondropex)|当数据放入窗口中，初始处理程序时调用。|
|[COleDropTarget::Register](#register)|将窗口注册为有效的放置目标。|
|[COleDropTarget::Revoke](#revoke)|使窗口停止正在有效的放置目标。|

## <a name="remarks"></a>备注

创建此类的对象可让在窗口中通过 OLE 拖放机制接受的数据。

若要在窗口中接受 drop 命令，应首先创建的对象`COleDropTarget`类，然后调用[注册](#register)用一个指针指向所需的函数`CWnd`对象作为唯一参数。

拖放操作的详细信息使用 OLE，请参阅文章[拖放 (OLE)](../../mfc/drag-and-drop-ole.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

`COleDropTarget`

## <a name="requirements"></a>要求

**标头：** afxole.h

##  <a name="coledroptarget"></a>  COleDropTarget::COleDropTarget

构造一个对象，类的`COleDropTarget`。

```
COleDropTarget();
```

### <a name="remarks"></a>备注

调用[注册](#register)将此对象与窗口相关联。

##  <a name="ondragenter"></a>  COleDropTarget::OnDragEnter

当光标首次拖动到窗口时由框架调用。

```
virtual DROPEFFECT OnDragEnter(
    CWnd* pWnd,
    COleDataObject* pDataObject,
    DWORD dwKeyState,
    CPoint point);
```

### <a name="parameters"></a>参数

*pWnd*<br/>
输入指向窗口的光标。

*pDataObject*<br/>
指向包含要删除的数据的数据对象。

*dwKeyState*<br/>
包含修改键的状态。 这是以下任意数量的组合：MK_CONTROL、 MK_SHIFT、 MK_ALT、 MK_LBUTTON、 MK_MBUTTON 和 MK_RBUTTON。

*point*<br/>
包含当前工作区坐标中的光标位置。

### <a name="return-value"></a>返回值

放置已尝试在指定的位置时所产生的效果*点*。 它可以是一个或多项操作：

- 不允许放置 DROPEFFECT_NONE。

- DROPEFFECT_COPY 会执行复制操作。

- DROPEFFECT_MOVE 会执行移动操作。

- 将建立 DROPEFFECT_LINK 链接放置的数据从原始数据。

- DROPEFFECT_SCROLL A 拖动滚动操作即将发生或目标中不存在。

### <a name="remarks"></a>备注

重写此函数，以允许删除操作发生在窗口中。 默认实现调用[CView::OnDragEnter](../../mfc/reference/cview-class.md#ondragenter)，这只是默认情况下返回 DROPEFFECT_NONE。

有关详细信息，请参阅[IDropTarget::DragEnter](/windows/desktop/api/oleidl/nf-oleidl-idroptarget-dragenter) Windows SDK 中。

##  <a name="ondragleave"></a>  COleDropTarget::OnDragLeave

当光标离开在窗口实际上拖放操作时由框架调用。

```
virtual void OnDragLeave(CWnd* pWnd);
```

### <a name="parameters"></a>参数

*pWnd*<br/>
指向以窗口中光标离开。

### <a name="remarks"></a>备注

如果要使用特殊行为拖放操作离开指定的窗口时，重写此函数。 此函数的默认实现调用[CView::OnDragLeave](../../mfc/reference/cview-class.md#ondragleave)。

有关详细信息，请参阅[IDropTarget::DragLeave](/windows/desktop/api/oleidl/nf-oleidl-idroptarget-dragleave) Windows SDK 中。

##  <a name="ondragover"></a>  COleDropTarget::OnDragOver

当光标拖至窗口上时，由框架调用。

```
virtual DROPEFFECT OnDragOver(
    CWnd* pWnd,
    COleDataObject* pDataObject,
    DWORD dwKeyState,
    CPoint point);
```

### <a name="parameters"></a>参数

*pWnd*<br/>
光标位于窗口的点。

*pDataObject*<br/>
指向包含要删除的数据的数据对象。

*dwKeyState*<br/>
包含修改键的状态。 这是以下任意数量的组合：MK_CONTROL、 MK_SHIFT、 MK_ALT、 MK_LBUTTON、 MK_MBUTTON 和 MK_RBUTTON。

*point*<br/>
包含当前工作区坐标中的光标位置。

### <a name="return-value"></a>返回值

放置已尝试在指定的位置时所产生的效果*点*。 它可以是一个或多项操作：

- 不允许放置 DROPEFFECT_NONE。

- DROPEFFECT_COPY 会执行复制操作。

- DROPEFFECT_MOVE 会执行移动操作。

- 将建立 DROPEFFECT_LINK 链接放置的数据从原始数据。

- DROPEFFECT_SCROLL 指示拖动滚动操作即将发生或目标中不存在。

### <a name="remarks"></a>备注

应重写此函数以允许删除操作发生在窗口中。 此函数的默认实现调用[CView::OnDragOver](../../mfc/reference/cview-class.md#ondragover)，其默认情况下返回 DROPEFFECT_NONE。 因为在拖放操作频繁调用此函数时，应尽可能多地进行优化。

有关详细信息，请参阅[IDropTarget::DragOver](/windows/desktop/api/oleidl/nf-oleidl-idroptarget-dragover) Windows SDK 中。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCOleContainer#21](../../mfc/codesnippet/cpp/coledroptarget-class_1.cpp)]

##  <a name="ondragscroll"></a>  COleDropTarget::OnDragScroll

由框架调用之前调用[OnDragEnter](#ondragenter)或[OnDragOver](#ondragover)以确定是否*点*滚动区域。

```
virtual DROPEFFECT OnDragScroll(
    CWnd* pWnd,
    DWORD dwKeyState,
    CPoint point);
```

### <a name="parameters"></a>参数

*pWnd*<br/>
光标位于当前窗口的点。

*dwKeyState*<br/>
包含修改键的状态。 这是以下任意数量的组合：MK_CONTROL、 MK_SHIFT、 MK_ALT、 MK_LBUTTON、 MK_MBUTTON 和 MK_RBUTTON。

*point*<br/>
包含以像素为单位，相对于屏幕光标的位置。

### <a name="return-value"></a>返回值

放置已尝试在指定的位置时所产生的效果*点*。 它可以是一个或多项操作：

- 不允许放置 DROPEFFECT_NONE。

- DROPEFFECT_COPY 会执行复制操作。

- DROPEFFECT_MOVE 会执行移动操作。

- 将建立 DROPEFFECT_LINK 链接放置的数据从原始数据。

- DROPEFFECT_SCROLL 指示拖动滚动操作即将发生或目标中不存在。

### <a name="remarks"></a>备注

当你想要为此事件提供特殊行为时，重写此函数。 此函数的默认实现调用[CView::OnDragScroll](../../mfc/reference/cview-class.md#ondragscroll)，它返回 DROPEFFECT_NONE 并将光标拖到该窗口的边框内的默认滚动区域时滚动窗口。

##  <a name="ondrop"></a>  COleDropTarget::OnDrop

发生放置操作时由框架调用。

```
virtual BOOL OnDrop(
    CWnd* pWnd,
    COleDataObject* pDataObject,
    DROPEFFECT dropEffect,
    CPoint point);
```

### <a name="parameters"></a>参数

*pWnd*<br/>
光标位于当前窗口的点。

*pDataObject*<br/>
指向包含要删除的数据的数据对象。

*dropEffect*<br/>
用户选择为删除操作的效果。 它可以是一个或多项操作：

- DROPEFFECT_COPY 会执行复制操作。

- DROPEFFECT_MOVE 会执行移动操作。

- 将建立 DROPEFFECT_LINK 链接放置的数据从原始数据。

*point*<br/>
包含以像素为单位，相对于屏幕光标的位置。

### <a name="return-value"></a>返回值

如果下拉成功; 非零值否则为 0。

### <a name="remarks"></a>备注

框架将第一个调用[OnDropEx](#ondropex)。 如果`OnDropEx`函数不会处理拖放、 框架然后调用此成员函数， `OnDrop`。 通常情况下，应用程序的重写[OnDropEx](../../mfc/reference/cview-class.md#ondropex)在视图类来处理鼠标右键拖放。 通常情况下，视图类[OnDrop](../../mfc/reference/cview-class.md#ondrop)用于处理简单的拖放功能。

默认实现`COleDropTarget::OnDrop`调用[CView::OnDrop](../../mfc/reference/cview-class.md#ondrop)，这只是默认情况下返回 FALSE。

有关详细信息，请参阅[IDropTarget::Drop](/windows/desktop/api/oleidl/nf-oleidl-idroptarget-drop) Windows SDK 中。

##  <a name="ondropex"></a>  COleDropTarget::OnDropEx

发生放置操作时由框架调用。

```
virtual DROPEFFECT OnDropEx(
    CWnd* pWnd,
    COleDataObject* pDataObject,
    DROPEFFECT dropDefault,
    DROPEFFECT dropList,
    CPoint point);
```

### <a name="parameters"></a>参数

*pWnd*<br/>
光标位于当前窗口的点。

*pDataObject*<br/>
指向包含要删除的数据的数据对象。

*dropDefault*<br/>
用户选择基于当前的关键状态的默认拖放操作效果。 它可以是 DROPEFFECT_NONE。 放置效果备注部分所述。

*dropList*<br/>
放置源支持拖放效果的列表。 可以使用的按位 OR 组合放置效果值 (**&#124;**) 操作。 放置效果备注部分所述。

*point*<br/>
包含以像素为单位，相对于屏幕光标的位置。

### <a name="return-value"></a>返回值

由于在指定的位置删除尝试而导致的放效果*点*。 放置效果备注部分所述。

### <a name="remarks"></a>备注

首先，框架调用此函数。 如果它无法处理下拉菜单，然后调用框架[OnDrop](#ondrop)。 通常情况下，您将重写[OnDropEx](../../mfc/reference/cview-class.md#ondropex)在视图类，以支持鼠标右键拖放。 通常情况下，视图类[OnDrop](../../mfc/reference/cview-class.md#ondrop)用于处理对简单的拖放功能的支持情况。

默认实现`COleDropTarget::OnDropEx`调用[CView::OnDropEx](../../mfc/reference/cview-class.md#ondropex)。 默认情况下[CView::OnDropEx](../../mfc/reference/cview-class.md#ondropex)只需返回虚拟值以指示[OnDrop](#ondrop)应调用成员函数。

放置效果描述与拖放操作相关联的操作。 请参阅下面放置效果的列表：

- 不允许放置 DROPEFFECT_NONE。

- DROPEFFECT_COPY 会执行复制操作。

- DROPEFFECT_MOVE 会执行移动操作。

- 将建立 DROPEFFECT_LINK 链接放置的数据从原始数据。

- DROPEFFECT_SCROLL 指示拖动滚动操作即将发生或目标中不存在。

有关详细信息，请参阅[IDropTarget::Drop](/windows/desktop/api/oleidl/nf-oleidl-idroptarget-drop) Windows SDK 中。

##  <a name="register"></a>  COleDropTarget::Register

调用此函数向 OLE Dll 作为有效的放置目标注册您的窗口。

```
BOOL Register(CWnd* pWnd);
```

### <a name="parameters"></a>参数

*pWnd*<br/>
指向要注册为放置目标的窗口。

### <a name="return-value"></a>返回值

如果注册成功，则非零值否则为 0。

### <a name="remarks"></a>备注

拖放操作可以被接受，必须调用此函数。

有关详细信息，请参阅[RegisterDragDrop](/windows/desktop/api/ole2/nf-ole2-registerdragdrop) Windows SDK 中。

##  <a name="revoke"></a>  COleDropTarget::Revoke

销毁已注册为放置目标，通过调用任何窗口之前调用此函数[注册](#register)从放置目标的列表中删除它。

```
virtual void Revoke();
```

### <a name="remarks"></a>备注

从自动调用此函数[OnDestroy](../../mfc/reference/cwnd-class.md#ondestroy)处理程序已注册，因此通常需要显式调用此函数的窗口。

有关详细信息，请参阅[RevokeDragDrop](/windows/desktop/api/ole2/nf-ole2-revokedragdrop) Windows SDK 中。

## <a name="see-also"></a>请参阅

[MFC 示例 HIERSVR](../../overview/visual-cpp-samples.md)<br/>
[MFC 示例 OCLIENT](../../overview/visual-cpp-samples.md)<br/>
[CCmdTarget 类](../../mfc/reference/ccmdtarget-class.md)<br/>
[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[COleDropSource 类](../../mfc/reference/coledropsource-class.md)
