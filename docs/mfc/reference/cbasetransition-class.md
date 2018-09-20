---
title: CBaseTransition 类 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CBaseTransition
- AFXANIMATIONCONTROLLER/CBaseTransition
- AFXANIMATIONCONTROLLER/CBaseTransition::CBaseTransition
- AFXANIMATIONCONTROLLER/CBaseTransition::AddToStoryboard
- AFXANIMATIONCONTROLLER/CBaseTransition::AddToStoryboardAtKeyframes
- AFXANIMATIONCONTROLLER/CBaseTransition::Clear
- AFXANIMATIONCONTROLLER/CBaseTransition::Create
- AFXANIMATIONCONTROLLER/CBaseTransition::GetEndKeyframe
- AFXANIMATIONCONTROLLER/CBaseTransition::GetRelatedVariable
- AFXANIMATIONCONTROLLER/CBaseTransition::GetStartKeyframe
- AFXANIMATIONCONTROLLER/CBaseTransition::GetTransition
- AFXANIMATIONCONTROLLER/CBaseTransition::GetType
- AFXANIMATIONCONTROLLER/CBaseTransition::IsAdded
- AFXANIMATIONCONTROLLER/CBaseTransition::SetKeyframes
- AFXANIMATIONCONTROLLER/CBaseTransition::SetRelatedVariable
- AFXANIMATIONCONTROLLER/CBaseTransition::m_bAdded
- AFXANIMATIONCONTROLLER/CBaseTransition::m_pEndKeyframe
- AFXANIMATIONCONTROLLER/CBaseTransition::m_pRelatedVariable
- AFXANIMATIONCONTROLLER/CBaseTransition::m_pStartKeyframe
- AFXANIMATIONCONTROLLER/CBaseTransition::m_transition
- AFXANIMATIONCONTROLLER/CBaseTransition::m_type
dev_langs:
- C++
helpviewer_keywords:
- CBaseTransition [MFC], CBaseTransition
- CBaseTransition [MFC], AddToStoryboard
- CBaseTransition [MFC], AddToStoryboardAtKeyframes
- CBaseTransition [MFC], Clear
- CBaseTransition [MFC], Create
- CBaseTransition [MFC], GetEndKeyframe
- CBaseTransition [MFC], GetRelatedVariable
- CBaseTransition [MFC], GetStartKeyframe
- CBaseTransition [MFC], GetTransition
- CBaseTransition [MFC], GetType
- CBaseTransition [MFC], IsAdded
- CBaseTransition [MFC], SetKeyframes
- CBaseTransition [MFC], SetRelatedVariable
- CBaseTransition [MFC], m_bAdded
- CBaseTransition [MFC], m_pEndKeyframe
- CBaseTransition [MFC], m_pRelatedVariable
- CBaseTransition [MFC], m_pStartKeyframe
- CBaseTransition [MFC], m_transition
- CBaseTransition [MFC], m_type
ms.assetid: dfe84007-bbc5-43b7-b5b8-fae9145573bf
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 16c838d9ffbef8ace933990fdaa88dc84c1c56ee
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46385490"
---
# <a name="cbasetransition-class"></a>CBaseTransition 类

表示基本转换。

## <a name="syntax"></a>语法

```
class CBaseTransition : public CObject;
```

## <a name="members"></a>成员

### <a name="public-enumerations"></a>公共枚举

