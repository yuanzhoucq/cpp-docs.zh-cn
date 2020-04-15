---
title: CCubicTransition 类
ms.date: 11/04/2016
f1_keywords:
- CCubicTransition
- AFXANIMATIONCONTROLLER/CCubicTransition
- AFXANIMATIONCONTROLLER/CCubicTransition::CCubicTransition
- AFXANIMATIONCONTROLLER/CCubicTransition::Create
- AFXANIMATIONCONTROLLER/CCubicTransition::m_dblFinalValue
- AFXANIMATIONCONTROLLER/CCubicTransition::m_dblFinalVelocity
- AFXANIMATIONCONTROLLER/CCubicTransition::m_duration
helpviewer_keywords:
- CCubicTransition [MFC], CCubicTransition
- CCubicTransition [MFC], Create
- CCubicTransition [MFC], m_dblFinalValue
- CCubicTransition [MFC], m_dblFinalVelocity
- CCubicTransition [MFC], m_duration
ms.assetid: 4fc30e9c-160c-45e1-bdbe-51adf8fee9c5
ms.openlocfilehash: de376503111dab157ca34744863fb1d35a58785e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369336"
---
# <a name="ccubictransition-class"></a>CCubicTransition 类

封装立方转换。

## <a name="syntax"></a>语法

```
class CCubicTransition : public CBaseTransition;
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[立方转换：C立方转换](#ccubictransition)|构造过渡对象并初始化其参数。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CCubic 转换：创建](#create)|调用过渡库以创建封装的过渡 COM 对象。 （覆盖[CBase 转换：创建](../../mfc/reference/cbasetransition-class.md#create).）|

### <a name="public-data-members"></a>公共数据成员

|名称|说明|
|----------|-----------------|
|[CCubic 转换：m_dblFinalValue](#m_dblfinalvalue)|过渡结束时动画变量的值。|
|[CCubic 转换：m_dblFinalVelocity](#m_dblfinalvelocity)|转换结束时变量的速度。|
|[CCubic 转换：m_duration](#m_duration)|转换的持续时间。|

## <a name="remarks"></a>备注

在立方过渡期间，动画变量的值在过渡期间从初始值更改为指定的最终值，以指定速度结束。 由于所有转换都将自动清除，因此建议使用运算符 new 分配。 封装的 IUI动画转换 COM 对象由 C动画控制器：：AnimateGroup 创建，直到此为止，它才为 NULL。 创建此 COM 对象后更改成员变量不起作用。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CBase 转换](../../mfc/reference/cbasetransition-class.md)

`CCubicTransition`

## <a name="requirements"></a>要求

**标头：** afxanimationcontroller.h

## <a name="ccubictransitionccubictransition"></a><a name="ccubictransition"></a>立方转换：C立方转换

构造过渡对象并初始化其参数。

```
CCubicTransition(
    UI_ANIMATION_SECONDS duration,
    DOUBLE finalValue,
    DOUBLE finalVelocity);
```

### <a name="parameters"></a>参数

*时间*<br/>
转换的持续时间。

*最终价值*<br/>
过渡结束时动画变量的值。

*最终速度*<br/>
转换结束时变量的速度。

## <a name="ccubictransitioncreate"></a><a name="create"></a>CCubic 转换：创建

调用过渡库以创建封装的过渡 COM 对象。

```
virtual BOOL Create(
    IUIAnimationTransitionLibrary* pLibrary,
    IUIAnimationTransitionFactory* \*not used*\);
```

### <a name="parameters"></a>参数

*p库*<br/>
指向[IUIAnimation 转换库接口](/windows/win32/api/uianimation/nn-uianimation-iuianimationtransitionlibrary)的指针，该接口定义标准转换库。

### <a name="return-value"></a>返回值

如果成功创建转换，则为 TRUE;如果成功创建转换，则为 TRUE。否则 FALSE。

## <a name="ccubictransitionm_dblfinalvalue"></a><a name="m_dblfinalvalue"></a>CCubic 转换：m_dblFinalValue

过渡结束时动画变量的值。

```
DOUBLE m_dblFinalValue;
```

## <a name="ccubictransitionm_dblfinalvelocity"></a><a name="m_dblfinalvelocity"></a>CCubic 转换：m_dblFinalVelocity

转换结束时变量的速度。

```
DOUBLE m_dblFinalVelocity;
```

## <a name="ccubictransitionm_duration"></a><a name="m_duration"></a>CCubic 转换：m_duration

转换的持续时间。

```
UI_ANIMATION_SECONDS m_duration;
```

## <a name="see-also"></a>另请参阅

[类](../../mfc/reference/mfc-classes.md)
