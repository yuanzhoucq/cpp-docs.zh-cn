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
ms.openlocfilehash: 1d3bc50255dae93bfa80e8212c2349db66db4eb6
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372280"
---
# <a name="clineartransition-class"></a>CLinearTransition 类

封装线性转换。

## <a name="syntax"></a>语法

```
class CLinearTransition : public CBaseTransition;
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[C线性转换：C线性转换](#clineartransition)|构造线性过渡对象，并初始化其持续时间和最终值。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[C线性转换：创建](#create)|调用过渡库以创建封装的过渡 COM 对象。 （覆盖[CBase 转换：创建](../../mfc/reference/cbasetransition-class.md#create).）|

### <a name="public-data-members"></a>公共数据成员

|名称|说明|
|----------|-----------------|
|[C线性转换：m_dblFinalValue](#m_dblfinalvalue)|过渡结束时动画变量的值。|
|[C线性转换：m_duration](#m_duration)|转换的持续时间。|

## <a name="remarks"></a>备注

在线性转换期间，动画变量的值从初始值线性转换为指定的最终值。 由于所有转换都将自动清除，因此建议使用运算符 new 分配。 封装的 IUI动画转换 COM 对象由 C动画控制器：：AnimateGroup 创建，直到此为止，它才为 NULL。 创建此 COM 对象后更改成员变量不起作用。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CBase 转换](../../mfc/reference/cbasetransition-class.md)

[C线性转换](../../mfc/reference/clineartransition-class.md)

## <a name="requirements"></a>要求

**标头：** afxanimationcontroller.h

## <a name="clineartransitionclineartransition"></a><a name="clineartransition"></a>C线性转换：C线性转换

构造线性过渡对象，并初始化其持续时间和最终值。

```
CLinearTransition(
    UI_ANIMATION_SECONDS duration,
    DOUBLE dblFinalValue);
```

### <a name="parameters"></a>参数

*时间*<br/>
转换的持续时间。

*dbl 最终值*<br/>
过渡结束时动画变量的值。

## <a name="clineartransitioncreate"></a><a name="create"></a>C线性转换：创建

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

## <a name="clineartransitionm_dblfinalvalue"></a><a name="m_dblfinalvalue"></a>C线性转换：m_dblFinalValue

过渡结束时动画变量的值。

```
DOUBLE m_dblFinalValue;
```

## <a name="clineartransitionm_duration"></a><a name="m_duration"></a>C线性转换：m_duration

转换的持续时间。

```
UI_ANIMATION_SECONDS m_duration;
```

## <a name="see-also"></a>另请参阅

[类](../../mfc/reference/mfc-classes.md)
