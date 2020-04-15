---
title: CMFCRibbonButtonsGroup 类
ms.date: 11/04/2016
f1_keywords:
- CMFCRibbonButtonsGroup
- AFXRIBBONBUTTONSGROUP/CMFCRibbonButtonsGroup
- AFXRIBBONBUTTONSGROUP/CMFCRibbonButtonsGroup::CMFCRibbonButtonsGroup
- AFXRIBBONBUTTONSGROUP/CMFCRibbonButtonsGroup::AddButton
- AFXRIBBONBUTTONSGROUP/CMFCRibbonButtonsGroup::AddButtons
- AFXRIBBONBUTTONSGROUP/CMFCRibbonButtonsGroup::GetButton
- AFXRIBBONBUTTONSGROUP/CMFCRibbonButtonsGroup::GetCount
- AFXRIBBONBUTTONSGROUP/CMFCRibbonButtonsGroup::GetImageSize
- AFXRIBBONBUTTONSGROUP/CMFCRibbonButtonsGroup::GetRegularSize
- AFXRIBBONBUTTONSGROUP/CMFCRibbonButtonsGroup::HasImages
- AFXRIBBONBUTTONSGROUP/CMFCRibbonButtonsGroup::OnDrawImage
- AFXRIBBONBUTTONSGROUP/CMFCRibbonButtonsGroup::RemoveAll
- AFXRIBBONBUTTONSGROUP/CMFCRibbonButtonsGroup::SetImages
- AFXRIBBONBUTTONSGROUP/CMFCRibbonButtonsGroup::SetParentCategory
helpviewer_keywords:
- CMFCRibbonButtonsGroup [MFC], CMFCRibbonButtonsGroup
- CMFCRibbonButtonsGroup [MFC], AddButton
- CMFCRibbonButtonsGroup [MFC], AddButtons
- CMFCRibbonButtonsGroup [MFC], GetButton
- CMFCRibbonButtonsGroup [MFC], GetCount
- CMFCRibbonButtonsGroup [MFC], GetImageSize
- CMFCRibbonButtonsGroup [MFC], GetRegularSize
- CMFCRibbonButtonsGroup [MFC], HasImages
- CMFCRibbonButtonsGroup [MFC], OnDrawImage
- CMFCRibbonButtonsGroup [MFC], RemoveAll
- CMFCRibbonButtonsGroup [MFC], SetImages
- CMFCRibbonButtonsGroup [MFC], SetParentCategory
ms.assetid: b993d93e-fc1a-472f-a87f-1d7b7b499845
ms.openlocfilehash: af5919ff2a72fc2aa1eeeb95fc93afbe9e743582
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375278"
---
# <a name="cmfcribbonbuttonsgroup-class"></a>CMFCRibbonButtonsGroup 类

该`CMFCRibbonButtonsGroup`类允许您将一组功能区按钮组织到组中。 组中的所有按钮在水平位置上直接彼此相邻并位于边框中。

## <a name="syntax"></a>语法

