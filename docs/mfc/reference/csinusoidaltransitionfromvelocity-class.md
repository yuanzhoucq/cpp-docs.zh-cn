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
ms.openlocfilehash: 0df9ca6d140cb9e3ec85be3ce32760a66599c5d4
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81318244"
---
# <a name="csinusoidaltransitionfromvelocity-class"></a>CSinusoidalTransitionFromVelocity 类

封装其幅度由动画变量的初始速度决定的正弦速度转换。

## <a name="syntax"></a>语法

```
class CSinusoidalTransitionFromVelocity : public CBaseTransition;
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[从速度的CSinusoid过渡：从速度中转换的CSinusoid](#csinusoidaltransitionfromvelocity)|构造过渡对象。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[从速度转换的 CSinusoid 转换：创建](#create)|调用过渡库以创建封装的过渡 COM 对象。 （覆盖[CBase 转换：创建](../../mfc/reference/cbasetransition-class.md#create).）|

### <a name="public-data-members"></a>公共数据成员

|名称|说明|
|----------|-----------------|
|[从速度转换的CSinusoid转换：：m_duration](#m_duration)|转换的持续时间。|
|[从速度转换的CSinusoid转换：：m_period](#m_period)|正弦波的振荡周期（以秒为单位）。|

## <a name="remarks"></a>备注

动画变量的值在正弦范围转换的整个持续时间内围绕初始值振荡。 振荡的振幅由转换开始时动画变量的速度决定。 由于所有转换都将自动清除，因此建议使用运算符 new 分配。 封装的 IUI动画转换 COM 对象由 C动画控制器：：AnimateGroup 创建，直到此为止，它才为 NULL。 创建此 COM 对象后更改成员变量不起作用。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CBase 转换](../../mfc/reference/cbasetransition-class.md)

[从速度转换的 CSinusoid](../../mfc/reference/csinusoidaltransitionfromvelocity-class.md)

## <a name="requirements"></a>要求

**标头：** afxanimationcontroller.h

## <a name="csinusoidaltransitionfromvelocitycreate"></a><a name="create"></a>从速度转换的 CSinusoid 转换：创建

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

## <a name="csinusoidaltransitionfromvelocitycsinusoidaltransitionfromvelocity"></a><a name="csinusoidaltransitionfromvelocity"></a>从速度的CSinusoid过渡：从速度中转换的CSinusoid

构造过渡对象。

```
CSinusoidalTransitionFromVelocity(
    UI_ANIMATION_SECONDS duration,
    UI_ANIMATION_SECONDS period);
```

### <a name="parameters"></a>参数

*时间*<br/>
转换的持续时间。

*时期*<br/>
正弦波的振荡周期（以秒为单位）。

## <a name="csinusoidaltransitionfromvelocitym_duration"></a><a name="m_duration"></a>从速度转换的CSinusoid转换：：m_duration

转换的持续时间。

```
UI_ANIMATION_SECONDS m_duration;
```

## <a name="csinusoidaltransitionfromvelocitym_period"></a><a name="m_period"></a>从速度转换的CSinusoid转换：：m_period

正弦波的振荡周期（以秒为单位）。

```
UI_ANIMATION_SECONDS m_period;
```

## <a name="see-also"></a>另请参阅

[类](../../mfc/reference/mfc-classes.md)
