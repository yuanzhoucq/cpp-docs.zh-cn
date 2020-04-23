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
ms.openlocfilehash: b53a1338566a329fbdf5b91c41d0411a529afe8d
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/22/2020
ms.locfileid: "81755070"
---
# <a name="canimationvariable-class"></a>CAnimationVariable 类

表示动画变量。

## <a name="syntax"></a>语法

```
class CAnimationVariable;
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[动画变量：：动画变量](#canimationvariable)|构造动画变量对象。|
|[动画变量：：~C动画变量](#_dtorcanimationvariable)|析构函数。 在销毁 CAnimation 变量对象时调用。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[动画变量：：添加转换](#addtransition)|添加转换。|
|[动画变量：：应用转换](#applytransitions)|将从内部列表转换为情节提要。|
|[动画变量：：清除转换](#cleartransitions)|清除转换。|
|[动画变量：：创建](#create)|创建基础动画变量 COM 对象。|
|[动画变量：：创建转换](#createtransitions)|创建要应用于此动画变量的所有转换。|
|[动画变量：：启用整数值更改事件](#enableintegervaluechangedevent)|启用或禁用整数值更改事件。|
|[动画变量：：启用价值更改事件](#enablevaluechangedevent)|启用或禁用"值更改"事件。|
|[动画变量：获取默认值](#getdefaultvalue)|返回默认值。|
|[动画变量：：获取父动画对象](#getparentanimationobject)|返回父动画对象。|
|[动画变量：获取价值](#getvalue)|已重载。 返回动画变量的当前值。|
|[动画变量：获取变量](#getvariable)|返回指向 IUI动画可变 COM 对象的指针。|
|[动画变量：：设置默认值](#setdefaultvalue)|设置默认值并释放 IUI动画可变 COM 对象。|

### <a name="protected-methods"></a>受保护的方法

|名称|说明|
|----------|-----------------|
|[动画变量：：设置父动画对象](#setparentanimationobject)|设置动画变量和动画对象之间的关系。|

### <a name="public-data-members"></a>公共数据成员

|名称|说明|
|----------|-----------------|
|[动画变量：：m_bAutodestroyTransitions](#m_bautodestroytransitions)|指定是否应删除相关的过渡对象。|

### <a name="protected-data-members"></a>受保护的数据成员

|名称|说明|
|----------|-----------------|
|[动画变量：：m_dblDefaultValue](#m_dbldefaultvalue)|指定将传播为 IUI动画变量的默认值。|
|[动画变量：：m_lstTransitions](#m_lsttransitions)|包含为此动画变量设置动画的过渡列表。|
|[C动画变量：：m_pParentObject](#m_pparentobject)|指向封装此动画变量的动画对象的指针。|
|[动画变量：：m_variable](#m_variable)|存储指向 IUI动画可变 COM 对象的指针。 如果尚未创建 COM 对象，或者创建失败，则为 NULL。|

## <a name="remarks"></a>备注

C动画变量类封装 IUI动画变量 COM 对象。 它还包含要应用于情节提要中的动画变量的过渡列表。 CAnimationVariable 对象嵌入到动画对象中，可以在应用程序中表示动画值、点、大小、颜色和矩形。

## <a name="inheritance-hierarchy"></a>继承层次结构

`CAnimationVariable`

## <a name="requirements"></a>要求

**标头：** afxanimationcontroller.h

## <a name="canimationvariablecanimationvariable"></a><a name="_dtorcanimationvariable"></a>动画变量：：~C动画变量

析构函数。 在销毁 CAnimation 变量对象时调用。

```
virtual ~CAnimationVariable();
```

## <a name="canimationvariableaddtransition"></a><a name="addtransition"></a>动画变量：：添加转换

添加转换。

```cpp
void AddTransition(CBaseTransition* pTransition);
```

### <a name="parameters"></a>参数

*p 转换*<br/>
指向要添加的过渡的指针。

### <a name="remarks"></a>备注

调用此方法是为了向要应用于动画变量的过渡的内部列表添加过渡。 计划动画时，应清除此列表。

## <a name="canimationvariableapplytransitions"></a><a name="applytransitions"></a>动画变量：：应用转换

将从内部列表转换为情节提要。

```cpp
void ApplyTransitions(
    CAnimationController* pController,
    IUIAnimationStoryboard* pStoryboard,
    BOOL bDependOnKeyframes);
