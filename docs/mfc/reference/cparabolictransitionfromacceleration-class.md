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
ms.openlocfilehash: 0aa5831e2262602ee46bd69031e5927a86b978e1
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364093"
---
# <a name="cparabolictransitionfromacceleration-class"></a>CParabolicTransitionFromAcceleration 类

封装抛物线加速转换。

## <a name="syntax"></a>语法

```
class CParabolicTransitionFromAcceleration : public CBaseTransition;
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[从加速中转换的环数：：从加速转换的环代谢](#cparabolictransitionfromacceleration)|构造抛物面加速过渡，并用指定的参数初始化它。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[从加速转换：创建](#create)|调用过渡库以创建封装的过渡 COM 对象。 （覆盖[CBase 转换：创建](../../mfc/reference/cbasetransition-class.md#create).）|

### <a name="public-data-members"></a>公共数据成员

|名称|说明|
|----------|-----------------|
|[从加速转换：：m_dblAcceleration](#m_dblacceleration)|转换期间动画变量的加速度。|
|[从加速转换：：m_dblFinalValue](#m_dblfinalvalue)|过渡结束时动画变量的值。|
|[从加速转换：：m_dblFinalVelocity](#m_dblfinalvelocity)|转换结束时动画变量的速度。|

## <a name="remarks"></a>备注

在抛物面加速过渡期间，动画变量的值从初始值更改为以指定速度结束的最终值。 您可以通过指定加速度来控制变量到达最终值的速度。 由于所有转换都将自动清除，因此建议使用运算符 new 分配。 封装的 IUI动画转换 COM 对象由 C动画控制器：：AnimateGroup 创建，直到此为止，它才为 NULL。 创建此 COM 对象后更改成员变量不起作用。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CBase 转换](../../mfc/reference/cbasetransition-class.md)

[从加速过渡](../../mfc/reference/cparabolictransitionfromacceleration-class.md)

## <a name="requirements"></a>要求

**标头：** afxanimationcontroller.h

## <a name="cparabolictransitionfromaccelerationcparabolictransitionfromacceleration"></a><a name="cparabolictransitionfromacceleration"></a>从加速中转换的环数：：从加速转换的环代谢

构造抛物面加速过渡，并用指定的参数初始化它。

```
CParabolicTransitionFromAcceleration(
    DOUBLE dblFinalValue,
    DOUBLE dblFinalVelocity,
    DOUBLE dblAcceleration);
```

### <a name="parameters"></a>参数

*dbl 最终值*<br/>
过渡结束时动画变量的值。

*dblFinal速度*<br/>
转换结束时动画变量的速度。

*dbl加速*<br/>
转换期间动画变量的加速度。

## <a name="cparabolictransitionfromaccelerationcreate"></a><a name="create"></a>从加速转换：创建

调用过渡库以创建封装的过渡 COM 对象。

```
virtual BOOL Create(
    IUIAnimationTransitionLibrary* pLibrary,
    IUIAnimationTransitionFactory* /* not used */);
```

### <a name="parameters"></a>参数

*p库*<br/>
指向过渡库的指针，它负责创建标准转换。

### <a name="return-value"></a>返回值

如果成功创建转换，则为 TRUE;如果成功创建转换，则为 TRUE。否则 FALSE。

## <a name="cparabolictransitionfromaccelerationm_dblacceleration"></a><a name="m_dblacceleration"></a>从加速转换：：m_dblAcceleration

转换期间动画变量的加速度。

```
DOUBLE m_dblAcceleration;
```

## <a name="cparabolictransitionfromaccelerationm_dblfinalvalue"></a><a name="m_dblfinalvalue"></a>从加速转换：：m_dblFinalValue

过渡结束时动画变量的值。

```
DOUBLE m_dblFinalValue;
```

## <a name="cparabolictransitionfromaccelerationm_dblfinalvelocity"></a><a name="m_dblfinalvelocity"></a>从加速转换：：m_dblFinalVelocity

转换结束时动画变量的速度。

```
DOUBLE m_dblFinalVelocity;
```

## <a name="see-also"></a>另请参阅

[类](../../mfc/reference/mfc-classes.md)
