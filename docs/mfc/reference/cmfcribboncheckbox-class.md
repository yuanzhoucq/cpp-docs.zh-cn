---
title: CMFCRibbonCheckBox 类 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 0b10004551a594d6f969ffaf7893cd2e7efe2d76
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46396542"
---
# <a name="cmfcribboncheckbox-class"></a>CMFCRibbonCheckBox 类

`CMFCRibbonCheckBox` 类实现可添加到功能区面板、快速访问工具栏或弹出菜单的复选框。

## <a name="syntax"></a>语法

```
class CMFCRibbonCheckBox : public CMFCRibbonButton
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[CMFCRibbonCheckBox::CMFCRibbonCheckBox](#cmfcribboncheckbox)|构造函数。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CMFCRibbonCheckBox::GetCompactSize](#getcompactsize)|(重写[cmfcribbonbutton:: Getcompactsize](../../mfc/reference/cmfcribbonbutton-class.md#getcompactsize)。)|
|[CMFCRibbonCheckBox::GetIntermediateSize](#getintermediatesize)|(重写[cmfcribbonbutton:: Getintermediatesize](../../mfc/reference/cmfcribbonbutton-class.md#getintermediatesize)。)|
|[CMFCRibbonCheckBox::GetRegularSize](#getregularsize)|(重写[cmfcribbonbutton:: Getregularsize](../../mfc/reference/cmfcribbonbutton-class.md#getregularsize)。)|
|[CMFCRibbonCheckBox::IsDrawTooltipImage](#isdrawtooltipimage)|（重写 `CMFCRibbonButton::IsDrawTooltipImage`。）|
|[CMFCRibbonCheckBox::OnDraw](#ondraw)|(重写[cmfcribbonbutton:: Ondraw](../../mfc/reference/cmfcribbonbutton-class.md#ondraw)。)|
|[CMFCRibbonCheckBox::OnDrawMenuImage](#ondrawmenuimage)|(重写[cmfcribbonbaseelement:: Ondrawmenuimage](../../mfc/reference/cmfcribbonbaseelement-class.md#ondrawmenuimage)。)|
|[CMFCRibbonCheckBox::OnDrawOnList](#ondrawonlist)|（重写 `CMFCRibbonButton::OnDrawOnList`。）|
|[CMFCRibbonCheckBox::SetACCData](#setaccdata)|(重写[cmfcribbonbutton:: Setaccdata](../../mfc/reference/cmfcribbonbutton-class.md#setaccdata)。)|

## <a name="remarks"></a>备注

若要在应用程序中使用 `CMFCRibbonCheckBox`，请向代码添加以下构造函数：

```
CMFCRibbonCheckBox (UINT nID, LPCTSTR lpszText)
```
其中*nID*的复选框命令 id 并*lpszText*是复选框的文本标签。

可以通过向功能区面板添加复选框[cmfcribbonpanel:: Add](../../mfc/reference/cmfcribbonpanel-class.md#add)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)

[CMFCRibbonButton](../../mfc/reference/cmfcribbonbutton-class.md)

[CMFCRibbonCheckBox](../../mfc/reference/cmfcribboncheckbox-class.md)

## <a name="requirements"></a>要求

**标头：** afxribboncheckbox.h

##  <a name="cmfcribboncheckbox"></a>  CMFCRibbonCheckBox::CMFCRibbonCheckBox

功能区复选框对象的构造函数

```
CMFCRibbonCheckBox(
    UINT nID,
    LPCTSTR lpszText);
