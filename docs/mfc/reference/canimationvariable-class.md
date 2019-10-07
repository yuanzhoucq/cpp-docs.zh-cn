---
title: CAnimationVariable 类
ms.date: 03/27/2019
f1_keywords:
- CAnimationVariable
- AFXANIMATIONCONTROLLER/CAnimationVariable
- AFXANIMATIONCONTROLLER/CAnimationVariable::CAnimationVariable
- AFXANIMATIONCONTROLLER/CAnimationVariable::AddTransition
- AFXANIMATIONCONTROLLER/CAnimationVariable::ApplyTransitions
- AFXANIMATIONCONTROLLER/CAnimationVariable::ClearTransitions
- AFXANIMATIONCONTROLLER/CAnimationVariable::Create
- AFXANIMATIONCONTROLLER/CAnimationVariable::CreateTransitions
- AFXANIMATIONCONTROLLER/CAnimationVariable::EnableIntegerValueChangedEvent
- AFXANIMATIONCONTROLLER/CAnimationVariable::EnableValueChangedEvent
- AFXANIMATIONCONTROLLER/CAnimationVariable::GetDefaultValue
- AFXANIMATIONCONTROLLER/CAnimationVariable::GetParentAnimationObject
- AFXANIMATIONCONTROLLER/CAnimationVariable::GetValue
- AFXANIMATIONCONTROLLER/CAnimationVariable::GetVariable
- AFXANIMATIONCONTROLLER/CAnimationVariable::SetDefaultValue
- AFXANIMATIONCONTROLLER/CAnimationVariable::SetParentAnimationObject
- AFXANIMATIONCONTROLLER/CAnimationVariable::m_bAutodestroyTransitions
- AFXANIMATIONCONTROLLER/CAnimationVariable::m_dblDefaultValue
- AFXANIMATIONCONTROLLER/CAnimationVariable::m_lstTransitions
- AFXANIMATIONCONTROLLER/CAnimationVariable::m_pParentObject
- AFXANIMATIONCONTROLLER/CAnimationVariable::m_variable
helpviewer_keywords:
- CAnimationVariable [MFC], CAnimationVariable
- CAnimationVariable [MFC], AddTransition
- CAnimationVariable [MFC], ApplyTransitions
- CAnimationVariable [MFC], ClearTransitions
- CAnimationVariable [MFC], Create
- CAnimationVariable [MFC], CreateTransitions
- CAnimationVariable [MFC], EnableIntegerValueChangedEvent
- CAnimationVariable [MFC], EnableValueChangedEvent
- CAnimationVariable [MFC], GetDefaultValue
- CAnimationVariable [MFC], GetParentAnimationObject
- CAnimationVariable [MFC], GetValue
- CAnimationVariable [MFC], GetVariable
- CAnimationVariable [MFC], SetDefaultValue
- CAnimationVariable [MFC], SetParentAnimationObject
- CAnimationVariable [MFC], m_bAutodestroyTransitions
- CAnimationVariable [MFC], m_dblDefaultValue
- CAnimationVariable [MFC], m_lstTransitions
- CAnimationVariable [MFC], m_pParentObject
- CAnimationVariable [MFC], m_variable
ms.assetid: 506e697e-31a8-4033-a27e-292f4d7b42d9
ms.openlocfilehash: b6767ed42d66aff467ef36bd2a7b5234ad181ced
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69507544"
---
# <a name="canimationvariable-class"></a>CAnimationVariable 类

表示动画变量。

## <a name="syntax"></a>语法

