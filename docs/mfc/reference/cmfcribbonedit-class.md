---
title: CMFCRibbonEdit 类
ms.date: 11/04/2016
f1_keywords:
- CMFCRibbonEdit
- AFXRIBBONEDIT/CMFCRibbonEdit
- AFXRIBBONEDIT/CMFCRibbonEdit::CMFCRibbonEdit
- AFXRIBBONEDIT/CMFCRibbonEdit::CanBeStretched
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
helpviewer_keywords:
- CMFCRibbonEdit [MFC], CMFCRibbonEdit
- CMFCRibbonEdit [MFC], CanBeStretched
- CMFCRibbonEdit [MFC], CMFCRibbonEdit
- CMFCRibbonEdit [MFC], CopyFrom
- CMFCRibbonEdit [MFC], CreateEdit
- CMFCRibbonEdit [MFC], DestroyCtrl
- CMFCRibbonEdit [MFC], DropDownList
- CMFCRibbonEdit [MFC], EnableSpinButtons
- CMFCRibbonEdit [MFC], GetCompactSize
- CMFCRibbonEdit [MFC], GetEditText
- CMFCRibbonEdit [MFC], GetIntermediateSize
- CMFCRibbonEdit [MFC], GetTextAlign
- CMFCRibbonEdit [MFC], GetWidth
- CMFCRibbonEdit [MFC], HasCompactMode
- CMFCRibbonEdit [MFC], HasFocus
- CMFCRibbonEdit [MFC], HasLargeMode
- CMFCRibbonEdit [MFC], HasSpinButtons
- CMFCRibbonEdit [MFC], IsHighlighted
- CMFCRibbonEdit [MFC], OnAfterChangeRect
- CMFCRibbonEdit [MFC], OnDraw
- CMFCRibbonEdit [MFC], OnDrawLabelAndImage
- CMFCRibbonEdit [MFC], OnDrawOnList
- CMFCRibbonEdit [MFC], OnEnable
- CMFCRibbonEdit [MFC], OnHighlight
- CMFCRibbonEdit [MFC], OnKey
- CMFCRibbonEdit [MFC], OnLButtonDown
- CMFCRibbonEdit [MFC], OnLButtonUp
- CMFCRibbonEdit [MFC], OnRTLChanged
- CMFCRibbonEdit [MFC], OnShow
- CMFCRibbonEdit [MFC], Redraw
- CMFCRibbonEdit [MFC], SetACCData
- CMFCRibbonEdit [MFC], SetEditText
- CMFCRibbonEdit [MFC], SetTextAlign
- CMFCRibbonEdit [MFC], SetWidth
ms.assetid: 9b85f1f2-446b-454e-9af9-104fdad8a897
ms.openlocfilehash: ab621a05f9b658eee9babb14e257680fa95e0f96
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375180"
---
# <a name="cmfcribbonedit-class"></a>CMFCRibbonEdit 类

实现位于功能区栏上的编辑控件。

## <a name="syntax"></a>语法