```
class CMFCRibbonButtonsGroup : public CMFCRibbonBaseElement
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[CMFCRibbonButtonsGroup::CMFCRibbonButtonsGroup](#cmfcribbonbuttonsgroup)|构造 `CMFCRibbonButtonsGroup` 对象。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CMFC功能功能按钮组：：添加按钮](#addbutton)|向组添加按钮。|
|[CMFC功能功能按钮组：添加按钮](#addbuttons)|将按钮列表添加到组。|
|[CMFC功能功能按钮组：获取按钮](#getbutton)|返回指向位于指定索引的按钮的指针。|
|[CMFC功能中心按钮组：获取计数](#getcount)|返回组中的按钮数。|
|[CMFCRibbonButtonsGroup::GetImageSize](#getimagesize)|返回功能区组中正常图像的图像大小（覆盖[CMFCRibbonBase元素：：获取图像大小](../../mfc/reference/cmfcribbonbaseelement-class.md#getimagesize)。|
|[CMFCRibbonButtonsGroup::GetRegularSize](#getregularsize)|返回功能区元素的常规大小（覆盖[CMFC 功能基础元素：：获取常规大小](../../mfc/reference/cmfcribbonbaseelement-class.md#getregularsize)。|
|[CMFCRibbonButtonsGroup::HasImages](#hasimages)|报告`CMFCRibbonButtonsGroup`对象是否包含工具栏图像。|
|[CMFCRibbonButtonsGroup::OnDrawImage](#ondrawimage)|根据按钮是正常、突出显示还是禁用，为指定的按钮绘制相应的图像。|
|[CMFCRibbonButtonsGroup::RemoveAll](#removeall)|从`CMFCRibbonButtonsGroup`对象中删除所有按钮。|
|[CMFC功能功能按钮组：：设置图像](#setimages)|将图像分配给组。|
|[CMFCRibbonButtonsGroup::SetParentCategory](#setparentcategory)|设置`CMFCRibbonButtonsGroup`对象的父`CMFCRibbonCategory`级及其内的所有按钮（覆盖[CMFC 功能基础元素：：设置父项类别](../../mfc/reference/cmfcribbonbaseelement-class.md#setparentcategory)。|

## <a name="remarks"></a>备注

该组派生自[CMFCBaseRibbonElement，](../../mfc/reference/cmfcribbonbaseelement-class.md)可以作为单个实体进行操作。 您可以将组放置在任何面板或弹出菜单上。

## <a name="example"></a>示例

下面的示例演示了如何使用 `CMFCRibbonButtonsGroup` 类中的各种方法。 该示例演示如何构造`CMFCRibbonButtonsGroup`对象、将图像分配给功能区按钮组以及向功能区按钮组添加按钮。 此代码片段属于 [Draw Client 示例](../../overview/visual-cpp-samples.md)。

[!code-cpp[NVC_MFC_DrawClient#2](../../mfc/reference/codesnippet/cpp/cmfcribbonbuttonsgroup-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)

[CMFCRibbonButtonsGroup](../../mfc/reference/cmfcribbonbuttonsgroup-class.md)

## <a name="requirements"></a>要求

**标题：** afxribbon 按钮组.h

## <a name="cmfcribbonbuttonsgroupaddbutton"></a><a name="addbutton"></a>CMFC功能功能按钮组：：添加按钮

向组添加按钮。

```
void AddButton(CMFCRibbonBaseElement* pButton);
```

### <a name="parameters"></a>参数

*pButton*<br/>
[在]指向要添加的按钮的指针。

## <a name="cmfcribbonbuttonsgroupaddbuttons"></a><a name="addbuttons"></a>CMFC功能功能按钮组：添加按钮

将按钮列表添加到组。

```
void AddButtons(
    const CList<CMFCRibbonBaseElement*,CMFCRibbonBaseElement*>& lstButtons);
