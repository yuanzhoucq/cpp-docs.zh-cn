---
title: CAnimationBaseObject 类 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2061f83efea3a4e46d24f0a8e63452486046fb80
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46439350"
---
# <a name="canimationbaseobject-class"></a>CAnimationBaseObject 类

所有动画对象的基类。

## <a name="syntax"></a>语法

```
class CAnimationBaseObject : public CObject;
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[CAnimationBaseObject::CAnimationBaseObject](#canimationbaseobject)|已重载。 构造一个动画对象。|
|[CAnimationBaseObject:: ~ CAnimationBaseObject](#canimationbaseobject__~canimationbaseobject)|析构函数。 当动画对象被销毁时调用。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CAnimationBaseObject::ApplyTransitions](#applytransitions)|添加到情节提要与封装的动画变量的转换。|
|[CAnimationBaseObject::ClearTransitions](#cleartransitions)|删除所有相关的转换。|
|[CAnimationBaseObject::ContainsVariable](#containsvariable)|确定动画对象是否包含特定的动画变量。|
|[CAnimationBaseObject::CreateTransitions](#createtransitions)|创建与动画对象关联的转换。|
|[CAnimationBaseObject::DetachFromController](#detachfromcontroller)|分离来自父动画控制器的动画对象。|
|[CAnimationBaseObject::EnableIntegerValueChangedEvent](#enableintegervaluechangedevent)|设置了整数值已更改事件处理程序。|
|[CAnimationBaseObject::EnableValueChangedEvent](#enablevaluechangedevent)|设置值发生更改时事件处理程序。|
|[CAnimationBaseObject::GetAutodestroyTransitions](#getautodestroytransitions)|指示是否自动销毁相关的转换。|
|[CAnimationBaseObject::GetGroupID](#getgroupid)|返回当前组 id。|
|[CAnimationBaseObject::GetObjectID](#getobjectid)|返回当前对象 id。|
|[CAnimationBaseObject::GetUserData](#getuserdata)|返回用户定义的数据。|
|[CAnimationBaseObject::SetAutodestroyTransitions](#setautodestroytransitions)|设置一个标志，用于自动销毁转换进行排序。|
|[CAnimationBaseObject::SetID](#setid)|设置新的 Id。|
|[CAnimationBaseObject::SetUserData](#setuserdata)|集用户定义数据。|

### <a name="protected-methods"></a>受保护的方法

|名称|描述|
|----------|-----------------|
|[CAnimationBaseObject::GetAnimationVariableList](#getanimationvariablelist)|收集到包含的动画变量的指针。|
|[CAnimationBaseObject::SetParentAnimationObjects](#setparentanimationobjects)|动画对象与它们的容器中包含的动画变量之间建立关系。|

### <a name="protected-data-members"></a>受保护的数据成员

|name|描述|
|----------|-----------------|
|[CAnimationBaseObject::m_bAutodestroyTransitions](#m_bautodestroytransitions)|指定是否应自动销毁相关的转换。|
|[CAnimationBaseObject::m_dwUserData](#m_dwuserdata)|存储用户定义数据。|
|[CAnimationBaseObject::m_nGroupID](#m_ngroupid)|指定动画对象的组 ID。|
|[CAnimationBaseObject::m_nObjectID](#m_nobjectid)|指定动画对象的对象 ID。|
|[CAnimationBaseObject::m_pParentController](#m_pparentcontroller)|指向父动画控制器的指针。|

## <a name="remarks"></a>备注

此类实现用于所有动画对象的基本方法。 动画对象可以表示值、 点、 大小、 矩形或应用程序，以及任何自定义实体中的颜色。 动画对象存储在动画组 （请参阅 CAnimationGroup）。 每个组可以单独显示动画，并且可以将其视为情节提要的相似之处。 动画对象封装一个或多个动画变量 （请参阅 CAnimationVariable），具体取决于其逻辑表示形式。 例如，CAnimationRect 包含四个动画变量的矩形的每一侧的一个变量。 每个动画对象类公开重载的下方法，用于将转换应用到封装的动画变量。 动画对象可以标识的对象 ID （可选） 和组 id。 组 ID 才可将动画对象到正确的组，但如果未指定组 ID，将对象放置在 id 为 0 的默认组中。 如果调用使用不同的 GroupID SetID，动画对象将移到另一个组 （如有必要，将创建新组）。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

`CAnimationBaseObject`

## <a name="requirements"></a>要求

**标头：** afxanimationcontroller.h

##  <a name="_dtorcanimationbaseobject"></a>  CAnimationBaseObject:: ~ CAnimationBaseObject

析构函数。 当动画对象被销毁时调用。

```
virtual ~CAnimationBaseObject();
```

##  <a name="applytransitions"></a>  CAnimationBaseObject::ApplyTransitions

添加到情节提要与封装的动画变量的转换。

```
virtual BOOL ApplyTransitions(
    IUIAnimationStoryboard* pStoryboard,
    BOOL bDependOnKeyframes);
