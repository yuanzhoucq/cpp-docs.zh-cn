---
title: "CTreeView 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CTreeView
- AFXCVIEW/CTreeView
- AFXCVIEW/CTreeView::CTreeView
- AFXCVIEW/CTreeView::GetTreeCtrl
dev_langs:
- C++
helpviewer_keywords:
- directory lists
- tree view controls
- file lists [C++]
- CTreeView class, common controls
- CTreeView class
ms.assetid: 5df583a6-d69f-42ca-9d8d-57e04558afff
caps.latest.revision: 22
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
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: c317d91a07b5cb45b58ec4c4af2e9ee0f3b24e28
ms.lasthandoff: 02/24/2017

---
# <a name="ctreeview-class"></a>CTreeView 类
简化了使用树控件和[CTreeCtrl](../../mfc/reference/ctreectrl-class.md)，封装树控件功能，与 MFC 文档视图体系结构的类。  
  
## <a name="syntax"></a>语法  
  
```  
class CTreeView : public CCtrlView  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|说明|  
|----------|-----------------|  
|[CTreeView::CTreeView](#ctreeview)|构造 `CTreeView` 对象。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|说明|  
|----------|-----------------|  
|[Ctreeview:: Gettreectrl](#gettreectrl)|返回与视图关联的树控件。|  
  
## <a name="remarks"></a>备注  
 这种体系结构的详细信息，请参阅概述[CView](../../mfc/reference/cview-class.md)类和引用存在交叉引用。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CView](../../mfc/reference/cview-class.md)  
  
 [CCtrlView](../../mfc/reference/cctrlview-class.md)  
  
 `CTreeView`  
  
## <a name="requirements"></a>要求  
 **标头︰** afxcview.h  
  
##  <a name="ctreeview"></a>CTreeView::CTreeView  
 构造 `CTreeView` 对象。  
  
```  
CTreeView();
```  
  
##  <a name="gettreectrl"></a>Ctreeview:: Gettreectrl  
 返回与视图相关联的树控件的引用。  
  
```  
CTreeCtrl& GetTreeCtrl() const;  
```  
  
## <a name="see-also"></a>另请参阅  
 [CCtrlView 类](../../mfc/reference/cctrlview-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CView 类](../../mfc/reference/cview-class.md)   
 [CCtrlView 类](../../mfc/reference/cctrlview-class.md)   
 [CTreeCtrl 类](../../mfc/reference/ctreectrl-class.md)

