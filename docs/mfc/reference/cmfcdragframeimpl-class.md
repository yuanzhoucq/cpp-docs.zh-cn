---
title: CMFCDragFrameImpl 类 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMFCDragFrameImpl
dev_langs:
- C++
helpviewer_keywords:
- CMFCDragFrameImpl class [MFC]
ms.assetid: 500cd824-8188-43c2-8754-b7bb46b5648a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: aee2c58d8763581987fec40b0cb486c67363697b
ms.sourcegitcommit: a41c4d096afca1e9b619bbbce045b77135d32ae2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/14/2018
ms.locfileid: "42541729"
---
# <a name="cmfcdragframeimpl-class"></a>CMFCDragFrameImpl 类
`CMFCDragFrameImpl`类绘制当用户在标准停靠模式下拖动窗格时显示的拖动矩形。  
   有关更多详细信息，请参阅中的源代码**VC\\atlmfc\\src\\mfc**的 Visual Studio 安装文件夹。  
   
## <a name="syntax"></a>语法  
  
```  
class CMFCDragFrameImpl  
```  
  
## <a name="remarks"></a>备注  
 此类的一个对象嵌入到每个[CPane 类](../../mfc/reference/cpane-class.md)对象。 因此，使用每个窗格`CanFloat`方法会在用户拖动它时显示拖动矩形。  
  
 可以通过使用控制的拖动矩形粗细[AFX_GLOBAL_DATA::m_nDragFrameThicknessFloat](afx-global-data-structure.md#m_ndragframethicknessfloat)并[AFX_GLOBAL_DATA::m_nDragFrameThicknessDock](afx-global-data-structure.md#m_ndragframethicknessdock)。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CMFCDragFrameImpl](../../mfc/reference/cmfcdragframeimpl-class.md)  
  
## <a name="requirements"></a>要求  
 **标头：** afxdragframeimpl.h  
  
##  <a name="enddrawdragframe"></a>  CMFCDragFrameImpl::EndDrawDragFrame  

  
```  
void EndDrawDragFrame(BOOL bClearInternalRects = TRUE);
```  
  
### <a name="parameters"></a>参数  
 [in]*bClearInternalRects*  
  
### <a name="remarks"></a>备注  
  
##  <a name="init"></a>  CMFCDragFrameImpl::Init  

  
```  
void Init(CWnd* pDraggedWnd);
```  
  
### <a name="parameters"></a>参数  
 [in]*pDraggedWnd*  
  
### <a name="remarks"></a>备注  
  
##  <a name="movedragframe"></a>  CMFCDragFrameImpl::MoveDragFrame  

  
```  
void MoveDragFrame(BOOL bForceMove = FALSE);
```  
  
### <a name="parameters"></a>参数  
 [in]*bForceMove*  
  
### <a name="remarks"></a>备注  
  
##  <a name="placetabpredocking"></a>  CMFCDragFrameImpl::PlaceTabPreDocking  

  
```  
void PlaceTabPreDocking(
    CBaseTabbedPane* pTabbedBar,  
    BOOL bFirstTime);  
  
void PlaceTabPreDocking(CWnd* pCBarToPlaceOn);
```  
  
### <a name="parameters"></a>参数  
 [in]*pTabbedBar*  
 [in]*bFirstTime*  
 [in]*pCBarToPlaceOn*  
  
### <a name="remarks"></a>备注  
  
##  <a name="removetabpredocking"></a>  CMFCDragFrameImpl::RemoveTabPreDocking  

  
```  
void RemoveTabPreDocking(CDockablePane* pOldTargetBar = NULL);
```  
  
### <a name="parameters"></a>参数  
 [in]*pOldTargetBar*  
  
### <a name="remarks"></a>备注  
  
##  <a name="resetstate"></a>  CMFCDragFrameImpl::ResetState  

  
```  
void ResetState();
```  
  
### <a name="remarks"></a>备注  
  
## <a name="see-also"></a>请参阅  
 [层次结构图表](../../mfc/hierarchy-chart.md)   
 [类](../../mfc/reference/mfc-classes.md)   
 [CPane 类](../../mfc/reference/cpane-class.md)