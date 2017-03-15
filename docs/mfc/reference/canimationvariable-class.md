---
title: "CAnimationVariable 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CAnimationVariable
- afxanimationcontroller/CAnimationVariable
dev_langs:
- C++
helpviewer_keywords:
- CAnimationVariable class
ms.assetid: 506e697e-31a8-4033-a27e-292f4d7b42d9
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
ms.openlocfilehash: 42513c841f6dc891369d7d6640ced1aa37f90e8e
ms.lasthandoff: 02/24/2017

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
|[CAnimationVariable::CAnimationVariable](#canimationvariable)|构造动画变量对象。|  
|[CAnimationVariable:: ~ CAnimationVariable](#canimationvariable__~canimationvariable)|析构函数。 当 CAnimationVariable 对象被销毁时调用。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|说明|  
|----------|-----------------|  
|[CAnimationVariable::AddTransition](#addtransition)|添加转换。|  
|[CAnimationVariable::ApplyTransitions](#applytransitions)|将转换添加到情节提要的内部列表中。|  
|[CAnimationVariable::ClearTransitions](#cleartransitions)|清除转换。|  
|[CAnimationVariable::Create](#create)|创建基础动画变量 COM 对象。|  
|[CAnimationVariable::CreateTransitions](#createtransitions)|创建应用于此动画变量的所有转换。|  
|[CAnimationVariable::EnableIntegerValueChangedEvent](#enableintegervaluechangedevent)|启用或禁用 IntegerValueChanged 事件。|  
|[CAnimationVariable::EnableValueChangedEvent](#enablevaluechangedevent)|启用或禁用 ValueChanged 事件。|  
|[CAnimationVariable::GetDefaultValue](#getdefaultvalue)|返回默认值。|  
|[CAnimationVariable::GetParentAnimationObject](#getparentanimationobject)|返回父动画对象。|  
|[CAnimationVariable::GetValue](#getvalue)|已重载。 返回的动画变量的当前值。|  
|[CAnimationVariable::GetVariable](#getvariable)|返回指向 IUIAnimationVariable COM 对象的指针。|  
|[CAnimationVariable::SetDefaultValue](#setdefaultvalue)|设置默认值，并释放 IUIAnimationVariable COM 对象。|  
  
### <a name="protected-methods"></a>受保护的方法  
  
|名称|说明|  
|----------|-----------------|  
|[CAnimationVariable::SetParentAnimationObject](#setparentanimationobject)|设置动画变量和动画对象之间的关系。|  
  
### <a name="public-data-members"></a>公共数据成员  
  
|名称|说明|  
|----------|-----------------|  
|[CAnimationVariable::m_bAutodestroyTransitions](#m_bautodestroytransitions)|指定是否应删除相关的转换对象。|  
  
### <a name="protected-data-members"></a>受保护的数据成员  
  
|名称|描述|  
|----------|-----------------|  
|[CAnimationVariable::m_dblDefaultValue](#m_dbldefaultvalue)|指定传播到 IUIAnimationVariable 的默认值。|  
|[CAnimationVariable::m_lstTransitions](#m_lsttransitions)|包含的转换进行动画处理此动画变量的列表。|  
|[CAnimationVariable::m_pParentObject](#m_pparentobject)|指向一个封装此动画变量的动画对象的指针。|  
|[CAnimationVariable::m_variable](#m_variable)|存储指向 IUIAnimationVariable COM 对象的指针。 如果尚未，创建的 COM 对象或创建失败，则为 NULL。|  
  
## <a name="remarks"></a>备注  
 CAnimationVariable 类封装 IUIAnimationVariable COM 对象。 它还包含应用于在演示图板动画变量的转换列表。 CAnimationVariable 对象嵌入到可以表示在应用程序动态值、 点、 大小、 颜色和矩形的动画对象中。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `CAnimationVariable`  
  
## <a name="requirements"></a>要求  
 **标头：** afxanimationcontroller.h  
  
##  <a name="a-namedtorcanimationvariablea--canimationvariablecanimationvariable"></a><a name="_dtorcanimationvariable"></a>CAnimationVariable:: ~ CAnimationVariable  
 析构函数。 当 CAnimationVariable 对象被销毁时调用。  
  
```  
virtual ~CAnimationVariable();
```  
  
##  <a name="a-nameaddtransitiona--canimationvariableaddtransition"></a><a name="addtransition"></a>CAnimationVariable::AddTransition  
 添加转换。  
  
```  
void AddTransition(CBaseTransition* pTransition);
```  
  
### <a name="parameters"></a>参数  
 `pTransition`  
 指向要添加的转换的指针。  
  
### <a name="remarks"></a>备注  
 调用此方法以将转换添加到内部列表应用于动画变量的转换。 在计划动画时，应清除此列表。  
  
##  <a name="a-nameapplytransitionsa--canimationvariableapplytransitions"></a><a name="applytransitions"></a>CAnimationVariable::ApplyTransitions  
 将转换添加到情节提要的内部列表中。  
  
```  
void ApplyTransitions(
    CAnimationController* pController,  
    IUIAnimationStoryboard* pStoryboard,  
    BOOL bDependOnKeyframes);
```  
  
### <a name="parameters"></a>参数  
 `pController`  
 指向父级动画控制器的指针。  
  
 `pStoryboard`  
 情节提要的指针。  
  
 `bDependOnKeyframes`  
 如果为 TRUE，则此方法应添加依赖于关键帧的转换。  
  
### <a name="remarks"></a>备注  
 此方法将转换添加到情节提要的内部列表中。 它称为从最高级别代码多次添加转换，它们不依赖于关键帧并且添加依赖于关键帧的转换。 如果尚未创建基础动画变量的 COM 对象，此方法将创建它在此阶段。  
  
##  <a name="a-namecanimationvariablea--canimationvariablecanimationvariable"></a><a name="canimationvariable"></a>CAnimationVariable::CAnimationVariable  
 构造动画变量对象。  
  
```  
CAnimationVariable(DOUBLE dblDefaultValue = 0.0);
```  
  
### <a name="parameters"></a>参数  
 `dblDefaultValue`  
 指定默认值。  
  
### <a name="remarks"></a>备注  
 构造动画变量对象，并设置其默认值。 变量没有动画效果，或无法进行动画处理时使用默认值。  
  
##  <a name="a-namecleartransitionsa--canimationvariablecleartransitions"></a><a name="cleartransitions"></a>CAnimationVariable::ClearTransitions  
 清除转换。  
  
```  
void ClearTransitions(BOOL bAutodestroy);
```  
  
### <a name="parameters"></a>参数  
 `bAutodestroy`  
 指定此方法是否应删除转换对象。  
  
### <a name="remarks"></a>备注  
 此方法从转换的内部列表中删除所有转换。 如果 bAutodestroy 为 TRUE，或 m_bAutodestroyTransitions 为 TRUE，则将删除转换。 否则调用方应释放转换对象。  
  
##  <a name="a-namecreatea--canimationvariablecreate"></a><a name="create"></a>CAnimationVariable::Create  
 创建基础动画变量 COM 对象。  
  
```  
virtual BOOL Create(IUIAnimationManager* pManager);
```  
  
### <a name="parameters"></a>参数  
 `pManager`  
 动画管理器指向的指针。  
  
### <a name="return-value"></a>返回值  
 如果已成功创建动画变量; 则为 TRUE否则为 FALSE。  
  
### <a name="remarks"></a>备注  
 此方法创建基础动画变量的 COM 对象，并设置其默认值。  
  
##  <a name="a-namecreatetransitionsa--canimationvariablecreatetransitions"></a><a name="createtransitions"></a>CAnimationVariable::CreateTransitions  
 创建应用于此动画变量的所有转换。  
  
```  
BOOL CreateTransitions(
    IUIAnimationTransitionLibrary* pLibrary,  
    IUIAnimationTransitionFactory* \*not used*\);
```  
  
### <a name="parameters"></a>参数  
`pLibrary`  
 一个指向[IUIAnimationTransitionLibrary 接口](https://msdn.microsoft.com/library/windows/desktop/dd371897)，后者定义一个标准转换的库。  
  
### <a name="return-value"></a>返回值  
 如果转换成功，则已创建，则返回 TRUE否则为 FALSE。  
  
### <a name="remarks"></a>备注  
 在需要创建已添加到该变量的内部列表中的转换的转换时，将由框架调用此方法。  
  
##  <a name="a-nameenableintegervaluechangedeventa--canimationvariableenableintegervaluechangedevent"></a><a name="enableintegervaluechangedevent"></a>CAnimationVariable::EnableIntegerValueChangedEvent  
 启用或禁用 IntegerValueChanged 事件。  
  
```  
void EnableIntegerValueChangedEvent (
    CAnimationController* pController,  
    BOOL bEnable);
```  
  
### <a name="parameters"></a>参数  
 `pController`  
 指向父控制器的指针。  
  
 `bEnable`  
 TRUE-启用事件，FALSE-禁用事件。  
  
### <a name="remarks"></a>备注  
 启用 ValueChanged 事件后，框架调用虚方法 CAnimationController::OnAnimationIntegerValueChanged。 您需要在为了处理此事件从 CAnimationController 派生的类中重写它。 每次更改的动画变量的整数值时，调用此方法。  
  
##  <a name="a-nameenablevaluechangedeventa--canimationvariableenablevaluechangedevent"></a><a name="enablevaluechangedevent"></a>CAnimationVariable::EnableValueChangedEvent  
 启用或禁用 ValueChanged 事件。  
  
```  
void EnableValueChangedEvent (
    CAnimationController* pController,  
    BOOL bEnable);
```  
  
### <a name="parameters"></a>参数  
 `pController`  
 指向父控制器的指针。  
  
 `bEnable`  
 TRUE-启用事件，FALSE-禁用事件。  
  
### <a name="remarks"></a>备注  
 启用 ValueChanged 事件后，框架调用虚方法 CAnimationController::OnAnimationValueChanged。 您需要在为了处理此事件从 CAnimationController 派生的类中重写它。 每次更改的动画变量的值后，调用此方法。  
  
##  <a name="a-namegetdefaultvaluea--canimationvariablegetdefaultvalue"></a><a name="getdefaultvalue"></a>CAnimationVariable::GetDefaultValue  
 返回默认值。  
  
```  
DOUBLE GetDefaultValue() const;  
```  
  
### <a name="return-value"></a>返回值  
 默认值。  
  
### <a name="remarks"></a>备注  
 使用此函数来获取动画变量的默认值。 在构造函数中或由 SetDefaultValue 方法，可以设置默认值。  
  
##  <a name="a-namegetparentanimationobjecta--canimationvariablegetparentanimationobject"></a><a name="getparentanimationobject"></a>CAnimationVariable::GetParentAnimationObject  
 返回父动画对象。  
  
```  
CAnimationBaseObject* GetParentAnimationObject();
```  
  
### <a name="return-value"></a>返回值  
 一个指针指向父动画对象，如果关系已建立，否则为 NULL。  
  
### <a name="remarks"></a>备注  
 可以调用此方法来检索指向父动画对象 （容器） 的指针。  
  
##  <a name="a-namegetvaluea--canimationvariablegetvalue"></a><a name="getvalue"></a>CAnimationVariable::GetValue  
 返回的动画变量的当前值。  
  
```  
HRESULT GetValue(DOUBLE& dblValue);  
HRESULT GetValue(INT32& nValue);
```  
  
### <a name="parameters"></a>参数  
 `dblValue`  
 动画变量的当前值。  
  
 `nValue`  
 动画变量的当前值。  
  
### <a name="return-value"></a>返回值  
 如果成功，获取的值或尚未创建基础动画变量则为 S_OK。 否则为 HRESULT 错误代码。  
  
### <a name="remarks"></a>备注  
 可以调用此方法来检索动画变量的当前值。 如果尚未创建基础 COM 对象，dblValue 将包含默认值，当函数返回。  
  
##  <a name="a-namegetvariablea--canimationvariablegetvariable"></a><a name="getvariable"></a>CAnimationVariable::GetVariable  
 返回指向 IUIAnimationVariable COM 对象的指针。  
  
```  
IUIAnimationVariable* GetVariable();
```  
  
### <a name="return-value"></a>返回值  
 指向 IUIAnimationVariable COM 对象或如果动画变量无法创建或未创建，则为 NULL 的有效指针。  
  
### <a name="remarks"></a>备注  
 使用此函数来访问基础 IUIAnimationVariable COM 对象并根据需要直接调用其方法。  
  
##  <a name="a-namembautodestroytransitionsa--canimationvariablembautodestroytransitions"></a><a name="m_bautodestroytransitions"></a>CAnimationVariable::m_bAutodestroyTransitions  
 指定是否应删除相关的转换对象。  
  
```  
BOOL m_bAutodestroyTransitions;  
```  
  
### <a name="remarks"></a>备注  
 此将值设置为 true 可强制转换对象删除时将被从转换的内部列表。 如果此值为 FALSE 转换应通过调用应用程序删除。 之后已安排动画，始终将被清除的转换列表。 默认值为 FALSE。  
  
##  <a name="a-namemdbldefaultvaluea--canimationvariablemdbldefaultvalue"></a><a name="m_dbldefaultvalue"></a>CAnimationVariable::m_dblDefaultValue  
 指定传播到 IUIAnimationVariable 的默认值。  
  
```  
DOUBLE m_dblDefaultValue;  
```  
  
##  <a name="a-namemlsttransitionsa--canimationvariablemlsttransitions"></a><a name="m_lsttransitions"></a>CAnimationVariable::m_lstTransitions  
 包含的转换进行动画处理此动画变量的列表。  
  
```  
CObList m_lstTransitions;  
```  
  
##  <a name="a-namempparentobjecta--canimationvariablempparentobject"></a><a name="m_pparentobject"></a>CAnimationVariable::m_pParentObject  
 指向一个封装此动画变量的动画对象的指针。  
  
```  
CAnimationBaseObject* m_pParentObject;  
```  
  
##  <a name="a-namemvariablea--canimationvariablemvariable"></a><a name="m_variable"></a>CAnimationVariable::m_variable  
 存储指向 IUIAnimationVariable COM 对象的指针。 如果尚未，创建的 COM 对象或创建失败，则为 NULL。  
  
```  
ATL::CComPtr<IUIAnimationVariable> m_variable;  
```  
  
##  <a name="a-namesetdefaultvaluea--canimationvariablesetdefaultvalue"></a><a name="setdefaultvalue"></a>CAnimationVariable::SetDefaultValue  
 设置默认值，并释放 IUIAnimationVariable COM 对象。  
  
```  
void SetDefaultValue(DOUBLE dblDefaultValue);
```  
  
### <a name="parameters"></a>参数  
 `dblDefaultValue`  
 指定新的默认值。  
  
### <a name="remarks"></a>备注  
 使用此方法以重置默认值。 此方法释放内部 IUIAnimationVariable COM 对象，因此重新创建动画变量时，基础 COM 对象获取新的默认值。 如果未创建 COM 对象，表示动画变量，或如果变量没有动画效果，GetValue 将返回默认值。  
  
##  <a name="a-namesetparentanimationobjecta--canimationvariablesetparentanimationobject"></a><a name="setparentanimationobject"></a>CAnimationVariable::SetParentAnimationObject  
 设置动画变量和动画对象之间的关系。  
  
```  
void SetParentAnimationObject(CAnimationBaseObject* pParentObject);
```  
  
### <a name="parameters"></a>参数  
 `pParentObject`  
 指向一个包含此变量的动画对象的指针。  
  
### <a name="remarks"></a>备注  
 在内部调用此方法以建立一个动画变量，并对其进行解封的动画对象之间的一对一关系。  
  
## <a name="see-also"></a>另请参阅  
 [类](../../mfc/reference/mfc-classes.md)

