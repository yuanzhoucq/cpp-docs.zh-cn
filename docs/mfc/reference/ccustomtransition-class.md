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
ms.openlocfilehash: af600704f82a0cad402948286fa0d4b11dca0c71
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50578368"
---
# <a name="ccustomtransition-class"></a>CCustomTransition 类

实现自定义转换。

## <a name="syntax"></a>语法

```
class CCustomTransition : public CBaseTransition;
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[CCustomTransition::CCustomTransition](#ccustomtransition)|构造一个自定义转换对象。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CCustomTransition::Create](#create)|调用要创建封装的转换 COM 对象的转换库。 (重写[CBaseTransition::Create](../../mfc/reference/cbasetransition-class.md#create)。)|
|[CCustomTransition::SetInitialValue](#setinitialvalue)|设置将应用于与此转换关联的动画变量的初始值。|
|[CCustomTransition::SetInitialVelocity](#setinitialvelocity)|设置初始速度，将应用于与此转换关联的动画变量。|

### <a name="protected-data-members"></a>受保护的数据成员

|name|描述|
|----------|-----------------|
|[CCustomTransition::m_bInitialValueSpecified](#m_binitialvaluespecified)|指定是否使用 SetInitialValue 指定的初始值。|
|[CCustomTransition::m_bInitialVelocitySpecified](#m_binitialvelocityspecified)|指定是否使用 setinitialvelocity 方法指定的初始速度。|
|[CCustomTransition::m_initialValue](#m_initialvalue)|将存储的初始值。|
|[CCustomTransition::m_initialVelocity](#m_initialvelocity)|将存储的初始速度。|
|[CCustomTransition::m_pInterpolator](#m_pinterpolator)|存储指向自定义内插器的指针。|

## <a name="remarks"></a>备注

CCustomTransitions 类允许开发人员实现自定义转换。 它已创建并用作一个标准转换，但其构造函数将作为参数接受指向自定义内插器的指针。 执行以下步骤以使用自定义的转换： 1。 从 CCustomInterpolator 派生一个类并实现至少 InterpolateValue 方法。 2. 请确保不能少于动画的持续时间使用该自定义内插器对象的生存期。 3. 实例化 （使用 new 运算符） CCustomTransition 对象并将指针传递到构造函数中的自定义内插器。 4. 如果这些参数所需的自定义内插，调用 CCustomTransition::SetInitialValue 和 CCustomTransition::SetInitialVelocity。 5. 将指针传递给自定义转换到下方法的动画对象，其值应使用自定义算法进行动画处理。 6. 当动画对象的值应更改 Windows 动画 API 将在 CCustomInterpolator 调用 InterpolateValue （和其他相关的方法）。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CBaseTransition](../../mfc/reference/cbasetransition-class.md)

`CCustomTransition`

## <a name="requirements"></a>要求

**标头：** afxanimationcontroller.h

##  <a name="ccustomtransition"></a>  CCustomTransition::CCustomTransition

构造一个自定义转换对象。

```
CCustomTransition(CCustomInterpolator* pInterpolator);
```

### <a name="parameters"></a>参数

*pInterpolator*<br/>
自定义内插器指向的指针。

##  <a name="create"></a>  CCustomTransition::Create

调用要创建封装的转换 COM 对象的转换库。

```
virtual BOOL Create(
    IUIAnimationTransitionLibrary* */,
    IUIAnimationTransitionFactory* pFactory);
```

### <a name="parameters"></a>参数

*pFactory*<br/>
指向转换工厂负责创建的自定义转换的指针。

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

此方法还可以设置初始值和初始速度要应用于与此转换相关联的动画变量。 为此必须调用 SetInitialValue 和 setinitialvelocity 方法之前，框架创建封装的转换 COM 对象 （它发生在调用 CAnimationController::AnimateGroup 时）。

##  <a name="m_binitialvaluespecified"></a>  CCustomTransition::m_bInitialValueSpecified

指定是否使用 SetInitialValue 指定的初始值。

```
BOOL m_bInitialValueSpecified;
```

##  <a name="m_binitialvelocityspecified"></a>  CCustomTransition::m_bInitialVelocitySpecified

指定是否使用 setinitialvelocity 方法指定的初始速度。

```
BOOL m_bInitialVelocitySpecified;
```

##  <a name="m_initialvalue"></a>  CCustomTransition::m_initialValue

将存储的初始值。

```
DOUBLE m_initialValue;
```

##  <a name="m_initialvelocity"></a>  CCustomTransition::m_initialVelocity

将存储的初始速度。

```
DOUBLE m_initialVelocity;
```

##  <a name="m_pinterpolator"></a>  CCustomTransition::m_pInterpolator

存储指向自定义内插器的指针。

```
CCustomInterpolator* m_pInterpolator;
```

##  <a name="setinitialvalue"></a>  CCustomTransition::SetInitialValue

设置将应用于与此转换关联的动画变量的初始值。

```
void SetInitialValue(DOUBLE initialValue);
```

### <a name="parameters"></a>参数

*initialValue*

##  <a name="setinitialvelocity"></a>  CCustomTransition::SetInitialVelocity

设置初始速度，将应用于与此转换关联的动画变量。

```
void SetInitialVelocity(DOUBLE initialVelocity);
```

### <a name="parameters"></a>参数

*initialVelocity*

## <a name="see-also"></a>请参阅

[类](../../mfc/reference/mfc-classes.md)
