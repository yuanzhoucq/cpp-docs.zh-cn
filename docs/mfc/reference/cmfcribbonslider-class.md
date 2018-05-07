---
title: CMFCRibbonSlider 类 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMFCRibbonSlider
- AFXRIBBONSLIDER/CMFCRibbonSlider
- AFXRIBBONSLIDER/CMFCRibbonSlider::CMFCRibbonSlider
- AFXRIBBONSLIDER/CMFCRibbonSlider::GetPos
- AFXRIBBONSLIDER/CMFCRibbonSlider::GetRangeMax
- AFXRIBBONSLIDER/CMFCRibbonSlider::GetRangeMin
- AFXRIBBONSLIDER/CMFCRibbonSlider::GetRegularSize
- AFXRIBBONSLIDER/CMFCRibbonSlider::GetZoomIncrement
- AFXRIBBONSLIDER/CMFCRibbonSlider::HasZoomButtons
- AFXRIBBONSLIDER/CMFCRibbonSlider::OnDraw
- AFXRIBBONSLIDER/CMFCRibbonSlider::SetPos
- AFXRIBBONSLIDER/CMFCRibbonSlider::SetRange
- AFXRIBBONSLIDER/CMFCRibbonSlider::SetZoomButtons
- AFXRIBBONSLIDER/CMFCRibbonSlider::SetZoomIncrement
dev_langs:
- C++
helpviewer_keywords:
- CMFCRibbonSlider [MFC], CMFCRibbonSlider
- CMFCRibbonSlider [MFC], GetPos
- CMFCRibbonSlider [MFC], GetRangeMax
- CMFCRibbonSlider [MFC], GetRangeMin
- CMFCRibbonSlider [MFC], GetRegularSize
- CMFCRibbonSlider [MFC], GetZoomIncrement
- CMFCRibbonSlider [MFC], HasZoomButtons
- CMFCRibbonSlider [MFC], OnDraw
- CMFCRibbonSlider [MFC], SetPos
- CMFCRibbonSlider [MFC], SetRange
- CMFCRibbonSlider [MFC], SetZoomButtons
- CMFCRibbonSlider [MFC], SetZoomIncrement
ms.assetid: 9351ac34-f234-4e42-91e2-763f1989c8ff
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4a4264f26028db4c581fe1dc143905ac0ffc8f66
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="cmfcribbonslider-class"></a>CMFCRibbonSlider 类
`CMFCRibbonSlider`类实现可以将添加到功能区栏或功能区状态栏的滑块控件。 功能区滑块控件类似于显示在 Office 2007 应用程序中的缩放滑块。  
  
## <a name="syntax"></a>语法  
  
```  
class CMFCRibbonSlider : public CMFCRibbonBaseElement  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[CMFCRibbonSlider::CMFCRibbonSlider](#cmfcribbonslider)|构造并初始化功能区滑块控件。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CMFCRibbonSlider::GetPos](#getpos)|返回当前滑块控件的位置。|  
|[CMFCRibbonSlider::GetRangeMax](#getrangemax)|返回将滑块的最大值。|  
|[CMFCRibbonSlider::GetRangeMin](#getrangemin)|返回将滑块的最小值。|  
|[CMFCRibbonSlider::GetRegularSize](#getregularsize)|返回功能区元素的常规大小。 (重写[cmfcribbonbaseelement:: Getregularsize](../../mfc/reference/cmfcribbonbaseelement-class.md#getregularsize)。)|  
|[CMFCRibbonSlider::GetZoomIncrement](#getzoomincrement)|返回的滑块控件的缩放增量的大小。|  
|[CMFCRibbonSlider::HasZoomButtons](#haszoombuttons)|指定滑块是否有缩放按钮。|  
|[CMFCRibbonSlider::OnDraw](#ondraw)|由框架调用以绘制功能区元素。 (重写[cmfcribbonbaseelement:: Ondraw](../../mfc/reference/cmfcribbonbaseelement-class.md#ondraw)。)|  
|[CMFCRibbonSlider::SetPos](#setpos)|设置滑块控件的当前位置。|  
|[CMFCRibbonSlider::SetRange](#setrange)|通过设置最小和最大值指定滑块控件的范围。|  
|[CMFCRibbonSlider::SetZoomButtons](#setzoombuttons)|显示或隐藏缩放按钮。|  
|[CMFCRibbonSlider::SetZoomIncrement](#setzoomincrement)|设置滑块控件的缩放增量大小。|  
  
## <a name="remarks"></a>备注  
 你可以使用`SetRange`方法来配置滑块缩放增量的范围。 你可以通过使用设置滑块的当前位置`SetPos`方法。  
  
 您可以通过使用循环缩放按钮显示在左侧和右侧的滑块控件`SetZoomButtons`方法。 默认情况下，滑块为水平方向、 左的缩放按钮将显示一个减号和右缩放按钮将显示一个加号。  
  
 `SetZoomIncrement`方法定义的增量将添加到或从当前位置减去，当用户单击缩放按钮。  
  
## <a name="example"></a>示例  
 下面的示例演示如何使用各种方法`CMFCRibbonSlider`类来设置滑块的属性。 该示例演示如何构造`CMFCRibbonSlider`对象、 显示缩放按钮、 设置滑块控件的当前位置和设置滑块控件的值的范围。  
  
 [!code-cpp[NVC_MFC_RibbonApp#12](../../mfc/reference/codesnippet/cpp/cmfcribbonslider-class_1.cpp)]  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)  
  
 [CMFCRibbonSlider](../../mfc/reference/cmfcribbonslider-class.md)  
  
## <a name="requirements"></a>要求  
 **标头：** afxribbonslider.h  
  
##  <a name="cmfcribbonslider"></a>  CMFCRibbonSlider::CMFCRibbonSlider  
 构造一个功能区滑块。  
  
```  
CMFCRibbonSlider(
    UINT nID,  
    int nWidth=100);
