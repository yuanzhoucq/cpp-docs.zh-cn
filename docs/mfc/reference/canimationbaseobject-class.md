---
title: CAnimationBaseObject 类
ms.date: 03/27/2019
f1_keywords:
- CAnimationBaseObject
- AFXANIMATIONCONTROLLER/CAnimationBaseObject
- AFXANIMATIONCONTROLLER/CAnimationBaseObject::CAnimationBaseObject
- AFXANIMATIONCONTROLLER/CAnimationBaseObject::ApplyTransitions
- AFXANIMATIONCONTROLLER/CAnimationBaseObject::ClearTransitions
- AFXANIMATIONCONTROLLER/CAnimationBaseObject::ContainsVariable
- AFXANIMATIONCONTROLLER/CAnimationBaseObject::CreateTransitions
- AFXANIMATIONCONTROLLER/CAnimationBaseObject::DetachFromController
- AFXANIMATIONCONTROLLER/CAnimationBaseObject::EnableIntegerValueChangedEvent
- AFXANIMATIONCONTROLLER/CAnimationBaseObject::EnableValueChangedEvent
- AFXANIMATIONCONTROLLER/CAnimationBaseObject::GetAutodestroyTransitions
- AFXANIMATIONCONTROLLER/CAnimationBaseObject::GetGroupID
- AFXANIMATIONCONTROLLER/CAnimationBaseObject::GetObjectID
- AFXANIMATIONCONTROLLER/CAnimationBaseObject::GetUserData
- AFXANIMATIONCONTROLLER/CAnimationBaseObject::SetAutodestroyTransitions
- AFXANIMATIONCONTROLLER/CAnimationBaseObject::SetID
- AFXANIMATIONCONTROLLER/CAnimationBaseObject::SetUserData
- AFXANIMATIONCONTROLLER/CAnimationBaseObject::GetAnimationVariableList
- AFXANIMATIONCONTROLLER/CAnimationBaseObject::SetParentAnimationObjects
- AFXANIMATIONCONTROLLER/CAnimationBaseObject::m_bAutodestroyTransitions
- AFXANIMATIONCONTROLLER/CAnimationBaseObject::m_dwUserData
- AFXANIMATIONCONTROLLER/CAnimationBaseObject::m_nGroupID
- AFXANIMATIONCONTROLLER/CAnimationBaseObject::m_nObjectID
- AFXANIMATIONCONTROLLER/CAnimationBaseObject::m_pParentController
helpviewer_keywords:
- CAnimationBaseObject [MFC], CAnimationBaseObject
- CAnimationBaseObject [MFC], ApplyTransitions
- CAnimationBaseObject [MFC], ClearTransitions
- CAnimationBaseObject [MFC], ContainsVariable
- CAnimationBaseObject [MFC], CreateTransitions
- CAnimationBaseObject [MFC], DetachFromController
- CAnimationBaseObject [MFC], EnableIntegerValueChangedEvent
- CAnimationBaseObject [MFC], EnableValueChangedEvent
- CAnimationBaseObject [MFC], GetAutodestroyTransitions
- CAnimationBaseObject [MFC], GetGroupID
- CAnimationBaseObject [MFC], GetObjectID
- CAnimationBaseObject [MFC], GetUserData
- CAnimationBaseObject [MFC], SetAutodestroyTransitions
- CAnimationBaseObject [MFC], SetID
- CAnimationBaseObject [MFC], SetUserData
- CAnimationBaseObject [MFC], GetAnimationVariableList
- CAnimationBaseObject [MFC], SetParentAnimationObjects
- CAnimationBaseObject [MFC], m_bAutodestroyTransitions
- CAnimationBaseObject [MFC], m_dwUserData
- CAnimationBaseObject [MFC], m_nGroupID
- CAnimationBaseObject [MFC], m_nObjectID
- CAnimationBaseObject [MFC], m_pParentController
ms.assetid: 76b25917-940e-4eba-940f-31d270702603
ms.openlocfilehash: 9581ea142c6f87ae12665374a483abc00763ad97
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371122"
---
# <a name="canimationbaseobject-class"></a>CAnimationBaseObject 类

