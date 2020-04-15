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
ms.openlocfilehash: 31c04c303e7e253ec4de41bf076130d19232aac0
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372271"
---
# <a name="clineartransitionfromspeed-class"></a>CLinearTransitionFromSpeed 类

封装线性速度转换。

## <a name="syntax"></a>语法

```
class CLinearTransitionFromSpeed : public CBaseTransition;
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[从速度转换的C线性：从速度转换的C线性转换](#clineartransitionfromspeed)|构造线性速度过渡对象，并初始化其速度和最终值。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[C线性转换从速度：创建](#create)|调用过渡库以创建封装的过渡 COM 对象。 （覆盖[CBase 转换：创建](../../mfc/reference/cbasetransition-class.md#create).）|

### <a name="public-data-members"></a>公共数据成员

|名称|说明|
|----------|-----------------|
|[C线性转换速度：：m_dblFinalValue](#m_dblfinalvalue)|过渡结束时动画变量的值。|
|[C线性转换速度：：m_dblSpeed](#m_dblspeed)|变量速度的绝对值。|

## <a name="remarks"></a>备注

在线性速度转换期间，动画变量的值会以指定速率更改。 转换的持续时间由初始值和指定最终值之间的差异决定。 由于所有转换都将自动清除，因此建议使用运算符 new 分配。 封装的 IUI动画转换 COM 对象由 C动画控制器：：AnimateGroup 创建，直到此为止，它才为 NULL。 创建此 COM 对象后更改成员变量不起作用。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CBase 转换](../../mfc/reference/cbasetransition-class.md)

[C线性从速度转换](../../mfc/reference/clineartransitionfromspeed-class.md)

## <a name="requirements"></a>要求

**标头：** afxanimationcontroller.h

## <a name="clineartransitionfromspeedclineartransitionfromspeed"></a><a name="clineartransitionfromspeed"></a>从速度转换的C线性：从速度转换的C线性转换

构造线性速度过渡对象，并初始化其速度和最终值。

```
CLinearTransitionFromSpeed(
    DOUBLE dblSpeed,
    DOUBLE dblFinalValue);
```

### <a name="parameters"></a>参数

*dblSpeed*<br/>
变量速度的绝对值。

*dbl 最终值*<br/>
过渡结束时动画变量的值。

## <a name="clineartransitionfromspeedcreate"></a><a name="create"></a>C线性转换从速度：创建

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

## <a name="clineartransitionfromspeedm_dblfinalvalue"></a><a name="m_dblfinalvalue"></a>C线性转换速度：：m_dblFinalValue

过渡结束时动画变量的值。

```
DOUBLE m_dblFinalValue;
```

## <a name="clineartransitionfromspeedm_dblspeed"></a><a name="m_dblspeed"></a>C线性转换速度：：m_dblSpeed

变量速度的绝对值。

```
DOUBLE m_dblSpeed;
```

## <a name="see-also"></a>另请参阅

[类](../../mfc/reference/mfc-classes.md)