```

### <a name="parameters"></a>参数

*pController*<br/>
指向父动画控制器的指针。

*板*<br/>
指向情节提要的指针。

*bDependon 关键帧*<br/>
TRUE，如果此方法应添加依赖于关键帧的过渡。

### <a name="remarks"></a>备注

此方法将从内部列表转换为情节提要。 它多次从顶级代码调用以添加不依赖于关键帧的过渡，并添加依赖于关键帧的过渡。 如果尚未创建基础动画变量 COM 对象，则此方法将在此阶段创建它。

## <a name="canimationvariablecanimationvariable"></a><a name="canimationvariable"></a>动画变量：：动画变量

构造动画变量对象。

```
CAnimationVariable(DOUBLE dblDefaultValue = 0.0);
```

### <a name="parameters"></a>参数

*dblDefault值*<br/>
指定默认值。

### <a name="remarks"></a>备注

构造动画变量对象并设置其默认值。 当变量未进行动画处理或无法进行动画处理时，将使用默认值。

## <a name="canimationvariablecleartransitions"></a><a name="cleartransitions"></a>动画变量：：清除转换

清除转换。

```cpp
void ClearTransitions(BOOL bAutodestroy);
```

### <a name="parameters"></a>参数

*b 自动销毁*<br/>
指定此方法是否应删除过渡对象。

### <a name="remarks"></a>备注

此方法从内部转换列表中删除所有转换。 如果 bAuto销毁为 TRUE，或者m_bAutodestroyTransitions为 TRUE，则删除转换。 否则，调用方应取消分配转换对象。

## <a name="canimationvariablecreate"></a><a name="create"></a>动画变量：：创建

创建基础动画变量 COM 对象。

```
virtual BOOL Create(IUIAnimationManager* pManager);
```

### <a name="parameters"></a>参数

*p经理*<br/>
指向动画管理器的指针。

### <a name="return-value"></a>返回值

如果动画变量已成功创建，则为 TRUE;如果动画变量已成功创建，则为 TRUE。否则 FALSE。

### <a name="remarks"></a>备注

此方法创建基础动画变量 COM 对象并设置其默认值。

## <a name="canimationvariablecreatetransitions"></a><a name="createtransitions"></a>动画变量：：创建转换

创建要应用于此动画变量的所有转换。

```
BOOL CreateTransitions(
    IUIAnimationTransitionLibrary* pLibrary,
    IUIAnimationTransitionFactory* \*not used*\);
```

### <a name="parameters"></a>参数

*p库*<br/>
指向[IUIAnimation 转换库接口](/windows/win32/api/uianimation/nn-uianimation-iuianimationtransitionlibrary)的指针，该接口定义标准转换库。

### <a name="return-value"></a>返回值

如果成功创建转换，则为 TRUE;否则 FALSE。

### <a name="remarks"></a>备注

当框架需要创建已添加到变量的内部转换列表中的转换时，框架会调用此方法。

## <a name="canimationvariableenableintegervaluechangedevent"></a><a name="enableintegervaluechangedevent"></a>动画变量：：启用整数值更改事件

启用或禁用整数值更改事件。

```cpp
void EnableIntegerValueChangedEvent (
    CAnimationController* pController,
    BOOL bEnable);
```

### <a name="parameters"></a>参数

*pController*<br/>
指向父控制器的指针。

*b 启用*<br/>
TRUE - 启用事件，FALSE - 禁用事件。

### <a name="remarks"></a>备注

启用 Value"更改"事件后，框架将调用虚拟方法 C动画控制器：：在动画中值已更改。 您需要在从 CAnimationController 派生的类中重写它，以便处理此事件。 每次更改动画变量的整数值时，都会调用此方法。

## <a name="canimationvariableenablevaluechangedevent"></a><a name="enablevaluechangedevent"></a>动画变量：：启用价值更改事件

启用或禁用"值更改"事件。

```cpp
void EnableValueChangedEvent (
    CAnimationController* pController,
    BOOL bEnable);