所有动画对象的基类。

## <a name="syntax"></a>语法

```
class CAnimationBaseObject : public CObject;
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[动画基础对象：：动画基对象](#canimationbaseobject)|已重载。 构造动画对象。|
|[动画基对象：：_C动画基对象](#_dtorcanimationbaseobject)|析构函数。 销毁动画对象时调用。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[动画基础对象：：应用转换](#applytransitions)|使用封装的动画变量将过渡添加到情节提要。|
|[动画基础对象：：清除转换](#cleartransitions)|删除所有相关转换。|
|[动画基础对象：：包含变量](#containsvariable)|确定动画对象是否包含特定的动画变量。|
|[动画基础对象：：创建转换](#createtransitions)|创建与动画对象关联的过渡。|
|[动画基础对象：:D从控制器](#detachfromcontroller)|从父动画控制器分离动画对象。|
|[动画基础对象：：启用整数值更改事件](#enableintegervaluechangedevent)|设置整数值已更改事件处理程序。|
|[动画基础对象：：启用值更改事件](#enablevaluechangedevent)|设置值更改的事件处理程序。|
|[动画基础对象：：获取自动销毁转换](#getautodestroytransitions)|告诉相关转换是否自动销毁。|
|[动画基础对象：获取群体 ID](#getgroupid)|返回当前组 ID。|
|[动画基础对象：：获取对象ID](#getobjectid)|返回当前对象 ID。|
|[动画基础对象：获取用户数据](#getuserdata)|返回用户定义的数据。|
|[动画基础对象：：设置自动销毁转换](#setautodestroytransitions)|设置标志以自动销毁过渡。|
|[动画基础对象：：SetID](#setid)|设置新指示。|
|[动画基础对象：：设置用户数据](#setuserdata)|设置用户定义的数据。|

### <a name="protected-methods"></a>受保护的方法

|名称|说明|
|----------|-----------------|
|[动画基础对象：：获取动画变量列表](#getanimationvariablelist)|收集指向包含的动画变量的指针。|
|[动画基础对象：：设置父动画对象](#setparentanimationobjects)|建立动画对象中包含的动画变量与其容器之间的关系。|

### <a name="protected-data-members"></a>受保护的数据成员

|名称|说明|
|----------|-----------------|
|[动画基础对象：：m_bAutodestroyTransitions](#m_bautodestroytransitions)|指定是否应自动销毁相关转换。|
|[动画基础对象：：m_dwUserData](#m_dwuserdata)|存储用户定义的数据。|
|[动画基础对象：：m_nGroupID](#m_ngroupid)|指定动画对象的组 ID。|
|[动画基础对象：：m_nObjectID](#m_nobjectid)|指定动画对象的对象 ID。|
|[动画基础对象：：m_pParentController](#m_pparentcontroller)|指向父动画控制器的指针。|

## <a name="remarks"></a>备注

此类为所有动画对象实现基本方法。 动画对象可以表示应用程序中的值、点、大小、矩形或颜色，以及任何自定义实体。 动画对象存储在动画组中（请参阅 C动画组）。 每个组可以单独进行动画处理，也可以被视为情节提要的模拟。 动画对象封装一个或多个动画变量（请参阅 CAnvariable），具体取决于其逻辑表示形式。 例如，CAnimationRect 包含四个动画变量 - 矩形每侧一个变量。 每个动画对象类公开重载的 AddTransition 方法，该方法应用于将过渡应用于封装的动画变量。 动画对象可以通过对象 ID（可选）和组 ID 标识。 要放置动画对象以更正组，需要组 ID，但如果未指定组 ID，则对象将放置在 ID 0 的默认组中。 如果使用不同的 GroupID 调用 SetID，动画对象将移动到另一个组（如有必要，将创建新组）。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

`CAnimationBaseObject`

## <a name="requirements"></a>要求

**标头：** afxanimationcontroller.h

## <a name="canimationbaseobjectcanimationbaseobject"></a><a name="_dtorcanimationbaseobject"></a>动画基对象：：_C动画基对象

析构函数。 销毁动画对象时调用。

```
virtual ~CAnimationBaseObject();
```

## <a name="canimationbaseobjectapplytransitions"></a><a name="applytransitions"></a>动画基础对象：：应用转换

使用封装的动画变量将过渡添加到情节提要。

```
virtual BOOL ApplyTransitions(
    IUIAnimationStoryboard* pStoryboard,
    BOOL bDependOnKeyframes);
