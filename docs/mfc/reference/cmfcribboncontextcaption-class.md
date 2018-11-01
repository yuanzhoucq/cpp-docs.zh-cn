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
ms.openlocfilehash: 3e6d8dcd643a58b3df60488b50da08288a34bab9
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50628379"
---
# <a name="cmfcribboncontextcaption-class"></a>CMFCRibbonContextCaption 类

实现显示在功能区类别或上下文类别顶部的彩色标题。

## <a name="syntax"></a>语法

```
class CMFCRibbonContextCaption : public CMFCRibbonButton
```

## <a name="members"></a>成员

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|`CMFCRibbonContextCaption::CreateObject`|由框架用于创建此类类型的动态实例。|
|[CMFCRibbonContextCaption::GetColor](#getcolor)|返回标题栏的颜色。|
|[CMFCRibbonContextCaption::GetRightTabX](#getrighttabx)||
|`CMFCRibbonContextCaption::GetThisClass`|由框架用于获取一个指向[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)与此类类型相关联的对象。|

## <a name="remarks"></a>备注

不能直接实例化此类。 [CMFCRibbonBar 类](../../mfc/reference/cmfcribbonbar-class.md)类在内部使用此类以将颜色添加到功能区类别。

若要设置功能区类别的颜色，请调用[cmfcribboncategory:: Settabcolor](../../mfc/reference/cmfcribboncategory-class.md#settabcolor)。 若要设置上下文类别的颜色，请调用[cmfcribbonbar:: Addcontextcategory](../../mfc/reference/cmfcribbonbar-class.md#addcontextcategory)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)

[CMFCRibbonButton](../../mfc/reference/cmfcribbonbutton-class.md)

[CMFCRibbonContextCaption](../../mfc/reference/cmfcribboncontextcaption-class.md)

## <a name="requirements"></a>要求

**标头：** afxRibbonBar.h

##  <a name="getcolor"></a>  CMFCRibbonContextCaption::GetColor

返回标题的背景色。

```
AFX_RibbonCategoryColor GetColor() const;
```

### <a name="return-value"></a>返回值

返回的值可以是下列枚举值之一：

- `AFX_CategoryColor_None`

- `AFX_CategoryColor_Red`

- `AFX_CategoryColor_Orange`

- `AFX_CategoryColor_Yellow`

- `AFX_CategoryColor_Green`

- `AFX_CategoryColor_Blue`

- `AFX_CategoryColor_Indigo`

- `AFX_CategoryColor_Violet`

### <a name="remarks"></a>备注

可以通过调用设置标题的颜色[cmfcribboncategory:: Settabcolor](../../mfc/reference/cmfcribboncategory-class.md#settabcolor)或[cmfcribbonbar:: Addcontextcategory](../../mfc/reference/cmfcribbonbar-class.md#addcontextcategory)。

##  <a name="getrighttabx"></a>  CMFCRibbonContextCaption::GetRightTabX

检索类别的功能区选项卡的右边缘的位置。

```
int GetRightTabX() const;
```

### <a name="return-value"></a>返回值

返回右侧的 X 值的包围矩形`CMFCRibbonCategory`对象的功能区选项卡上或如果该选项卡将被截断为-1 的值。

### <a name="remarks"></a>备注

## <a name="see-also"></a>请参阅

[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[类](../../mfc/reference/mfc-classes.md)<br/>
[CMFCRibbonButton 类](../../mfc/reference/cmfcribbonbutton-class.md)<br/>
[CMFCRibbonCategory 类](../../mfc/reference/cmfcribboncategory-class.md)<br/>
[CMFCRibbonBar 类](../../mfc/reference/cmfcribbonbar-class.md)
