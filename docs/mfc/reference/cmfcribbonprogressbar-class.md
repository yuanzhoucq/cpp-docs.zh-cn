---
title: "CMFCRibbonProgressBar 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCRibbonProgressBar
- AFXRIBBONPROGRESSBAR/CMFCRibbonProgressBar
- AFXRIBBONPROGRESSBAR/CMFCRibbonProgressBar::CMFCRibbonProgressBar
- AFXRIBBONPROGRESSBAR/CMFCRibbonProgressBar::GetPos
- AFXRIBBONPROGRESSBAR/CMFCRibbonProgressBar::GetRangeMax
- AFXRIBBONPROGRESSBAR/CMFCRibbonProgressBar::GetRangeMin
- AFXRIBBONPROGRESSBAR/CMFCRibbonProgressBar::GetRegularSize
- AFXRIBBONPROGRESSBAR/CMFCRibbonProgressBar::IsInfiniteMode
- AFXRIBBONPROGRESSBAR/CMFCRibbonProgressBar::OnDraw
- AFXRIBBONPROGRESSBAR/CMFCRibbonProgressBar::SetInfiniteMode
- AFXRIBBONPROGRESSBAR/CMFCRibbonProgressBar::SetPos
- AFXRIBBONPROGRESSBAR/CMFCRibbonProgressBar::SetRange
dev_langs:
- C++
helpviewer_keywords:
- CMFCRibbonProgressBar [MFC], CMFCRibbonProgressBar
- CMFCRibbonProgressBar [MFC], GetPos
- CMFCRibbonProgressBar [MFC], GetRangeMax
- CMFCRibbonProgressBar [MFC], GetRangeMin
- CMFCRibbonProgressBar [MFC], GetRegularSize
- CMFCRibbonProgressBar [MFC], IsInfiniteMode
- CMFCRibbonProgressBar [MFC], OnDraw
- CMFCRibbonProgressBar [MFC], SetInfiniteMode
- CMFCRibbonProgressBar [MFC], SetPos
- CMFCRibbonProgressBar [MFC], SetRange
ms.assetid: de3d9f2e-ed59-480e-aa7d-08a33ab36c67
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 1354b0b15837a733a890c438c7771ffe39526773
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="cmfcribbonprogressbar-class"></a>CMFCRibbonProgressBar 类
实现用于直观指示较长操作进度的控件。  
  
## <a name="syntax"></a>语法  
  
```  
class CMFCRibbonProgressBar : public CMFCRibbonBaseElement  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[CMFCRibbonProgressBar::CMFCRibbonProgressBar](#cmfcribbonprogressbar)|构造并初始化一个 `CMFCRibbonProgressBar` 对象。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CMFCRibbonProgressBar::GetPos](#getpos)|返回当前的进度。|  
|[CMFCRibbonProgressBar::GetRangeMax](#getrangemax)|返回当前范围的最大值。|  
|[CMFCRibbonProgressBar::GetRangeMin](#getrangemin)|返回当前范围的最小值。|  
|[CMFCRibbonProgressBar::GetRegularSize](#getregularsize)|返回功能区元素的常规大小。 (重写[cmfcribbonbaseelement:: Getregularsize](../../mfc/reference/cmfcribbonbaseelement-class.md#getregularsize)。)|  
|[CMFCRibbonProgressBar::IsInfiniteMode](#isinfinitemode)|指定是否在无限模式下工作的进度栏。|  
|[CMFCRibbonProgressBar::OnDraw](#ondraw)|由框架调用以绘制功能区元素。 (重写[cmfcribbonbaseelement:: Ondraw](../../mfc/reference/cmfcribbonbaseelement-class.md#ondraw)。)|  
|[CMFCRibbonProgressBar::SetInfiniteMode](#setinfinitemode)|设置进度栏在无限模式下工作。|  
|[CMFCRibbonProgressBar::SetPos](#setpos)|设置当前进度。|  
|[CMFCRibbonProgressBar::SetRange](#setrange)|设置最小和最大值。|  
  
## <a name="remarks"></a>备注  
 A`CMFCRibbonProgressBar`可以在两种模式中运行： 常规和无限。 在常规模式下，进度栏填充从左到右，并在它达到最大值时停止。 在无限模式下，进度栏会反复从填充的最小值到最大值。 您可能使用无限模式来指示操作正在进行，但完成时间未知。  
  
## <a name="example"></a>示例  
 下面的示例演示如何使用各种方法`CMFCRibbonProgressBar`类。 该示例演示如何设置无限模式 （其中一个操作的完成时间为未知） 中的工作的进度栏设置进度栏的最小和最大值，并设置进度栏的当前位置。 此代码片段属于[MS Office 2007 演示示例](../../visual-cpp-samples.md)。  
  
 [!code-cpp[NVC_MFC_MSOffice2007Demo#11](../../mfc/reference/codesnippet/cpp/cmfcribbonprogressbar-class_1.cpp)]  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)  
  
 [CMFCRibbonProgressBar](../../mfc/reference/cmfcribbonprogressbar-class.md)  
  
## <a name="requirements"></a>惠?  
 **标头：** afxRibbonProgressBar.h  
  
##  <a name="cmfcribbonprogressbar"></a>CMFCRibbonProgressBar::CMFCRibbonProgressBar  
 构造并初始化[CMFCRibbonProgressBar](../../mfc/reference/cmfcribbonprogressbar-class.md)对象。  
  
```  
CMFCRibbonProgressBar();

 
CMFCRibbonProgressBar(
    UINT nID,  
    int nWidth = 90,  
    int nHeight = 22);