|名称|描述|
|----------|-----------------|
|[CBaseTransition::TRANSITION_TYPE 枚举](#transition_type_enumeration)|定义当前支持 Windows 动画 API 的 MFC 实现的转换类型。|

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[CBaseTransition::CBaseTransition](#cbasetransition)|构造基本转换对象。|
|[CBaseTransition:: ~ CBaseTransition](#cbasetransition__~cbasetransition)|析构函数。 当转换对象被销毁时调用。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CBaseTransition::AddToStoryboard](#addtostoryboard)|将转换添加到情节提要。|
|[CBaseTransition::AddToStoryboardAtKeyframes](#addtostoryboardatkeyframes)|将转换添加到情节提要。|
|[CBaseTransition::Clear](#clear)|版本封装 IUIAnimationTransition COM 对象。|
|[CBaseTransition::Create](#create)|创建的 COM 过渡。|
|[CBaseTransition::GetEndKeyframe](#getendkeyframe)|开始返回关键帧。|
|[CBaseTransition::GetRelatedVariable](#getrelatedvariable)|返回一个指向相关的变量。|
|[CBaseTransition::GetStartKeyframe](#getstartkeyframe)|开始返回关键帧。|
|[CBaseTransition::GetTransition](#gettransition)|已重载。 返回指向基础 COM 转换对象的指针。|
|[CBaseTransition::GetType](#gettype)|返回转换类型。|
|[CBaseTransition::IsAdded](#isadded)|指示是否已将转换添加到情节提要。|
|[Cbasetransition::](#setkeyframes)|设置关键帧进行转换。|
|[CBaseTransition::SetRelatedVariable](#setrelatedvariable)|建立动画变量和转换之间的关系。|

### <a name="protected-data-members"></a>受保护的数据成员

|name|描述|
|----------|-----------------|
|[CBaseTransition::m_bAdded](#m_badded)|指定是否已将转换添加到情节提要。|
|[CBaseTransition::m_pEndKeyframe](#m_pendkeyframe)|将存储到指定的转换结束的关键帧的指针。|
|[CBaseTransition::m_pRelatedVariable](#m_prelatedvariable)|指向与存储在 m_transition 转换进行动画处理的动画变量的指针。|
|[CBaseTransition::m_pStartKeyframe](#m_pstartkeyframe)|存储指向指定过渡的开头的关键帧的指针。|
|[CBaseTransition::m_transition](#m_transition)|存储指向 IUIAnimationTransition 的指针。 如果尚未创建 COM 转换对象为 NULL。|
|[CBaseTransition::m_type](#m_type)|将存储的过渡类型。|

## <a name="remarks"></a>备注

此类封装 IUIAnimationTransition 接口，并用作基类的所有转换。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

`CBaseTransition`

## <a name="requirements"></a>要求

**标头：** afxanimationcontroller.h

##  <a name="_dtorcbasetransition"></a>  CBaseTransition:: ~ CBaseTransition

析构函数。 当转换对象被销毁时调用。

```
virtual ~CBaseTransition();
```

##  <a name="addtostoryboard"></a>  CBaseTransition::AddToStoryboard

将转换添加到情节提要。

```
BOOL AddToStoryboard(IUIAnimationStoryboard* pStoryboard);
```

### <a name="parameters"></a>参数

*pStoryboard*<br/>
情节提要的指针，这将对相关的变量进行动画处理。

### <a name="return-value"></a>返回值

如果为 TRUE，转换已成功添加到情节提要。

### <a name="remarks"></a>备注

将该转换应用到情节提要中的相关变量。 如果这是应用于此情节提要中此变量的第一个转换，转换将开始在情节提要开始。 否则，转换被追加到最近添加到该变量的转换。

##  <a name="addtostoryboardatkeyframes"></a>  CBaseTransition::AddToStoryboardAtKeyframes

将转换添加到情节提要。

```
BOOL AddToStoryboardAtKeyframes(IUIAnimationStoryboard* pStoryboard);
```

### <a name="parameters"></a>参数

*pStoryboard*<br/>
情节提要的指针，这将对相关的变量进行动画处理。

### <a name="return-value"></a>返回值

如果为 TRUE，转换已成功添加到情节提要。

### <a name="remarks"></a>备注

将该转换应用到情节提要中的相关变量。 如果指定了开始关键帧，在该关键帧开始转换。 如果指定了结束关键帧，转换将开始在启动关键帧，并且在结束关键帧处停止。 如果在创建转换时指定的持续时间参数，则会开始和结束关键帧之间的时间的持续时间以覆盖该持续时间。 如果不指定了任何关键帧，转换被追加到最近添加到该变量的转换。

##  <a name="cbasetransition"></a>  CBaseTransition::CBaseTransition

构造基本转换对象。

```
CBaseTransition();
```

##  <a name="clear"></a>  CBaseTransition::Clear

版本封装 IUIAnimationTransition COM 对象。

```
void Clear();
```

### <a name="remarks"></a>备注

为了防止 IUITransition 接口泄漏，应从派生的类的 Create 方法调用此方法。

##  <a name="create"></a>  CBaseTransition::Create

创建的 COM 过渡。

```
virtual BOOL Create(
    IUIAnimationTransitionLibrary* pLibrary,
    IUIAnimationTransitionFactory* pFactory) = 0;
```

### <a name="parameters"></a>参数

*pLibrary*<br/>
指向转换库，创建标准转换的指针。 它可以为 NULL 的自定义转换。

*pFactory*<br/>
创建自定义转换的转换工厂指向的指针。 它可以为 NULL 的标准转换。

### <a name="return-value"></a>返回值

如果转换为 COM 对象已成功创建;否则为 FALSE。

### <a name="remarks"></a>备注

这是必须在派生类中重写一个纯虚函数。 若要实例化的基础 COM 转换对象框架调用它。

##  <a name="getendkeyframe"></a>  CBaseTransition::GetEndKeyframe

开始返回关键帧。

```
CBaseKeyFrame* GetEndKeyframe();
```

### <a name="return-value"></a>返回值

指向一个关键帧或如果不应关键帧之间插入一个转换，则为 NULL 的有效指针。

### <a name="remarks"></a>备注

此方法可用于访问由 SetKeyframes 以前设置的关键帧对象。 当转换被添加到情节提要时，它是由顶级代码调用。

##  <a name="getrelatedvariable"></a>  CBaseTransition::GetRelatedVariable

返回一个指向相关的变量。

```
CAnimationVariable* GetRelatedVariable();
```

### <a name="return-value"></a>返回值

指向动画变量或如果 SetRelatedVariable 尚未设置动画变量，则为 NULL 的有效指针。

### <a name="remarks"></a>备注

这是对相关的动画变量的访问器。

##  <a name="getstartkeyframe"></a>  CBaseTransition::GetStartKeyframe

开始返回关键帧。

```
CBaseKeyFrame* GetStartKeyframe();
```

### <a name="return-value"></a>返回值

指向一个关键帧或如果关键帧后不能以一个转换，则为 NULL 的有效指针。

### <a name="remarks"></a>备注

此方法可用于访问由 SetKeyframes 以前设置的关键帧对象。 当转换被添加到情节提要时，它是由顶级代码调用。

##  <a name="gettransition"></a>  CBaseTransition::GetTransition

返回指向基础 COM 转换对象的指针。

```
IUIAnimationTransition* GetTransition(
    IUIAnimationTransitionLibrary* pLibrary,
    IUIAnimationTransitionFactory* pFactory);

IUIAnimationTransition* GetTransition();
```

### <a name="parameters"></a>参数

*pLibrary*<br/>
指向转换库，创建标准转换的指针。 它可以为 NULL 的自定义转换。

*pFactory*<br/>
创建自定义转换的转换工厂指向的指针。 它可以为 NULL 的标准转换。

### <a name="return-value"></a>返回值

无法创建 IUIAnimationTransition 或如果基础转换，则为 NULL 的有效指针。

### <a name="remarks"></a>备注

此方法返回指向基础 COM 转换对象的指针，必要时创建它。

##  <a name="gettype"></a>  CBaseTransition::GetType

返回转换类型。

```
TRANSITION_TYPE GetType() const;
```

### <a name="return-value"></a>返回值

一个 TRANSITION_TYPE 枚举值。

### <a name="remarks"></a>备注

此方法可以用于标识转换对象由其类型。 在派生类的构造函数集的类型。

##  <a name="isadded"></a>  CBaseTransition::IsAdded

指示是否已将转换添加到情节提要。

```
BOOL IsAdded();
```

### <a name="return-value"></a>返回值

如果已将转换添加到情节提要，否则为 FALSE，则返回 TRUE。

### <a name="remarks"></a>备注

最高级别代码添加到情节提要的转换时，将在内部设置此标志。

##  <a name="m_badded"></a>  CBaseTransition::m_bAdded

指定是否已将转换添加到情节提要。

```
BOOL m_bAdded;
```

##  <a name="m_pendkeyframe"></a>  CBaseTransition::m_pEndKeyframe

将存储到指定的转换结束的关键帧的指针。

```
CBaseKeyFrame* m_pEndKeyframe;
```

##  <a name="m_prelatedvariable"></a>  CBaseTransition::m_pRelatedVariable

指向与存储在 m_transition 转换进行动画处理的动画变量的指针。

```
CAnimationVariable* m_pRelatedVariable;
```

##  <a name="m_pstartkeyframe"></a>  CBaseTransition::m_pStartKeyframe

存储指向指定过渡的开头的关键帧的指针。

```
CBaseKeyFrame* m_pStartKeyframe;
```

##  <a name="m_transition"></a>  CBaseTransition::m_transition

存储指向 IUIAnimationTransition 的指针。 如果尚未创建 COM 转换对象为 NULL。

```
ATL::CComPtr<IUIAnimationTransition> m_transition;
```

##  <a name="m_type"></a>  CBaseTransition::m_type

将存储的过渡类型。

```
TRANSITION_TYPE m_type;
```

##  <a name="setkeyframes"></a>  Cbasetransition::

设置关键帧进行转换。

```
void SetKeyframes(
    CBaseKeyFrame* pStart = NULL,
    CBaseKeyFrame* pEnd = NULL);
```

### <a name="parameters"></a>参数

*pStart*<br/>
指定过渡的开头关键帧。

*挂起*<br/>
指定在转换结束关键帧。

### <a name="remarks"></a>备注

此方法要求指定关键帧后启动，并 （可选） 如果挂起不为 NULL，则最终的转换之前指定关键帧。 如果在创建转换时指定的持续时间参数，则会开始和结束关键帧之间的时间的持续时间以覆盖该持续时间。

##  <a name="setrelatedvariable"></a>  CBaseTransition::SetRelatedVariable

建立动画变量和转换之间的关系。

```
void SetRelatedVariable(CAnimationVariable* pVariable);
```

### <a name="parameters"></a>参数

*pVariable*<br/>
指向相关的动画变量的指针。

### <a name="remarks"></a>备注

建立动画变量和转换之间的关系。 可以仅对一个变量应用转换。

##  <a name="transition_type_enumeration"></a>  CBaseTransition::TRANSITION_TYPE 枚举

定义当前支持 Windows 动画 API 的 MFC 实现的转换类型。

```
enum TRANSITION_TYPE;
```

### <a name="remarks"></a>备注

转换类型的特定转换构造函数中设置。 例如，CSinusoidalTransitionFromRange 其类型设置为 SINUSOIDAL_FROM_RANGE。

## <a name="see-also"></a>请参阅

[类](../../mfc/reference/mfc-classes.md)
