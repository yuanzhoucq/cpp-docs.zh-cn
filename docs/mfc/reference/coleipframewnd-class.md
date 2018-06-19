---
title: COleIPFrameWnd 类 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- COleIPFrameWnd
- AFXOLE/COleIPFrameWnd
- AFXOLE/COleIPFrameWnd::COleIPFrameWnd
- AFXOLE/COleIPFrameWnd::OnCreateControlBars
- AFXOLE/COleIPFrameWnd::RepositionFrame
dev_langs:
- C++
helpviewer_keywords:
- COleIPFrameWnd [MFC], COleIPFrameWnd
- COleIPFrameWnd [MFC], OnCreateControlBars
- COleIPFrameWnd [MFC], RepositionFrame
ms.assetid: 24abb2cb-826c-4dda-a287-d8a8900a5763
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 466948653a5464a940a027e473e79c00dbf9a6ab
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33370375"
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
|[COleIPFrameWnd::OnCreateControlBars](#oncreatecontrolbars)|当以进行就地编辑在激活一项时，由框架调用。|  
|[COleIPFrameWnd::RepositionFrame](#repositionframe)|由框架调用以重新定位的就地编辑窗口。|  
  
## <a name="remarks"></a>备注  
 此类创建和位置控件条容器应用程序的文档窗口中。 它还可以通过嵌入生成的通知[COleResizeBar](../../mfc/reference/coleresizebar-class.md)对象时用户的就地编辑窗口大小调整。  
  
 有关详细信息使用`COleIPFrameWnd`，请参阅文章[激活](../../mfc/activation-cpp.md)。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CFrameWnd](../../mfc/reference/cframewnd-class.md)  
  
 `COleIPFrameWnd`  
  
## <a name="requirements"></a>要求  
 **标头：** afxole.h  
  
##  <a name="coleipframewnd"></a>  COleIPFrameWnd::COleIPFrameWnd  
 构造`COleIPFrameWnd`对象并初始化其现有状态信息，它存储在类型的结构**OLEINPLACEFRAMEINFO**。  
  
```  
COleIPFrameWnd();
```  
  
### <a name="remarks"></a>备注  
 有关详细信息，请参阅[OLEINPLACEFRAMEINFO](http://msdn.microsoft.com/library/windows/desktop/ms693737) Windows SDK 中。  
  
##  <a name="oncreatecontrolbars"></a>  COleIPFrameWnd::OnCreateControlBars  
 框架调用`OnCreateControlBars`函数时进行就地编辑在激活一项。  
  
```  
virtual BOOL OnCreateControlBars(
    CWnd* pWndFrame,  
    CWnd* pWndDoc);

 
virtual BOOL OnCreateControlBars(
    CFrameWnd* pWndFrame,  
    CFrameWnd* pWndDoc);
```  
  
### <a name="parameters"></a>参数  
 *pWndFrame*  
 到容器应用程序的框架窗口的指针。  
  
 *pWndDoc*  
 指向容器的文档级窗口的指针。 可以是**NULL**如果容器是 SDI 应用程序。  
  
### <a name="return-value"></a>返回值  
 成功; 则为非零否则为为 0。  
  
### <a name="remarks"></a>备注  
 默认实现不执行任何操作。 重写此函数以执行任何所需控件条创建时的特殊处理。  
  
##  <a name="repositionframe"></a>  COleIPFrameWnd::RepositionFrame  
 框架调用`RepositionFrame`成员函数来设置控件条布局和重新定位的就地编辑窗口，因此它是可见。  
  
```  
virtual void RepositionFrame(
    LPCRECT lpPosRect,  
    LPCRECT lpClipRect);
```  
  
### <a name="parameters"></a>参数  
 `lpPosRect`  
 指向`RECT`结构或`CRect`对象，其中包含的就地框架窗口的当前位置坐标，以像素为单位，相对于工作区。  
  
 `lpClipRect`  
 指向`RECT`结构或`CRect`对象，其中包含的就地框架窗口的当前剪辑矩形坐标，以像素为单位，相对于工作区。  
  
### <a name="remarks"></a>备注  
 在容器窗口中的控件条布局不同于执行的非 OLE 框架窗口。 非 OLE 框架窗口计算的控件条和从给定的框架窗口大小，如下所示调用其他对象的位置[CFrameWnd::RecalcLayout](../../mfc/reference/cframewnd-class.md#recalclayout)。 客户端区域是其余后减去控件条和其他对象的空间。 A`COleIPFrameWnd`窗口，另一方面，确定工具栏位置根据给定的工作区。 换而言之， `CFrameWnd::RecalcLayout` "发件人的外部，"起作用，而`COleIPFrameWnd::RepositionFrame`有效"发件人括号外的顺序。"  
  
## <a name="see-also"></a>请参阅  
 [MFC 示例 HIERSVR](../../visual-cpp-samples.md)   
 [CFrameWnd 类](../../mfc/reference/cframewnd-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CFrameWnd 类](../../mfc/reference/cframewnd-class.md)
