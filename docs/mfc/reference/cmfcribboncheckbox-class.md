---
title: CMFC功能框类
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
ms.openlocfilehash: 089c8056afebef31ff98a435bf145566ae64fe1e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375255"
---
# <a name="cmfcribboncheckbox-class"></a>CMFC功能框类

`CMFCRibbonCheckBox` 类实现可添加到功能区面板、快速访问工具栏或弹出菜单的复选框。

## <a name="syntax"></a>语法

```
class CMFCRibbonCheckBox : public CMFCRibbonButton
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[CMFCRibbonCheckBox::CMFCRibbonCheckBox](#cmfcribboncheckbox)|构造函数。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CMFC 功能包包：：获取压缩大小](#getcompactsize)|（覆盖[CMFC 功能按钮：获取压缩大小](../../mfc/reference/cmfcribbonbutton-class.md#getcompactsize).）|
|[CMFC 功能包复选框：获取中间大小](#getintermediatesize)|（覆盖[CMFC 功能按钮：获取中间大小](../../mfc/reference/cmfcribbonbutton-class.md#getintermediatesize).）|
|[CMFC 功能检查框：获取常规大小](#getregularsize)|（覆盖[CMFC 功能按钮：获取常规大小](../../mfc/reference/cmfcribbonbutton-class.md#getregularsize).）|
|[CMFCRibbonCheckBox::IsDrawTooltipImage](#isdrawtooltipimage)|（重写 `CMFCRibbonButton::IsDrawTooltipImage`。）|
|[CMFCRibbonCheckBox::OnDraw](#ondraw)|（覆盖[CMFC 功能按钮：onDraw](../../mfc/reference/cmfcribbonbutton-class.md#ondraw).）|
|[CMFCRibbonCheckBox::OnDrawMenuImage](#ondrawmenuimage)|（覆盖[CMFC 功能基础元素：在DrawMenuImage.）](../../mfc/reference/cmfcribbonbaseelement-class.md#ondrawmenuimage)|
|[CMFCRibbonCheckBox::OnDrawOnList](#ondrawonlist)|（重写 `CMFCRibbonButton::OnDrawOnList`。）|
|[CMFCRibbonCheckBox::SetACCData](#setaccdata)|（覆盖[CMFC 功能按钮：设置ACC数据](../../mfc/reference/cmfcribbonbutton-class.md#setaccdata).）|

## <a name="remarks"></a>备注

若要在应用程序中使用 `CMFCRibbonCheckBox`，请向代码添加以下构造函数：

```
CMFCRibbonCheckBox (UINT nID, LPCTSTR lpszText)
```

*其中 nID*是复选框命令 ID，lpszText 是复选框的文本标签。 *lpszText*

您可以使用[CMFC 功能面板：：：添加](../../mfc/reference/cmfcribbonpanel-class.md#add)，将复选框添加到功能区面板中。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)

[CMFCRibbonButton](../../mfc/reference/cmfcribbonbutton-class.md)

[CMFCRibbonCheckBox](../../mfc/reference/cmfcribboncheckbox-class.md)

## <a name="requirements"></a>要求

**标题：** afxribboncheckbox.h

## <a name="cmfcribboncheckboxcmfcribboncheckbox"></a><a name="cmfcribboncheckbox"></a>CMFC功能框：CMFC功能框

功能区复选框对象的构造函数

```
CMFCRibbonCheckBox(
    UINT nID,
    LPCTSTR lpszText);
