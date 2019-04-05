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
ms.openlocfilehash: 39979d48eb7b0f7aba9dbe7bd42c2f91845af968
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/05/2019
ms.locfileid: "58781986"
---
# <a name="cmfcribbonbuttonsgroup-class"></a>CMFCRibbonButtonsGroup 类

`CMFCRibbonButtonsGroup`类使您可以将一组功能区按钮组织到组。 组中的所有按钮在水平位置上直接彼此相邻并位于边框中。

## <a name="syntax"></a>语法

```
class CMFCRibbonButtonsGroup : public CMFCRibbonBaseElement
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[CMFCRibbonButtonsGroup::CMFCRibbonButtonsGroup](#cmfcribbonbuttonsgroup)|构造 `CMFCRibbonButtonsGroup` 对象。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CMFCRibbonButtonsGroup::AddButton](#addbutton)|向组添加一个按钮。|
|[CMFCRibbonButtonsGroup::AddButtons](#addbuttons)|向组添加的按钮的列表。|
|[CMFCRibbonButtonsGroup::GetButton](#getbutton)|返回一个指向位于指定索引处的按钮。|
|[CMFCRibbonButtonsGroup::GetCount](#getcount)|返回组中的按钮的数目。|
|[CMFCRibbonButtonsGroup::GetImageSize](#getimagesize)|在功能区组中返回正常图像的图像大小 (重写[cmfcribbonbaseelement:: Getimagesize](../../mfc/reference/cmfcribbonbaseelement-class.md#getimagesize)。)|
|[CMFCRibbonButtonsGroup::GetRegularSize](#getregularsize)|返回功能区元素的常规大小 (重写[cmfcribbonbaseelement:: Getregularsize](../../mfc/reference/cmfcribbonbaseelement-class.md#getregularsize)。)|
|[CMFCRibbonButtonsGroup::HasImages](#hasimages)|报告是否`CMFCRibbonButtonsGroup`对象包含工具栏图像。|
|[CMFCRibbonButtonsGroup::OnDrawImage](#ondrawimage)|绘制指定的按钮，具体取决于该按钮是否正常、 突出显示或已禁用的相应映像。|
|[CMFCRibbonButtonsGroup::RemoveAll](#removeall)|移除所有按钮从`CMFCRibbonButtonsGroup`对象。|
|[CMFCRibbonButtonsGroup::SetImages](#setimages)|将图像分配给组。|
|[CMFCRibbonButtonsGroup::SetParentCategory](#setparentcategory)|设置父级`CMFCRibbonCategory`的`CMFCRibbonButtonsGroup`对象和在其中的所有按钮 (重写[cmfcribbonbaseelement:: Setparentcategory](../../mfc/reference/cmfcribbonbaseelement-class.md#setparentcategory)。)|

## <a name="remarks"></a>备注

组派生自[CMFCBaseRibbonElement](../../mfc/reference/cmfcribbonbaseelement-class.md) ，可以作为单个实体进行操作。 可以在任何面板或弹出菜单中放置组。

## <a name="example"></a>示例

下面的示例演示了如何使用 `CMFCRibbonButtonsGroup` 类中的各种方法。 该示例演示如何构造`CMFCRibbonButtonsGroup`对象，将图像分配给功能区按钮的组并将按钮添加到功能区按钮的组。 此代码片段属于 [Draw Client 示例](../../overview/visual-cpp-samples.md)。

[!code-cpp[NVC_MFC_DrawClient#2](../../mfc/reference/codesnippet/cpp/cmfcribbonbuttonsgroup-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)

[CMFCRibbonButtonsGroup](../../mfc/reference/cmfcribbonbuttonsgroup-class.md)

## <a name="requirements"></a>要求

**标头：** afxribbonbuttonsgroup.h

##  <a name="addbutton"></a>  CMFCRibbonButtonsGroup::AddButton

向组添加一个按钮。

```
void AddButton(CMFCRibbonBaseElement* pButton);
```

### <a name="parameters"></a>参数

*pButton*<br/>
[in]一个指向用于添加的按钮。

##  <a name="addbuttons"></a>  CMFCRibbonButtonsGroup::AddButtons

向组添加的按钮的列表。

```
void AddButtons(
    const CList<CMFCRibbonBaseElement*,CMFCRibbonBaseElement*>& lstButtons);