```

### <a name="parameters"></a>参数

*nID*<br/>
[in]指定命令 id。

*lpszText*<br/>
[in]指定文本标签。

### <a name="return-value"></a>返回值

构造一个功能区复选框对象。

### <a name="example"></a>示例

下面的示例演示如何构造的对象`CMFCRibbonCheckBox`类。

[!code-cpp[NVC_MFC_RibbonApp#17](../../mfc/reference/codesnippet/cpp/cmfcribboncheckbox-class_1.cpp)]

##  <a name="getcompactsize"></a>  CMFCRibbonCheckBox::GetCompactSize

重写时，获取复选框的压缩大小。

```
virtual CSize GetCompactSize(CDC* pDC);
```

### <a name="parameters"></a>参数

*pDC*<br/>
[in]指向与复选框相关联的 CDC。

### <a name="return-value"></a>返回值

返回`CSize`对象，其中包含复选框的压缩大小。

### <a name="remarks"></a>备注

如果未重写时，返回复选框的中间大小。

##  <a name="getintermediatesize"></a>  CMFCRibbonCheckBox::GetIntermediateSize

获取中间复选框的大小。

```
virtual CSize GetIntermediateSize(CDC* pDC);
```

### <a name="parameters"></a>参数

*pDC*<br/>
[in]指向与此复选框相关联的 CDC。

### <a name="return-value"></a>返回值

一个`CSize`对象，其中包含中间复选框的大小。

### <a name="remarks"></a>备注

如果未重写，将计算默认复选框大小具有中间的大小 ( `AFX_CHECK_BOX_DEFAULT_SIZE`) 以及文本大小和边距。

##  <a name="getregularsize"></a>  CMFCRibbonCheckBox::GetRegularSize

获取复选框的常规大小。

```
virtual CSize GetRegularSize(CDC* pDC);
```

### <a name="parameters"></a>参数

*pDC*<br/>
[in]指向与此复选框关联的 CDC 对象指针。

### <a name="return-value"></a>返回值

返回`CSize`对象，其中包含复选框的常规大小。

### <a name="remarks"></a>备注

如果未重写时，返回复选框的中间大小。

##  <a name="isdrawtooltipimage"></a>  CMFCRibbonCheckBox::IsDrawTooltipImage

指示是否存在与复选框相关联的工具提示映像。

```
virtual BOOL IsDrawTooltipImage() const;
```

### <a name="return-value"></a>返回值

如果工具提示映像关联的复选框，或如果不是 FALSE，则返回 TRUE。

### <a name="remarks"></a>备注

##  <a name="ondraw"></a>  CMFCRibbonCheckBox::OnDraw

由框架调用以绘制复选框使用指定的设备上下文。

```
virtual void OnDraw(CDC* pDC);
```

### <a name="parameters"></a>参数

*pDC*<br/>
[in]指向要在其中绘制复选框 CDC。

### <a name="remarks"></a>备注

##  <a name="ondrawmenuimage"></a>  CMFCRibbonCheckBox::OnDrawMenuImage

由框架调用以绘制菜单图标的复选框。

```
virtual BOOL OnDrawMenuImage(CDC*, CRect);
```

### <a name="parameters"></a>参数

[in]*CDC** CDC 指向关联的复选框。

*CRect*<br/>
[in]一个`CRect`对象，它指定要在其中绘制的菜单图像的矩形。

### <a name="return-value"></a>返回值

如果已绘制图像，则为 TRUE 或 FALSE，如果不是返回。

### <a name="remarks"></a>备注

如果未重写，将返回 FALSE。

##  <a name="ondrawonlist"></a>  CMFCRibbonCheckBox::OnDrawOnList

由框架调用以绘制命令列表框中的复选框。

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
[in]指向要在其中绘制复选框的设备上下文指针。

*strText*<br/>
[in]显示文本。

*nTextOffset*<br/>
[in]以像素为单位，从左侧和右侧显示文本的列表框的距离。

*rect*<br/>
[in]复选框显示矩形。

*bIsSelected*<br/>
[in]如果此复选框处于选中状态，或如果不是 FALSE，则为 TRUE。

*bHighlighted*<br/>
[in]如果复选框为选中此选项，或如果不是 FALSE，则为 TRUE。

### <a name="remarks"></a>备注

##  <a name="setaccdata"></a>  CMFCRibbonCheckBox::SetACCData

设置复选框的可访问性数据。

```
virtual BOOL SetACCData(
    CWnd* pParent,
    CAccessibilityData& data);
```

### <a name="parameters"></a>参数

*pParent*<br/>
复选框的父窗口。

*data*<br/>
复选框可访问性数据。

### <a name="return-value"></a>返回值

始终返回 TRUE。

### <a name="remarks"></a>备注

默认情况下此方法设置复选框的可访问性数据，并始终返回 TRUE。 重写此方法以设置可访问性数据并返回一个指示成功或失败的值。

## <a name="see-also"></a>请参阅

[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[类](../../mfc/reference/mfc-classes.md)<br/>
[CMFCRibbonPanel 类](../../mfc/reference/cmfcribbonpanel-class.md)
