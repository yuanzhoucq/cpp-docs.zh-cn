---
title: CAnimationGroup 类
ms.date: 11/04/2016
f1_keywords:
- CAnimationGroup
- AFXANIMATIONCONTROLLER/CAnimationGroup
- AFXANIMATIONCONTROLLER/CAnimationGroup::CAnimationGroup
- AFXANIMATIONCONTROLLER/CAnimationGroup::Animate
- AFXANIMATIONCONTROLLER/CAnimationGroup::ApplyTransitions
- AFXANIMATIONCONTROLLER/CAnimationGroup::FindAnimationObject
- AFXANIMATIONCONTROLLER/CAnimationGroup::GetGroupID
- AFXANIMATIONCONTROLLER/CAnimationGroup::RemoveKeyframes
- AFXANIMATIONCONTROLLER/CAnimationGroup::RemoveTransitions
- AFXANIMATIONCONTROLLER/CAnimationGroup::Schedule
- AFXANIMATIONCONTROLLER/CAnimationGroup::SetAutodestroyTransitions
- AFXANIMATIONCONTROLLER/CAnimationGroup::AddKeyframes
- AFXANIMATIONCONTROLLER/CAnimationGroup::AddTransitions
- AFXANIMATIONCONTROLLER/CAnimationGroup::CreateTransitions
- AFXANIMATIONCONTROLLER/CAnimationGroup::m_bAutoclearTransitions
- AFXANIMATIONCONTROLLER/CAnimationGroup::m_bAutodestroyAnimationObjects
- AFXANIMATIONCONTROLLER/CAnimationGroup::m_bAutodestroyKeyframes
- AFXANIMATIONCONTROLLER/CAnimationGroup::m_lstAnimationObjects
- AFXANIMATIONCONTROLLER/CAnimationGroup::m_lstKeyFrames
- AFXANIMATIONCONTROLLER/CAnimationGroup::m_pStoryboard
- AFXANIMATIONCONTROLLER/CAnimationGroup::m_nGroupID
- AFXANIMATIONCONTROLLER/CAnimationGroup::m_pParentController
helpviewer_keywords:
- CAnimationGroup [MFC], CAnimationGroup
- CAnimationGroup [MFC], Animate
- CAnimationGroup [MFC], ApplyTransitions
- CAnimationGroup [MFC], FindAnimationObject
- CAnimationGroup [MFC], GetGroupID
- CAnimationGroup [MFC], RemoveKeyframes
- CAnimationGroup [MFC], RemoveTransitions
- CAnimationGroup [MFC], Schedule
- CAnimationGroup [MFC], SetAutodestroyTransitions
- CAnimationGroup [MFC], AddKeyframes
- CAnimationGroup [MFC], AddTransitions
- CAnimationGroup [MFC], CreateTransitions
- CAnimationGroup [MFC], m_bAutoclearTransitions
- CAnimationGroup [MFC], m_bAutodestroyAnimationObjects
- CAnimationGroup [MFC], m_bAutodestroyKeyframes
- CAnimationGroup [MFC], m_lstAnimationObjects
- CAnimationGroup [MFC], m_lstKeyFrames
- CAnimationGroup [MFC], m_pStoryboard
- CAnimationGroup [MFC], m_nGroupID
- CAnimationGroup [MFC], m_pParentController
ms.assetid: 8bc18ceb-33a2-41d0-9731-71811adacab7
ms.openlocfilehash: b05de00697aa019382014402f7701a8341da5198
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50512913"
---
# <a name="canimationgroup-class"></a>CAnimationGroup 类

实现结合了动画情节提要、 动画对象和转换来定义动画的动画组。

## <a name="syntax"></a>语法

