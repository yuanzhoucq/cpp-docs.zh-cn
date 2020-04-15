---
title: CAnimationGroup 类
ms.date: 03/27/2019
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
ms.openlocfilehash: 28d305e2107f7b9a8fd2164eb0ec9678d62ef8fa
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369749"
---
# <a name="canimationgroup-class"></a>CAnimationGroup 类

实现动画组，该动画组结合了动画情节提要、动画对象和过渡以定义动画。

## <a name="syntax"></a>语法

```
class CAnimationGroup;
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[动画组：：动画组](#canimationgroup)|构造动画组。|
|[动画组：*动画组](#_dtorcanimationgroup)|析构函数。 在销毁动画组时调用。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[动画组：动画](#animate)|为组设置动画。|
|[动画组：：应用转换](#applytransitions)|将转换应用于动画对象。|
|[动画组：：查找动画对象](#findanimationobject)|查找包含指定动画变量的动画对象。|
|[动画组：：获取群体ID](#getgroupid)|返回组 ID。|
|[动画组：：删除关键帧](#removekeyframes)|删除并选择性地销毁属于动画组的所有关键帧。|
|[动画组：：删除转换](#removetransitions)|从属于动画组的动画对象中删除过渡。|
|[动画组：：时间表](#schedule)|在指定时间安排动画。|
|[动画组：：设置自动销毁转换](#setautodestroytransitions)|引导属于组的所有动画对象自动销毁过渡。|

### <a name="protected-methods"></a>受保护的方法

|名称|说明|
|----------|-----------------|
|[动画组：：添加关键帧](#addkeyframes)|向情节提要添加关键帧的帮助程序。|
|[动画组：：添加转换](#addtransitions)|向情节提要添加过渡的帮助程序。|
|[动画组：：创建转换](#createtransitions)|创建 COM 转换对象的帮助程序。|

### <a name="public-data-members"></a>公共数据成员

|名称|说明|
|----------|-----------------|
|[动画组：：m_bAutoclearTransitions](#m_bautocleartransitions)|指定如何清除属于组的动画对象的转换。 如果此成员为 TRUE，则在计划动画时会自动删除过渡。 否则，您需要手动删除过渡。|
|[动画组：m_bAutodestroyAnimationObjects](#m_bautodestroyanimationobjects)|指定如何销毁动画对象。 如果此参数为 TRUE，则在销毁组时将自动销毁动画对象。 否则，必须手动销毁动画对象。 默认值是 FALSE。 仅当属于组的所有动画对象都使用运算符 new 动态分配时，才将此值设置为 TRUE。|
|[动画组：m_bAutodestroyKeyframes](#m_bautodestroykeyframes)|指定如何销毁关键帧。 如果此值为 TRUE，则删除并销毁所有关键帧;如果此值为 TRUE，则删除并销毁所有关键帧。否则，它们仅从列表中删除。 默认值为 TRUE。|
|[动画组：：m_lstAnimationObjects](#m_lstanimationobjects)|包含动画对象的列表。|
|[动画组：：m_lstKeyFrames](#m_lstkeyframes)|包含关键帧的列表。|
|[动画组：：m_pStoryboard](#m_pstoryboard)|指向动画情节提要。 此指针仅在在 Animate 上调用后有效。|

### <a name="protected-data-members"></a>受保护的数据成员

|名称|说明|
|----------|-----------------|
|[动画组：：m_nGroupID](#m_ngroupid)|动画组的唯一标识符。|
|[动画组：：m_pParentController](#m_pparentcontroller)|指向此组所属的动画控制器的指针。|

## <a name="remarks"></a>备注

当您使用 CAnimationController：：add 动画对象添加动画对象时，动画组由动画控制器 （CAnimationController） 自动创建。 动画组由 GroupID 标识，它通常被视为操作动画组的参数。 GroupID 取自添加到新动画组的第一个动画对象。 在调用 CAnimateController：：AnimateGroup 后，将创建一个封装的动画情节提要，并且可以通过公共成员m_pStoryboard访问。

## <a name="inheritance-hierarchy"></a>继承层次结构

`CAnimationGroup`

## <a name="requirements"></a>要求

**标头：** afxanimationcontroller.h

## <a name="canimationgroupcanimationgroup"></a><a name="_dtorcanimationgroup"></a>动画组：*动画组

析构函数。 在销毁动画组时调用。

```
~CAnimationGroup();
```

## <a name="canimationgroupaddkeyframes"></a><a name="addkeyframes"></a>动画组：：添加关键帧

向情节提要添加关键帧的帮助程序。

```
void AddKeyframes(IUIAnimationStoryboard* pStoryboard, BOOL bAddDeep);
```

### <a name="parameters"></a>参数

*板*<br/>
指向情节提要 COM 对象的指针。

*bAddDeep*<br/>
指定此方法是否应添加到依赖于其他关键帧的情节提要关键帧。

## <a name="canimationgroupaddtransitions"></a><a name="addtransitions"></a>动画组：：添加转换

向情节提要添加过渡的帮助程序。

```
void AddTransitions(
    IUIAnimationStoryboard* pStoryboard,
    BOOL bDependOnKeyframes);
