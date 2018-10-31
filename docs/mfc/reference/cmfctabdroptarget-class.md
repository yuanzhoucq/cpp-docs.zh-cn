---
title: CMFCTabDropTarget 类 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMFCTabDropTarget
- AFXBASETABCTRL/CMFCTabDropTarget
- AFXBASETABCTRL/CMFCTabDropTarget::OnDragEnter
- AFXBASETABCTRL/CMFCTabDropTarget::OnDragLeave
- AFXBASETABCTRL/CMFCTabDropTarget::OnDragOver
- AFXBASETABCTRL/CMFCTabDropTarget::OnDropEx
- AFXBASETABCTRL/CMFCTabDropTarget::Register
dev_langs:
- C++
helpviewer_keywords:
- CMFCTabDropTarget [MFC], OnDragEnter
- CMFCTabDropTarget [MFC], OnDragLeave
- CMFCTabDropTarget [MFC], OnDragOver
- CMFCTabDropTarget [MFC], OnDropEx
- CMFCTabDropTarget [MFC], Register
ms.assetid: 9777b7b6-10da-4c4b-b1d1-7ea795b0f1cb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ca9b67737933ceeb59861234759aa2652b6b985e
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/25/2018
ms.locfileid: "50057447"
---
# <a name="cmfctabdroptarget-class"></a>CMFCTabDropTarget 类

提供了一个选项卡控件与 OLE 库之间的通信机制。

## <a name="syntax"></a>语法

```
class CMFCTabDropTarget : public COleDropTarget
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|||
|-|-|
|名称|描述|
|`CMFCTabDropTarget::CMFCTabDropTarget`|默认构造函数。|

### <a name="public-methods"></a>公共方法

|||
|-|-|
|名称|描述|
|[CMFCTabDropTarget::OnDragEnter](#ondragenter)|用户将对象拖到选项卡窗口时由框架调用。 (重写[COleDropTarget::OnDragEnter](../../mfc/reference/coledroptarget-class.md#ondragenter)。)|
|[CMFCTabDropTarget::OnDragLeave](#ondragleave)|在用户拖动对象具有焦点的选项卡窗口之外时由框架调用。 (重写[COleDropTarget::OnDragLeave](../../mfc/reference/coledroptarget-class.md#ondragleave)。)|
|[CMFCTabDropTarget::OnDragOver](#ondragover)|用户到具有焦点的选项卡窗口上拖动对象时由框架调用。 (重写[COleDropTarget::OnDragOver](../../mfc/reference/coledroptarget-class.md#ondragover)。)|
|[CMFCTabDropTarget::OnDropEx](#ondropex)|当用户释放鼠标按钮拖动操作结束时由框架调用。 (重写[COleDropTarget::OnDropEx](../../mfc/reference/coledroptarget-class.md#ondropex)。)|
|[CMFCTabDropTarget::Register](#register)|将控件注册为一个可以是 OLE 拖放操作的目标。|

### <a name="remarks"></a>备注

此类提供拖放支持添加到`CMFCBaseTabCtrl`类。 如果你的应用程序使用的初始化 OLE 库[AfxOleInit](ole-initialization.md#afxoleinit)函数，`CMFCBaseTabCtrl`对象将自行注册为拖放操作。

`CMFCTabDropTarget`类活动拖放操作时是光标下的选项卡，从而扩展其基本类。 有关拖放操作的详细信息，请参阅[拖放 (OLE)](../../mfc/drag-and-drop-ole.md)。

## <a name="example"></a>示例

下列示例演示如何构造 `CMFCTabDropTarget` 对象并使用其 `Register` 方法。

[!code-cpp[NVC_MFC_RibbonApp#39](../../mfc/reference/codesnippet/cpp/cmfctabdroptarget-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[COleDropTarget](../../mfc/reference/coledroptarget-class.md)

[CMFCTabDropTarget](../../mfc/reference/cmfctabdroptarget-class.md)

## <a name="requirements"></a>要求

**标头：** afxbasetabctrl.h

##  <a name="ondragenter"></a>  CMFCTabDropTarget::OnDragEnter

用户将对象拖到选项卡窗口时由框架调用。

```
virtual DROPEFFECT OnDragEnter(
    CWnd* pWnd,
    COleDataObject* pDataObject,
    DWORD dwKeyState,
    CPoint point);