```

### <a name="parameters"></a>参数

*pStoryboard*<br/>
指向情节提要的指针。

*bDependOnKeyframes*<br/>
为 false，则此方法将添加仅这些不依赖于关键帧的转换。

### <a name="return-value"></a>返回值

如果已成功添加转换，则为 TRUE。

### <a name="remarks"></a>备注

添加相关的转换，已添加与下 （在派生类中重载方法），到情节提要。

##  <a name="canimationbaseobject"></a>  CAnimationBaseObject::CAnimationBaseObject

构造一个动画对象。

```
CAnimationBaseObject();


CAnimationBaseObject(
    UINT32 nGroupID,
    UINT32 nObjectID = (UINT32)-1,
    DWORD dwUserData = 0);
```

### <a name="parameters"></a>参数

*nGroupID*<br/>
指定组 id。

*nObjectID*<br/>
指定对象 id。

*dwUserData*<br/>
用户定义数据，这可以与动画对象相关联并在运行时检索更高版本。

### <a name="remarks"></a>备注

构造动画对象，并分配默认对象 ID (0) 和组 ID (0)。

##  <a name="cleartransitions"></a>  CAnimationBaseObject::ClearTransitions

删除所有相关的转换。

```
virtual void ClearTransitions(BOOL bAutodestroy);
```

### <a name="parameters"></a>参数

*bAutodestroy*<br/>
指定是否自动销毁转换对象或只需从相关的列表中删除它们。

### <a name="remarks"></a>备注

删除所有相关的转换，并会销毁它们如果 bAutodestroy 或 m_bAutodestroyTransitions 标志为 TRUE。 仅当它们不能在堆栈上分配，应自动销毁转换。 如果以上标志为 FALSE，转换会只需从相关的转换的内部列表中删除。

##  <a name="containsvariable"></a>  CAnimationBaseObject::ContainsVariable

确定动画对象是否包含特定的动画变量。

```
virtual BOOL ContainsVariable(IUIAnimationVariable* pVariable);
```

### <a name="parameters"></a>参数

*pVariable*<br/>
指向动画变量的指针。

### <a name="return-value"></a>返回值

如果动画变量包含在动画对象; 则为 TRUE否则为 FALSE。

### <a name="remarks"></a>备注

此方法可以用于确定动画对象中是否包含指定 pVariable 动画变量。 动画对象，具体取决于它的类型，可能包含多个动画变量。 例如，CAnimationColor 包含三个变量，一个用于每个颜色组件 （红色、 绿色和蓝色）。 当动画变量的值已更改时，Windows 动画 API 发送 ValueChanged 或 IntegerValueChanged 事件 （如果启用），以及此事件的参数是指向接口 IUIAnimationVariable 动画变量的指针。 此方法有助于从指向包含 COM 对象的指针到动画中获取的指针。

##  <a name="createtransitions"></a>  CAnimationBaseObject::CreateTransitions

创建与动画对象关联的转换。

```
BOOL CreateTransitions();
```

### <a name="return-value"></a>返回值

如果转换成功，则已创建，则返回 TRUE否则为 FALSE。

### <a name="remarks"></a>备注

循环访问封装在派生的动画对象的动画变量的列表，并创建与每个动画变量相关联的转换。

##  <a name="detachfromcontroller"></a>  CAnimationBaseObject::DetachFromController

分离来自父动画控制器的动画对象。

```
void DetachFromController();
```

### <a name="remarks"></a>备注

在内部使用此方法。

##  <a name="enableintegervaluechangedevent"></a>  CAnimationBaseObject::EnableIntegerValueChangedEvent

设置了整数值已更改事件处理程序。

```
virtual void EnableIntegerValueChangedEvent(
    CAnimationController* pController,
    BOOL bEnable);
