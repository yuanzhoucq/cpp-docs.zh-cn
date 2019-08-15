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
ms.openlocfilehash: 7087dfa13972737f0a1244d2cc9a7088b23dc184
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69506852"
---
# <a name="cdiscretetransition-class"></a>CDiscreteTransition 类

封装离散转换。

## <a name="syntax"></a>语法

```
class CDiscreteTransition : public CBaseTransition;
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[CDiscreteTransition::CDiscreteTransition](#cdiscretetransition)|构造离散转换对象并初始化其参数。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CDiscreteTransition::Create](#create)|调用转换库以创建封装的转换 COM 对象。 (重写[CBaseTransition:: Create](../../mfc/reference/cbasetransition-class.md#create)。)|

### <a name="public-data-members"></a>公共数据成员

|名称|描述|
|----------|-----------------|
|[CDiscreteTransition::m_dblFinalValue](#m_dblfinalvalue)|转换结束时动画变量的值。|
|[CDiscreteTransition::m_delay](#m_delay)|将瞬时开关延迟到最终值的时间量。|
|[CDiscreteTransition::m_hold](#m_hold)|变量在其最终值上保留的时间量。|

## <a name="remarks"></a>备注

在离散转换期间, 动画变量在指定延迟时间内保持为初始值, 然后立即切换到指定的最终值并在给定的保留时间内保持该值。 由于所有转换都将自动清除, 因此建议使用 operator new 将其分配给它们。 封装的 IUIAnimationTransition COM 对象由 CAnimationController:: AnimateGroup 创建, 直到它为 NULL。 在创建此 COM 对象之后更改成员变量不起作用。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CBaseTransition](../../mfc/reference/cbasetransition-class.md)

[CDiscreteTransition](../../mfc/reference/cdiscretetransition-class.md)

## <a name="requirements"></a>要求

**标头：** afxanimationcontroller.h

##  <a name="cdiscretetransition"></a>CDiscreteTransition:: CDiscreteTransition

构造离散转换对象并初始化其参数。

```
CDiscreteTransition(
    UI_ANIMATION_SECONDS delay,
    DOUBLE dblFinalValue,
    UI_ANIMATION_SECONDS hold);
```

### <a name="parameters"></a>参数

*delay*<br/>
将瞬时开关延迟到最终值的时间量。

*dblFinalValue*<br/>
转换结束时动画变量的值。

*暂时*<br/>
变量在其最终值上保留的时间量。

##  <a name="create"></a>CDiscreteTransition:: Create

调用转换库以创建封装的转换 COM 对象。

```
virtual BOOL Create(
    IUIAnimationTransitionLibrary* pLibrary,
    IUIAnimationTransitionFactory* \*not used*\);
```

*pLibrary*<br/>
指向[IUIAnimationTransitionLibrary 接口](/windows/win32/api/uianimation/nn-uianimation-iuianimationtransitionlibrary)的指针, 该接口定义标准转换库。

### <a name="return-value"></a>返回值

如果成功创建转换, 则为 TRUE;否则为 FALSE。

##  <a name="m_dblfinalvalue"></a>CDiscreteTransition:: m_dblFinalValue

转换结束时动画变量的值。

```
DOUBLE m_dblFinalValue;
```

##  <a name="m_delay"></a>CDiscreteTransition:: m_delay

将瞬时开关延迟到最终值的时间量。

```
UI_ANIMATION_SECONDS m_delay;
```

##  <a name="m_hold"></a>CDiscreteTransition:: m_hold

变量在其最终值上保留的时间量。

```
UI_ANIMATION_SECONDS m_hold;
```

## <a name="see-also"></a>请参阅

[类](../../mfc/reference/mfc-classes.md)
