---
title: CCustomTransition 类
ms.date: 11/04/2016
f1_keywords:
- CCustomTransition
- AFXANIMATIONCONTROLLER/CCustomTransition
- AFXANIMATIONCONTROLLER/CCustomTransition::CCustomTransition
- AFXANIMATIONCONTROLLER/CCustomTransition::Create
- AFXANIMATIONCONTROLLER/CCustomTransition::SetInitialValue
- AFXANIMATIONCONTROLLER/CCustomTransition::SetInitialVelocity
- AFXANIMATIONCONTROLLER/CCustomTransition::m_bInitialValueSpecified
- AFXANIMATIONCONTROLLER/CCustomTransition::m_bInitialVelocitySpecified
- AFXANIMATIONCONTROLLER/CCustomTransition::m_initialValue
- AFXANIMATIONCONTROLLER/CCustomTransition::m_initialVelocity
- AFXANIMATIONCONTROLLER/CCustomTransition::m_pInterpolator
helpviewer_keywords:
- CCustomTransition [MFC], CCustomTransition
- CCustomTransition [MFC], Create
- CCustomTransition [MFC], SetInitialValue
- CCustomTransition [MFC], SetInitialVelocity
- CCustomTransition [MFC], m_bInitialValueSpecified
- CCustomTransition [MFC], m_bInitialVelocitySpecified
- CCustomTransition [MFC], m_initialValue
- CCustomTransition [MFC], m_initialVelocity
- CCustomTransition [MFC], m_pInterpolator
ms.assetid: 5bd3f492-940f-4290-a38b-fa68eb8f8401
ms.openlocfilehash: 8bdd0ebab0a6e4138e24edff38da9b444745f83a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369331"
---
# <a name="ccustomtransition-class"></a>CCustomTransition 类

实现自定义转换。

## <a name="syntax"></a>语法

```
class CCustomTransition : public CBaseTransition;
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[C自定义转换：C自定义转换](#ccustomtransition)|构造自定义转换对象。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[C自定义转换：：创建](#create)|调用过渡库以创建封装的过渡 COM 对象。 （覆盖[CBase 转换：创建](../../mfc/reference/cbasetransition-class.md#create).）|
|[C自定义转换：：设置初始值](#setinitialvalue)|设置初始值，该值将应用于与此转换关联的动画变量。|
|[C自定义转换：：设置初始速度](#setinitialvelocity)|设置初始速度，它将应用于与此转换关联的动画变量。|

### <a name="protected-data-members"></a>受保护的数据成员

|名称|说明|
|----------|-----------------|
|[C自定义转换：m_bInitialValueSpecified](#m_binitialvaluespecified)|指定初始值是否使用 Set 初始值指定。|
|[C自定义转换：：m_bInitialVelocitySpecified](#m_binitialvelocityspecified)|指定初始速度是否使用 Set 初始速度指定。|
|[C自定义转换：：m_initialValue](#m_initialvalue)|存储初始值。|
|[C自定义转换：：m_initialVelocity](#m_initialvelocity)|存储初始速度。|
|[CCustom 转换：：m_pInterpolator](#m_pinterpolator)|存储指向自定义插值器的指针。|

## <a name="remarks"></a>备注

CCustomTransitions 类允许开发人员实现自定义转换。 它创建并用作标准转换，但其构造函数接受作为参数指向自定义插值器的指针。 执行以下步骤以使用自定义转换：1。 从 CCustomInterpolator 派生类，并实现至少插值值方法。 2. 确保自定义插值器对象的生存期必须长于使用该对象的动画持续时间。 3. 实例化（使用运算符 new）CCustomTransition 对象，并将指针传递到构造函数中的自定义插值器。 4. 调用 CCustom 转换：：设置初始值和 CCustom 转换：：如果自定义插值需要这些参数，则设置初始速度。 5. 将指向自定义转换的指针传递给动画对象的 AddTransition 方法，其值应使用自定义算法进行动画处理。 6. 当动画对象的值应更改 Windows 动画 API 时，将在 CCustomInterpolator 中调用插值值（和其他相关方法）。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CBase 转换](../../mfc/reference/cbasetransition-class.md)

`CCustomTransition`

## <a name="requirements"></a>要求

**标头：** afxanimationcontroller.h

## <a name="ccustomtransitionccustomtransition"></a><a name="ccustomtransition"></a>C自定义转换：C自定义转换

构造自定义转换对象。

```
CCustomTransition(CCustomInterpolator* pInterpolator);
```

### <a name="parameters"></a>参数

*p插值器*<br/>
指向自定义插值器的指针。

## <a name="ccustomtransitioncreate"></a><a name="create"></a>C自定义转换：：创建

调用过渡库以创建封装的过渡 COM 对象。

```
virtual BOOL Create(
    IUIAnimationTransitionLibrary* */,
    IUIAnimationTransitionFactory* pFactory);
```

### <a name="parameters"></a>参数

*pFactory*<br/>
指向转换工厂的指针，它负责创建自定义转换。

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

此方法还可以设置初始值和初始速度以应用于动画变量，该变量与此转换相关联。 为此，您必须在框架创建封装的过渡 COM 对象之前调用 Set初始值和 Set初始速度（当您调用 CAnimateController：：AnimateGroup）时，将调用 SetValueValue 和 Set初始速度。

## <a name="ccustomtransitionm_binitialvaluespecified"></a><a name="m_binitialvaluespecified"></a>C自定义转换：m_bInitialValueSpecified

指定初始值是否使用 Set 初始值指定。

```
BOOL m_bInitialValueSpecified;
```

## <a name="ccustomtransitionm_binitialvelocityspecified"></a><a name="m_binitialvelocityspecified"></a>C自定义转换：：m_bInitialVelocitySpecified

指定初始速度是否使用 Set 初始速度指定。

```
BOOL m_bInitialVelocitySpecified;
```

## <a name="ccustomtransitionm_initialvalue"></a><a name="m_initialvalue"></a>C自定义转换：：m_initialValue

存储初始值。

```
DOUBLE m_initialValue;
```

## <a name="ccustomtransitionm_initialvelocity"></a><a name="m_initialvelocity"></a>C自定义转换：：m_initialVelocity

存储初始速度。

```
DOUBLE m_initialVelocity;
```

## <a name="ccustomtransitionm_pinterpolator"></a><a name="m_pinterpolator"></a>CCustom 转换：：m_pInterpolator

存储指向自定义插值器的指针。

```
CCustomInterpolator* m_pInterpolator;
```

## <a name="ccustomtransitionsetinitialvalue"></a><a name="setinitialvalue"></a>C自定义转换：：设置初始值

设置初始值，该值将应用于与此转换关联的动画变量。

```
void SetInitialValue(DOUBLE initialValue);
```

### <a name="parameters"></a>参数

*初始值*

## <a name="ccustomtransitionsetinitialvelocity"></a><a name="setinitialvelocity"></a>C自定义转换：：设置初始速度

设置初始速度，它将应用于与此转换关联的动画变量。

```
void SetInitialVelocity(DOUBLE initialVelocity);
```

### <a name="parameters"></a>参数

*初始速度*

## <a name="see-also"></a>另请参阅

[类](../../mfc/reference/mfc-classes.md)
