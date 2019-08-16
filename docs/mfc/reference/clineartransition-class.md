---
title: CLinearTransition 类
ms.date: 11/04/2016
f1_keywords:
- CLinearTransition
- AFXANIMATIONCONTROLLER/CLinearTransition
- AFXANIMATIONCONTROLLER/CLinearTransition::CLinearTransition
- AFXANIMATIONCONTROLLER/CLinearTransition::Create
- AFXANIMATIONCONTROLLER/CLinearTransition::m_dblFinalValue
- AFXANIMATIONCONTROLLER/CLinearTransition::m_duration
helpviewer_keywords:
- CLinearTransition [MFC], CLinearTransition
- CLinearTransition [MFC], Create
- CLinearTransition [MFC], m_dblFinalValue
- CLinearTransition [MFC], m_duration
ms.assetid: 7fcb2dba-beb8-4933-9f5d-3b7fb1585ef0
ms.openlocfilehash: 1a6348d1afd0117683bd31af61324b14e16f710c
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69505747"
---
# <a name="clineartransition-class"></a>CLinearTransition 类

封装线性转换。

## <a name="syntax"></a>语法

```
class CLinearTransition : public CBaseTransition;
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[CLinearTransition:: CLinearTransition](#clineartransition)|构造线性转换对象, 并使用 duration 和 final 值对其进行初始化。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CLinearTransition::Create](#create)|调用转换库以创建封装的转换 COM 对象。 (重写[CBaseTransition:: Create](../../mfc/reference/cbasetransition-class.md#create)。)|

### <a name="public-data-members"></a>公共数据成员

|名称|描述|
|----------|-----------------|
|[CLinearTransition::m_dblFinalValue](#m_dblfinalvalue)|转换结束时动画变量的值。|
|[CLinearTransition::m_duration](#m_duration)|转换的持续时间。|

## <a name="remarks"></a>备注

在线性转换期间, 动画变量的值将从其初始值转换为指定的最终值。 由于所有转换都将自动清除, 因此建议使用 operator new 将其分配给它们。 封装的 IUIAnimationTransition COM 对象由 CAnimationController:: AnimateGroup 创建, 直到它为 NULL。 在创建此 COM 对象之后更改成员变量不起作用。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CBaseTransition](../../mfc/reference/cbasetransition-class.md)

[CLinearTransition](../../mfc/reference/clineartransition-class.md)

## <a name="requirements"></a>要求

**标头：** afxanimationcontroller.h

##  <a name="clineartransition"></a>CLinearTransition:: CLinearTransition

构造线性转换对象, 并使用 duration 和 final 值对其进行初始化。

```
CLinearTransition(
    UI_ANIMATION_SECONDS duration,
    DOUBLE dblFinalValue);
```

### <a name="parameters"></a>参数

*duration*<br/>
转换的持续时间。

*dblFinalValue*<br/>
转换结束时动画变量的值。

##  <a name="create"></a>CLinearTransition:: Create

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

##  <a name="m_dblfinalvalue"></a>CLinearTransition:: m_dblFinalValue

转换结束时动画变量的值。

```
DOUBLE m_dblFinalValue;
```

##  <a name="m_duration"></a>CLinearTransition:: m_duration

转换的持续时间。

```
UI_ANIMATION_SECONDS m_duration;
```

## <a name="see-also"></a>请参阅

[类](../../mfc/reference/mfc-classes.md)
