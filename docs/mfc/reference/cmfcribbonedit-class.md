---
title: "CMFCRibbonEdit 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCRibbonEdit
- AFXRIBBONEDIT/CMFCRibbonEdit
- AFXRIBBONEDIT/CMFCRibbonEdit::CMFCRibbonEdit
- AFXRIBBONEDIT/CMFCRibbonEdit::CanBeStretched
- AFXRIBBONEDIT/CMFCRibbonEdit::CMFCRibbonEdit
- AFXRIBBONEDIT/CMFCRibbonEdit::CopyFrom
- AFXRIBBONEDIT/CMFCRibbonEdit::CreateEdit
- AFXRIBBONEDIT/CMFCRibbonEdit::DestroyCtrl
- AFXRIBBONEDIT/CMFCRibbonEdit::DropDownList
- AFXRIBBONEDIT/CMFCRibbonEdit::EnableSpinButtons
- AFXRIBBONEDIT/CMFCRibbonEdit::GetCompactSize
- AFXRIBBONEDIT/CMFCRibbonEdit::GetEditText
- AFXRIBBONEDIT/CMFCRibbonEdit::GetIntermediateSize
- AFXRIBBONEDIT/CMFCRibbonEdit::GetTextAlign
- AFXRIBBONEDIT/CMFCRibbonEdit::GetWidth
- AFXRIBBONEDIT/CMFCRibbonEdit::HasCompactMode
- AFXRIBBONEDIT/CMFCRibbonEdit::HasFocus
- AFXRIBBONEDIT/CMFCRibbonEdit::HasLargeMode
- AFXRIBBONEDIT/CMFCRibbonEdit::HasSpinButtons
- AFXRIBBONEDIT/CMFCRibbonEdit::IsHighlighted
- AFXRIBBONEDIT/CMFCRibbonEdit::OnAfterChangeRect
- AFXRIBBONEDIT/CMFCRibbonEdit::OnDraw
- AFXRIBBONEDIT/CMFCRibbonEdit::OnDrawLabelAndImage
- AFXRIBBONEDIT/CMFCRibbonEdit::OnDrawOnList
- AFXRIBBONEDIT/CMFCRibbonEdit::OnEnable
- AFXRIBBONEDIT/CMFCRibbonEdit::OnHighlight
- AFXRIBBONEDIT/CMFCRibbonEdit::OnKey
- AFXRIBBONEDIT/CMFCRibbonEdit::OnLButtonDown
- AFXRIBBONEDIT/CMFCRibbonEdit::OnLButtonUp
- AFXRIBBONEDIT/CMFCRibbonEdit::OnRTLChanged
- AFXRIBBONEDIT/CMFCRibbonEdit::OnShow
- AFXRIBBONEDIT/CMFCRibbonEdit::Redraw
- AFXRIBBONEDIT/CMFCRibbonEdit::SetACCData
- AFXRIBBONEDIT/CMFCRibbonEdit::SetEditText
- AFXRIBBONEDIT/CMFCRibbonEdit::SetTextAlign
- AFXRIBBONEDIT/CMFCRibbonEdit::SetWidth
dev_langs:
- C++
helpviewer_keywords:
- CMFCRibbonEdit class
ms.assetid: 9b85f1f2-446b-454e-9af9-104fdad8a897
caps.latest.revision: 25
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
ms.openlocfilehash: 03eb96bf971b53a2100e6f93bac2f0641f0298e1
ms.lasthandoff: 02/24/2017

---
# <a name="cmfcribbonedit-class"></a>CMFCRibbonEdit 类
在功能区栏上实现位于编辑控件。  
  
## <a name="syntax"></a>语法  
  
