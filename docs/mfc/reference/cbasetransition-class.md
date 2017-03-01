---
title: "CBaseTransition 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CBaseTransition
- afxanimationcontroller/CBaseTransition
dev_langs:
- C++
helpviewer_keywords:
- CBaseTransition class
ms.assetid: dfe84007-bbc5-43b7-b5b8-fae9145573bf
caps.latest.revision: 17
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: b979d03587ada42486d0462733dfe6fd22f9f7cc
ms.lasthandoff: 02/24/2017

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
|[CBaseTransition::TRANSITION_TYPE 枚举](#transition_type_enumeration)|定义当前支持 Windows 动画 API 的 MFC 实现的转换类型。|  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|说明|  
|----------|-----------------|  
|[CBaseTransition::CBaseTransition](#cbasetransition)|构造基本转换对象。|  
|[CBaseTransition:: ~ CBaseTransition](#cbasetransition__~cbasetransition)|析构函数。 当转换对象被销毁时调用。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|说明|  
|----------|-----------------|  
|[CBaseTransition::AddToStoryboard](#addtostoryboard)|将转换添加到情节提要。|  
|[CBaseTransition::AddToStoryboardAtKeyframes](#addtostoryboardatkeyframes)|将转换添加到情节提要。|  
|[CBaseTransition::Clear](#clear)|版本封装 IUIAnimationTransition COM 对象。|  
|[CBaseTransition::Create](#create)|创建 COM 过渡效果。|  
|[CBaseTransition::GetEndKeyframe](#getendkeyframe)|返回开始关键帧。|  
|[CBaseTransition::GetRelatedVariable](#getrelatedvariable)|返回指向相关变量的指针。|  
|[CBaseTransition::GetStartKeyframe](#getstartkeyframe)|返回开始关键帧。|  
|[CBaseTransition::GetTransition](#gettransition)|已重载。 返回指向基础 COM 转换对象的指针。|  
|[CBaseTransition::GetType](#gettype)|返回转换类型。|  
|[CBaseTransition::IsAdded](#isadded)|指示是否已将转换添加到情节提要。|  
|[CBaseTransition::SetKeyframes](#setkeyframes)|设置关键帧进行转换。|  
|[CBaseTransition::SetRelatedVariable](#setrelatedvariable)|建立动画变量和转换之间的关系。|  
  
### <a name="protected-data-members"></a>受保护的数据成员  
  
|名称|说明|  
|----------|-----------------|  
|[CBaseTransition::m_bAdded](#m_badded)|指定是否已将转换添加到情节提要。|  
|[CBaseTransition::m_pEndKeyframe](#m_pendkeyframe)|存储指定过渡的结束的关键帧的指针。|  
|[CBaseTransition::m_pRelatedVariable](#m_prelatedvariable)|指向与存储在 m_transition 转换进行动画处理的动画变量的指针。|  
|[CBaseTransition::m_pStartKeyframe](#m_pstartkeyframe)|存储指定过渡的开头的关键帧的指针。|  
|[CBaseTransition::m_transition](#m_transition)|存储指向 IUIAnimationTransition。 如果尚未创建 COM 转换对象为 NULL。|  
|[CBaseTransition::m_type](#m_type)|存储的转换类型。|  
  
## <a name="remarks"></a>备注  
 此类封装 IUIAnimationTransition 接口，并用作基类的所有转换。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CBaseTransition`  
  
## <a name="requirements"></a>要求  
 **标头：** afxanimationcontroller.h  
  
##  <a name="a-namedtorcbasetransitiona--cbasetransitioncbasetransition"></a><a name="_dtorcbasetransition"></a>CBaseTransition:: ~ CBaseTransition  
 析构函数。 当转换对象被销毁时调用。  
  
```  
virtual ~CBaseTransition();
```  
  
##  <a name="a-nameaddtostoryboarda--cbasetransitionaddtostoryboard"></a><a name="addtostoryboard"></a>CBaseTransition::AddToStoryboard  
 将转换添加到情节提要。  
  
```  
BOOL AddToStoryboard(IUIAnimationStoryboard* pStoryboard);
```  
  
### <a name="parameters"></a>参数  
 `pStoryboard`  
 情节提要的指针，它将对相关的变量进行动画处理。  
  
### <a name="return-value"></a>返回值  
 如果为 TRUE，转换已成功添加到情节提要。  
  
### <a name="remarks"></a>备注  
 将该转换应用到情节提要中的相关变量。 如果这是应用到此情节提要中该变量的第一个转换，转换将开始在情节提要的开始处。 否则，转换将追加到最近添加到该变量的转换。  
  
##  <a name="a-nameaddtostoryboardatkeyframesa--cbasetransitionaddtostoryboardatkeyframes"></a><a name="addtostoryboardatkeyframes"></a>CBaseTransition::AddToStoryboardAtKeyframes  
 将转换添加到情节提要。  
  
```  
BOOL AddToStoryboardAtKeyframes(IUIAnimationStoryboard* pStoryboard);
```  
  
### <a name="parameters"></a>参数  
 `pStoryboard`  
 情节提要的指针，它将对相关的变量进行动画处理。  
  
### <a name="return-value"></a>返回值  
 如果为 TRUE，转换已成功添加到情节提要。  
  
### <a name="remarks"></a>备注  
 将该转换应用到情节提要中的相关变量。 如果指定了开始关键帧，该转换将开始在该关键帧处。 如果指定了结束关键帧，在开始关键帧处开始转换，并在结束关键帧处停止。 如果创建转换时使用指定的持续时间参数，该持续时间将被覆盖的开始和结束关键帧之间的时间的持续时间。 如果指定了未关键帧，转换追加到最近添加到该变量的转换。  
  
##  <a name="a-namecbasetransitiona--cbasetransitioncbasetransition"></a><a name="cbasetransition"></a>CBaseTransition::CBaseTransition  
 构造基本转换对象。  
  
```  
CBaseTransition();
```  
  
##  <a name="a-namecleara--cbasetransitionclear"></a><a name="clear"></a>CBaseTransition::Clear  
 版本封装 IUIAnimationTransition COM 对象。  
  
```  
void Clear();
```  
  
### <a name="remarks"></a>备注  
 为了防止 IUITransition 接口泄漏，应从派生的类的 Create 方法中调用此方法。  
  
##  <a name="a-namecreatea--cbasetransitioncreate"></a><a name="create"></a>CBaseTransition::Create  
 创建 COM 过渡效果。  
  
```  
virtual BOOL Create(
    IUIAnimationTransitionLibrary* pLibrary,  
    IUIAnimationTransitionFactory* pFactory) = 0;  
```  
  
### <a name="parameters"></a>参数  
 `pLibrary`  
 创建标准转换的转换库指向的指针。 它可以为 NULL 的自定义转换。  
  
 `pFactory`  
 创建自定义转换的转换工厂指向的指针。 它可以为 NULL 的标准转换。  
  
### <a name="return-value"></a>返回值  
 如果转换为 COM 对象已成功创建;否则为 FALSE。  
  
### <a name="remarks"></a>备注  
 这是必须在派生类中重写一个纯虚函数。 它是由框架调用以实例化基础 COM 转换对象。  
  
##  <a name="a-namegetendkeyframea--cbasetransitiongetendkeyframe"></a><a name="getendkeyframe"></a>CBaseTransition::GetEndKeyframe  
 返回开始关键帧。  
  
```  
CBaseKeyFrame* GetEndKeyframe();
```  
  
### <a name="return-value"></a>返回值  
 关键帧，或者为 NULL，如果转换不应插入关键帧之间有效指针。  
  
### <a name="remarks"></a>备注  
 此方法可用于访问由 SetKeyframes 以前设置的关键帧对象。 当转换被添加到情节提要时，它是由顶级代码调用。  
  
##  <a name="a-namegetrelatedvariablea--cbasetransitiongetrelatedvariable"></a><a name="getrelatedvariable"></a>CBaseTransition::GetRelatedVariable  
 返回指向相关变量的指针。  
  
```  
CAnimationVariable* GetRelatedVariable();
```  
  
### <a name="return-value"></a>返回值  
 指向动画变量或如果尚未设置 SetRelatedVariable 由动画变量为 NULL 的有效指针。  
  
### <a name="remarks"></a>备注  
 这是对相关的动画变量的访问器。  
  
##  <a name="a-namegetstartkeyframea--cbasetransitiongetstartkeyframe"></a><a name="getstartkeyframe"></a>CBaseTransition::GetStartKeyframe  
 返回开始关键帧。  
  
```  
CBaseKeyFrame* GetStartKeyframe();
```  
  
### <a name="return-value"></a>返回值  
 指向一个关键帧，则为 NULL，如果转换不应在关键帧后启动的有效指针。  
  
### <a name="remarks"></a>备注  
 此方法可用于访问由 SetKeyframes 以前设置的关键帧对象。 当转换被添加到情节提要时，它是由顶级代码调用。  
  
##  <a name="a-namegettransitiona--cbasetransitiongettransition"></a><a name="gettransition"></a>CBaseTransition::GetTransition  
 返回指向基础 COM 转换对象的指针。  
  
```  
IUIAnimationTransition* GetTransition(
    IUIAnimationTransitionLibrary* pLibrary,  
    IUIAnimationTransitionFactory* pFactory);  
  
IUIAnimationTransition* GetTransition();
```  
  
### <a name="parameters"></a>参数  
 `pLibrary`  
 创建标准转换的转换库指向的指针。 它可以为 NULL 的自定义转换。  
  
 `pFactory`  
 创建自定义转换的转换工厂指向的指针。 它可以为 NULL 的标准转换。  
  
### <a name="return-value"></a>返回值  
 无法创建指向 IUIAnimationTransition 或如果基础转换为 NULL 的有效指针。  
  
### <a name="remarks"></a>备注  
 此方法返回指向基础 COM 转换对象的指针，如有必要将创建它。  
  
##  <a name="a-namegettypea--cbasetransitiongettype"></a><a name="gettype"></a>CBaseTransition::GetType  
 返回转换类型。  
  
```  
TRANSITION_TYPE GetType() const;  
```  
  
### <a name="return-value"></a>返回值  
 一个 TRANSITION_TYPE 枚举值。  
  
### <a name="remarks"></a>备注  
 此方法可用于标识转换对象由其类型。 在派生类中的构造函数集的类型。  
  
##  <a name="a-nameisaddeda--cbasetransitionisadded"></a><a name="isadded"></a>CBaseTransition::IsAdded  
 指示是否已将转换添加到情节提要。  
  
```  
BOOL IsAdded();
```  
  
### <a name="return-value"></a>返回值  
 如果已将转换添加到情节提要，否则为 FALSE，则返回 TRUE。  
  
### <a name="remarks"></a>备注  
 顶级代码将转换添加到情节提要时，将在内部设置此标志。  
  
##  <a name="a-namembaddeda--cbasetransitionmbadded"></a><a name="m_badded"></a>CBaseTransition::m_bAdded  
 指定是否已将转换添加到情节提要。  
  
```  
BOOL m_bAdded;  
```  
  
##  <a name="a-namempendkeyframea--cbasetransitionmpendkeyframe"></a><a name="m_pendkeyframe"></a>CBaseTransition::m_pEndKeyframe  
 存储指定过渡的结束的关键帧的指针。  
  
```  
CBaseKeyFrame* m_pEndKeyframe;  
```  
  
##  <a name="a-namemprelatedvariablea--cbasetransitionmprelatedvariable"></a><a name="m_prelatedvariable"></a>CBaseTransition::m_pRelatedVariable  
 指向与存储在 m_transition 转换进行动画处理的动画变量的指针。  
  
```  
CAnimationVariable* m_pRelatedVariable;  
```  
  
##  <a name="a-namempstartkeyframea--cbasetransitionmpstartkeyframe"></a><a name="m_pstartkeyframe"></a>CBaseTransition::m_pStartKeyframe  
 存储指定过渡的开头的关键帧的指针。  
  
```  
CBaseKeyFrame* m_pStartKeyframe;  
```  
  
##  <a name="a-namemtransitiona--cbasetransitionmtransition"></a><a name="m_transition"></a>CBaseTransition::m_transition  
 存储指向 IUIAnimationTransition。 如果尚未创建 COM 转换对象为 NULL。  
  
```  
ATL::CComPtr<IUIAnimationTransition> m_transition;  
```  
  
##  <a name="a-namemtypea--cbasetransitionmtype"></a><a name="m_type"></a>CBaseTransition::m_type  
 存储的转换类型。  
  
```  
TRANSITION_TYPE m_type;  
```  
  
##  <a name="a-namesetkeyframesa--cbasetransitionsetkeyframes"></a><a name="setkeyframes"></a>CBaseTransition::SetKeyframes  
 设置关键帧进行转换。  
  
```  
void SetKeyframes(
    CBaseKeyFrame* pStart = NULL,  
    CBaseKeyFrame* pEnd = NULL);
```  
  
### <a name="parameters"></a>参数  
 `pStart`  
 指定过渡的开头的一个关键帧。  
  
 `pEnd`  
 指定转换的结束关键帧。  
  
### <a name="remarks"></a>备注  
 此方法指示在指定的关键帧后启动，并 （可选） 如果挂起不为 NULL，则最终的转换之前指定的关键帧。 如果创建转换时使用指定的持续时间参数，该持续时间将被覆盖的开始和结束关键帧之间的时间的持续时间。  
  
##  <a name="a-namesetrelatedvariablea--cbasetransitionsetrelatedvariable"></a><a name="setrelatedvariable"></a>CBaseTransition::SetRelatedVariable  
 建立动画变量和转换之间的关系。  
  
```  
void SetRelatedVariable(CAnimationVariable* pVariable);
```  
  
### <a name="parameters"></a>参数  
 `pVariable`  
 指向相关的动画变量的指针。  
  
### <a name="remarks"></a>备注  
 建立动画变量和转换之间的关系。 转换可以只能应用于一个变量。  
  
##  <a name="a-nametransitiontypeenumerationa--cbasetransitiontransitiontype-enumeration"></a><a name="transition_type_enumeration"></a>CBaseTransition::TRANSITION_TYPE 枚举  
 定义当前支持 Windows 动画 API 的 MFC 实现的转换类型。  
  
```  
enum TRANSITION_TYPE;  
```  
  
### <a name="remarks"></a>备注  
 转换类型的特定转换构造函数中设置。 例如，CSinusoidalTransitionFromRange 将其类型设置为 SINUSOIDAL_FROM_RANGE。  
  
## <a name="see-also"></a>另请参阅  
 [类](../../mfc/reference/mfc-classes.md)