```

### <a name="parameters"></a>参数

*nID*<br/>
[在]指定命令 ID。

*lpszText*<br/>
[在]指定文本标签。

### <a name="return-value"></a>返回值

构造功能区复选框对象。

### <a name="example"></a>示例

下面的示例演示如何构造`CMFCRibbonCheckBox`类的对象。

[!code-cpp[NVC_MFC_RibbonApp#17](../../mfc/reference/codesnippet/cpp/cmfcribboncheckbox-class_1.cpp)]

## <a name="cmfcribboncheckboxgetcompactsize"></a><a name="getcompactsize"></a>CMFC 功能包包：：获取压缩大小

重写时，获取复选框的紧凑大小。

```
virtual CSize GetCompactSize(CDC* pDC);
```

### <a name="parameters"></a>参数

*pDC*<br/>
[在]指向与复选框关联的 CDC 的指针。

### <a name="return-value"></a>返回值

返回包含`CSize`该复选框的紧凑大小的对象。

### <a name="remarks"></a>备注

如果未重写，请返回复选框的中间大小。

## <a name="cmfcribboncheckboxgetintermediatesize"></a><a name="getintermediatesize"></a>CMFC 功能包复选框：获取中间大小

获取复选框的中间大小。

```
virtual CSize GetIntermediateSize(CDC* pDC);
```

### <a name="parameters"></a>参数

*pDC*<br/>
[在]指向与此复选框关联的 CDC 的指针。

### <a name="return-value"></a>返回值

`CSize`包含中间大小的复选框的对象。

### <a name="remarks"></a>备注

如果未重写，则将中间大小计算为默认复选框大小 （ `AFX_CHECK_BOX_DEFAULT_SIZE`） 加上文本大小加上边距。

## <a name="cmfcribboncheckboxgetregularsize"></a><a name="getregularsize"></a>CMFC 功能检查框：获取常规大小

获取复选框的常规大小。

```
virtual CSize GetRegularSize(CDC* pDC);
```

### <a name="parameters"></a>参数

*pDC*<br/>
[在]指向与此复选框关联的 CDC 对象的指针。

### <a name="return-value"></a>返回值

返回包含`CSize`常规大小的对象复选框。

### <a name="remarks"></a>备注

如果未重写，请返回复选框的中间大小。

## <a name="cmfcribboncheckboxisdrawtooltipimage"></a><a name="isdrawtooltipimage"></a>CMFC 功能框：：正在绘制工具提示图像

指示是否存在与复选框关联的工具提示图像。

```
virtual BOOL IsDrawTooltipImage() const;
```

### <a name="return-value"></a>返回值

如果存在与复选框关联的工具提示图像，则返回 TRUE;如果没有，则返回 FALSE。

### <a name="remarks"></a>备注

## <a name="cmfcribboncheckboxondraw"></a><a name="ondraw"></a>CMFC功能框：：开奖

框架调用使用指定的设备上下文绘制复选框。

```
virtual void OnDraw(CDC* pDC);
```

### <a name="parameters"></a>参数

*pDC*<br/>
[在]指向用于在其中绘制复选框的 CDC 的指针。

### <a name="remarks"></a>备注

## <a name="cmfcribboncheckboxondrawmenuimage"></a><a name="ondrawmenuimage"></a>CMFC功能框：：在DrawMenu图像

由框架调用为复选框绘制菜单图像。

```
virtual BOOL OnDrawMenuImage(CDC*, CRect);
```

### <a name="parameters"></a>参数

[在]*CDC&#42;*<br/>
指向与复选框关联的 CDC 的指针。

*CRect*<br/>
[在]指定`CRect`用于绘制菜单图像的矩形的对象。

### <a name="return-value"></a>返回值

如果绘制了图像，则返回 TRUE;如果未绘制，则返回 FALSE。

### <a name="remarks"></a>备注

如果未重写，则返回 FALSE。

## <a name="cmfcribboncheckboxondrawonlist"></a><a name="ondrawonlist"></a>CMFC功能框：：在画上列表

框架调用以在命令列表框中绘制复选框。

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
[在]指向要在其中绘制复选框的设备上下文的指针。

*斯特文本*<br/>
[在]显示文本。

*n文本偏移*<br/>
[在]从列表框左侧到显示文本的距离（以像素为单位）。

*矩形*<br/>
[在]复选框的显示矩形。

*bIs选择*<br/>
[在]如果选中该复选框，则为 TRUE，如果未选中，则为 FALSE。

*b 突出显示*<br/>
[在]如果突出显示该复选框，则为 TRUE，如果没有，则为 FALSE。

### <a name="remarks"></a>备注

## <a name="cmfcribboncheckboxsetaccdata"></a><a name="setaccdata"></a>CMFC功能框：：设置ACC数据

设置复选框的辅助功能数据。

```
virtual BOOL SetACCData(
    CWnd* pParent,
    CAccessibilityData& data);
```

### <a name="parameters"></a>参数

*p 父级*<br/>
复选框的父窗口。

*数据*<br/>
复选框的辅助功能数据。

### <a name="return-value"></a>返回值

始终返回 TRUE。

### <a name="remarks"></a>备注

默认情况下，此方法设置复选框的辅助功能数据，并且始终返回 TRUE。 重写此方法以设置可访问性数据并返回一个指示成功或失败的值。

## <a name="see-also"></a>另请参阅

[层次结构图表](../../mfc/hierarchy-chart.md)<br/>
[类](../../mfc/reference/mfc-classes.md)<br/>
[CMFCRibbonPanel 类](../../mfc/reference/cmfcribbonpanel-class.md)
