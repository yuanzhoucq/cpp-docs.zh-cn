---
title: "COleResizeBar 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- COleResizeBar
- AFXOLE/COleResizeBar
- AFXOLE/COleResizeBar::COleResizeBar
- AFXOLE/COleResizeBar::Create
dev_langs:
- C++
helpviewer_keywords:
- OLE items, resizing
- in-place items
- in-place items, resizing
- resizing in-place OLE items
- control bars, resizing
- COleResizeBar class
ms.assetid: 56a708d9-28c5-4eb0-9404-77b688d91c63
caps.latest.revision: 23
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
ms.sourcegitcommit: 040985df34f2613b4e4fae29498721aef15d50cb
ms.openlocfilehash: 99ba53c771d018b8c69c5951703b9d6f7b4afe9b
ms.contentlocale: zh-cn
ms.lasthandoff: 02/24/2017

---
# <a name="coleresizebar-class"></a>COleResizeBar 类
支持调整现有 OLE 项的控件条类型。  
  
## <a name="syntax"></a>语法  
  
```  
class COleResizeBar : public CControlBar  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|说明|  
|----------|-----------------|  
|[COleResizeBar::COleResizeBar](#coleresizebar)|构造 `COleResizeBar` 对象。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|说明|  
|----------|-----------------|  
|[COleResizeBar::Create](#create)|创建和初始化 Windows 子窗口，并将关联到`COleResizeBar`对象。|  
  
## <a name="remarks"></a>备注  
 `COleResizeBar`对象显示为[CRectTracker](../../mfc/reference/crecttracker-class.md)具有阴影边框和外部调整大小图柄。  
  
 `COleResizeBar`对象是从派生的框架窗口对象的通常嵌入的成员[COleIPFrameWnd](../../mfc/reference/coleipframewnd-class.md)类。  
  
 有关详细信息，请参阅文章[激活](../../mfc/activation-cpp.md)。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CControlBar](../../mfc/reference/ccontrolbar-class.md)  
  
 `COleResizeBar`  
  
## <a name="requirements"></a>要求  
 **标头︰** afxole.h  
  
##  <a name="coleresizebar"></a>COleResizeBar::COleResizeBar  
 构造 `COleResizeBar` 对象。  
  
```  
COleResizeBar();
```  
  
### <a name="remarks"></a>备注  
 调用**创建**创建重设大小条对象。  
  
##  <a name="create"></a>COleResizeBar::Create  
 创建一个子窗口，并将其与关联`COleResizeBar`对象。  
  
```  
virtual BOOL Create(
    CWnd* pParentWnd,  
    DWORD dwStyle = WS_CHILD | WS_VISIBLE,  
    UINT nID = AFX_IDW_RESIZE_BAR);
```  
  
### <a name="parameters"></a>参数  
 `pParentWnd`  
 调整大小条的父级窗口的指针。  
  
 `dwStyle`  
 指定[窗口样式](../../mfc/reference/window-styles.md)属性。  
  
 `nID`  
 调整大小条子窗口 id。  
  
### <a name="return-value"></a>返回值  
 调整大小条; 如果已为非零否则为 0。  
  
## <a name="see-also"></a>另请参阅  
 [MFC 示例 SUPERPAD](../../visual-cpp-samples.md)   
 [CControlBar 类](../../mfc/reference/ccontrolbar-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [COleServerDoc 类](../../mfc/reference/coleserverdoc-class.md)

