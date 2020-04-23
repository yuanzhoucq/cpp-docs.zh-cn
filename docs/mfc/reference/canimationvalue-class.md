---
title: CAnimationValue 类
ms.date: 11/04/2016
f1_keywords:
- CAnimationValue
- AFXANIMATIONCONTROLLER/CAnimationValue
- AFXANIMATIONCONTROLLER/CAnimationValue::CAnimationValue
- AFXANIMATIONCONTROLLER/CAnimationValue::AddTransition
- AFXANIMATIONCONTROLLER/CAnimationValue::GetValue
- AFXANIMATIONCONTROLLER/CAnimationValue::GetVariable
- AFXANIMATIONCONTROLLER/CAnimationValue::SetDefaultValue
- AFXANIMATIONCONTROLLER/CAnimationValue::GetAnimationVariableList
- AFXANIMATIONCONTROLLER/CAnimationValue::m_value
helpviewer_keywords:
- CAnimationValue [MFC], CAnimationValue
- CAnimationValue [MFC], AddTransition
- CAnimationValue [MFC], GetValue
- CAnimationValue [MFC], GetVariable
- CAnimationValue [MFC], SetDefaultValue
- CAnimationValue [MFC], GetAnimationVariableList
- CAnimationValue [MFC], m_value
ms.assetid: 78c5ae19-ede5-4f20-bfbe-68b467b603c2
ms.openlocfilehash: e020e3e123bb5dc96a623e7a41896d75c611b81e
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/22/2020
ms.locfileid: "81755086"
---
# <a name="canimationvalue-class"></a>CAnimationValue 类

实现有一个值的动画对象功能。

## <a name="syntax"></a>语法

```
class CAnimationValue : public CAnimationBaseObject;
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[动画值：：动画值](#canimationvalue)|已重载。 构造 CAnimationValue 对象。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[动画值：：添加转换](#addtransition)|添加要应用于值的过渡。|
|[动画值：获取价值](#getvalue)|已重载。 检索当前值。|
|[动画值：：获取变量](#getvariable)|提供对封装动画变量的访问。|
|[动画值：：设置默认值](#setdefaultvalue)|设置默认值。|

### <a name="protected-methods"></a>受保护的方法

|名称|说明|
|----------|-----------------|
|[动画值：：获取动画变量列表](#getanimationvariablelist)|将封装的动画变量放入列表中。 （覆盖[动画基础对象：获取动画变量列表](../../mfc/reference/canimationbaseobject-class.md#getanimationvariablelist)。|

### <a name="public-operators"></a>公共运算符

|名称|说明|
|----------|-----------------|
|[动画值：：运算符 DOUBLE](#operator_double)|提供"动画值"和"双"之间的转换。|
|[动画值：：操作员 INT32](#operator_int32)|提供 C动画值和 INT32 之间的转换。|
|[动画值：：操作员*](#operator_eq)|已重载。 将 INT32 值分配给 CAnimationValue。|

### <a name="protected-data-members"></a>受保护的数据成员

|名称|说明|
|----------|-----------------|
|[动画值：：m_value](#m_value)|表示动画值的封装动画变量。|

## <a name="remarks"></a>备注

CAnimationValue 类封装单个 CAnimationvariable 对象，可以在应用程序中表示单个动画值。 例如，当需要根据单个动画值创建动画时，可以使用此类进行动画透明度（淡入淡出效果）、角度（旋转对象）或任何其他情况。 要在应用程序中使用此类，只需实例化此类的对象，请使用 CAnimationController：：addAnimationObject 将其添加到动画控制器，并调用要应用于该值的每个转换的 AddTransition。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[动画基础对象](../../mfc/reference/canimationbaseobject-class.md)

`CAnimationValue`

## <a name="requirements"></a>要求

**标头：** afxanimationcontroller.h

## <a name="canimationvalueaddtransition"></a><a name="addtransition"></a>动画值：：添加转换

添加要应用于值的过渡。

```cpp
void AddTransition(CBaseTransition* pTransition);
```

### <a name="parameters"></a>参数

*p 转换*<br/>
指向过渡对象的指针。

### <a name="remarks"></a>备注

调用此函数以向要应用于动画变量的过渡的内部列表添加转换。 添加转换时，不会立即应用这些转换并存储在内部列表中。 当您调用 CAnimationController：：AnimateGroup 时，将应用转换（添加到特定值的情节提要中）。

## <a name="canimationvaluecanimationvalue"></a><a name="canimationvalue"></a>动画值：：动画值

构造 CAnimationValue 对象。

```
CAnimationValue();

CAnimationValue(
    DOUBLE dblDefaultValue,
    UINT32 nGroupID,
    UINT32 nObjectID = (UINT32)-1,
    DWORD dwUserData = 0);