```  
class CMFCRibbonEdit : public CMFCRibbonButton  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|说明|  
|----------|-----------------|  
|[CMFCRibbonEdit::CMFCRibbonEdit](#cmfcribbonedit)|构造 `CMFCRibbonEdit` 对象。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|说明|  
|----------|-----------------|  
|[CMFCRibbonEdit::CanBeStretched](#canbestretched)|指示是否的高度`CMFCRibbonEdit`控件可以垂直方向上增加到功能区行的高度。|  
|[CMFCRibbonEdit::CMFCRibbonEdit](#cmfcribbonedit)|构造 `CMFCRibbonEdit` 对象。|  
|[CMFCRibbonEdit::CopyFrom](#copyfrom)|将指定的状态复制`CMFCRibbonEdit`对象与当前`CMFCRibbonEdit`对象。|  
|[CMFCRibbonEdit::CreateEdit](#createedit)|创建一个新文本框`CMFCRibbonEdit`对象。|  
|[CMFCRibbonEdit::DestroyCtrl](#destroyctrl)|销毁`CMFCRibbonEdit`对象。|  
|[CMFCRibbonEdit::DropDownList](#dropdownlist)|下拉列表框。|  
|[CMFCRibbonEdit::EnableSpinButtons](#enablespinbuttons)|启用并设置文本框的数值调节钮的范围。|  
|[CMFCRibbonEdit::GetCompactSize](#getcompactsize)|检索的压缩大小`CFMCRibbonEdit`对象。|  
|[CMFCRibbonEdit::GetEditText](#getedittext)|检索在文本框中的文本。|  
|[CMFCRibbonEdit::GetIntermediateSize](#getintermediatesize)|检索的中间大小`CMFCRibbonEdit`对象。|  
|[CMFCRibbonEdit::GetTextAlign](#gettextalign)|检索文本框中文本的对齐方式。|  
|[CMFCRibbonEdit::GetWidth](#getwidth)|检索的宽度，以像素为单位的`CMFCRibbonEdit`控件。|  
|[CMFCRibbonEdit::HasCompactMode](#hascompactmode)|指示是否显示大小调整为`CMFCRibbonEdit`控件均可以是 compact。|  
|[CMFCRibbonEdit::HasFocus](#hasfocus)|指示是否`CMFCRIbbonEdit`控件具有焦点。|  
|[CMFCRibbonEdit::HasLargeMode](#haslargemode)|指示是否显示大小调整为`CMFCRibbonEdit`控件可能很大。|  
|[CMFCRibbonEdit::HasSpinButtons](#hasspinbuttons)|指示文本框是否具有数值调节钮。|  
|[CMFCRibbonEdit::IsHighlighted](#ishighlighted)|指示是否`CMFCRibbonEdit`突出显示控件。|  
|[CMFCRibbonEdit::OnAfterChangeRect](#onafterchangerect)|由框架调用时的显示矩形的尺寸`CMFCRibbonEdit`控制的更改。|  
|[CMFCRibbonEdit::OnDraw](#ondraw)|由框架调用以绘制`CMFCRibbonEdit`控件。|  
|[CMFCRibbonEdit::OnDrawLabelAndImage](#ondrawlabelandimage)|由框架调用以绘制标签和图像的`CMFCRibbonEdit`控件。|  
|[CMFCRibbonEdit::OnDrawOnList](#ondrawonlist)|由框架调用以绘制`CMFCRibbonEdit`命令列表框中的控件。|  
|[CMFCRibbonEdit::OnEnable](#onenable)|由框架调用以启用或禁用`CMFCRibbonEdit`控件。|  
|[CMFCRibbonEdit::OnHighlight](#onhighlight)|当鼠标指针进入或离开的边界由框架调用`CMFCRibbonEdit`控件。|  
|[CMFCRibbonEdit::OnKey](#onkey)|由框架调用，当用户按快捷键提示和`CMFCRibbonEdit`控件具有焦点。|  
|[CMFCRibbonEdit::OnLButtonDown](#onlbuttondown)|由框架调用以更新`CMFCRibbonEdit`控制当用户按鼠标左键在控件上。|  
|[CMFCRibbonEdit::OnLButtonUp](#onlbuttonup)|在用户释放鼠标左键时由框架调用。|  
|[CMFCRibbonEdit::OnRTLChanged](#onrtlchanged)|由框架调用以更新`CMFCRibbonEdit`控制布局时更改方向。|  
|[CMFCRibbonEdit::OnShow](#onshow)|由框架调用以显示或隐藏`CMFCRibbonEdit`控件。|  
|[CMFCRibbonEdit::Redraw](#redraw)|更新的显示`CMFCRibbonEdit`控件。|  
|[CMFCRibbonEdit::SetACCData](#setaccdata)|设置的可访问性数据`CMFCRibbonEdit`对象。|  
|[CMFCRibbonEdit::SetEditText](#setedittext)|在文本框中设置的文本。|  
|[CMFCRibbonEdit::SetTextAlign](#settextalign)|设置文本框中的文本对齐方式。|  
|[CMFCRibbonEdit::SetWidth](#setwidth)|设置文本框的宽度`CMFCRibbonEdit`控件。|  
  
## <a name="remarks"></a>备注  
  
## <a name="example"></a>示例  
 下面的示例演示如何构造`CMFCRibbonEdit`对象、 显示数字显示按钮旁边的编辑控件，并设置编辑控件的文本。 此代码段属于[MS Office 2007 演示示例](../../visual-cpp-samples.md)。  
  
 [!code-cpp[NVC_MFC_MSOffice2007Demo #&7;](../../mfc/reference/codesnippet/cpp/cmfcribbonedit-class_1.cpp)]  
  
## <a name="requirements"></a>要求  
 **标头︰** afxRibbonEdit.h  
  
##  <a name="canbestretched"></a>CMFCRibbonEdit::CanBeStretched  
 指示是否的高度[CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md)控件可以垂直方向上增加到功能区行的高度。  
  
```  
virtual BOOL CanBeStretched();
```  
  
### <a name="return-value"></a>返回值  
 始终返回 `FALSE`。  
  
### <a name="remarks"></a>备注  
  
##  <a name="cmfcribbonedit"></a>CMFCRibbonEdit::CMFCRibbonEdit  
 构造[CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md)对象。  
  
```  
CMFCRibbonEdit(
    UINT nID,  
    int nWidth,  
    LPCTSTR lpszLabel = NULL,  
    int nImage = -1);

