---
title: CMFCRibbonGalleryMenuButton 类
ms.date: 11/04/2016
f1_keywords:
- CMFCRibbonGalleryMenuButton
- AFXRIBBONPALETTEGALLERY/CMFCRibbonGalleryMenuButton
- AFXRIBBONPALETTEGALLERY/CMFCRibbonGalleryMenuButton::CMFCRibbonGalleryMenuButton
- AFXRIBBONPALETTEGALLERY/CMFCRibbonGalleryMenuButton::CopyFrom
- AFXRIBBONPALETTEGALLERY/CMFCRibbonGalleryMenuButton::CreatePopupMenu
- AFXRIBBONPALETTEGALLERY/CMFCRibbonGalleryMenuButton::GetPalette
- AFXRIBBONPALETTEGALLERY/CMFCRibbonGalleryMenuButton::HasButton
- AFXRIBBONPALETTEGALLERY/CMFCRibbonGalleryMenuButton::IsEmptyMenuAllowed
helpviewer_keywords:
- CMFCRibbonGalleryMenuButton [MFC], CMFCRibbonGalleryMenuButton
- CMFCRibbonGalleryMenuButton [MFC], CopyFrom
- CMFCRibbonGalleryMenuButton [MFC], CreatePopupMenu
- CMFCRibbonGalleryMenuButton [MFC], GetPalette
- CMFCRibbonGalleryMenuButton [MFC], HasButton
- CMFCRibbonGalleryMenuButton [MFC], IsEmptyMenuAllowed
ms.assetid: 4d459d9b-8b1a-4371-92f6-dc4ce6cc42c8
ms.openlocfilehash: b63eab7c1e4d03a9103795892603b819eb7d02f3
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/18/2019
ms.locfileid: "58777137"
---
# <a name="cmfcribbongallerymenubutton-class"></a>CMFCRibbonGalleryMenuButton 类

实现包含功能区库的功能区菜单按钮。
有关更多详细信息，请参阅中的源代码**VC\\atlmfc\\src\\mfc**的 Visual Studio 安装文件夹。

## <a name="syntax"></a>语法

```
class CMFCRibbonGalleryMenuButton : public CMFCToolBarMenuButton
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[CMFCRibbonGalleryMenuButton::CMFCRibbonGalleryMenuButton](#cmfcribbongallerymenubutton)|构造并初始化一个 `CMFCRibbonGalleryMenuButton` 对象。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CMFCRibbonGalleryMenuButton::CopyFrom](#copyfrom)|(重写[cmfctoolbarmenubutton:: Copyfrom](../../mfc/reference/cmfctoolbarmenubutton-class.md#copyfrom)。)|
|[CMFCRibbonGalleryMenuButton::CreatePopupMenu](#createpopupmenu)|(重写[cmfctoolbarmenubutton:: Createpopupmenu](../../mfc/reference/cmfctoolbarmenubutton-class.md#createpopupmenu)。)|
|[CMFCRibbonGalleryMenuButton::GetPalette](#getpalette)||
|[CMFCRibbonGalleryMenuButton::HasButton](#hasbutton)|（重写 `CMFCToolBarMenuButton::HasButton`。）|
|[CMFCRibbonGalleryMenuButton::IsEmptyMenuAllowed](#isemptymenuallowed)|(重写[cmfctoolbarmenubutton:: Isemptymenuallowed](../../mfc/reference/cmfctoolbarmenubutton-class.md#isemptymenuallowed)。)|

### <a name="remarks"></a>备注

库菜单按钮显示为带箭头的弹出菜单。 用户单击此按钮时，会显示图像库。 构造库菜单按钮时，必须指定包含这些图像的图像列表。

## <a name="example"></a>示例

下面的示例演示如何采用菜单按钮显示项目符号库：

```
BOOL CMainFrame::OnShowPopupMenu (CMFCPopupMenu* pMenuPopup)
{
    int nBulletIndex = pMenuBar->CommandToIndex (ID_PARA_BULLETS);

    if (nBulletIndex>= 0)
{
    CMFCToolBarButton* pExButton =
    pMenuBar->GetButton(nBulletIndex);
ASSERT_VALID (pExButton);

    CMFCRibbonGalleryMenuButton paletteBullet (
    pExButton->m_nID,
    pExButton->GetImage (),
    pExButton->m_strText);

InitBulletPalette (&paletteBullet.GetPalette ());

    pMenuBar->ReplaceButton (ID_PARA_BULLETS,
    paletteBullet);

}
}
```

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md) [CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md) [CMFCToolBarMenuButton](../../mfc/reference/cmfctoolbarmenubutton-class.md) [CMFCRibbonGalleryMenuButton](../../mfc/reference/cmfcribbongallerymenubutton-class.md)

## <a name="requirements"></a>要求

**标头：** afxRibbonPaletteGallery.h

##  <a name="copyfrom"></a>  CMFCRibbonGalleryMenuButton::CopyFrom

```
virtual void CopyFrom(const CMFCToolBarButton& src);
```

### <a name="parameters"></a>参数

[in] *src*<br/>

### <a name="remarks"></a>备注

##  <a name="cmfcribbongallerymenubutton"></a>  CMFCRibbonGalleryMenuButton::CMFCRibbonGalleryMenuButton

构造并初始化[CMFCRibbonGalleryMenuButton](../../mfc/reference/cmfcribbongallerymenubutton-class.md)对象。

```
CMFCRibbonGalleryMenuButton(
    UINT uiID,
    int iImage,
    LPCTSTR lpszText,
    CMFCToolBarImages& imagesPalette);

