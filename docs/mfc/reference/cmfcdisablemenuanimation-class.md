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
ms.openlocfilehash: c6d81f253016d3a292dd50b16c19f76a05e75e56
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/22/2020
ms.locfileid: "81752415"
---
# <a name="cmfcdisablemenuanimation-class"></a>CMFCDisableMenuAnimation 类

禁用弹出式菜单动画。

## <a name="syntax"></a>语法

```
class CMFCDisableMenuAnimation
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|||
|-|-|
|名称|说明|
|`CMFCDisableMenuAnimation::CMFCDisableMenuAnimation`|构造 `CMFCDisableMenuAnimation` 对象。|
|`CMFCDisableMenuAnimation::~CMFCDisableMenuAnimation`|析构函数。|

### <a name="public-methods"></a>公共方法

|||
|-|-|
|名称|说明|
|[CMFC禁用菜单动画：：恢复](#restore)|还原框架用于显示弹出式菜单的上一个动画。|

### <a name="data-members"></a>数据成员

|||
|-|-|
|名称|说明|
|`CMFCDisableMenuAnimation::m_animType`|存储以前的弹出式菜单动画类型。|

### <a name="remarks"></a>备注

使用此帮助器类可暂时禁用弹出式菜单动画（例如，处理鼠标或键盘命令时）。

对象`CMFCDisableMenuAnimation`在其生存期内禁用弹出式菜单动画。 构造函数将当前弹出式菜单动画类型存储在字段中，`m_animType`并将当前动画类型设置为`CMFCPopupMenu::NO_ANIMATION`。 析构函数还原以前的动画类型。

您可以在堆栈上`CMFCDisableMenuAnimation`创建对象，以在整个单个函数中禁用弹出菜单动画。 如果要在函数之间禁用弹出菜单动画，请在堆上创建`CMFCDisableMenuAnimation`一个对象，然后在要还原弹出菜单动画时将其删除。

## <a name="example"></a>示例

下面的示例演示如何使用堆栈临时禁用菜单动画。

[!code-cpp[NVC_MFC_Misc#1](../../mfc/reference/codesnippet/cpp/cmfcdisablemenuanimation-class_1.h)]

## <a name="inheritance-hierarchy"></a>继承层次结构

[CMFC禁用菜单动画](../../mfc/reference/cmfcdisablemenuanimation-class.md)

## <a name="requirements"></a>要求

**标题：** afxpopupmenu.h

## <a name="cmfcdisablemenuanimationrestore"></a><a name="restore"></a>CMFC禁用菜单动画：：恢复

还原框架用于显示弹出式菜单的上一个动画。

```cpp
void Restore ();
```

### <a name="remarks"></a>备注

`CMFCDisableMenuAnimation`析构函数调用此方法以还原框架用于显示弹出式菜单的上一个动画。

## <a name="see-also"></a>请参阅

[层次结构图表](../../mfc/hierarchy-chart.md)<br/>
[类](../../mfc/reference/mfc-classes.md)<br/>
[CMFCPopupMenu 类](../../mfc/reference/cmfcpopupmenu-class.md)
