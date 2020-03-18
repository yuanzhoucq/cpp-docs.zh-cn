---
title: CMFCRibbonCheckBox 类
ms.date: 11/04/2016
f1_keywords:
- CMFCRibbonCheckBox
- AFXRIBBONCHECKBOX/CMFCRibbonCheckBox
- AFXRIBBONCHECKBOX/CMFCRibbonCheckBox::CMFCRibbonCheckBox
- AFXRIBBONCHECKBOX/CMFCRibbonCheckBox::GetCompactSize
- AFXRIBBONCHECKBOX/CMFCRibbonCheckBox::GetIntermediateSize
- AFXRIBBONCHECKBOX/CMFCRibbonCheckBox::GetRegularSize
- AFXRIBBONCHECKBOX/CMFCRibbonCheckBox::IsDrawTooltipImage
- AFXRIBBONCHECKBOX/CMFCRibbonCheckBox::OnDraw
- AFXRIBBONCHECKBOX/CMFCRibbonCheckBox::OnDrawMenuImage
- AFXRIBBONCHECKBOX/CMFCRibbonCheckBox::OnDrawOnList
- AFXRIBBONCHECKBOX/CMFCRibbonCheckBox::SetACCData
helpviewer_keywords:
- CMFCRibbonCheckBox [MFC], CMFCRibbonCheckBox
- CMFCRibbonCheckBox [MFC], GetCompactSize
- CMFCRibbonCheckBox [MFC], GetIntermediateSize
- CMFCRibbonCheckBox [MFC], GetRegularSize
- CMFCRibbonCheckBox [MFC], IsDrawTooltipImage
- CMFCRibbonCheckBox [MFC], OnDraw
- CMFCRibbonCheckBox [MFC], OnDrawMenuImage
- CMFCRibbonCheckBox [MFC], OnDrawOnList
- CMFCRibbonCheckBox [MFC], SetACCData
ms.assetid: 3a6c3891-c8d1-4af0-b954-7b9ab048782a
ms.openlocfilehash: a8048f860a2cce75c37a065cfdd2751141054f1b
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/17/2020
ms.locfileid: "79446241"
---
# <a name="cmfcribboncheckbox-class"></a>CMFCRibbonCheckBox 类

`CMFCRibbonCheckBox` 类实现可添加到功能区面板、快速访问工具栏或弹出菜单的复选框。

## <a name="syntax"></a>语法

```
class CMFCRibbonCheckBox : public CMFCRibbonButton
```

