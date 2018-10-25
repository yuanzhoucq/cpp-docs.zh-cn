---
title: CAnimationValue 类 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- CAnimationValue [MFC], CAnimationValue
- CAnimationValue [MFC], AddTransition
- CAnimationValue [MFC], GetValue
- CAnimationValue [MFC], GetVariable
- CAnimationValue [MFC], SetDefaultValue
- CAnimationValue [MFC], GetAnimationVariableList
- CAnimationValue [MFC], m_value
ms.assetid: 78c5ae19-ede5-4f20-bfbe-68b467b603c2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: afa8c61894a62df81705f98d461a37c35f615510
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/25/2018
ms.locfileid: "50062582"
---
# <a name="canimationvalue-class"></a>CAnimationValue 类

实现有一个值的动画对象功能。

## <a name="syntax"></a>语法

```
class CAnimationValue : public CAnimationBaseObject;
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[CAnimationValue::CAnimationValue](#canimationvalue)|已重载。 构造一个 CAnimationValue 对象。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CAnimationValue::AddTransition](#addtransition)|添加转换应用于一个值。|
|[CAnimationValue::GetValue](#getvalue)|已重载。 检索当前值。|
|[CAnimationValue::GetVariable](#getvariable)|提供对封装的动画变量的访问。|
|[CAnimationValue::SetDefaultValue](#setdefaultvalue)|设置默认值。|

### <a name="protected-methods"></a>受保护的方法

|名称|描述|
|----------|-----------------|
|[CAnimationValue::GetAnimationVariableList](#getanimationvariablelist)|将封装的动画变量放入列表。 (重写[CAnimationBaseObject::GetAnimationVariableList](../../mfc/reference/canimationbaseobject-class.md#getanimationvariablelist)。)|

### <a name="public-operators"></a>公共运算符

|名称|描述|
|----------|-----------------|
|[CAnimationValue::operator 双](#operator_double)|提供之间 CAnimationValue 和双精度型的转换。|
|[CAnimationValue::operator INT32](#operator_int32)|提供了 CAnimationValue 和 INT32 之间的转换。|
|[CAnimationValue::operator =](#operator_eq)|已重载。 将一个 INT32 值分配给 CAnimationValue。|

### <a name="protected-data-members"></a>受保护的数据成员

|name|描述|
|----------|-----------------|
|[CAnimationValue::m_value](#m_value)|表示动画值的封装的动画变量。|

## <a name="remarks"></a>备注

CAnimationValue 类封装单个 CAnimationVariable 对象，并可以表示在应用程序中的单个动画的值。 例如，可以使用此类为动画的透明度 （淡入淡出效果） 角度 （以旋转对象），或任何其他用例时您需要创建一个动画，具体取决于单个动画值。 若要使用此类应用程序中，只需实例化此类的对象、 将其添加到动画控制器使用 CAnimationController::AddAnimationObject 和调用每个转换的下，若要应用于值。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CAnimationBaseObject](../../mfc/reference/canimationbaseobject-class.md)

`CAnimationValue`

## <a name="requirements"></a>要求

**标头：** afxanimationcontroller.h

##  <a name="addtransition"></a>  CAnimationValue::AddTransition

添加转换应用于一个值。

```
void AddTransition(CBaseTransition* pTransition);
```

### <a name="parameters"></a>参数

*pTransition*<br/>
指向转换对象的指针。

### <a name="remarks"></a>备注

调用此函数可将转换添加到内部列表转换为应用于动画变量。 添加转换，它们不会立即应用并存储在内部列表。 转换应用 （已添加到情节提要的特定值） 当你调用 CAnimationController::AnimateGroup。

##  <a name="canimationvalue"></a>  CAnimationValue::CAnimationValue

构造一个 CAnimationValue 对象。

```
CAnimationValue();

CAnimationValue(
    DOUBLE dblDefaultValue,
    UINT32 nGroupID,
    UINT32 nObjectID = (UINT32)-1,
    DWORD dwUserData = 0);
