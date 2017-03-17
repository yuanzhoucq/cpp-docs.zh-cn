---
title: "CAnimationBaseObject 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
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
- CAnimationBaseObject class
ms.assetid: 76b25917-940e-4eba-940f-31d270702603
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
ms.openlocfilehash: c714c78b7017ed314b30f64df4bfceb587226c15
ms.lasthandoff: 02/24/2017

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
|[CAnimationBaseObject::CAnimationBaseObject](#canimationbaseobject)|已重载。 构造的动画对象。|  
|[CAnimationBaseObject:: ~ CAnimationBaseObject](#canimationbaseobject__~canimationbaseobject)|析构函数。 当动画对象被销毁时调用。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|说明|  
|----------|-----------------|  
|[CAnimationBaseObject::ApplyTransitions](#applytransitions)|添加到情节提要与封装的动画变量的转换。|  
|[CAnimationBaseObject::ClearTransitions](#cleartransitions)|删除所有相关的转换。|  
|[CAnimationBaseObject::ContainsVariable](#containsvariable)|确定动画对象是否包含特定的动画变量。|  
|[CAnimationBaseObject::CreateTransitions](#createtransitions)|创建与动画对象相关联的转换。|  
|[CAnimationBaseObject::DetachFromController](#detachfromcontroller)|从父级动画控制器的动画对象中分离。|  
|[CAnimationBaseObject::EnableIntegerValueChangedEvent](#enableintegervaluechangedevent)|设置整数值已更改事件处理程序。|  
|[CAnimationBaseObject::EnableValueChangedEvent](#enablevaluechangedevent)|设置值发生更改时事件处理程序。|  
|[CAnimationBaseObject::GetAutodestroyTransitions](#getautodestroytransitions)|指示是否自动销毁相关的转换。|  
|[CAnimationBaseObject::GetGroupID](#getgroupid)|返回当前组 id。|  
|[CAnimationBaseObject::GetObjectID](#getobjectid)|返回当前对象 id。|  
|[CAnimationBaseObject::GetUserData](#getuserdata)|返回用户定义的数据。|  
|[CAnimationBaseObject::SetAutodestroyTransitions](#setautodestroytransitions)|设置自动销毁转换进行排序的标志。|  
|[CAnimationBaseObject::SetID](#setid)|设置新的 Id。|  
|[CAnimationBaseObject::SetUserData](#setuserdata)|设置用户定义的数据。|  
  
### <a name="protected-methods"></a>受保护的方法  
  
|名称|描述|  
|----------|-----------------|  
|[CAnimationBaseObject::GetAnimationVariableList](#getanimationvariablelist)|收集到包含的动画变量的指针。|  
|[CAnimationBaseObject::SetParentAnimationObjects](#setparentanimationobjects)|动画对象与它们的容器中包含的动画变量之间建立关系。|  
  
### <a name="protected-data-members"></a>受保护的数据成员  
  
|名称|描述|  
|----------|-----------------|  
|[CAnimationBaseObject::m_bAutodestroyTransitions](#m_bautodestroytransitions)|指定是否应自动销毁相关的转换。|  
|[CAnimationBaseObject::m_dwUserData](#m_dwuserdata)|存储用户定义的数据。|  
|[CAnimationBaseObject::m_nGroupID](#m_ngroupid)|指定动画对象的组 ID。|  
|[CAnimationBaseObject::m_nObjectID](#m_nobjectid)|指定动画对象的对象 ID。|  
|[CAnimationBaseObject::m_pParentController](#m_pparentcontroller)|指向父级动画控制器的指针。|  
  
## <a name="remarks"></a>备注  
 此类实现所有动画对象的基本方法。 动画对象可以表示值、 点、 大小、 矩形或在应用程序，以及任何自定义实体中的颜色。 动画对象存储在动画组 （请参阅 CAnimationGroup） 中。 每个组可以单独显示动画，并且可以将其视为模拟情节提要。 动画对象封装一个或多个动画变量 （请参阅 CAnimationVariable），具体取决于其逻辑表示形式。 例如，CAnimationRect 包含四个动画变量的矩形的每一侧的一个变量。 每个动画对象类公开重载的 AddTransition 方法，应该用于将转换应用到封装的动画变量。 动画对象可以 （可选） 通过对象 ID 来标识和组 id。 组 ID 为是必需的放置到正确的组的动画对象，但如果未指定组 ID，将对象放置在具有 ID 0 的默认组。 如果调用使用不同的 GroupID SetID，动画对象将移到另一个组 （如有必要，将创建一个新组）。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CAnimationBaseObject`  
  
## <a name="requirements"></a>要求  
 **标头：** afxanimationcontroller.h  
  
##  <a name="_dtorcanimationbaseobject"></a>CAnimationBaseObject:: ~ CAnimationBaseObject  
 析构函数。 当动画对象被销毁时调用。  
  
```  
virtual ~CAnimationBaseObject();
```  
  
##  <a name="applytransitions"></a>CAnimationBaseObject::ApplyTransitions  
 添加到情节提要与封装的动画变量的转换。  
  
```  
virtual BOOL ApplyTransitions(
    IUIAnimationStoryboard* pStoryboard,  
    BOOL bDependOnKeyframes);
```  
  
### <a name="parameters"></a>参数  
 `pStoryboard`  
 指向一个情节提要的指针。  
  
 `bDependOnKeyframes`  
 为 false，则此方法添加不依赖于关键帧的这些转换。  
  
### <a name="return-value"></a>返回值  
 如果已成功添加转换，则为 TRUE。  
  
### <a name="remarks"></a>备注  
 添加已添加了 AddTransition （在派生类中重载方法），到情节提要的相关的转换。  
  
##  <a name="canimationbaseobject"></a>CAnimationBaseObject::CAnimationBaseObject  
 构造的动画对象。  
  
```  
CAnimationBaseObject();

 
CAnimationBaseObject(
    UINT32 nGroupID,  
    UINT32 nObjectID = (UINT32)-1,  
    DWORD dwUserData = 0);
```  
  
### <a name="parameters"></a>参数  
 `nGroupID`  
 指定组的 id。  
  
 `nObjectID`  
 指定的对象 id。  
  
 `dwUserData`  
 用户定义数据，它可以与动画对象相关联并在运行时检索更高版本。  
  
### <a name="remarks"></a>备注  
 构造动画对象，并分配默认对象 ID (0) 和组 ID (0)。  
  
##  <a name="cleartransitions"></a>CAnimationBaseObject::ClearTransitions  
 删除所有相关的转换。  
  
```  
virtual void ClearTransitions(BOOL bAutodestroy);
```  
  
### <a name="parameters"></a>参数  
 `bAutodestroy`  
 指定是否自动销毁转换对象还是仅从相关的列表中删除它们。  
  
### <a name="remarks"></a>备注  
 删除所有相关的转换，并会销毁它们如果 bAutodestroy 或 m_bAutodestroyTransitions 标志为 TRUE。 仅当它们不在堆栈上分配，应自动销毁转换。 如果上面的标志均为 FALSE，过渡只会从相关的转换的内部列表。  
  
##  <a name="containsvariable"></a>CAnimationBaseObject::ContainsVariable  
 确定动画对象是否包含特定的动画变量。  
  
```  
virtual BOOL ContainsVariable(IUIAnimationVariable* pVariable);
```  
  
### <a name="parameters"></a>参数  
 `pVariable`  
 指向动画变量的指针。  
  
### <a name="return-value"></a>返回值  
 动画变量包含在动画对象; 如果为 TRUE否则为 FALSE。  
  
### <a name="remarks"></a>备注  
 此方法可以用于确定是否将由 pVariable 指定动画变量包含在动画对象内。 动画对象，具体取决于它的类型，可能包含多个动画变量。 例如，CAnimationColor 包含三个变量，一个用于每个颜色组件 （红色、 绿色和蓝色）。 当动画变量的值已更改时，Windows 动画 API 发送 ValueChanged 或 IntegerValueChanged 事件 （如果启用），以及此事件的参数是指向接口 IUIAnimationVariable 动画变量的指针。 此方法可帮助获得一个指针，指向包含的 COM 对象的指针从动画。  
  
##  <a name="createtransitions"></a>CAnimationBaseObject::CreateTransitions  
 创建与动画对象相关联的转换。  
  
```  
BOOL CreateTransitions();
```  
  
### <a name="return-value"></a>返回值  
 如果转换成功，则已创建，则返回 TRUE否则为 FALSE。  
  
### <a name="remarks"></a>备注  
 循环访问封装在派生的动画对象的动画变量的列表，并创建与每个动画变量相关联的转换。  
  
##  <a name="detachfromcontroller"></a>CAnimationBaseObject::DetachFromController  
 从父级动画控制器的动画对象中分离。  
  
```  
void DetachFromController();
```  
  
### <a name="remarks"></a>备注  
 此方法在内部使用。  
  
##  <a name="enableintegervaluechangedevent"></a>CAnimationBaseObject::EnableIntegerValueChangedEvent  
 设置整数值已更改事件处理程序。  
  
```  
virtual void EnableIntegerValueChangedEvent(
    CAnimationController* pController,  
    BOOL bEnable);
```  
  
### <a name="parameters"></a>参数  
 `pController`  
 指向父控制器的指针。  
  
 `bEnable`  
 指定是否启用或禁用的整数值已更改事件。  
  
### <a name="remarks"></a>备注  
 如果启用了整数值已更改事件处理程序，您可以处理 CAnimationController::OnAnimationIntegerValueChanged 方法，应在 CAnimationController 派生类中重写该方法中的此事件。 每次的动画的整数值发生更改时，调用此方法。  
  
##  <a name="enablevaluechangedevent"></a>CAnimationBaseObject::EnableValueChangedEvent  
 设置值发生更改时事件处理程序。  
  
```  
virtual void EnableValueChangedEvent(
    CAnimationController* pController,  
    BOOL bEnable);
```  
  
### <a name="parameters"></a>参数  
 `pController`  
 指向父控制器的指针。  
  
 `bEnable`  
 指定是否启用或禁用值已更改事件。  
  
### <a name="remarks"></a>备注  
 如果启用了值发生更改时事件处理程序，您可以处理 CAnimationController::OnAnimationValueChanged 方法，应在 CAnimationController 派生类中重写该方法中的此事件。 每次的动画值已更改时，调用此方法。  
  
##  <a name="getanimationvariablelist"></a>CAnimationBaseObject::GetAnimationVariableList  
 收集到包含的动画变量的指针。  
  
```  
virtual void GetAnimationVariableList(
    CList<CAnimationVariable*, 
    CAnimationVariable*>& lst) = 0;  
```  
  
### <a name="parameters"></a>参数  
 `lst`  
 必须使用动画对象中包含的动画变量填充列表。  
  
### <a name="remarks"></a>备注  
 这是必须在派生类中重写的纯虚方法。 动画对象，具体取决于它的类型，包含一个或多个动画变量。 例如，CAnimationPoint 包含 X 和 Y 坐标分别表示两个变量。 基类 CAnimationBaseObject 实现某些泛型方法，在列表中的动画变量的作用︰ ApplyTransitions、 ClearTransitions、 EnableValueChangedEvent、 EnableIntegerValueChangedEvent。 这些方法调用 GetAnimationVariableList，该类填充在派生类中有特定的动画对象中包含的实际动画变量，然后循环访问列表并执行必要的操作。 如果创建自定义动画对象时，您必须向 lst 添加该对象中包含的所有动画变量。  
  
##  <a name="getautodestroytransitions"></a>CAnimationBaseObject::GetAutodestroyTransitions  
 指示是否自动销毁相关的转换。  
  
```  
BOOL GetAutodestroyTransitions() const;  
```  
  
### <a name="return-value"></a>返回值  
 如果为 TRUE，相关的转换将销毁自动保存功能。如果为 FALSE，则应通过调用应用程序释放转换对象。  
  
### <a name="remarks"></a>备注  
 默认情况下此标志为 TRUE。 仅当分配到堆栈上的转换和/或转换应该释放通过调用应用程序，请设置此标志。  
  
##  <a name="getgroupid"></a>CAnimationBaseObject::GetGroupID  
 返回当前组 id。  
  
```  
UINT32 GetGroupID() const;  
```  
  
### <a name="return-value"></a>返回值  
 当前组 id。  
  
### <a name="remarks"></a>备注  
 使用此方法来检索组 id。 如果组 ID 尚未设置显式构造函数中或使用 SetID，的 0。  
  
##  <a name="getobjectid"></a>CAnimationBaseObject::GetObjectID  
 返回当前对象 id。  
  
```  
UINT32 GetObjectID() const;  
```  
  
### <a name="return-value"></a>返回值  
 当前的对象 id。  
  
### <a name="remarks"></a>备注  
 使用此方法可检索的对象 id。 如果对象 ID 尚未设置显式构造函数中或使用 SetID，的 0。  
  
##  <a name="getuserdata"></a>CAnimationBaseObject::GetUserData  
 返回用户定义的数据。  
  
```  
DWORD GetUserData() const;  
```  
  
### <a name="return-value"></a>返回值  
 自定义数据的值。  
  
### <a name="remarks"></a>备注  
 调用此方法以检索在运行时的自定义数据。 如果它未显式初始化，在构造函数中或使用 SetUserData，则返回的值将为 0。  
  
##  <a name="m_bautodestroytransitions"></a>CAnimationBaseObject::m_bAutodestroyTransitions  
 指定是否应自动销毁相关的转换。  
  
```  
BOOL m_bAutodestroyTransitions;  
```  
  
##  <a name="m_dwuserdata"></a>CAnimationBaseObject::m_dwUserData  
 存储用户定义的数据。  
  
```  
DWORD m_dwUserData;  
```  
  
##  <a name="m_ngroupid"></a>CAnimationBaseObject::m_nGroupID  
 指定动画对象的组 ID。  
  
```  
UINT32 m_nGroupID;  
```  
  
##  <a name="m_nobjectid"></a>CAnimationBaseObject::m_nObjectID  
 指定动画对象的对象 ID。  
  
```  
UINT32 m_nObjectID;  
```  
  
##  <a name="m_pparentcontroller"></a>CAnimationBaseObject::m_pParentController  
 指向父级动画控制器的指针。  
  
```  
CAnimationController* m_pParentController;  
```  
  
##  <a name="setautodestroytransitions"></a>CAnimationBaseObject::SetAutodestroyTransitions  
 设置自动销毁转换进行排序的标志。  
  
```  
void SetAutodestroyTransitions(BOOL bValue);
```  
  
### <a name="parameters"></a>参数  
 `bValue`  
 指定自动销毁标志。  
  
### <a name="remarks"></a>备注  
 设置此标志仅当分配使用 new 运算符的转换对象。 如果由于某种原因，在堆栈分配的转换对象，自动销毁标志应为 FALSE。 默认情况下此标志为 TRUE。  
  
##  <a name="setid"></a>CAnimationBaseObject::SetID  
 设置新的 Id。  
  
```  
void SetID(
    UINT32 nObjectID,  
    UINT32 nGroupID = 0);
```  
  
### <a name="parameters"></a>参数  
 `nObjectID`  
 指定新的对象 id。  
  
 `nGroupID`  
 指定新的组 id。  
  
### <a name="remarks"></a>备注  
 允许更改对象 ID 和组 id。 如果新的组 ID 不同于当前的 ID，动画对象移动到另一个组 （新组将被创建，如有必要）。  
  
##  <a name="setparentanimationobjects"></a>CAnimationBaseObject::SetParentAnimationObjects  
 动画对象与它们的容器中包含的动画变量之间建立关系。  
  
```  
virtual void SetParentAnimationObjects();
```  
  
### <a name="remarks"></a>备注  
 这是一个帮助程序，可用于动画对象与它们的容器中包含的动画变量之间建立关系。 它循环的动画变量，并将后向指针设置为将父动画对象传递给每个动画变量。 在当前实现中在 CAnimationBaseObject::ApplyTransitions 中建立的实际关系，因此反向指针不会设置在您调用 CAnimationGroup::Animate 之前。 当您处理事件并需要获取父动画对象从 CAnimationVariable （使用 CAnimationVariable::GetParentAnimationObject） 时可能有所了解关系。  
  
##  <a name="setuserdata"></a>CAnimationBaseObject::SetUserData  
 设置用户定义的数据。  
  
```  
void SetUserData (DWORD dwUserData);
```  
  
### <a name="parameters"></a>参数  
 `dwUserData`  
 指定自定义数据。  
  
### <a name="remarks"></a>备注  
 此方法用于将自定义数据与动画对象相关联。 此数据可能会更高版本在运行时通过检索 GetUserData。  
  
## <a name="see-also"></a>另请参阅  
 [类](../../mfc/reference/mfc-classes.md)

