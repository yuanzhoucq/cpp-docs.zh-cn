---
title: "COleIPFrameWnd 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
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
- COleIPFrameWnd class
- OLE, editing
- OLE, in-place activation
- in-place editing
ms.assetid: 24abb2cb-826c-4dda-a287-d8a8900a5763
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
translationtype: Machine Translation
ms.sourcegitcommit: 040985df34f2613b4e4fae29498721aef15d50cb
ms.openlocfilehash: 85ce028bb5d72c06a0e228abba1bd08a7f6526cb
ms.lasthandoff: 02/24/2017

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
  
|名称|说明|  
|----------|-----------------|  
|[COleIPFrameWnd::OnCreateControlBars](#oncreatecontrolbars)|当激活某个项时就地编辑时由框架调用。|  
|[COleIPFrameWnd::RepositionFrame](#repositionframe)|由框架后，若要重新定位在就地编辑窗口调用。|  
  
## <a name="remarks"></a>备注  
 此类创建和位置控制容器应用程序的文档窗口中的条形图。 它还可以通过嵌入生成的通知[COleResizeBar](../../mfc/reference/coleresizebar-class.md)对象时在用户调整大小的就地编辑窗口。  
  
 有关详细信息使用`COleIPFrameWnd`，请参阅文章[激活](../../mfc/activation-cpp.md)。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CFrameWnd](../../mfc/reference/cframewnd-class.md)  
  
 `COleIPFrameWnd`  
  
## <a name="requirements"></a>要求  
 **标头︰** afxole.h  
  
##  <a name="coleipframewnd"></a>COleIPFrameWnd::COleIPFrameWnd  
 构造`COleIPFrameWnd`对象，并初始化其适当地状态信息，它存储在类型的结构**OLEINPLACEFRAMEINFO**。  
  
```  
COleIPFrameWnd();
```  
  
### <a name="remarks"></a>备注  
 有关详细信息，请参阅[OLEINPLACEFRAMEINFO](http://msdn.microsoft.com/library/windows/desktop/ms693737)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="oncreatecontrolbars"></a>COleIPFrameWnd::OnCreateControlBars  
 框架将调用`OnCreateControlBars`激活某个项时就地编辑时的功能。  
  
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
 如果成功; Nonzero否则为 0。  
  
### <a name="remarks"></a>备注  
 默认实现不执行任何操作。 重写此函数以执行任何所需控件条在创建时的特殊处理。  
  
##  <a name="repositionframe"></a>COleIPFrameWnd::RepositionFrame  
 框架将调用`RepositionFrame`来布置控件条的大小和位置在就地编辑窗口，因此它是可见的成员函数。  
  
```  
virtual void RepositionFrame(
    LPCRECT lpPosRect,  
    LPCRECT lpClipRect);
```  
  
### <a name="parameters"></a>参数  
 `lpPosRect`  
 指向`RECT`结构或`CRect`对象，其中包含中就地框架窗口的当前位置坐标，以像素为单位，相对于工作区。  
  
 `lpClipRect`  
 指向`RECT`结构或`CRect`对象，其中包含中就地框架窗口的当前剪辑矩形坐标，以像素为单位，相对于工作区。  
  
### <a name="remarks"></a>备注  
 在容器窗口中的控件条的布局不同于执行的非 OLE 框架窗口。 非 OLE 框架窗口计算的位置控件条和其他对象从给定的框架窗口大小，如下所示调用[CFrameWnd::RecalcLayout](../../mfc/reference/cframewnd-class.md#recalclayout)。 工作区是保留其他哪些东西后的空间容纳控件条和其他对象中减去该值。 一个`COleIPFrameWnd`窗口，相反，确定工具栏位置根据给定的工作区。 换而言之， `CFrameWnd::RecalcLayout` "发件人在中，外部"起作用，而`COleIPFrameWnd::RepositionFrame`工作原理"从内到外。"  
  
## <a name="see-also"></a>另请参阅  
 [MFC 示例 HIERSVR](../../visual-cpp-samples.md)   
 [CFrameWnd 类](../../mfc/reference/cframewnd-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CFrameWnd 类](../../mfc/reference/cframewnd-class.md)