```  
  
### <a name="parameters"></a>参数  
 [in] `nID`  
 滑块 id。  
  
 [in]。 `nWidth`  
 以像素为单位的滑块宽度。  
  
### <a name="remarks"></a>备注  
 构造是一个功能区滑块`nWidth`像素宽在其中添加滑块的面板类别。 默认情况下，滑块为水平方向。  
  
##  <a name="getpos"></a>  CMFCRibbonSlider::GetPos  
 返回当前滑块控件的位置。  
  
```  
int GetPos() const;  
```  
  
### <a name="return-value"></a>返回值  
 滑块控件，这是滑块的相对于开始的位置的当前位置。  
  
##  <a name="getrangemax"></a>  CMFCRibbonSlider::GetRangeMax  
 获取滑块可以经过的滑块控件的滑块的最大增量。  
  
```  
int GetRangeMax() const;  
```  
  
### <a name="return-value"></a>返回值  
 滑块可以经过的滑块控件将滑块的最大增量。  
  
##  <a name="getrangemin"></a>  CMFCRibbonSlider::GetRangeMin  
 返回滑块可以经过的滑块控件的最小增量。  
  
```  
int GetRangeMin() const;  
```  
  
### <a name="return-value"></a>返回值  
 滑块可以经过的滑块控件的最小增量。  
  
##  <a name="getregularsize"></a>  CMFCRibbonSlider::GetRegularSize  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual CSize GetRegularSize(CDC* pDC);
```  
  
### <a name="parameters"></a>参数  
 [in] `pDC`  
  
### <a name="return-value"></a>返回值  
  
### <a name="remarks"></a>备注  
  
##  <a name="getzoomincrement"></a>  CMFCRibbonSlider::GetZoomIncrement  
 获取滑块控件的缩放增量。  
  
```  
int GetZoomIncrement() const;  
```  
  
### <a name="return-value"></a>返回值  
 滑块控件缩放增量。  
  
##  <a name="haszoombuttons"></a>  CMFCRibbonSlider::HasZoomButtons  
 指定滑块是否有缩放按钮。  
  
```  
BOOL HasZoomButtons() const;  
```  
  
### <a name="return-value"></a>返回值  
 `TRUE` 如果滑块具有缩放按钮;`FALSE`否则为。  
  
##  <a name="ondraw"></a>  CMFCRibbonSlider::OnDraw  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual void OnDraw(CDC* pDC);
```  
  
### <a name="parameters"></a>参数  
 [in] `pDC`  
  
### <a name="remarks"></a>备注  
  
##  <a name="setpos"></a>  CMFCRibbonSlider::SetPos  
 设置滑块控件的当前位置。  
  
```  
void SetPos(
    int nPos,  
    BOOL bRedraw=TRUE);
```  
  
### <a name="parameters"></a>参数  
 [in] `nPos`  
 指定要设置滑块的位置。 相对于滑块的开始位置。  
  
 [in] `bRedraw`  
 如果`TRUE`，滑块将重绘。  
  
##  <a name="setrange"></a>  CMFCRibbonSlider::SetRange  
 设置滑块控件的值的范围。  
  
```  
void SetRange(
    int nMin,  
    int nMax);
```  
  
### <a name="parameters"></a>参数  
 [in] `nMin`  
 指定滑块控件的最小值。  
  
 [in] `nMax`  
 指定滑块控件的最大值。  
  
### <a name="remarks"></a>备注  
 通过设置最小和最大值指定滑块控件的值的范围。  
  
##  <a name="setzoombuttons"></a>  CMFCRibbonSlider::SetZoomButtons  
 显示或隐藏缩放按钮。  
  
```  
void SetZoomButtons(BOOL bSet=TRUE);
```  
  
### <a name="parameters"></a>参数  
 [in]。 `bSet`  
 `TRUE` 若要显示缩放按钮;`FALSE`以隐藏它们。  
  
##  <a name="setzoomincrement"></a>  CMFCRibbonSlider::SetZoomIncrement  
 设置滑块控件的缩放增量。  
  
```  
void SetZoomIncrement(int nZoomIncrement);
```  
  
### <a name="parameters"></a>参数  
 [in] `nZoomIncrement`  
 指定滑块控件的缩放增量。  
  
## <a name="see-also"></a>请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [类](../../mfc/reference/mfc-classes.md)   
 [CMFCRibbonBaseElement 类](../../mfc/reference/cmfcribbonbaseelement-class.md)