```

### <a name="parameters"></a>参数

*pController*<br/>
指向父控制器的指针。

*b 启用*<br/>
TRUE - 启用事件，FALSE - 禁用事件。

### <a name="remarks"></a>备注

启用 Value"更改"事件后，框架将调用虚拟方法 C动画控制器：：打开动画值。 您需要在从 CAnimationController 派生的类中重写它，以便处理此事件。 每次更改动画变量的值时，都会调用此方法。

## <a name="canimationvariablegetdefaultvalue"></a><a name="getdefaultvalue"></a>动画变量：获取默认值

返回默认值。

```
DOUBLE GetDefaultValue() const;
```

### <a name="return-value"></a>返回值

默认值。

### <a name="remarks"></a>备注

使用此函数获取动画变量的默认值。 默认值可以在构造函数中设置，也可以通过 SetDefaultValue 方法设置。

## <a name="canimationvariablegetparentanimationobject"></a><a name="getparentanimationobject"></a>动画变量：：获取父动画对象

返回父动画对象。

```
CAnimationBaseObject* GetParentAnimationObject();
```

### <a name="return-value"></a>返回值

指向父动画对象的指针（如果已建立关系，则为 NULL）。

### <a name="remarks"></a>备注

可以调用此方法来检索指向父动画对象（容器）的指针。

## <a name="canimationvariablegetvalue"></a><a name="getvalue"></a>动画变量：获取价值

返回动画变量的当前值。

```
HRESULT GetValue(DOUBLE& dblValue);
HRESULT GetValue(INT32& nValue);
```

### <a name="parameters"></a>参数

*dblValue*<br/>
动画变量的当前值。

*n值*<br/>
动画变量的当前值。

### <a name="return-value"></a>返回值

S_OK如果该值成功获得，或者尚未创建基础动画变量。 否则，HRESULT 错误代码。

### <a name="remarks"></a>备注

可以调用此方法来检索动画变量的当前值。 如果未创建基础 COM 对象，则当函数返回时，dblValue 将包含默认值。

## <a name="canimationvariablegetvariable"></a><a name="getvariable"></a>动画变量：获取变量

返回指向 IUI动画可变 COM 对象的指针。

```
IUIAnimationVariable* GetVariable();
```

### <a name="return-value"></a>返回值

指向 IUIAnimationvariable COM 对象的有效指针，或 NULL（如果未创建动画变量或无法创建）。

### <a name="remarks"></a>备注

使用此函数可以访问基础 IUI动画可变 COM 对象，并在需要时直接调用其方法。

## <a name="canimationvariablem_bautodestroytransitions"></a><a name="m_bautodestroytransitions"></a>动画变量：：m_bAutodestroyTransitions

指定是否应删除相关的过渡对象。

```
BOOL m_bAutodestroyTransitions;
```

### <a name="remarks"></a>备注

将此值设置为 TRUE，以强制删除过渡对象，当它们从内部转换列表中删除时。 如果此值为 FALSE，则应通过调用应用程序删除转换。 计划动画后，始终清除转换列表。 默认值是 FALSE。

## <a name="canimationvariablem_dbldefaultvalue"></a><a name="m_dbldefaultvalue"></a>动画变量：：m_dblDefaultValue

指定将传播为 IUI动画变量的默认值。

```
DOUBLE m_dblDefaultValue;
```

## <a name="canimationvariablem_lsttransitions"></a><a name="m_lsttransitions"></a>动画变量：：m_lstTransitions

包含为此动画变量设置动画的过渡列表。

```
CObList m_lstTransitions;
```

## <a name="canimationvariablem_pparentobject"></a><a name="m_pparentobject"></a>C动画变量：：m_pParentObject

指向封装此动画变量的动画对象的指针。

```
CAnimationBaseObject* m_pParentObject;
```

## <a name="canimationvariablem_variable"></a><a name="m_variable"></a>动画变量：：m_variable

存储指向 IUI动画可变 COM 对象的指针。 如果尚未创建 COM 对象，或者创建失败，则为 NULL。

```
ATL::CComPtr<IUIAnimationVariable> m_variable;
```

## <a name="canimationvariablesetdefaultvalue"></a><a name="setdefaultvalue"></a>动画变量：：设置默认值

设置默认值并释放 IUI动画可变 COM 对象。

```cpp
void SetDefaultValue(DOUBLE dblDefaultValue);
```

### <a name="parameters"></a>参数

*dblDefault值*<br/>
指定新的默认值。

### <a name="remarks"></a>备注

使用此方法重置默认值。 此方法释放内部 IUI动画可变 COM 对象，因此在重新创建动画变量时，基础 COM 对象获取新的默认值。 如果未创建表示动画变量的 COM 对象，或者该变量尚未进行动画处理，则 GetValue 会返回默认值。

## <a name="canimationvariablesetparentanimationobject"></a><a name="setparentanimationobject"></a>动画变量：：设置父动画对象

设置动画变量和动画对象之间的关系。

```cpp
void SetParentAnimationObject(CAnimationBaseObject* pParentObject);
```

### <a name="parameters"></a>参数

*p 父对象*<br/>
指向包含此变量的动画对象的指针。

### <a name="remarks"></a>备注

此方法在内部调用，以建立动画变量和封装它的动画对象之间的一对一关系。

## <a name="see-also"></a>请参阅

[类](../../mfc/reference/mfc-classes.md)
