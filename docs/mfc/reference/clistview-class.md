---
title: "CListView 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CListView
- AFXCVIEW/CListView
- AFXCVIEW/CListView::CListView
- AFXCVIEW/CListView::GetListCtrl
- AFXCVIEW/CListView::RemoveImageList
dev_langs:
- C++
helpviewer_keywords:
- views, and common controls
- CListView class
ms.assetid: 7626bdb2-a1b8-4eab-b631-6743710a8432
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
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: ebf6c93aa6d88d1942af4ecb9e3373fa57d84b65
ms.lasthandoff: 02/24/2017

---
# <a name="clistview-class"></a>CListView 类
简化了使用列表控件和[CListCtrl](../../mfc/reference/clistctrl-class.md)，封装列表控件功能，与 MFC 文档视图体系结构的类。  
  
## <a name="syntax"></a>语法  
  
```  
class CListView : public CCtrlView  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|说明|  
|----------|-----------------|  
|[CListView::CListView](#clistview)|构造 `CListView` 对象。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|说明|  
|----------|-----------------|  
|[CListView::GetListCtrl](#getlistctrl)|返回与视图关联的列表控件。|  
  
### <a name="protected-methods"></a>受保护的方法  
  
|名称|说明|  
|----------|-----------------|  
|[CListView::RemoveImageList](#removeimagelist)|从列表视图中移除指定的图像列表。|  
  
## <a name="remarks"></a>备注  
 这种体系结构的详细信息，请参阅概述[CView](../../mfc/reference/cview-class.md)类和引用存在交叉引用。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CView](../../mfc/reference/cview-class.md)  
  
 [CCtrlView](../../mfc/reference/cctrlview-class.md)  
  
 `CListView`  
  
## <a name="requirements"></a>要求  
 **标头︰** afxcview.h  
  
##  <a name="clistview"></a>CListView::CListView  
 构造 `CListView` 对象。  
  
```  
CListView();
```  
  
##  <a name="getlistctrl"></a>CListView::GetListCtrl  
 调用该成员函数以获取对列表控件与视图关联的引用。  
  
```  
CListCtrl& GetListCtrl() const;  
```  
  
### <a name="return-value"></a>返回值  
 对列表控件与视图关联的引用。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCListView #&7;](../../atl/reference/codesnippet/cpp/clistview-class_1.cpp)]  
  
##  <a name="removeimagelist"></a>CListView::RemoveImageList  
 从列表视图中移除指定的图像列表。  
  
```  
void RemoveImageList(int nImageList);
```  
  
### <a name="parameters"></a>参数  
 `nImageList`  
 要删除的图像的从零开始的索引。  
  
## <a name="see-also"></a>另请参阅  
 [MFC 示例 ROWLIST](../../visual-cpp-samples.md)   
 [CCtrlView 类](../../mfc/reference/cctrlview-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CCtrlView 类](../../mfc/reference/cctrlview-class.md)