CMFCRibbonEdit();
```  
  
### <a name="parameters"></a>参数  
 [in] `nID`  
 命令 ID`CMFCRibbonEdit`控件。  
  
 [in] `nWidth`  
 宽度 （像素） 的文本框中`CMFCRibbonEdit`控件。  
  
 [in] `lpszLabel`  
 标签`CMFCRibbonEdit`控件。  
  
 [in] `nImage`  
 要使用的小图像索引`CMFCRibbonEdit`控件。 由父功能区类别进行维护的较小的图像的集合。  
  
### <a name="remarks"></a>备注  
 `CMFCRibbonEdit`控件不使用较大的图像。  
  
##  <a name="copyfrom"></a>CMFCRibbonEdit::CopyFrom  
 将指定的状态复制[CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md)对象与当前[CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md)对象。  
  
```  
virtual void CopyFrom(const CMFCRibbonBaseElement& src);
```  
  
### <a name="parameters"></a>参数  
 [in] `src`  
 源 `CMFCRibbonEdit` 对象。  
  
### <a name="remarks"></a>备注  
 `src`参数的类型必须为`CMFCRibbonEdit`。  
  
##  <a name="createedit"></a>CMFCRibbonEdit::CreateEdit  
 创建一个新文本框[CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md)对象。  
  
```  
virtual CMFCRibbonRichEditCtrl* CreateEdit(
    CWnd* pWndParent,  
    DWORD dwEditStyle);
```  
  
### <a name="parameters"></a>参数  
 [in] `pWndParent`  
 指向的父窗口的指针`CMFCRibbonEdit`对象。  
  
 [in] `dwEditStyle`  
 指定文本框中的样式。 您可以组合使用备注部分中列出的窗口样式[编辑控件样式](http://msdn.microsoft.com/library/windows/desktop/bb775464)Windows SDK 中介绍。  
  
### <a name="return-value"></a>返回值  
 新的文本框中，如果此方法已成功，则指向的指针否则为`NULL`。  
  
### <a name="remarks"></a>备注  
 重写此方法在派生类中创建一个自定义文本框中。  
  
 您可以将应用以下[窗口样式](../../mfc/reference/window-styles.md)的文本框中︰  
  
- **WS_CHILD**  
  
- **WS_VISIBLE**  
  
- **WS_DISABLED**  
  
- **WS_GROUP**  
  
- **WS_TABSTOP**  
  
##  <a name="destroyctrl"></a>CMFCRibbonEdit::DestroyCtrl  
 销毁[CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md)对象。  
  
```  
virtual void DestroyCtrl();
```  
  
### <a name="remarks"></a>备注  
  
##  <a name="dropdownlist"></a>CMFCRibbonEdit::DropDownList  
 下拉列表框。  
  
```  
virtual void DropDownList();
```  
  
### <a name="remarks"></a>备注  
 默认情况下此方法没有任何效果。 重写此方法以下拉列表框。  
  
##  <a name="enablespinbuttons"></a>CMFCRibbonEdit::EnableSpinButtons  
 启用并设置文本框的数值调节钮的范围。  
  
```  
void EnableSpinButtons(
    int nMin,  
    int nMax);