```

### <a name="parameters"></a>参数

*板*<br/>
指向情节提要的指针。

*bDependon 关键帧*<br/>
当 FALSE 时，此方法仅添加不依赖于关键帧的转换。

### <a name="return-value"></a>返回值

如果成功添加了转换，则为 TRUE。

### <a name="remarks"></a>备注

将使用 AddTransition（派生类中重载方法）添加到情节提要的相关转换。

## <a name="canimationbaseobjectcanimationbaseobject"></a><a name="canimationbaseobject"></a>动画基础对象：：动画基对象

构造动画对象。

```
CAnimationBaseObject();

CAnimationBaseObject(
    UINT32 nGroupID,
    UINT32 nObjectID = (UINT32)-1,
    DWORD dwUserData = 0);
```

### <a name="parameters"></a>参数

*n集团ID*<br/>
指定组 ID。

*nObjectID*<br/>
指定对象 ID。

*dwUserData*<br/>
用户定义的数据，这些数据可以与动画对象关联，并在运行时稍后检索。

### <a name="remarks"></a>备注

构造动画对象并分配默认对象 ID （0） 和组 ID （0）。

## <a name="canimationbaseobjectcleartransitions"></a><a name="cleartransitions"></a>动画基础对象：：清除转换

删除所有相关转换。

```
virtual void ClearTransitions(BOOL bAutodestroy);
```

### <a name="parameters"></a>参数

*b 自动销毁*<br/>
指定是自动销毁过渡对象，还是仅将其从相关列表中删除。

### <a name="remarks"></a>备注

删除所有相关转换，并在 bAuto销毁或m_bAutodestroyTransitions标志为 TRUE 时销毁它们。 仅当转换未在堆栈上分配时，才应自动销毁这些转换。 如果上述标志为 FALSE，则只会从相关转换的内部列表中删除转换。

## <a name="canimationbaseobjectcontainsvariable"></a><a name="containsvariable"></a>动画基础对象：：包含变量

确定动画对象是否包含特定的动画变量。

```
virtual BOOL ContainsVariable(IUIAnimationVariable* pVariable);
```

### <a name="parameters"></a>参数

*pvariable*<br/>
指向动画变量的指针。

### <a name="return-value"></a>返回值

如果动画变量包含在动画对象中，则为 TRUE;如果动画变量包含在动画对象中，则为 TRUE。否则 FALSE。

### <a name="remarks"></a>备注

此方法可用于确定 pVariable 指定的动画变量是否包含在动画对象中。 动画对象（根据其类型）可能包含多个动画变量。 例如，CAnimationColor 包含三个变量，每个颜色组件（红色、绿色和蓝色）一个。 当动画变量的值发生更改时，Windows 动画 API 将发送 Value"更改"或"整数值更改"事件（如果启用），此事件的参数是指向动画变量的接口 IUIAnimationvariable 的指针。 此方法有助于从指针获取指向包含的 COM 对象的动画指针。

## <a name="canimationbaseobjectcreatetransitions"></a><a name="createtransitions"></a>动画基础对象：：创建转换

创建与动画对象关联的过渡。

```
BOOL CreateTransitions();
```

### <a name="return-value"></a>返回值

如果成功创建转换，则为 TRUE;否则 FALSE。

### <a name="remarks"></a>备注

循环在派生动画对象中封装的动画变量列表，并创建与每个动画变量关联的过渡。

## <a name="canimationbaseobjectdetachfromcontroller"></a><a name="detachfromcontroller"></a>动画基础对象：:D从控制器

从父动画控制器分离动画对象。

```
void DetachFromController();
```

### <a name="remarks"></a>备注

此方法在内部使用。

## <a name="canimationbaseobjectenableintegervaluechangedevent"></a><a name="enableintegervaluechangedevent"></a>动画基础对象：：启用整数值更改事件

设置整数值已更改事件处理程序。

```
virtual void EnableIntegerValueChangedEvent(
    CAnimationController* pController,
    BOOL bEnable);