```cpp
class CMFCRibbonEdit : public CMFCRibbonButton
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[CMFC 剪彩编辑：CMFC 剪彩编辑](#cmfcribbonedit)|构造 `CMFCRibbonEdit` 对象。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CMFC 剪彩编辑：可拉伸](#canbestretched)|指示`CMFCRibbonEdit`控件的高度是否可以垂直增加到功能区行的高度。|
|[CMFC 剪彩编辑：CMFC 剪彩编辑](#cmfcribbonedit)|构造 `CMFCRibbonEdit` 对象。|
|[CMFC 剪彩编辑：：从](#copyfrom)|将指定`CMFCRibbonEdit`对象的状态复制到当前`CMFCRibbonEdit`对象。|
|[CMFC 功能编辑：创建编辑](#createedit)|为`CMFCRibbonEdit`对象创建新的文本框。|
|[CMFC剪发编辑：:D](#destroyctrl)|销毁`CMFCRibbonEdit`对象。|
|[CMFC 功能编辑：:DropDownlist](#dropdownlist)|下一个列表框。|
|[CMFC 功能编辑：：启用旋转按钮](#enablespinbuttons)|启用并设置文本框的旋转按钮的范围。|
|[CMFC 功能编辑：获取压缩尺寸](#getcompactsize)|检索`CFMCRibbonEdit`对象的紧凑大小。|
|[CMFC 功能编辑：获取编辑文本](#getedittext)|检索文本框中的文本。|
|[CMFC 功能编辑：获取中间大小](#getintermediatesize)|检索`CMFCRibbonEdit`对象的中间大小。|
|[CMFC 功能编辑：获取文本对齐](#gettextalign)|检索文本框中文本的对齐方式。|
|[CMFC 功能编辑：获取宽度](#getwidth)|检索`CMFCRibbonEdit`控件的宽度（以像素为单位）。|
|[CMFC 功能编辑：：具有压缩模式](#hascompactmode)|指示`CMFCRibbonEdit`控件的显示大小是否可以紧凑。|
|[CMFC 功能编辑：：有焦点](#hasfocus)|指示`CMFCRIbbonEdit`控件是否具有焦点。|
|[CMFC 功能编辑：具有大型模式](#haslargemode)|指示`CMFCRibbonEdit`控件的显示大小是否可以很大。|
|[CMFC 功能编辑：：哈斯平按钮](#hasspinbuttons)|指示文本框是否具有旋转按钮。|
|[CMFC 功能编辑：已突出显示](#ishighlighted)|指示`CMFCRibbonEdit`控件是否突出显示。|
|[CMFC 剪经：在转换后](#onafterchangerect)|当`CMFCRibbonEdit`控件的显示矩形的尺寸发生更改时，由框架调用。|
|[CMFC 剪彩编辑：OnDraw](#ondraw)|由框架调用以绘制`CMFCRibbonEdit`控件。|
|[CMFC 剪贴画：画条和图像](#ondrawlabelandimage)|由框架调用以绘制`CMFCRibbonEdit`控件的标签和图像。|
|[CMFC 剪彩编辑：在画上列表](#ondrawonlist)|由框架调用以`CMFCRibbonEdit`在命令列表框中绘制控件。|
|[CMFC 剪彩编辑：启用](#onenable)|由框架调用以启用或禁用`CMFCRibbonEdit`控件。|
|[CMFC 剪彩编辑：：上高亮显示](#onhighlight)|当指针进入或离开`CMFCRibbonEdit`控件的边界时，由框架调用。|
|[CMFC 剪彩编辑：：打开键](#onkey)|当用户按下键尖并且`CMFCRibbonEdit`控件具有焦点时，由框架调用。|
|[CMFC 剪彩编辑：：打开按钮](#onlbuttondown)|当用户按下控件上的鼠标左键`CMFCRibbonEdit`时，框架调用以更新控件。|
|[CMFC 剪接编辑：：OnLButtonUp](#onlbuttonup)|当用户释放鼠标左键时由框架调用。|
|[CMFC 剪彩编辑：：打开](#onrtlchanged)|由框架调用，`CMFCRibbonEdit`以在布局更改方向时更新控件。|
|[CMFC 剪彩编辑：在展会上](#onshow)|由框架调用以显示或隐藏`CMFCRibbonEdit`控件。|
|[CMFC 剪彩编辑：重绘](#redraw)|更新控件的`CMFCRibbonEdit`显示。|
|[CMFC 功能编辑：设置ACC数据](#setaccdata)|设置`CMFCRibbonEdit`对象的辅助功能数据。|
|[CMFC 功能编辑：：设置编辑文本](#setedittext)|在文本框中设置文本。|
|[CMFC 剪彩编辑：：设置文本对齐](#settextalign)|设置文本框的文本对齐方式。|
|[CMFC 功能编辑：：设置宽度](#setwidth)|设置控件的文本框的`CMFCRibbonEdit`宽度。|

## <a name="remarks"></a>备注

## <a name="example"></a>示例

下面的示例演示如何构造`CMFCRibbonEdit`对象、在编辑控件旁边显示旋转按钮以及设置编辑控件的文本。 此代码段是 MS [Office 2007 演示示例](../../overview/visual-cpp-samples.md)的一部分。

[!code-cpp[NVC_MFC_MSOffice2007Demo#7](../../mfc/reference/codesnippet/cpp/cmfcribbonedit-class_1.cpp)]

## <a name="requirements"></a>要求

**标题：** afxRibbonEdit.h

## <a name="cmfcribboneditcanbestretched"></a><a name="canbestretched"></a>CMFC 剪彩编辑：可拉伸

指示[CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md)控件的高度是否可以垂直增加到功能区行的高度。

```cpp
virtual BOOL CanBeStretched();
```

### <a name="return-value"></a>返回值

始终返回 FALSE。

### <a name="remarks"></a>备注

## <a name="cmfcribboneditcmfcribbonedit"></a><a name="cmfcribbonedit"></a>CMFC 剪彩编辑：CMFC 剪彩编辑

构造[CMFC 功能编辑](../../mfc/reference/cmfcribbonedit-class.md)对象。

```cpp
CMFCRibbonEdit(
    UINT nID,
    int nWidth,
    LPCTSTR lpszLabel = NULL,
    int nImage = -1);

