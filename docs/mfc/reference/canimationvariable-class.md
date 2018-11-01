---
title: CAnimationVariable 类
ms.date: 11/04/2016
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
ms.openlocfilehash: 1ad14060c7607698cd647ae34fb35b6ea3ae547c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50559557"
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
|[CAnimationVariable::CAnimationVariable](#canimationvariable)|构造一个动画变量对象。|
|[CAnimationVariable:: ~ CAnimationVariable](#canimationvariable__~canimationvariable)|析构函数。 CAnimationVariable 对象被销毁时调用。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CAnimationVariable::AddTransition](#addtransition)|添加转换。|
|[CAnimationVariable::ApplyTransitions](#applytransitions)|将转换添加到情节提要的内部列表中。|
|[CAnimationVariable::ClearTransitions](#cleartransitions)|清除转换。|
|[CAnimationVariable::Create](#create)|创建基础动画变量 COM 对象。|
|[CAnimationVariable::CreateTransitions](#createtransitions)|创建要应用于此动画变量的所有转换。|
|[CAnimationVariable::EnableIntegerValueChangedEvent](#enableintegervaluechangedevent)|启用或禁用 IntegerValueChanged 事件。|
|[CAnimationVariable::EnableValueChangedEvent](#enablevaluechangedevent)|启用或禁用 ValueChanged 事件。|
|[CAnimationVariable::GetDefaultValue](#getdefaultvalue)|返回默认值。|
|[CAnimationVariable::GetParentAnimationObject](#getparentanimationobject)|返回父动画对象。|
|[CAnimationVariable::GetValue](#getvalue)|已重载。 返回当前动画变量的值。|
|[CAnimationVariable::GetVariable](#getvariable)|返回指向 IUIAnimationVariable COM 对象的指针。|
|[CAnimationVariable::SetDefaultValue](#setdefaultvalue)|设置默认值并释放 IUIAnimationVariable COM 对象。|

### <a name="protected-methods"></a>受保护的方法

|名称|描述|
|----------|-----------------|
|[CAnimationVariable::SetParentAnimationObject](#setparentanimationobject)|设置动画变量和动画对象之间的关系。|

### <a name="public-data-members"></a>公共数据成员

|名称|描述|
|----------|-----------------|
|[CAnimationVariable::m_bAutodestroyTransitions](#m_bautodestroytransitions)|指定是否应删除相关的转换对象。|

### <a name="protected-data-members"></a>受保护的数据成员

|name|描述|
|----------|-----------------|
|[CAnimationVariable::m_dblDefaultValue](#m_dbldefaultvalue)|指定默认值传播到 IUIAnimationVariable。|
|[CAnimationVariable::m_lstTransitions](#m_lsttransitions)|包含转换进行动画处理此动画变量的列表。|
|[CAnimationVariable::m_pParentObject](#m_pparentobject)|指向一个封装此动画变量的动画对象的指针。|
|[CAnimationVariable::m_variable](#m_variable)|存储指向 IUIAnimationVariable COM 对象的指针。 如果尚未，创建 COM 对象或创建失败，则为 NULL。|

## <a name="remarks"></a>备注

CAnimationVariable 类封装 IUIAnimationVariable COM 对象。 它还包含一系列转换应用于情节提要中的动画变量。 CAnimationVariable 对象嵌入到动画对象，它可以在应用程序经过动画处理的值、 点、 大小、 颜色和矩形表示。

## <a name="inheritance-hierarchy"></a>继承层次结构

`CAnimationVariable`

## <a name="requirements"></a>要求

**标头：** afxanimationcontroller.h

##  <a name="_dtorcanimationvariable"></a>  CAnimationVariable:: ~ CAnimationVariable

析构函数。 CAnimationVariable 对象被销毁时调用。

```
virtual ~CAnimationVariable();
```

##  <a name="addtransition"></a>  CAnimationVariable::AddTransition

添加转换。

```
void AddTransition(CBaseTransition* pTransition);
```

### <a name="parameters"></a>参数

*pTransition*<br/>
指向要添加的转换的指针。

### <a name="remarks"></a>备注

调用此方法将转换添加到转换应用于动画变量的内部列表。 在计划动画时，应清除此列表。

##  <a name="applytransitions"></a>  CAnimationVariable::ApplyTransitions

将转换添加到情节提要的内部列表中。

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
情节提要的指针。

*bDependOnKeyframes*<br/>
如果为 TRUE，此方法应添加依赖于关键帧的转换。

### <a name="remarks"></a>备注

此方法将转换添加到情节提要的内部列表中。 它是从代码中调用最高级别多次添加转换，请不要依赖于关键帧并添加依赖于关键帧的转换。 如果尚未创建基础的动画变量的 COM 对象，此方法将创建它在此阶段。

##  <a name="canimationvariable"></a>  CAnimationVariable::CAnimationVariable

构造一个动画变量对象。

```
CAnimationVariable(DOUBLE dblDefaultValue = 0.0);
```

### <a name="parameters"></a>参数

*dblDefaultValue*<br/>
指定默认值。

### <a name="remarks"></a>备注

将构造一个动画变量对象并设置其默认值。 变量未进行动画处理，或不能进行动画处理时，使用默认值。

##  <a name="cleartransitions"></a>  CAnimationVariable::ClearTransitions

清除转换。

```
void ClearTransitions(BOOL bAutodestroy);
```

### <a name="parameters"></a>参数

*bAutodestroy*<br/>
指定此方法是否应删除转换对象。

### <a name="remarks"></a>备注

此方法从转换的内部列表中移除所有转换。 如果 bAutodestroy 为 TRUE，或 m_bAutodestroyTransitions 为 TRUE，则会删除转换。 否则调用方应释放转换对象。

##  <a name="create"></a>  CAnimationVariable::Create

创建基础动画变量 COM 对象。

```
virtual BOOL Create(IUIAnimationManager* pManager);
```

### <a name="parameters"></a>参数

*pManager*<br/>
动画管理器指向的指针。

### <a name="return-value"></a>返回值

如果已成功创建动画变量; 则为 TRUE否则为 FALSE。

### <a name="remarks"></a>备注

此方法创建的基础的动画变量的 COM 对象，并设置其默认值。

##  <a name="createtransitions"></a>  CAnimationVariable::CreateTransitions

创建要应用于此动画变量的所有转换。

```
BOOL CreateTransitions(
    IUIAnimationTransitionLibrary* pLibrary,
    IUIAnimationTransitionFactory* \*not used*\);
```

### <a name="parameters"></a>参数

*pLibrary*<br/>
一个指向[IUIAnimationTransitionLibrary 接口](/windows/desktop/api/uianimation/nn-uianimation-iuianimationtransitionlibrary)，用于定义的标准转换库。

### <a name="return-value"></a>返回值

如果转换成功，则已创建，则返回 TRUE否则为 FALSE。

### <a name="remarks"></a>备注

需要创建已添加到变量的内部列表中的转换的转换时，由框架调用此方法。

##  <a name="enableintegervaluechangedevent"></a>  CAnimationVariable::EnableIntegerValueChangedEvent

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
TRUE-启用事件，FALSE-禁用事件。

### <a name="remarks"></a>备注

启用 ValueChanged 事件后，框架将调用虚拟方法 CAnimationController::OnAnimationIntegerValueChanged。 您需要以处理此事件从 CAnimationController 派生的类中重写它。 每次更改动画变量的整数值时，调用此方法。

##  <a name="enablevaluechangedevent"></a>  CAnimationVariable::EnableValueChangedEvent

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
TRUE-启用事件，FALSE-禁用事件。

### <a name="remarks"></a>备注

启用 ValueChanged 事件后，框架将调用虚拟方法 CAnimationController::OnAnimationValueChanged。 您需要以处理此事件从 CAnimationController 派生的类中重写它。 每次更改动画变量的值时，调用此方法。

##  <a name="getdefaultvalue"></a>  CAnimationVariable::GetDefaultValue

返回默认值。

```
DOUBLE GetDefaultValue() const;
```

### <a name="return-value"></a>返回值

默认值。

### <a name="remarks"></a>备注

使用此函数获取动画变量的默认值。 可以在构造函数或 SetDefaultValue 方法设置默认值。

##  <a name="getparentanimationobject"></a>  CAnimationVariable::GetParentAnimationObject

返回父动画对象。

```
CAnimationBaseObject* GetParentAnimationObject();
```

### <a name="return-value"></a>返回值

一个指针指向父动画对象，如果已建立关系，否则为空。

### <a name="remarks"></a>备注

可以调用此方法来检索指向父动画对象 （容器） 的指针。

##  <a name="getvalue"></a>  CAnimationVariable::GetValue

返回当前动画变量的值。

```
HRESULT GetValue(DOUBLE& dblValue);
HRESULT GetValue(INT32& nValue);
```

### <a name="parameters"></a>参数

*dblValue*<br/>
动画变量的当前值。

*n 值*<br/>
动画变量的当前值。

### <a name="return-value"></a>返回值

如果值已获取的成功，或尚未创建基础动画变量，则为 S_OK。 否则为 HRESULT 错误代码。

### <a name="remarks"></a>备注

可以调用此方法来检索当前动画变量的值。 如果尚未创建基础 COM 对象，dblValue 将包含默认值，该函数返回时。

##  <a name="getvariable"></a>  CAnimationVariable::GetVariable

返回指向 IUIAnimationVariable COM 对象的指针。

```
IUIAnimationVariable* GetVariable();
```

### <a name="return-value"></a>返回值

指向 IUIAnimationVariable COM 对象或如果动画变量未创建，或无法创建，则为 NULL 的有效指针。

### <a name="remarks"></a>备注

使用此函数来访问基础 IUIAnimationVariable COM 对象并根据需要直接调用其方法。

##  <a name="m_bautodestroytransitions"></a>  CAnimationVariable::m_bAutodestroyTransitions

指定是否应删除相关的转换对象。

```
BOOL m_bAutodestroyTransitions;
```

### <a name="remarks"></a>备注

要从中转换的内部列表时，请设置此值设置为 true 以强制删除转换对象。 如果此值为 FALSE 则应通过调用应用程序删除转换。 已安排动画，始终会清除的转换列表。 默认值是 FALSE。

##  <a name="m_dbldefaultvalue"></a>  CAnimationVariable::m_dblDefaultValue

指定默认值传播到 IUIAnimationVariable。

```
DOUBLE m_dblDefaultValue;
```

##  <a name="m_lsttransitions"></a>  CAnimationVariable::m_lstTransitions

包含转换进行动画处理此动画变量的列表。

```
CObList m_lstTransitions;
```

##  <a name="m_pparentobject"></a>  CAnimationVariable::m_pParentObject

指向一个封装此动画变量的动画对象的指针。

```
CAnimationBaseObject* m_pParentObject;
```

##  <a name="m_variable"></a>  CAnimationVariable::m_variable

存储指向 IUIAnimationVariable COM 对象的指针。 如果尚未，创建 COM 对象或创建失败，则为 NULL。

```
ATL::CComPtr<IUIAnimationVariable> m_variable;
```

##  <a name="setdefaultvalue"></a>  CAnimationVariable::SetDefaultValue

设置默认值并释放 IUIAnimationVariable COM 对象。

```
void SetDefaultValue(DOUBLE dblDefaultValue);
```

### <a name="parameters"></a>参数

*dblDefaultValue*<br/>
指定新的默认值。

### <a name="remarks"></a>备注

使用此方法来重置默认值。 此方法释放内部 IUIAnimationVariable COM 对象，因此重新创建动画变量时，基础 COM 对象获取新的默认值。 如果不创建表示动画变量的 COM 对象，或如果变量没有动画效果，GetValue 将返回默认值。

##  <a name="setparentanimationobject"></a>  CAnimationVariable::SetParentAnimationObject

设置动画变量和动画对象之间的关系。

```
void SetParentAnimationObject(CAnimationBaseObject* pParentObject);
```

### <a name="parameters"></a>参数

*pParentObject*<br/>
指向一个动画对象，包含此变量的指针。

### <a name="remarks"></a>备注

在内部调用此方法来建立一个动画变量和封装该动画对象之间的一对一关系。

## <a name="see-also"></a>请参阅

[类](../../mfc/reference/mfc-classes.md)
