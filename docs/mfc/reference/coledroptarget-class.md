---
title: "COleDropTarget 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
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
dev_langs: C++
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
caps.latest.revision: "23"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: fecdedc84f4fd93cbd9efe5e525c1771c5eb1c7e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
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
|[COleDropTarget::OnDragLeave](#ondragleave)|当光标拖出窗口时调用。|  
|[COleDropTarget::OnDragOver](#ondragover)|重复调用时将光标拖到窗口。|  
|[COleDropTarget::OnDragScroll](#ondragscroll)|调用以确定是否将光标拖到窗口的滚动区域。|  
|[COleDropTarget::OnDrop](#ondrop)|将数据放到窗口中，默认处理程序时调用。|  
|[COleDropTarget::OnDropEx](#ondropex)|将数据放到窗口中，初始处理程序时调用。|  
|[COleDropTarget::Register](#register)|将窗口注册为有效的放置目标。|  
|[COleDropTarget::Revoke](#revoke)|使窗口停止正在有效的放置目标。|  
  
## <a name="remarks"></a>备注  
 创建此类的对象可让一个窗口以通过 OLE 拖放机制接受数据。  
  
 若要接受 drop 命令窗口，你应首先创建的对象`COleDropTarget`类，，然后调用[注册](#register)用一个指针指向所需的函数`CWnd`作为唯一参数的对象。  
  
 有关拖放操作的详细信息使用 OLE，请参阅文章[拖放 (OLE)](../../mfc/drag-and-drop-ole.md)。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 `COleDropTarget`  
  
## <a name="requirements"></a>惠?  
 **标头：** afxole.h  
  
##  <a name="coledroptarget"></a>COleDropTarget::COleDropTarget  
 构造类的对象`COleDropTarget`。  
  
```  
COleDropTarget();
```  
  
### <a name="remarks"></a>备注  
 调用[注册](#register)将此对象与一个窗口相关联。  
  
##  <a name="ondragenter"></a>COleDropTarget::OnDragEnter  
 当光标第一次拖动到窗口时，由框架调用。  
  
```  
virtual DROPEFFECT OnDragEnter(
    CWnd* pWnd,  
    COleDataObject* pDataObject,  
    DWORD dwKeyState,  
    CPoint point);
```  
  
### <a name="parameters"></a>参数  
 `pWnd`  
 指向窗口输入光标。  
  
 `pDataObject`  
 指向包含可以放置的数据的数据对象。  
  
 `dwKeyState`  
 包含修改键的状态。 这是任意数量的以下组合： **MK_CONTROL**， **MK_SHIFT**， **MK_ALT**， **MK_LBUTTON**， **MK_MBUTTON**，和**MK_RBUTTON**。  
  
 `point`  
 包含当前工作区坐标中光标的位置。  
  
### <a name="return-value"></a>返回值  
 如果尝试在指定的位置的放置将产生的效果`point`。 它可以是一个或多个以下：  
  
- `DROPEFFECT_NONE`不允许删除。  
  
- `DROPEFFECT_COPY`将执行复制操作。  
  
- `DROPEFFECT_MOVE`将执行移动操作。  
  
- `DROPEFFECT_LINK`将建立从放置的数据到原始数据的链接。  
  
- `DROPEFFECT_SCROLL`拖动滚动操作即将发生或者问题发生在目标中。  
  
### <a name="remarks"></a>备注  
 重写此函数可允许拖放操作发生在窗口中。 默认实现调用[CView::OnDragEnter](../../mfc/reference/cview-class.md#ondragenter)，只返回`DROPEFFECT_NONE`默认情况下。  
  
 有关详细信息，请参阅[IDropTarget::DragEnter](http://msdn.microsoft.com/library/windows/desktop/ms680106) Windows SDK 中。  
  
##  <a name="ondragleave"></a>COleDropTarget::OnDragLeave  
 当光标离开窗口实际上拖动操作时，由框架调用。  
  
```  
virtual void OnDragLeave(CWnd* pWnd);
```  
  
### <a name="parameters"></a>参数  
 `pWnd`  
 指向窗口光标将脱离。  
  
### <a name="remarks"></a>备注  
 如果在拖动操作离开指定的窗口时，你需要特殊行为，重写此函数。 此函数的默认实现调用[CView::OnDragLeave](../../mfc/reference/cview-class.md#ondragleave)。  
  
 有关详细信息，请参阅[IDropTarget::DragLeave](http://msdn.microsoft.com/library/windows/desktop/ms680110) Windows SDK 中。  
  
##  <a name="ondragover"></a>COleDropTarget::OnDragOver  
 当光标拖到窗口时，由框架调用。  
  
```  
virtual DROPEFFECT OnDragOver(
    CWnd* pWnd,  
    COleDataObject* pDataObject,  
    DWORD dwKeyState,  
    CPoint point);
```  
  
### <a name="parameters"></a>参数  
 `pWnd`  
 指向以光标位于窗口。  
  
 `pDataObject`  
 指向包含要删除的数据的数据对象。  
  
 `dwKeyState`  
 包含修改键的状态。 这是任意数量的以下组合： **MK_CONTROL**， **MK_SHIFT**， **MK_ALT**， **MK_LBUTTON**， **MK_MBUTTON**，和**MK_RBUTTON**。  
  
 `point`  
 包含当前工作区坐标中光标的位置。  
  
### <a name="return-value"></a>返回值  
 如果尝试在指定的位置的放置将产生的效果`point`。 它可以是一个或多个以下：  
  
- `DROPEFFECT_NONE`不允许删除。  
  
- `DROPEFFECT_COPY`将执行复制操作。  
  
- `DROPEFFECT_MOVE`将执行移动操作。  
  
- `DROPEFFECT_LINK`将建立从放置的数据到原始数据的链接。  
  
- `DROPEFFECT_SCROLL`指示，拖动滚动操作即将发生或者问题发生在目标中。  
  
### <a name="remarks"></a>备注  
 此函数应被替代，以允许拖放操作发生在窗口中。 此函数的默认实现调用[CView::OnDragOver](../../mfc/reference/cview-class.md#ondragover)，它将返回`DROPEFFECT_NONE`默认情况下。 因为经常在拖放操作过程中调用此函数，应尽可能多地进行优化。  
  
 有关详细信息，请参阅[IDropTarget::DragOver](http://msdn.microsoft.com/library/windows/desktop/ms680129) Windows SDK 中。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCOleContainer#21](../../mfc/codesnippet/cpp/coledroptarget-class_1.cpp)]  
  
##  <a name="ondragscroll"></a>COleDropTarget::OnDragScroll  
 由框架在调用之前调用[OnDragEnter](#ondragenter)或[OnDragOver](#ondragover)以确定是否`point`位于滚动区域。  
  
```  
virtual DROPEFFECT OnDragScroll(
    CWnd* pWnd,  
    DWORD dwKeyState,  
    CPoint point);
```  
  
### <a name="parameters"></a>参数  
 `pWnd`  
 指向以光标位于当前窗口。  
  
 `dwKeyState`  
 包含修改键的状态。 这是任意数量的以下组合： **MK_CONTROL**， **MK_SHIFT**， **MK_ALT**， **MK_LBUTTON**， **MK_MBUTTON**，和**MK_RBUTTON**。  
  
 `point`  
 包含光标，以像素为单位，相对于屏幕的位置。  
  
### <a name="return-value"></a>返回值  
 如果尝试在指定的位置的放置将产生的效果`point`。 它可以是一个或多个以下：  
  
- `DROPEFFECT_NONE`不允许删除。  
  
- `DROPEFFECT_COPY`将执行复制操作。  
  
- `DROPEFFECT_MOVE`将执行移动操作。  
  
- `DROPEFFECT_LINK`将建立从放置的数据到原始数据的链接。  
  
- `DROPEFFECT_SCROLL`指示，拖动滚动操作即将发生或者问题发生在目标中。  
  
### <a name="remarks"></a>备注  
 如果你想要为此事件提供特殊行为，重写此函数。 此函数的默认实现调用[CView::OnDragScroll](../../mfc/reference/cview-class.md#ondragscroll)，它将返回`DROPEFFECT_NONE`和滚动窗口，当光标拖放到该窗口的边框内的默认滚动区域。  
  
##  <a name="ondrop"></a>COleDropTarget::OnDrop  
 拖放操作发生时由框架调用。  
  
```  
virtual BOOL OnDrop(
    CWnd* pWnd,  
    COleDataObject* pDataObject,  
    DROPEFFECT dropEffect,  
    CPoint point);
```  
  
### <a name="parameters"></a>参数  
 `pWnd`  
 指向以光标位于当前窗口。  
  
 `pDataObject`  
 指向包含要删除的数据的数据对象。  
  
 `dropEffect`  
 用户选择放操作效果。 它可以是一个或多个以下：  
  
- `DROPEFFECT_COPY`将执行复制操作。  
  
- `DROPEFFECT_MOVE`将执行移动操作。  
  
- `DROPEFFECT_LINK`将建立从放置的数据到原始数据的链接。  
  
 `point`  
 包含光标，以像素为单位，相对于屏幕的位置。  
  
### <a name="return-value"></a>返回值  
 Drop 是成功; 如果非零否则为 0。  
  
### <a name="remarks"></a>备注  
 框架的第一个调用[OnDropEx](#ondropex)。 如果`OnDropEx`函数不处理拖放、 框架然后调用此成员函数， `OnDrop`。 通常情况下，应用程序的重写[OnDropEx](../../mfc/reference/cview-class.md#ondropex)在视图类来处理右侧的鼠标按钮拖放。 通常情况下，视图类[OnDrop](../../mfc/reference/cview-class.md#ondrop)用于处理简单的拖放。  
  
 默认实现`COleDropTarget::OnDrop`调用[CView::OnDrop](../../mfc/reference/cview-class.md#ondrop)，只返回**FALSE**默认情况下。  
  
 有关详细信息，请参阅[IDropTarget::Drop](http://msdn.microsoft.com/library/windows/desktop/ms687242) Windows SDK 中。  
  
##  <a name="ondropex"></a>COleDropTarget::OnDropEx  
 拖放操作发生时由框架调用。  
  
```  
virtual DROPEFFECT OnDropEx(
    CWnd* pWnd,  
    COleDataObject* pDataObject,  
    DROPEFFECT dropDefault,  
    DROPEFFECT dropList,  
    CPoint point);
```  
  
### <a name="parameters"></a>参数  
 `pWnd`  
 指向以光标位于当前窗口。  
  
 `pDataObject`  
 指向包含要删除的数据的数据对象。  
  
 `dropDefault`  
 用户选择基于当前的关键状态的默认拖放操作效果。 它可以是`DROPEFFECT_NONE`。 在备注部分中讨论了放置效果。  
  
 `dropList`  
 放置源支持拖放效果的列表。 可以使用按位 OR 组合放置效果值 ( **&#124;**) 操作。 在备注部分中讨论了放置效果。  
  
 `point`  
 包含光标，以像素为单位，相对于屏幕的位置。  
  
### <a name="return-value"></a>返回值  
 从指定位置处删除尝试导致的放置效果`point`。 在备注部分中讨论了放置效果。  
  
### <a name="remarks"></a>备注  
 首先，框架会调用此函数。 如果它无法处理下拉菜单，然后调用 framework [OnDrop](#ondrop)。 通常情况下，您将重写[OnDropEx](../../mfc/reference/cview-class.md#ondropex)在视图类，以支持右侧的鼠标按钮拖放。 通常情况下，视图类[OnDrop](../../mfc/reference/cview-class.md#ondrop)用于处理对简单的拖放支持这种情况。  
  
 默认实现`COleDropTarget::OnDropEx`调用[CView::OnDropEx](../../mfc/reference/cview-class.md#ondropex)。 默认情况下， [CView::OnDropEx](../../mfc/reference/cview-class.md#ondropex)只是返回一个虚拟值，以指示[OnDrop](#ondrop)应调用成员函数。  
  
 放置效果描述与拖放操作相关联的操作。 请参阅以下放置效果的列表：  
  
- `DROPEFFECT_NONE`不允许删除。  
  
- `DROPEFFECT_COPY`将执行复制操作。  
  
- `DROPEFFECT_MOVE`将执行移动操作。  
  
- `DROPEFFECT_LINK`将建立从放置的数据到原始数据的链接。  
  
- `DROPEFFECT_SCROLL`指示，拖动滚动操作即将发生或者问题发生在目标中。  
  
 有关详细信息，请参阅[IDropTarget::Drop](http://msdn.microsoft.com/library/windows/desktop/ms687242) Windows SDK 中。  
  
##  <a name="register"></a>COleDropTarget::Register  
 调用此函数可注册 OLE Dll 作为有效的放置目标的你的窗口。  
  
```  
BOOL Register(CWnd* pWnd);
```  
  
### <a name="parameters"></a>参数  
 `pWnd`  
 指向要注册为放置目标的窗口。  
  
### <a name="return-value"></a>返回值  
 如果注册成功; 则为非 0否则为 0。  
  
### <a name="remarks"></a>备注  
 必须为拖放操作，接受调用此函数。  
  
 有关详细信息，请参阅[RegisterDragDrop](http://msdn.microsoft.com/library/windows/desktop/ms678405) Windows SDK 中。  
  
##  <a name="revoke"></a>COleDropTarget::Revoke  
 在销毁已注册为放置目标通过调用任何窗口之前调用此函数[注册](#register)从放置目标的列表中删除。  
  
```  
virtual void Revoke();
```  
  
### <a name="remarks"></a>备注  
 从自动调用此函数[OnDestroy](../../mfc/reference/cwnd-class.md#ondestroy)处理程序已注册，因此它通常是不显式调用此函数所需的窗口。  
  
 有关详细信息，请参阅[RevokeDragDrop](http://msdn.microsoft.com/library/windows/desktop/ms692643) Windows SDK 中。  
  
## <a name="see-also"></a>请参阅  
 [MFC 示例 HIERSVR](../../visual-cpp-samples.md)   
 [MFC 示例 OCLIENT](../../visual-cpp-samples.md)   
 [CCmdTarget 类](../../mfc/reference/ccmdtarget-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [COleDropSource 类](../../mfc/reference/coledropsource-class.md)
