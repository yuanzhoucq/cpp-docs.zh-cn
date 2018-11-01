---
title: CSinusoidalTransitionFromRange 类
ms.date: 11/04/2016
f1_keywords:
- CSinusoidalTransitionFromRange
- AFXANIMATIONCONTROLLER/CSinusoidalTransitionFromRange
- AFXANIMATIONCONTROLLER/CSinusoidalTransitionFromRange::CSinusoidalTransitionFromRange
- AFXANIMATIONCONTROLLER/CSinusoidalTransitionFromRange::Create
- AFXANIMATIONCONTROLLER/CSinusoidalTransitionFromRange::m_dblMaximumValue
- AFXANIMATIONCONTROLLER/CSinusoidalTransitionFromRange::m_dblMinimumValue
- AFXANIMATIONCONTROLLER/CSinusoidalTransitionFromRange::m_duration
- AFXANIMATIONCONTROLLER/CSinusoidalTransitionFromRange::m_period
- AFXANIMATIONCONTROLLER/CSinusoidalTransitionFromRange::m_slope
helpviewer_keywords:
- CSinusoidalTransitionFromRange [MFC], CSinusoidalTransitionFromRange
- CSinusoidalTransitionFromRange [MFC], Create
- CSinusoidalTransitionFromRange [MFC], m_dblMaximumValue
- CSinusoidalTransitionFromRange [MFC], m_dblMinimumValue
- CSinusoidalTransitionFromRange [MFC], m_duration
- CSinusoidalTransitionFromRange [MFC], m_period
- CSinusoidalTransitionFromRange [MFC], m_slope
ms.assetid: 8b66a729-5f10-431a-b055-e3600d0065da
ms.openlocfilehash: 20e910dfa34e90af2c8a2765947ad85a2465c596
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50477579"
---
# <a name="csinusoidaltransitionfromrange-class"></a>CSinusoidalTransitionFromRange 类

封装具有给定振动范围的正弦范围转换。

## <a name="syntax"></a>语法

```
class CSinusoidalTransitionFromRange : public CBaseTransition;
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[CSinusoidalTransitionFromRange::CSinusoidalTransitionFromRange](#csinusoidaltransitionfromrange)|构造一个转换对象。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CSinusoidalTransitionFromRange::Create](#create)|调用要创建封装的转换 COM 对象的转换库。 (重写[CBaseTransition::Create](../../mfc/reference/cbasetransition-class.md#create)。)|

### <a name="public-data-members"></a>公共数据成员

|名称|描述|
|----------|-----------------|
|[CSinusoidalTransitionFromRange::m_dblMaximumValue](#m_dblmaximumvalue)|在高峰期的正弦波次的动画变量的值。|
|[CSinusoidalTransitionFromRange::m_dblMinimumValue](#m_dblminimumvalue)|在通过正弦波的动画变量的值。|
|[CSinusoidalTransitionFromRange::m_duration](#m_duration)|过渡的持续时间。|
|[CSinusoidalTransitionFromRange::m_period](#m_period)|以秒为单位的正弦波振荡的段。|
|[CSinusoidalTransitionFromRange::m_slope](#m_slope)|在过渡的开头增量的斜率。|

## <a name="remarks"></a>备注

通过正弦范围转换的整个持续时间指定的最小值和最大值之间波动动画变量的值。 增量的斜率参数用于消除其他参数指定两个可能正弦波之间的歧义。 因为会自动清除所有转换，我们建议分配它们使用新运算符。 封装 IUIAnimationTransition 创建 COM 对象通过 CAnimationController::AnimateGroup，直到它为 NULL。 创建此 COM 对象不起作用之后更改成员变量。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CBaseTransition](../../mfc/reference/cbasetransition-class.md)

[CSinusoidalTransitionFromRange](../../mfc/reference/csinusoidaltransitionfromrange-class.md)

## <a name="requirements"></a>要求

**标头：** afxanimationcontroller.h

##  <a name="create"></a>  CSinusoidalTransitionFromRange::Create

调用要创建封装的转换 COM 对象的转换库。

```
virtual BOOL Create(
    IUIAnimationTransitionLibrary* pLibrary,
    IUIAnimationTransitionFactory* \*not used*\);
```

### <a name="parameters"></a>参数

*pLibrary*<br/>
指向转换库，负责创建标准转换的指针。

### <a name="return-value"></a>返回值

如果成功，则创建转换，则返回 TRUE否则为 FALSE。

##  <a name="csinusoidaltransitionfromrange"></a>  CSinusoidalTransitionFromRange::CSinusoidalTransitionFromRange

构造一个转换对象。

```
CSinusoidalTransitionFromRange(
    UI_ANIMATION_SECONDS duration,
    DOUBLE dblMinimumValue,
    DOUBLE dblMaximumValue,
    UI_ANIMATION_SECONDS period,
    UI_ANIMATION_SLOPE slope);
```

### <a name="parameters"></a>参数

*持续时间*<br/>
过渡的持续时间。

*dblMinimumValue*<br/>
在通过正弦波的动画变量的值。

*dblMaximumValue*<br/>
在高峰期的正弦波次的动画变量的值。

*段*<br/>
以秒为单位的正弦波振荡的段。

*增量的斜率*<br/>
在过渡的开头增量的斜率。

##  <a name="m_dblmaximumvalue"></a>  CSinusoidalTransitionFromRange::m_dblMaximumValue

在高峰期的正弦波次的动画变量的值。

```
DOUBLE m_dblMaximumValue;
```

##  <a name="m_dblminimumvalue"></a>  CSinusoidalTransitionFromRange::m_dblMinimumValue

在通过正弦波的动画变量的值。

```
DOUBLE m_dblMinimumValue;
```

##  <a name="m_duration"></a>  CSinusoidalTransitionFromRange::m_duration

过渡的持续时间。

```
UI_ANIMATION_SECONDS m_duration;
```

##  <a name="m_period"></a>  CSinusoidalTransitionFromRange::m_period

以秒为单位的正弦波振荡的段。

```
UI_ANIMATION_SECONDS m_period;
```

##  <a name="m_slope"></a>  CSinusoidalTransitionFromRange::m_slope

在过渡的开头增量的斜率。

```
UI_ANIMATION_SLOPE m_slope;
```

## <a name="see-also"></a>请参阅

[类](../../mfc/reference/mfc-classes.md)
