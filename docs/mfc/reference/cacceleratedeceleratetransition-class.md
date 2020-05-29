---
title: C加速减速转换类
ms.date: 11/04/2016
f1_keywords:
- CAccelerateDecelerateTransition
- afxanimationcontroller/CAccelerateDecelerateTransition
helpviewer_keywords:
- CAccelerateDecelerateTransition class [MFC]
ms.assetid: b1f31ee8-bb11-4ccc-b124-365fb02b025c
ms.openlocfilehash: 356ba30e6d9a638672d2c356676735ebfaed8f3e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371152"
---
# <a name="cacceleratedeceleratetransition-class"></a>C加速减速转换类

实现加速-减速转换。

## <a name="syntax"></a>语法

```
class CAccelerateDecelerateTransition : public CBaseTransition;
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[C加速减速转换：：C加速减速转换](#cacceleratedeceleratetransition)|构造过渡对象。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[C加速减速转换：：创建](#create)|调用过渡库以创建封装的过渡 COM 对象。 （覆盖[CBase 转换：创建](../../mfc/reference/cbasetransition-class.md#create).）|

### <a name="public-data-members"></a>公共数据成员

|名称|说明|
|----------|-----------------|
|[C加速减速转换：：m_accelerationRatio](#m_accelerationratio)|加速时间与持续时间的比率。|
|[C加速减速转换：：m_decelerationRatio](#m_decelerationratio)|减速时间与持续时间的比率。|
|[C加速减速转换：：m_duration](#m_duration)|转换的持续时间。|
|[C加速减速转换：：m_finalValue](#m_finalvalue)|过渡结束时动画变量的值。|

## <a name="remarks"></a>备注

在加速减速转换期间，动画变量会加速，然后在转换期间减慢速度，以指定值结束。 通过指定不同的加速和减速比，您可以控制变量独立加速和减速的速度。 当初始速度为零时，加速度比是变量将加速花费的持续时间的一小部分;同样与减速率。 如果初始速度是非零，则它是速度达到零和过渡结束之间的时间分数。 加速度比和减速率应总和为最大 1.0。 由于所有转换都将自动清除，因此建议使用运算符 new 分配。 封装的 IUI动画转换 COM 对象由 C动画控制器：：AnimateGroup 创建，直到此为止，它才为 NULL。 创建此 COM 对象后更改成员变量不起作用。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CBase 转换](../../mfc/reference/cbasetransition-class.md)

`CAccelerateDecelerateTransition`

## <a name="requirements"></a>要求

**标头：** afxanimationcontroller.h

## <a name="cacceleratedeceleratetransitioncacceleratedeceleratetransition"></a><a name="cacceleratedeceleratetransition"></a>C加速减速转换：：C加速减速转换

构造过渡对象。

```
CAccelerateDecelerateTransition(
    UI_ANIMATION_SECONDS duration,
    DOUBLE finalValue,
    DOUBLE accelerationRatio = 0.3,
    DOUBLE decelerationRatio = 0.3);
```

### <a name="parameters"></a>参数

*时间*<br/>
转换的持续时间。

*最终价值*<br/>
过渡结束时动画变量的值。

*加速度比*<br/>
加速时间与持续时间的比率。

*减速比*<br/>
减速时间与持续时间的比率。

## <a name="cacceleratedeceleratetransitioncreate"></a><a name="create"></a>C加速减速转换：：创建

调用过渡库以创建封装的过渡 COM 对象。

```
virtual BOOL Create(
    IUIAnimationTransitionLibrary* pLibrary,
    IUIAnimationTransitionFactory* *\not used*\);
```

### <a name="parameters"></a>参数

*p库*<br/>
指向[IUIAnimation 转换库接口](/windows/win32/api/uianimation/nn-uianimation-iuianimationtransitionlibrary)的指针，该接口定义标准转换库。

### <a name="return-value"></a>返回值

如果成功创建转换，则为 TRUE;如果成功创建转换，则为 TRUE。否则 FALSE。

## <a name="cacceleratedeceleratetransitionm_accelerationratio"></a><a name="m_accelerationratio"></a>C加速减速转换：：m_accelerationRatio

加速时间与持续时间的比率。

```
DOUBLE m_accelerationRatio;
```

## <a name="cacceleratedeceleratetransitionm_decelerationratio"></a><a name="m_decelerationratio"></a>C加速减速转换：：m_decelerationRatio

减速时间与持续时间的比率。

```
DOUBLE m_decelerationRatio;
```

## <a name="cacceleratedeceleratetransitionm_duration"></a><a name="m_duration"></a>C加速减速转换：：m_duration

转换的持续时间。

```
UI_ANIMATION_SECONDS m_duration;
```

## <a name="cacceleratedeceleratetransitionm_finalvalue"></a><a name="m_finalvalue"></a>C加速减速转换：：m_finalValue

过渡结束时动画变量的值。

```
DOUBLE m_finalValue;
```

## <a name="see-also"></a>另请参阅

[类](../../mfc/reference/mfc-classes.md)
