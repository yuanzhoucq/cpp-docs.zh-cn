---
title: CReversalTransition 类 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CReversalTransition
- AFXANIMATIONCONTROLLER/CReversalTransition
- AFXANIMATIONCONTROLLER/CReversalTransition::CReversalTransition
- AFXANIMATIONCONTROLLER/CReversalTransition::Create
- AFXANIMATIONCONTROLLER/CReversalTransition::m_duration
dev_langs:
- C++
helpviewer_keywords:
- CReversalTransition [MFC], CReversalTransition
- CReversalTransition [MFC], Create
- CReversalTransition [MFC], m_duration
ms.assetid: e89516be-2d07-4885-95a8-fc278f46e3ad
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 393c0ed7c9d1c5715528468e0c611ae399fbadf6
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46431497"
---
# <a name="creversaltransition-class"></a>CReversalTransition 类

封装反向转换。

## <a name="syntax"></a>语法

```
class CReversalTransition : public CBaseTransition;
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[CReversalTransition::CReversalTransition](#creversaltransition)|构造反向转换对象并初始化其持续时间。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CReversalTransition::Create](#create)|调用要创建封装的转换 COM 对象的转换库。 (重写[CBaseTransition::Create](../../mfc/reference/cbasetransition-class.md#create)。)|

### <a name="public-data-members"></a>公共数据成员

|名称|描述|
|----------|-----------------|
|[CReversalTransition::m_duration](#m_duration)|过渡的持续时间。|

## <a name="remarks"></a>备注

反向转换顺利地更改在给定持续时间内的方向。 最终值将为初始值相同，最终的速度将初始速度的负值。 因为会自动清除所有转换，我们建议分配它们使用新运算符。 封装 IUIAnimationTransition 创建 COM 对象通过 CAnimationController::AnimateGroup，直到它为 NULL。 创建此 COM 对象不起作用之后更改成员变量。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CBaseTransition](../../mfc/reference/cbasetransition-class.md)

[CReversalTransition](../../mfc/reference/creversaltransition-class.md)

## <a name="requirements"></a>要求

**标头：** afxanimationcontroller.h

##  <a name="create"></a>  CReversalTransition::Create

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

##  <a name="creversaltransition"></a>  CReversalTransition::CReversalTransition

构造反向转换对象并初始化其持续时间。

```
CReversalTransition(UI_ANIMATION_SECONDS duration);
```

### <a name="parameters"></a>参数

*持续时间*<br/>
过渡的持续时间。

##  <a name="m_duration"></a>  CReversalTransition::m_duration

过渡的持续时间。

```
UI_ANIMATION_SECONDS m_duration;
```

## <a name="see-also"></a>请参阅

[类](../../mfc/reference/mfc-classes.md)
