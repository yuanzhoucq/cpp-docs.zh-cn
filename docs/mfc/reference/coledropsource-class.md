---
title: COleDropSource 类 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- COleDropSource
- AFXOLE/COleDropSource
- AFXOLE/COleDropSource::COleDropSource
- AFXOLE/COleDropSource::GiveFeedback
- AFXOLE/COleDropSource::OnBeginDrag
- AFXOLE/COleDropSource::QueryContinueDrag
dev_langs:
- C++
helpviewer_keywords:
- COleDropSource [MFC], COleDropSource
- COleDropSource [MFC], GiveFeedback
- COleDropSource [MFC], OnBeginDrag
- COleDropSource [MFC], QueryContinueDrag
ms.assetid: d3eecc5f-a70b-4a01-b705-7d2c098ebe17
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e510811fcaac81aa54699250ef37f48ffe1f40e2
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="coledropsource-class"></a>COleDropSource 类
允许数据拖动到放置目标。  
  
## <a name="syntax"></a>语法  
  
```  
class COleDropSource : public CCmdTarget  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[COleDropSource::COleDropSource](#coledropsource)|构造 `COleDropSource` 对象。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[COleDropSource::GiveFeedback](#givefeedback)|拖放操作期间更改光标。|  
|[COleDropSource::OnBeginDrag](#onbegindrag)|拖放操作期间处理鼠标捕获。|  
|[COleDropSource::QueryContinueDrag](#querycontinuedrag)|检查以确定是否拖动应继续。|  
  
## <a name="remarks"></a>备注  
 [COleDropTarget](../../mfc/reference/coledroptarget-class.md)类处理拖放操作的接收部分。 `COleDropSource`对象负责确定拖动操作开始时，在拖动操作期间，提供反馈和确定拖动操作结束时。  
  
 若要使用`COleDropSource`对象，只需调用构造函数。 这可简化确定哪些事件，例如单击鼠标，开始拖动操作使用的过程[coledatasource:: Dodragdrop](../../mfc/reference/coledatasource-class.md#dodragdrop)， [COleClientItem::DoDragDrop](../../mfc/reference/coleclientitem-class.md#dodragdrop)，或[COleServerItem::DoDragDrop](../../mfc/reference/coleserveritem-class.md#dodragdrop)函数。 这些函数将创建`COleDropSource`为你的对象。 你可能想要修改的默认行为`COleDropSource`可重写函数。 这些成员函数将由框架调用在合适的时间。  
  
 有关拖放操作的详细信息使用 OLE，请参阅文章[拖放 (OLE)](../../mfc/drag-and-drop-ole.md)。  
  
 有关详细信息，请参阅[IDropSource](http://msdn.microsoft.com/library/windows/desktop/ms690071) Windows SDK 中。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 `COleDropSource`  
  
## <a name="requirements"></a>要求  
 **标头：** afxole.h  
  
##  <a name="coledropsource"></a>  COleDropSource::COleDropSource  
 构造 `COleDropSource` 对象。  
  
```  
COleDropSource();
```  
  
##  <a name="givefeedback"></a>  COleDropSource::GiveFeedback  
 在调用由框架调用[COleDropTarget::OnDragOver](../../mfc/reference/coledroptarget-class.md#ondragover)或[COleDropTarget::DragEnter](../../mfc/reference/coledroptarget-class.md#ondragenter)。  
  
```  
virtual SCODE GiveFeedback(DROPEFFECT dropEffect);
```  
  
### <a name="parameters"></a>参数  
 `dropEffect`  
 你想要向用户显示的效果，通常指示什么会删除与所选数据这一时刻发生。 通常，这是到最新的调用所返回的值[CView::OnDragEnter](../../mfc/reference/cview-class.md#ondragenter)或[CView::OnDragOver](../../mfc/reference/cview-class.md#ondragover)。 它可以是一个或多个以下：  
  
- `DROPEFFECT_NONE` 不允许删除。  
  
- `DROPEFFECT_COPY` 将执行复制操作。  
  
- `DROPEFFECT_MOVE` 将执行移动操作。  
  
- `DROPEFFECT_LINK` 将建立从放置的数据到原始数据的链接。  
  
- `DROPEFFECT_SCROLL` 拖动滚动操作即将发生或者问题发生在目标中。  
  
### <a name="return-value"></a>返回值  
 返回**DRAGDROP_S_USEDEFAULTCURSORS**如果拖动正在进行， **NOERROR**如果它不是。  
  
### <a name="remarks"></a>备注  
 重写此函数可向用户如果放发生在此时，会发生什么情况提供反馈。 默认实现使用的 OLE 默认光标。 有关拖放操作的详细信息使用 OLE，请参阅文章[拖放 (OLE)](../../mfc/drag-and-drop-ole.md)。  
  
 有关详细信息，请参阅[IDropSource::GiveFeedback](http://msdn.microsoft.com/library/windows/desktop/ms693723)， [IDropTarget::DragOver](http://msdn.microsoft.com/library/windows/desktop/ms680129)，和[IDropTarget::DragEnter](http://msdn.microsoft.com/library/windows/desktop/ms680106) Windows SDK 中。  
  
##  <a name="onbegindrag"></a>  COleDropSource::OnBeginDrag  
 由框架事件发生时无法开始拖动操作，如按鼠标左键。  
  
```  
virtual BOOL OnBeginDrag(CWnd* pWnd);
```  
  
### <a name="parameters"></a>参数  
 `pWnd`  
 指向以包含所选的数据的窗口。  
  
### <a name="return-value"></a>返回值  
 如果拖动允许，否则为 0，则为非 0。  
  
### <a name="remarks"></a>备注  
 如果你想要修改拖动进程启动的方式，重写此函数。 默认实现捕获鼠标，并保留在拖动模式，直到用户单击左或向右鼠标按钮或点击的 ESC，此时它会释放鼠标。  
  
##  <a name="querycontinuedrag"></a>  COleDropSource::QueryContinueDrag  
 拖动开始后，此函数是重复由框架调用直到取消或完成拖动操作。  
  
```  
virtual SCODE QueryContinueDrag(
    BOOL bEscapePressed, 
    DWORD dwKeyState);
```  
  
### <a name="parameters"></a>参数  
 *bEscapePressed*  
 状态在最后一个调用是否按 ESC 键`COleDropSource::QueryContinueDrag`。  
  
 `dwKeyState`  
 包含修改键键盘上的状态。 这是任意数量的以下组合： **MK_CONTROL**， **MK_SHIFT**， **MK_ALT**， **MK_LBUTTON**， **MK_MBUTTON**，和**MK_RBUTTON**。  
  
### <a name="return-value"></a>返回值  
 **DRAGDROP_S_CANCEL**如果按下 ESC 键或右侧的按钮，或左键拖动启动之前，将引发。 **DRAGDROP_S_DROP**是否应进行拖放操作。 否则为`S_OK`。  
  
### <a name="remarks"></a>备注  
 重写此函数取消你想要更改在哪些拖动的点或 drop 时发生。  
  
 默认实现启动拖放或，如下所示取消拖动。 在按下 ESC 键或鼠标右键按钮时，它会取消拖动操作。 拖动开始后引发鼠标左键时，它将启动拖放操作。 否则，它将返回`S_OK`并执行任何进一步的操作。  
  
 因为此函数被频繁调用，应尽可能多地进行优化。  
  
## <a name="see-also"></a>请参阅  
 [MFC 示例 HIERSVR](../../visual-cpp-samples.md)   
 [MFC 示例 OCLIENT](../../visual-cpp-samples.md)   
 [CCmdTarget 类](../../mfc/reference/ccmdtarget-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)



