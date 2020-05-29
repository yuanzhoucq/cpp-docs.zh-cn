---
title: CMFC 功能放大缩小字体功能 放大缩小字体功能
ms.date: 11/04/2016
f1_keywords:
- CMFCRibbonUndoButton
- AFXRIBBONUNDOBUTTON/CMFCRibbonUndoButton
- AFXRIBBONUNDOBUTTON/CMFCRibbonUndoButton::CMFCRibbonUndoButton
- AFXRIBBONUNDOBUTTON/CMFCRibbonUndoButton::AddUndoAction
- AFXRIBBONUNDOBUTTON/CMFCRibbonUndoButton::CleanUpUndoList
- AFXRIBBONUNDOBUTTON/CMFCRibbonUndoButton::GetActionNumber
- AFXRIBBONUNDOBUTTON/CMFCRibbonUndoButton::HasMenu
helpviewer_keywords:
- CMFCRibbonUndoButton [MFC], CMFCRibbonUndoButton
- CMFCRibbonUndoButton [MFC], AddUndoAction
- CMFCRibbonUndoButton [MFC], CleanUpUndoList
- CMFCRibbonUndoButton [MFC], GetActionNumber
- CMFCRibbonUndoButton [MFC], HasMenu
ms.assetid: 5c42adf7-871d-4239-901e-47ae7fb816fc
ms.openlocfilehash: 15cf93d39057f0e235779d47cf24d920d80a807d
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/22/2020
ms.locfileid: "81753493"
---
# <a name="cmfcribbonundobutton-class"></a>CMFC 功能放大缩小字体功能 放大缩小字体功能

类`CMFCRibbonUndoButton`实现包含最新用户命令的下拉列表按钮。 用户可以从下拉列表中选择一个或多个最新命令，以重做或撤消这些命令。

## <a name="syntax"></a>语法

```
class CMFCRibbonUndoButton : public CMFCRibbonGallery
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[CMFC 功能Undo按钮：：CMFC功能放大缩小字体功能](#cmfcribbonundobutton)|使用指定的命令`CMFCRibbonUndoButton`ID、文本标签和父对象的图像列表中的图像来构造新对象。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CMFC 功能Undo按钮：：添加UndoAction](#addundoaction)|向操作列表添加新操作。|
|[CMFC 功能整理按钮：：清除 Undo 列表](#cleanupundolist)|清除操作列表，这是下拉列表。|
|[CMFC 功能Undo按钮：获取操作编号](#getactionnumber)|确定用户从下拉列表中选择的项数。|
|[CMFC功能放大缩小字体功能 放大缩小字体功能](#hasmenu)|指示对象是否包含菜单。|

## <a name="remarks"></a>备注

类`CMFCRibbonUndoButton`使用堆栈来表示下拉列表。

## <a name="example"></a>示例

下面的示例演示如何构造`CMFCRibbonUndoButton`类的对象，以及如何向操作列表中添加新操作。 此代码段是[功能区小工具示例的一](../../overview/visual-cpp-samples.md)部分。

[!code-cpp[NVC_MFC_RibbonGadgets#2](../../mfc/reference/codesnippet/cpp/cmfcribbonundobutton-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)

[CMFCRibbonButton](../../mfc/reference/cmfcribbonbutton-class.md)

[CMFCRibbonGallery](../../mfc/reference/cmfcribbongallery-class.md)

[CMFCRibbonUndoButton](../../mfc/reference/cmfcribbonundobutton-class.md)

## <a name="requirements"></a>要求

**标题：** afxribbonundobutton.h

## <a name="cmfcribbonundobuttonaddundoaction"></a><a name="addundoaction"></a>CMFC 功能Undo按钮：：添加UndoAction

向操作列表添加新操作。

```cpp
void AddUndoAction(LPCTSTR lpszLabel);
```

### <a name="parameters"></a>参数

*lpszLabel*<br/>
[在]将在下拉列表中显示的操作标签。

## <a name="cmfcribbonundobuttoncleanupundolist"></a><a name="cleanupundolist"></a>CMFC 功能整理按钮：：清除 Undo 列表

清除操作列表，这是下拉列表。

```cpp
void CleanUpUndoList();
```

## <a name="cmfcribbonundobuttoncmfcribbonundobutton"></a><a name="cmfcribbonundobutton"></a>CMFC 功能Undo按钮：：CMFC功能放大缩小字体功能

使用指定的命令`CMFCRibbonUndoButton`ID、文本标签和父对象的图像列表中的图像来构造新对象。

```
CMFCRibbonUndoButton(
    UINT nID,
    LPCTSTR lpszText,
    int nSmallImageIndex=-1,
    int nLargeImageIndex=-1);

CMFCRibbonUndoButton(
    UINT nID,
    LPCTSTR lpszText,
    HICON hIcon);
```

### <a name="parameters"></a>参数

*nID*<br/>
[在]指定命令标识符。

*lpszText*<br/>
[在]指定按钮的文本标签。

*n 小图像索引*<br/>
[在]按钮小图像的父对象图像列表中的零索引。

*nLargeImageIndex*<br/>
[在]按钮大图像的父对象图像列表中的零索引。

*hIcon*<br/>
[在]图标的句柄，您可以将其用作按钮的图像。

## <a name="cmfcribbonundobuttongetactionnumber"></a><a name="getactionnumber"></a>CMFC 功能Undo按钮：获取操作编号

确定用户从下拉列表中选择的项数。

```
int GetActionNumber() const;
```

### <a name="return-value"></a>返回值

用户选择的项数。

## <a name="cmfcribbonundobuttonhasmenu"></a><a name="hasmenu"></a>CMFC功能放大缩小字体功能 放大缩小字体功能

指示对象是否包含菜单。

```
virtual BOOL HasMenu() const;
```

### <a name="return-value"></a>返回值

始终返回 TRUE。

### <a name="remarks"></a>备注

## <a name="see-also"></a>请参阅

[层次结构图表](../../mfc/hierarchy-chart.md)<br/>
[类](../../mfc/reference/mfc-classes.md)<br/>
[CMFCRibbonGallery 类](../../mfc/reference/cmfcribbongallery-class.md)<br/>
[CMFC 功能按钮类](../../mfc/reference/cmfcribbonbutton-class.md)
