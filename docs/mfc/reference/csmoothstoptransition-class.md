---
title: CSmoothStopTransition 类
ms.date: 11/04/2016
f1_keywords:
- CSmoothStopTransition
- AFXANIMATIONCONTROLLER/CSmoothStopTransition
- AFXANIMATIONCONTROLLER/CSmoothStopTransition::CSmoothStopTransition
- AFXANIMATIONCONTROLLER/CSmoothStopTransition::Create
- AFXANIMATIONCONTROLLER/CSmoothStopTransition::m_dblFinalValue
- AFXANIMATIONCONTROLLER/CSmoothStopTransition::m_maximumDuration
helpviewer_keywords:
- CSmoothStopTransition [MFC], CSmoothStopTransition
- CSmoothStopTransition [MFC], Create
- CSmoothStopTransition [MFC], m_dblFinalValue
- CSmoothStopTransition [MFC], m_maximumDuration
ms.assetid: e1a4b476-6f96-43dd-90db-870a64406b85
ms.openlocfilehash: 0ba550b4a0b9443d0681e17195687fb94c207ace
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81318207"
---
# <a name="csmoothstoptransition-class"></a>CSmoothStopTransition 类

封装平稳停止转换。

## <a name="syntax"></a>语法

```
class CSmoothStopTransition : public CBaseTransition;
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[C"平滑停止转换"：：C"平滑停止转换"](#csmoothstoptransition)|构造平稳停止过渡并初始化其最大持续时间和最终值。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[C平滑停止转换：：创建](#create)|调用过渡库以创建封装的过渡 COM 对象。 （覆盖[CBase 转换：创建](../../mfc/reference/cbasetransition-class.md#create).）|

### <a name="public-data-members"></a>公共数据成员

|名称|说明|
|----------|-----------------|
|[C"平滑停止转换：：m_dblFinalValue](#m_dblfinalvalue)|过渡结束时动画变量的值。|
|[C"平滑停止转换：：m_maximumDuration](#m_maximumduration)|转换的最大持续时间。|

## <a name="remarks"></a>备注

平稳停止过渡在接近给定的最终值时变慢，并且以零的速度到达它。 转换的持续时间由初始速度、初始值和最终值之间的差异以及指定的最长持续时间决定。 如果没有由单个抛物线弧组成的解，则此方法将创建立方过渡。 由于所有转换都将自动清除，因此建议使用运算符 new 分配。 封装的 IUI动画转换 COM 对象由 C动画控制器：：AnimateGroup 创建，直到此为止，它才为 NULL。 创建此 COM 对象后更改成员变量不起作用。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CBase 转换](../../mfc/reference/cbasetransition-class.md)

[C平滑停止转换](../../mfc/reference/csmoothstoptransition-class.md)

## <a name="requirements"></a>要求

**标头：** afxanimationcontroller.h

## <a name="csmoothstoptransitioncreate"></a><a name="create"></a>C平滑停止转换：：创建

调用过渡库以创建封装的过渡 COM 对象。

```
virtual BOOL Create(
    IUIAnimationTransitionLibrary* pLibrary,
    IUIAnimationTransitionFactory* \*not used*\);
```

### <a name="parameters"></a>参数

*p库*<br/>
指向过渡库的指针，它负责创建标准转换。

### <a name="return-value"></a>返回值

如果成功创建转换，则为 TRUE;如果成功创建转换，则为 TRUE。否则 FALSE。

## <a name="csmoothstoptransitioncsmoothstoptransition"></a><a name="csmoothstoptransition"></a>C"平滑停止转换"：：C"平滑停止转换"

构造平稳停止过渡并初始化其最大持续时间和最终值。

```
CSmoothStopTransition(
    UI_ANIMATION_SECONDS maximumDuration,
    DOUBLE dblFinalValue);
```

### <a name="parameters"></a>参数

*最大持续时间*<br/>
转换的最大持续时间。

*dbl 最终值*<br/>
过渡结束时动画变量的值。

## <a name="csmoothstoptransitionm_dblfinalvalue"></a><a name="m_dblfinalvalue"></a>C"平滑停止转换：：m_dblFinalValue

过渡结束时动画变量的值。

```
DOUBLE m_dblFinalValue;
```

## <a name="csmoothstoptransitionm_maximumduration"></a><a name="m_maximumduration"></a>C"平滑停止转换：：m_maximumDuration

转换的最大持续时间。

```
UI_ANIMATION_SECONDS m_maximumDuration;
```

## <a name="see-also"></a>另请参阅

[类](../../mfc/reference/mfc-classes.md)