```

### <a name="parameters"></a>参数

*dblDefaultValue*<br/>
指定默认值。

*nGroupID*<br/>
指定组 id。

*nObjectID*<br/>
指定对象 id。

*dwUserData*<br/>
指定用户定义的数据。

### <a name="remarks"></a>备注

构造具有默认属性 CAnimationValue 对象： 组 ID 和对象 ID 的默认值设置为 0。

##  <a name="getanimationvariablelist"></a>  CAnimationValue::GetAnimationVariableList

将封装的动画变量放入列表。

```
virtual void GetAnimationVariableList(
    CList<CAnimationVariable*,
    CAnimationVariable*>& lst);
```

### <a name="parameters"></a>参数

*lst*<br/>
当函数返回时，它包含指向 CAnimationVariable 表示动画的值的指针。

##  <a name="getvalue"></a>  CAnimationValue::GetValue

检索当前值。

```
BOOL GetValue(DOUBLE& dblValue);
BOOL GetValue(INT32& nValue);
```

### <a name="parameters"></a>参数

*dblValue*<br/>
输出。 在函数返回时它会包含动画变量的当前值。

*n 值*<br/>
输出。 在函数返回时它会包含动画变量的当前值。

### <a name="return-value"></a>返回值

如果成功，则检索到的当前值，则返回 TRUE否则为 FALSE。

### <a name="remarks"></a>备注

调用此函数可检索当前值。 此实现会调用封装的 COM 对象，并且如果调用失败，此方法返回在构造函数中或使用 SetDefaultValue 以前设置的默认值。

##  <a name="getvariable"></a>  CAnimationValue::GetVariable

提供对封装的动画变量的访问。

```
CAnimationVariable& GetVariable();
```

### <a name="return-value"></a>返回值

对封装的动画变量的引用。

### <a name="remarks"></a>备注

使用此方法访问封装的动画变量。 从 CAnimationVariable 你有权访问基础 IUIAnimationVariable 对象，其指针可以为 NULL，如果尚未创建动画变量。

##  <a name="m_value"></a>  CAnimationValue::m_value

表示动画值的封装的动画变量。

```
CAnimationVariable m_value;
```

##  <a name="operator_double"></a>  CAnimationValue::operator 双

提供之间 CAnimationValue 和双精度型的转换。

```
operator DOUBLE();
```

### <a name="return-value"></a>返回值

动画值的当前值。

### <a name="remarks"></a>备注

提供之间 CAnimationValue 和双精度型的转换。 此方法在内部调用 GetValue 并不会检查有错误。 如果 GetValue 失败，返回的值将包含在构造函数中或使用 SetDefaultValue 以前设置的默认值。

##  <a name="operator_int32"></a>  CAnimationValue::operator INT32

提供了 CAnimationValue 和 INT32 之间的转换。

```
operator INT32();
```

### <a name="return-value"></a>返回值

动画值作为整数的当前值。

### <a name="remarks"></a>备注

提供了 CAnimationValue 和 INT32 之间的转换。 此方法在内部调用 GetValue 并不会检查有错误。 如果 GetValue 失败，返回的值将包含在构造函数中或使用 SetDefaultValue 以前设置的默认值。

##  <a name="operator_eq"></a>  CAnimationValue::operator =

将一个双精度值分配给 CAnimationValue。

```
void operator=(DOUBLE dblVal);
void operator=(INT32 nVal);
```

### <a name="parameters"></a>参数

*dblVal*<br/>
指定要分配给动画的值的值。

*nVal*<br/>
指定要分配给动画的值的值。

### <a name="remarks"></a>备注

将一个双精度值分配给 CAnimationValue。 此值设置为封装的动画变量的默认值。 如果你订阅事件 （ValueChanged 或 IntegerValueChanged） 此动画对象，您需要重新启用这些事件。

##  <a name="setdefaultvalue"></a>  CAnimationValue::SetDefaultValue

设置默认值。

```
void SetDefaultValue(DOUBLE dblDefaultValue);
```

### <a name="parameters"></a>参数

*dblDefaultValue*<br/>
指定默认值。

### <a name="remarks"></a>备注

此方法用于设置默认值。 尚未启动动画和/或尚未创建基础 COM 对象时，默认值被返回到应用程序。 如果已创建封装在 CAnimationVarible 的基础 COM 对象，此方法将重新创建它，因此您可能需要再次调用 EnableValueChanged/EnableIntegerValueChanged 方法。

## <a name="see-also"></a>请参阅

[类](../../mfc/reference/mfc-classes.md)