CMFCRibbonEdit();
```

### <a name="parameters"></a>参数

*nID*<br/>
[在]控件的命令`CMFCRibbonEdit`ID。

*n 宽度*<br/>
[在]`CMFCRibbonEdit`控件的文本框的宽度（以像素为单位）。

*lpszLabel*<br/>
[在]控件的标签`CMFCRibbonEdit`。

*n图像*<br/>
[在]用于控件的小图像的`CMFCRibbonEdit`索引。 小图像的集合由父功能区类别维护。

### <a name="remarks"></a>备注

控件`CMFCRibbonEdit`不使用大图像。

## <a name="cmfcribboneditcopyfrom"></a><a name="copyfrom"></a>CMFC 剪彩编辑：：从

将指定的[CMFC 功能编辑](../../mfc/reference/cmfcribbonedit-class.md)对象的状态复制到当前[CMFC 功能编辑](../../mfc/reference/cmfcribbonedit-class.md)对象。

```cpp
virtual void CopyFrom(const CMFCRibbonBaseElement& src);
```

### <a name="parameters"></a>参数

*src*<br/>
[在]源`CMFCRibbonEdit`对象。

### <a name="remarks"></a>备注

*src*参数的类型必须`CMFCRibbonEdit`为 。

## <a name="cmfcribboneditcreateedit"></a><a name="createedit"></a>CMFC 功能编辑：创建编辑

为[CMFC 功能编辑](../../mfc/reference/cmfcribbonedit-class.md)对象创建新的文本框。

```cpp
virtual CMFCRibbonRichEditCtrl* CreateEdit(
    CWnd* pWndParent,
    DWORD dwEditStyle);
```

### <a name="parameters"></a>参数

*pwnd 父级*<br/>
[在]指向对象的父窗口的`CMFCRibbonEdit`指针。

*dwEdit风格*<br/>
[在]指定文本框的样式。 您可以将"备注"部分中列出的窗口样式与 Windows SDK 中描述的[编辑控件样式](/windows/win32/Controls/edit-control-styles)相结合。

### <a name="return-value"></a>返回值

如果方法成功，则指向新文本框的指针;否则，NULL。

### <a name="remarks"></a>备注

重写派生类中的此方法以创建自定义文本框。

您可以将以下[窗口样式](../../mfc/reference/styles-used-by-mfc.md#window-styles)应用于文本框：

- **WS_CHILD**

- **WS_VISIBLE**

- **WS_DISABLED**

- **WS_GROUP**

- **WS_TABSTOP**

## <a name="cmfcribboneditdestroyctrl"></a><a name="destroyctrl"></a>CMFC剪发编辑：:D

销毁[CMFC 功能编辑](../../mfc/reference/cmfcribbonedit-class.md)对象。

```cpp
virtual void DestroyCtrl();
```

### <a name="remarks"></a>备注

## <a name="cmfcribboneditdropdownlist"></a><a name="dropdownlist"></a>CMFC 功能编辑：:DropDownlist

下一个列表框。

```cpp
virtual void DropDownList();
```

### <a name="remarks"></a>备注

默认情况下，此方法不执行任何操作。 重写此方法以下拉列表框。

## <a name="cmfcribboneditenablespinbuttons"></a><a name="enablespinbuttons"></a>CMFC 功能编辑：：启用旋转按钮

启用并设置文本框的旋转按钮的范围。

```cpp
void EnableSpinButtons(
    int nMin,
    int nMax);
