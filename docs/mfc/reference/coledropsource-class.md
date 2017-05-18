---
title: "COleDropSource 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
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
- drag operations
- drop target, dragging data to
- COleDropSource class
- drag and drop, drop source
ms.assetid: d3eecc5f-a70b-4a01-b705-7d2c098ebe17
caps.latest.revision: 24
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: f3d0e5b7184cf305459173065b8e1cc07e032aef
ms.contentlocale: zh-cn
ms.lasthandoff: 02/24/2017

---
# <a name="coledropsource-class"></a>COleDropSource 类
允许将数据拖动到放置目标。  
  
## <a name="syntax"></a>语法  
  
```  
class COleDropSource : public CCmdTarget  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|说明|  
|----------|-----------------|  
|[COleDropSource::COleDropSource](#coledropsource)|构造 `COleDropSource` 对象。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[COleDropSource::GiveFeedback](#givefeedback)|在拖放操作过程中更改光标。|  
|[COleDropSource::OnBeginDrag](#onbegindrag)|在拖放操作过程中处理鼠标捕获。|  
|[COleDropSource::QueryContinueDrag](#querycontinuedrag)|检查以确定拖动是否也应继续。|  
  
## <a name="remarks"></a>备注  
 [COleDropTarget](../../mfc/reference/coledroptarget-class.md)类处理拖放操作的接收部分。 `COleDropSource`对象负责确定在拖动操作开始时，在拖动操作过程中提供的反馈以及确定结束拖放操作时。  
  
 若要使用`COleDropSource`对象，只需调用构造函数。 这简化了过程确定哪些事件，如鼠标单击开始拖动操作使用[COleDataSource::DoDragDrop](../../mfc/reference/coledatasource-class.md#dodragdrop)， [COleClientItem::DoDragDrop](../../mfc/reference/coleclientitem-class.md#dodragdrop)，或[COleServerItem::DoDragDrop](../../mfc/reference/coleserveritem-class.md#dodragdrop)函数。 这些函数将创建`COleDropSource`为您的对象。 你可能想要修改的默认行为`COleDropSource`可重写函数。 由框架，将在适当的时候调用这些成员函数。  
  
 拖放操作的详细信息使用 OLE，请参阅文章[拖放 (OLE)](../../mfc/drag-and-drop-ole.md)。  
  
 有关详细信息，请参阅[IDropSource](http://msdn.microsoft.com/library/windows/desktop/ms690071)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 `COleDropSource`  
  
## <a name="requirements"></a>要求  
 **标头︰** afxole.h  
  
##  <a name="coledropsource"></a>COleDropSource::COleDropSource  
 构造 `COleDropSource` 对象。  
  
```  
COleDropSource();
```  
  
##  <a name="givefeedback"></a>COleDropSource::GiveFeedback  
 由框架调用之后调用[COleDropTarget::OnDragOver](../../mfc/reference/coledroptarget-class.md#ondragover)或[COleDropTarget::DragEnter](../../mfc/reference/coledroptarget-class.md#ondragenter)。  
  
```  
virtual SCODE GiveFeedback(DROPEFFECT dropEffect);
```  
  
### <a name="parameters"></a>参数  
 `dropEffect`  
 如果与所选数据这一时刻发生放置，你想要向用户显示的效果，通常表示什么会发生。 通常情况下，这是到最新的调用所返回的值[CView::OnDragEnter](../../mfc/reference/cview-class.md#ondragenter)或[CView::OnDragOver](../../mfc/reference/cview-class.md#ondragover)。 它可以是一个或多项操作︰  
  
- `DROPEFFECT_NONE`将不允许放置。  
  
- `DROPEFFECT_COPY`将执行复制操作。  
  
- `DROPEFFECT_MOVE`将执行移动操作。  
  
- `DROPEFFECT_LINK`将建立到原始数据放置的数据的链接。  
  
- `DROPEFFECT_SCROLL`拖动滚动操作将要发生或者问题发生在目标中。  
  
### <a name="return-value"></a>返回值  
 返回**DRAGDROP_S_USEDEFAULTCURSORS**拖动过程中，如果**NOERROR**如果不是。  
  
### <a name="remarks"></a>备注  
 重写此函数向有关如果放置这个时候发生，会发生什么情况的用户提供反馈。 默认实现使用的 OLE 默认光标。 拖放操作的详细信息使用 OLE，请参阅文章[拖放 (OLE)](../../mfc/drag-and-drop-ole.md)。  
  
 有关详细信息，请参阅[IDropSource::GiveFeedback](http://msdn.microsoft.com/library/windows/desktop/ms693723)， [IDropTarget::DragOver](http://msdn.microsoft.com/library/windows/desktop/ms680129)，和[IDropTarget::DragEnter](http://msdn.microsoft.com/library/windows/desktop/ms680106)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="onbegindrag"></a>COleDropSource::OnBeginDrag  
 由框架在事件发生时无法开始拖动操作，例如，按下鼠标左键。  
  
```  
virtual BOOL OnBeginDrag(CWnd* pWnd);
```  
  
### <a name="parameters"></a>参数  
 `pWnd`  
 指向以包含所选的数据的窗口。  
  
### <a name="return-value"></a>返回值  
 如果拖动允许，否则为 0，非零值。  
  
### <a name="remarks"></a>备注  
 如果您想要修改拖动进程启动的方式，重写此函数。 默认实现捕获到鼠标，并保留在拖动模式，直到用户单击鼠标左键或右键按钮，或点击 esc 键，此时会释放鼠标。  
  
##  <a name="querycontinuedrag"></a>COleDropSource::QueryContinueDrag  
 拖动开始后，此函数是重复调用，由框架直到取消或完成拖动操作。  
  
```  
virtual SCODE QueryContinueDrag(
    BOOL bEscapePressed, 
    DWORD dwKeyState);
```  
  
### <a name="parameters"></a>参数  
 *bEscapePressed*  
 指出是否自上次调用以来按 ESC 键`COleDropSource::QueryContinueDrag`。  
  
 `dwKeyState`  
 包含在键盘上的修改键的状态。 这是以下任意数量的组合︰ **MK_CONTROL**， **MK_SHIFT**， **MK_ALT**， **MK_LBUTTON**， **MK_MBUTTON**，和**MK_RBUTTON**。  
  
### <a name="return-value"></a>返回值  
 **DRAGDROP_S_CANCEL**如果按下 ESC 键或右键，或者拖动启动之前，将引发左侧的按钮。 **DRAGDROP_S_DROP**是否应进行拖放操作。 否则为`S_OK`。  
  
### <a name="remarks"></a>备注  
 重写此函数将取消您想要更改哪些拖动的点或 drop 时发生。  
  
 默认实现将启动拖放或取消拖动，如下所示。 按下 ESC 键或鼠标按钮时，它会取消拖动操作。 鼠标左键拖动已开始后引发时，它启动拖放操作。 否则，它将返回`S_OK`并执行任何进一步的操作。  
  
 因为频繁地调用此函数时，应尽可能多地进行优化。  
  
## <a name="see-also"></a>另请参阅  
 [MFC 示例 HIERSVR](../../visual-cpp-samples.md)   
 [MFC 示例 OCLIENT](../../visual-cpp-samples.md)   
 [CCmdTarget 类](../../mfc/reference/ccmdtarget-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)