```
class CAnimationGroup;
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[CAnimationGroup::CAnimationGroup](#canimationgroup)|构造一个动画组。|
|[CAnimationGroup:: ~ CAnimationGroup](#canimationgroup__~canimationgroup)|析构函数。 当动画组被销毁时调用。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CAnimationGroup::Animate](#animate)|对组进行动画处理。|
|[CAnimationGroup::ApplyTransitions](#applytransitions)|适用于动画对象的转换。|
|[CAnimationGroup::FindAnimationObject](#findanimationobject)|查找包含指定的动画变量的动画对象。|
|[CAnimationGroup::GetGroupID](#getgroupid)|返回 GroupID。|
|[CAnimationGroup::RemoveKeyframes](#removekeyframes)|删除并有选择地销毁所有属于组的动画的关键帧。|
|[CAnimationGroup::RemoveTransitions](#removetransitions)|从属于组的动画的动画对象中删除转换。|
|[CAnimationGroup::Schedule](#schedule)|计划在指定的时间的动画。|
|[CAnimationGroup::SetAutodestroyTransitions](#setautodestroytransitions)|指示属于进行自动分组的所有动画对象都销毁转换。|

### <a name="protected-methods"></a>受保护的方法

|名称|描述|
|----------|-----------------|
|[CAnimationGroup::AddKeyframes](#addkeyframes)|将关键帧添加到情节提要帮助器。|
|[CAnimationGroup::AddTransitions](#addtransitions)|一个帮助程序，将转换添加到情节提要。|
|[CAnimationGroup::CreateTransitions](#createtransitions)|一个帮助程序，创建 COM 转换对象。|

### <a name="public-data-members"></a>公共数据成员

|名称|描述|
|----------|-----------------|
|[CAnimationGroup::m_bAutoclearTransitions](#m_bautocleartransitions)|指定如何清除从属于组的动画对象的转换。 如果此成员为 TRUE，则会自动删除转换时已安排动画。 否则，您需要手动删除转换。|
|[CAnimationGroup::m_bAutodestroyAnimationObjects](#m_bautodestroyanimationobjects)|指定如何销毁动画对象。 如果此参数为 TRUE，则销毁组时，将自动销毁动画对象。 否则，必须手动销毁动画对象。 默认值是 FALSE。 仅当使用 new 运算符动态分配属于组的所有动画对象，请将此值设置为 TRUE。|
|[CAnimationGroup::m_bAutodestroyKeyframes](#m_bautodestroykeyframes)|指定要销毁的关键帧的方式。 如果此值为 TRUE，删除并销毁; 所有关键帧否则会从列表中只中删除。 默认值为 TRUE。|
|[CAnimationGroup::m_lstAnimationObjects](#m_lstanimationobjects)|包含的动画对象的列表。|
|[CAnimationGroup::m_lstKeyFrames](#m_lstkeyframes)|包含一系列关键帧。|
|[CAnimationGroup::m_pStoryboard](#m_pstoryboard)|指向以动画情节提要。 此指针仅在调用上进行动画处理后才有效。|

### <a name="protected-data-members"></a>受保护的数据成员

|name|描述|
|----------|-----------------|
|[CAnimationGroup::m_nGroupID](#m_ngroupid)|动画组的唯一标识符。|
|[CAnimationGroup::m_pParentController](#m_pparentcontroller)|指向此组所属的动画控制器的指针。|

## <a name="remarks"></a>备注

动画组由动画控制器 (CAnimationController) 添加动画对象使用 CAnimationController::AddAnimationObject 时自动创建。 由 GroupID，通常会作为参数来操作动画组标识的动画组。 GroupID 取自被添加到新的动画组的第一个动画对象。 调用 CAnimationController::AnimateGroup，可以通过公共成员 m_pStoryboard 访问后，将创建封装的动画情节提要。

## <a name="inheritance-hierarchy"></a>继承层次结构

`CAnimationGroup`

## <a name="requirements"></a>要求

**标头：** afxanimationcontroller.h

##  <a name="_dtorcanimationgroup"></a>  CAnimationGroup:: ~ CAnimationGroup

析构函数。 当动画组被销毁时调用。

```
~CAnimationGroup();
```

##  <a name="addkeyframes"></a>  CAnimationGroup::AddKeyframes

将关键帧添加到情节提要帮助器。

```
void AddKeyframes(IUIAnimationStoryboard* pStoryboard, BOOL bAddDeep);
```

### <a name="parameters"></a>参数

*pStoryboard*<br/>
指向情节提要 COM 对象的指针。

*bAddDeep*<br/>
指定是否应将此方法添加到依赖于其他关键帧的情节提要关键帧。

##  <a name="addtransitions"></a>  CAnimationGroup::AddTransitions

一个帮助程序，将转换添加到情节提要。

```
void AddTransitions(
    IUIAnimationStoryboard* pStoryboard,
    BOOL bDependOnKeyframes);
