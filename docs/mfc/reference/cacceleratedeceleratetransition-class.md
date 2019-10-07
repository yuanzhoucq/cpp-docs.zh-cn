---
title: CAccelerateDecelerateTransition 类
ms.date: 11/04/2016
f1_keywords:
- CAccelerateDecelerateTransition
- afxanimationcontroller/CAccelerateDecelerateTransition
helpviewer_keywords:
- CAccelerateDecelerateTransition class [MFC]
ms.assetid: b1f31ee8-bb11-4ccc-b124-365fb02b025c
ms.openlocfilehash: 1e55e81b4d9b5c324f86bfd141b74d9faa362d94
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69507742"
---
# <a name="cacceleratedeceleratetransition-class"></a>CAccelerateDecelerateTransition 类

实现加速-减速转换。

## <a name="syntax"></a>语法

```
class CAccelerateDecelerateTransition : public CBaseTransition;
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[CAccelerateDecelerateTransition::CAccelerateDecelerateTransition](#cacceleratedeceleratetransition)|构造转换对象。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CAccelerateDecelerateTransition::Create](#create)|调用转换库以创建封装的转换 COM 对象。 (重写[CBaseTransition:: Create](../../mfc/reference/cbasetransition-class.md#create)。)|

### <a name="public-data-members"></a>公共数据成员

|名称|描述|
|----------|-----------------|
|[CAccelerateDecelerateTransition::m_accelerationRatio](#m_accelerationratio)|加速到持续时间所花费的时间的比率。|
|[CAccelerateDecelerateTransition::m_decelerationRatio](#m_decelerationratio)|减速花费的时间与持续时间的比率。|
|[CAccelerateDecelerateTransition::m_duration](#m_duration)|转换的持续时间。|
|[CAccelerateDecelerateTransition::m_finalValue](#m_finalvalue)|转换结束时动画变量的值。|

## <a name="remarks"></a>备注

在加速减速转换期间, 动画变量会加速, 然后在转换的持续时间内减速, 并以指定的值结束。 可以通过指定不同的加速和减速比率, 来控制变量加速和减速的速度。 当初始速度为零时, 加速度比是变量将在加速中花费的持续时间的小数部分;同样, 采用减速度率。 如果初始速度非零, 则它是速度达到零和转换结束之间的时间的小数部分。 加速比率和减速度比率应最大为1.0。 由于所有转换都将自动清除, 因此建议使用 operator new 将其分配给它们。 封装的 IUIAnimationTransition COM 对象由 CAnimationController:: AnimateGroup 创建, 直到它为 NULL。 在创建此 COM 对象之后更改成员变量不起作用。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CBaseTransition](../../mfc/reference/cbasetransition-class.md)

`CAccelerateDecelerateTransition`

## <a name="requirements"></a>要求

**标头：** afxanimationcontroller.h

##  <a name="cacceleratedeceleratetransition"></a>CAccelerateDecelerateTransition::CAccelerateDecelerateTransition

构造转换对象。

```
CAccelerateDecelerateTransition(
    UI_ANIMATION_SECONDS duration,
    DOUBLE finalValue,
    DOUBLE accelerationRatio = 0.3,
    DOUBLE decelerationRatio = 0.3);
```

### <a name="parameters"></a>参数

*duration*<br/>
转换的持续时间。

*finalValue*<br/>
转换结束时动画变量的值。

*accelerationRatio*<br/>
加速到持续时间所花费的时间的比率。

*decelerationRatio*<br/>
减速花费的时间与持续时间的比率。

##  <a name="create"></a>  CAccelerateDecelerateTransition::Create

调用转换库以创建封装的转换 COM 对象。

```
virtual BOOL Create(
    IUIAnimationTransitionLibrary* pLibrary,
    IUIAnimationTransitionFactory* *\not used*\);
```

### <a name="parameters"></a>参数

*pLibrary*<br/>
指向[IUIAnimationTransitionLibrary 接口](/windows/win32/api/uianimation/nn-uianimation-iuianimationtransitionlibrary)的指针, 该接口定义标准转换库。

### <a name="return-value"></a>返回值

如果成功创建转换, 则为 TRUE;否则为 FALSE。

##  <a name="m_accelerationratio"></a>  CAccelerateDecelerateTransition::m_accelerationRatio

加速到持续时间所花费的时间的比率。

```
DOUBLE m_accelerationRatio;
```

##  <a name="m_decelerationratio"></a>  CAccelerateDecelerateTransition::m_decelerationRatio

减速花费的时间与持续时间的比率。

```
DOUBLE m_decelerationRatio;
```

##  <a name="m_duration"></a>  CAccelerateDecelerateTransition::m_duration

转换的持续时间。

```
UI_ANIMATION_SECONDS m_duration;
```

##  <a name="m_finalvalue"></a>CAccelerateDecelerateTransition::m_finalValue

转换结束时动画变量的值。

```
DOUBLE m_finalValue;
```

## <a name="see-also"></a>请参阅

[类](../../mfc/reference/mfc-classes.md)