```

### <a name="parameters"></a>参数

*nMin*<br/>
[在]旋转按钮的最小值。

*nMax*<br/>
[在]旋转按钮的最大值。

### <a name="remarks"></a>备注

旋转按钮显示向上和向下箭头，使用户能够通过一组固定的值移动。

## <a name="cmfcribboneditgetcompactsize"></a><a name="getcompactsize"></a>CMFC 功能编辑：获取压缩尺寸

检索[CMFC 功能编辑](../../mfc/reference/cmfcribbonedit-class.md)对象的紧凑大小。

```cpp
virtual CSize GetCompactSize(CDC* pDC);
```

### <a name="parameters"></a>参数

*pDC*<br/>
[在]指向`CMFCRibbonEdit`对象的设备上下文。

### <a name="return-value"></a>返回值

`CMFCRibbonEdit`对象的紧凑大小。

### <a name="remarks"></a>备注

## <a name="cmfcribboneditgetedittext"></a><a name="getedittext"></a>CMFC 功能编辑：获取编辑文本

检索文本框中的文本。

```cpp
CString GetEditText() const;
```

### <a name="return-value"></a>返回值

文本框中的文本。

### <a name="remarks"></a>备注

## <a name="cmfcribboneditgetintermediatesize"></a><a name="getintermediatesize"></a>CMFC 功能编辑：获取中间大小

检索[CMFC 功能编辑](../../mfc/reference/cmfcribbonedit-class.md)对象的中间大小。

```cpp
virtual CSize GetIntermediateSize(CDC* pDC);
```

### <a name="parameters"></a>参数

*pDC*<br/>
[在]指向`CMFCRibbonEdit`对象的设备上下文。

### <a name="return-value"></a>返回值

`CMFCRibbonEdit`对象的中间大小。

### <a name="remarks"></a>备注

## <a name="cmfcribboneditgettextalign"></a><a name="gettextalign"></a>CMFC 功能编辑：获取文本对齐

检索文本框中文本的对齐方式。

```cpp
int GetTextAlign() const;
```

### <a name="return-value"></a>返回值

文本对齐枚举值。 有关可能的值，请参阅备注部分。

### <a name="remarks"></a>备注

返回的值是以下编辑控件样式之一：

- **用于**左对齐ES_LEFT

- **用于中心对齐的ES_CENTER**

- **ES_RIGHT，** 用于正确对齐

有关这些样式的详细信息，请参阅[编辑控件样式](/windows/win32/Controls/edit-control-styles)。

## <a name="cmfcribboneditgetwidth"></a><a name="getwidth"></a>CMFC 功能编辑：获取宽度

检索[CMFC 功能编辑](../../mfc/reference/cmfcribbonedit-class.md)控件的宽度（以像素为单位）。

```cpp
int GetWidth(BOOL bInFloatyMode = FALSE) const;
```

### <a name="parameters"></a>参数

*bInFloatyMode*<br/>
[在]如果`CMFCRibbonEdit`控件处于浮动模式，则为 TRUE;否则，FALSE。

### <a name="return-value"></a>返回值

控件的`CMFCRibbonEdit`宽度（以像素为单位）。

### <a name="remarks"></a>备注

## <a name="cmfcribbonedithascompactmode"></a><a name="hascompactmode"></a>CMFC 功能编辑：：具有压缩模式

指示[CMFC 功能编辑](../../mfc/reference/cmfcribbonedit-class.md)控件的显示大小是否可以紧凑。

```cpp
virtual BOOL HasCompactMode() const;
```

### <a name="return-value"></a>返回值

始终返回 TRUE。

### <a name="remarks"></a>备注

默认情况下，此方法始终返回 TRUE。 重写此方法以指示显示大小是否可以紧凑。

## <a name="cmfcribbonedithasfocus"></a><a name="hasfocus"></a>CMFC 功能编辑：：有焦点

指示[CMFC 功能编辑](../../mfc/reference/cmfcribbonedit-class.md)控件是否有焦点。

```cpp
virtual BOOL HasFocus() const;
```

### <a name="return-value"></a>返回值

如果控件具有`CMFCRibbonEdit`焦点，则为 TRUE;否则 FALSE。

### <a name="remarks"></a>备注

## <a name="cmfcribbonedithaslargemode"></a><a name="haslargemode"></a>CMFC 功能编辑：具有大型模式

指示[CMFC 功能编辑](../../mfc/reference/cmfcribbonedit-class.md)控件的显示大小是否较大。

```cpp
virtual BOOL HasLargeMode() const;
```

### <a name="return-value"></a>返回值

始终返回 FALSE。

### <a name="remarks"></a>备注

默认情况下，此方法始终返回 FALSE。 重写此方法以指示显示大小是否可以大。

## <a name="cmfcribbonedithasspinbuttons"></a><a name="hasspinbuttons"></a>CMFC 功能编辑：：哈斯平按钮

指示文本框是否具有旋转按钮。

```cpp
virtual BOOL HasSpinButtons() const;
```

### <a name="return-value"></a>返回值

如果文本框具有旋转按钮，则为 TRUE;否则 FALSE。

### <a name="remarks"></a>备注

## <a name="cmfcribboneditishighlighted"></a><a name="ishighlighted"></a>CMFC 功能编辑：已突出显示

指示是否突出显示[了 CMFC 功能编辑](../../mfc/reference/cmfcribbonedit-class.md)控件。

```cpp
virtual BOOL IsHighlighted() const;
```

### <a name="return-value"></a>返回值

如果控件突出显示`CMFCRibbonEdit`，则为 TRUE;如果控件突出显示，则为 TRUE。否则 FALSE。

### <a name="remarks"></a>备注

## <a name="cmfcribboneditonafterchangerect"></a><a name="onafterchangerect"></a>CMFC 剪经：在转换后

当[CMFC 功能编辑](../../mfc/reference/cmfcribbonedit-class.md)控件的显示矩形的尺寸发生更改时，由框架调用。

```cpp
virtual void OnAfterChangeRect(CDC* pDC);
```

### <a name="parameters"></a>参数

*pDC*<br/>
[在]指向`CMFCRibbonEdit`控件的设备上下文。

### <a name="remarks"></a>备注

## <a name="cmfcribboneditondraw"></a><a name="ondraw"></a>CMFC 剪彩编辑：OnDraw

由框架调用以绘制[CMFC 功能区编辑](../../mfc/reference/cmfcribbonedit-class.md)控件。

```cpp
virtual void OnDraw(CDC* pDC);
```

### <a name="parameters"></a>参数

*pDC*<br/>
[在]指向`CMFCRibbonEdit`控件的设备上下文。

### <a name="remarks"></a>备注

## <a name="cmfcribboneditondrawlabelandimage"></a><a name="ondrawlabelandimage"></a>CMFC 剪贴画：画条和图像

由框架调用，以绘制[CMFC 功能编辑](../../mfc/reference/cmfcribbonedit-class.md)控件的标签和图像。

```cpp
virtual void OnDrawLabelAndImage(CDC* pDC);
```

### <a name="parameters"></a>参数

*pDC*<br/>
[在]指向`CMFCRibbonEdit`控件的设备上下文。

### <a name="remarks"></a>备注

## <a name="cmfcribboneditondrawonlist"></a><a name="ondrawonlist"></a>CMFC 剪彩编辑：在画上列表

由框架调用以在命令列表框中绘制[CMFCRibbonEdit 控件](../../mfc/reference/cmfcribbonedit-class.md)。

```cpp
virtual void OnDrawOnList(
    CDC* pDC,
    CString strText,
    int nTextOffset,
    CRect rect,
    BOOL bIsSelected,
    BOOL bHighlighted);
