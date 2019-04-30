---
title: CParabolicTransitionFromAcceleration 类
ms.date: 11/04/2016
f1_keywords:
- CParabolicTransitionFromAcceleration
- AFXANIMATIONCONTROLLER/CParabolicTransitionFromAcceleration
- AFXANIMATIONCONTROLLER/CParabolicTransitionFromAcceleration::CParabolicTransitionFromAcceleration
- AFXANIMATIONCONTROLLER/CParabolicTransitionFromAcceleration::Create
- AFXANIMATIONCONTROLLER/CParabolicTransitionFromAcceleration::m_dblAcceleration
- AFXANIMATIONCONTROLLER/CParabolicTransitionFromAcceleration::m_dblFinalValue
- AFXANIMATIONCONTROLLER/CParabolicTransitionFromAcceleration::m_dblFinalVelocity
helpviewer_keywords:
- CParabolicTransitionFromAcceleration [MFC], CParabolicTransitionFromAcceleration
- CParabolicTransitionFromAcceleration [MFC], Create
- CParabolicTransitionFromAcceleration [MFC], m_dblAcceleration
- CParabolicTransitionFromAcceleration [MFC], m_dblFinalValue
- CParabolicTransitionFromAcceleration [MFC], m_dblFinalVelocity
ms.assetid: 1e59b86f-358b-4da0-a4fd-8eaf5e85e00f
ms.openlocfilehash: 3d4a073a0fd74f7564d9183779acfd66b41a9540
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62372967"
---
# <a name="cparabolictransitionfromacceleration-class"></a>CParabolicTransitionFromAcceleration 类

封装抛物线加速转换。

## <a name="syntax"></a>语法

```
class CParabolicTransitionFromAcceleration : public CBaseTransition;
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[CParabolicTransitionFromAcceleration::CParabolicTransitionFromAcceleration](#cparabolictransitionfromacceleration)|构造一个抛物线加速转换并初始化使用指定的参数。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CParabolicTransitionFromAcceleration::Create](#create)|调用要创建封装的转换 COM 对象的转换库。 (重写[CBaseTransition::Create](../../mfc/reference/cbasetransition-class.md#create)。)|

### <a name="public-data-members"></a>公共数据成员

|名称|描述|
|----------|-----------------|
|[CParabolicTransitionFromAcceleration::m_dblAcceleration](#m_dblacceleration)|在转换期间的动画变量的加速度。|
|[CParabolicTransitionFromAcceleration::m_dblFinalValue](#m_dblfinalvalue)|转换结束时的动画变量的值。|
|[CParabolicTransitionFromAcceleration::m_dblFinalVelocity](#m_dblfinalvelocity)|转换结束时的动画变量的速度。|

## <a name="remarks"></a>备注

期间一个抛物线加速转换，动画变量的值从初始的值更改为结束时间指定速度的最终值。 您可以控制变量通过指定的加速的速率达到的最终值的速度。 因为会自动清除所有转换，我们建议分配它们使用新运算符。 封装 IUIAnimationTransition 创建 COM 对象通过 CAnimationController::AnimateGroup，直到它为 NULL。 创建此 COM 对象不起作用之后更改成员变量。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CBaseTransition](../../mfc/reference/cbasetransition-class.md)

[CParabolicTransitionFromAcceleration](../../mfc/reference/cparabolictransitionfromacceleration-class.md)

## <a name="requirements"></a>要求

**标头：** afxanimationcontroller.h

##  <a name="cparabolictransitionfromacceleration"></a>  CParabolicTransitionFromAcceleration::CParabolicTransitionFromAcceleration

构造一个抛物线加速转换并初始化使用指定的参数。

```
CParabolicTransitionFromAcceleration(
    DOUBLE dblFinalValue,
    DOUBLE dblFinalVelocity,
    DOUBLE dblAcceleration);
```

### <a name="parameters"></a>参数

*dblFinalValue*<br/>
转换结束时的动画变量的值。

*dblFinalVelocity*<br/>
转换结束时的动画变量的速度。

*dblAcceleration*<br/>
在转换期间的动画变量的加速度。

##  <a name="create"></a>  CParabolicTransitionFromAcceleration::Create

调用要创建封装的转换 COM 对象的转换库。

```
virtual BOOL Create(
    IUIAnimationTransitionLibrary* pLibrary,
    IUIAnimationTransitionFactory* /* not used */);
```

### <a name="parameters"></a>参数

*pLibrary*<br/>
指向转换库，负责创建标准转换的指针。

### <a name="return-value"></a>返回值

如果成功，则创建转换，则返回 TRUE否则为 FALSE。

##  <a name="m_dblacceleration"></a>  CParabolicTransitionFromAcceleration::m_dblAcceleration

在转换期间的动画变量的加速度。

```
DOUBLE m_dblAcceleration;
```

##  <a name="m_dblfinalvalue"></a>  CParabolicTransitionFromAcceleration::m_dblFinalValue

转换结束时的动画变量的值。

```
DOUBLE m_dblFinalValue;
```

##  <a name="m_dblfinalvelocity"></a>  CParabolicTransitionFromAcceleration::m_dblFinalVelocity

转换结束时的动画变量的速度。

```
DOUBLE m_dblFinalVelocity;
```

## <a name="see-also"></a>请参阅

[类](../../mfc/reference/mfc-classes.md)
