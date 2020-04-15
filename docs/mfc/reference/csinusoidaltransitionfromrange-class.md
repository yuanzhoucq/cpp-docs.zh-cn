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
ms.openlocfilehash: 0612a4b365b928d3c9be6d76168a76b4ee1caa85
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81318258"
---
# <a name="csinusoidaltransitionfromrange-class"></a>CSinusoidalTransitionFromRange 类

封装具有给定振动范围的正弦范围转换。

## <a name="syntax"></a>语法

```
class CSinusoidalTransitionFromRange : public CBaseTransition;
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[从范围转换的CSinusoid转换：从范围转换的CSinusoid](#csinusoidaltransitionfromrange)|构造过渡对象。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CSinusoid 从范围转换：创建](#create)|调用过渡库以创建封装的过渡 COM 对象。 （覆盖[CBase 转换：创建](../../mfc/reference/cbasetransition-class.md#create).）|

### <a name="public-data-members"></a>公共数据成员

|名称|说明|
|----------|-----------------|
|[CSinusoid 从范围转换：：m_dblMaximumValue](#m_dblmaximumvalue)|正弦波峰值处动画变量的值。|
|[CSinusoid 从范围转换：：m_dblMinimumValue](#m_dblminimumvalue)|正弦波槽处动画变量的值。|
|[CSinusoid 从范围转换：：m_duration](#m_duration)|转换的持续时间。|
|[CSinusoid 从范围转换：：m_period](#m_period)|正弦波的振荡周期（以秒为单位）。|
|[CSinusoid 从范围转换：：m_slope](#m_slope)|过渡开始时的斜率。|

## <a name="remarks"></a>备注

动画变量的值在正弦范围转换的整个持续时间内在指定的最小值和最大值之间波动。 坡度参数用于消除其他参数指定的两个可能的正子波之间的歧义。 由于所有转换都将自动清除，因此建议使用运算符 new 分配。 封装的 IUI动画转换 COM 对象由 C动画控制器：：AnimateGroup 创建，直到此为止，它才为 NULL。 创建此 COM 对象后更改成员变量不起作用。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CBase 转换](../../mfc/reference/cbasetransition-class.md)

[从范围转换的 CSinusoid](../../mfc/reference/csinusoidaltransitionfromrange-class.md)

## <a name="requirements"></a>要求

**标头：** afxanimationcontroller.h

## <a name="csinusoidaltransitionfromrangecreate"></a><a name="create"></a>CSinusoid 从范围转换：创建

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

## <a name="csinusoidaltransitionfromrangecsinusoidaltransitionfromrange"></a><a name="csinusoidaltransitionfromrange"></a>从范围转换的CSinusoid转换：从范围转换的CSinusoid

构造过渡对象。

```
CSinusoidalTransitionFromRange(
    UI_ANIMATION_SECONDS duration,
    DOUBLE dblMinimumValue,
    DOUBLE dblMaximumValue,
    UI_ANIMATION_SECONDS period,
    UI_ANIMATION_SLOPE slope);
```

### <a name="parameters"></a>参数

*时间*<br/>
转换的持续时间。

*最小值*<br/>
正弦波槽处动画变量的值。

*最大值*<br/>
正弦波峰值处动画变量的值。

*时期*<br/>
正弦波的振荡周期（以秒为单位）。

*边坡*<br/>
过渡开始时的斜率。

## <a name="csinusoidaltransitionfromrangem_dblmaximumvalue"></a><a name="m_dblmaximumvalue"></a>CSinusoid 从范围转换：：m_dblMaximumValue

正弦波峰值处动画变量的值。

```
DOUBLE m_dblMaximumValue;
```

## <a name="csinusoidaltransitionfromrangem_dblminimumvalue"></a><a name="m_dblminimumvalue"></a>CSinusoid 从范围转换：：m_dblMinimumValue

正弦波槽处动画变量的值。

```
DOUBLE m_dblMinimumValue;
```

## <a name="csinusoidaltransitionfromrangem_duration"></a><a name="m_duration"></a>CSinusoid 从范围转换：：m_duration

转换的持续时间。

```
UI_ANIMATION_SECONDS m_duration;
```

## <a name="csinusoidaltransitionfromrangem_period"></a><a name="m_period"></a>CSinusoid 从范围转换：：m_period

正弦波的振荡周期（以秒为单位）。

```
UI_ANIMATION_SECONDS m_period;
```

## <a name="csinusoidaltransitionfromrangem_slope"></a><a name="m_slope"></a>CSinusoid 从范围转换：：m_slope

过渡开始时的斜率。

```
UI_ANIMATION_SLOPE m_slope;
```

## <a name="see-also"></a>另请参阅

[类](../../mfc/reference/mfc-classes.md)
