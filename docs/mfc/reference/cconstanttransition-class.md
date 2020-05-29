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
ms.openlocfilehash: 0d5d92f02cc3b56268966f1cd79451578a5cc390
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369411"
---
# <a name="cconstanttransition-class"></a>CConstantTransition 类

封装常量转换。

## <a name="syntax"></a>语法

```
class CConstantTransition : public CBaseTransition;
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[C 常量转换：：C 常量转换](#cconstanttransition)|构造过渡对象并初始化其持续时间。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[C 常量转换：创建](#create)|调用过渡库以创建封装的过渡 COM 对象。 （覆盖[CBase 转换：创建](../../mfc/reference/cbasetransition-class.md#create).）|

### <a name="public-data-members"></a>公共数据成员

|名称|说明|
|----------|-----------------|
|[C 常量转换：：m_duration](#m_duration)|转换的持续时间。|

## <a name="remarks"></a>备注

在恒定转换期间，动画变量的值在转换期间保持在初始值。 由于所有转换都将自动清除，因此建议使用运算符 new 分配。 封装的 IUI动画转换 COM 对象由 C动画控制器：：AnimateGroup 创建，直到此为止，它才为 NULL。 创建此 COM 对象后更改成员变量不起作用。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CBase 转换](../../mfc/reference/cbasetransition-class.md)

`CConstantTransition`

## <a name="requirements"></a>要求

**标头：** afxanimationcontroller.h

## <a name="cconstanttransitioncconstanttransition"></a><a name="cconstanttransition"></a>C 常量转换：：C 常量转换

构造过渡对象并初始化其持续时间。

```
CConstantTransition (UI_ANIMATION_SECONDS duration);
```

### <a name="parameters"></a>参数

*时间*<br/>
转换的持续时间。

## <a name="cconstanttransitioncreate"></a><a name="create"></a>C 常量转换：创建

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

## <a name="cconstanttransitionm_duration"></a><a name="m_duration"></a>C 常量转换：：m_duration

转换的持续时间。

```
UI_ANIMATION_SECONDS m_duration;
```

## <a name="see-also"></a>另请参阅

[类](../../mfc/reference/mfc-classes.md)
