---
title: Cacceleratedeceleratetransition 类类
ms.date: 11/04/2016
f1_keywords:
- CAccelerateDecelerateTransition
- afxanimationcontroller/CAccelerateDecelerateTransition
helpviewer_keywords:
- CAccelerateDecelerateTransition class [MFC]
ms.assetid: b1f31ee8-bb11-4ccc-b124-365fb02b025c
ms.openlocfilehash: dbebe794ba76ae4abd3d1e3ea6bc8ee31bc3007f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62151196"
---
# <a name="cacceleratedeceleratetransition-class"></a>Cacceleratedeceleratetransition 类类

实现加速-减速转换。

## <a name="syntax"></a>语法

```
class CAccelerateDecelerateTransition : public CBaseTransition;
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[CAccelerateDecelerateTransition::CAccelerateDecelerateTransition](#cacceleratedeceleratetransition)|构造一个转换对象。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CAccelerateDecelerateTransition::Create](#create)|调用要创建封装的转换 COM 对象的转换库。 (重写[CBaseTransition::Create](../../mfc/reference/cbasetransition-class.md#create)。)|

### <a name="public-data-members"></a>公共数据成员

|名称|描述|
|----------|-----------------|
|[CAccelerateDecelerateTransition::m_accelerationRatio](#m_accelerationratio)|持续时间为所用的时间的比率。|
|[CAccelerateDecelerateTransition::m_decelerationRatio](#m_decelerationratio)|持续时间减速所用的时间的比率。|
|[CAccelerateDecelerateTransition::m_duration](#m_duration)|过渡的持续时间。|
|[CAccelerateDecelerateTransition::m_finalValue](#m_finalvalue)|转换结束时的动画变量的值。|

## <a name="remarks"></a>备注

在包含加速-减速转换、 动画变量的速度并再减速的转换，结束时间的指定值的持续时间内。 您可以控制如何快速变量独立加速和减速，通过指定不同的加速和减速比率。 初始速度为零，加速比率时，该变量将用于加速; 的持续时间的比例同样与的减速度比。 如果初始速度为非零，则速度接近零和转换结束之间的时间部分。 加速比率和减速度比应总和为 1.0 的最大值。 因为会自动清除所有转换，我们建议分配它们使用新运算符。 封装 IUIAnimationTransition 创建 COM 对象通过 CAnimationController::AnimateGroup，直到它为 NULL。 创建此 COM 对象不起作用之后更改成员变量。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CBaseTransition](../../mfc/reference/cbasetransition-class.md)

`CAccelerateDecelerateTransition`

## <a name="requirements"></a>要求

**标头：** afxanimationcontroller.h

##  <a name="cacceleratedeceleratetransition"></a>  CAccelerateDecelerateTransition::CAccelerateDecelerateTransition

构造一个转换对象。

```
CAccelerateDecelerateTransition(
    UI_ANIMATION_SECONDS duration,
    DOUBLE finalValue,
    DOUBLE accelerationRatio = 0.3,
    DOUBLE decelerationRatio = 0.3);
```

### <a name="parameters"></a>参数

*duration*<br/>
过渡的持续时间。

*finalValue*<br/>
转换结束时的动画变量的值。

*accelerationRatio*<br/>
持续时间为所用的时间的比率。

*decelerationRatio*<br/>
持续时间减速所用的时间的比率。

##  <a name="create"></a>  CAccelerateDecelerateTransition::Create

调用要创建封装的转换 COM 对象的转换库。

```
virtual BOOL Create(
    IUIAnimationTransitionLibrary* pLibrary,
    IUIAnimationTransitionFactory* *\not used*\);
```

### <a name="parameters"></a>参数

*pLibrary*<br/>
一个指向[IUIAnimationTransitionLibrary 接口](/windows/desktop/api/uianimation/nn-uianimation-iuianimationtransitionlibrary)，用于定义的标准转换库。

### <a name="return-value"></a>返回值

如果成功，则创建转换，则返回 TRUE否则为 FALSE。

##  <a name="m_accelerationratio"></a>  CAccelerateDecelerateTransition::m_accelerationRatio

持续时间为所用的时间的比率。

```
DOUBLE m_accelerationRatio;
```

##  <a name="m_decelerationratio"></a>  CAccelerateDecelerateTransition::m_decelerationRatio

持续时间减速所用的时间的比率。

```
DOUBLE m_decelerationRatio;
```

##  <a name="m_duration"></a>  CAccelerateDecelerateTransition::m_duration

过渡的持续时间。

```
UI_ANIMATION_SECONDS m_duration;
```

##  <a name="m_finalvalue"></a>  CAccelerateDecelerateTransition::m_finalValue

转换结束时的动画变量的值。

```
DOUBLE m_finalValue;
```

## <a name="see-also"></a>请参阅

[类](../../mfc/reference/mfc-classes.md)