```

### <a name="parameters"></a>参数

*lstButtons*<br/>
[in]指向要添加的按钮的指针的列表。

##  <a name="cmfcribbonbuttonsgroup"></a>  CMFCRibbonButtonsGroup::CMFCRibbonButtonsGroup

构造 `CMFCRibbonButtonsGroup` 对象。

```
CMFCRibbonButtonsGroup();
CMFCRibbonButtonsGroup(CMFCRibbonBaseElement* pButton);
```

### <a name="parameters"></a>参数

*pButton*<br/>
[in]指定要添加到新创建的按钮`CMFCRibbonButtonsGroup`对象。

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

##  <a name="getbutton"></a>  CMFCRibbonButtonsGroup::GetButton

返回一个指向位于指定索引处的按钮。

```
CMFCRibbonBaseElement* GetButton(int i) const;
```

### <a name="parameters"></a>参数

*i*<br/>
[in]按钮可返回一个从零开始的索引。

### <a name="return-value"></a>返回值

一个指向位于指定索引处的按钮。 如果指定的索引超出范围，则为 NULL。

### <a name="remarks"></a>备注

##  <a name="getcount"></a>  CMFCRibbonButtonsGroup::GetCount

返回组中的按钮的数目。

```
int GetCount() const;
```

### <a name="return-value"></a>返回值

在组中的按钮的数目。

##  <a name="getimagesize"></a>  CMFCRibbonButtonsGroup::GetImageSize

检索受保护的源映像大小`CMFCToolBarImages`成员`m_Images`。

```
const CSize GetImageSize() const;
```

### <a name="return-value"></a>返回值

如果存在，或返回的工具栏图像，图像大小`CSize`的如果不为零。

### <a name="remarks"></a>备注

##  <a name="getregularsize"></a>  CMFCRibbonButtonsGroup::GetRegularSize

检索功能区组元素的最大可能大小。

```
virtual CSize GetRegularSize(CDC* pDC);
```

### <a name="parameters"></a>参数

*pDC*<br/>
[in]指向功能区组的设备上下文指针。

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

##  <a name="hasimages"></a>  CMFCRibbonButtonsGroup::HasImages

报告是否`CMFCRibbonButtonsGroup`对象包含工具栏图像。

```
BOOL HasImages() const;
```

### <a name="return-value"></a>返回值

返回 TRUE，如果受保护`CMFCToolBarImages`成员`m_Images`不包含任何图像或 false。

### <a name="remarks"></a>备注

##  <a name="ondrawimage"></a>  CMFCRibbonButtonsGroup::OnDrawImage

绘制指定的按钮，具体取决于该按钮是否正常、 突出显示或已禁用的相应映像。

```
virtual void OnDrawImage(
    CDC* pDC,
    CRect rectImage,
    CMFCRibbonBaseElement* pButton,
    int nImageIndex);
```

### <a name="parameters"></a>参数

*pDC*<br/>
[in]指向设备上下文的`CMFCRibbonButtonsGroup`对象。

*rectImage*<br/>
[in]在其中绘制图像的矩形。

*pButton*<br/>
[in]要为其绘制图像按钮。

*nImageIndex*<br/>
[in]（在一个正常、 突出显示或已禁用按钮的三个映像数组） 的按钮上绘制图像的索引。

### <a name="remarks"></a>备注

##  <a name="removeall"></a>  CMFCRibbonButtonsGroup::RemoveAll

移除所有按钮从`CMFCRibbonButtonsGroup`对象。

```
void RemoveAll();
```

### <a name="remarks"></a>备注

##  <a name="setimages"></a>  CMFCRibbonButtonsGroup::SetImages

将图像分配给功能区按钮的组。

```
void SetImages(
    CMFCToolBarImages* pImages,
    CMFCToolBarImages* pHotImages,
    CMFCToolBarImages* pDisabledImages);
```

### <a name="parameters"></a>参数

*pImages*<br/>
[in]常规映像。

*pHotImages*<br/>
[in]热的映像。

*pDisabledImages*<br/>
[in]已禁用的映像。

### <a name="remarks"></a>备注

调用`SetImages`将按钮添加到组之前。 映像数量必须大于或等于的按钮添加到组的数目。

> [!NOTE]
>  热映像是当用户悬停在按钮上时显示的映像。 已禁用的图像是按钮处于禁用状态时显示的图像。

##  <a name="setparentcategory"></a>  CMFCRibbonButtonsGroup::SetParentCategory

设置父级`CMFCRibbonCategory`的`CMFCRibbonButtonsGroup`对象和在其中的所有按钮。

```
virtual void SetParentCategory(CMFCRibbonCategory* pCategory);
```

### <a name="parameters"></a>参数

*pCategory*<br/>
[in]指向要设置的父类别 （功能区控件中的选项卡式的组称为类别）。

### <a name="remarks"></a>备注

## <a name="see-also"></a>请参阅

[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[类](../../mfc/reference/mfc-classes.md)
