---
title: CTreeView 类 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CTreeView
- AFXCVIEW/CTreeView
- AFXCVIEW/CTreeView::CTreeView
- AFXCVIEW/CTreeView::GetTreeCtrl
dev_langs:
- C++
helpviewer_keywords:
- CTreeView [MFC], CTreeView
- CTreeView [MFC], GetTreeCtrl
ms.assetid: 5df583a6-d69f-42ca-9d8d-57e04558afff
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8d19d4958de2f7909f2072b2ae2f59c00e63d65a
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33373620"
---
# <a name="ctreeview-class"></a>CTreeView 类
简化了使用树控件 and 的[CTreeCtrl](../../mfc/reference/ctreectrl-class.md)，封装树控件功能，带有 MFC 文档视图体系结构的类。  
  
## <a name="syntax"></a>语法  
  
```  
class CTreeView : public CCtrlView  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[CTreeView::CTreeView](#ctreeview)|构造 `CTreeView` 对象。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[Ctreeview:: Gettreectrl](#gettreectrl)|返回与视图关联的树控件。|  
  
## <a name="remarks"></a>备注  
 有关此体系结构的详细信息，请参阅的概览[CView](../../mfc/reference/cview-class.md)类和交叉引用存在引用。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CView](../../mfc/reference/cview-class.md)  
  
 [CCtrlView](../../mfc/reference/cctrlview-class.md)  
  
 `CTreeView`  
  
## <a name="requirements"></a>要求  
 **标头：** afxcview.h  
  
##  <a name="ctreeview"></a>  CTreeView::CTreeView  
 构造 `CTreeView` 对象。  
  
```  
CTreeView();
```  
  
##  <a name="gettreectrl"></a>  Ctreeview:: Gettreectrl  
 返回与视图相关联的树控件的引用。  
  
```  
CTreeCtrl& GetTreeCtrl() const;  
```  
  
## <a name="see-also"></a>请参阅  
 [CCtrlView 类](../../mfc/reference/cctrlview-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CView 类](../../mfc/reference/cview-class.md)   
 [CCtrlView 类](../../mfc/reference/cctrlview-class.md)   
 [CTreeCtrl 类](../../mfc/reference/ctreectrl-class.md)