```
class CAnimationVariable;
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[CAnimationVariable::CAnimationVariable](#canimationvariable)|构造动画变量对象。|
|[CAnimationVariable:: ~ CAnimationVariable](#_dtorcanimationvariable)|析构函数。 在销毁 CAnimationVariable 对象时调用。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CAnimationVariable::AddTransition](#addtransition)|添加一个转换。|
|[CAnimationVariable::ApplyTransitions](#applytransitions)|将内部列表中的转换添加到情节提要。|
|[CAnimationVariable::ClearTransitions](#cleartransitions)|清除转换。|
|[CAnimationVariable::Create](#create)|创建基础动画变量 COM 对象。|
|[CAnimationVariable::CreateTransitions](#createtransitions)|创建要应用于此动画变量的所有转换。|
|[CAnimationVariable::EnableIntegerValueChangedEvent](#enableintegervaluechangedevent)|启用或禁用 IntegerValueChanged 事件。|
|[CAnimationVariable::EnableValueChangedEvent](#enablevaluechangedevent)|启用或禁用 ValueChanged 事件。|
|[CAnimationVariable::GetDefaultValue](#getdefaultvalue)|返回默认值。|
|[CAnimationVariable::GetParentAnimationObject](#getparentanimationobject)|返回父动画对象。|
|[CAnimationVariable::GetValue](#getvalue)|已重载。 返回动画变量的当前值。|
|[CAnimationVariable::GetVariable](#getvariable)|返回指向 IUIAnimationVariable COM 对象的指针。|
|[CAnimationVariable::SetDefaultValue](#setdefaultvalue)|设置默认值并释放 IUIAnimationVariable COM 对象。|

### <a name="protected-methods"></a>受保护的方法

|名称|描述|
|----------|-----------------|
|[CAnimationVariable::SetParentAnimationObject](#setparentanimationobject)|设置动画变量和动画对象之间的关系。|

### <a name="public-data-members"></a>公共数据成员

|名称|描述|
|----------|-----------------|
|[CAnimationVariable::m_bAutodestroyTransitions](#m_bautodestroytransitions)|指定是否应删除相关转换对象。|

### <a name="protected-data-members"></a>受保护的数据成员

|name|描述|
|----------|-----------------|
|[CAnimationVariable::m_dblDefaultValue](#m_dbldefaultvalue)|指定传播到 IUIAnimationVariable 的默认值。|
|[CAnimationVariable::m_lstTransitions](#m_lsttransitions)|包含对此动画变量进行动画处理的转换的列表。|
|[CAnimationVariable::m_pParentObject](#m_pparentobject)|指向封装此动画变量的动画对象的指针。|
|[CAnimationVariable::m_variable](#m_variable)|存储指向 IUIAnimationVariable COM 对象的指针。 如果尚未创建 COM 对象, 则为 NULL; 否则为。|

## <a name="remarks"></a>备注

CAnimationVariable 类封装 IUIAnimationVariable COM 对象。 它还包含要应用于情节提要中的动画变量的转换的列表。 CAnimationVariable 对象嵌入到动画对象, 动画对象在应用程序中表示动画值、点、大小、颜色和矩形。

## <a name="inheritance-hierarchy"></a>继承层次结构

`CAnimationVariable`

## <a name="requirements"></a>要求

**标头：** afxanimationcontroller.h

##  <a name="_dtorcanimationvariable"></a>CAnimationVariable:: ~ CAnimationVariable

析构函数。 在销毁 CAnimationVariable 对象时调用。

```
virtual ~CAnimationVariable();
```

##  <a name="addtransition"></a>CAnimationVariable:: AddTransition

添加一个转换。

```
void AddTransition(CBaseTransition* pTransition);
```

### <a name="parameters"></a>参数

*pTransition*<br/>
指向要添加的转换的指针。

### <a name="remarks"></a>备注

调用此方法可将转换添加到要应用于动画变量的转换的内部列表。 计划动画时, 应清除此列表。

##  <a name="applytransitions"></a>CAnimationVariable:: ApplyTransitions

将内部列表中的转换添加到情节提要。

```
void ApplyTransitions(
    CAnimationController* pController,
    IUIAnimationStoryboard* pStoryboard,
    BOOL bDependOnKeyframes);
