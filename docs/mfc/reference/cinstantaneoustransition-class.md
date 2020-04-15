---
title: CInstantaneousTransition 类
ms.date: 11/04/2016
f1_keywords:
- CInstantaneousTransition
- AFXANIMATIONCONTROLLER/CInstantaneousTransition
- AFXANIMATIONCONTROLLER/CInstantaneousTransition::CInstantaneousTransition
- AFXANIMATIONCONTROLLER/CInstantaneousTransition::Create
- AFXANIMATIONCONTROLLER/CInstantaneousTransition::m_dblFinalValue
helpviewer_keywords:
- CInstantaneousTransition [MFC], CInstantaneousTransition
- CInstantaneousTransition [MFC], Create
- CInstantaneousTransition [MFC], m_dblFinalValue
ms.assetid: c3d5121f-2c6b-4221-9e57-10e082a31120
ms.openlocfilehash: 15c471d64309cc1358c9c5b0b33577261dd877f6
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372429"
---
# <a name="cinstantaneoustransition-class"></a>CInstantaneousTransition 类

封装瞬时转换。

## <a name="syntax"></a>语法

```
class CInstantaneousTransition : public CBaseTransition;
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[瞬时转换：C瞬时转换](#cinstantaneoustransition)|构造过渡对象并初始化其最终值。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[瞬时转换：创建](#create)|调用过渡库以创建封装的过渡 COM 对象。 （覆盖[CBase 转换：创建](../../mfc/reference/cbasetransition-class.md#create).）|

### <a name="public-data-members"></a>公共数据成员

|名称|说明|
|----------|-----------------|
|[瞬时转换：m_dblFinalValue](#m_dblfinalvalue)|过渡结束时动画变量的值。|

## <a name="remarks"></a>备注

在瞬时转换期间，动画变量的值会立即从当前值更改为指定的最终值。 此转换的持续时间始终为零。 由于所有转换都将自动清除，因此建议使用运算符 new 分配。 封装的 IUI动画转换 COM 对象由 C动画控制器：：AnimateGroup 创建，直到此为止，它才为 NULL。 创建此 COM 对象后更改成员变量不起作用。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CBase 转换](../../mfc/reference/cbasetransition-class.md)

[C瞬时转换](../../mfc/reference/cinstantaneoustransition-class.md)

## <a name="requirements"></a>要求

**标头：** afxanimationcontroller.h

## <a name="cinstantaneoustransitioncinstantaneoustransition"></a><a name="cinstantaneoustransition"></a>瞬时转换：C瞬时转换

构造过渡对象并初始化其最终值。

```
CInstantaneousTransition(DOUBLE dblFinalValue);
```

### <a name="parameters"></a>参数

*dbl 最终值*<br/>
过渡结束时动画变量的值。

## <a name="cinstantaneoustransitioncreate"></a><a name="create"></a>瞬时转换：创建

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

## <a name="cinstantaneoustransitionm_dblfinalvalue"></a><a name="m_dblfinalvalue"></a>瞬时转换：m_dblFinalValue

过渡结束时动画变量的值。

```
DOUBLE m_dblFinalValue;
```

## <a name="see-also"></a>另请参阅

[类](../../mfc/reference/mfc-classes.md)
