---
title: CMFCRibbonSlider 类 |Microsoft Docs
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
ms.openlocfilehash: 307b7f769035a9ddb84a3d0e51e0ff6d8a016472
ms.sourcegitcommit: 26fff80635bd1d51bc51899203fddfea8b29b530
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/05/2018
ms.locfileid: "37850847"
---
# <a name="cmfcribbonslider-class"></a>CMFCRibbonSlider 类
`CMFCRibbonSlider`类实现可添加到功能区栏或功能区状态栏的滑块控件。 功能区滑块控件类似于显示在 Office 2007 应用程序中的缩放滑块。  
  
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
|[CMFCRibbonSlider::GetPos](#getpos)|返回当前位置的滑块控件。|  
|[CMFCRibbonSlider::GetRangeMax](#getrangemax)|返回滑块的最大值。|  
|[CMFCRibbonSlider::GetRangeMin](#getrangemin)|返回滑块的最小值。|  
|[CMFCRibbonSlider::GetRegularSize](#getregularsize)|返回功能区元素的常规大小。 (重写[cmfcribbonbaseelement:: Getregularsize](../../mfc/reference/cmfcribbonbaseelement-class.md#getregularsize)。)|  
|[CMFCRibbonSlider::GetZoomIncrement](#getzoomincrement)|返回滑块控件的缩放增量的大小。|  
|[CMFCRibbonSlider::HasZoomButtons](#haszoombuttons)|指定滑块是否有缩放按钮。|  
|[CMFCRibbonSlider::OnDraw](#ondraw)|由框架调用以绘制功能区元素。 (重写[cmfcribbonbaseelement:: Ondraw](../../mfc/reference/cmfcribbonbaseelement-class.md#ondraw)。)|  
|[CMFCRibbonSlider::SetPos](#setpos)|设置滑块控件的当前位置。|  
|[CMFCRibbonSlider::SetRange](#setrange)|通过设置最小值和最大值指定滑块控件的范围。|  
|[CMFCRibbonSlider::SetZoomButtons](#setzoombuttons)|显示或隐藏缩放按钮。|  
|[CMFCRibbonSlider::SetZoomIncrement](#setzoomincrement)|设置缩放增量为滑块控件的大小。|  
  
## <a name="remarks"></a>备注  
 可以使用`SetRange`方法配置缩放增量为滑块的范围。 可以通过使用设置滑块的当前位置`SetPos`方法。  
  
 可以通过在左侧和右侧的滑块控件中显示循环缩放按钮`SetZoomButtons`方法。 默认情况下是水平的滑块、 左的缩放按钮显示负号和正确缩放按钮将显示一个加号。  
  
 `SetZoomIncrement`方法定义的递增加上或减去从当前位置，当用户单击缩放按钮。  
  
## <a name="example"></a>示例  
 下面的示例演示如何使用中的各种方法`CMFCRibbonSlider`类来设置滑块的属性。 该示例演示如何构造`CMFCRibbonSlider`对象、 显示缩放按钮、 设置滑块控件的当前位置和设置的滑块控件的值范围。  
  
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
 [in]*nID*  
 滑块 id。  
  
 [in]。 *nWidth*  
 滑块以像素为单位的宽度。  
  
### <a name="remarks"></a>备注  
 构造是一个功能区滑块*nWidth*像素宽面板类别添加滑块的位置中。 默认情况下，为水平滑块。  
  
##  <a name="getpos"></a>  CMFCRibbonSlider::GetPos  
 返回当前位置的滑块控件。  
  
```  
int GetPos() const;  
```  
  
### <a name="return-value"></a>返回值  
 滑块控件，它是相对于开头的滑块的位置的当前位置。  
  
##  <a name="getrangemax"></a>  CMFCRibbonSlider::GetRangeMax  
 获取滑块可以传输滑块控件的滑块的最大增量。  
  
```  
int GetRangeMax() const;  
```  
  
### <a name="return-value"></a>返回值  
 滑块可以传输滑块控件的滑块的最大增量。  
  
##  <a name="getrangemin"></a>  CMFCRibbonSlider::GetRangeMin  
 返回滑块可以传输滑块控件的最小增量。  
  
```  
int GetRangeMin() const;  
```  
  
### <a name="return-value"></a>返回值  
 将滑块可以传输滑块控件的最小增量。  
  
##  <a name="getregularsize"></a>  CMFCRibbonSlider::GetRegularSize  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual CSize GetRegularSize(CDC* pDC);
```  
  
### <a name="parameters"></a>参数  
 [in]*pDC*  
  
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
 如果该滑块有缩放按钮; 则为 TRUEFALSE 否则为。  
  
##  <a name="ondraw"></a>  CMFCRibbonSlider::OnDraw  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual void OnDraw(CDC* pDC);
```  
  
### <a name="parameters"></a>参数  
 [in]*pDC*  
  
### <a name="remarks"></a>备注  
  
##  <a name="setpos"></a>  CMFCRibbonSlider::SetPos  
 设置滑块控件的当前位置。  
  
```  
void SetPos(
    int nPos,  
    BOOL bRedraw=TRUE);
```  
  
### <a name="parameters"></a>参数  
 [in]*nPos*  
 指定要为滑块设置的位置。 位置是相对于滑块的开头。  
  
 [in]*bRedraw*  
 如果为 TRUE，则滑块将重新绘制。  
  
##  <a name="setrange"></a>  CMFCRibbonSlider::SetRange  
 设置范围滑块控件的值。  
  
```  
void SetRange(
    int nMin,  
    int nMax);
```  
  
### <a name="parameters"></a>参数  
 [in]*nMin*  
 指定滑块控件的最小的值。  
  
 [in]*最*  
 指定滑块控件的最大的值。  
  
### <a name="remarks"></a>备注  
 通过设置最小值和最大值指定滑块控件的值的范围。  
  
##  <a name="setzoombuttons"></a>  CMFCRibbonSlider::SetZoomButtons  
 显示或隐藏缩放按钮。  
  
```  
void SetZoomButtons(BOOL bSet=TRUE);
```  
  
### <a name="parameters"></a>参数  
 [in]。 *bSet*  
 为 TRUE，则显示缩放按钮;如果为 FALSE，以将其隐藏。  
  
##  <a name="setzoomincrement"></a>  CMFCRibbonSlider::SetZoomIncrement  
 设置滑块控件的缩放增量。  
  
```  
void SetZoomIncrement(int nZoomIncrement);
```  
  
### <a name="parameters"></a>参数  
 [in]*nZoomIncrement*  
 指定滑块控件的缩放增量。  
  
## <a name="see-also"></a>请参阅  
 [层次结构图表](../../mfc/hierarchy-chart.md)   
 [类](../../mfc/reference/mfc-classes.md)   
 [CMFCRibbonBaseElement 类](../../mfc/reference/cmfcribbonbaseelement-class.md)