```

### <a name="parameters"></a>参数

*pStoryboard*<br/>
指向情节提要 COM 对象的指针。

*bDependOnKeyframes*

##  <a name="animate"></a>  CAnimationGroup::Animate

对组进行动画处理。

```
BOOL Animate(
    IUIAnimationManager* pManager,
    IUIAnimationTimer* pTimer,
    BOOL bScheduleNow);
```

### <a name="parameters"></a>参数

*pManager*<br/>
*pTimer*
*bScheduleNow*

### <a name="return-value"></a>返回值

如果方法成功，则为 TRUE否则为 FALSE。

### <a name="remarks"></a>备注

此方法创建内部情节提要、 创建和应用转换和动画安排 bScheduleNow 为 TRUE。 如果 bScheduleNow 为 FALSE，您需要调用计划来启动动画在指定的时间。

##  <a name="applytransitions"></a>  CAnimationGroup::ApplyTransitions

适用于动画对象的转换。

```
void ApplyTransitions();
```

### <a name="remarks"></a>备注

此方法断言在调试模式下，如果尚未创建情节提要。 它首先，创建所有转换，然后添加"静态"关键帧 （取决于的偏移量的关键帧），、 添加不依赖于关键帧的转换、 添加关键帧，具体取决于转换和其他关键帧，并且最后添加依赖于关键帧的转换.

##  <a name="canimationgroup"></a>  CAnimationGroup::CAnimationGroup

构造一个动画组。

```
CAnimationGroup(CAnimationController* pParentController, UINT32 nGroupID);
```

### <a name="parameters"></a>参数

*pParentController*<br/>
指向用于创建一组动画控制器的指针。

*nGroupID*<br/>
指定 GroupID。

##  <a name="createtransitions"></a>  CAnimationGroup::CreateTransitions

一个帮助程序，创建 COM 转换对象。

```
BOOL CreateTransitions();
```

### <a name="return-value"></a>返回值

TRUE 是此方法成功，否则为 FALSE。

##  <a name="findanimationobject"></a>  CAnimationGroup::FindAnimationObject

查找包含指定的动画变量的动画对象。

```
CAnimationBaseObject* FindAnimationObject(IUIAnimationVariable* pVariable);
```

### <a name="parameters"></a>参数

*pVariable*<br/>
指向动画变量的指针。

### <a name="return-value"></a>返回值

动画对象或如果找不到动画对象，则为 NULL 的指针。

##  <a name="getgroupid"></a>  CAnimationGroup::GetGroupID

返回 GroupID。

```
UINT32 GetGroupID() const;
```

### <a name="return-value"></a>返回值

组标识符。

##  <a name="m_bautocleartransitions"></a>  CAnimationGroup::m_bAutoclearTransitions

指定如何清除从属于组的动画对象的转换。 如果此成员为 TRUE，则会自动删除转换时已安排动画。 否则，您需要手动删除转换。

```
BOOL m_bAutoclearTransitions;
```

##  <a name="m_bautodestroyanimationobjects"></a>  CAnimationGroup::m_bAutodestroyAnimationObjects

指定如何销毁动画对象。 如果此参数为 TRUE，则销毁组时，将自动销毁动画对象。 否则，必须手动销毁动画对象。 默认值是 FALSE。 仅当使用 new 运算符动态分配属于组的所有动画对象，请将此值设置为 TRUE。

```
BOOL m_bAutodestroyAnimationObjects;
```

##  <a name="m_bautodestroykeyframes"></a>  CAnimationGroup::m_bAutodestroyKeyframes

指定要销毁的关键帧的方式。 如果此值为 TRUE，删除并销毁; 所有关键帧否则会从列表中只中删除。 默认值为 TRUE。

```
BOOL m_bAutodestroyKeyframes;
```

##  <a name="m_lstanimationobjects"></a>  CAnimationGroup::m_lstAnimationObjects

包含的动画对象的列表。

```
CObList m_lstAnimationObjects;
```

##  <a name="m_lstkeyframes"></a>  CAnimationGroup::m_lstKeyFrames

包含一系列关键帧。

```
CObList m_lstKeyFrames;
```

##  <a name="m_ngroupid"></a>  CAnimationGroup::m_nGroupID

动画组的唯一标识符。

```
UINT32 m_nGroupID;
```

##  <a name="m_pparentcontroller"></a>  CAnimationGroup::m_pParentController

指向此组所属的动画控制器的指针。

```
CAnimationController* m_pParentController;
```

##  <a name="m_pstoryboard"></a>  CAnimationGroup::m_pStoryboard

指向以动画情节提要。 此指针仅在调用上进行动画处理后才有效。

```
ATL::CComPtr<IUIAnimationStoryboard> m_pStoryboard;
```

##  <a name="removekeyframes"></a>  CAnimationGroup::RemoveKeyframes

删除并有选择地销毁所有属于组的动画的关键帧。

```
void RemoveKeyframes();
```

### <a name="remarks"></a>备注

如果 m_bAutodestroyKeyframes 成员为 TRUE，则删除关键帧并将其销毁，否则从关键帧的内部列表只是删除关键帧。

##  <a name="removetransitions"></a>  CAnimationGroup::RemoveTransitions

从属于组的动画的动画对象中删除转换。

```
void RemoveTransitions();
```

### <a name="remarks"></a>备注

如果 m_bAutoclearTransitions 标志设置为 TRUE，此方法将循环属于的组的所有动画对象，并调用 CAnimationObject::ClearTransitions(FALSE)。

##  <a name="schedule"></a>  CAnimationGroup::Schedule

计划在指定的时间的动画。

```
BOOL Schedule(IUIAnimationTimer* pTimer, UI_ANIMATION_SECONDS time);
```

### <a name="parameters"></a>参数

*pTimer*<br/>
指向动画计时器的指针。

*time*<br/>
指定调度动画的时间。

### <a name="return-value"></a>返回值

如果方法成功，则为 TRUEFALSE 如果方法失败或如果进行动画处理尚未调用与 bScheduleNow 设置为 FALSE。

### <a name="remarks"></a>备注

调用此函数可计划在指定的时间的动画。 必须首先设置为 FALSE 的 bScheduleNow 与调用进行动画处理。

##  <a name="setautodestroytransitions"></a>  CAnimationGroup::SetAutodestroyTransitions

指示属于进行自动分组的所有动画对象都销毁转换。

```
void SetAutodestroyTransitions(BOOL bAutoDestroy = TRUE);
```

### <a name="parameters"></a>参数

*bAutoDestroy*<br/>
指定如何销毁转换。

### <a name="remarks"></a>备注

将此值设置为 FALSE，仅当分配在堆栈上的转换。 默认值为 TRUE，因此强烈建议分配使用 new 运算符的转换对象。

## <a name="see-also"></a>请参阅

[类](../../mfc/reference/mfc-classes.md)
