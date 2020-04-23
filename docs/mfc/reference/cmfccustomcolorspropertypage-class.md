---
title: CMFCCustomColorsPropertyPage 类
ms.date: 11/04/2016
f1_keywords:
- CMFCCustomColorsPropertyPage
- AFXCUSTOMCOLORSPROPERTYPAGE/CMFCCustomColorsPropertyPage
- AFXCUSTOMCOLORSPROPERTYPAGE/CMFCCustomColorsPropertyPage::Setup
helpviewer_keywords:
- CMFCCustomColorsPropertyPage [MFC], Setup
ms.assetid: 46a45ba2-1fda-440d-8018-d4dcd44f5816
ms.openlocfilehash: 468d947947fc89f9ebc832cda722d854bb8b4be2
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/22/2020
ms.locfileid: "81752473"
---
# <a name="cmfccustomcolorspropertypage-class"></a>CMFCCustomColorsPropertyPage 类

表示可在颜色对话框中选择自定义颜色的属性页。

## <a name="syntax"></a>语法

```
class CMFCCustomColorsPropertyPage : public CPropertyPage
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|||
|-|-|
|名称|说明|
|`CMFCCustomColorsPropertyPage::CMFCCustomColorsPropertyPage`|默认构造函数。|

### <a name="public-methods"></a>公共方法

|||
|-|-|
|名称|说明|
|`CMFCCustomColorsPropertyPage::CreateObject`|由框架用于创建此类类型的动态实例。|
|`CMFCCustomColorsPropertyPage::GetThisClass`|框架用于获取指向与此类类型关联的[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)对象的指针。|
|[CMFC自定义颜色属性页：：设置](#setup)|设置属性页的颜色组件。|

### <a name="remarks"></a>备注

类`CMFCColorDialog`使用此类来显示自定义颜色属性页。 有关 的详细信息`CMFCColorDialog`，请参阅[CMFCColorDialog 类](../../mfc/reference/cmfccolordialog-class.md)。

## <a name="example"></a>示例

下面的示例演示如何构造`CMFCCustomColorsPropertyPage`对象并设置属性页的颜色组件。

[!code-cpp[NVC_MFC_RibbonApp#35](../../mfc/reference/codesnippet/cpp/cmfccustomcolorspropertypage-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CPropertyPage](../../mfc/reference/cpropertypage-class.md)

[CMFC自定义颜色属性页](../../mfc/reference/cmfccustomcolorspropertypage-class.md)

## <a name="requirements"></a>要求

**标题：** afx自定义颜色属性页.h

## <a name="cmfccustomcolorspropertypagesetup"></a><a name="setup"></a>CMFC自定义颜色属性页：：设置

设置属性页的颜色组件。

```cpp
void Setup(
    BYTE R,
    BYTE G,
    BYTE B);
```

### <a name="parameters"></a>参数

|||
|-|-|
|参数|说明|
|*R*|[在]RGB 值的红色组件。|
|*G*|[在]RGB 值的绿色组件。|
|*B*|[在]RGB 值的蓝色组件。|

### <a name="remarks"></a>备注

此方法更新属性页的当前 RGB 和关联的 HLS（色调、光度和饱和度）颜色值。 当框架初始化颜色对话框或用户按下鼠标左键时[，CMFCColorDialog：setPageTWO](../../mfc/reference/cmfccolordialog-class.md#setpagetwo)方法调用此方法。 有关 的详细信息`CMFCColorDialog`，请参阅[CMFCColorDialog 类](../../mfc/reference/cmfccolordialog-class.md)。

## <a name="see-also"></a>请参阅

[层次结构图表](../../mfc/hierarchy-chart.md)<br/>
[类](../../mfc/reference/mfc-classes.md)<br/>
[CMFCColor对话类](../../mfc/reference/cmfccolordialog-class.md)<br/>
[CMFCStandardColorsPropertyPage 类](../../mfc/reference/cmfcstandardcolorspropertypage-class.md)
