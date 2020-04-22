---
title: CCustomInterpolator 类
ms.date: 11/04/2016
f1_keywords:
- CCustomInterpolator
- AFXANIMATIONCONTROLLER/CCustomInterpolator
- AFXANIMATIONCONTROLLER/CCustomInterpolator::CCustomInterpolator
- AFXANIMATIONCONTROLLER/CCustomInterpolator::GetDependencies
- AFXANIMATIONCONTROLLER/CCustomInterpolator::GetDuration
- AFXANIMATIONCONTROLLER/CCustomInterpolator::GetFinalValue
- AFXANIMATIONCONTROLLER/CCustomInterpolator::Init
- AFXANIMATIONCONTROLLER/CCustomInterpolator::InterpolateValue
- AFXANIMATIONCONTROLLER/CCustomInterpolator::InterpolateVelocity
- AFXANIMATIONCONTROLLER/CCustomInterpolator::SetDuration
- AFXANIMATIONCONTROLLER/CCustomInterpolator::SetInitialValueAndVelocity
- AFXANIMATIONCONTROLLER/CCustomInterpolator::m_currentValue
- AFXANIMATIONCONTROLLER/CCustomInterpolator::m_currentVelocity
- AFXANIMATIONCONTROLLER/CCustomInterpolator::m_duration
- AFXANIMATIONCONTROLLER/CCustomInterpolator::m_finalValue
- AFXANIMATIONCONTROLLER/CCustomInterpolator::m_initialValue
- AFXANIMATIONCONTROLLER/CCustomInterpolator::m_initialVelocity
helpviewer_keywords:
- CCustomInterpolator [MFC], CCustomInterpolator
- CCustomInterpolator [MFC], GetDependencies
- CCustomInterpolator [MFC], GetDuration
- CCustomInterpolator [MFC], GetFinalValue
- CCustomInterpolator [MFC], Init
- CCustomInterpolator [MFC], InterpolateValue
- CCustomInterpolator [MFC], InterpolateVelocity
- CCustomInterpolator [MFC], SetDuration
- CCustomInterpolator [MFC], SetInitialValueAndVelocity
- CCustomInterpolator [MFC], m_currentValue
- CCustomInterpolator [MFC], m_currentVelocity
- CCustomInterpolator [MFC], m_duration
- CCustomInterpolator [MFC], m_finalValue
- CCustomInterpolator [MFC], m_initialValue
- CCustomInterpolator [MFC], m_initialVelocity
ms.assetid: 28d85595-989a-40a3-b003-e0e38437a94d
ms.openlocfilehash: 00ce0661fa3fbde714a7299ecbbd54df7c9bcc36
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/22/2020
ms.locfileid: "81749172"
---
# <a name="ccustominterpolator-class"></a>CCustomInterpolator 类

实现基本插值程序。

## <a name="syntax"></a>语法

```
class CCustomInterpolator;
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[海关组织：：海关插值器](#ccustominterpolator)|已重载。 构造自定义插值器对象，并将持续时间和速度初始化到指定值。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CCustom 插值器：：获取依赖性](#getdependencies)|获取插值器的依赖项。|
|[CCustom 插值器：获取持续时间](#getduration)|获取插值器的持续时间。|
|[CCustom 插值器：：获取最终值](#getfinalvalue)|获取插值器引由的最终值。|
|[CCustom插值器：：Init](#init)|初始化持续时间和最终值。|
|[海关组织：：刑警价值](#interpolatevalue)|插值在给定偏移处的值。|
|[海关刑警：：刑警组织](#interpolatevelocity)|在给定偏移处插入速度|
|[C自定义设置器：：设置持续时间](#setduration)|设置插值器的持续时间。|
|[C自定义插值器：：设置初始值和速度](#setinitialvalueandvelocity)|设置插值器的初始值和速度。|

### <a name="protected-data-members"></a>受保护的数据成员

|名称|说明|
|----------|-----------------|
|[海关组织：：m_currentValue](#m_currentvalue)|插值值。|
|[C自定义插值器：：m_currentVelocity](#m_currentvelocity)|插值速度。|
|[C自定义插值器：：m_duration](#m_duration)|转换的持续时间。|
|[C自定义插值器：：m_finalValue](#m_finalvalue)|转换结束时变量的最终值。|
|[C自定义插值器：：m_initialValue](#m_initialvalue)|转换开始时变量的值。|
|[海关：m_initialVelocity](#m_initialvelocity)|转换开始时变量的速度。|

## <a name="remarks"></a>备注

从 CCustomInterpolator 派生一个类并重写所有必要的方法，以实现自定义插值算法。 指向此类的指针应作为参数传递给 CCustomTransition。

## <a name="inheritance-hierarchy"></a>继承层次结构

`CCustomInterpolator`

## <a name="requirements"></a>要求

**标头：** afxanimationcontroller.h

## <a name="ccustominterpolatorccustominterpolator"></a><a name="ccustominterpolator"></a>海关组织：：海关插值器

构造自定义插值器对象，并将所有值设置为默认 0。

```
CCustomInterpolator();

CCustomInterpolator(
    UI_ANIMATION_SECONDS duration,
    DOUBLE finalValue);
```

### <a name="parameters"></a>参数

*duration*<br/>
转换的持续时间。

*最终价值*

### <a name="remarks"></a>备注

使用 CCustomInterpolator：：Init 在代码的后面部分初始化持续时间和最终值。

## <a name="ccustominterpolatorgetdependencies"></a><a name="getdependencies"></a>CCustom 插值器：：获取依赖性

获取插值器的依赖项。

```
virtual BOOL GetDependencies(
    UI_ANIMATION_DEPENDENCIES* initialValueDependencies,
    UI_ANIMATION_DEPENDENCIES* initialVelocityDependencies,
    UI_ANIMATION_DEPENDENCIES* durationDependencies);