```

### <a name="parameters"></a>参数

|||
|-|-|
|参数|描述|
|*pWnd*|[in]未使用。|
|*pDataObject*|[in]指向用户拖动的对象的指针。|
|*dwKeyState*|[in]包含修改键的状态。 这是以下任意数量的组合： MK_CONTROL、 MK_SHIFT、 MK_ALT、 MK_LBUTTON、 MK_MBUTTON 和 MK_RBUTTON。|
|*点*|[in]工作区坐标中的光标位置。|

### <a name="return-value"></a>返回值

如果在指定的位置发生放置操作的效果*点*。 它可以是一个或多项操作：

- DROPEFFECT_NONE

- DROPEFFECT_COPY

- DROPEFFECT_MOVE

- DROPEFFECT_LINK

- DROPEFFECT_SCROLL

### <a name="remarks"></a>备注

如果工具栏框架不是在自定义模式或剪贴板数据格式将不可用，则此方法返回 DROPEFFECT_NONE。 否则，返回的调用结果`CMFCBaseTabCtrl::OnDragEnter`与提供的参数。

有关自定义模式的详细信息，请参阅[CMFCToolBar::IsCustomizeMode](../../mfc/reference/cmfctoolbar-class.md#iscustomizemode)。 有关剪贴板数据格式的详细信息，请参阅[COleDataObject::IsDataAvailable](../../mfc/reference/coledataobject-class.md#isdataavailable)。

##  <a name="ondragleave"></a>  CMFCTabDropTarget::OnDragLeave

在用户拖动对象具有焦点的选项卡窗口之外时由框架调用。

```
virtual void OnDragLeave(CWnd* pWnd);
```

### <a name="parameters"></a>参数

|||
|-|-|
|参数|描述|
|*pWnd*|[in]未使用。|

### <a name="remarks"></a>备注

此方法调用`CMFCBaseTabCtrl::OnDragLeave`方法来执行拖动操作。

##  <a name="ondragover"></a>  CMFCTabDropTarget::OnDragOver

用户到具有焦点的选项卡窗口上拖动对象时由框架调用。

```
virtual DROPEFFECT OnDragOver(
    CWnd* pWnd,
    COleDataObject* pDataObject,
    DWORD dwKeyState,
    CPoint point);
```

### <a name="parameters"></a>参数

|||
|-|-|
|参数|描述|
|*pWnd*|[in]未使用。|
|*pDataObject*|[in]指向用户拖动的对象的指针。|
|*dwKeyState*|[in]包含修改键的状态。 这是以下任意数量的组合： MK_CONTROL、 MK_SHIFT、 MK_ALT、 MK_LBUTTON、 MK_MBUTTON 和 MK_RBUTTON。|
|*点*|[in]在客户端坐标中鼠标指针的位置。|

### <a name="return-value"></a>返回值

如果在指定的位置发生放置操作的效果*点*。 它可以是一个或多项操作：

- DROPEFFECT_NONE

- DROPEFFECT_COPY

- DROPEFFECT_MOVE

- DROPEFFECT_LINK

- DROPEFFECT_SCROLL

### <a name="remarks"></a>备注

此方法将活动拖放操作时是光标下的选项卡。 如果工具栏框架不在自定义模式或剪贴板数据格式将不可用，则返回 DROPEFFECT_NONE。 否则，返回的调用结果`CMFCBaseTabCtrl::OnDragOver`与提供的参数。

有关自定义模式的详细信息，请参阅[CMFCToolBar::IsCustomizeMode](../../mfc/reference/cmfctoolbar-class.md#iscustomizemode)。 有关剪贴板数据格式的详细信息，请参阅[COleDataObject::IsDataAvailable](../../mfc/reference/coledataobject-class.md#isdataavailable)。

##  <a name="ondropex"></a>  CMFCTabDropTarget::OnDropEx

当用户释放鼠标按钮拖动操作结束时由框架调用。

```
virtual DROPEFFECT OnDropEx(
    CWnd* pWnd,
    COleDataObject* pDataObject,
    DROPEFFECT dropEffect,
    DROPEFFECT dropList,
    CPoint point);
```

### <a name="parameters"></a>参数

|||
|-|-|
|参数|描述|
|*pWnd*|[in]未使用。|
|*pDataObject*|[in]指向用户拖动的对象的指针。|
|*dropEffect*|[in]默认删除操作。|
|*下拉列表*|[in]未使用。|
|*点*|[in]在客户端坐标中鼠标指针的位置。|

### <a name="return-value"></a>返回值

生成的放置效果。 它可以是一个或多项操作：

- DROPEFFECT_NONE

- DROPEFFECT_COPY

- DROPEFFECT_MOVE

- DROPEFFECT_LINK

- DROPEFFECT_SCROLL

### <a name="remarks"></a>备注

此方法调用`CMFCBaseTabCtrl::OnDrop`如果工具栏框架是在自定义模式，并且可用的剪贴板数据格式。 如果在调用`CMFCBaseTabCtrl::OnDrop`返回非零值，此方法返回指定的默认放置效果*dropEffect*。 否则，此方法返回 DROPEFFECT_NONE。 有关放置效果的详细信息，请参阅[COleDropTarget::OnDropEx](../../mfc/reference/coledroptarget-class.md#ondropex)。

有关自定义模式的详细信息，请参阅[CMFCToolBar::IsCustomizeMode](../../mfc/reference/cmfctoolbar-class.md#iscustomizemode)。 有关剪贴板数据格式的详细信息，请参阅[COleDataObject::IsDataAvailable](../../mfc/reference/coledataobject-class.md#isdataavailable)。

##  <a name="register"></a>  CMFCTabDropTarget::Register

将控件注册为一个可以是 OLE 拖放操作的目标。

```
BOOL Register(CMFCBaseTabCtrl *pOwner);
```

### <a name="parameters"></a>参数

|||
|-|-|
|参数|描述|
|*pOwner*|[in]要注册为放置目标的选项卡控件。|

### <a name="return-value"></a>返回值

如果注册成功，则非零值否则为 0。

### <a name="remarks"></a>备注

此方法调用[COleDropTarget::Register](../../mfc/reference/coledroptarget-class.md#register)来注册控件的拖放操作。

## <a name="see-also"></a>请参阅

[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[类](../../mfc/reference/mfc-classes.md)<br/>
[拖放 (OLE)](../../mfc/drag-and-drop-ole.md)