```  
  
### <a name="parameters"></a>参数  
 [in] `nMin`  
 数值调节钮的最小值。  
  
 [in] `nMax`  
 数值调节钮的最大值。  
  
### <a name="remarks"></a>备注  
 数值调节钮显示向上和向下箭头并使用户能够浏览一组固定的值。  
  
##  <a name="getcompactsize"></a>CMFCRibbonEdit::GetCompactSize  
 检索的压缩大小[CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md)对象。  
  
```  
virtual CSize GetCompactSize(CDC* pDC);
```  
  
### <a name="parameters"></a>参数  
 [in] `pDC`  
 指向设备上下文指针`CMFCRibbonEdit`对象。  
  
### <a name="return-value"></a>返回值  
 尺寸紧凑`CMFCRibbonEdit`对象。  
  
### <a name="remarks"></a>备注  
  
##  <a name="getedittext"></a>CMFCRibbonEdit::GetEditText  
 检索在文本框中的文本。  
  
```  
CString GetEditText() const;  
```  
  
### <a name="return-value"></a>返回值  
 中的文本框的文本。  
  
### <a name="remarks"></a>备注  
  
##  <a name="getintermediatesize"></a>CMFCRibbonEdit::GetIntermediateSize  
 检索的中间大小[CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md)对象。  
  
```  
virtual CSize GetIntermediateSize(CDC* pDC);
```  
  
### <a name="parameters"></a>参数  
 [in] `pDC`  
 指向设备上下文指针`CMFCRibbonEdit`对象。  
  
### <a name="return-value"></a>返回值  
 中间的大小`CMFCRibbonEdit`对象。  
  
### <a name="remarks"></a>备注  
  
##  <a name="gettextalign"></a>CMFCRibbonEdit::GetTextAlign  
 检索文本框中文本的对齐方式。  
  
```  
int GetTextAlign() const;  
```  
  
### <a name="return-value"></a>返回值  
 文本对齐方式的枚举值。 请参阅备注部分中有关可能的值。  
  
### <a name="remarks"></a>备注  
 返回的值是下面的编辑控件样式之一︰  
  
- **ES_LEFT**为左对齐  
  
- **ES_CENTER**为居中对齐  
  
- **ES_RIGHT**为右对齐  
  
 有关这些样式的详细信息，请参阅[编辑控件样式](http://msdn.microsoft.com/library/windows/desktop/bb775464)。  
  
##  <a name="getwidth"></a>CMFCRibbonEdit::GetWidth  
 检索的宽度，以像素为单位的[CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md)控件。  
  
```  
int GetWidth(BOOL bInFloatyMode = FALSE) const;  
```  
  
### <a name="parameters"></a>参数  
 [in] `bInFloatyMode`  
 `TRUE`如果`CMFCRibbonEdit`控件是否处于浮动模式; 否则为`FALSE`。  
  
### <a name="return-value"></a>返回值  
 宽度，以像素为单位的`CMFCRibbonEdit`控件。  
  
### <a name="remarks"></a>备注  
  
##  <a name="hascompactmode"></a>CMFCRibbonEdit::HasCompactMode  
 指示是否显示大小调整为[CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md)控件均可以是 compact。  
  
```  
virtual BOOL HasCompactMode() const;  
```  
  
### <a name="return-value"></a>返回值  
 始终返回 `TRUE`。  
  
### <a name="remarks"></a>备注  
 默认情况下此方法始终返回`TRUE`。 重写此方法以指示是否可以压缩的显示大小。  
  
##  <a name="hasfocus"></a>CMFCRibbonEdit::HasFocus  
 指示是否[CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md)控件具有焦点。  
  
```  
virtual BOOL HasFocus() const;  
```  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果`CMFCRibbonEdit`控件具有焦点; 否则为`FALSE`。  
  
### <a name="remarks"></a>备注  
  
##  <a name="haslargemode"></a>CMFCRibbonEdit::HasLargeMode  
 指示是否显示大小调整为[CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md)控件可能很大。  
  
```  
virtual BOOL HasLargeMode() const;  
```  
  
### <a name="return-value"></a>返回值  
 始终返回 `FALSE`。  
  
### <a name="remarks"></a>备注  
 默认情况下此方法始终返回`FALSE`。 重写此方法以指示是否显示大小可能会大。  
  
##  <a name="hasspinbuttons"></a>CMFCRibbonEdit::HasSpinButtons  
 指示文本框是否具有数值调节钮。  
  
```  
virtual BOOL HasSpinButtons() const;  
```  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果文本框具有数值调节钮;否则为`FALSE`。  
  
### <a name="remarks"></a>备注  
  
##  <a name="ishighlighted"></a>CMFCRibbonEdit::IsHighlighted  
 指示是否[CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md)突出显示控件。  
  
```  
virtual BOOL IsHighlighted() const;  
```  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果`CMFCRibbonEdit`控件是突出显示; 否则为`FALSE`。  
  
### <a name="remarks"></a>备注  
  
##  <a name="onafterchangerect"></a>CMFCRibbonEdit::OnAfterChangeRect  
 由框架调用时的显示矩形的尺寸[CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md)控制更改。  
  
```  
virtual void OnAfterChangeRect(CDC* pDC);
```  
  
### <a name="parameters"></a>参数  
 [in] `pDC`  
 指向设备上下文指针`CMFCRibbonEdit`控件。  
  
### <a name="remarks"></a>备注  
  
##  <a name="ondraw"></a>CMFCRibbonEdit::OnDraw  
 由框架调用以绘制[CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md)控件。  
  
```  
virtual void OnDraw(CDC* pDC);
```  
  
### <a name="parameters"></a>参数  
 [in] `pDC`  
 指向设备上下文指针`CMFCRibbonEdit`控件。  
  
### <a name="remarks"></a>备注  
  
##  <a name="ondrawlabelandimage"></a>CMFCRibbonEdit::OnDrawLabelAndImage  
 由框架调用以绘制标签和图像的[CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md)控件。  
  
```  
virtual void OnDrawLabelAndImage(CDC* pDC);
```  
  
### <a name="parameters"></a>参数  
 [in] `pDC`  
 指向设备上下文指针`CMFCRibbonEdit`控件。  
  
### <a name="remarks"></a>备注  
  
##  <a name="ondrawonlist"></a>CMFCRibbonEdit::OnDrawOnList  
 由框架调用以绘制[CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md)命令列表框中的控件。  
  
```  
virtual void OnDrawOnList(
    CDC* pDC,  
    CString strText,  
    int nTextOffset,  
    CRect rect,  
    BOOL bIsSelected,  
    BOOL bHighlighted);
