---
title: "CMFCBaseToolBar 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCBaseToolBar::CreateObject
- ~CMFCBaseToolBar
- CMFCBaseToolBar
- CMFCBaseToolBar::CMFCBaseToolBar
- CMFCBaseToolBar::~CMFCBaseToolBar
- CMFCBaseToolBar.~CMFCBaseToolBar
- CreateObject
- CMFCBaseToolBar.CMFCBaseToolBar
- CMFCBaseToolBar.CreateObject
dev_langs:
- C++
helpviewer_keywords:
- CMFCBaseToolBar class, constructor
- CMFCBaseToolBar class, destructor
- ~CMFCBaseToolBar destructor
- CreateObject method
- CMFCBaseToolBar class
ms.assetid: 5d79206d-55e4-46f8-b1b8-042e34d7f9da
caps.latest.revision: 19
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
ms.openlocfilehash: f608b23c0dbee3ec0e2d2b234612365e3c2461b0
ms.lasthandoff: 02/24/2017

---
# <a name="cmfcbasetoolbar-class"></a>CMFCBaseToolBar 类
工具栏的基类。  
  
## <a name="syntax"></a>语法  
  
```  
class CMFCBaseToolBar : public CPane  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|说明|  
|----------|-----------------|  
|`CMFCBaseToolBar::CMFCBaseToolBar`|默认构造函数。|  
|`CMFCBaseToolBar::~CMFCBaseToolBar`|析构函数。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|`CMFCBaseToolBar::CreateObject`|由框架用于创建此类类型的动态实例。|  
|[CMFCBaseToolBar::GetDockingMode](#getdockingmode)|返回停靠模式。 (重写[CBasePane::GetDockingMode](../../mfc/reference/cbasepane-class.md#getdockingmode)。)|  
|[CMFCBaseToolBar::GetMinSize](#getminsize)|返回一个工具栏的最小大小。 (重写[CPane::GetMinSize](../../mfc/reference/cpane-class.md#getminsize)。)|  
|[CMFCBaseToolBar::OnAfterChangeParent](#onafterchangeparent)|由框架调用窗格中的父发生更改后。 (重写[CBasePane::OnAfterChangeParent](../../mfc/reference/cbasepane-class.md#onafterchangeparent)。)|  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CBasePane](../../mfc/reference/cbasepane-class.md)  
  
 [CPane](../../mfc/reference/cpane-class.md)  
  
 [CMFCBaseToolBar](../../mfc/reference/cmfcbasetoolbar-class.md)  
  
## <a name="requirements"></a>要求  
 **标头︰** afxbasetoolbar.h  
  
##  <a name="a-namegetdockingmodea--cmfcbasetoolbargetdockingmode"></a><a name="getdockingmode"></a>CMFCBaseToolBar::GetDockingMode  
 返回停靠模式。  
  
```  
virtual AFX_DOCK_TYPE GetDockingMode() const;  
```  
  
### <a name="return-value"></a>返回值  
 停靠的模式。  
  
##  <a name="a-namegetminsizea--cmfcbasetoolbargetminsize"></a><a name="getminsize"></a>CMFCBaseToolBar::GetMinSize  
 返回一个工具栏的最小大小。  
  
```  
virtual void GetMinSize(CSize& size) const;  
```  
  
### <a name="parameters"></a>参数  
 [out] `size`  
 工具栏的最小大小。  
  
##  <a name="a-nameonafterchangeparenta--cmfcbasetoolbaronafterchangeparent"></a><a name="onafterchangeparent"></a>CMFCBaseToolBar::OnAfterChangeParent  
 由框架调用窗格中的父发生更改后。  
  
```  
virtual void OnAfterChangeParent(CWnd* pWndOldParent);
```  
  
### <a name="parameters"></a>参数  
 [in] `pWndOldParent`  
 指向上一个父窗口的指针。  
  
## <a name="see-also"></a>另请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [类](../../mfc/reference/mfc-classes.md)

