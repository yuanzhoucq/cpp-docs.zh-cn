---
title: CMFCRibbonContextCaption 类
ms.date: 11/04/2016
f1_keywords:
- CMFCRibbonContextCaption
- AFXRIBBONBAR/CMFCRibbonContextCaption
- AFXRIBBONBAR/CMFCRibbonContextCaption::GetColor
- AFXRIBBONBAR/CMFCRibbonContextCaption::GetRightTabX
helpviewer_keywords:
- CMFCRibbonContextCaption [MFC], GetColor
- CMFCRibbonContextCaption [MFC], GetRightTabX
ms.assetid: cce2c0a2-8370-4266-997e-f8d0eeb3d616
ms.openlocfilehash: 7aacbe23684914c91129d9962ae847d442cc411b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375220"
---
# <a name="cmfcribboncontextcaption-class"></a>CMFCRibbonContextCaption 类

实现显示在功能区类别或上下文类别顶部的彩色标题。

## <a name="syntax"></a>语法

```
class CMFCRibbonContextCaption : public CMFCRibbonButton
```

## <a name="members"></a>成员

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|`CMFCRibbonContextCaption::CreateObject`|由框架用于创建此类类型的动态实例。|
|[CMFC功能相关标题：获取颜色](#getcolor)|返回标题栏的颜色。|
|[CMFC功能相关标题：获取正确的TabX](#getrighttabx)||
|`CMFCRibbonContextCaption::GetThisClass`|框架用于获取指向与此类类型关联的[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)对象的指针。|

## <a name="remarks"></a>备注

不能直接实例化此类。 [CMFCRibbonBar 类](../../mfc/reference/cmfcribbonbar-class.md)在内部使用此类向功能区类别添加颜色。

要设置功能区类别的颜色，请致电[CMFC 功能区类别：：SetTabColor](../../mfc/reference/cmfcribboncategory-class.md#settabcolor)。 要设置上下文类别的颜色，请致电[CMFC 功能区栏：：添加上下文类别](../../mfc/reference/cmfcribbonbar-class.md#addcontextcategory)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)

[CMFCRibbonButton](../../mfc/reference/cmfcribbonbutton-class.md)

[CMFCRibbonContextCaption](../../mfc/reference/cmfcribboncontextcaption-class.md)

## <a name="requirements"></a>要求

**标题：** afxRibbonBar.h

## <a name="cmfcribboncontextcaptiongetcolor"></a><a name="getcolor"></a>CMFC功能相关标题：获取颜色

返回标题的背景颜色。

```
AFX_RibbonCategoryColor GetColor() const;
```

### <a name="return-value"></a>返回值

返回的值可以是以下枚举值之一：

- `AFX_CategoryColor_None`

- `AFX_CategoryColor_Red`

- `AFX_CategoryColor_Orange`

- `AFX_CategoryColor_Yellow`

- `AFX_CategoryColor_Green`

- `AFX_CategoryColor_Blue`

- `AFX_CategoryColor_Indigo`

- `AFX_CategoryColor_Violet`

### <a name="remarks"></a>备注

标题的颜色可以通过调用[CMFC 功能分类：：SetTabColor](../../mfc/reference/cmfcribboncategory-class.md#settabcolor)或[CMFC 功能栏：：添加上下文类别](../../mfc/reference/cmfcribbonbar-class.md#addcontextcategory)来设置。

## <a name="cmfcribboncontextcaptiongetrighttabx"></a><a name="getrighttabx"></a>CMFC功能相关标题：获取正确的TabX

检索类别功能区选项卡右侧边缘的位置。

```
int GetRightTabX() const;
```

### <a name="return-value"></a>返回值

返回`CMFCRibbonCategory`对象功能区选项卡的封闭矩形的右侧 X 值，如果选项卡被截断，则返回 -1 的值。

### <a name="remarks"></a>备注

## <a name="see-also"></a>另请参阅

[层次结构图表](../../mfc/hierarchy-chart.md)<br/>
[类](../../mfc/reference/mfc-classes.md)<br/>
[CMFC 功能按钮类](../../mfc/reference/cmfcribbonbutton-class.md)<br/>
[CMFCRibbonCategory 类](../../mfc/reference/cmfcribboncategory-class.md)<br/>
[CMFC剪条类](../../mfc/reference/cmfcribbonbar-class.md)
