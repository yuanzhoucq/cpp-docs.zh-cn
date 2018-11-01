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
ms.openlocfilehash: b35db4d6cd322cd363a9c490283c1351fe7a7ce2
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50473627"
---
# <a name="cmfccustomcolorspropertypage-class"></a>CMFCCustomColorsPropertyPage 类

表示可以在颜色对话框中选择自定义颜色的属性页。

## <a name="syntax"></a>语法

```
class CMFCCustomColorsPropertyPage : public CPropertyPage
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|||
|-|-|
|名称|描述|
|`CMFCCustomColorsPropertyPage::CMFCCustomColorsPropertyPage`|默认构造函数。|

### <a name="public-methods"></a>公共方法

|||
|-|-|
|名称|描述|
|`CMFCCustomColorsPropertyPage::CreateObject`|由框架用于创建此类类型的动态实例。|
|`CMFCCustomColorsPropertyPage::GetThisClass`|由框架用于获取一个指向[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)与此类类型相关联的对象。|
|[CMFCCustomColorsPropertyPage::Setup](#setup)|设置的属性页的颜色组件。|

### <a name="remarks"></a>备注

`CMFCColorDialog`类使用此类以显示自定义颜色属性页。 有关详细信息`CMFCColorDialog`，请参阅[CMFCColorDialog 类](../../mfc/reference/cmfccolordialog-class.md)。

## <a name="example"></a>示例

下面的示例演示如何构造`CMFCCustomColorsPropertyPage`对象并设置属性页的颜色组件。

[!code-cpp[NVC_MFC_RibbonApp#35](../../mfc/reference/codesnippet/cpp/cmfccustomcolorspropertypage-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CPropertyPage](../../mfc/reference/cpropertypage-class.md)

[CMFCCustomColorsPropertyPage](../../mfc/reference/cmfccustomcolorspropertypage-class.md)

## <a name="requirements"></a>要求

**标头：** afxcustomcolorspropertypage.h

##  <a name="setup"></a>  CMFCCustomColorsPropertyPage::Setup

设置的属性页的颜色组件。

```
void Setup(
    BYTE R,
    BYTE G,
    BYTE B);
```

### <a name="parameters"></a>参数

|||
|-|-|
|参数|描述|
|*R*|[in]RGB 值的红色部分。|
|*G*|[in]RGB 值的绿色部分。|
|*B*|[in]RGB 值的蓝色部分。|

### <a name="remarks"></a>备注

此方法会更新当前 RGB 和关联的 HLS （hue、 亮度和饱和度） 颜色值的属性页。 [CMFCColorDialog::SetPageTwo](../../mfc/reference/cmfccolordialog-class.md#setpagetwo)方法框架初始化颜色对话框或用户按下鼠标左键时调用此方法。 有关详细信息`CMFCColorDialog`，请参阅[CMFCColorDialog 类](../../mfc/reference/cmfccolordialog-class.md)。

## <a name="see-also"></a>请参阅

[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[类](../../mfc/reference/mfc-classes.md)<br/>
[CMFCColorDialog 类](../../mfc/reference/cmfccolordialog-class.md)<br/>
[CMFCStandardColorsPropertyPage 类](../../mfc/reference/cmfcstandardcolorspropertypage-class.md)
