---
title: CSmoothStopTransition 类 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CSmoothStopTransition
- AFXANIMATIONCONTROLLER/CSmoothStopTransition
- AFXANIMATIONCONTROLLER/CSmoothStopTransition::CSmoothStopTransition
- AFXANIMATIONCONTROLLER/CSmoothStopTransition::Create
- AFXANIMATIONCONTROLLER/CSmoothStopTransition::m_dblFinalValue
- AFXANIMATIONCONTROLLER/CSmoothStopTransition::m_maximumDuration
dev_langs:
- C++
helpviewer_keywords:
- CSmoothStopTransition [MFC], CSmoothStopTransition
- CSmoothStopTransition [MFC], Create
- CSmoothStopTransition [MFC], m_dblFinalValue
- CSmoothStopTransition [MFC], m_maximumDuration
ms.assetid: e1a4b476-6f96-43dd-90db-870a64406b85
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: db43e550b38778dbbdc34fb6e696129ca767d28f
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46377734"
---
# <a name="csmoothstoptransition-class"></a>CSmoothStopTransition 类

封装平稳停止转换。

## <a name="syntax"></a>语法

```
class CSmoothStopTransition : public CBaseTransition;
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[CSmoothStopTransition::CSmoothStopTransition](#csmoothstoptransition)|构造平稳停止转换并初始化其最大持续时间和最终值。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CSmoothStopTransition::Create](#create)|调用要创建封装的转换 COM 对象的转换库。 (重写[CBaseTransition::Create](../../mfc/reference/cbasetransition-class.md#create)。)|

### <a name="public-data-members"></a>公共数据成员

|名称|描述|
|----------|-----------------|
|[CSmoothStopTransition::m_dblFinalValue](#m_dblfinalvalue)|转换结束时的动画变量的值。|
|[CSmoothStopTransition::m_maximumDuration](#m_maximumduration)|过渡的最大持续时间。|

## <a name="remarks"></a>备注

随着它接近给定的最终值，并且使用零速度达到平稳停止转换速度变慢。 过渡的持续时间取决于初始速度，初始和最终值和指定的最大持续时间之间的差异。 如果有任何解决方案，其中包含的单一的抛物线圆弧，则此方法创建三次转换。 因为会自动清除所有转换，我们建议分配它们使用新运算符。 封装 IUIAnimationTransition 创建 COM 对象通过 CAnimationController::AnimateGroup，直到它为 NULL。 创建此 COM 对象不起作用之后更改成员变量。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CBaseTransition](../../mfc/reference/cbasetransition-class.md)

[CSmoothStopTransition](../../mfc/reference/csmoothstoptransition-class.md)

## <a name="requirements"></a>要求

**标头：** afxanimationcontroller.h

##  <a name="create"></a>  CSmoothStopTransition::Create

调用要创建封装的转换 COM 对象的转换库。

```
virtual BOOL Create(
    IUIAnimationTransitionLibrary* pLibrary,
    IUIAnimationTransitionFactory* \*not used*\);
```

### <a name="parameters"></a>参数

*pLibrary*<br/>
指向转换库，负责创建标准转换的指针。

### <a name="return-value"></a>返回值

如果成功，则创建转换，则返回 TRUE否则为 FALSE。

##  <a name="csmoothstoptransition"></a>  CSmoothStopTransition::CSmoothStopTransition

构造平稳停止转换并初始化其最大持续时间和最终值。

```
CSmoothStopTransition(
    UI_ANIMATION_SECONDS maximumDuration,
    DOUBLE dblFinalValue);
```

### <a name="parameters"></a>参数

*maximumDuration*<br/>
过渡的最大持续时间。

*dblFinalValue*<br/>
转换结束时的动画变量的值。

##  <a name="m_dblfinalvalue"></a>  CSmoothStopTransition::m_dblFinalValue

转换结束时的动画变量的值。

```
DOUBLE m_dblFinalValue;
```

##  <a name="m_maximumduration"></a>  CSmoothStopTransition::m_maximumDuration

过渡的最大持续时间。

```
UI_ANIMATION_SECONDS m_maximumDuration;
```

## <a name="see-also"></a>请参阅

[类](../../mfc/reference/mfc-classes.md)
