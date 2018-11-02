---
title: CMFCDisableMenuAnimation 类
ms.date: 11/04/2016
f1_keywords:
- CMFCDisableMenuAnimation
- AFXPOPUPMENU/CMFCDisableMenuAnimation
- AFXPOPUPMENU/CMFCDisableMenuAnimation::Restore
helpviewer_keywords:
- CMFCDisableMenuAnimation [MFC], Restore
ms.assetid: c6eb07da-c382-43d6-8028-007f2320e50e
ms.openlocfilehash: 0b0df30d48b2f77d620b00f67d40743445981b66
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50665031"
---
# <a name="cmfcdisablemenuanimation-class"></a>CMFCDisableMenuAnimation 类

禁用弹出菜单动画。

## <a name="syntax"></a>语法

```
class CMFCDisableMenuAnimation
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|||
|-|-|
|名称|描述|
|`CMFCDisableMenuAnimation::CMFCDisableMenuAnimation`|构造 `CMFCDisableMenuAnimation` 对象。|
|`CMFCDisableMenuAnimation::~CMFCDisableMenuAnimation`|析构函数。|

### <a name="public-methods"></a>公共方法

|||
|-|-|
|名称|描述|
|[CMFCDisableMenuAnimation::Restore](#restore)|还原前一个动画的框架用于显示一个弹出菜单。|

### <a name="data-members"></a>数据成员

|||
|-|-|
|name|描述|
|`CMFCDisableMenuAnimation::m_animType`|将存储以前的弹出菜单动画类型。|

### <a name="remarks"></a>备注

使用此帮助器类来暂时禁用弹出菜单动画 （例如，当处理鼠标或键盘命令）。

一个`CMFCDisableMenuAnimation`对象禁用弹出菜单动画在其生存期内。 构造函数将存储在当前的弹出菜单动画类型`m_animType`字段中并设置当前的动画类型到`CMFCPopupMenu::NO_ANIMATION`。 析构函数将还原以前的动画类型。

您可以创建`CMFCDisableMenuAnimation`禁用整个单个函数的弹出菜单动画在堆栈上的对象。 如果你想要禁用函数之间的弹出菜单动画，创建`CMFCDisableMenuAnimation`堆上对象，然后将其删除时你想要还原的弹出菜单动画。

## <a name="example"></a>示例

下面的示例演示如何使用堆栈来暂时禁用菜单动画。

[!code-cpp[NVC_MFC_Misc#1](../../mfc/reference/codesnippet/cpp/cmfcdisablemenuanimation-class_1.h)]

## <a name="inheritance-hierarchy"></a>继承层次结构

[CMFCDisableMenuAnimation](../../mfc/reference/cmfcdisablemenuanimation-class.md)

## <a name="requirements"></a>要求

**标头：** afxpopupmenu.h

##  <a name="restore"></a>  CMFCDisableMenuAnimation::Restore

还原前一个动画的框架用于显示一个弹出菜单。

```
void Restore ();
```

### <a name="remarks"></a>备注

调用此方法`CMFCDisableMenuAnimation`析构函数以还原前一个动画的框架用于显示一个弹出菜单。

## <a name="see-also"></a>请参阅

[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[类](../../mfc/reference/mfc-classes.md)<br/>
[CMFCPopupMenu 类](../../mfc/reference/cmfcpopupmenu-class.md)
