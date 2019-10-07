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
ms.openlocfilehash: 891b19112c8baf2efb088f064892e1ea19a7deab
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69503969"
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
|[COleDropTarget::OnDragLeave](#ondragleave)|当将光标拖出窗口时调用。|
|[COleDropTarget::OnDragOver](#ondragover)|将光标拖动到窗口上时, 将重复调用。|
|[COleDropTarget::OnDragScroll](#ondragscroll)|调用以确定光标是否拖到窗口的滚动区域。|
|[COleDropTarget::OnDrop](#ondrop)|在将数据放入窗口时调用, 默认处理程序。|
|[COleDropTarget::OnDropEx](#ondropex)|在将数据放入窗口时调用, 初始处理程序。|
|[COleDropTarget::Register](#register)|将窗口注册为有效的拖放目标。|
|[COleDropTarget::Revoke](#revoke)|使窗口停止为有效的拖放目标。|

## <a name="remarks"></a>备注

通过创建此类的对象, 窗口可以通过 OLE 拖放机制接受数据。

若要获取窗口以接受 drop 命令, 你应该首先创建`COleDropTarget`类的对象, 然后使用指向所需`CWnd`对象的指针作为唯一参数调用[Register](#register)函数。

有关使用 OLE 拖放操作的详细信息, 请参阅[拖放 (OLE)](../../mfc/drag-and-drop-ole.md)一文。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

`COleDropTarget`

## <a name="requirements"></a>要求

**标头:** afxole

##  <a name="coledroptarget"></a>  COleDropTarget::COleDropTarget

构造类`COleDropTarget`的对象。

```
COleDropTarget();
```

### <a name="remarks"></a>备注

调用[Register](#register)将此对象与窗口关联。

##  <a name="ondragenter"></a>  COleDropTarget::OnDragEnter

当游标第一次拖动到窗口中时由框架调用。

```
virtual DROPEFFECT OnDragEnter(
    CWnd* pWnd,
    COleDataObject* pDataObject,
    DWORD dwKeyState,
    CPoint point);
```

### <a name="parameters"></a>参数

*pWnd*<br/>
指向光标进入的窗口。

*pDataObject*<br/>
指向包含可以删除的数据的数据对象。

*dwKeyState*<br/>
包含修改键的状态。 这是以下任意数量的组合:MK_CONTROL、MK_SHIFT、MK_ALT、MK_LBUTTON、MK_MBUTTON 和 MK_RBUTTON。

*point*<br/>
包含光标在工作区坐标中的当前位置。

### <a name="return-value"></a>返回值

尝试在*点*指定的位置处放置时将产生的效果。 它可以是下列一项或多项:

- DROPEFFECT_NONE 不允许删除。

- DROPEFFECT_COPY 将执行复制操作。

- DROPEFFECT_MOVE 将执行移动操作。

- DROPEFFECT_LINK 会建立从已删除数据到原始数据的链接。

- DROPEFFECT_SCROLL 将发生拖动滚动操作, 或在目标中发生。

### <a name="remarks"></a>备注

重写此函数以允许在窗口中执行放置操作。 默认实现调用[CView:: system.windows.uielement.ondragenter](../../mfc/reference/cview-class.md#ondragenter), 后者在默认情况下只返回 DROPEFFECT_NONE。

有关详细信息, 请参阅 IDropTarget: Windows SDK 中的[::D ragenter](/windows/win32/api/oleidl/nf-oleidl-idroptarget-dragenter) 。

##  <a name="ondragleave"></a>  COleDropTarget::OnDragLeave

当光标离开窗口且拖动操作有效时由框架调用。

```
virtual void OnDragLeave(CWnd* pWnd);
```

### <a name="parameters"></a>参数

*pWnd*<br/>
指向光标离开的窗口。

### <a name="remarks"></a>备注

如果要在拖动操作离开指定窗口时有特殊行为, 请重写此函数。 此函数的默认实现调用[CView:: system.windows.uielement.ondragleave](../../mfc/reference/cview-class.md#ondragleave)。

有关详细信息, 请参阅 IDropTarget: Windows SDK 中的[::D ragleave](/windows/win32/api/oleidl/nf-oleidl-idroptarget-dragleave) 。

##  <a name="ondragover"></a>  COleDropTarget::OnDragOver

当光标拖动到窗口上时由框架调用。

```
virtual DROPEFFECT OnDragOver(
    CWnd* pWnd,
    COleDataObject* pDataObject,
    DWORD dwKeyState,
    CPoint point);
```

### <a name="parameters"></a>参数

*pWnd*<br/>
指向光标所在的窗口。

*pDataObject*<br/>
指向包含要删除的数据的数据对象。

*dwKeyState*<br/>
包含修改键的状态。 这是以下任意数量的组合:MK_CONTROL、MK_SHIFT、MK_ALT、MK_LBUTTON、MK_MBUTTON 和 MK_RBUTTON。

*point*<br/>
包含光标在工作区坐标中的当前位置。

### <a name="return-value"></a>返回值

尝试在*点*指定的位置处放置时将产生的效果。 它可以是下列一项或多项:

- DROPEFFECT_NONE 不允许删除。

- DROPEFFECT_COPY 将执行复制操作。

- DROPEFFECT_MOVE 将执行移动操作。

- DROPEFFECT_LINK 会建立从已删除数据到原始数据的链接。

- DROPEFFECT_SCROLL 指示将要发生或在目标中发生拖动滚动操作。

### <a name="remarks"></a>备注

应重写此函数, 以允许在窗口中执行 drop 操作。 此函数的默认实现将调用[CView:: system.windows.uielement.ondragover](../../mfc/reference/cview-class.md#ondragover), 这将默认返回 DROPEFFECT_NONE。 由于在拖放操作过程中频繁调用此函数, 因此应尽可能优化此函数。

有关详细信息, 请参阅 IDropTarget: Windows SDK 中的[::D ragover](/windows/win32/api/oleidl/nf-oleidl-idroptarget-dragover) 。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCOleContainer#21](../../mfc/codesnippet/cpp/coledroptarget-class_1.cpp)]

##  <a name="ondragscroll"></a>  COleDropTarget::OnDragScroll

在调用[system.windows.uielement.ondragenter](#ondragenter)或[system.windows.uielement.ondragover](#ondragover)之前由框架调用, 以确定*点*是否在滚动区域中。

```
virtual DROPEFFECT OnDragScroll(
    CWnd* pWnd,
    DWORD dwKeyState,
    CPoint point);
```

### <a name="parameters"></a>参数

*pWnd*<br/>
指向光标当前悬停的窗口。

*dwKeyState*<br/>
包含修改键的状态。 这是以下任意数量的组合:MK_CONTROL、MK_SHIFT、MK_ALT、MK_LBUTTON、MK_MBUTTON 和 MK_RBUTTON。

*point*<br/>
包含光标相对于屏幕的位置 (以像素为单位)。

### <a name="return-value"></a>返回值

尝试在*点*指定的位置处放置时将产生的效果。 它可以是下列一项或多项:

- DROPEFFECT_NONE 不允许删除。

- DROPEFFECT_COPY 将执行复制操作。

- DROPEFFECT_MOVE 将执行移动操作。

- DROPEFFECT_LINK 会建立从已删除数据到原始数据的链接。

- DROPEFFECT_SCROLL 指示将要发生或在目标中发生拖动滚动操作。

### <a name="remarks"></a>备注

如果要为此事件提供特殊行为, 请重写此函数。 此函数的默认实现将调用[CView:: OnDragScroll](../../mfc/reference/cview-class.md#ondragscroll), 这将返回 DROPEFFECT_NONE, 并在光标拖动到窗口边框内的默认滚动区域内时滚动窗口。

##  <a name="ondrop"></a>  COleDropTarget::OnDrop

当发生放置操作时由框架调用。

```
virtual BOOL OnDrop(
    CWnd* pWnd,
    COleDataObject* pDataObject,
    DROPEFFECT dropEffect,
    CPoint point);
```

### <a name="parameters"></a>参数

*pWnd*<br/>
指向光标当前悬停的窗口。

*pDataObject*<br/>
指向包含要删除的数据的数据对象。

*dropEffect*<br/>
用户为放置操作选择的效果。 它可以是下列一项或多项:

- DROPEFFECT_COPY 将执行复制操作。

- DROPEFFECT_MOVE 将执行移动操作。

- DROPEFFECT_LINK 会建立从已删除数据到原始数据的链接。

*point*<br/>
包含光标相对于屏幕的位置 (以像素为单位)。

### <a name="return-value"></a>返回值

如果删除成功, 则为非零值;否则为0。

### <a name="remarks"></a>备注

框架首先调用[OnDropEx](#ondropex)。 如果该`OnDrop`函数不处理放置, 则框架将调用此成员函数。 `OnDropEx` 通常, 应用程序会重写视图类中的[OnDropEx](../../mfc/reference/cview-class.md#ondropex) , 以处理鼠标右键拖放。 通常, 视图类[system.windows.uielement.ondrop](../../mfc/reference/cview-class.md#ondrop)用于处理简单的拖放。

的`COleDropTarget::OnDrop`默认实现调用[CView:: system.windows.uielement.ondrop](../../mfc/reference/cview-class.md#ondrop), 后者在默认情况下只返回 FALSE。

有关详细信息, 请参阅 IDropTarget: Windows SDK 中的[::D rop](/windows/win32/api/oleidl/nf-oleidl-idroptarget-drop) 。

##  <a name="ondropex"></a>  COleDropTarget::OnDropEx

当发生放置操作时由框架调用。

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
指向光标当前悬停的窗口。

*pDataObject*<br/>
指向包含要删除的数据的数据对象。

*dropDefault*<br/>
用户根据当前键状态选择的默认删除操作的效果。 它可以是 DROPEFFECT_NONE。 "备注" 部分讨论了 Drop 效果。

*dropList*<br/>
放置源所支持的放置效果的列表。 可以使用按位 "或" ( **&#124;** ) 运算组合删除效果值。 "备注" 部分讨论了 Drop 效果。

*point*<br/>
包含光标相对于屏幕的位置 (以像素为单位)。

### <a name="return-value"></a>返回值

由于放置尝试在*点*指定的位置导致的放置效果。 "备注" 部分讨论了 Drop 效果。

### <a name="remarks"></a>备注

框架首先调用此函数。 如果它未处理 drop, 则框架将调用[system.windows.uielement.ondrop](#ondrop)。 通常, 您将重写 view 类中的[OnDropEx](../../mfc/reference/cview-class.md#ondropex)以支持鼠标右键拖放。 通常, 视图类[system.windows.uielement.ondrop](../../mfc/reference/cview-class.md#ondrop)用于处理简单拖放支持的情况。

的`COleDropTarget::OnDropEx`默认实现调用[CView:: OnDropEx](../../mfc/reference/cview-class.md#ondropex)。 默认情况下, [CView:: OnDropEx](../../mfc/reference/cview-class.md#ondropex)只返回一个虚拟值, 以指示应调用[system.windows.uielement.ondrop](#ondrop)成员函数。

Drop 效果描述与删除操作相关联的操作。 请参阅下面的删除效果列表:

- DROPEFFECT_NONE 不允许删除。

- DROPEFFECT_COPY 将执行复制操作。

- DROPEFFECT_MOVE 将执行移动操作。

- DROPEFFECT_LINK 会建立从已删除数据到原始数据的链接。

- DROPEFFECT_SCROLL 指示将要发生或在目标中发生拖动滚动操作。

有关详细信息, 请参阅 IDropTarget: Windows SDK 中的[::D rop](/windows/win32/api/oleidl/nf-oleidl-idroptarget-drop) 。

##  <a name="register"></a>  COleDropTarget::Register

调用此函数可将您的窗口和 OLE Dll 注册为有效的放置目标。

```
BOOL Register(CWnd* pWnd);
```

### <a name="parameters"></a>参数

*pWnd*<br/>
指向要注册为拖放目标的窗口。

### <a name="return-value"></a>返回值

如果注册成功, 则为非零值;否则为0。

### <a name="remarks"></a>备注

若要接受 drop 操作, 必须调用此函数。

有关详细信息, 请参阅 Windows SDK 中的[RegisterDragDrop](/windows/win32/api/ole2/nf-ole2-registerdragdrop) 。

##  <a name="revoke"></a>  COleDropTarget::Revoke

在销毁已通过调用[Register](#register)注册为拖放目标的任何窗口之前调用此函数, 以将其从拖放目标列表中删除。

```
virtual void Revoke();
```

### <a name="remarks"></a>备注

此函数是从已注册窗口的[OnDestroy](../../mfc/reference/cwnd-class.md#ondestroy)处理程序自动调用的, 因此通常不需要显式调用此函数。

有关详细信息, 请参阅 Windows SDK 中的[RevokeDragDrop](/windows/win32/api/ole2/nf-ole2-revokedragdrop) 。

## <a name="see-also"></a>请参阅

[MFC 示例 HIERSVR](../../overview/visual-cpp-samples.md)<br/>
[MFC 示例 OCLIENT](../../overview/visual-cpp-samples.md)<br/>
[CCmdTarget 类](../../mfc/reference/ccmdtarget-class.md)<br/>
[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[COleDropSource 类](../../mfc/reference/coledropsource-class.md)
