---
title: "CMFCDragFrameImpl 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCDragFrameImpl
dev_langs:
- C++
helpviewer_keywords:
- CMFCDragFrameImpl class
ms.assetid: 500cd824-8188-43c2-8754-b7bb46b5648a
caps.latest.revision: 26
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
ms.openlocfilehash: 8c21e3bcca36838e40cb7a0edcddba432ecb0540
ms.lasthandoff: 02/24/2017

---
# <a name="cmfcdragframeimpl-class"></a>CMFCDragFrameImpl 类
`CMFCDragFrameImpl`类绘制当用户在标准停靠模式下拖动窗格时显示的拖动矩形。  
  
## <a name="syntax"></a>语法  
  
```  
class CMFCDragFrameImpl  
```  
  
## <a name="remarks"></a>备注  
 此类的一个对象嵌入到每个[CPane 类](../../mfc/reference/cpane-class.md)对象。 因此，使用每个窗格`CanFloat`方法显示拖动矩形，当用户拖动它。  
  
 你可以通过使用控制的拖动矩形的粗细 [AFX_GLOBAL_DATA::m_nDragFrameThicknessFloat]--brokenlink--(afx-global-data-structure.md#m_ndragframethicknessfloat) 和[AFX_GLOBAL_DATA::m_nDragFrameThicknessDock](afx-global-data-structure.md#m_ndragframethicknessdock)。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CMFCDragFrameImpl](../../mfc/reference/cmfcdragframeimpl-class.md)  
  
## <a name="requirements"></a>要求  
 **标头︰** afxdragframeimpl.h  
  
##  <a name="enddrawdragframe"></a>CMFCDragFrameImpl::EndDrawDragFrame  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
void EndDrawDragFrame(BOOL bClearInternalRects = TRUE);
```  
  
### <a name="parameters"></a>参数  
 [in] `bClearInternalRects`  
  
### <a name="remarks"></a>备注  
  
##  <a name="init"></a>CMFCDragFrameImpl::Init  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
void Init(CWnd* pDraggedWnd);
```  
  
### <a name="parameters"></a>参数  
 [in] `pDraggedWnd`  
  
### <a name="remarks"></a>备注  
  
##  <a name="movedragframe"></a>CMFCDragFrameImpl::MoveDragFrame  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
void MoveDragFrame(BOOL bForceMove = FALSE);
```  
  
### <a name="parameters"></a>参数  
 [in] `bForceMove`  
  
### <a name="remarks"></a>备注  
  
##  <a name="placetabpredocking"></a>CMFCDragFrameImpl::PlaceTabPreDocking  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
void PlaceTabPreDocking(
    CBaseTabbedPane* pTabbedBar,  
    BOOL bFirstTime);  
  
void PlaceTabPreDocking(CWnd* pCBarToPlaceOn);
```  
  
### <a name="parameters"></a>参数  
 [in] `pTabbedBar`  
 [in] `bFirstTime`  
 [in] `pCBarToPlaceOn`  
  
### <a name="remarks"></a>备注  
  
##  <a name="removetabpredocking"></a>CMFCDragFrameImpl::RemoveTabPreDocking  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
void RemoveTabPreDocking(CDockablePane* pOldTargetBar = NULL);
```  
  
### <a name="parameters"></a>参数  
 [in] `pOldTargetBar`  
  
### <a name="remarks"></a>备注  
  
##  <a name="resetstate"></a>CMFCDragFrameImpl::ResetState  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
void ResetState();
```  
  
### <a name="remarks"></a>备注  
  
## <a name="see-also"></a>另请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [类](../../mfc/reference/mfc-classes.md)   
 [CPane 类](../../mfc/reference/cpane-class.md)
