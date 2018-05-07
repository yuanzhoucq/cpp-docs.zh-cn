---
title: CBaseTransition 类 |Microsoft 文档
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
ms.openlocfilehash: db69941b0ee0f2267185604318d240d107604177
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
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
|[CBaseTransition::Create](#create)|创建 COM 转换。|  
|[CBaseTransition::GetEndKeyframe](#getendkeyframe)|返回启动关键帧。|  
|[CBaseTransition::GetRelatedVariable](#getrelatedvariable)|将指针返回到相关的变量。|  
|[CBaseTransition::GetStartKeyframe](#getstartkeyframe)|返回启动关键帧。|  
|[CBaseTransition::GetTransition](#gettransition)|已重载。 将指针返回到基础 COM 转换对象。|  
|[CBaseTransition::GetType](#gettype)|返回转换类型。|  
|[CBaseTransition::IsAdded](#isadded)|指示是否已将转换添加到情节提要。|  
|[Cbasetransition::](#setkeyframes)|设置转换的关键帧。|  
|[CBaseTransition::SetRelatedVariable](#setrelatedvariable)|建立动画变量和转换之间的关系。|  
  
### <a name="protected-data-members"></a>受保护的数据成员  
  
|名称|描述|  
|----------|-----------------|  
|[CBaseTransition::m_bAdded](#m_badded)|指定是否已将转换添加到情节提要。|  
|[CBaseTransition::m_pEndKeyframe](#m_pendkeyframe)|将存储到指定的结束过渡的关键帧的指针。|  
|[CBaseTransition::m_pRelatedVariable](#m_prelatedvariable)|指向与存储在 m_transition 转换进行动画处理的动画变量的指针。|  
|[CBaseTransition::m_pStartKeyframe](#m_pstartkeyframe)|将存储指向指定转换的起始时间的关键帧的指针。|  
|[CBaseTransition::m_transition](#m_transition)|存储指向 IUIAnimationTransition。 如果尚未创建 COM 转换对象为 NULL。|  
|[CBaseTransition::m_type](#m_type)|存储的转换类型。|  
  
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
 `pStoryboard`  
 情节提要的指针，其将进行动画处理相关的变量。  
  
### <a name="return-value"></a>返回值  
 如果为 TRUE，转换已成功添加到情节提要。  
  
### <a name="remarks"></a>备注  
 将该转换应用到情节提要中的相关变量。 如果这是应用于此情节提要中的此变量的第一个转换，转换将开始情节提要的开头。 否则，转换将追加到最近添加到变量的转换。  
  
##  <a name="addtostoryboardatkeyframes"></a>  CBaseTransition::AddToStoryboardAtKeyframes  
 将转换添加到情节提要。  
  
```  
BOOL AddToStoryboardAtKeyframes(IUIAnimationStoryboard* pStoryboard);
```  
  
### <a name="parameters"></a>参数  
 `pStoryboard`  
 情节提要的指针，其将进行动画处理相关的变量。  
  
### <a name="return-value"></a>返回值  
 如果为 TRUE，转换已成功添加到情节提要。  
  
### <a name="remarks"></a>备注  
 将该转换应用到情节提要中的相关变量。 如果已指定开始关键帧，转换将开始该关键帧。 如果已指定了结束关键帧，转换开始启动关键帧和，在结束关键帧处停止。 如果创建转换时使用指定的持续时间参数，该持续时间将被覆盖的开始和结束的关键帧之间的时间的持续时间。 如果已不指定任何关键帧，转换被追加到最近添加到变量的转换。  
  
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
 创建 COM 转换。  
  
```  
virtual BOOL Create(
    IUIAnimationTransitionLibrary* pLibrary,  
    IUIAnimationTransitionFactory* pFactory) = 0;  
```  
  
### <a name="parameters"></a>参数  
 `pLibrary`  
 创建标准转换的转换库指向的指针。 自定义转换，它可以为 NULL。  
  
 `pFactory`  
 指向转换工厂，其创建自定义转换的指针。 它可以为 NULL 的标准转换。  
  
### <a name="return-value"></a>返回值  
 如果成功，则创建转换 COM 对象，则返回 TRUE否则为 FALSE。  
  
### <a name="remarks"></a>备注  
 这是必须在派生类中重写一个纯虚拟函数。 它是由要实例化的基础 COM 转换对象的框架调用。  
  
##  <a name="getendkeyframe"></a>  CBaseTransition::GetEndKeyframe  
 返回启动关键帧。  
  
```  
CBaseKeyFrame* GetEndKeyframe();
```  
  
### <a name="return-value"></a>返回值  
 指向关键帧，则为 NULL，如果转换不应插入关键帧之间的有效指针。  
  
### <a name="remarks"></a>备注  
 此方法可以用于访问 SetKeyframes 以前设置的关键帧对象。 当转换被添加到情节提要时，它是由顶级代码调用。  
  
##  <a name="getrelatedvariable"></a>  CBaseTransition::GetRelatedVariable  
 将指针返回到相关的变量。  
  
```  
CAnimationVariable* GetRelatedVariable();
```  
  
### <a name="return-value"></a>返回值  
 指向动画变量，则为 NULL，如果尚未设置 SetRelatedVariable 由动画变量的有效指针。  
  
### <a name="remarks"></a>备注  
 这是对相关的动画变量的访问器。  
  
##  <a name="getstartkeyframe"></a>  CBaseTransition::GetStartKeyframe  
 返回启动关键帧。  
  
```  
CBaseKeyFrame* GetStartKeyframe();
```  
  
### <a name="return-value"></a>返回值  
 指向关键帧，则为 NULL，如果转换不应启动后关键帧的有效指针。  
  
### <a name="remarks"></a>备注  
 此方法可以用于访问 SetKeyframes 以前设置的关键帧对象。 当转换被添加到情节提要时，它是由顶级代码调用。  
  
##  <a name="gettransition"></a>  CBaseTransition::GetTransition  
 将指针返回到基础 COM 转换对象。  
  
```  
IUIAnimationTransition* GetTransition(
    IUIAnimationTransitionLibrary* pLibrary,  
    IUIAnimationTransitionFactory* pFactory);  
  
IUIAnimationTransition* GetTransition();
```  
  
### <a name="parameters"></a>参数  
 `pLibrary`  
 创建标准转换的转换库指向的指针。 自定义转换，它可以为 NULL。  
  
 `pFactory`  
 指向转换工厂，其创建自定义转换的指针。 它可以为 NULL 的标准转换。  
  
### <a name="return-value"></a>返回值  
 无法创建 IUIAnimationTransition 或 NULL 如果基础转换的有效指针。  
  
### <a name="remarks"></a>备注  
 此方法将指针返回到基础 COM 转换对象，如有必要将创建它。  
  
##  <a name="gettype"></a>  CBaseTransition::GetType  
 返回转换类型。  
  
```  
TRANSITION_TYPE GetType() const;  
```  
  
### <a name="return-value"></a>返回值  
 一个 TRANSITION_TYPE 枚举值。  
  
### <a name="remarks"></a>备注  
 此方法可以用于标识转换对象按照其类型。 在派生类中的构造函数集的类型。  
  
##  <a name="isadded"></a>  CBaseTransition::IsAdded  
 指示是否已将转换添加到情节提要。  
  
```  
BOOL IsAdded();
```  
  
### <a name="return-value"></a>返回值  
 如果已将转换添加到情节提要，否则为 FALSE，则返回 TRUE。  
  
### <a name="remarks"></a>备注  
 当顶层代码添加到情节提要的转换时，将内部设置此标志。  
  
##  <a name="m_badded"></a>  CBaseTransition::m_bAdded  
 指定是否已将转换添加到情节提要。  
  
```  
BOOL m_bAdded;  
```  
  
##  <a name="m_pendkeyframe"></a>  CBaseTransition::m_pEndKeyframe  
 将存储到指定的结束过渡的关键帧的指针。  
  
```  
CBaseKeyFrame* m_pEndKeyframe;  
```  
  
##  <a name="m_prelatedvariable"></a>  CBaseTransition::m_pRelatedVariable  
 指向与存储在 m_transition 转换进行动画处理的动画变量的指针。  
  
```  
CAnimationVariable* m_pRelatedVariable;  
```  
  
##  <a name="m_pstartkeyframe"></a>  CBaseTransition::m_pStartKeyframe  
 将存储指向指定转换的起始时间的关键帧的指针。  
  
```  
CBaseKeyFrame* m_pStartKeyframe;  
```  
  
##  <a name="m_transition"></a>  CBaseTransition::m_transition  
 存储指向 IUIAnimationTransition。 如果尚未创建 COM 转换对象为 NULL。  
  
```  
ATL::CComPtr<IUIAnimationTransition> m_transition;  
```  
  
##  <a name="m_type"></a>  CBaseTransition::m_type  
 存储的转换类型。  
  
```  
TRANSITION_TYPE m_type;  
```  
  
##  <a name="setkeyframes"></a>  Cbasetransition::  
 设置转换的关键帧。  
  
```  
void SetKeyframes(
    CBaseKeyFrame* pStart = NULL,  
    CBaseKeyFrame* pEnd = NULL);
```  
  
### <a name="parameters"></a>参数  
 `pStart`  
 指定转换的起始关键帧。  
  
 `pEnd`  
 指定转换结束关键帧。  
  
### <a name="remarks"></a>备注  
 此方法指示转换后指定的关键帧启动，和 （可选） 如果挂起不为 NULL，则结束之前指定的关键帧。 如果创建转换时使用指定的持续时间参数，该持续时间将被覆盖的开始和结束的关键帧之间的时间的持续时间。  
  
##  <a name="setrelatedvariable"></a>  CBaseTransition::SetRelatedVariable  
 建立动画变量和转换之间的关系。  
  
```  
void SetRelatedVariable(CAnimationVariable* pVariable);
```  
  
### <a name="parameters"></a>参数  
 `pVariable`  
 指向相关的动画变量的指针。  
  
### <a name="remarks"></a>备注  
 建立动画变量和转换之间的关系。 转换可以只能应用于一个变量。  
  
##  <a name="transition_type_enumeration"></a>  CBaseTransition::TRANSITION_TYPE 枚举  
 定义当前支持 Windows 动画 API 的 MFC 实现的转换类型。  
  
```  
enum TRANSITION_TYPE;  
```  
  
### <a name="remarks"></a>备注  
 转换类型的特定转换构造函数中设置。 例如，CSinusoidalTransitionFromRange 将其类型设置为 SINUSOIDAL_FROM_RANGE。  
  
## <a name="see-also"></a>请参阅  
 [类](../../mfc/reference/mfc-classes.md)
