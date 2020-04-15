---
title: CBaseTransition 类
ms.date: 03/27/2019
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
ms.openlocfilehash: 8339785fd10fa3dcef1c0fb573310762dc2d2405
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81352834"
---
# <a name="cbasetransition-class"></a>CBaseTransition 类

表示基本转换。

## <a name="syntax"></a>语法

```
class CBaseTransition : public CObject;
```

## <a name="members"></a>成员

### <a name="public-enumerations"></a>公共枚举

|名称|说明|
|----------|-----------------|
|[CBase 转换：：TRANSITION_TYPE枚举](#transition_type_enumeration)|定义 Windows 动画 API MFC 实现当前支持的过渡类型。|

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[CBase 转换：CBase 转换](#cbasetransition)|构造基本过渡对象。|
|[CBase 转换：*CBase 转换](#_dtorcbasetransition)|析构函数。 在销毁过渡对象时调用。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CBase 转换：：添加到故事板](#addtostoryboard)|向情节提要添加过渡。|
|[CBase 转换：：添加到故事板的帧](#addtostoryboardatkeyframes)|向情节提要添加过渡。|
|[CBase 转换：清除](#clear)|释放封装的 IUI 动画转换 COM 对象。|
|[CBase 转换：创建](#create)|创建 COM 转换。|
|[CBase 转换：获取结束关键帧](#getendkeyframe)|返回启动关键帧。|
|[CBase 转换：获取相关变量](#getrelatedvariable)|返回指向相关变量的指针。|
|[CBase 转换：获取启动关键帧](#getstartkeyframe)|返回启动关键帧。|
|[CBase 转换：获取过渡](#gettransition)|已重载。 返回指向基础 COM 过渡对象的指针。|
|[CBase 转换：获取类型](#gettype)|返回转换类型。|
|[CBase 转换：已添加](#isadded)|告诉是否已将过渡添加到情节提要中。|
|[CBase 转换：：设置关键帧](#setkeyframes)|为过渡设置关键帧。|
|[CBase 转换：：设置相关变量](#setrelatedvariable)|在动画变量和转换之间建立关系。|

### <a name="protected-data-members"></a>受保护的数据成员

|名称|说明|
|----------|-----------------|
|[CBase 转换：m_bAdded](#m_badded)|指定过渡是否已添加到情节提要。|
|[CBase 转换：m_pEndKeyframe](#m_pendkeyframe)|存储指向指定过渡结束的关键帧的指针。|
|[CBase 转换：m_pRelatedVariable](#m_prelatedvariable)|指向动画变量的指针，该变量使用存储在m_transition中的过渡进行动画处理。|
|[CBase 转换：m_pStartKeyframe](#m_pstartkeyframe)|存储指向指定转换开始的关键帧的指针。|
|[CBase 转换：m_transition](#m_transition)|存储指向 IUI 动画转换的指针。 如果未创建 COM 过渡对象，则为 NULL。|
|[CBase 转换：m_type](#m_type)|存储过渡类型。|

## <a name="remarks"></a>备注

此类封装 IUIAnimation 转换接口，并用作所有转换的基类。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

`CBaseTransition`

## <a name="requirements"></a>要求

**标头：** afxanimationcontroller.h

## <a name="cbasetransitioncbasetransition"></a><a name="_dtorcbasetransition"></a>CBase 转换：*CBase 转换

析构函数。 在销毁过渡对象时调用。

```
virtual ~CBaseTransition();
```

## <a name="cbasetransitionaddtostoryboard"></a><a name="addtostoryboard"></a>CBase 转换：：添加到故事板

向情节提要添加过渡。

```
BOOL AddToStoryboard(IUIAnimationStoryboard* pStoryboard);
```

### <a name="parameters"></a>参数

*板*<br/>
指向情节提要的指针，它将为相关变量设置动画。

### <a name="return-value"></a>返回值

如果过渡已成功添加到情节提要，则为 TRUE。

### <a name="remarks"></a>备注

将转换应用于情节提要中的相关变量。 如果这是在此情节提要中应用于此变量的第一个过渡，则过渡从情节提要的开头开始。 否则，过渡将追加到最近添加到变量的过渡。

## <a name="cbasetransitionaddtostoryboardatkeyframes"></a><a name="addtostoryboardatkeyframes"></a>CBase 转换：：添加到故事板的帧

向情节提要添加过渡。

```
BOOL AddToStoryboardAtKeyframes(IUIAnimationStoryboard* pStoryboard);
```

### <a name="parameters"></a>参数

*板*<br/>
指向情节提要的指针，它将为相关变量设置动画。

### <a name="return-value"></a>返回值

如果过渡已成功添加到情节提要，则为 TRUE。

### <a name="remarks"></a>备注

将转换应用于情节提要中的相关变量。 如果指定了启动关键帧，则转换从该关键帧开始。 如果指定了端键帧，则过渡从启动关键帧开始，并在端键帧停止。 如果转换是在指定持续时间参数下创建的，则该持续时间将覆盖在开始和结束关键帧之间的持续时间。 如果未指定关键帧，则过渡将追加到最近添加到变量的过渡中。

## <a name="cbasetransitioncbasetransition"></a><a name="cbasetransition"></a>CBase 转换：CBase 转换

构造基本过渡对象。

```
CBaseTransition();
```

## <a name="cbasetransitionclear"></a><a name="clear"></a>CBase 转换：清除

释放封装的 IUI 动画转换 COM 对象。

```
void Clear();
```

### <a name="remarks"></a>备注

应从派生类的 Create 方法调用此方法，以防止 IUI 转换接口泄漏。

## <a name="cbasetransitioncreate"></a><a name="create"></a>CBase 转换：创建

创建 COM 转换。

```
virtual BOOL Create(
    IUIAnimationTransitionLibrary* pLibrary,
    IUIAnimationTransitionFactory* pFactory) = 0;
```

### <a name="parameters"></a>参数

*p库*<br/>
指向过渡库的指针，该指针创建标准转换。 对于自定义转换，它可以为 NULL。

*pFactory*<br/>
指向转换工厂的指针，该指针创建自定义转换。 对于标准转换，它可以为 NULL。

### <a name="return-value"></a>返回值

如果成功创建了转换 COM 对象，则为 TRUE;如果成功创建了转换 COM 对象，则为 TRUE。否则 FALSE。

### <a name="remarks"></a>备注

这是一个纯虚拟函数，必须在派生类中重写。 框架调用它来实例化基础 COM 转换对象。

## <a name="cbasetransitiongetendkeyframe"></a><a name="getendkeyframe"></a>CBase 转换：获取结束关键帧

返回启动关键帧。

```
CBaseKeyFrame* GetEndKeyframe();
```

### <a name="return-value"></a>返回值

如果不应在关键帧之间插入过渡，则指向关键帧的有效指针或 NULL。

### <a name="remarks"></a>备注

此方法可用于访问以前由 SetKeyframe 设置的关键帧对象。 在将转换添加到情节提要时，由顶级代码调用它。

## <a name="cbasetransitiongetrelatedvariable"></a><a name="getrelatedvariable"></a>CBase 转换：获取相关变量

返回指向相关变量的指针。

```
CAnimationVariable* GetRelatedVariable();
```

### <a name="return-value"></a>返回值

动画变量尚未由 Set关联变量设置动画变量，则指向动画变量的有效指针，或 NULL。

### <a name="remarks"></a>备注

这是相关动画变量的访问器。

## <a name="cbasetransitiongetstartkeyframe"></a><a name="getstartkeyframe"></a>CBase 转换：获取启动关键帧

返回启动关键帧。

```
CBaseKeyFrame* GetStartKeyframe();
```

### <a name="return-value"></a>返回值

如果过渡不应在关键帧之后启动，则指向关键帧的有效指针或 NULL。

### <a name="remarks"></a>备注

此方法可用于访问以前由 SetKeyframe 设置的关键帧对象。 在将转换添加到情节提要时，由顶级代码调用它。

## <a name="cbasetransitiongettransition"></a><a name="gettransition"></a>CBase 转换：获取过渡

返回指向基础 COM 过渡对象的指针。

```
IUIAnimationTransition* GetTransition(
    IUIAnimationTransitionLibrary* pLibrary,
    IUIAnimationTransitionFactory* pFactory);

IUIAnimationTransition* GetTransition();
```

### <a name="parameters"></a>参数

*p库*<br/>
指向过渡库的指针，该指针创建标准转换。 对于自定义转换，它可以为 NULL。

*pFactory*<br/>
指向转换工厂的指针，该指针创建自定义转换。 对于标准转换，它可以为 NULL。

### <a name="return-value"></a>返回值

如果无法创建基础转换，则指向 IUIAnimation 转换或 NULL 的有效指针。

### <a name="remarks"></a>备注

此方法返回指向基础 COM 过渡对象的指针，并在必要时创建它。

## <a name="cbasetransitiongettype"></a><a name="gettype"></a>CBase 转换：获取类型

返回转换类型。

```
TRANSITION_TYPE GetType() const;
```

### <a name="return-value"></a>返回值

TRANSITION_TYPE枚举值之一。

### <a name="remarks"></a>备注

此方法可用于按其类型标识过渡对象。 类型在派生类中的构造函数中设置。

## <a name="cbasetransitionisadded"></a><a name="isadded"></a>CBase 转换：已添加

告诉是否已将过渡添加到情节提要中。

```
BOOL IsAdded();
```

### <a name="return-value"></a>返回值

如果过渡已添加到情节提要，则返回 TRUE，否则为 FALSE。

### <a name="remarks"></a>备注

当顶级代码向情节提要添加转换时，将在内部设置此标志。

## <a name="cbasetransitionm_badded"></a><a name="m_badded"></a>CBase 转换：m_bAdded

指定过渡是否已添加到情节提要。

```
BOOL m_bAdded;
```

## <a name="cbasetransitionm_pendkeyframe"></a><a name="m_pendkeyframe"></a>CBase 转换：m_pEndKeyframe

存储指向指定过渡结束的关键帧的指针。

```
CBaseKeyFrame* m_pEndKeyframe;
```

## <a name="cbasetransitionm_prelatedvariable"></a><a name="m_prelatedvariable"></a>CBase 转换：m_pRelatedVariable

指向动画变量的指针，该变量使用存储在m_transition中的过渡进行动画处理。

```
CAnimationVariable* m_pRelatedVariable;
```

## <a name="cbasetransitionm_pstartkeyframe"></a><a name="m_pstartkeyframe"></a>CBase 转换：m_pStartKeyframe

存储指向指定转换开始的关键帧的指针。

```
CBaseKeyFrame* m_pStartKeyframe;
```

## <a name="cbasetransitionm_transition"></a><a name="m_transition"></a>CBase 转换：m_transition

存储指向 IUI 动画转换的指针。 如果未创建 COM 过渡对象，则为 NULL。

```
ATL::CComPtr<IUIAnimationTransition> m_transition;
```

## <a name="cbasetransitionm_type"></a><a name="m_type"></a>CBase 转换：m_type

存储过渡类型。

```
TRANSITION_TYPE m_type;
```

## <a name="cbasetransitionsetkeyframes"></a><a name="setkeyframes"></a>CBase 转换：：设置关键帧

为过渡设置关键帧。

```
void SetKeyframes(
    CBaseKeyFrame* pStart = NULL,
    CBaseKeyFrame* pEnd = NULL);
```

### <a name="parameters"></a>参数

*p 开始*<br/>
指定转换开头的关键帧。

*pEnd*<br/>
指定过渡结束的关键帧。

### <a name="remarks"></a>备注

此方法告诉转换在指定的关键帧之后开始，并且（可选地，如果 pEnd 不是 NULL）在指定的关键帧之前结束。 如果转换是在指定持续时间参数下创建的，则该持续时间将覆盖在开始和结束关键帧之间的持续时间。

## <a name="cbasetransitionsetrelatedvariable"></a><a name="setrelatedvariable"></a>CBase 转换：：设置相关变量

在动画变量和转换之间建立关系。

```
void SetRelatedVariable(CAnimationVariable* pVariable);
```

### <a name="parameters"></a>参数

*pvariable*<br/>
指向相关动画变量的指针。

### <a name="remarks"></a>备注

在动画变量和转换之间建立关系。 转换只能应用于一个变量。

## <a name="cbasetransitiontransition_type-enumeration"></a><a name="transition_type_enumeration"></a>CBase 转换：：TRANSITION_TYPE枚举

定义 Windows 动画 API MFC 实现当前支持的过渡类型。

```
enum TRANSITION_TYPE;
```

### <a name="remarks"></a>备注

在特定过渡的构造函数中设置过渡类型。 例如，CSinusoid转换FromRange将其类型设置为SINUSOIDAL_FROM_RANGE。

## <a name="see-also"></a>另请参阅

[类](../../mfc/reference/mfc-classes.md)
