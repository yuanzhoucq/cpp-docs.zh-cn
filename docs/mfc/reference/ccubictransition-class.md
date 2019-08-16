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
ms.openlocfilehash: b6bb626f944ce87748809a5eb03a6f06f92c3de5
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69507142"
---
# <a name="ccubictransition-class"></a>CCubicTransition 类

封装立方转换。

## <a name="syntax"></a>语法

```
class CCubicTransition : public CBaseTransition;
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[CCubicTransition::CCubicTransition](#ccubictransition)|构造转换对象并初始化其参数。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CCubicTransition::Create](#create)|调用转换库以创建封装的转换 COM 对象。 (重写[CBaseTransition:: Create](../../mfc/reference/cbasetransition-class.md#create)。)|

### <a name="public-data-members"></a>公共数据成员

|名称|描述|
|----------|-----------------|
|[CCubicTransition::m_dblFinalValue](#m_dblfinalvalue)|转换结束时动画变量的值。|
|[CCubicTransition::m_dblFinalVelocity](#m_dblfinalvelocity)|变量在转换结束时的速度。|
|[CCubicTransition::m_duration](#m_duration)|转换的持续时间。|

## <a name="remarks"></a>备注

在三次转换期间, 动画变量的值在转换期间从其初始值更改为指定的最终值, 以指定速度结束。 由于所有转换都将自动清除, 因此建议使用 operator new 将其分配给它们。 封装的 IUIAnimationTransition COM 对象由 CAnimationController:: AnimateGroup 创建, 直到它为 NULL。 在创建此 COM 对象之后更改成员变量不起作用。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CBaseTransition](../../mfc/reference/cbasetransition-class.md)

`CCubicTransition`

## <a name="requirements"></a>要求

**标头：** afxanimationcontroller.h

##  <a name="ccubictransition"></a>CCubicTransition:: CCubicTransition

构造转换对象并初始化其参数。

```
CCubicTransition(
    UI_ANIMATION_SECONDS duration,
    DOUBLE finalValue,
    DOUBLE finalVelocity);
```

### <a name="parameters"></a>参数

*duration*<br/>
转换的持续时间。

*finalValue*<br/>
转换结束时动画变量的值。

*finalVelocity*<br/>
变量在转换结束时的速度。

##  <a name="create"></a>CCubicTransition:: Create

调用转换库以创建封装的转换 COM 对象。

```
virtual BOOL Create(
    IUIAnimationTransitionLibrary* pLibrary,
    IUIAnimationTransitionFactory* \*not used*\);
```

### <a name="parameters"></a>参数

*pLibrary*<br/>
指向[IUIAnimationTransitionLibrary 接口](/windows/win32/api/uianimation/nn-uianimation-iuianimationtransitionlibrary)的指针, 该接口定义标准转换库。

### <a name="return-value"></a>返回值

如果成功创建转换, 则为 TRUE;否则为 FALSE。

##  <a name="m_dblfinalvalue"></a>CCubicTransition:: m_dblFinalValue

转换结束时动画变量的值。

```
DOUBLE m_dblFinalValue;
```

##  <a name="m_dblfinalvelocity"></a>CCubicTransition:: m_dblFinalVelocity

变量在转换结束时的速度。

```
DOUBLE m_dblFinalVelocity;
```

##  <a name="m_duration"></a>CCubicTransition:: m_duration

转换的持续时间。

```
UI_ANIMATION_SECONDS m_duration;
```

## <a name="see-also"></a>请参阅

[类](../../mfc/reference/mfc-classes.md)
