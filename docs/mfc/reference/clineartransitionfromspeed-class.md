---
title: CLinearTransitionFromSpeed 类
ms.date: 11/04/2016
f1_keywords:
- CLinearTransitionFromSpeed
- AFXANIMATIONCONTROLLER/CLinearTransitionFromSpeed
- AFXANIMATIONCONTROLLER/CLinearTransitionFromSpeed::CLinearTransitionFromSpeed
- AFXANIMATIONCONTROLLER/CLinearTransitionFromSpeed::Create
- AFXANIMATIONCONTROLLER/CLinearTransitionFromSpeed::m_dblFinalValue
- AFXANIMATIONCONTROLLER/CLinearTransitionFromSpeed::m_dblSpeed
helpviewer_keywords:
- CLinearTransitionFromSpeed [MFC], CLinearTransitionFromSpeed
- CLinearTransitionFromSpeed [MFC], Create
- CLinearTransitionFromSpeed [MFC], m_dblFinalValue
- CLinearTransitionFromSpeed [MFC], m_dblSpeed
ms.assetid: 8f159a1c-8893-4017-951e-09e5758aba7d
ms.openlocfilehash: 50c958a092478f4b9ec4e94f9e5e973a74c334c2
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69505710"
---
# <a name="clineartransitionfromspeed-class"></a>CLinearTransitionFromSpeed 类

封装线性速度转换。

## <a name="syntax"></a>语法

```
class CLinearTransitionFromSpeed : public CBaseTransition;
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[CLinearTransitionFromSpeed::CLinearTransitionFromSpeed](#clineartransitionfromspeed)|构造线性速度转换对象, 并使用速度和最终值对其进行初始化。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CLinearTransitionFromSpeed::Create](#create)|调用转换库以创建封装的转换 COM 对象。 (重写[CBaseTransition:: Create](../../mfc/reference/cbasetransition-class.md#create)。)|

### <a name="public-data-members"></a>公共数据成员

|名称|描述|
|----------|-----------------|
|[CLinearTransitionFromSpeed::m_dblFinalValue](#m_dblfinalvalue)|转换结束时动画变量的值。|
|[CLinearTransitionFromSpeed::m_dblSpeed](#m_dblspeed)|变量速度的绝对值。|

## <a name="remarks"></a>备注

在线性过渡期间, 动画变量的值以指定速率更改。 转换的持续时间取决于初始值与指定的最后一个值之间的差异。 由于所有转换都将自动清除, 因此建议使用 operator new 将其分配给它们。 封装的 IUIAnimationTransition COM 对象由 CAnimationController:: AnimateGroup 创建, 直到它为 NULL。 在创建此 COM 对象之后更改成员变量不起作用。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CBaseTransition](../../mfc/reference/cbasetransition-class.md)

[CLinearTransitionFromSpeed](../../mfc/reference/clineartransitionfromspeed-class.md)

## <a name="requirements"></a>要求

**标头：** afxanimationcontroller.h

##  <a name="clineartransitionfromspeed"></a>CLinearTransitionFromSpeed:: CLinearTransitionFromSpeed

构造线性速度转换对象, 并使用速度和最终值对其进行初始化。

```
CLinearTransitionFromSpeed(
    DOUBLE dblSpeed,
    DOUBLE dblFinalValue);
```

### <a name="parameters"></a>参数

*dblSpeed*<br/>
变量速度的绝对值。

*dblFinalValue*<br/>
转换结束时动画变量的值。

##  <a name="create"></a>CLinearTransitionFromSpeed:: Create

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

##  <a name="m_dblfinalvalue"></a>CLinearTransitionFromSpeed:: m_dblFinalValue

转换结束时动画变量的值。

```
DOUBLE m_dblFinalValue;
```

##  <a name="m_dblspeed"></a>CLinearTransitionFromSpeed:: m_dblSpeed

变量速度的绝对值。

```
DOUBLE m_dblSpeed;
```

## <a name="see-also"></a>请参阅

[类](../../mfc/reference/mfc-classes.md)