```

### <a name="parameters"></a>参数

*pController*<br/>
指向父控制器的指针。

*bEnable*<br/>
指定是否启用或禁用整数值已更改事件。

### <a name="remarks"></a>备注

如果启用了整数值已更改事件处理程序，可以处理在 CAnimationController::OnAnimationIntegerValueChanged 方法，应在 CAnimationController 派生类中重写此事件。 每次的动画的整数值已更改时，调用此方法。

##  <a name="enablevaluechangedevent"></a>  CAnimationBaseObject::EnableValueChangedEvent

设置值发生更改时事件处理程序。

```
virtual void EnableValueChangedEvent(
    CAnimationController* pController,
    BOOL bEnable);
```

### <a name="parameters"></a>参数

*pController*<br/>
指向父控制器的指针。

*bEnable*<br/>
指定是否启用或禁用值已更改事件。

### <a name="remarks"></a>备注

如果已启用的值更改事件处理程序，可以处理在 CAnimationController::OnAnimationValueChanged 方法，应在 CAnimationController 派生类中重写此事件。 每次的动画值已更改时，调用此方法。

##  <a name="getanimationvariablelist"></a>  CAnimationBaseObject::GetAnimationVariableList

收集到包含的动画变量的指针。

```
virtual void GetAnimationVariableList(
    CList<CAnimationVariable*,
    CAnimationVariable*>& lst) = 0;