```

### <a name="parameters"></a>参数

*pController*<br/>
指向父动画控制器的指针。

*pStoryboard*<br/>
指向情节提要的指针。

*bDependOnKeyframes*<br/>
如果此方法应添加依赖于关键帧的转换, 则为 TRUE。

### <a name="remarks"></a>备注

此方法将内部列表中的转换添加到情节提要。 它将多次从顶级代码调用, 以添加不依赖于关键帧的转换, 并添加依赖于关键帧的转换。 如果尚未创建基础动画变量 COM 对象, 则此方法会在此阶段创建该对象。

##  <a name="canimationvariable"></a>CAnimationVariable:: CAnimationVariable

构造动画变量对象。

```
CAnimationVariable(DOUBLE dblDefaultValue = 0.0);
```

### <a name="parameters"></a>参数

*dblDefaultValue*<br/>
指定默认值。

### <a name="remarks"></a>备注

构造动画变量对象并设置其默认值。 当变量未进行动画处理或无法进行动画处理时, 将使用默认值。

##  <a name="cleartransitions"></a>CAnimationVariable:: ClearTransitions

清除转换。

```
void ClearTransitions(BOOL bAutodestroy);
```

### <a name="parameters"></a>参数

*bAutodestroy*<br/>
指定此方法是否应删除转换对象。

### <a name="remarks"></a>备注

此方法删除内部转换列表中的所有转换。 如果 bAutodestroy 为 TRUE, 或 m_bAutodestroyTransitions 为 TRUE, 则将删除转换。 否则, 调用方应释放转换对象。

##  <a name="create"></a>CAnimationVariable:: Create

创建基础动画变量 COM 对象。

```
virtual BOOL Create(IUIAnimationManager* pManager);
```

### <a name="parameters"></a>参数

*pManager*<br/>
指向动画管理器的指针。

### <a name="return-value"></a>返回值

如果已成功创建动画变量, 则为 TRUE;否则为 FALSE。

### <a name="remarks"></a>备注

此方法创建基础动画变量 COM 对象并设置其默认值。

##  <a name="createtransitions"></a>CAnimationVariable:: CreateTransitions

创建要应用于此动画变量的所有转换。

```
BOOL CreateTransitions(
    IUIAnimationTransitionLibrary* pLibrary,
    IUIAnimationTransitionFactory* \*not used*\);
```

### <a name="parameters"></a>参数

*pLibrary*<br/>
指向[IUIAnimationTransitionLibrary 接口](/windows/win32/api/uianimation/nn-uianimation-iuianimationtransitionlibrary)的指针, 该接口定义标准转换库。

### <a name="return-value"></a>返回值

如果成功创建了转换, 则为 TRUE;否则为 FALSE。

### <a name="remarks"></a>备注

当框架需要创建已添加到变量的内部转换列表中的转换时, 框架会调用此方法。

##  <a name="enableintegervaluechangedevent"></a>CAnimationVariable:: EnableIntegerValueChangedEvent

启用或禁用 IntegerValueChanged 事件。

```
void EnableIntegerValueChangedEvent (
    CAnimationController* pController,
    BOOL bEnable);
```

### <a name="parameters"></a>参数

*pController*<br/>
指向父控制器的指针。

*bEnable*<br/>
TRUE-启用事件, FALSE-禁用事件。

### <a name="remarks"></a>备注

启用 ValueChanged 事件后, 框架将调用虚拟方法 CAnimationController:: OnAnimationIntegerValueChanged。 你需要在从 CAnimationController 派生的类中重写它, 才能处理此事件。 每次更改动画变量的整数值时, 都会调用此方法。

##  <a name="enablevaluechangedevent"></a>CAnimationVariable:: EnableValueChangedEvent

启用或禁用 ValueChanged 事件。

```
void EnableValueChangedEvent (
    CAnimationController* pController,
    BOOL bEnable);