```

### <a name="parameters"></a>参数

*初始价值依赖性*<br/>
输出。 插值器的一些方面，这些插值取决于传递给 Set初始值和Velocity 的初始值。

*初始速度依赖性*<br/>
输出。 插值器的方面，这些插值器取决于传递给 Set 初始值和Velocity的初始速度。

*持续时间 依赖*<br/>
输出。 插值器的一些方面，这些插值器取决于传递给 SetDuration 的持续时间。

### <a name="return-value"></a>返回值

基本实现始终返回 TRUE。 如果要使事件失败，则从重写的实现返回 FALSE。

## <a name="ccustominterpolatorgetduration"></a><a name="getduration"></a>CCustom 插值器：获取持续时间

获取插值器的持续时间。

```
virtual BOOL GetDuration(UI_ANIMATION_SECONDS* duration);
```

### <a name="parameters"></a>参数

*duration*<br/>
输出。 转换的持续时间，以秒为单位。

### <a name="return-value"></a>返回值

基本实现始终返回 TRUE。 如果要使事件失败，则从重写的实现返回 FALSE。

## <a name="ccustominterpolatorgetfinalvalue"></a><a name="getfinalvalue"></a>CCustom 插值器：：获取最终值

获取插值器引由的最终值。

```
virtual BOOL GetFinalValue(DOUBLE* value);
```

### <a name="parameters"></a>参数

*value*<br/>
输出。 转换结束时变量的最终值。

### <a name="return-value"></a>返回值

基本实现始终返回 TRUE。 如果要使事件失败，则从重写的实现返回 FALSE。

## <a name="ccustominterpolatorinit"></a><a name="init"></a>CCustom插值器：：Init

初始化持续时间和最终值。

```cpp
void Init(
    UI_ANIMATION_SECONDS duration,
    DOUBLE finalValue);
```

### <a name="parameters"></a>参数

*duration*<br/>
转换的持续时间。

*最终价值*<br/>
转换结束时变量的最终值。

## <a name="ccustominterpolatorinterpolatevalue"></a><a name="interpolatevalue"></a>海关组织：：刑警价值

插值在给定偏移处的值。

```
virtual BOOL InterpolateValue(
    UI_ANIMATION_SECONDS */,
    DOUBLE* value);
```

### <a name="parameters"></a>参数

*value*<br/>
输出。 插值值。

### <a name="return-value"></a>返回值

基本实现始终返回 TRUE。 如果要使事件失败，则从重写的实现返回 FALSE。

## <a name="ccustominterpolatorinterpolatevelocity"></a><a name="interpolatevelocity"></a>海关刑警：：刑警组织

在给定偏移处插入速度

```
virtual BOOL InterpolateVelocity(
    UI_ANIMATION_SECONDS */,
    DOUBLE* velocity);
```

### <a name="parameters"></a>参数

*velocity*<br/>
输出。 偏移处变量的速度。

### <a name="return-value"></a>返回值

基本实现始终返回 TRUE。 如果要使事件失败，则从重写的实现返回 FALSE。

## <a name="ccustominterpolatorm_currentvalue"></a><a name="m_currentvalue"></a>海关组织：：m_currentValue

插值值。

```
DOUBLE m_currentValue;
```

## <a name="ccustominterpolatorm_currentvelocity"></a><a name="m_currentvelocity"></a>C自定义插值器：：m_currentVelocity

插值速度。

```
DOUBLE m_currentVelocity;
```

## <a name="ccustominterpolatorm_duration"></a><a name="m_duration"></a>C自定义插值器：：m_duration

转换的持续时间。

```
UI_ANIMATION_SECONDS m_duration;
```

## <a name="ccustominterpolatorm_finalvalue"></a><a name="m_finalvalue"></a>C自定义插值器：：m_finalValue

转换结束时变量的最终值。

```
DOUBLE m_finalValue;
```

## <a name="ccustominterpolatorm_initialvalue"></a><a name="m_initialvalue"></a>C自定义插值器：：m_initialValue

转换开始时变量的值。

```
DOUBLE m_initialValue;
```

## <a name="ccustominterpolatorm_initialvelocity"></a><a name="m_initialvelocity"></a>海关：m_initialVelocity

转换开始时变量的速度。

```
DOUBLE m_initialVelocity;
```

## <a name="ccustominterpolatorsetduration"></a><a name="setduration"></a>C自定义设置器：：设置持续时间

设置插值器的持续时间。

```
virtual BOOL SetDuration(UI_ANIMATION_SECONDS duration);
```

### <a name="parameters"></a>参数

*duration*<br/>
转换的持续时间。

### <a name="return-value"></a>返回值

基本实现始终返回 TRUE。 如果要使事件失败，则从重写的实现返回 FALSE。

## <a name="ccustominterpolatorsetinitialvalueandvelocity"></a><a name="setinitialvalueandvelocity"></a>C自定义插值器：：设置初始值和速度

设置插值器的初始值和速度。

```
virtual BOOL SetInitialValueAndVelocity(
    DOUBLE initialValue,
    DOUBLE initialVelocity);
```

### <a name="parameters"></a>参数

*初始值*<br/>
转换开始时变量的值。

*初始速度*<br/>
转换开始时变量的速度。

### <a name="return-value"></a>返回值

基本实现始终返回 TRUE。 如果要使事件失败，则从重写的实现返回 FALSE。

## <a name="see-also"></a>请参阅

[类](../../mfc/reference/mfc-classes.md)
