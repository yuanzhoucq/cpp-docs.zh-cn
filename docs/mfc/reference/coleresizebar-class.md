---
title: "COleResizeBar 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- COleResizeBar
- AFXOLE/COleResizeBar
- AFXOLE/COleResizeBar::COleResizeBar
- AFXOLE/COleResizeBar::Create
dev_langs: C++
helpviewer_keywords:
- COleResizeBar [MFC], COleResizeBar
- COleResizeBar [MFC], Create
ms.assetid: 56a708d9-28c5-4eb0-9404-77b688d91c63
caps.latest.revision: "23"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 0cc0b9f85392a69191ee3c948985c61bd2d1f494
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="coleresizebar-class"></a>COleResizeBar 类
支持调整现有 OLE 项的控件条类型。  
  
## <a name="syntax"></a>语法  
  
```  
class COleResizeBar : public CControlBar  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[COleResizeBar::COleResizeBar](#coleresizebar)|构造 `COleResizeBar` 对象。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[COleResizeBar::Create](#create)|创建和初始化 Windows 子窗口，并将关联到`COleResizeBar`对象。|  
  
## <a name="remarks"></a>备注  
 `COleResizeBar`对象显示为[CRectTracker](../../mfc/reference/crecttracker-class.md)具有阴影边框和外部重设大小句柄。  
  
 `COleResizeBar`对象是派生自的框架窗口对象的通常嵌入的成员[COleIPFrameWnd](../../mfc/reference/coleipframewnd-class.md)类。  
  
 有关详细信息，请参阅文章[激活](../../mfc/activation-cpp.md)。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CControlBar](../../mfc/reference/ccontrolbar-class.md)  
  
 `COleResizeBar`  
  
## <a name="requirements"></a>惠?  
 **标头：** afxole.h  
  
##  <a name="coleresizebar"></a>COleResizeBar::COleResizeBar  
 构造 `COleResizeBar` 对象。  
  
```  
COleResizeBar();
```  
  
### <a name="remarks"></a>备注  
 调用**创建**创建大小调整条对象。  
  
##  <a name="create"></a>COleResizeBar::Create  
 创建子窗口，并将其与关联`COleResizeBar`对象。  
  
```  
virtual BOOL Create(
    CWnd* pParentWnd,  
    DWORD dwStyle = WS_CHILD | WS_VISIBLE,  
    UINT nID = AFX_IDW_RESIZE_BAR);
```  
  
### <a name="parameters"></a>参数  
 `pParentWnd`  
 向父窗口的大小调整栏的指针。  
  
 `dwStyle`  
 指定[窗口样式](../../mfc/reference/styles-used-by-mfc.md#window-styles)属性。  
  
 `nID`  
 调整大小条子窗口 id。  
  
### <a name="return-value"></a>返回值  
 如果已创建的大小调整栏; 则为非 0否则为 0。  
  
## <a name="see-also"></a>请参阅  
 [MFC 示例 SUPERPAD](../../visual-cpp-samples.md)   
 [CControlBar 类](../../mfc/reference/ccontrolbar-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [COleServerDoc 类](../../mfc/reference/coleserverdoc-class.md)