```

### <a name="parameters"></a>参数

*pDC*<br/>
[在]指向`CMFCRibbonEdit`控件的设备上下文。

*斯特文本*<br/>
[在]显示文本[](../../mfc/reference/cmfcribbonedit-class.md "cmfcribbonedit 类")。

*n文本偏移*<br/>
[在]从列表框左侧到显示文本的距离（以像素为单位）。

*矩形*<br/>
[在]控件的`CMFCRibbonEdit`显示矩形。

*bIs选择*<br/>
[在]不使用此参数。

*b 突出显示*<br/>
[在]不使用此参数。

### <a name="remarks"></a>备注

命令列表框显示功能区控件，使用户能够自定义快速访问工具栏。

## <a name="cmfcribboneditonenable"></a><a name="onenable"></a>CMFC 剪彩编辑：启用

由框架调用以启用或禁用[CMFC 功能编辑](../../mfc/reference/cmfcribbonedit-class.md)控件。

```cpp
virtual void OnEnable(BOOL bEnable);
```

### <a name="parameters"></a>参数

*b 启用*<br/>
[在]TRUE 以启用控件;FALSE 以禁用控件。

### <a name="remarks"></a>备注

## <a name="cmfcribboneditonhighlight"></a><a name="onhighlight"></a>CMFC 剪彩编辑：：上高亮显示

当指针进入或离开[CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md)控件的边界时，由框架调用。

```cpp
virtual void OnHighlight(BOOL bHighlight);
```

### <a name="parameters"></a>参数

*b 高光*<br/>
[在]如果指针位于控件的边界内，`CMFCRibbonEdit`则为 TRUE;如果指针位于控件的边界内，则为 TRUE。否则，FALSE。

### <a name="remarks"></a>备注

## <a name="cmfcribboneditonkey"></a><a name="onkey"></a>CMFC 剪彩编辑：：打开键

当用户按下钥匙尖和[CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md)控件具有焦点时，由框架调用。

```cpp
virtual BOOL OnKey(BOOL bIsMenuKey);
```

### <a name="parameters"></a>参数

*bIsMenu键*<br/>
[在]如果钥匙提示显示弹出式菜单，则为 TRUE;否则，FALSE。

### <a name="return-value"></a>返回值

如果事件已处理，则为 TRUE;否则，FALSE。

### <a name="remarks"></a>备注

## <a name="cmfcribboneditonlbuttondown"></a><a name="onlbuttondown"></a>CMFC 剪彩编辑：：打开按钮

当用户按下控件上的鼠标左键时，框架调用以更新[CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md)控件。

```cpp
virtual void OnLButtonDown(CPoint point);
```

### <a name="parameters"></a>参数

*点*<br/>
[在]不使用此参数。

### <a name="remarks"></a>备注

## <a name="cmfcribboneditonlbuttonup"></a><a name="onlbuttonup"></a>CMFC 剪接编辑：：OnLButtonUp

当用户释放鼠标左键时由框架调用。

```cpp
virtual void OnLButtonUp(CPoint point);
```

### <a name="parameters"></a>参数

*点*<br/>
[在]不使用此参数。

### <a name="remarks"></a>备注

## <a name="cmfcribboneditonrtlchanged"></a><a name="onrtlchanged"></a>CMFC 剪彩编辑：：打开

当布局更改方向时，框架调用以更新[CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md)控件。

```cpp
virtual void OnRTLChanged(BOOL bIsRTL);
```

### <a name="parameters"></a>参数

*比塞尔*<br/>
[在]如果布局从右到左，则为 TRUE;如果布局从右到左，则为 TRUE。如果布局从左到右，则 FALSE。

### <a name="remarks"></a>备注

## <a name="cmfcribboneditonshow"></a><a name="onshow"></a>CMFC 剪彩编辑：在展会上

由框架调用以显示或隐藏[CMFC 功能编辑](../../mfc/reference/cmfcribbonedit-class.md)控件。

```cpp
virtual void OnShow(BOOL bShow);
```

### <a name="parameters"></a>参数

*b显示*<br/>
[在]TRUE 以显示控件;FALSE 以隐藏控件。

### <a name="remarks"></a>备注

## <a name="cmfcribboneditredraw"></a><a name="redraw"></a>CMFC 剪彩编辑：重绘

更新[CMFC 功能编辑控件](../../mfc/reference/cmfcribbonedit-class.md)的显示。

```cpp
virtual void Redraw();
```

### <a name="remarks"></a>备注

此方法通过间接调用`CMFCRibbonEdit`[CWnd：：redrawWindow，](/windows/win32/api/winuser/nf-winuser-redrawwindow)并设置了RDW_INVALIDATE、RDW_ERASE和RDW_UPDATENOW标志，从而重绘对象的显示矩形。

## <a name="cmfcribboneditsetaccdata"></a><a name="setaccdata"></a>CMFC 功能编辑：设置ACC数据

设置[CMFC 功能编辑](../../mfc/reference/cmfcribbonedit-class.md)对象的辅助功能数据。

```cpp
virtual BOOL SetACCData(
    CWnd* pParent,
    CAccessibilityData& data);