```  
  
### <a name="parameters"></a>参数  
 [in] `pDC`  
 指向设备上下文指针`CMFCRibbonEdit`控件。  
  
 [in] `strText`  
 显示文本[ ](../../mfc/reference/cmfcribbonedit-class.md "cmfcribbonedit class")。  
  
 [in] `nTextOffset`  
 以像素为单位，从列表框中显示文本到左侧的距离。  
  
 [in] `rect`  
 有关显示矩形`CMFCRibbonEdit`控件。  
  
 [in] `bIsSelected`  
 未使用此参数。  
  
 [in] `bHighlighted`  
 未使用此参数。  
  
### <a name="remarks"></a>备注  
 命令列表框中显示功能区控件，以使用户能够自定义快速访问工具栏。  
  
##  <a name="onenable"></a>CMFCRibbonEdit::OnEnable  
 由框架调用以启用或禁用[CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md)控件。  
  
```  
virtual void OnEnable(BOOL bEnable);
```  
  
### <a name="parameters"></a>参数  
 [in] `bEnable`  
 `TRUE`若要启用控件;`FALSE`要禁用控件。  
  
### <a name="remarks"></a>备注  
  
##  <a name="onhighlight"></a>CMFCRibbonEdit::OnHighlight  
 当鼠标指针进入或离开的边界由框架调用[CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md)控件。  
  
```  
virtual void OnHighlight(BOOL bHighlight);
```  
  
### <a name="parameters"></a>参数  
 [in] `bHighlight`  
 `TRUE`如果指针的界限内`CMFCRibbonEdit`控件的指针; 否则为`FALSE`。  
  
### <a name="remarks"></a>备注  
  
##  <a name="onkey"></a>CMFCRibbonEdit::OnKey  
 由框架调用，当用户按快捷键提示和[CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md)控件具有焦点。  
  
```  
virtual BOOL OnKey(BOOL bIsMenuKey);
```  
  
### <a name="parameters"></a>参数  
 [in] `bIsMenuKey`  
 `TRUE`如果快捷键提示会显示一个弹出菜单;否则为`FALSE`。  
  
### <a name="return-value"></a>返回值  
 如果已处理事件，则 `TRUE`，否则为 `FALSE`。  
  
### <a name="remarks"></a>备注  
  
##  <a name="onlbuttondown"></a>CMFCRibbonEdit::OnLButtonDown  
 由框架调用以更新[CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md)控制当用户按鼠标左键在控件上。  
  
```  
virtual void OnLButtonDown(CPoint point);
```  
  
### <a name="parameters"></a>参数  
 [in] `point`  
 未使用此参数。  
  
### <a name="remarks"></a>备注  
  
##  <a name="onlbuttonup"></a>CMFCRibbonEdit::OnLButtonUp  
 在用户释放鼠标左键时由框架调用。  
  
```  
virtual void OnLButtonUp(CPoint point);
```  
  
### <a name="parameters"></a>参数  
 [in] `point`  
 未使用此参数。  
  
### <a name="remarks"></a>备注  
  
##  <a name="onrtlchanged"></a>CMFCRibbonEdit::OnRTLChanged  
 由框架调用以更新[CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md)控制布局时更改方向。  
  
```  
virtual void OnRTLChanged(BOOL bIsRTL);
```  
  
### <a name="parameters"></a>参数  
 [in] `bIsRTL`  
 `TRUE`如果布局，则从右到左;`FALSE`如果是从左到右的布局。  
  
### <a name="remarks"></a>备注  
  
##  <a name="onshow"></a>CMFCRibbonEdit::OnShow  
 由框架调用以显示或隐藏[CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md)控件。  
  
```  
virtual void OnShow(BOOL bShow);
```  
  
### <a name="parameters"></a>参数  
 [in] `bShow`  
 `TRUE`若要显示的控件;`FALSE`将隐藏该控件。  
  
### <a name="remarks"></a>备注  
  
##  <a name="redraw"></a>CMFCRibbonEdit::Redraw  
 更新的显示[CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md)控件。  
  
```  
virtual void Redraw();
```  
  
### <a name="remarks"></a>备注  
 此方法将重新绘制的显示矩形`CMFCRibbonEdit`对象通过间接调用[CWnd::RedrawWindow](http://msdn.microsoft.com/library/windows/desktop/dd162911)与`RDW_INVALIDATE`， `RDW_ERASE`，和`RDW_UPDATENOW`标记集。  
  
##  <a name="setaccdata"></a>CMFCRibbonEdit::SetACCData  
 设置的可访问性数据[CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md)对象。  
  
```  
virtual BOOL SetACCData(
    CWnd* pParent,  
    CAccessibilityData& data);
