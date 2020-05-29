---
title: CDiscreteTransition 类
ms.date: 11/04/2016
f1_keywords:
- CDiscreteTransition
- AFXANIMATIONCONTROLLER/CDiscreteTransition
- AFXANIMATIONCONTROLLER/CDiscreteTransition::CDiscreteTransition
- AFXANIMATIONCONTROLLER/CDiscreteTransition::Create
- AFXANIMATIONCONTROLLER/CDiscreteTransition::m_dblFinalValue
- AFXANIMATIONCONTROLLER/CDiscreteTransition::m_delay
- AFXANIMATIONCONTROLLER/CDiscreteTransition::m_hold
helpviewer_keywords:
- CDiscreteTransition [MFC], CDiscreteTransition
- CDiscreteTransition [MFC], Create
- CDiscreteTransition [MFC], m_dblFinalValue
- CDiscreteTransition [MFC], m_delay
- CDiscreteTransition [MFC], m_hold
ms.assetid: b4d84fb3-ccaa-451c-a69b-6b50dcb9b9c8
ms.openlocfilehash: 2a32ee7921e927e25a5196d38c8f5ae350ab2b8d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375655"
---
# <a name="cdiscretetransition-class"></a>CDiscreteTransition 类

封装离散转换。

## <a name="syntax"></a>语法

```
class CDiscreteTransition : public CBaseTransition;
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[离散转换：C离散转换](#cdiscretetransition)|构造离散过渡对象并初始化其参数。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[离散转换：创建](#create)|调用过渡库以创建封装的过渡 COM 对象。 （覆盖[CBase 转换：创建](../../mfc/reference/cbasetransition-class.md#create).）|

### <a name="public-data-members"></a>公共数据成员

|名称|说明|
|----------|-----------------|
|[离散转换：：m_dblFinalValue](#m_dblfinalvalue)|过渡结束时动画变量的值。|
|[离散转换：：m_delay](#m_delay)|将瞬时开关延迟到最终值的时间量。|
|[离散转换：：m_hold](#m_hold)|将变量保留在其最终值的时间量。|

## <a name="remarks"></a>备注

在离散转换期间，动画变量在指定延迟时间保持初始值，然后即时切换到指定的最终值，并在给定的保持时间内保持该值。 由于所有转换都将自动清除，因此建议使用运算符 new 分配。 封装的 IUI动画转换 COM 对象由 C动画控制器：：AnimateGroup 创建，直到此为止，它才为 NULL。 创建此 COM 对象后更改成员变量不起作用。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CBase 转换](../../mfc/reference/cbasetransition-class.md)

[C离散转换](../../mfc/reference/cdiscretetransition-class.md)

## <a name="requirements"></a>要求

**标头：** afxanimationcontroller.h

## <a name="cdiscretetransitioncdiscretetransition"></a><a name="cdiscretetransition"></a>离散转换：C离散转换

构造离散过渡对象并初始化其参数。

```
CDiscreteTransition(
    UI_ANIMATION_SECONDS delay,
    DOUBLE dblFinalValue,
    UI_ANIMATION_SECONDS hold);
```

### <a name="parameters"></a>参数

*延迟*<br/>
将瞬时开关延迟到最终值的时间量。

*dbl 最终值*<br/>
过渡结束时动画变量的值。

*保持*<br/>
将变量保留在其最终值的时间量。

## <a name="cdiscretetransitioncreate"></a><a name="create"></a>离散转换：创建

调用过渡库以创建封装的过渡 COM 对象。

```
virtual BOOL Create(
    IUIAnimationTransitionLibrary* pLibrary,
    IUIAnimationTransitionFactory* \*not used*\);
```

*p库*<br/>
指向[IUIAnimation 转换库接口](/windows/win32/api/uianimation/nn-uianimation-iuianimationtransitionlibrary)的指针，该接口定义标准转换库。

### <a name="return-value"></a>返回值

如果成功创建转换，则为 TRUE;如果成功创建转换，则为 TRUE。否则 FALSE。

## <a name="cdiscretetransitionm_dblfinalvalue"></a><a name="m_dblfinalvalue"></a>离散转换：：m_dblFinalValue

过渡结束时动画变量的值。

```
DOUBLE m_dblFinalValue;
```

## <a name="cdiscretetransitionm_delay"></a><a name="m_delay"></a>离散转换：：m_delay

将瞬时开关延迟到最终值的时间量。

```
UI_ANIMATION_SECONDS m_delay;
```

## <a name="cdiscretetransitionm_hold"></a><a name="m_hold"></a>离散转换：：m_hold

将变量保留在其最终值的时间量。

```
UI_ANIMATION_SECONDS m_hold;
```

## <a name="see-also"></a>另请参阅

[类](../../mfc/reference/mfc-classes.md)