```

### <a name="parameters"></a>参数

*p 父级*<br/>
指向`CMFCRibbonEdit`对象的父窗口。

*数据*<br/>
`CMFCRibbonEdit`对象的辅助功能数据。

### <a name="return-value"></a>返回值

始终返回 TRUE。

### <a name="remarks"></a>备注

## <a name="cmfcribboneditsetedittext"></a><a name="setedittext"></a>CMFC 功能编辑：：设置编辑文本

在文本框中设置文本。

```cpp
void SetEditText(CString strText);
```

### <a name="parameters"></a>参数

*斯特文本*<br/>
[在]文本框的文本。

## <a name="cmfcribboneditsettextalign"></a><a name="settextalign"></a>CMFC 剪彩编辑：：设置文本对齐

设置文本框的文本对齐方式。

```cpp
void SetTextAlign(int nAlign);
```

### <a name="parameters"></a>参数

*n对齐*<br/>
[在]文本对齐枚举值。 有关可能的值，请参阅备注部分。

### <a name="remarks"></a>备注

参数*nAlign*是以下编辑控件样式之一：

- 用于左对齐ES_LEFT

- 用于中心对齐的ES_CENTER

- 用于正确对齐的ES_RIGHT

有关这些样式的详细信息，请参阅[编辑控件样式](/windows/win32/Controls/edit-control-styles)。

## <a name="cmfcribboneditsetwidth"></a><a name="setwidth"></a>CMFC 功能编辑：：设置宽度

设置[CMFC 功能编辑](../../mfc/reference/cmfcribbonedit-class.md)控件的文本框的宽度。

```cpp
void SetWidth(
    int nWidth,
    BOOL bInFloatyMode = FALSE);
```

### <a name="parameters"></a>参数

*n 宽度*<br/>
[在]文本框的宽度（以像素为单位）。

*bInFloatyMode*<br/>
TRUE 设置为浮动模式的宽度;FALSE 设置为常规模式的宽度。

### <a name="remarks"></a>备注

控件`CMFCRibbonEdit`有两个宽度，具体取决于其显示模式：浮动模式和常规模式。

## <a name="see-also"></a>另请参阅

[层次结构图表](../../mfc/hierarchy-chart.md)<br/>
[类](../../mfc/reference/mfc-classes.md)<br/>
[CMFC 功能按钮类](../../mfc/reference/cmfcribbonbutton-class.md)<br/>
[CMFC剪条类](../../mfc/reference/cmfcribbonbar-class.md)