```

### <a name="parameters"></a>参数

*lst*<br/>
必须填充动画对象中包含的动画变量的列表。

### <a name="remarks"></a>备注

这是必须在派生类中重写的纯虚方法。 动画对象，具体取决于它的类型，包含一个或多个动画变量。 例如，CAnimationPoint 包含 X 和 Y 坐标分别表示两个变量。 基类 CAnimationBaseObject 实现某些泛型方法，作用于动画变量的列表： ApplyTransitions、 ClearTransitions、 EnableValueChangedEvent、 EnableIntegerValueChangedEvent。 这些方法调用 GetAnimationVariableList，该类填充派生类中有特定动画对象中包含的实际动画变量，然后循环访问列表并执行必要的操作。 如果创建自定义动画对象，您必须向 lst 添加该对象中包含的所有动画变量。

##  <a name="getautodestroytransitions"></a>  CAnimationBaseObject::GetAutodestroyTransitions

指示是否自动销毁相关的转换。

```
BOOL GetAutodestroyTransitions() const;
```

### <a name="return-value"></a>返回值

如果为 TRUE，相关的转换销毁自动保存功能。如果为 FALSE，应由调用应用程序释放转换对象。

### <a name="remarks"></a>备注

默认情况下此标志为 TRUE。 仅分配在堆栈上的过渡和/或转换应释放通过调用应用程序时，才设置此标志。

##  <a name="getgroupid"></a>  CAnimationBaseObject::GetGroupID

返回当前组 id。

```
UINT32 GetGroupID() const;
```

### <a name="return-value"></a>返回值

当前组 id。

### <a name="remarks"></a>备注

使用此方法来检索组 id。 如果组 ID 尚未设置显式构造函数中或使用 SetID，的 0。

##  <a name="getobjectid"></a>  CAnimationBaseObject::GetObjectID

返回当前对象 id。

```
UINT32 GetObjectID() const;
```

### <a name="return-value"></a>返回值

当前对象 id。

### <a name="remarks"></a>备注

此方法用于检索对象 id。 如果对象 ID 尚未设置显式构造函数中或使用 SetID，的 0。

##  <a name="getuserdata"></a>  CAnimationBaseObject::GetUserData

返回用户定义的数据。

```
DWORD GetUserData() const;
```

### <a name="return-value"></a>返回值

自定义数据的值。

### <a name="remarks"></a>备注

调用此方法以检索在运行时的自定义数据。 如果它未显式初始化构造函数中或使用 SetUserData，返回的值将为 0。

##  <a name="m_bautodestroytransitions"></a>  CAnimationBaseObject::m_bAutodestroyTransitions

指定是否应自动销毁相关的转换。

```
BOOL m_bAutodestroyTransitions;
```

##  <a name="m_dwuserdata"></a>  CAnimationBaseObject::m_dwUserData

存储用户定义数据。

```
DWORD m_dwUserData;
```

##  <a name="m_ngroupid"></a>  CAnimationBaseObject::m_nGroupID

指定动画对象的组 ID。

```
UINT32 m_nGroupID;
```

##  <a name="m_nobjectid"></a>  CAnimationBaseObject::m_nObjectID

指定动画对象的对象 ID。

```
UINT32 m_nObjectID;
```

##  <a name="m_pparentcontroller"></a>  CAnimationBaseObject::m_pParentController

指向父动画控制器的指针。

```
CAnimationController* m_pParentController;
```

##  <a name="setautodestroytransitions"></a>  CAnimationBaseObject::SetAutodestroyTransitions

设置一个标志，用于自动销毁转换进行排序。

```
void SetAutodestroyTransitions(BOOL bValue);
```

### <a name="parameters"></a>参数

*其中 bValue*<br/>
指定自动销毁标志。

### <a name="remarks"></a>备注

设置此标志仅当分配使用 new 运算符的转换对象。 如果出于某种原因，在堆栈分配转换对象，自动销毁标志应为 FALSE。 默认情况下此标志为 TRUE。

##  <a name="setid"></a>  CAnimationBaseObject::SetID

设置新的 Id。

```
void SetID(
    UINT32 nObjectID,
    UINT32 nGroupID = 0);
```

### <a name="parameters"></a>参数

*nObjectID*<br/>
指定新的对象 id。

*nGroupID*<br/>
指定新的组 id。

### <a name="remarks"></a>备注

允许更改对象 ID 和组 id。 如果新的组 ID 不同于当前的 ID，动画对象移动到另一个组 （新的组将创建，如有必要）。

##  <a name="setparentanimationobjects"></a>  CAnimationBaseObject::SetParentAnimationObjects

动画对象与它们的容器中包含的动画变量之间建立关系。

```
virtual void SetParentAnimationObjects();
```

### <a name="remarks"></a>备注

这是一个帮助程序，可用于动画对象与它们的容器中包含的动画变量之间建立关系。 它循环的动画变量，并将返回的指针设置为父动画对象到每个动画变量。 在当前实现中的实际关系建立 CAnimationBaseObject::ApplyTransitions 中，因此反向指针未设置在您调用 CAnimationGroup::Animate 之前。 当您处理事件并需要获取父动画对象从 CAnimationVariable （使用 CAnimationVariable::GetParentAnimationObject），了解关系可能会有帮助。

##  <a name="setuserdata"></a>  CAnimationBaseObject::SetUserData

集用户定义数据。

```
void SetUserData (DWORD dwUserData);
```

### <a name="parameters"></a>参数

*dwUserData*<br/>
指定自定义数据。

### <a name="remarks"></a>备注

使用此方法将自定义数据与动画对象相关联。 此数据可能会更高版本在运行时通过检索 GetUserData。

## <a name="see-also"></a>请参阅

[类](../../mfc/reference/mfc-classes.md)