```

### <a name="parameters"></a>参数

*pController*<br/>
指向父控制器的指针。

*bEnable*<br/>
TRUE-启用事件, FALSE-禁用事件。

### <a name="remarks"></a>备注

启用 ValueChanged 事件后, 框架将调用虚拟方法 CAnimationController:: OnAnimationValueChanged。 你需要在从 CAnimationController 派生的类中重写它, 才能处理此事件。 每次更改动画变量的值时, 都会调用此方法。

##  <a name="getdefaultvalue"></a>CAnimationVariable:: GetDefaultValue

返回默认值。

```
DOUBLE GetDefaultValue() const;
```

### <a name="return-value"></a>返回值

默认值。

### <a name="remarks"></a>备注

使用此函数获取动画变量的默认值。 可以在构造函数或 SetDefaultValue 方法中设置默认值。

##  <a name="getparentanimationobject"></a>CAnimationVariable:: GetParentAnimationObject

返回父动画对象。

```
CAnimationBaseObject* GetParentAnimationObject();
```

### <a name="return-value"></a>返回值

如果已建立关系, 则为指向父级动画对象的指针; 否则为 NULL。

### <a name="remarks"></a>备注

可以调用此方法来检索指向父动画对象 (容器) 的指针。

##  <a name="getvalue"></a>CAnimationVariable:: GetValue

返回动画变量的当前值。

```
HRESULT GetValue(DOUBLE& dblValue);
HRESULT GetValue(INT32& nValue);
```

### <a name="parameters"></a>参数

*dblValue*<br/>
动画变量的当前值。

*nValue*<br/>
动画变量的当前值。

### <a name="return-value"></a>返回值

如果已成功获取值, 则为 S_OK; 否则尚未创建基础动画变量。 否则为 HRESULT 错误代码。

### <a name="remarks"></a>备注

可以调用此方法来检索动画变量的当前值。 如果尚未创建基础 COM 对象, 则当函数返回时, dblValue 将包含默认值。

##  <a name="getvariable"></a>CAnimationVariable:: GetVariable

返回指向 IUIAnimationVariable COM 对象的指针。

```
IUIAnimationVariable* GetVariable();
```

### <a name="return-value"></a>返回值

指向 IUIAnimationVariable COM 对象的有效指针, 如果未创建或无法创建动画变量, 则为 NULL。

### <a name="remarks"></a>备注

使用此函数可访问基础 IUIAnimationVariable COM 对象, 并根据需要直接调用其方法。

##  <a name="m_bautodestroytransitions"></a>CAnimationVariable:: m_bAutodestroyTransitions

指定是否应删除相关转换对象。

```
BOOL m_bAutodestroyTransitions;
```

### <a name="remarks"></a>备注

将此值设置为 TRUE 可在从转换的内部列表中删除转换对象时强制删除这些对象。 如果此值为 FALSE, 则应通过调用应用程序删除转换。 转换列表在动画计划之后始终会被清除。 默认值是 FALSE。

##  <a name="m_dbldefaultvalue"></a>CAnimationVariable:: m_dblDefaultValue

指定传播到 IUIAnimationVariable 的默认值。

```
DOUBLE m_dblDefaultValue;
```

##  <a name="m_lsttransitions"></a>CAnimationVariable:: m_lstTransitions

包含对此动画变量进行动画处理的转换的列表。

```
CObList m_lstTransitions;
```

##  <a name="m_pparentobject"></a>CAnimationVariable:: m_pParentObject

指向封装此动画变量的动画对象的指针。

```
CAnimationBaseObject* m_pParentObject;
```

##  <a name="m_variable"></a>CAnimationVariable:: m_variable

存储指向 IUIAnimationVariable COM 对象的指针。 如果尚未创建 COM 对象, 则为 NULL; 否则为。

```
ATL::CComPtr<IUIAnimationVariable> m_variable;
```

##  <a name="setdefaultvalue"></a>CAnimationVariable:: SetDefaultValue

设置默认值并释放 IUIAnimationVariable COM 对象。

```
void SetDefaultValue(DOUBLE dblDefaultValue);
```

### <a name="parameters"></a>参数

*dblDefaultValue*<br/>
指定新的默认值。

### <a name="remarks"></a>备注

使用此方法重置默认值。 此方法释放内部 IUIAnimationVariable COM 对象, 因此, 在重新创建动画变量时, 基础 COM 对象将获取新的默认值。 如果未创建表示动画变量的 COM 对象, 或者如果该变量尚未进行动画处理, 则使用 GetValue 返回默认值。

##  <a name="setparentanimationobject"></a>CAnimationVariable:: SetParentAnimationObject

设置动画变量和动画对象之间的关系。

```
void SetParentAnimationObject(CAnimationBaseObject* pParentObject);
```

### <a name="parameters"></a>参数

*pParentObject*<br/>
指向包含此变量的动画对象的指针。

### <a name="remarks"></a>备注

此方法在内部调用, 以在动画变量和封装它的动画对象之间建立一对一关系。

## <a name="see-also"></a>请参阅

[类](../../mfc/reference/mfc-classes.md)