```

### <a name="parameters"></a>参数

*dblDefault值*<br/>
指定默认值。

*n集团ID*<br/>
指定组 ID。

*nObjectID*<br/>
指定对象 ID。

*dwUserData*<br/>
指定用户定义的数据。

### <a name="remarks"></a>备注

构造具有默认属性的 CAnimationValue 对象：默认值、组 ID 和对象 ID 设置为 0。

## <a name="canimationvaluegetanimationvariablelist"></a><a name="getanimationvariablelist"></a>动画值：：获取动画变量列表

将封装的动画变量放入列表中。

```
virtual void GetAnimationVariableList(
    CList<CAnimationVariable*,
    CAnimationVariable*>& lst);
```

### <a name="parameters"></a>参数

*Lst*<br/>
当函数返回时，它包含一个指向表示动画值的 CAnimation 变量的指针。

## <a name="canimationvaluegetvalue"></a><a name="getvalue"></a>动画值：获取价值

检索当前值。

```
BOOL GetValue(DOUBLE& dblValue);
BOOL GetValue(INT32& nValue);
```

### <a name="parameters"></a>参数

*dblValue*<br/>
输出。 当函数返回时，它包含动画变量的当前值。

*n值*<br/>
输出。 当函数返回时，它包含动画变量的当前值。

### <a name="return-value"></a>返回值

如果成功检索当前值，则为 TRUE;如果成功检索当前值，则为 TRUE。否则 FALSE。

### <a name="remarks"></a>备注

调用此函数以检索当前值。 此实现调用封装的 COM 对象，如果调用失败，此方法将返回以前在构造函数或 SetDefaultValue 中设置的默认值。

## <a name="canimationvaluegetvariable"></a><a name="getvariable"></a>动画值：：获取变量

提供对封装动画变量的访问。

```
CAnimationVariable& GetVariable();
```

### <a name="return-value"></a>返回值

对封装动画变量的引用。

### <a name="remarks"></a>备注

使用此方法访问封装的动画变量。 从 CAnimationVariable 可以访问基础 IUI动画变量对象，如果尚未创建动画变量，该对象的指针可以是 NULL。

## <a name="canimationvaluem_value"></a><a name="m_value"></a>动画值：：m_value

表示动画值的封装动画变量。

```
CAnimationVariable m_value;
```

## <a name="canimationvalueoperator-double"></a><a name="operator_double"></a>动画值：：运算符 DOUBLE

提供"动画值"和"双"之间的转换。

```
operator DOUBLE();
```

### <a name="return-value"></a>返回值

动画值的当前值。

### <a name="remarks"></a>备注

提供"动画值"和"双"之间的转换。 此方法在内部调用 GetValue，不检查错误。 如果 GetValue 失败，则返回的值将包含以前在构造函数中设置的默认值或 SetDefaultValue 中设置的值。

## <a name="canimationvalueoperator-int32"></a><a name="operator_int32"></a>动画值：：操作员 INT32

提供 C动画值和 INT32 之间的转换。

```
operator INT32();
```

### <a name="return-value"></a>返回值

动画值的当前值（以整数形式）。

### <a name="remarks"></a>备注

提供 C动画值和 INT32 之间的转换。 此方法在内部调用 GetValue，不检查错误。 如果 GetValue 失败，则返回的值将包含以前在构造函数中设置的默认值或 SetDefaultValue 中设置的值。

## <a name="canimationvalueoperator"></a><a name="operator_eq"></a>动画值：：操作员*

将 DOUBLE 值分配给 CAnimationValue。

```cpp
void operator=(DOUBLE dblVal);
void operator=(INT32 nVal);
```

### <a name="parameters"></a>参数

*德布尔瓦尔*<br/>
指定要分配给动画值的值。

*恩瓦尔*<br/>
指定要分配给动画值的值。

### <a name="remarks"></a>备注

将 DOUBLE 值分配给 CAnimationValue。 此值设置为封装动画变量的默认值。 如果将此动画对象订阅到事件（Value已更改或整数值更改），则需要重新启用这些事件。

## <a name="canimationvaluesetdefaultvalue"></a><a name="setdefaultvalue"></a>动画值：：设置默认值

设置默认值。

```cpp
void SetDefaultValue(DOUBLE dblDefaultValue);
```

### <a name="parameters"></a>参数

*dblDefault值*<br/>
指定默认值。

### <a name="remarks"></a>备注

使用此方法设置默认值。 尚未启动动画和/或尚未创建基础 COM 对象时，默认值将返回到应用程序。 如果已在 CAnimationVarible 中封装的基础 COM 对象已创建，此方法将重新创建它，因此您可能需要再次调用启用Value更改/启用 IntegerValue 更改方法。

## <a name="see-also"></a>请参阅

[类](../../mfc/reference/mfc-classes.md)