```  
  
### <a name="parameters"></a>参数  
 [in] `nID`  
 指定功能区进度栏的命令 ID。  
  
 [in] `nWidth`  
 指定以像素为单位，功能区进度栏的宽度。  
  
 [in] `nHeight`  
 指定以像素为单位，功能区进度栏的高度。  
  
##  <a name="getpos"></a>CMFCRibbonProgressBar::GetPos  
 返回进度栏的当前位置。  
  
```  
int GetPos () const;  
```  
  
### <a name="return-value"></a>返回值  
 表示进度栏的当前位置的值。  
  
### <a name="remarks"></a>备注  
 正在设置的范围必须在指定的范围内[CMFCRibbonProgressBar::SetRange](#setrange)方法。  
  
##  <a name="getrangemax"></a>CMFCRibbonProgressBar::GetRangeMax  
 返回进度栏的当前最大值。  
  
```  
int GetRangeMax() const;  
```  
  
### <a name="return-value"></a>返回值  
 当前范围的最大值。  
  
### <a name="remarks"></a>备注  
  
##  <a name="getrangemin"></a>CMFCRibbonProgressBar::GetRangeMin  
 返回进度栏的当前最小范围值。  
  
```  
int GetRangeMin() const;  
```  
  
### <a name="return-value"></a>返回值  
 当前范围最小值。  
  
##  <a name="getregularsize"></a>CMFCRibbonProgressBar::GetRegularSize  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual CSize GetRegularSize(CDC* pDC);
```  
  
### <a name="parameters"></a>参数  
 [in] `pDC`  
  
### <a name="return-value"></a>返回值  
  
### <a name="remarks"></a>备注  
  
##  <a name="isinfinitemode"></a>CMFCRibbonProgressBar::IsInfiniteMode  
 指定是否在无限模式下工作的进度栏。  
  
```  
BOOL IsInfiniteMode() const;  
```  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果进度栏在无限模式;否则为`FALSE`。  
  
### <a name="remarks"></a>备注  
 在无限模式下，进度栏填充重复从最小值到最大值。 您可能使用无限模式来指示操作正在进行，但完成时间未知。  
  
##  <a name="ondraw"></a>CMFCRibbonProgressBar::OnDraw  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual void OnDraw(CDC* pDC);
```  
  
### <a name="parameters"></a>参数  
 [in] `pDC`  
  
### <a name="remarks"></a>备注  
  
##  <a name="setinfinitemode"></a>CMFCRibbonProgressBar::SetInfiniteMode  
 设置进度栏在无限模式下工作。  
  
```  
void SetInfiniteMode(BOOL bSet = TRUE);
```  
  
### <a name="parameters"></a>参数  
 [in] `bSet`  
 `TRUE`若要指定进度栏处于无限模式;否则为`FALSE`。  
  
### <a name="remarks"></a>备注  
 通常情况下，如果进度栏在无限模式下，它将告诉用户操作正在进行，但完成时间未知。 因此，进度条填满重复从最小值到最大值。  
  
##  <a name="setpos"></a>CMFCRibbonProgressBar::SetPos  
 设置进度栏的当前位置。  
  
```  
void SetPos(
    int nPos,  
    BOOL bRedraw = TRUE);
```  
  
### <a name="parameters"></a>参数  
 [in] `nPos`  
 指定为设置进度栏的位置。  
  
 [in] `bRedraw`  
 指定是否应重绘进度栏。  
  
### <a name="remarks"></a>备注  
 正在设置的范围必须在指定的范围内[CMFCRibbonProgressBar::SetRange](#setrange)方法。  
  
##  <a name="setrange"></a>CMFCRibbonProgressBar::SetRange  
 设置进度栏的最小和最大值。  
  
```  
void SetRange(
    int nMin,  
    int nMax);
```  
  
### <a name="parameters"></a>参数  
 [in] `nMin`  
 指定范围的最小值。  
  
 [in] `nMax`  
 指定范围的最大值。  
  
### <a name="remarks"></a>备注  
 使用此方法，通过设置最小和最大值定义进度栏的范围。  
  
## <a name="see-also"></a>请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [类](../../mfc/reference/mfc-classes.md)   
 [CMFCRibbonBaseElement 类](../../mfc/reference/cmfcribbonbaseelement-class.md)   
 [CMFCRibbonBar 类](../../mfc/reference/cmfcribbonbar-class.md)