```

### <a name="parameters"></a>参数

*板*<br/>
指向情节提要 COM 对象的指针。

*bDependon 关键帧*

## <a name="canimationgroupanimate"></a><a name="animate"></a>动画组：动画

为组设置动画。

```
BOOL Animate(
    IUIAnimationManager* pManager,
    IUIAnimationTimer* pTimer,
    BOOL bScheduleNow);
```

### <a name="parameters"></a>参数

*p经理*<br/>
*pTimer*
*b计划现在*

### <a name="return-value"></a>返回值

如果方法成功，则为 TRUE;否则 FALSE。

### <a name="remarks"></a>备注

此方法创建内部情节提要，创建并应用过渡，并在 b-IsisNow 为 TRUE 时安排动画。 如果 bTimeisNow 是 FALSE，则需要调用计划才能在指定时间启动动画。

## <a name="canimationgroupapplytransitions"></a><a name="applytransitions"></a>动画组：：应用转换

将转换应用于动画对象。

```
void ApplyTransitions();
```

### <a name="remarks"></a>备注

如果尚未创建情节提要，此方法 ASSERTS 处于调试模式。 它首先创建所有过渡，然后添加"静态"关键帧（依赖于偏移的关键帧），添加不依赖于关键帧的过渡，根据过渡和其他关键帧添加关键帧，最后添加依赖于关键帧的过渡。

## <a name="canimationgroupcanimationgroup"></a><a name="canimationgroup"></a>动画组：：动画组

构造动画组。

```
CAnimationGroup(CAnimationController* pParentController, UINT32 nGroupID);
```

### <a name="parameters"></a>参数

*p 家长控制器*<br/>
指向创建组的动画控制器的指针。

*n集团ID*<br/>
指定组 ID。

## <a name="canimationgroupcreatetransitions"></a><a name="createtransitions"></a>动画组：：创建转换

创建 COM 转换对象的帮助程序。

```
BOOL CreateTransitions();
```

### <a name="return-value"></a>返回值

TRUE 是方法成功，否则 FALSE。

## <a name="canimationgroupfindanimationobject"></a><a name="findanimationobject"></a>动画组：：查找动画对象

查找包含指定动画变量的动画对象。

```
CAnimationBaseObject* FindAnimationObject(IUIAnimationVariable* pVariable);
```

### <a name="parameters"></a>参数

*pvariable*<br/>
指向动画变量的指针。

### <a name="return-value"></a>返回值

指向动画对象的指针，如果未找到动画对象，则为 NULL。

## <a name="canimationgroupgetgroupid"></a><a name="getgroupid"></a>动画组：：获取群体ID

返回组 ID。

```
UINT32 GetGroupID() const;
```

### <a name="return-value"></a>返回值

组标识符。

## <a name="canimationgroupm_bautocleartransitions"></a><a name="m_bautocleartransitions"></a>动画组：：m_bAutoclearTransitions

指定如何清除属于组的动画对象的转换。 如果此成员为 TRUE，则在计划动画时会自动删除过渡。 否则，您需要手动删除过渡。

```
BOOL m_bAutoclearTransitions;
```

## <a name="canimationgroupm_bautodestroyanimationobjects"></a><a name="m_bautodestroyanimationobjects"></a>动画组：m_bAutodestroyAnimationObjects

指定如何销毁动画对象。 如果此参数为 TRUE，则在销毁组时将自动销毁动画对象。 否则，必须手动销毁动画对象。 默认值是 FALSE。 仅当属于组的所有动画对象都使用运算符 new 动态分配时，才将此值设置为 TRUE。

```
BOOL m_bAutodestroyAnimationObjects;
```

## <a name="canimationgroupm_bautodestroykeyframes"></a><a name="m_bautodestroykeyframes"></a>动画组：m_bAutodestroyKeyframes

指定如何销毁关键帧。 如果此值为 TRUE，则删除并销毁所有关键帧;如果此值为 TRUE，则删除并销毁所有关键帧。否则，它们仅从列表中删除。 默认值为 TRUE。

```
BOOL m_bAutodestroyKeyframes;
```

## <a name="canimationgroupm_lstanimationobjects"></a><a name="m_lstanimationobjects"></a>动画组：：m_lstAnimationObjects

包含动画对象的列表。

```
CObList m_lstAnimationObjects;
```

## <a name="canimationgroupm_lstkeyframes"></a><a name="m_lstkeyframes"></a>动画组：：m_lstKeyFrames

包含关键帧的列表。

```
CObList m_lstKeyFrames;
```

## <a name="canimationgroupm_ngroupid"></a><a name="m_ngroupid"></a>动画组：：m_nGroupID

动画组的唯一标识符。

```
UINT32 m_nGroupID;
```

## <a name="canimationgroupm_pparentcontroller"></a><a name="m_pparentcontroller"></a>动画组：：m_pParentController

指向此组所属的动画控制器的指针。

```
CAnimationController* m_pParentController;
```

## <a name="canimationgroupm_pstoryboard"></a><a name="m_pstoryboard"></a>动画组：：m_pStoryboard

指向动画情节提要。 此指针仅在在 Animate 上调用后有效。

```
ATL::CComPtr<IUIAnimationStoryboard> m_pStoryboard;
```

## <a name="canimationgroupremovekeyframes"></a><a name="removekeyframes"></a>动画组：：删除关键帧

删除并选择性地销毁属于动画组的所有关键帧。

```
void RemoveKeyframes();
```

### <a name="remarks"></a>备注

如果m_bAutodestroyKeyframes成员为 TRUE，则关键帧将被删除并销毁，否则关键帧将仅从关键帧的内部列表中删除。

## <a name="canimationgroupremovetransitions"></a><a name="removetransitions"></a>动画组：：删除转换

从属于动画组的动画对象中删除过渡。

```
void RemoveTransitions();
```

### <a name="remarks"></a>备注

如果m_bAutoclearTransitions标志设置为 TRUE，则此方法将循环访问属于该组的所有动画对象，并调用 CAnimationObject：：：清除转换（FALSE）。

## <a name="canimationgroupschedule"></a><a name="schedule"></a>动画组：：时间表

在指定时间安排动画。

```
BOOL Schedule(IUIAnimationTimer* pTimer, UI_ANIMATION_SECONDS time);
```

### <a name="parameters"></a>参数

*pTimer*<br/>
指向动画计时器的指针。

*time*<br/>
指定计划动画的时间。

### <a name="return-value"></a>返回值

如果方法成功，则为 TRUE;如果方法失败或 Animate 尚未调用，则使用 b-计划现在设置为 FALSE，则 FALSE。

### <a name="remarks"></a>备注

调用此函数以在指定时间安排动画。 您必须先将 b-计划现在设置为 FALSE 的 Animate。

## <a name="canimationgroupsetautodestroytransitions"></a><a name="setautodestroytransitions"></a>动画组：：设置自动销毁转换

引导属于组的所有动画对象自动销毁过渡。

```
void SetAutodestroyTransitions(BOOL bAutoDestroy = TRUE);
```

### <a name="parameters"></a>参数

*bAuto销毁*<br/>
指定如何销毁转换。

### <a name="remarks"></a>备注

仅当在堆栈上分配过渡时，才将此值设置为 FALSE。 默认值为 TRUE，因此强烈建议使用运算符 new 分配过渡对象。

## <a name="see-also"></a>另请参阅

[类](../../mfc/reference/mfc-classes.md)
