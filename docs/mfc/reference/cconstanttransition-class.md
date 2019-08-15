---
title: CConstantTransition 类
ms.date: 11/04/2016
f1_keywords:
- CConstantTransition
- AFXANIMATIONCONTROLLER/CConstantTransition
- AFXANIMATIONCONTROLLER/CConstantTransition::CConstantTransition
- AFXANIMATIONCONTROLLER/CConstantTransition::Create
- AFXANIMATIONCONTROLLER/CConstantTransition::m_duration
helpviewer_keywords:
- CConstantTransition [MFC], CConstantTransition
- CConstantTransition [MFC], Create
- CConstantTransition [MFC], m_duration
ms.assetid: f6fa4780-a71b-4cd6-80aa-d4792ace36c2
ms.openlocfilehash: ccf08b309e64cd82215acb6032bc2a777f4c809a
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69507170"
---
# <a name="cconstanttransition-class"></a>CConstantTransition 类

封装常量转换。

## <a name="syntax"></a>语法

```
class CConstantTransition : public CBaseTransition;
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[CConstantTransition::CConstantTransition](#cconstanttransition)|构造转换对象并初始化其持续时间。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CConstantTransition::Create](#create)|调用转换库以创建封装的转换 COM 对象。 (重写[CBaseTransition:: Create](../../mfc/reference/cbasetransition-class.md#create)。)|

### <a name="public-data-members"></a>公共数据成员

|名称|描述|
|----------|-----------------|
|[CConstantTransition::m_duration](#m_duration)|转换的持续时间。|

## <a name="remarks"></a>备注

在常量转换期间, 动画变量的值将在转换的持续时间内保留为初始值。 由于所有转换都将自动清除, 因此建议使用 operator new 将其分配给它们。 封装的 IUIAnimationTransition COM 对象由 CAnimationController:: AnimateGroup 创建, 直到它为 NULL。 在创建此 COM 对象之后更改成员变量不起作用。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CBaseTransition](../../mfc/reference/cbasetransition-class.md)

`CConstantTransition`

## <a name="requirements"></a>要求

**标头：** afxanimationcontroller.h

##  <a name="cconstanttransition"></a>CConstantTransition:: CConstantTransition

构造转换对象并初始化其持续时间。

```
CConstantTransition (UI_ANIMATION_SECONDS duration);
```

### <a name="parameters"></a>参数

*duration*<br/>
转换的持续时间。

##  <a name="create"></a>CConstantTransition:: Create

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

##  <a name="m_duration"></a>CConstantTransition:: m_duration

转换的持续时间。

```
UI_ANIMATION_SECONDS m_duration;
```

## <a name="see-also"></a>请参阅

[类](../../mfc/reference/mfc-classes.md)