## <a name="members"></a>Members

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[CMFCRibbonCheckBox::CMFCRibbonCheckBox](#cmfcribboncheckbox)|构造函数。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CMFCRibbonCheckBox：： GetCompactSize](#getcompactsize)|（重写[CMFCRibbonButton：： GetCompactSize](../../mfc/reference/cmfcribbonbutton-class.md#getcompactsize)。）|
|[CMFCRibbonCheckBox：： GetIntermediateSize](#getintermediatesize)|（重写[CMFCRibbonButton：： GetIntermediateSize](../../mfc/reference/cmfcribbonbutton-class.md#getintermediatesize)。）|
|[CMFCRibbonCheckBox：： GetRegularSize](#getregularsize)|（重写[CMFCRibbonButton：： GetRegularSize](../../mfc/reference/cmfcribbonbutton-class.md#getregularsize)。）|
|[CMFCRibbonCheckBox::IsDrawTooltipImage](#isdrawtooltipimage)|（重写 `CMFCRibbonButton::IsDrawTooltipImage`。）|
|[CMFCRibbonCheckBox：： OnDraw](#ondraw)|（重写[CMFCRibbonButton：： OnDraw](../../mfc/reference/cmfcribbonbutton-class.md#ondraw)。）|
|[CMFCRibbonCheckBox：： OnDrawMenuImage](#ondrawmenuimage)|（重写[CMFCRibbonBaseElement：： OnDrawMenuImage](../../mfc/reference/cmfcribbonbaseelement-class.md#ondrawmenuimage)。）|
|[CMFCRibbonCheckBox::OnDrawOnList](#ondrawonlist)|（重写 `CMFCRibbonButton::OnDrawOnList`。）|
|[CMFCRibbonCheckBox：： SetACCData](#setaccdata)|（重写[CMFCRibbonButton：： SetACCData](../../mfc/reference/cmfcribbonbutton-class.md#setaccdata)。）|

## <a name="remarks"></a>备注

若要在应用程序中使用 `CMFCRibbonCheckBox`，请向代码添加以下构造函数：

```
CMFCRibbonCheckBox (UINT nID, LPCTSTR lpszText)
```

其中， *nID*是复选框命令 ID， *lpszText*是复选框的文本标签。

可以通过使用[CMFCRibbonPanel：： add](../../mfc/reference/cmfcribbonpanel-class.md#add)将复选框添加到功能区面板。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)

[CMFCRibbonButton](../../mfc/reference/cmfcribbonbutton-class.md)

[CMFCRibbonCheckBox](../../mfc/reference/cmfcribboncheckbox-class.md)

## <a name="requirements"></a>要求

**标头：** afxribboncheckbox

##  <a name="cmfcribboncheckbox"></a>CMFCRibbonCheckBox::CMFCRibbonCheckBox

功能区复选框对象的构造函数

```
CMFCRibbonCheckBox(
    UINT nID,
    LPCTSTR lpszText);
```

### <a name="parameters"></a>参数

*nID*<br/>
中指定命令 ID。

*lpszText*<br/>
中指定文本标签。

### <a name="return-value"></a>返回值

构造功能区复选框对象。

### <a name="example"></a>示例

下面的示例演示如何构造 `CMFCRibbonCheckBox` 类的对象。

[!code-cpp[NVC_MFC_RibbonApp#17](../../mfc/reference/codesnippet/cpp/cmfcribboncheckbox-class_1.cpp)]

##  <a name="getcompactsize"></a>CMFCRibbonCheckBox：： GetCompactSize

重写时，获取复选框的压缩大小。

```
virtual CSize GetCompactSize(CDC* pDC);
```

### <a name="parameters"></a>参数

*pDC*<br/>
中指向与此复选框关联的 CDC 的指针。

### <a name="return-value"></a>返回值

返回一个 `CSize` 对象，该对象包含复选框的压缩大小。

### <a name="remarks"></a>备注

如果未重写，则返回复选框的中间大小。

##  <a name="getintermediatesize"></a>CMFCRibbonCheckBox：： GetIntermediateSize

获取复选框的中间大小。

```
virtual CSize GetIntermediateSize(CDC* pDC);
```

### <a name="parameters"></a>参数

*pDC*<br/>
中指向与此复选框关联的 CDC 的指针。

### <a name="return-value"></a>返回值

包含复选框的中间大小的 `CSize` 对象。

### <a name="remarks"></a>备注

如果未重写，则将中间大小计算为默认复选框大小（`AFX_CHECK_BOX_DEFAULT_SIZE`）加上文本大小和边距。

##  <a name="getregularsize"></a>CMFCRibbonCheckBox：： GetRegularSize

获取复选框的常规大小。

```
virtual CSize GetRegularSize(CDC* pDC);
```

### <a name="parameters"></a>参数

*pDC*<br/>
中指向与此复选框关联的 CDC 对象的指针。

### <a name="return-value"></a>返回值

返回一个 `CSize` 对象，该对象包含复选框的正常大小。

### <a name="remarks"></a>备注

如果未重写，则返回复选框的中间大小。

##  <a name="isdrawtooltipimage"></a>CMFCRibbonCheckBox::IsDrawTooltipImage

指示是否存在与该复选框相关联的工具提示图像。

```
virtual BOOL IsDrawTooltipImage() const;
```

### <a name="return-value"></a>返回值

如果有与该复选框相关联的工具提示图像，则返回 TRUE; 否则返回 FALSE。

### <a name="remarks"></a>备注

##  <a name="ondraw"></a>CMFCRibbonCheckBox：： OnDraw

由框架调用，以使用指定的设备上下文绘制复选框。

```
virtual void OnDraw(CDC* pDC);
```

### <a name="parameters"></a>参数

*pDC*<br/>
中一个指针，指向要在其中绘制复选框的 CDC。

### <a name="remarks"></a>备注

##  <a name="ondrawmenuimage"></a>CMFCRibbonCheckBox：： OnDrawMenuImage

由框架调用以绘制复选框的菜单图像。

```
virtual BOOL OnDrawMenuImage(CDC*, CRect);
```

### <a name="parameters"></a>参数

中*CDC&#42;*<br/>
指向与此复选框关联的 CDC 的指针。

*CRect*<br/>
中一个 `CRect` 对象，该对象指定要在其中绘制菜单图像的矩形。

### <a name="return-value"></a>返回值

如果绘制图像，则返回 TRUE; 否则返回 FALSE。

### <a name="remarks"></a>备注

如果未重写，则返回 FALSE。

##  <a name="ondrawonlist"></a>CMFCRibbonCheckBox::OnDrawOnList

由框架调用，用于在命令列表框中绘制复选框。

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

*pDC*<br/>
中一个指针，指向要在其中绘制复选框的设备上下文。

*strText*<br/>
中显示文本。

*nTextOffset*<br/>
中从列表框左侧到显示文本的距离（以像素为单位）。

*rect*<br/>
中复选框的显示矩形。

*bIsSelected*<br/>
中如果选中此复选框，则为 TRUE; 否则为 FALSE。

*bHighlighted*<br/>
中如果突出显示复选框，则为 TRUE; 否则为 FALSE。

### <a name="remarks"></a>备注

##  <a name="setaccdata"></a>CMFCRibbonCheckBox：： SetACCData

设置复选框的辅助功能数据。

```
virtual BOOL SetACCData(
    CWnd* pParent,
    CAccessibilityData& data);
```

### <a name="parameters"></a>参数

*pParent*<br/>
复选框的父窗口。

*data*<br/>
复选框的辅助功能数据。

### <a name="return-value"></a>返回值

始终返回 TRUE。

### <a name="remarks"></a>备注

默认情况下，此方法设置复选框的可访问性数据，并始终返回 TRUE。 重写此方法以设置可访问性数据并返回一个指示成功或失败的值。

## <a name="see-also"></a>另请参阅

[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[类](../../mfc/reference/mfc-classes.md)<br/>
[CMFCRibbonPanel 类](../../mfc/reference/cmfcribbonpanel-class.md)