```

### <a name="parameters"></a>参数

*pController*<br/>
指向父控制器的指针。

*b 启用*<br/>
指定是启用还是禁用整数值更改事件。

### <a name="remarks"></a>备注

如果启用了整数值更改事件处理程序，则可以在 CAnimationController：：onAnimationIntegerValue"更改"方法中处理此事件，该方法应在 CAnimationController 派生类中重写。 每次更改动画整数值时，都会调用此方法。

## <a name="canimationbaseobjectenablevaluechangedevent"></a><a name="enablevaluechangedevent"></a>动画基础对象：：启用值更改事件

设置值更改的事件处理程序。

```
virtual void EnableValueChangedEvent(
    CAnimationController* pController,
    BOOL bEnable);
```

### <a name="parameters"></a>参数

*pController*<br/>
指向父控制器的指针。

*b 启用*<br/>
指定是启用还是禁用"值更改"事件。

### <a name="remarks"></a>备注

如果启用了"值更改"事件处理程序，则可以在 CAnimationController：：onAnimationValue 更改方法中处理此事件，该方法应在 CAnimationController 派生类中重写。 每次动画值更改时，都会调用此方法。

## <a name="canimationbaseobjectgetanimationvariablelist"></a><a name="getanimationvariablelist"></a>动画基础对象：：获取动画变量列表

收集指向包含的动画变量的指针。

```
virtual void GetAnimationVariableList(
    CList<CAnimationVariable*,
    CAnimationVariable*>& list) = 0;
