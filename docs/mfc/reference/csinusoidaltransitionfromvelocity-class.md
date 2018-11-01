---
title: CSinusoidalTransitionFromVelocity 类
ms.date: 11/04/2016
f1_keywords:
- CSinusoidalTransitionFromVelocity
- AFXANIMATIONCONTROLLER/CSinusoidalTransitionFromVelocity
- AFXANIMATIONCONTROLLER/CSinusoidalTransitionFromVelocity::CSinusoidalTransitionFromVelocity
- AFXANIMATIONCONTROLLER/CSinusoidalTransitionFromVelocity::Create
- AFXANIMATIONCONTROLLER/CSinusoidalTransitionFromVelocity::m_duration
- AFXANIMATIONCONTROLLER/CSinusoidalTransitionFromVelocity::m_period
helpviewer_keywords:
- CSinusoidalTransitionFromVelocity [MFC], CSinusoidalTransitionFromVelocity
- CSinusoidalTransitionFromVelocity [MFC], Create
- CSinusoidalTransitionFromVelocity [MFC], m_duration
- CSinusoidalTransitionFromVelocity [MFC], m_period
ms.assetid: cc885f17-b84b-45ee-8f1f-36a8bbb7adad
ms.openlocfilehash: 585ffcf787b2e1156b4f0b9f6444b15a4d5bfc54
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50500511"
---
# <a name="csinusoidaltransitionfromvelocity-class"></a>CSinusoidalTransitionFromVelocity 类

封装其幅度由动画变量的初始速度决定的正弦速度转换。

## <a name="syntax"></a>语法

```
class CSinusoidalTransitionFromVelocity : public CBaseTransition;
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[CSinusoidalTransitionFromVelocity::CSinusoidalTransitionFromVelocity](#csinusoidaltransitionfromvelocity)|构造一个转换对象。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CSinusoidalTransitionFromVelocity::Create](#create)|调用要创建封装的转换 COM 对象的转换库。 (重写[CBaseTransition::Create](../../mfc/reference/cbasetransition-class.md#create)。)|

### <a name="public-data-members"></a>公共数据成员

|名称|描述|
|----------|-----------------|
|[CSinusoidalTransitionFromVelocity::m_duration](#m_duration)|过渡的持续时间。|
|[CSinusoidalTransitionFromVelocity::m_period](#m_period)|以秒为单位的正弦波振荡的段。|

## <a name="remarks"></a>备注

正弦范围转换在整个持续时间内，初始值两边摆动动画变量的值。 该转换开始时由动画变量的速度决定振荡的幅度。 因为会自动清除所有转换，我们建议分配它们使用新运算符。 封装 IUIAnimationTransition 创建 COM 对象通过 CAnimationController::AnimateGroup，直到它为 NULL。 创建此 COM 对象不起作用之后更改成员变量。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CBaseTransition](../../mfc/reference/cbasetransition-class.md)

[CSinusoidalTransitionFromVelocity](../../mfc/reference/csinusoidaltransitionfromvelocity-class.md)

## <a name="requirements"></a>要求

**标头：** afxanimationcontroller.h

##  <a name="create"></a>  CSinusoidalTransitionFromVelocity::Create

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

##  <a name="csinusoidaltransitionfromvelocity"></a>  CSinusoidalTransitionFromVelocity::CSinusoidalTransitionFromVelocity

构造一个转换对象。

```
CSinusoidalTransitionFromVelocity(
    UI_ANIMATION_SECONDS duration,
    UI_ANIMATION_SECONDS period);
```

### <a name="parameters"></a>参数

*持续时间*<br/>
过渡的持续时间。

*段*<br/>
以秒为单位的正弦波振荡的段。

##  <a name="m_duration"></a>  CSinusoidalTransitionFromVelocity::m_duration

过渡的持续时间。

```
UI_ANIMATION_SECONDS m_duration;
```

##  <a name="m_period"></a>  CSinusoidalTransitionFromVelocity::m_period

以秒为单位的正弦波振荡的段。

```
UI_ANIMATION_SECONDS m_period;
```

## <a name="see-also"></a>请参阅

[类](../../mfc/reference/mfc-classes.md)