```  
  
### <a name="parameters"></a>参数  
 `pParent`  
 父窗口的指针`CMFCRibbonEdit`对象。  
  
 `data`  
 可访问性数据`CMFCRibbonEdit`对象。  
  
### <a name="return-value"></a>返回值  
 始终返回 `TRUE`。  
  
### <a name="remarks"></a>备注  
  
##  <a name="setedittext"></a>CMFCRibbonEdit::SetEditText  
 在文本框中设置的文本。  
  
```  
void SetEditText(CString strText);
```  
  
### <a name="parameters"></a>参数  
 [in] `strText`  
 文本框的文本。  
  
##  <a name="settextalign"></a>CMFCRibbonEdit::SetTextAlign  
 设置文本框中的文本对齐方式。  
  
```  
void SetTextAlign(int nAlign);
```  
  
### <a name="parameters"></a>参数  
 [in] `nAlign`  
 文本对齐方式的枚举值。 请参阅备注部分中有关可能的值。  
  
### <a name="remarks"></a>备注  
 该参数`nAlign`是一个以下编辑控件样式︰  
  
- **ES_LEFT**为左对齐  
  
- **ES_CENTER**为居中对齐  
  
- **ES_RIGHT**为右对齐  
  
 有关这些样式的详细信息，请参阅[编辑控件样式](http://msdn.microsoft.com/library/windows/desktop/bb775464)。  
  
##  <a name="setwidth"></a>CMFCRibbonEdit::SetWidth  
 设置文本框的宽度[CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md)控件。  
  
```  
void SetWidth(
    int nWidth,  
    BOOL bInFloatyMode = FALSE);
```  
  
### <a name="parameters"></a>参数  
 [in] `nWidth`  
 以像素为单位，在文本框的宽度。  
  
 `bInFloatyMode`  
 `TRUE`若要设置为浮动的模式; 宽度`FALSE`设置常规显示模式的宽度。  
  
### <a name="remarks"></a>备注  
 `CMFCRibbonEdit`在控件有两个宽度，具体取决于其显示模式︰ 浮动模式和常规显示模式。  
  
## <a name="see-also"></a>另请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [类](../../mfc/reference/mfc-classes.md)   
 [CMFCRibbonButton 类](../../mfc/reference/cmfcribbonbutton-class.md)   
 [CMFCRibbonBar 类](../../mfc/reference/cmfcribbonbar-class.md)