```

### <a name="parameters"></a>参数

*list*<br/>
必须填充动画对象中包含的动画变量的列表。

### <a name="remarks"></a>备注

必须在派生类中重写此纯虚拟方法。 动画对象（根据其类型）包含一个或多个动画变量。 例如，CAnimationPoint 包含两个变量，分别用于 X 和 Y 坐标。 基本类 CAnimationBaseObject 实现一些泛型方法，这些方法作用于动画变量列表：应用转换、清除转换、启用价值更改事件、启用 IntegerValue 更改事件。 这些方法称为 GetAnimationvariableList，它填充在派生类中，其中包含特定动画对象中包含的实际动画变量，然后循环访问列表并执行必要的操作。 如果创建自定义动画对象，则必须添加到*列出*该对象中包含的所有动画变量。

## <a name="canimationbaseobjectgetautodestroytransitions"></a><a name="getautodestroytransitions"></a>动画基础对象：：获取自动销毁转换

告诉相关转换是否自动销毁。

```
BOOL GetAutodestroyTransitions() const;
```

### <a name="return-value"></a>返回值

如果为 TRUE，则相关转换将自动销毁;如果为 TRUE，则会自动销毁相关转换。如果 FALSE，则转换对象应通过调用应用程序进行处理。

### <a name="remarks"></a>备注

默认情况下，此标志为 TRUE。 仅当在堆栈上分配过渡和/或转换应由调用应用程序处理时，才设置此标志。

## <a name="canimationbaseobjectgetgroupid"></a><a name="getgroupid"></a>动画基础对象：获取群体 ID

返回当前组 ID。

```
UINT32 GetGroupID() const;
```

### <a name="return-value"></a>返回值

当前组 ID。

### <a name="remarks"></a>备注

使用此方法检索组 ID。 如果组 ID 未在构造函数中或 SetID 中显式设置，则为 0。

## <a name="canimationbaseobjectgetobjectid"></a><a name="getobjectid"></a>动画基础对象：：获取对象ID

返回当前对象 ID。

```
UINT32 GetObjectID() const;
```

### <a name="return-value"></a>返回值

当前对象 ID。

### <a name="remarks"></a>备注

使用此方法检索对象 ID。 如果对象 ID 未在构造函数中或 SetID 中显式设置，则为 0。

## <a name="canimationbaseobjectgetuserdata"></a><a name="getuserdata"></a>动画基础对象：获取用户数据

返回用户定义的数据。

```
DWORD GetUserData() const;
```

### <a name="return-value"></a>返回值

自定义数据的值。

### <a name="remarks"></a>备注

调用此方法以在运行时检索自定义数据。 如果在构造函数或使用 SetUserData 中显式初始化该值，则返回的值将为 0。

## <a name="canimationbaseobjectm_bautodestroytransitions"></a><a name="m_bautodestroytransitions"></a>动画基础对象：：m_bAutodestroyTransitions

指定是否应自动销毁相关转换。

```
BOOL m_bAutodestroyTransitions;
```

## <a name="canimationbaseobjectm_dwuserdata"></a><a name="m_dwuserdata"></a>动画基础对象：：m_dwUserData

存储用户定义的数据。

```
DWORD m_dwUserData;
```

## <a name="canimationbaseobjectm_ngroupid"></a><a name="m_ngroupid"></a>动画基础对象：：m_nGroupID

指定动画对象的组 ID。

```
UINT32 m_nGroupID;
```

## <a name="canimationbaseobjectm_nobjectid"></a><a name="m_nobjectid"></a>动画基础对象：：m_nObjectID

指定动画对象的对象 ID。

```
UINT32 m_nObjectID;
```

## <a name="canimationbaseobjectm_pparentcontroller"></a><a name="m_pparentcontroller"></a>动画基础对象：：m_pParentController

指向父动画控制器的指针。

```
CAnimationController* m_pParentController;
```

## <a name="canimationbaseobjectsetautodestroytransitions"></a><a name="setautodestroytransitions"></a>动画基础对象：：设置自动销毁转换

设置标志以自动销毁过渡。

```
void SetAutodestroyTransitions(BOOL bValue);
```

### <a name="parameters"></a>参数

*bValue*<br/>
指定自动销毁标志。

### <a name="remarks"></a>备注

仅当使用运算符 new 分配过渡对象时，才设置此标志。 如果由于某种原因在堆栈上分配过渡对象，则自动销毁标志应为 FALSE。 默认情况下，此标志为 TRUE。

## <a name="canimationbaseobjectsetid"></a><a name="setid"></a>动画基础对象：：SetID

设置新指示。

```
void SetID(
    UINT32 nObjectID,
    UINT32 nGroupID = 0);
```

### <a name="parameters"></a>参数

*nObjectID*<br/>
指定新的对象 ID。

*n集团ID*<br/>
指定新的组 ID。

### <a name="remarks"></a>备注

允许您更改对象 ID 和组 ID。 如果新的组 ID 与当前 ID 不同，则动画对象将移动到另一个组（如有必要，将创建新组）。

## <a name="canimationbaseobjectsetparentanimationobjects"></a><a name="setparentanimationobjects"></a>动画基础对象：：设置父动画对象

建立动画对象中包含的动画变量与其容器之间的关系。

```
virtual void SetParentAnimationObjects();
```

### <a name="remarks"></a>备注

此帮助程序可用于在动画对象中包含的动画变量与其容器之间建立关系。 它循环在动画变量上，并将指向父动画对象的回指针设置到每个动画变量。 在当前实现中，实际关系在 CAnimationBaseObject：：apply 转换中建立，因此在调用 CAnimateGroup：：Animate 之前不会设置回指针。 当您处理事件并且需要从 CAnimationVariable 获取父动画对象时，了解关系可能会有所帮助。 使用"动画变量："获取父动画对象。

## <a name="canimationbaseobjectsetuserdata"></a><a name="setuserdata"></a>动画基础对象：：设置用户数据

设置用户定义的数据。

```
void SetUserData (DWORD dwUserData);
```

### <a name="parameters"></a>参数

*dwUserData*<br/>
指定自定义数据。

### <a name="remarks"></a>备注

使用此方法将自定义数据与动画对象相关联。 GetUserData 可在稍后运行时检索此数据。

## <a name="see-also"></a>另请参阅

[类](../../mfc/reference/mfc-classes.md)