CMFCRibbonGalleryMenuButton(
    UINT uiID,
    int iImage,
    LPCTSTR lpszText,
    UINT uiImagesPaletteResID = 0,
    int cxPaletteImage = 0);
```

### <a name="parameters"></a>参数

*uiID*<br/>
按钮的命令 ID。 这是在用户单击此按钮时发送 WM_COMMAND 消息中的值。

*iImage*<br/>
要与库菜单按钮显示的图像的索引。 图像存储在*imagesPalette*参数。

*lpszText*<br/>
要在菜单按钮上显示的文本。

*imagesPalette*<br/>
包含要在库上显示的图像的列表。

*uiImagesPaletteResID*<br/>
要在库上显示的图像列表的图像资源 ID。

*cxPaletteImage*<br/>
指定以像素为单位的要在库上显示的图像的宽度。

### <a name="remarks"></a>备注

库菜单按钮显示为一个带有箭头的弹出菜单。 用户单击此按钮时，会显示图像库。

### <a name="example"></a>示例

下面的示例演示如何使用的构造函数`CMFCRibbonGalleryMenuButton`类。 此代码片段属于[MS Office 2007 演示示例](../../overview/visual-cpp-samples.md)。

[!code-cpp[NVC_MFC_MSOffice2007Demo#8](../../mfc/reference/codesnippet/cpp/cmfcribbongallerymenubutton-class_1.cpp)]

##  <a name="createpopupmenu"></a>  CMFCRibbonGalleryMenuButton::CreatePopupMenu

```
virtual CMFCPopupMenu* CreatePopupMenu();
```

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

##  <a name="getpalette"></a>  CMFCRibbonGalleryMenuButton::GetPalette

```
CMFCRibbonGallery& GetPalette();
```

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

##  <a name="hasbutton"></a>  CMFCRibbonGalleryMenuButton::HasButton

```
virtual BOOL HasButton() const;
```

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

##  <a name="isemptymenuallowed"></a>  CMFCRibbonGalleryMenuButton::IsEmptyMenuAllowed

```
virtual BOOL IsEmptyMenuAllowed() const;
```

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

## <a name="see-also"></a>请参阅

[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[类](../../mfc/reference/mfc-classes.md)<br/>
[CMFCToolBarMenuButton 类](../../mfc/reference/cmfctoolbarmenubutton-class.md)<br/>
[CMFCRibbonGallery 类](../../mfc/reference/cmfcribbongallery-class.md)