```

### <a name="parameters"></a>参数

*lstButtons*<br/>
[在]指向要添加的按钮的指针列表。

## <a name="cmfcribbonbuttonsgroupcmfcribbonbuttonsgroup"></a><a name="cmfcribbonbuttonsgroup"></a>CMFC功能中心按钮组：CMFC功能功能按钮组

构造 `CMFCRibbonButtonsGroup` 对象。

```
CMFCRibbonButtonsGroup();
CMFCRibbonButtonsGroup(CMFCRibbonBaseElement* pButton);
```

### <a name="parameters"></a>参数

*pButton*<br/>
[在]指定要添加到新创建`CMFCRibbonButtonsGroup`的对象的按钮。

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

## <a name="cmfcribbonbuttonsgroupgetbutton"></a><a name="getbutton"></a>CMFC功能功能按钮组：获取按钮

返回指向位于指定索引的按钮的指针。

```
CMFCRibbonBaseElement* GetButton(int i) const;
```

### <a name="parameters"></a>参数

*Ⅰ*<br/>
[在]要返回的按钮的零基索引。

### <a name="return-value"></a>返回值

指向位于指定索引的按钮的指针。 如果指定的索引范围不一，则为 NULL。

### <a name="remarks"></a>备注

## <a name="cmfcribbonbuttonsgroupgetcount"></a><a name="getcount"></a>CMFC功能中心按钮组：获取计数

返回组中的按钮数。

```
int GetCount() const;
```

### <a name="return-value"></a>返回值

组中的按钮数。

## <a name="cmfcribbonbuttonsgroupgetimagesize"></a><a name="getimagesize"></a>CMFC 功能按钮组：获取图像大小

检索受保护`CMFCToolBarImages`成员`m_Images`的源映像大小。

```
const CSize GetImageSize() const;
```

### <a name="return-value"></a>返回值

返回工具栏图像的源图像大小（如果存在）或`CSize`零（如果没有）。

### <a name="remarks"></a>备注

## <a name="cmfcribbonbuttonsgroupgetregularsize"></a><a name="getregularsize"></a>CMFC 功能按钮组：获取常规尺寸

检索功能区组元素的最大可能大小。

```
virtual CSize GetRegularSize(CDC* pDC);
```

### <a name="parameters"></a>参数

*pDC*<br/>
[在]指向功能区组的设备上下文。

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

## <a name="cmfcribbonbuttonsgrouphasimages"></a><a name="hasimages"></a>CMFC功能中心按钮组：：有图像

报告`CMFCRibbonButtonsGroup`对象是否包含工具栏图像。

```
BOOL HasImages() const;
```

### <a name="return-value"></a>返回值

如果受保护`CMFCToolBarImages`成员`m_Images`包含任何图像，则返回 TRUE;如果不包含，则返回 FALSE。

### <a name="remarks"></a>备注

## <a name="cmfcribbonbuttonsgroupondrawimage"></a><a name="ondrawimage"></a>CMFC功能中心按钮组：：在DrawImage上

根据按钮是正常、突出显示还是禁用，为指定的按钮绘制相应的图像。

```
virtual void OnDrawImage(
    CDC* pDC,
    CRect rectImage,
    CMFCRibbonBaseElement* pButton,
    int nImageIndex);
```

### <a name="parameters"></a>参数

*pDC*<br/>
[在]指向`CMFCRibbonButtonsGroup`对象的设备上下文的指针。

*rectImage*<br/>
[在]要在其中绘制图像的矩形。

*pButton*<br/>
[在]为其绘制图像的按钮。

*n图像索引*<br/>
[在]要在按钮上绘制的图像索引（在用于正常、突出显示或禁用按钮的三个图像数组之一中）。

### <a name="remarks"></a>备注

## <a name="cmfcribbonbuttonsgroupremoveall"></a><a name="removeall"></a>CMFC功能功能按钮组：：删除所有

从`CMFCRibbonButtonsGroup`对象中删除所有按钮。

```
void RemoveAll();
```

### <a name="remarks"></a>备注

## <a name="cmfcribbonbuttonsgroupsetimages"></a><a name="setimages"></a>CMFC功能功能按钮组：：设置图像

将图像分配给功能区按钮组。

```
void SetImages(
    CMFCToolBarImages* pImages,
    CMFCToolBarImages* pHotImages,
    CMFCToolBarImages* pDisabledImages);
```

### <a name="parameters"></a>参数

*pImage*<br/>
[在]常规图像。

*pHotImages*<br/>
[在]热门图像。

*p 禁用图像*<br/>
[在]已禁用的图像。

### <a name="remarks"></a>备注

在`SetImages`将按钮添加到组之前调用。 图像数必须大于或等于要添加到组中的按钮数。

> [!NOTE]
> 热图像是当用户悬停在按钮上时显示的图像。 禁用的图像是禁用按钮时显示的图像。

## <a name="cmfcribbonbuttonsgroupsetparentcategory"></a><a name="setparentcategory"></a>CMFC 功能按钮组：：设置父项类别

设置`CMFCRibbonButtonsGroup`对象的父`CMFCRibbonCategory`级及其内的所有按钮。

```
virtual void SetParentCategory(CMFCRibbonCategory* pCategory);
```

### <a name="parameters"></a>参数

*p 类别*<br/>
[在]指向要设置的父类别（功能区控件中的选项卡式组称为类别）。

### <a name="remarks"></a>备注

## <a name="see-also"></a>另请参阅

[层次结构图表](../../mfc/hierarchy-chart.md)<br/>
[类](../../mfc/reference/mfc-classes.md)
