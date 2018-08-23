---
title: COleResizeBar 类 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- COleResizeBar
- AFXOLE/COleResizeBar
- AFXOLE/COleResizeBar::COleResizeBar
- AFXOLE/COleResizeBar::Create
dev_langs:
- C++
helpviewer_keywords:
- COleResizeBar [MFC], COleResizeBar
- COleResizeBar [MFC], Create
ms.assetid: 56a708d9-28c5-4eb0-9404-77b688d91c63
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3706521108d848535742bf2314142fedf46f1746
ms.sourcegitcommit: 26fff80635bd1d51bc51899203fddfea8b29b530
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/05/2018
ms.locfileid: "37852707"
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
|[COleResizeBar::Create](#create)|创建和初始化 Windows 子窗口并将关联到`COleResizeBar`对象。|  
  
## <a name="remarks"></a>备注  
 `COleResizeBar` 对象显示为[CRectTracker](../../mfc/reference/crecttracker-class.md)具有阴影边框和外部重设大小句柄。  
  
 `COleResizeBar` 对象是通常嵌入的成员的框架窗口对象派生自[COleIPFrameWnd](../../mfc/reference/coleipframewnd-class.md)类。  
  
 有关详细信息，请参阅文章[激活](../../mfc/activation-cpp.md)。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CControlBar](../../mfc/reference/ccontrolbar-class.md)  
  
 `COleResizeBar`  
  
## <a name="requirements"></a>要求  
 **标头：** afxole.h  
  
##  <a name="coleresizebar"></a>  COleResizeBar::COleResizeBar  
 构造 `COleResizeBar` 对象。  
  
```  
COleResizeBar();
```  
  
### <a name="remarks"></a>备注  
 调用`Create`创建大小调整条对象。  
  
##  <a name="create"></a>  COleResizeBar::Create  
 创建子窗口，并将其与`COleResizeBar`对象。  
  
```  
virtual BOOL Create(
    CWnd* pParentWnd,  
    DWORD dwStyle = WS_CHILD | WS_VISIBLE,  
    UINT nID = AFX_IDW_RESIZE_BAR);
```  
  
### <a name="parameters"></a>参数  
 *pParentWnd*  
 向父窗口大小调整条的指针。  
  
 *dwStyle*  
 指定[窗口样式](../../mfc/reference/styles-used-by-mfc.md#window-styles)属性。  
  
 *nID*  
 大小调整条的子窗口 id。  
  
### <a name="return-value"></a>返回值  
 如果创建的大小调整条; 非零值否则为 0。  
  
## <a name="see-also"></a>请参阅  
 [MFC 示例 SUPERPAD](../../visual-cpp-samples.md)   
 [CControlBar 类](../../mfc/reference/ccontrolbar-class.md)   
 [层次结构图表](../../mfc/hierarchy-chart.md)   
 [COleServerDoc 类](../../mfc/reference/coleserverdoc-class.md)
